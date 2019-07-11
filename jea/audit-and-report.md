---
ms.date: 07/10/2019
keywords: jea, powershell, säkerhet
title: Granskning och rapportering i JEA
ms.openlocfilehash: 2afefe83acecc1fc3643d49766120ffecc25378f
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726754"
---
# <a name="auditing-and-reporting-on-jea"></a>Granskning och rapportering i JEA

När du har distribuerat JEA kan behöva du granska regelbundet JEA-konfigurationen. Granskning kan utvärdera du att rätt personer har åtkomst till JEA-slutpunkt och deras tilldelade roller är fortfarande lämpliga.

## <a name="find-registered-jea-sessions-on-a-machine"></a>Hitta registrerade JEA-sessioner på en dator

Du kan kontrollera vilka JEA-sessioner är registrerade på en dator genom att använda den [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.

```powershell
# Filter for sessions that are configured as 'RestrictedRemoteServer' to find JEA-like session configurations
Get-PSSessionConfiguration | Where-Object { $_.SessionType -eq 'RestrictedRemoteServer' }
```

```Output
Name          : JEAMaintenance
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : CONTOSO\JEA_DNS_ADMINS AccessAllowed, CONTOSO\JEA_DNS_OPERATORS AccessAllowed,
                CONTOSO\JEA_DNS_AUDITORS AccessAllowed
```

De effektiva rättigheterna för slutpunkten visas i den **behörighet** egenskapen. Dessa användare har behörighet att ansluta till JEA-slutpunkt. Men de roller och kommandon som de har åtkomst till bestäms av den **RoleDefinitions** -egenskapen i den [session konfigurationsfilen](session-configurations.md) som användes för att registrera slutpunkten. Expandera den **RoleDefinitions** egenskapen att utvärdera rollen mappningarna i en registrerad JEA-slutpunkt.

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{
  Name = 'Role Capabilities'
  Expression = { $_.Value.RoleCapabilities }
}
```

## <a name="find-available-role-capabilities-on-the-machine"></a>Hitta tillgängliga rollfunktioner på datorn

JEA hämtar rollfunktioner från den `.psrc` filer som lagras i den **RoleCapabilities** mapp inuti en PowerShell-modul. Följande funktion hittar alla rollfunktioner på en dator.

```powershell
function Find-LocalRoleCapability {
    $results = @()

    # Find modules with a "RoleCapabilities" subfolder and add any PSRC files to the result set
    Get-Module -ListAvailable | ForEach-Object {
        $psrcpath = Join-Path -Path $_.ModuleBase -ChildPath 'RoleCapabilities'
        if (Test-Path $psrcpath) {
            $results += Get-ChildItem -Path $psrcpath -Filter *.psrc
        }
    }

    # Format the results nicely to make it easier to read
    $results | Select-Object @{ Name = 'Name'; Expression = { $_.Name.TrimEnd('.psrc') }}, @{
        Name = 'Path'; Expression = { $_.FullName }
    } | Sort-Object Name
}
```

> [!NOTE]
> Ordningen på resultaten från den här funktionen är inte nödvändigtvis ordningen som rollfunktioner väljs om flera rollfunktioner delar samma namn.

## <a name="check-effective-rights-for-a-specific-user"></a>Kontrollera effektiva rättigheterna för en viss användare

Den [Get-PSSessionCapability](/powershell/module/microsoft.powershell.core/Get-PSSessionCapability) cmdlet räknar upp alla kommandon som är tillgängliga på en JEA-slutpunkt som baseras på en användares gruppmedlemskap.
Utdata från `Get-PSSessionCapability` är identisk med den angivna användaren som kör `Get-Command -CommandType All` i en JEA-session.

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

Om användarna inte är permanenta medlemmar i grupper som beviljar dem ytterligare JEA rättigheter, kan denna cmdlet inte återspeglar de extra behörigheterna. Detta inträffar när du använder just-in-time-privilegierad åtkomst hanteringssystem så att användarna kan tillfälligt tillhör en säkerhetsgrupp. Utvärdera noggrant mappning av användare till roller och funktioner så att användare bara får åtkomstnivån som behövs för att utföra sitt arbete.

## <a name="powershell-event-logs"></a>PowerShell-händelseloggar

Om du har aktiverat modulen eller skript blockera inloggning systemet kan du se händelser i Windows-händelseloggar för varje kommando som en användare kör i en JEA-session. Du hittar dessa händelser genom att öppna **Microsoft-Windows-PowerShell/Operational** händelselogg och leta efter händelser med händelse-ID **4104**.

Varje post i händelseloggen innehåller information om sessionen där kommandot kördes. Om JEA-sessioner, händelsen innehåller information om den **ConnectedUser** och **användare**. Den **ConnectedUser** är den faktiska användaren som skapade JEA-sessionen. Den **användare** är kontot JEA används för att köra kommandot.

Händelseloggarna för programmet visa ändringar som görs av den **användare**. Så att ha modulen och skript loggning är aktiverat krävs för att spåra ett visst kommandoanrop tillbaka till den **ConnectedUser**.

## <a name="application-event-logs"></a>Händelseloggarna för programmet

Kommandon körs i en JEA-session som interagerar med externa program eller tjänster kan logga händelser till sina egna händelseloggar. Till skillnad från PowerShell loggar och avskrifter avbilda inte andra mekanismer som loggning anslutna användaren JEA-sessionen. I stället logga programmen endast virtuella kör som-användaren.
För att fastställa vem som körde kommandot, som du behöver läsa en [session avskrift](#session-transcripts) eller korrelera PowerShell händelseloggar med tiden och användaren visas i programmets händelselogg.

WinRM-loggen kan också hjälpa dig att korrelera kör som-användare till den anslutande användaren i händelseloggen för ett program. Händelse-ID **193** i den **Microsoft-Windows-Windows Remote Management/Operational** log registrerar säkerhetsidentifierare (SID) och namnet på tjänstkontot för både den anslutande användaren och kör som användare för varje ny JEA sessionen.

## <a name="session-transcripts"></a>Sessionen avskrifter

Om du har konfigurerat JEA för att skapa en avskrift för varje användarsession lagras en Textversion av varje användares åtgärder i den angivna mappen.

Följande kommando (som administratör) hittar alla funktionerna för avskrift kataloger.

```powershell
Get-PSSessionConfiguration |
  Where-Object { $_.TranscriptDirectory -ne $null } |
    Format-Table Name, TranscriptDirectory
```

Varje avskrift börjar med information om den tid som sessionen igång, vilka användare som är ansluten till sessionen och vilken JEA-identitet har tilldelats.

```
**********************
Windows PowerShell transcript start
Start time: 20160710144736
Username: CONTOSO\Alice
RunAs User: WinRM Virtual Users\WinRM VA_1_CONTOSO_Alice
Machine: SERVER01 (Microsoft Windows NT 10.0.14393.0)
[...]
```

Brödtexten i avskriften innehåller information om varje kommando som anropas av användaren. Den exakta syntaxen för kommandot är inte tillgänglig i JEA-sessioner på grund av sättet kommandon omvandlas för PowerShell-fjärrkommunikation. Du kan dock fortfarande kontrollera effektiva kommandot som kördes. Nedan visas ett exempel avskrift kodavsnitt från en användare som kör `Get-Service Dns` i en JEA-session:

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

En **CommandInvocation** rad är avsedd för varje kommando som en användare kör. **ParameterBindings** registrera varje parametern och värdet som angetts i kommandot. I exemplet ovan kan du se att parametern **namn** har angetts i med värdet **Dns** för den `Get-Service` cmdlet.

Utdata för var och en kommandot också utlösare en **CommandInvocation**, vanligtvis i `Out-Default`. Den **InputObject** av `Out-Default` är PowerShell-objektet som returnerades från kommandot. Information om objektet skrivs ut några rader under nära frihandsbilden vad användaren skulle ha sett.

## <a name="see-also"></a>Se även

[*PowerShell ♥ blå teamet* blogginlägg om säkerhet](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
