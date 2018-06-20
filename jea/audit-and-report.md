---
ms.date: 06/12/2017
keywords: jea powershell säkerhet
title: Granskning och rapportering av JEA
ms.openlocfilehash: e68206cd6fe94c51507f42ae2c3e6702f6fd4e0f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188860"
---
# <a name="auditing-and-reporting-on-jea"></a>Granskning och rapportering av JEA

> Gäller för: Windows PowerShell 5.0

När du har distribuerat JEA, kommer du vill granska regelbundet JEA konfigurationen.
Detta hjälper dig att bedöma om rätt personer har åtkomst till slutpunkten JEA och deras tilldelade roller är fortfarande lämplig.

Det här avsnittet beskrivs de olika sätt som du kan granska en JEA slutpunkt.

## <a name="find-registered-jea-sessions-on-a-machine"></a>Hitta registrerade JEA sessioner på en dator

För att kontrollera vilka JEA sessioner är registrerade på en dator, använda den [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.

```powershell
# Filter for sessions that are configured as 'RestrictedRemoteServer' to find JEA-like session configurations
PS C:\> Get-PSSessionConfiguration | Where-Object { $_.SessionType -eq 'RestrictedRemoteServer' }


Name          : JEAMaintenance
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : CONTOSO\JEA_DNS_ADMINS AccessAllowed, CONTOSO\JEA_DNS_OPERATORS AccessAllowed, CONTOSO\JEA_DNS_AUDITORS AccessAllowed
```

De effektiva rättigheterna för slutpunkten anges i egenskapen ”tillstånd”.
Dessa användare har behörighet att ansluta till JEA slutpunkten, men vilka roller (och därmed kommandon) de har tillgång till bestäms av fältet ”RoleDefinitions” i den [session konfigurationsfilen](session-configurations.md) som användes för att registrera den slutpunkt.

Du kan utvärdera rollen mappningarna i en registrerad JEA slutpunkt genom att expandera data i egenskapen ”RoleDefinitions”.

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{ Name = 'Role Capabilities'; Expression = { $_.Value.RoleCapabilities } }
```

## <a name="find-available-role-capabilities-on-the-machine"></a>Hitta funktioner tillgängliga roller på datorn

Rollen funktionsfiler kommer bara att användas av JEA om de lagras i en ”RoleCapabilities” mapp inuti en giltig PowerShell-modul.
Du hittar alla rollen funktioner som är tillgängliga på en dator genom att söka i listan över tillgängliga moduler.

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
    $results | Select-Object @{ Name = 'Name'; Expression = { $_.Name.TrimEnd('.psrc') }}, @{ Name = 'Path'; Expression = { $_.FullName }} | Sort-Object Name
}
```

> [!NOTE]
> Ordningen på resultaten från den här funktionen är inte nödvändigtvis ordning i vilken roll-funktioner kommer att markeras om flera rollen funktionerna delar samma namn.

## <a name="check-effective-rights-for-a-specific-user"></a>Kontrollera effektiva rättigheterna för en viss användare

När du har konfigurerat en slutpunkt för JEA kanske du vill kontrollera vilka kommandon som är tillgängliga för en viss användare i en JEA-session.
Du kan använda [Get-PSSessionCapability](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Get-PSSessionCapability) att räkna upp alla kommandon som gäller för en användare om de starta en session i JEA med deras aktuella gruppmedlemskap.
Utdata från `Get-PSSessionCapability` är identisk med den angivna användaren som kör `Get-Command -CommandType All` i en JEA-session.

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

Om användarna inte är permanenta medlemmar i grupper som skulle ge dem ytterligare JEA rättigheter, kan denna cmdlet inte återspeglar de extra behörigheterna.
Detta är vanligtvis när du använder system för just-in-time privilegierad åtkomst så att användarna kan tillfälligt tillhör en säkerhetsgrupp.
Alltid noggrant utvärdera koppling av användare till roller och innehållet i varje roll för att säkerställa att användarna bara får åtkomst till ett minimum av kommandon som krävs för att utföra sitt arbete.

## <a name="powershell-event-logs"></a>PowerShell-händelseloggar

Om du har aktiverat modulen och/eller skript block loggning på datorn kommer du att kunna hitta händelser i Windows-händelseloggar för varje kommando som en användare som körde i sina JEA sessioner.
Om du vill söka efter dessa händelser, öppna Loggboken, navigera till den **Microsoft-Windows-PowerShell/Operational** händelselogg och leta efter händelser med händelse-ID **4104**.

Varje post i händelseloggen innehåller information om sessionen som kommandot kördes.
För JEA sessioner detta innehåller viktig information om den **ConnectedUser**, vilket är den faktiska användare som skapade JEA sessionen, samt de **användare** som identifierar kontot JEA används för att Kör kommandot.
Händelseloggarna program visas ändringar av användare, så att betyg eller skriptet och module loggning är aktiverat är avgörande för att kunna spåra ett kommando för anrop till en användare.

## <a name="application-event-logs"></a>Händelseloggarna program

När du kör ett kommando i en session i JEA som samverkar med ett externt program eller en tjänst, kan dessa program logghändelser till sina egna loggar.
Till skillnad från PowerShell-loggar och betyg andra mekanismer för loggning kommer inte att avbilda den anslutna användaren JEA sessionen och i stället loggas bara virtuella kör som-användaren eller grupphanterade tjänstkontot.
För att fastställa vem som körde kommandot, måste du kontakta en [session betyg](#session-transcripts) eller korrelera PowerShell händelseloggar med tiden och visas i programmets händelselogg.

WinRM loggen kan också hjälpa dig att korrelera körs som användare i händelseloggen för ett program med den anslutande användaren.
Händelse-ID **193** i den **Microsoft Windows Windows Remote Management/Operational** loggposter säkerhetsidentifierare (SID) och kontot namn för den anslutande användaren och köra som användaren varje gång en JEA sessionen har skapats.

## <a name="session-transcripts"></a>Sessionen betyg

Om du har konfigurerat JEA för att skapa ett betyg för varje användarsession lagras en text kopia av varje användaråtgärder i den angivna mappen.

Du hittar alla betyg kataloger genom att köra följande kommando som administratör på datorn konfigureras med JEA:

```powershell
Get-PSSessionConfiguration | Where-Object { $_.TranscriptDirectory -ne $null } | Format-Table Name, TranscriptDirectory
```

Varje betyg börjar med information om den tid som en session startades vilka användare som anslöt till sessionen och vilken JEA identitet har tilldelats.

```
**********************
Windows PowerShell transcript start
Start time: 20160710144736
Username: CONTOSO\Alice
RunAs User: WinRM Virtual Users\WinRM VA_1_CONTOSO_Alice
Machine: SERVER01 (Microsoft Windows NT 10.0.14393.0)
[...]
```

I brödtexten för betyg loggas information om varje kommando som anropas av användaren.
Den exakta syntaxen för kommandot som kördes användaren är inte tillgänglig i JEA sessioner på grund av det sätt som kommandon omvandlas för PowerShell-fjärrkommunikation, men du kan fortfarande se effektiva kommandot som kördes.
Nedan visas ett exempel betyg kodavsnitt från en användare som kör `Get-Service Dns` i en JEA-session:

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

För varje kommando som en användare kör en rad ”CommandInvocation” skrivs, som beskriver cmdlet eller fungera användaren anropas.
ParameterBindings följer varje CommandInvocation för information om varje parameter och ett värde som har angetts i kommandot.
I exemplet ovan kan du se att parametern ”namn” har lämnat värdet ”Dns” för ”Get-tjänst”-cmdlet.

Utdata från varje kommando kommer också utlösa en CommandInvocation vanligtvis ut som standard.
InputObject Out-Default är PowerShell-objektet som returnerades från kommandot.
Information om objektet skrivs ut några rader under nära frihandsbilden vad användaren skulle ha sett.

## <a name="see-also"></a>Se även

- [Granska användaråtgärder i en JEA session](audit-and-report.md)
- [*PowerShell ♥ blå teamet* blogginlägg om säkerhet](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)