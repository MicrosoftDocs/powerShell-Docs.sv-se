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
# <a name="auditing-and-reporting-on-jea"></a><span data-ttu-id="fe7fe-103">Granskning och rapportering i JEA</span><span class="sxs-lookup"><span data-stu-id="fe7fe-103">Auditing and Reporting on JEA</span></span>

<span data-ttu-id="fe7fe-104">När du har distribuerat JEA kan behöva du granska regelbundet JEA-konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="fe7fe-104">After you've deployed JEA, you need to regularly audit the JEA configuration.</span></span> <span data-ttu-id="fe7fe-105">Granskning kan utvärdera du att rätt personer har åtkomst till JEA-slutpunkt och deras tilldelade roller är fortfarande lämpliga.</span><span class="sxs-lookup"><span data-stu-id="fe7fe-105">Auditing helps you assess that the correct people have access to the JEA endpoint and their assigned roles are still appropriate.</span></span>

## <a name="find-registered-jea-sessions-on-a-machine"></a><span data-ttu-id="fe7fe-106">Hitta registrerade JEA-sessioner på en dator</span><span class="sxs-lookup"><span data-stu-id="fe7fe-106">Find registered JEA sessions on a machine</span></span>

<span data-ttu-id="fe7fe-107">Du kan kontrollera vilka JEA-sessioner är registrerade på en dator genom att använda den [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fe7fe-107">To check which JEA sessions are registered on a machine, use the [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.</span></span>

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

<span data-ttu-id="fe7fe-108">De effektiva rättigheterna för slutpunkten visas i den **behörighet** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="fe7fe-108">The effective rights for the endpoint are listed in the **Permission** property.</span></span> <span data-ttu-id="fe7fe-109">Dessa användare har behörighet att ansluta till JEA-slutpunkt.</span><span class="sxs-lookup"><span data-stu-id="fe7fe-109">These users have the right to connect to the JEA endpoint.</span></span> <span data-ttu-id="fe7fe-110">Men de roller och kommandon som de har åtkomst till bestäms av den **RoleDefinitions** -egenskapen i den [session konfigurationsfilen](session-configurations.md) som användes för att registrera slutpunkten.</span><span class="sxs-lookup"><span data-stu-id="fe7fe-110">However, the roles and commands they have access to is determined by the **RoleDefinitions** property in the [session configuration file](session-configurations.md) that was used to register the endpoint.</span></span> <span data-ttu-id="fe7fe-111">Expandera den **RoleDefinitions** egenskapen att utvärdera rollen mappningarna i en registrerad JEA-slutpunkt.</span><span class="sxs-lookup"><span data-stu-id="fe7fe-111">Expand the **RoleDefinitions** property to evaluate the role mappings in a registered JEA endpoint.</span></span>

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{
  Name = 'Role Capabilities'
  Expression = { $_.Value.RoleCapabilities }
}
```

## <a name="find-available-role-capabilities-on-the-machine"></a><span data-ttu-id="fe7fe-112">Hitta tillgängliga rollfunktioner på datorn</span><span class="sxs-lookup"><span data-stu-id="fe7fe-112">Find available role capabilities on the machine</span></span>

<span data-ttu-id="fe7fe-113">JEA hämtar rollfunktioner från den `.psrc` filer som lagras i den **RoleCapabilities** mapp inuti en PowerShell-modul.</span><span class="sxs-lookup"><span data-stu-id="fe7fe-113">JEA gets role capabilities from the `.psrc` files stored in the **RoleCapabilities** folder inside a PowerShell module.</span></span> <span data-ttu-id="fe7fe-114">Följande funktion hittar alla rollfunktioner på en dator.</span><span class="sxs-lookup"><span data-stu-id="fe7fe-114">The following function finds all role capabilities available on a computer.</span></span>

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
> <span data-ttu-id="fe7fe-115">Ordningen på resultaten från den här funktionen är inte nödvändigtvis ordningen som rollfunktioner väljs om flera rollfunktioner delar samma namn.</span><span class="sxs-lookup"><span data-stu-id="fe7fe-115">The order of results from this function is not necessarily the order in which the role capabilities will be selected if multiple role capabilities share the same name.</span></span>

## <a name="check-effective-rights-for-a-specific-user"></a><span data-ttu-id="fe7fe-116">Kontrollera effektiva rättigheterna för en viss användare</span><span class="sxs-lookup"><span data-stu-id="fe7fe-116">Check effective rights for a specific user</span></span>

<span data-ttu-id="fe7fe-117">Den [Get-PSSessionCapability](/powershell/module/microsoft.powershell.core/Get-PSSessionCapability) cmdlet räknar upp alla kommandon som är tillgängliga på en JEA-slutpunkt som baseras på en användares gruppmedlemskap.</span><span class="sxs-lookup"><span data-stu-id="fe7fe-117">The [Get-PSSessionCapability](/powershell/module/microsoft.powershell.core/Get-PSSessionCapability) cmdlet enumerates all the commands available on a JEA endpoint based on a user's group memberships.</span></span>
<span data-ttu-id="fe7fe-118">Utdata från `Get-PSSessionCapability` är identisk med den angivna användaren som kör `Get-Command -CommandType All` i en JEA-session.</span><span class="sxs-lookup"><span data-stu-id="fe7fe-118">The output of `Get-PSSessionCapability` is identical to that of the specified user running `Get-Command -CommandType All` in a JEA session.</span></span>

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

<span data-ttu-id="fe7fe-119">Om användarna inte är permanenta medlemmar i grupper som beviljar dem ytterligare JEA rättigheter, kan denna cmdlet inte återspeglar de extra behörigheterna.</span><span class="sxs-lookup"><span data-stu-id="fe7fe-119">If your users aren't permanent members of groups that would grant them additional JEA rights, this cmdlet may not reflect those extra permissions.</span></span> <span data-ttu-id="fe7fe-120">Detta inträffar när du använder just-in-time-privilegierad åtkomst hanteringssystem så att användarna kan tillfälligt tillhör en säkerhetsgrupp.</span><span class="sxs-lookup"><span data-stu-id="fe7fe-120">This happens when using just-in-time privileged access management systems to allow users to temporarily belong to a security group.</span></span> <span data-ttu-id="fe7fe-121">Utvärdera noggrant mappning av användare till roller och funktioner så att användare bara får åtkomstnivån som behövs för att utföra sitt arbete.</span><span class="sxs-lookup"><span data-stu-id="fe7fe-121">Carefully evaluate the mapping of users to roles and capabilities to ensure that users only get the level of access needed to do their jobs successfully.</span></span>

## <a name="powershell-event-logs"></a><span data-ttu-id="fe7fe-122">PowerShell-händelseloggar</span><span class="sxs-lookup"><span data-stu-id="fe7fe-122">PowerShell event logs</span></span>

<span data-ttu-id="fe7fe-123">Om du har aktiverat modulen eller skript blockera inloggning systemet kan du se händelser i Windows-händelseloggar för varje kommando som en användare kör i en JEA-session.</span><span class="sxs-lookup"><span data-stu-id="fe7fe-123">If you enabled module or script block logging on the system, you can see events in the Windows event logs for each command a user runs in a JEA session.</span></span> <span data-ttu-id="fe7fe-124">Du hittar dessa händelser genom att öppna **Microsoft-Windows-PowerShell/Operational** händelselogg och leta efter händelser med händelse-ID **4104**.</span><span class="sxs-lookup"><span data-stu-id="fe7fe-124">To find these events, open **Microsoft-Windows-PowerShell/Operational** event log and look for events with event ID **4104**.</span></span>

<span data-ttu-id="fe7fe-125">Varje post i händelseloggen innehåller information om sessionen där kommandot kördes.</span><span class="sxs-lookup"><span data-stu-id="fe7fe-125">Each event log entry includes information about the session in which the command was run.</span></span> <span data-ttu-id="fe7fe-126">Om JEA-sessioner, händelsen innehåller information om den **ConnectedUser** och **användare**.</span><span class="sxs-lookup"><span data-stu-id="fe7fe-126">For JEA sessions, the event includes information about the **ConnectedUser** and the **RunAsUser**.</span></span> <span data-ttu-id="fe7fe-127">Den **ConnectedUser** är den faktiska användaren som skapade JEA-sessionen.</span><span class="sxs-lookup"><span data-stu-id="fe7fe-127">The **ConnectedUser** is the actual user who created the JEA session.</span></span> <span data-ttu-id="fe7fe-128">Den **användare** är kontot JEA används för att köra kommandot.</span><span class="sxs-lookup"><span data-stu-id="fe7fe-128">The **RunAsUser** is the account JEA used to execute the command.</span></span>

<span data-ttu-id="fe7fe-129">Händelseloggarna för programmet visa ändringar som görs av den **användare**.</span><span class="sxs-lookup"><span data-stu-id="fe7fe-129">Application event logs show changes being made by the **RunAsUser**.</span></span> <span data-ttu-id="fe7fe-130">Så att ha modulen och skript loggning är aktiverat krävs för att spåra ett visst kommandoanrop tillbaka till den **ConnectedUser**.</span><span class="sxs-lookup"><span data-stu-id="fe7fe-130">So having module and script logging enabled is required to trace a specific command invocation back to the **ConnectedUser**.</span></span>

## <a name="application-event-logs"></a><span data-ttu-id="fe7fe-131">Händelseloggarna för programmet</span><span class="sxs-lookup"><span data-stu-id="fe7fe-131">Application event logs</span></span>

<span data-ttu-id="fe7fe-132">Kommandon körs i en JEA-session som interagerar med externa program eller tjänster kan logga händelser till sina egna händelseloggar.</span><span class="sxs-lookup"><span data-stu-id="fe7fe-132">Commands run in a JEA session that interact with external applications or services may log events to their own event logs.</span></span> <span data-ttu-id="fe7fe-133">Till skillnad från PowerShell loggar och avskrifter avbilda inte andra mekanismer som loggning anslutna användaren JEA-sessionen.</span><span class="sxs-lookup"><span data-stu-id="fe7fe-133">Unlike PowerShell logs and transcripts, other logging mechanisms don't capture the connected user of the JEA session.</span></span> <span data-ttu-id="fe7fe-134">I stället logga programmen endast virtuella kör som-användaren.</span><span class="sxs-lookup"><span data-stu-id="fe7fe-134">Instead, those applications only log the virtual run-as user.</span></span>
<span data-ttu-id="fe7fe-135">För att fastställa vem som körde kommandot, som du behöver läsa en [session avskrift](#session-transcripts) eller korrelera PowerShell händelseloggar med tiden och användaren visas i programmets händelselogg.</span><span class="sxs-lookup"><span data-stu-id="fe7fe-135">To determine who ran the command, you need to consult a [session transcript](#session-transcripts) or correlate PowerShell event logs with the time and user shown in the application event log.</span></span>

<span data-ttu-id="fe7fe-136">WinRM-loggen kan också hjälpa dig att korrelera kör som-användare till den anslutande användaren i händelseloggen för ett program.</span><span class="sxs-lookup"><span data-stu-id="fe7fe-136">The WinRM log can also help you correlate run-as users to the connecting user in an application event log.</span></span> <span data-ttu-id="fe7fe-137">Händelse-ID **193** i den **Microsoft-Windows-Windows Remote Management/Operational** log registrerar säkerhetsidentifierare (SID) och namnet på tjänstkontot för både den anslutande användaren och kör som användare för varje ny JEA sessionen.</span><span class="sxs-lookup"><span data-stu-id="fe7fe-137">Event ID **193** in the **Microsoft-Windows-Windows Remote Management/Operational** log records the security identifier (SID) and account name for both the connecting user and run as user for every new JEA session.</span></span>

## <a name="session-transcripts"></a><span data-ttu-id="fe7fe-138">Sessionen avskrifter</span><span class="sxs-lookup"><span data-stu-id="fe7fe-138">Session transcripts</span></span>

<span data-ttu-id="fe7fe-139">Om du har konfigurerat JEA för att skapa en avskrift för varje användarsession lagras en Textversion av varje användares åtgärder i den angivna mappen.</span><span class="sxs-lookup"><span data-stu-id="fe7fe-139">If you configured JEA to create a transcript for each user session, a text copy of every user's actions are stored in the specified folder.</span></span>

<span data-ttu-id="fe7fe-140">Följande kommando (som administratör) hittar alla funktionerna för avskrift kataloger.</span><span class="sxs-lookup"><span data-stu-id="fe7fe-140">The following command (as an administrator) finds all transcript directories.</span></span>

```powershell
Get-PSSessionConfiguration |
  Where-Object { $_.TranscriptDirectory -ne $null } |
    Format-Table Name, TranscriptDirectory
```

<span data-ttu-id="fe7fe-141">Varje avskrift börjar med information om den tid som sessionen igång, vilka användare som är ansluten till sessionen och vilken JEA-identitet har tilldelats.</span><span class="sxs-lookup"><span data-stu-id="fe7fe-141">Each transcript starts with information about the time the session started, which user connected to the session, and which JEA identity was assigned to them.</span></span>

```
**********************
Windows PowerShell transcript start
Start time: 20160710144736
Username: CONTOSO\Alice
RunAs User: WinRM Virtual Users\WinRM VA_1_CONTOSO_Alice
Machine: SERVER01 (Microsoft Windows NT 10.0.14393.0)
[...]
```

<span data-ttu-id="fe7fe-142">Brödtexten i avskriften innehåller information om varje kommando som anropas av användaren.</span><span class="sxs-lookup"><span data-stu-id="fe7fe-142">The body of the transcript contains information about each command the user invoked.</span></span> <span data-ttu-id="fe7fe-143">Den exakta syntaxen för kommandot är inte tillgänglig i JEA-sessioner på grund av sättet kommandon omvandlas för PowerShell-fjärrkommunikation.</span><span class="sxs-lookup"><span data-stu-id="fe7fe-143">The exact syntax of the command used is unavailable in JEA sessions because of the way commands are transformed for PowerShell remoting.</span></span> <span data-ttu-id="fe7fe-144">Du kan dock fortfarande kontrollera effektiva kommandot som kördes.</span><span class="sxs-lookup"><span data-stu-id="fe7fe-144">However, you can still determine the effective command that was executed.</span></span> <span data-ttu-id="fe7fe-145">Nedan visas ett exempel avskrift kodavsnitt från en användare som kör `Get-Service Dns` i en JEA-session:</span><span class="sxs-lookup"><span data-stu-id="fe7fe-145">Below is an example transcript snippet from a user running `Get-Service Dns` in a JEA session:</span></span>

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

<span data-ttu-id="fe7fe-146">En **CommandInvocation** rad är avsedd för varje kommando som en användare kör.</span><span class="sxs-lookup"><span data-stu-id="fe7fe-146">A **CommandInvocation** line is written for each command a user runs.</span></span> <span data-ttu-id="fe7fe-147">**ParameterBindings** registrera varje parametern och värdet som angetts i kommandot.</span><span class="sxs-lookup"><span data-stu-id="fe7fe-147">**ParameterBindings** record each parameter and value supplied with the command.</span></span> <span data-ttu-id="fe7fe-148">I exemplet ovan kan du se att parametern **namn** har angetts i med värdet **Dns** för den `Get-Service` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fe7fe-148">In the previous example, you can see that the parameter **Name** was supplied the with value **Dns** for the `Get-Service` cmdlet.</span></span>

<span data-ttu-id="fe7fe-149">Utdata för var och en kommandot också utlösare en **CommandInvocation**, vanligtvis i `Out-Default`.</span><span class="sxs-lookup"><span data-stu-id="fe7fe-149">The output of each command also triggers a **CommandInvocation**, usually to `Out-Default`.</span></span> <span data-ttu-id="fe7fe-150">Den **InputObject** av `Out-Default` är PowerShell-objektet som returnerades från kommandot.</span><span class="sxs-lookup"><span data-stu-id="fe7fe-150">The **InputObject** of `Out-Default` is the PowerShell object returned from the command.</span></span> <span data-ttu-id="fe7fe-151">Information om objektet skrivs ut några rader under nära frihandsbilden vad användaren skulle ha sett.</span><span class="sxs-lookup"><span data-stu-id="fe7fe-151">The details of that object are printed a few lines below, closely mimicking what the user would have seen.</span></span>

## <a name="see-also"></a><span data-ttu-id="fe7fe-152">Se även</span><span class="sxs-lookup"><span data-stu-id="fe7fe-152">See also</span></span>

[<span data-ttu-id="fe7fe-153">*PowerShell ♥ blå teamet* blogginlägg om säkerhet</span><span class="sxs-lookup"><span data-stu-id="fe7fe-153">*PowerShell ♥ the Blue Team* blog post on security</span></span>](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
