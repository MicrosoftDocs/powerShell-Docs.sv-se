---
ms.date: 07/10/2019
keywords: Jea, PowerShell, säkerhet
title: Granskning och rapportering av JEA
ms.openlocfilehash: 2afefe83acecc1fc3643d49766120ffecc25378f
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017925"
---
# <a name="auditing-and-reporting-on-jea"></a>Granskning och rapportering av JEA

När du har distribuerat JEA måste du regelbundet granska JEA-konfigurationen. Granskningen hjälper dig att utvärdera att rätt personer har åtkomst till JEA-slutpunkten och att de tilldelade rollerna fortfarande är lämpliga.

## <a name="find-registered-jea-sessions-on-a-machine"></a>Hitta registrerade JEA-sessioner på en dator

Använd cmdleten [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) för att kontrol lera vilka Jea-sessioner som har registrerats på en dator.

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

De effektiva rättigheterna för slut punkten visas i egenskapen **behörighet** . Dessa användare har behörighet att ansluta till JEA-slutpunkten. Men de roller och kommandon som de har åtkomst till bestäms av egenskapen **RoleDefinitions** i den [konfigurations fil för sessionen](session-configurations.md) som användes för att registrera slut punkten. Expandera egenskapen **RoleDefinitions** för att utvärdera roll mappningarna i en registrerad Jea-slutpunkt.

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{
  Name = 'Role Capabilities'
  Expression = { $_.Value.RoleCapabilities }
}
```

## <a name="find-available-role-capabilities-on-the-machine"></a>Hitta tillgängliga roll funktioner på datorn

Jea hämtar roll funktioner från `.psrc` filerna som lagras i mappen **RoleCapabilities** i en PowerShell-modul. Följande funktion hittar alla roll funktioner som är tillgängliga på en dator.

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
> Ordningen på resultaten från den här funktionen är inte nödvändigt vis den ordning som roll funktionerna ska väljas i om flera roll funktioner delar samma namn.

## <a name="check-effective-rights-for-a-specific-user"></a>Kontrol lera gällande rättigheter för en speciell användare

Cmdlet [: en get-PSSessionCapability](/powershell/module/microsoft.powershell.core/Get-PSSessionCapability) räknar upp alla kommandon som är tillgängliga på en Jea-slutpunkt baserat på användarens grupp medlemskap.
Resultatet av `Get-PSSessionCapability` är identiskt med den angivna användaren som körs `Get-Command -CommandType All` i en Jea-session.

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

Om användarna inte är permanenta medlemmar i grupper som skulle ge dem ytterligare JEA-rättigheter kanske denna cmdlet inte återspeglar dessa extra behörigheter. Detta inträffar när du använder just-in-Time-hanterings system för att tillåta användare att tillfälligt tillhöra en säkerhets grupp. Utvärdera noggrant mappningen av användare till roller och funktioner för att säkerställa att användarna bara får den åtkomst nivå som krävs för att utföra sina jobb.

## <a name="powershell-event-logs"></a>PowerShell-händelseloggar

Om du har aktiverat modul-eller skript Blocks loggning i systemet kan du se händelser i händelse loggarna i Windows för varje kommando som en användare kör i en JEA-session. Du hittar de här händelserna genom att öppna **Microsoft-Windows-PowerShell/Operations-** händelseloggen och leta efter händelser med händelse-ID **4104**.

Varje post i händelse loggen innehåller information om sessionen där kommandot kördes. För JEA-sessioner innehåller händelsen information om **ConnectedUser** och **RunAsUser**. **ConnectedUser** är den faktiska användaren som skapade Jea-sessionen. **RunAsUser** är det konto-Jea som används för att köra kommandot.

Program händelse loggar visar ändringar som görs av **RunAsUser**. Därför krävs att modul-och skript loggning är aktiverat för att spåra ett särskilt kommando anrop tillbaka till **ConnectedUser**.

## <a name="application-event-logs"></a>Program händelse loggar

Kommandon som körs i en JEA-session som interagerar med externa program eller tjänster kan logga händelser till sina egna händelse loggar. Till skillnad från PowerShell-loggar och avskrifter fångar inte andra loggnings metoder den anslutna användaren av JEA-sessionen. I stället loggar de här programmen enbart den virtuella kör som-användaren.
För att fastställa vem som körde kommandot måste du kontakta en [session avskrift](#session-transcripts) eller korrelera PowerShell-händelseloggen med den tid och användare som visas i program händelse loggen.

WinRM-loggen kan också hjälpa dig att korrelera kör som-användare till den anslutande användaren i en program händelse logg. Händelse-ID **193** i **Microsoft-Windows-Windows-fjärrhantering/drift** logg registrerar säkerhets identifieraren (sid) och konto namnet för både den anslutna användaren och kör som-användare för varje ny Jea-session.

## <a name="session-transcripts"></a>Avskrifter för session

Om du har konfigurerat JEA för att skapa en avskrift för varje användarsession lagras en text kopia av varje användares åtgärder i den angivna mappen.

Följande kommando (som administratör) hittar alla avskrifts kataloger.

```powershell
Get-PSSessionConfiguration |
  Where-Object { $_.TranscriptDirectory -ne $null } |
    Format-Table Name, TranscriptDirectory
```

Varje avskrift börjar med information om tiden då sessionen startades, vilken användare anslöt till sessionen och vilken JEA identitet som har tilldelats dem.

```
**********************
Windows PowerShell transcript start
Start time: 20160710144736
Username: CONTOSO\Alice
RunAs User: WinRM Virtual Users\WinRM VA_1_CONTOSO_Alice
Machine: SERVER01 (Microsoft Windows NT 10.0.14393.0)
[...]
```

Bröd texten i avskriften innehåller information om varje kommando som användaren anropade. Den exakta syntaxen för kommandot som används är inte tillgänglig i JEA-sessioner på grund av hur kommandon omvandlas för PowerShell-fjärrkommunikation. Du kan dock fortfarande bestämma det effektiva kommando som kördes. Nedan visas ett exempel på en avskrifts- `Get-Service Dns` kodfragment från en användare som körs i en Jea-session:

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

En **CommandInvocation** -rad skrivs för varje kommando som en användare kör. **ParameterBindings** spelar in varje parameter och värde som medföljer kommandot. I det tidigare exemplet kan du se att parameter **namnet** angavs med värdet **DNS** för `Get-Service` cmdleten.

Utdata från varje kommando utlöser även en **CommandInvocation**, vanligt vis `Out-Default`till. **InputObject** för `Out-Default` är PowerShell-objektet som returnerades från kommandot. Informationen om objektet skrivs ut några rader nedan, och mimicking vad användaren skulle ha sett.

## <a name="see-also"></a>Se även

[*PowerShell ♥ det blå teamets* blogg inlägg om säkerhet](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
