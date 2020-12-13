---
ms.date: 07/10/2019
keywords: Jea, PowerShell, säkerhet
title: Granskning och rapportering av JEA
description: Granskningen hjälper dig att utvärdera att rätt personer har åtkomst till JEA-slutpunkten och att de tilldelade rollerna fortfarande är lämpliga.
ms.openlocfilehash: 2140d6b756ae38d82e4943c373e8a75beea30e28
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92500019"
---
# <a name="auditing-and-reporting-on-jea"></a><span data-ttu-id="16c58-104">Granskning och rapportering av JEA</span><span class="sxs-lookup"><span data-stu-id="16c58-104">Auditing and Reporting on JEA</span></span>

<span data-ttu-id="16c58-105">När du har distribuerat JEA måste du regelbundet granska JEA-konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="16c58-105">After you've deployed JEA, you need to regularly audit the JEA configuration.</span></span> <span data-ttu-id="16c58-106">Granskningen hjälper dig att utvärdera att rätt personer har åtkomst till JEA-slutpunkten och att de tilldelade rollerna fortfarande är lämpliga.</span><span class="sxs-lookup"><span data-stu-id="16c58-106">Auditing helps you assess that the correct people have access to the JEA endpoint and their assigned roles are still appropriate.</span></span>

## <a name="find-registered-jea-sessions-on-a-machine"></a><span data-ttu-id="16c58-107">Hitta registrerade JEA-sessioner på en dator</span><span class="sxs-lookup"><span data-stu-id="16c58-107">Find registered JEA sessions on a machine</span></span>

