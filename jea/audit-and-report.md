---
ms.date: 06/12/2017
keywords: jea, powershell, säkerhet
title: Granskning och rapportering i JEA
ms.openlocfilehash: 2388c735840d8d3683aa8bc9869b9fb0371e5902
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688604"
---
# <a name="auditing-and-reporting-on-jea"></a>Granskning och rapportering i JEA

> Gäller för: Windows PowerShell 5.0

När du har distribuerat JEA, kommer du att regelbundet granska JEA-konfigurationen.
Detta hjälper dig att utvärdera om rätt personer har åtkomst till JEA-slutpunkt och om deras tilldelade roller är fortfarande lämpliga.

Det här avsnittet beskrivs de olika sätt som du kan granska en JEA-slutpunkt.

## <a name="find-registered-jea-sessions-on-a-machine"></a>Hitta registrerade JEA-sessioner på en dator

Du kan kontrollera vilka JEA-sessioner är registrerade på en dator genom att använda den [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.

```powershell
# Filter for sessions that are configured as 'RestrictedRemoteServer' to find JEA-like session configurations
PS C:\> Get-PSSessionConfiguration | Where-Object { $_.SessionType -eq 'RestrictedRemoteServer' }


Name          : JEAMaintenance
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : CONTOSO\JEA_DNS_ADMINS AccessAllowed, CONTOSO\JEA_DNS_OPERATORS AccessAllowed, CONTOSO\JEA_DNS_AUDITORS AccessAllowed
```

De effektiva rättigheterna för slutpunkten visas i egenskapen ”tillstånd”.
Dessa användare har behörighet att ansluta till JEA-slutpunkt, men vilka roller (och därmed kommandon) de har åtkomst till fastställs av ”RoleDefinitions”-fältet i den [session konfigurationsfilen](session-configurations.md) som användes för att registrera den slutpunkt.

Du kan utvärdera rollen mappningarna i en registrerad JEA-slutpunkt genom att expandera data i egenskapen ”RoleDefinitions”.

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{ Name = 'Role Capabilities'; Expression = { $_.Value.RoleCapabilities } }
```

## <a name="find-available-role-capabilities-on-the-machine"></a>Hitta tillgängliga rollfunktioner på datorn

Rollen funktionsfiler ska endast användas av JEA om de lagras i en ”RoleCapabilities”-mapp inuti en giltig PowerShell-modul.
Du hittar alla rollfunktioner på en dator genom att söka igenom listan över tillgängliga moduler.

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
> Ordningen på resultaten från den här funktionen är inte nödvändigtvis ordningen som rollfunktioner väljs om flera rollfunktioner delar samma namn.

## <a name="check-effective-rights-for-a-specific-user"></a>Kontrollera effektiva rättigheterna för en viss användare

När du har konfigurerat en JEA-slutpunkt, kanske du vill kontrollera vilka kommandon som är tillgängliga för en viss användare i en JEA-session.
Du kan använda [Get-PSSessionCapability](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Get-PSSessionCapability) att räkna upp alla kommandon som gäller för en användare om de vore att starta en JEA-session med deras aktuella gruppmedlemskap.
Utdata från `Get-PSSessionCapability` är identisk med den angivna användaren som kör `Get-Command -CommandType All` i en JEA-session.

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

Om användarna inte är permanenta medlemmar i grupper som beviljar dem ytterligare JEA rättigheter, kan denna cmdlet inte återspeglar de extra behörigheterna.
Detta är vanligtvis fallet när du använder just-in-time privilegierad åtkomst hanteringssystem så att användarna kan tillfälligt tillhör en säkerhetsgrupp.
Utvärdera alltid noggrant mappningen av användare till roller och innehållet i varje roll för att säkerställa att användarna bara får åtkomst till den minsta uppsättningen kommandon som krävs för att utföra sitt arbete.

## <a name="powershell-event-logs"></a>PowerShell-händelseloggar

Om du har aktiverat modulen och/eller skript blockera inloggning systemet kommer du att kunna hitta händelser i Windows-händelseloggar för varje kommando som en användare som körde i sina JEA-sessioner.
För att hitta dessa händelser, öppnar du Windows Loggboken, navigera till den **Microsoft-Windows-PowerShell/Operational** händelselogg och leta efter händelser med händelse-ID **4104**.

Varje post i händelseloggen innehåller information om den session där kommandot kördes.
Om JEA-sessioner, detta innehåller viktig information om den **ConnectedUser**, vilket är den faktiska användare som skapade JEA-sessionen, samt de **användare** som identifierar kontot JEA används för att Kör kommandot.
Händelseloggarna för programmet visas ändringar av användare, så att ha betyg eller modulen/skript-loggning är aktiverat är avgörande för att kunna spåra ett visst kommandoanrop tillbaka till en användare.

## <a name="application-event-logs"></a>Händelseloggarna för programmet

När du kör ett kommando i en JEA-session som interagerar med ett externt program eller en tjänst, kan dessa program logga händelser till sina egna händelseloggar.
Till skillnad från PowerShell loggar och avskrifter, andra mekanismer som loggning kan inte avgöra hur anslutna användaren JEA-sessionen och i stället loggas bara virtuella kör som-användaren eller grupphanterade tjänstkontot.
Om du vill fastställa som körde kommandot, behöver läsa en [session avskrift](#session-transcripts) eller korrelera PowerShell händelseloggar med tiden och användaren visas i programmets händelselogg.

WinRM logg kan också hjälpa dig att korrelera kör som användare i händelseloggen för ett program med den anslutande användaren.
Händelse-ID **193** i den **Microsoft-Windows-Windows Remote Management/Operational** loggposter säkerhetsidentifierare (SID) och kontot för anslutande användaren och kör som användare varje gång en JEA session skapas.

## <a name="session-transcripts"></a>Sessionen avskrifter

Om du har konfigurerat JEA för att skapa en avskrift för varje användarsession kommer en Textversion av varje användares åtgärder att lagras i den angivna mappen.

Kör följande kommando som administratör på datorn du vill hitta alla avskrift kataloger konfigurerad med JEA:

```powershell
Get-PSSessionConfiguration | Where-Object { $_.TranscriptDirectory -ne $null } | Format-Table Name, TranscriptDirectory
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

I brödtexten i avskriften loggas information om varje kommando som anropas av användaren.
Den exakta syntaxen för kommandot som kördes av användaren är inte tillgänglig i JEA-sessioner på grund av det sätt som kommandon omvandlas för PowerShell-fjärrkommunikation, men du kan fortfarande se gällande kommandot som kördes.
Nedan visas ett exempel avskrift kodavsnitt från en användare som kör `Get-Service Dns` i en JEA-session:

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

För varje kommando som en användare kör en ”CommandInvocation”-linje ska skrivas, som beskriver cmdleten eller fungera användaren anropas.
ParameterBindings Följ varje CommandInvocation för att du berättar om varje parametern och värdet som har angetts i kommandot.
I exemplet ovan ser du att parametern ”namn” har angett värdet ”Dns” för cmdleten ”Get-Service”.

Utdata för varje kommando kommer också utlösa en CommandInvocation vanligtvis ut som standard.
InputObject Out-Default är PowerShell-objektet som returnerades från kommandot.
Information om objektet skrivs ut några rader under nära frihandsbilden vad användaren skulle ha sett.

## <a name="see-also"></a>Se även

- [*PowerShell ♥ blå teamet* blogginlägg om säkerhet](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)
