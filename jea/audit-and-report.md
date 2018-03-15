---
ms.date: 2017-06-12
author: rpsqrd
ms.topic: conceptual
keywords: "jea powershell säkerhet"
title: Granskning och rapportering av JEA
ms.openlocfilehash: 57148bc3753bdd751bfa21fc3198aca3f8654849
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/15/2018
---
# <a name="auditing-and-reporting-on-jea"></a><span data-ttu-id="7823e-103">Granskning och rapportering av JEA</span><span class="sxs-lookup"><span data-stu-id="7823e-103">Auditing and Reporting on JEA</span></span>

> <span data-ttu-id="7823e-104">Gäller för: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="7823e-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="7823e-105">När du har distribuerat JEA, kommer du vill granska regelbundet JEA konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="7823e-105">After you've deployed JEA, you will want to regularly audit the JEA configuration.</span></span>
<span data-ttu-id="7823e-106">Detta hjälper dig att bedöma om rätt personer har åtkomst till slutpunkten JEA och deras tilldelade roller är fortfarande lämplig.</span><span class="sxs-lookup"><span data-stu-id="7823e-106">This will help you assess if the correct people have access to the JEA endpoint and if their assigned roles are still appropriate.</span></span>

<span data-ttu-id="7823e-107">Det här avsnittet beskrivs de olika sätt som du kan granska en JEA slutpunkt.</span><span class="sxs-lookup"><span data-stu-id="7823e-107">This topic describes the various ways you can audit a JEA endpoint.</span></span>

## <a name="find-registered-jea-sessions-on-a-machine"></a><span data-ttu-id="7823e-108">Hitta registrerade JEA sessioner på en dator</span><span class="sxs-lookup"><span data-stu-id="7823e-108">Find registered JEA sessions on a machine</span></span>