<span data-ttu-id="16c58-108">Använd cmdleten [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) för att kontrol lera vilka Jea-sessioner som har registrerats på en dator.</span><span class="sxs-lookup"><span data-stu-id="16c58-108">To check which JEA sessions are registered on a machine, use the [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.</span></span>

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

<span data-ttu-id="16c58-109">De effektiva rättigheterna för slut punkten visas i egenskapen **behörighet** .</span><span class="sxs-lookup"><span data-stu-id="16c58-109">The effective rights for the endpoint are listed in the **Permission** property.</span></span> <span data-ttu-id="16c58-110">Dessa användare har behörighet att ansluta till JEA-slutpunkten.</span><span class="sxs-lookup"><span data-stu-id="16c58-110">These users have the right to connect to the JEA endpoint.</span></span> <span data-ttu-id="16c58-111">Men de roller och kommandon som de har åtkomst till bestäms av egenskapen **RoleDefinitions** i den [konfigurations fil för sessionen](session-configurations.md) som användes för att registrera slut punkten.</span><span class="sxs-lookup"><span data-stu-id="16c58-111">However, the roles and commands they have access to is determined by the **RoleDefinitions** property in the [session configuration file](session-configurations.md) that was used to register the endpoint.</span></span> <span data-ttu-id="16c58-112">Expandera egenskapen **RoleDefinitions** för att utvärdera roll mappningarna i en registrerad Jea-slutpunkt.</span><span class="sxs-lookup"><span data-stu-id="16c58-112">Expand the **RoleDefinitions** property to evaluate the role mappings in a registered JEA endpoint.</span></span>

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{
  Name = 'Role Capabilities'
  Expression = { $_.Value.RoleCapabilities }
}
```

## <a name="find-available-role-capabilities-on-the-machine"></a><span data-ttu-id="16c58-113">Hitta tillgängliga roll funktioner på datorn</span><span class="sxs-lookup"><span data-stu-id="16c58-113">Find available role capabilities on the machine</span></span>

<span data-ttu-id="16c58-114">JEA hämtar roll funktioner från `.psrc` filerna som lagras i mappen **RoleCapabilities** i en PowerShell-modul.</span><span class="sxs-lookup"><span data-stu-id="16c58-114">JEA gets role capabilities from the `.psrc` files stored in the **RoleCapabilities** folder inside a PowerShell module.</span></span> <span data-ttu-id="16c58-115">Följande funktion hittar alla roll funktioner som är tillgängliga på en dator.</span><span class="sxs-lookup"><span data-stu-id="16c58-115">The following function finds all role capabilities available on a computer.</span></span>

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
> <span data-ttu-id="16c58-116">Ordningen på resultaten från den här funktionen är inte nödvändigt vis den ordning som roll funktionerna ska väljas i om flera roll funktioner delar samma namn.</span><span class="sxs-lookup"><span data-stu-id="16c58-116">The order of results from this function is not necessarily the order in which the role capabilities will be selected if multiple role capabilities share the same name.</span></span>

## <a name="check-effective-rights-for-a-specific-user"></a><span data-ttu-id="16c58-117">Kontrol lera gällande rättigheter för en speciell användare</span><span class="sxs-lookup"><span data-stu-id="16c58-117">Check effective rights for a specific user</span></span>

<span data-ttu-id="16c58-118">Cmdlet [: en get-PSSessionCapability](/powershell/module/microsoft.powershell.core/Get-PSSessionCapability) räknar upp alla kommandon som är tillgängliga på en Jea-slutpunkt baserat på användarens grupp medlemskap.</span><span class="sxs-lookup"><span data-stu-id="16c58-118">The [Get-PSSessionCapability](/powershell/module/microsoft.powershell.core/Get-PSSessionCapability) cmdlet enumerates all the commands available on a JEA endpoint based on a user's group memberships.</span></span>
<span data-ttu-id="16c58-119">Resultatet av `Get-PSSessionCapability` är identiskt med den angivna användaren som körs `Get-Command -CommandType All` i en Jea-session.</span><span class="sxs-lookup"><span data-stu-id="16c58-119">The output of `Get-PSSessionCapability` is identical to that of the specified user running `Get-Command -CommandType All` in a JEA session.</span></span>

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

<span data-ttu-id="16c58-120">Om användarna inte är permanenta medlemmar i grupper som skulle ge dem ytterligare JEA-rättigheter kanske denna cmdlet inte återspeglar dessa extra behörigheter.</span><span class="sxs-lookup"><span data-stu-id="16c58-120">If your users aren't permanent members of groups that would grant them additional JEA rights, this cmdlet may not reflect those extra permissions.</span></span> <span data-ttu-id="16c58-121">Detta inträffar när du använder just-in-Time-hanterings system för att tillåta användare att tillfälligt tillhöra en säkerhets grupp.</span><span class="sxs-lookup"><span data-stu-id="16c58-121">This happens when using just-in-time privileged access management systems to allow users to temporarily belong to a security group.</span></span> <span data-ttu-id="16c58-122">Utvärdera noggrant mappningen av användare till roller och funktioner för att säkerställa att användarna bara får den åtkomst nivå som krävs för att utföra sina jobb.</span><span class="sxs-lookup"><span data-stu-id="16c58-122">Carefully evaluate the mapping of users to roles and capabilities to ensure that users only get the level of access needed to do their jobs successfully.</span></span>

## <a name="powershell-event-logs"></a><span data-ttu-id="16c58-123">PowerShell-händelseloggar</span><span class="sxs-lookup"><span data-stu-id="16c58-123">PowerShell event logs</span></span>

<span data-ttu-id="16c58-124">Om du har aktiverat modul-eller skript Blocks loggning i systemet kan du se händelser i händelse loggarna i Windows för varje kommando som en användare kör i en JEA-session.</span><span class="sxs-lookup"><span data-stu-id="16c58-124">If you enabled module or script block logging on the system, you can see events in the Windows event logs for each command a user runs in a JEA session.</span></span> <span data-ttu-id="16c58-125">Du hittar de här händelserna genom att öppna **Microsoft-Windows-PowerShell/Operations-** händelseloggen och leta efter händelser med händelse-ID **4104**.</span><span class="sxs-lookup"><span data-stu-id="16c58-125">To find these events, open **Microsoft-Windows-PowerShell/Operational** event log and look for events with event ID **4104**.</span></span>

<span data-ttu-id="16c58-126">Varje post i händelse loggen innehåller information om sessionen där kommandot kördes.</span><span class="sxs-lookup"><span data-stu-id="16c58-126">Each event log entry includes information about the session in which the command was run.</span></span> <span data-ttu-id="16c58-127">För JEA-sessioner innehåller händelsen information om **ConnectedUser** och **RunAsUser**.</span><span class="sxs-lookup"><span data-stu-id="16c58-127">For JEA sessions, the event includes information about the **ConnectedUser** and the **RunAsUser**.</span></span> <span data-ttu-id="16c58-128">**ConnectedUser** är den faktiska användaren som skapade Jea-sessionen.</span><span class="sxs-lookup"><span data-stu-id="16c58-128">The **ConnectedUser** is the actual user who created the JEA session.</span></span> <span data-ttu-id="16c58-129">**RunAsUser** är det konto-Jea som används för att köra kommandot.</span><span class="sxs-lookup"><span data-stu-id="16c58-129">The **RunAsUser** is the account JEA used to execute the command.</span></span>

<span data-ttu-id="16c58-130">Program händelse loggar visar ändringar som görs av **RunAsUser**.</span><span class="sxs-lookup"><span data-stu-id="16c58-130">Application event logs show changes being made by the **RunAsUser**.</span></span> <span data-ttu-id="16c58-131">Därför krävs att modul-och skript loggning är aktiverat för att spåra ett särskilt kommando anrop tillbaka till **ConnectedUser**.</span><span class="sxs-lookup"><span data-stu-id="16c58-131">So having module and script logging enabled is required to trace a specific command invocation back to the **ConnectedUser**.</span></span>

## <a name="application-event-logs"></a><span data-ttu-id="16c58-132">Program händelse loggar</span><span class="sxs-lookup"><span data-stu-id="16c58-132">Application event logs</span></span>

<span data-ttu-id="16c58-133">Kommandon som körs i en JEA-session som interagerar med externa program eller tjänster kan logga händelser till sina egna händelse loggar.</span><span class="sxs-lookup"><span data-stu-id="16c58-133">Commands run in a JEA session that interact with external applications or services may log events to their own event logs.</span></span> <span data-ttu-id="16c58-134">Till skillnad från PowerShell-loggar och avskrifter fångar inte andra loggnings metoder den anslutna användaren av JEA-sessionen.</span><span class="sxs-lookup"><span data-stu-id="16c58-134">Unlike PowerShell logs and transcripts, other logging mechanisms don't capture the connected user of the JEA session.</span></span> <span data-ttu-id="16c58-135">I stället loggar de här programmen enbart den virtuella kör som-användaren.</span><span class="sxs-lookup"><span data-stu-id="16c58-135">Instead, those applications only log the virtual run-as user.</span></span>
<span data-ttu-id="16c58-136">För att fastställa vem som körde kommandot måste du kontakta en [session avskrift](#session-transcripts) eller korrelera PowerShell-händelseloggen med den tid och användare som visas i program händelse loggen.</span><span class="sxs-lookup"><span data-stu-id="16c58-136">To determine who ran the command, you need to consult a [session transcript](#session-transcripts) or correlate PowerShell event logs with the time and user shown in the application event log.</span></span>

<span data-ttu-id="16c58-137">WinRM-loggen kan också hjälpa dig att korrelera kör som-användare till den anslutande användaren i en program händelse logg.</span><span class="sxs-lookup"><span data-stu-id="16c58-137">The WinRM log can also help you correlate run-as users to the connecting user in an application event log.</span></span> <span data-ttu-id="16c58-138">Händelse-ID **193** i **Microsoft-Windows-Windows-fjärrhantering/drift** logg registrerar säkerhets identifieraren (sid) och konto namnet för både den anslutna användaren och kör som-användare för varje ny Jea-session.</span><span class="sxs-lookup"><span data-stu-id="16c58-138">Event ID **193** in the **Microsoft-Windows-Windows Remote Management/Operational** log records the security identifier (SID) and account name for both the connecting user and run as user for every new JEA session.</span></span>

## <a name="session-transcripts"></a><span data-ttu-id="16c58-139">Avskrifter för session</span><span class="sxs-lookup"><span data-stu-id="16c58-139">Session transcripts</span></span>

<span data-ttu-id="16c58-140">Om du har konfigurerat JEA för att skapa en avskrift för varje användarsession lagras en text kopia av varje användares åtgärder i den angivna mappen.</span><span class="sxs-lookup"><span data-stu-id="16c58-140">If you configured JEA to create a transcript for each user session, a text copy of every user's actions are stored in the specified folder.</span></span>

<span data-ttu-id="16c58-141">Följande kommando (som administratör) hittar alla avskrifts kataloger.</span><span class="sxs-lookup"><span data-stu-id="16c58-141">The following command (as an administrator) finds all transcript directories.</span></span>

```powershell
Get-PSSessionConfiguration |
  Where-Object { $_.TranscriptDirectory -ne $null } |
    Format-Table Name, TranscriptDirectory
```

<span data-ttu-id="16c58-142">Varje avskrift börjar med information om tiden då sessionen startades, vilken användare anslöt till sessionen och vilken JEA identitet som har tilldelats dem.</span><span class="sxs-lookup"><span data-stu-id="16c58-142">Each transcript starts with information about the time the session started, which user connected to the session, and which JEA identity was assigned to them.</span></span>

```
**********************
Windows PowerShell transcript start
Start time: 20160710144736
Username: CONTOSO\Alice
RunAs User: WinRM Virtual Users\WinRM VA_1_CONTOSO_Alice
Machine: SERVER01 (Microsoft Windows NT 10.0.14393.0)
[...]
```

<span data-ttu-id="16c58-143">Bröd texten i avskriften innehåller information om varje kommando som användaren anropade.</span><span class="sxs-lookup"><span data-stu-id="16c58-143">The body of the transcript contains information about each command the user invoked.</span></span> <span data-ttu-id="16c58-144">Den exakta syntaxen för kommandot som används är inte tillgänglig i JEA-sessioner på grund av hur kommandon omvandlas för PowerShell-fjärrkommunikation.</span><span class="sxs-lookup"><span data-stu-id="16c58-144">The exact syntax of the command used is unavailable in JEA sessions because of the way commands are transformed for PowerShell remoting.</span></span> <span data-ttu-id="16c58-145">Du kan dock fortfarande bestämma det effektiva kommando som kördes.</span><span class="sxs-lookup"><span data-stu-id="16c58-145">However, you can still determine the effective command that was executed.</span></span> <span data-ttu-id="16c58-146">Nedan visas ett exempel på en avskrifts-kodfragment från en användare `Get-Service Dns` som körs i en Jea-session:</span><span class="sxs-lookup"><span data-stu-id="16c58-146">Below is an example transcript snippet from a user running `Get-Service Dns` in a JEA session:</span></span>

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

<span data-ttu-id="16c58-147">En **CommandInvocation** -rad skrivs för varje kommando som en användare kör.</span><span class="sxs-lookup"><span data-stu-id="16c58-147">A **CommandInvocation** line is written for each command a user runs.</span></span> <span data-ttu-id="16c58-148">**ParameterBindings** spelar in varje parameter och värde som medföljer kommandot.</span><span class="sxs-lookup"><span data-stu-id="16c58-148">**ParameterBindings** record each parameter and value supplied with the command.</span></span> <span data-ttu-id="16c58-149">I det tidigare exemplet kan du se att parameter **namnet** angavs med värdet **DNS** för `Get-Service` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="16c58-149">In the previous example, you can see that the parameter **Name** was supplied the with value **Dns** for the `Get-Service` cmdlet.</span></span>

<span data-ttu-id="16c58-150">Utdata från varje kommando utlöser även en **CommandInvocation**, vanligt vis till `Out-Default` .</span><span class="sxs-lookup"><span data-stu-id="16c58-150">The output of each command also triggers a **CommandInvocation**, usually to `Out-Default`.</span></span> <span data-ttu-id="16c58-151">**InputObject** för `Out-Default` är PowerShell-objektet som returnerades från kommandot.</span><span class="sxs-lookup"><span data-stu-id="16c58-151">The **InputObject** of `Out-Default` is the PowerShell object returned from the command.</span></span> <span data-ttu-id="16c58-152">Informationen om objektet skrivs ut några rader nedan, och mimicking vad användaren skulle ha sett.</span><span class="sxs-lookup"><span data-stu-id="16c58-152">The details of that object are printed a few lines below, closely mimicking what the user would have seen.</span></span>

## <a name="see-also"></a><span data-ttu-id="16c58-153">Se även</span><span class="sxs-lookup"><span data-stu-id="16c58-153">See also</span></span>

[<span data-ttu-id="16c58-154">*PowerShell ♥ det blå teamets* blogg inlägg om säkerhet</span><span class="sxs-lookup"><span data-stu-id="16c58-154">*PowerShell ♥ the Blue Team* blog post on security</span></span>](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