<span data-ttu-id="7823e-109">För att kontrollera vilka JEA sessioner är registrerade på en dator, använda den [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7823e-109">To check which JEA sessions are registered on a machine, use the [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.</span></span>

```powershell
# Filter for sessions that are configured as 'RestrictedRemoteServer' to find JEA-like session configurations
PS C:\> Get-PSSessionConfiguration | Where-Object { $_.SessionType -eq 'RestrictedRemoteServer' }


Name          : JEAMaintenance
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : CONTOSO\JEA_DNS_ADMINS AccessAllowed, CONTOSO\JEA_DNS_OPERATORS AccessAllowed, CONTOSO\JEA_DNS_AUDITORS AccessAllowed
```

<span data-ttu-id="7823e-110">De effektiva rättigheterna för slutpunkten anges i egenskapen ”tillstånd”.</span><span class="sxs-lookup"><span data-stu-id="7823e-110">The effective rights for the endpoint are listed in the "Permission" property.</span></span>
<span data-ttu-id="7823e-111">Dessa användare har behörighet att ansluta till JEA slutpunkten, men vilka roller (och därmed kommandon) de har tillgång till bestäms av fältet ”RoleDefinitions” i den [session konfigurationsfilen](session-configurations.md) som användes för att registrera den slutpunkt.</span><span class="sxs-lookup"><span data-stu-id="7823e-111">These users have the right to connect to the JEA endpoint, but which roles (and, by extension, commands) they have access to is determined by the "RoleDefinitions" field in the [session configuration file](session-configurations.md) that was used to register the endpoint.</span></span>

<span data-ttu-id="7823e-112">Du kan utvärdera rollen mappningarna i en registrerad JEA slutpunkt genom att expandera data i egenskapen ”RoleDefinitions”.</span><span class="sxs-lookup"><span data-stu-id="7823e-112">You can evaluate the role mappings in a registered JEA endpoint by expanding the data in the "RoleDefinitions" property.</span></span>

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{ Name = 'Role Capabilities'; Expression = { $_.Value.RoleCapabilities } }
```

## <a name="find-available-role-capabilities-on-the-machine"></a><span data-ttu-id="7823e-113">Hitta funktioner tillgängliga roller på datorn</span><span class="sxs-lookup"><span data-stu-id="7823e-113">Find available role capabilities on the machine</span></span>

<span data-ttu-id="7823e-114">Rollen funktionsfiler kommer bara att användas av JEA om de lagras i en ”RoleCapabilities” mapp inuti en giltig PowerShell-modul.</span><span class="sxs-lookup"><span data-stu-id="7823e-114">Role capability files will only be used by JEA if they are stored in a "RoleCapabilities" folder inside a valid PowerShell module.</span></span>
<span data-ttu-id="7823e-115">Du hittar alla rollen funktioner som är tillgängliga på en dator genom att söka i listan över tillgängliga moduler.</span><span class="sxs-lookup"><span data-stu-id="7823e-115">You can find all role capabilities available on a computer by searching the list of available modules.</span></span>

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
> <span data-ttu-id="7823e-116">Ordningen på resultaten från den här funktionen är inte nödvändigtvis ordning i vilken roll-funktioner kommer att markeras om flera rollen funktionerna delar samma namn.</span><span class="sxs-lookup"><span data-stu-id="7823e-116">The order of results from this function is not necessarily the order in which the role capabilities will be selected if multiple role capabilities share the same name.</span></span>

## <a name="check-effective-rights-for-a-specific-user"></a><span data-ttu-id="7823e-117">Kontrollera effektiva rättigheterna för en viss användare</span><span class="sxs-lookup"><span data-stu-id="7823e-117">Check effective rights for a specific user</span></span>

<span data-ttu-id="7823e-118">När du har konfigurerat en slutpunkt för JEA kanske du vill kontrollera vilka kommandon som är tillgängliga för en viss användare i en JEA-session.</span><span class="sxs-lookup"><span data-stu-id="7823e-118">Once you have set up a JEA endpoint, you may want to check which commands are available to a specific user in a JEA session.</span></span>
<span data-ttu-id="7823e-119">Du kan använda [Get-PSSessionCapability](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Get-PSSessionCapability) att räkna upp alla kommandon som gäller för en användare om de starta en session i JEA med deras aktuella gruppmedlemskap.</span><span class="sxs-lookup"><span data-stu-id="7823e-119">You can use [Get-PSSessionCapability](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Get-PSSessionCapability) to enumerate all of the commands applicable to a user if they were to start a JEA session with their current group memberships.</span></span>
<span data-ttu-id="7823e-120">Utdata från `Get-PSSessionCapability` är identisk med den angivna användaren som kör `Get-Command -CommandType All` i en JEA-session.</span><span class="sxs-lookup"><span data-stu-id="7823e-120">The output of `Get-PSSessionCapability` is identical to that of the specified user running `Get-Command -CommandType All` in a JEA session.</span></span>

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

<span data-ttu-id="7823e-121">Om användarna inte är permanenta medlemmar i grupper som skulle ge dem ytterligare JEA rättigheter, kan denna cmdlet inte återspeglar de extra behörigheterna.</span><span class="sxs-lookup"><span data-stu-id="7823e-121">If your users are not permanent members of groups which would grant them additional JEA rights, this cmdlet may not reflect those extra permissions.</span></span>
<span data-ttu-id="7823e-122">Detta är vanligtvis när du använder system för just-in-time privilegierad åtkomst så att användarna kan tillfälligt tillhör en säkerhetsgrupp.</span><span class="sxs-lookup"><span data-stu-id="7823e-122">This is typically the case when using just-in-time privileged access management systems to allow users to temporarily belong to a security group.</span></span>
<span data-ttu-id="7823e-123">Alltid noggrant utvärdera koppling av användare till roller och innehållet i varje roll för att säkerställa att användarna bara får åtkomst till ett minimum av kommandon som krävs för att utföra sitt arbete.</span><span class="sxs-lookup"><span data-stu-id="7823e-123">Always carefully evaluate the mapping of users to roles and the contents of each role to ensure users are only getting access to the least amount of commands needed to do their jobs successfully.</span></span>

## <a name="powershell-event-logs"></a><span data-ttu-id="7823e-124">PowerShell-händelseloggar</span><span class="sxs-lookup"><span data-stu-id="7823e-124">PowerShell event logs</span></span>

<span data-ttu-id="7823e-125">Om du har aktiverat modulen och/eller skript block loggning på datorn kommer du att kunna hitta händelser i Windows-händelseloggar för varje kommando som en användare som körde i sina JEA sessioner.</span><span class="sxs-lookup"><span data-stu-id="7823e-125">If you enabled module and/or script block logging on the system, you will be able to find events in the Windows event logs for each command a user ran in their JEA sessions.</span></span>
<span data-ttu-id="7823e-126">Om du vill söka efter dessa händelser, öppna Loggboken, navigera till den **Microsoft-Windows-PowerShell/Operational** händelselogg och leta efter händelser med händelse-ID **4104**.</span><span class="sxs-lookup"><span data-stu-id="7823e-126">To find these events, open the Windows Event Viewer, navigate to the **Microsoft-Windows-PowerShell/Operational** event log, and look for events with event ID **4104**.</span></span>

<span data-ttu-id="7823e-127">Varje post i händelseloggen innehåller information om sessionen som kommandot kördes.</span><span class="sxs-lookup"><span data-stu-id="7823e-127">Each event log entry will include information about the session in which the command was run.</span></span>
<span data-ttu-id="7823e-128">För JEA sessioner detta innehåller viktig information om den **ConnectedUser**, vilket är den faktiska användare som skapade JEA sessionen, samt de **användare** som identifierar kontot JEA används för att Kör kommandot.</span><span class="sxs-lookup"><span data-stu-id="7823e-128">For JEA sessions, this includes important information about the **ConnectedUser**, which is the actual user who created the JEA session, as well as the **RunAsUser** which identifies the account JEA used to execute the command.</span></span>
<span data-ttu-id="7823e-129">Händelseloggarna program visas ändringar av användare, så att betyg eller skriptet och module loggning är aktiverat är avgörande för att kunna spåra ett kommando för anrop till en användare.</span><span class="sxs-lookup"><span data-stu-id="7823e-129">Application event logs will show changes being made by the RunAsUser, so having transcripts or module/script logging enabled is crucial to be able to trace a specific command invocation back to a user.</span></span>

## <a name="application-event-logs"></a><span data-ttu-id="7823e-130">Händelseloggarna program</span><span class="sxs-lookup"><span data-stu-id="7823e-130">Application event logs</span></span>

<span data-ttu-id="7823e-131">När du kör ett kommando i en session i JEA som samverkar med ett externt program eller en tjänst, kan dessa program logghändelser till sina egna loggar.</span><span class="sxs-lookup"><span data-stu-id="7823e-131">When you run a command in a JEA session that interacts with an external application or service, those applications may log events to their own event logs.</span></span>
<span data-ttu-id="7823e-132">Till skillnad från PowerShell-loggar och betyg andra mekanismer för loggning kommer inte att avbilda den anslutna användaren JEA sessionen och i stället loggas bara virtuella kör som-användaren eller grupphanterade tjänstkontot.</span><span class="sxs-lookup"><span data-stu-id="7823e-132">Unlike PowerShell logs and transcripts, other logging mechanisms will not capture the connected user of the JEA session, and will instead only log the virtual run-as user or group managed service account.</span></span>
<span data-ttu-id="7823e-133">För att fastställa vem som körde kommandot, måste du kontakta en [session betyg](#session-transcripts) eller korrelera PowerShell händelseloggar med tiden och visas i programmets händelselogg.</span><span class="sxs-lookup"><span data-stu-id="7823e-133">In order to determine who ran the command, you will need to consult a [session transcript](#session-transcripts) or correlate PowerShell event logs with the time and user shown in the application event log.</span></span>

<span data-ttu-id="7823e-134">WinRM loggen kan också hjälpa dig att korrelera körs som användare i händelseloggen för ett program med den anslutande användaren.</span><span class="sxs-lookup"><span data-stu-id="7823e-134">The WinRM log can also help you correlate run as users in an application event log with the connecting user.</span></span>
<span data-ttu-id="7823e-135">Händelse-ID **193** i den **Microsoft Windows Windows Remote Management/Operational** loggposter säkerhetsidentifierare (SID) och kontot namn för den anslutande användaren och köra som användaren varje gång en JEA sessionen har skapats.</span><span class="sxs-lookup"><span data-stu-id="7823e-135">Event ID **193** in the **Microsoft-Windows-Windows Remote Management/Operational** log records the security identifier (SID) and account name for both the connecting user and run as user every time a JEA session is created.</span></span>

## <a name="session-transcripts"></a><span data-ttu-id="7823e-136">Sessionen betyg</span><span class="sxs-lookup"><span data-stu-id="7823e-136">Session transcripts</span></span>

<span data-ttu-id="7823e-137">Om du har konfigurerat JEA för att skapa ett betyg för varje användarsession lagras en text kopia av varje användaråtgärder i den angivna mappen.</span><span class="sxs-lookup"><span data-stu-id="7823e-137">If you configured JEA to create a transcript for each user session, a text copy of every user's actions will be stored in the specified folder.</span></span>

<span data-ttu-id="7823e-138">Du hittar alla betyg kataloger genom att köra följande kommando som administratör på datorn konfigureras med JEA:</span><span class="sxs-lookup"><span data-stu-id="7823e-138">To find all transcript directories, run the following command as an administrator on the computer configured with JEA:</span></span>

```powershell
Get-PSSessionConfiguration | Where-Object { $_.TranscriptDirectory -ne $null } | Format-Table Name, TranscriptDirectory
```

<span data-ttu-id="7823e-139">Varje betyg börjar med information om den tid som en session startades vilka användare som anslöt till sessionen och vilken JEA identitet har tilldelats.</span><span class="sxs-lookup"><span data-stu-id="7823e-139">Each transcript starts with information about the time the session started, which user connected to the session, and which JEA identity was assigned to them.</span></span>

```
**********************
Windows PowerShell transcript start
Start time: 20160710144736
Username: CONTOSO\Alice
RunAs User: WinRM Virtual Users\WinRM VA_1_CONTOSO_Alice
Machine: SERVER01 (Microsoft Windows NT 10.0.14393.0)
[...]
```

<span data-ttu-id="7823e-140">I brödtexten för betyg loggas information om varje kommando som anropas av användaren.</span><span class="sxs-lookup"><span data-stu-id="7823e-140">In the body of the transcript, information is logged about each command the user invoked.</span></span>
<span data-ttu-id="7823e-141">Den exakta syntaxen för kommandot som kördes användaren är inte tillgänglig i JEA sessioner på grund av det sätt som kommandon omvandlas för PowerShell-fjärrkommunikation, men du kan fortfarande se effektiva kommandot som kördes.</span><span class="sxs-lookup"><span data-stu-id="7823e-141">The exact syntax of the command the user ran is unavailable in JEA sessions due to the way commands are transformed for PowerShell remoting, however you can still determine the effective command that was executed.</span></span>
<span data-ttu-id="7823e-142">Nedan visas ett exempel betyg kodavsnitt från en användare som kör `Get-Service Dns` i en JEA-session:</span><span class="sxs-lookup"><span data-stu-id="7823e-142">Below is an example transcript snippet from a user running `Get-Service Dns` in a JEA session:</span></span>

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

<span data-ttu-id="7823e-143">För varje kommando som en användare kör en rad ”CommandInvocation” skrivs, som beskriver cmdlet eller fungera användaren anropas.</span><span class="sxs-lookup"><span data-stu-id="7823e-143">For each command a user runs, a "CommandInvocation" line will be written, describing the cmdlet or function the user invoked.</span></span>
<span data-ttu-id="7823e-144">ParameterBindings följer varje CommandInvocation för information om varje parameter och ett värde som har angetts i kommandot.</span><span class="sxs-lookup"><span data-stu-id="7823e-144">ParameterBindings follow each CommandInvocation to tell you about each parameter and value that was supplied with the command.</span></span>
<span data-ttu-id="7823e-145">I exemplet ovan kan du se att parametern ”namn” har lämnat värdet ”Dns” för ”Get-tjänst”-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7823e-145">In the above example, you can see that the parameter "Name" was supplied the value "Dns" for the "Get-Service" cmdlet.</span></span>

<span data-ttu-id="7823e-146">Utdata från varje kommando kommer också utlösa en CommandInvocation vanligtvis ut som standard.</span><span class="sxs-lookup"><span data-stu-id="7823e-146">The output of each command will also trigger a CommandInvocation, usually to Out-Default.</span></span> <span data-ttu-id="7823e-147">InputObject Out-Default är PowerShell-objektet som returnerades från kommandot.</span><span class="sxs-lookup"><span data-stu-id="7823e-147">The InputObject of Out-Default is the PowerShell object returned from the command.</span></span>
<span data-ttu-id="7823e-148">Information om objektet skrivs ut några rader under nära frihandsbilden vad användaren skulle ha sett.</span><span class="sxs-lookup"><span data-stu-id="7823e-148">The details of that object are printed a few lines below, closely mimicking what the user would have seen.</span></span>

## <a name="see-also"></a><span data-ttu-id="7823e-149">Se även</span><span class="sxs-lookup"><span data-stu-id="7823e-149">See also</span></span>

- [<span data-ttu-id="7823e-150">Granska användaråtgärder i en JEA session</span><span class="sxs-lookup"><span data-stu-id="7823e-150">Audit user actions in a JEA session</span></span>](audit-and-report.md)
- [<span data-ttu-id="7823e-151">*PowerShell ♥ blå teamet* blogginlägg om säkerhet</span><span class="sxs-lookup"><span data-stu-id="7823e-151">*PowerShell ♥ the Blue Team* blog post on security</span></span>](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)

