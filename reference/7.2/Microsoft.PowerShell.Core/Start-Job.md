---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/start-job?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Job
ms.openlocfilehash: 491292253578f287940490bad198698fc4b87e37
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709984"
---
# <span data-ttu-id="23271-102">Start-Job</span><span class="sxs-lookup"><span data-stu-id="23271-102">Start-Job</span></span>

## <span data-ttu-id="23271-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="23271-103">SYNOPSIS</span></span>
<span data-ttu-id="23271-104">Startar ett PowerShell-bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="23271-104">Starts a PowerShell background job.</span></span>

## <span data-ttu-id="23271-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="23271-105">SYNTAX</span></span>

### <span data-ttu-id="23271-106">ComputerName (standard)</span><span class="sxs-lookup"><span data-stu-id="23271-106">ComputerName (Default)</span></span>

```
Start-Job [-Name <String>] [-ScriptBlock] <ScriptBlock> [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>]
 [-WorkingDirectory <String>] [-RunAs32] [-PSVersion <Version>] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="23271-107">DefinitionName</span><span class="sxs-lookup"><span data-stu-id="23271-107">DefinitionName</span></span>

```
Start-Job [-DefinitionName] <String> [[-DefinitionPath] <String>] [[-Type] <String>]
 [-WorkingDirectory <String>] [<CommonParameters>]
```

### <span data-ttu-id="23271-108">FilePathComputerName</span><span class="sxs-lookup"><span data-stu-id="23271-108">FilePathComputerName</span></span>

```
Start-Job [-Name <String>] [-Credential <PSCredential>] [-FilePath] <String>
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>]
 [-WorkingDirectory <String>] [-RunAs32] [-PSVersion <Version>] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="23271-109">LiteralFilePathComputerName</span><span class="sxs-lookup"><span data-stu-id="23271-109">LiteralFilePathComputerName</span></span>

```
Start-Job [-Name <String>] [-Credential <PSCredential>] -LiteralPath <String>
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>]
 [-WorkingDirectory <String>] [-RunAs32] [-PSVersion <Version>] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

## <span data-ttu-id="23271-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="23271-110">DESCRIPTION</span></span>

<span data-ttu-id="23271-111">`Start-Job`Cmdleten startar ett PowerShell-bakgrunds jobb på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="23271-111">The `Start-Job` cmdlet starts a PowerShell background job on the local computer.</span></span>

<span data-ttu-id="23271-112">Ett PowerShell-bakgrunds jobb kör ett kommando utan att interagera med den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="23271-112">A PowerShell background job runs a command without interacting with the current session.</span></span> <span data-ttu-id="23271-113">När du startar ett bakgrunds jobb returnerar ett Job-objekt omedelbart, även om jobbet tar lång tid att slutföra.</span><span class="sxs-lookup"><span data-stu-id="23271-113">When you start a background job, a job object returns immediately, even if the job takes an extended time to finish.</span></span> <span data-ttu-id="23271-114">Du kan fortsätta att arbeta i sessionen utan avbrott medan jobbet körs.</span><span class="sxs-lookup"><span data-stu-id="23271-114">You can continue to work in the session without interruption while the job runs.</span></span>

<span data-ttu-id="23271-115">Jobbobjektet innehåller användbar information om jobbet, men det innehåller inte jobb resultatet.</span><span class="sxs-lookup"><span data-stu-id="23271-115">The job object contains useful information about the job, but it doesn't contain the job results.</span></span>
<span data-ttu-id="23271-116">När jobbet har slutförts använder du `Receive-Job` cmdleten för att hämta resultatet av jobbet.</span><span class="sxs-lookup"><span data-stu-id="23271-116">When the job finishes, use the `Receive-Job` cmdlet to get the results of the job.</span></span> <span data-ttu-id="23271-117">Mer information om bakgrunds jobb finns [about_Jobs](./About/about_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="23271-117">For more information about background jobs, see [about_Jobs](./About/about_Jobs.md).</span></span>

<span data-ttu-id="23271-118">Om du vill köra ett bakgrunds jobb på en fjärrdator använder du parametern **AsJob** som är tillgänglig på många cmdletar eller använder `Invoke-Command` cmdleten för att köra ett `Start-Job` kommando på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="23271-118">To run a background job on a remote computer, use the **AsJob** parameter that is available on many cmdlets, or use the `Invoke-Command` cmdlet to run a `Start-Job` command on the remote computer.</span></span> <span data-ttu-id="23271-119">Mer information finns i [about_Remote_Jobs](./About/about_Remote_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="23271-119">For more information, see [about_Remote_Jobs](./About/about_Remote_Jobs.md).</span></span>

<span data-ttu-id="23271-120">Från och med PowerShell 3,0 `Start-Job` kan instanser av anpassade jobb typer startas, till exempel schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="23271-120">Starting in PowerShell 3.0, `Start-Job` can start instances of custom job types, such as scheduled jobs.</span></span> <span data-ttu-id="23271-121">Information om hur du använder `Start-Job` för att starta jobb med anpassade typer finns i hjälp dokumenten för funktionen jobb typ.</span><span class="sxs-lookup"><span data-stu-id="23271-121">For information about how to use `Start-Job` to start jobs with custom types, see the help documents for the job type feature.</span></span>

<span data-ttu-id="23271-122">Från och med PowerShell 6,0 kan du starta jobb med `&` bakgrunds operatorn et ().</span><span class="sxs-lookup"><span data-stu-id="23271-122">Beginning in PowerShell 6.0, you can start jobs using the ampersand (`&`) background operator.</span></span> <span data-ttu-id="23271-123">Bakgrunds operatorns funktioner liknar `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="23271-123">The functionality of the background operator is similar to `Start-Job`.</span></span> <span data-ttu-id="23271-124">Båda metoderna för att starta ett jobb skapar ett **PSRemotingJob** Job-objekt.</span><span class="sxs-lookup"><span data-stu-id="23271-124">Both methods to start a job create a **PSRemotingJob** job object.</span></span> <span data-ttu-id="23271-125">Mer information om hur du använder et-tecknet ( `&` ) finns [about_Operators](./about/about_operators.md#background-operator-).</span><span class="sxs-lookup"><span data-stu-id="23271-125">For more information about using the ampersand (`&`), see [about_Operators](./about/about_operators.md#background-operator-).</span></span>

<span data-ttu-id="23271-126">PowerShell 7 introducerade parametern **WorkingDirectory** som anger ett bakgrunds jobbs ursprungliga arbets katalog.</span><span class="sxs-lookup"><span data-stu-id="23271-126">PowerShell 7 introduced the **WorkingDirectory** parameter that specifies a background job's initial working directory.</span></span> <span data-ttu-id="23271-127">Om parametern inte anges används `Start-Job` den aktuella arbets katalogen för den anropare som startade jobbet som standard.</span><span class="sxs-lookup"><span data-stu-id="23271-127">If the parameter isn't specified, `Start-Job` defaults to the current working directory of the caller that started the job.</span></span>

> [!NOTE]
> <span data-ttu-id="23271-128">Att skapa ett bakgrunds jobb utanför processen med `Start-Job` stöds inte i scenariot där PowerShell finns i andra program, till exempel PowerShell-Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="23271-128">Creating an out-of-process background job with `Start-Job` is not supported in the scenario where PowerShell is being hosted in other applications, such as the PowerShell Azure Functions.</span></span>
>
> <span data-ttu-id="23271-129">Detta är avsiktligt eftersom `Start-Job` det beror på att den `pwsh` körbara filen är tillgänglig under `$PSHOME` för att starta ett bakgrunds jobb utanför processen, men när ett program är värd för PowerShell, är det direkt med POWERSHELL-NuGet SDK-paket och har inte `pwsh` levererats tillsammans.</span><span class="sxs-lookup"><span data-stu-id="23271-129">This is by design because `Start-Job` depends on the `pwsh` executable to be available under `$PSHOME` to start an out-of-process background job, but when an application is hosting PowerShell, it's directly using the PowerShell NuGet SDK packages and won't have `pwsh` shipped along.</span></span>
>
> <span data-ttu-id="23271-130">Ersättningen i det scenariot är `Start-ThreadJob` från modulen **[ThreadJob](https://www.powershellgallery.com/packages/ThreadJob)**.</span><span class="sxs-lookup"><span data-stu-id="23271-130">The substitute in that scenario is `Start-ThreadJob` from the module **[ThreadJob](https://www.powershellgallery.com/packages/ThreadJob)**.</span></span>

## <span data-ttu-id="23271-131">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="23271-131">EXAMPLES</span></span>

### <span data-ttu-id="23271-132">Exempel 1: starta ett bakgrunds jobb</span><span class="sxs-lookup"><span data-stu-id="23271-132">Example 1: Start a background job</span></span>

<span data-ttu-id="23271-133">I det här exemplet startas ett bakgrunds jobb som körs på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="23271-133">This example starts a background job that runs on the local computer.</span></span>

```powershell
Start-Job -ScriptBlock { Get-Process -Name pwsh }
```

```Output
Id  Name   PSJobTypeName   State     HasMoreData   Location    Command
--  ----   -------------   -----     -----------   --------    -------
1   Job1   BackgroundJob   Running   True          localhost   Get-Process -Name pwsh
```

<span data-ttu-id="23271-134">`Start-Job` använder parametern **script block** för att köras `Get-Process` som ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="23271-134">`Start-Job` uses the **ScriptBlock** parameter to run `Get-Process` as a background job.</span></span> <span data-ttu-id="23271-135">Parametern **Name** anger för att hitta PowerShell-processer `pwsh` .</span><span class="sxs-lookup"><span data-stu-id="23271-135">The **Name** parameter specifies to find PowerShell processes, `pwsh`.</span></span> <span data-ttu-id="23271-136">Jobb informationen visas och PowerShell återgår till en prompt medan jobbet körs i bakgrunden.</span><span class="sxs-lookup"><span data-stu-id="23271-136">The job information is displayed and PowerShell returns to a prompt while the job runs in the background.</span></span>

<span data-ttu-id="23271-137">Om du vill visa jobbets utdata använder du `Receive-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="23271-137">To view the job's output, use the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="23271-138">Ett exempel är `Receive-Job -Id 1`.</span><span class="sxs-lookup"><span data-stu-id="23271-138">For example, `Receive-Job -Id 1`.</span></span>

### <span data-ttu-id="23271-139">Exempel 2: Använd bakgrunds operatorn för att starta ett bakgrunds jobb</span><span class="sxs-lookup"><span data-stu-id="23271-139">Example 2: Use the background operator to start a background job</span></span>

<span data-ttu-id="23271-140">I det här exemplet används et-tecknet ( `&` ) som bakgrunds operator för att starta ett bakgrunds jobb på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="23271-140">This example uses the ampersand (`&`) background operator to start a background job on the local computer.</span></span> <span data-ttu-id="23271-141">Jobbet får samma resultat som `Start-Job` i exempel 1.</span><span class="sxs-lookup"><span data-stu-id="23271-141">The job gets the same result as `Start-Job` in Example 1.</span></span>

```powershell
Get-Process -Name pwsh &
```

```Output
Id    Name   PSJobTypeName   State       HasMoreData     Location      Command
--    ----   -------------   -----       -----------     --------      -------
5     Job5   BackgroundJob   Running     True            localhost     Microsoft.PowerShell.Man...
```

<span data-ttu-id="23271-142">`Get-Process` använder parametern **Name** för att ange PowerShell-processer `pwsh` .</span><span class="sxs-lookup"><span data-stu-id="23271-142">`Get-Process` uses the **Name** parameter to specify PowerShell processes, `pwsh`.</span></span> <span data-ttu-id="23271-143">Et-tecknet ( `&` ) kör kommandot som ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="23271-143">The ampersand (`&`) runs the command as a background job.</span></span> <span data-ttu-id="23271-144">Jobb informationen visas och PowerShell återgår till en prompt medan jobbet körs i bakgrunden.</span><span class="sxs-lookup"><span data-stu-id="23271-144">The job information is displayed and PowerShell returns to a prompt while the job runs in the background.</span></span>

<span data-ttu-id="23271-145">Om du vill visa jobbets utdata använder du `Receive-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="23271-145">To view the job's output, use the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="23271-146">Ett exempel är `Receive-Job -Id 5`.</span><span class="sxs-lookup"><span data-stu-id="23271-146">For example, `Receive-Job -Id 5`.</span></span>

### <span data-ttu-id="23271-147">Exempel 3: starta ett jobb med Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="23271-147">Example 3: Start a job using Invoke-Command</span></span>

<span data-ttu-id="23271-148">I det här exemplet körs ett jobb på flera datorer.</span><span class="sxs-lookup"><span data-stu-id="23271-148">This example runs a job on multiple computers.</span></span> <span data-ttu-id="23271-149">Jobbet lagras i en variabel och körs med hjälp av variabel namnet på PowerShell-kommandoraden.</span><span class="sxs-lookup"><span data-stu-id="23271-149">The job is stored in a variable and is executed by using the variable name on the PowerShell command line.</span></span>

```powershell
$jobWRM = Invoke-Command -ComputerName (Get-Content -Path C:\Servers.txt) -ScriptBlock {
   Get-Service -Name WinRM } -JobName WinRM -ThrottleLimit 16 -AsJob
```

<span data-ttu-id="23271-150">Ett jobb som använder `Invoke-Command` skapas och lagras i `$jobWRM` variabeln.</span><span class="sxs-lookup"><span data-stu-id="23271-150">A job that uses `Invoke-Command` is created and stored in the `$jobWRM` variable.</span></span> <span data-ttu-id="23271-151">`Invoke-Command` använder parametern **computername** för att ange de datorer där jobbet körs.</span><span class="sxs-lookup"><span data-stu-id="23271-151">`Invoke-Command` uses the **ComputerName** parameter to specify the computers where the job runs.</span></span> <span data-ttu-id="23271-152">`Get-Content` hämtar Server namnen från `C:\Servers.txt` filen.</span><span class="sxs-lookup"><span data-stu-id="23271-152">`Get-Content` gets the server names from the `C:\Servers.txt` file.</span></span>

<span data-ttu-id="23271-153">Parametern **script block** anger ett kommando som `Get-Service` hämtar **WinRM** -tjänsten.</span><span class="sxs-lookup"><span data-stu-id="23271-153">The **ScriptBlock** parameter specifies a command that `Get-Service` gets the **WinRM** service.</span></span> <span data-ttu-id="23271-154">Parametern **JobName** anger ett eget namn för jobbet, **WinRM**.</span><span class="sxs-lookup"><span data-stu-id="23271-154">The **JobName** parameter specifies a friendly name for the job, **WinRM**.</span></span> <span data-ttu-id="23271-155">Parametern **ThrottleLimit** begränsar antalet samtidiga kommandon till 16.</span><span class="sxs-lookup"><span data-stu-id="23271-155">The **ThrottleLimit** parameter limits the number of concurrent commands to 16.</span></span> <span data-ttu-id="23271-156">Parametern **AsJob** startar ett bakgrunds jobb som kör kommandot på servrarna.</span><span class="sxs-lookup"><span data-stu-id="23271-156">The **AsJob** parameter starts a background job that runs the command on the servers.</span></span>

### <span data-ttu-id="23271-157">Exempel 4: Hämta jobb information</span><span class="sxs-lookup"><span data-stu-id="23271-157">Example 4: Get job information</span></span>

<span data-ttu-id="23271-158">I det här exemplet får du information om ett jobb och visar resultatet av ett slutfört jobb som kördes på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="23271-158">This example gets information about a job and displays the results of a completed job that was run on the local computer.</span></span>

```powershell
$j = Start-Job -ScriptBlock { Get-WinEvent -Log System } -Credential Domain01\User01
$j | Select-Object -Property *
```

```Output
State         : Completed
HasMoreData   : True
StatusMessage :
Location      : localhost
Command       : Get-WinEvent -Log System
JobStateInfo  : Completed
Finished      : System.Threading.ManualResetEvent
InstanceId    : 27ce3fd9-40ed-488a-99e5-679cd91b9dd3
Id            : 18
Name          : Job18
ChildJobs     : {Job19}
PSBeginTime   : 8/8/2019 14:41:57
PSEndTime     : 8/8/2019 14:42:07
PSJobTypeName : BackgroundJob
Output        : {}
Error         : {}
Progress      : {}
Verbose       : {}
Debug         : {}
Warning       : {}
Information   : {}
```

<span data-ttu-id="23271-159">`Start-Job` använder parametern **script block** för att köra ett kommando som anger `Get-WinEvent` för att hämta **system** loggen.</span><span class="sxs-lookup"><span data-stu-id="23271-159">`Start-Job` uses the **ScriptBlock** parameter to run a command that specifies `Get-WinEvent` to get the **System** log.</span></span> <span data-ttu-id="23271-160">Parametern **Credential** anger ett domän användar konto med behörighet att köra jobbet på datorn.</span><span class="sxs-lookup"><span data-stu-id="23271-160">The **Credential** parameter specifies a domain user account with permission to run the job on the computer.</span></span> <span data-ttu-id="23271-161">Jobbobjektet lagras i `$j` variabeln.</span><span class="sxs-lookup"><span data-stu-id="23271-161">The job object is stored in the `$j` variable.</span></span>

<span data-ttu-id="23271-162">Objektet i `$j` variabeln skickas nedåt i pipeline till `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="23271-162">The object in the `$j` variable is sent down the pipeline to `Select-Object`.</span></span> <span data-ttu-id="23271-163">**Egenskaps** parametern anger en asterisk ( `*` ) för att visa alla jobb objekt egenskaper.</span><span class="sxs-lookup"><span data-stu-id="23271-163">The **Property** parameter specifies an asterisk (`*`) to display all the job object's properties.</span></span>

### <span data-ttu-id="23271-164">Exempel 5: köra ett skript som ett bakgrunds jobb</span><span class="sxs-lookup"><span data-stu-id="23271-164">Example 5: Run a script as a background job</span></span>

<span data-ttu-id="23271-165">I det här exemplet körs ett skript på den lokala datorn som ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="23271-165">In this example, a script on the local computer is run as a background job.</span></span>

```powershell
Start-Job -FilePath C:\Scripts\Sample.ps1
```

<span data-ttu-id="23271-166">`Start-Job` använder parametern **sökväg** för att ange en skript fil som är lagrad på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="23271-166">`Start-Job` uses the **FilePath** parameter to specify a script file that's stored on the local computer.</span></span>

### <span data-ttu-id="23271-167">Exempel 6: få en process med ett bakgrunds jobb</span><span class="sxs-lookup"><span data-stu-id="23271-167">Example 6: Get a process using a background job</span></span>

<span data-ttu-id="23271-168">I det här exemplet används ett bakgrunds jobb för att hämta en angiven process efter namn.</span><span class="sxs-lookup"><span data-stu-id="23271-168">This example uses a background job to get a specified process by name.</span></span>

```powershell
Start-Job -Name PShellJob -ScriptBlock { Get-Process -Name PowerShell }
```

<span data-ttu-id="23271-169">`Start-Job` använder **namn** parametern för att ange ett eget jobbnamn, **PShellJob**.</span><span class="sxs-lookup"><span data-stu-id="23271-169">`Start-Job` uses the **Name** parameter to specify a friendly job name, **PShellJob**.</span></span> <span data-ttu-id="23271-170">Parametern **script block** anger `Get-Process` för att hämta processer med namnet **PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="23271-170">The **ScriptBlock** parameter specifies `Get-Process` to get processes with the name **PowerShell**.</span></span>

### <span data-ttu-id="23271-171">Exempel 7: samla in och spara data med hjälp av ett bakgrunds jobb</span><span class="sxs-lookup"><span data-stu-id="23271-171">Example 7: Collect and save data by using a background job</span></span>

<span data-ttu-id="23271-172">I det här exemplet startas ett jobb som samlar in en stor mängd kartdata och sparar den sedan i en `.tif` fil.</span><span class="sxs-lookup"><span data-stu-id="23271-172">This example starts a job that collects a large amount of map data and then saves it in a `.tif` file.</span></span>

```powershell
Start-Job -Name GetMappingFiles -InitializationScript {Import-Module MapFunctions} -ScriptBlock {
   Get-Map -Name * | Set-Content -Path D:\Maps.tif }
```

<span data-ttu-id="23271-173">`Start-Job` använder **namn** parametern för att ange ett eget jobbnamn, **GetMappingFiles**.</span><span class="sxs-lookup"><span data-stu-id="23271-173">`Start-Job` uses the **Name** parameter to specify a friendly job name, **GetMappingFiles**.</span></span> <span data-ttu-id="23271-174">Parametern **InitializationScript** kör ett skript block som importerar **MapFunctions** -modulen.</span><span class="sxs-lookup"><span data-stu-id="23271-174">The **InitializationScript** parameter runs a script block that imports the **MapFunctions** module.</span></span> <span data-ttu-id="23271-175">Parametern **script block** körs `Get-Map` och `Set-Content` sparar data på den plats som anges i parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="23271-175">The **ScriptBlock** parameter runs `Get-Map` and `Set-Content` saves the data in the location specified by the **Path** parameter.</span></span>

### <span data-ttu-id="23271-176">Exempel 8: skicka in ininformation till ett bakgrunds jobb</span><span class="sxs-lookup"><span data-stu-id="23271-176">Example 8: Pass input to a background job</span></span>

<span data-ttu-id="23271-177">I det här exemplet används den `$input` automatiska variabeln för att bearbeta ett indatamängds objekt.</span><span class="sxs-lookup"><span data-stu-id="23271-177">This example uses the `$input` automatic variable to process an input object.</span></span> <span data-ttu-id="23271-178">Används `Receive-Job` för att Visa jobbets utdata.</span><span class="sxs-lookup"><span data-stu-id="23271-178">Use `Receive-Job` to view the job's output.</span></span>

```powershell
Start-Job -ScriptBlock { Get-Content $input } -InputObject "C:\Servers.txt"
Receive-Job -Name Job45 -Keep
```

```Output
Server01
Server02
Server03
Server04
```

<span data-ttu-id="23271-179">`Start-Job` använder parametern **script block** för att köra `Get-Content` med den `$input` automatiska variabeln.</span><span class="sxs-lookup"><span data-stu-id="23271-179">`Start-Job` uses the **ScriptBlock** parameter to run `Get-Content` with the `$input` automatic variable.</span></span> <span data-ttu-id="23271-180">`$input`Variabeln hämtar objekt från **InputObject** -parametern.</span><span class="sxs-lookup"><span data-stu-id="23271-180">The `$input` variable gets objects from the **InputObject** parameter.</span></span> <span data-ttu-id="23271-181">`Receive-Job` använder parametern **Name** för att ange jobbet och ger resultatet utdata.</span><span class="sxs-lookup"><span data-stu-id="23271-181">`Receive-Job` uses the **Name** parameter to specify the job and outputs the results.</span></span> <span data-ttu-id="23271-182">Parametern **Keep** sparar jobbets utdata så att den kan visas igen under PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="23271-182">The **Keep** parameter saves the job output so it can be viewed again during the PowerShell session.</span></span>

### <span data-ttu-id="23271-183">Exempel 9: Ange arbets katalog för ett bakgrunds jobb</span><span class="sxs-lookup"><span data-stu-id="23271-183">Example 9: Set the working directory for a background job</span></span>

<span data-ttu-id="23271-184">Med **WorkingDirectory** kan du ange en alternativ katalog för ett jobb som du kan köra skript eller öppna filer från.</span><span class="sxs-lookup"><span data-stu-id="23271-184">The **WorkingDirectory** allows you to specify an alternate directory for a job from which you can run scripts or open files.</span></span> <span data-ttu-id="23271-185">I det här exemplet anger bakgrunds jobbet en arbets katalog som skiljer sig från den aktuella katalog platsen.</span><span class="sxs-lookup"><span data-stu-id="23271-185">In this example, the background job specifies a working directory that's different than the current directory location.</span></span>

```
PS C:\Test> Start-Job -WorkingDirectory C:\Test\Scripts { $PWD } | Receive-Job -AutoRemoveJob -Wait

Path
----
C:\Test\Scripts
```

<span data-ttu-id="23271-186">Det här exemplet är den aktuella arbets katalogen `C:\Test` .</span><span class="sxs-lookup"><span data-stu-id="23271-186">This example's current working directory is `C:\Test`.</span></span> <span data-ttu-id="23271-187">`Start-Job` använder parametern **WorkingDirectory** för att ange jobbets arbets katalog.</span><span class="sxs-lookup"><span data-stu-id="23271-187">`Start-Job` uses the **WorkingDirectory** parameter to specify the job's working directory.</span></span> <span data-ttu-id="23271-188">**Script block** -parametern använder `$PWD` för att Visa jobbets arbets katalog.</span><span class="sxs-lookup"><span data-stu-id="23271-188">The **ScriptBlock** parameter uses `$PWD` to display the job's working directory.</span></span> <span data-ttu-id="23271-189">`Receive-Job` visar bakgrunds jobbets utdata.</span><span class="sxs-lookup"><span data-stu-id="23271-189">`Receive-Job` displays the background job's output.</span></span>
<span data-ttu-id="23271-190">**AutoRemoveJob** tar bort jobbet och **väntar** på att ignorera kommando tolken tills alla resultat tas emot.</span><span class="sxs-lookup"><span data-stu-id="23271-190">**AutoRemoveJob** deletes the job and **Wait** suppresses the command prompt until all results are received.</span></span>

### <span data-ttu-id="23271-191">Exempel 10: Använd parametern argument list för att ange en matris</span><span class="sxs-lookup"><span data-stu-id="23271-191">Example 10: Use the ArgumentList parameter to specify an array</span></span>

<span data-ttu-id="23271-192">I det här exemplet används parametern **argument List** för att ange en matris med argument.</span><span class="sxs-lookup"><span data-stu-id="23271-192">This example uses the **ArgumentList** parameter to specify an array of arguments.</span></span> <span data-ttu-id="23271-193">Matrisen är en kommaavgränsad lista med process namn.</span><span class="sxs-lookup"><span data-stu-id="23271-193">The array is a comma-separated list of process names.</span></span>

```powershell
Start-Job -ScriptBlock { Get-Process -Name $args } -ArgumentList powershell, pwsh, notepad
```

```Output
Id     Name      PSJobTypeName   State       HasMoreData     Location     Command
--     ----      -------------   -----       -----------     --------     -------
1      Job1      BackgroundJob   Running     True            localhost    Get-Process -Name $args
```

<span data-ttu-id="23271-194">`Start-Job`Cmdleten använder parametern **script block** för att köra ett kommando.</span><span class="sxs-lookup"><span data-stu-id="23271-194">The `Start-Job` cmdlet uses the **ScriptBlock** parameter to run a command.</span></span> <span data-ttu-id="23271-195">`Get-Process` använder parametern **Name** för att ange den automatiska variabeln `$args` .</span><span class="sxs-lookup"><span data-stu-id="23271-195">`Get-Process` uses the **Name** parameter to specify the automatic variable `$args`.</span></span> <span data-ttu-id="23271-196">Parametern **argument List** skickar matrisen med process namn till `$args` .</span><span class="sxs-lookup"><span data-stu-id="23271-196">The **ArgumentList** parameter passes the array of process names to `$args`.</span></span> <span data-ttu-id="23271-197">Process namnen PowerShell, pwsh och Notepad är processer som körs på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="23271-197">The process names powershell, pwsh, and notepad are processes running on the local computer.</span></span>

<span data-ttu-id="23271-198">Om du vill visa jobbets utdata använder du `Receive-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="23271-198">To view the job's output, use the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="23271-199">Ett exempel är `Receive-Job -Id 1`.</span><span class="sxs-lookup"><span data-stu-id="23271-199">For example, `Receive-Job -Id 1`.</span></span>

### <span data-ttu-id="23271-200">Exempel 11: Kör jobb i en Windows PowerShell 5,1</span><span class="sxs-lookup"><span data-stu-id="23271-200">Example 11: Run job in a Windows PowerShell 5.1</span></span>

<span data-ttu-id="23271-201">I det här exemplet används parametern **PSVersion** med värdet **5,1** för att köra jobbet i en Windows PowerShell 5,1-session.</span><span class="sxs-lookup"><span data-stu-id="23271-201">This example uses the **PSVersion** parameter with value **5.1** to run job in a Windows PowerShell 5.1 session.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Patch  PreReleaseLabel BuildLabel
-----  -----  -----  --------------- ----------
7      0      0      rc.1
```

```powershell
$job = Start-Job { $PSVersionTable.PSVersion } -PSVersion 5.1
Receive-Job $job
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  3383
```

## <span data-ttu-id="23271-202">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="23271-202">PARAMETERS</span></span>

### <span data-ttu-id="23271-203">– Argument List</span><span class="sxs-lookup"><span data-stu-id="23271-203">-ArgumentList</span></span>

<span data-ttu-id="23271-204">Anger en matris med argument, eller parameter värden, för det skript som anges av parametern för **Sök väg** eller ett kommando som anges med parametern **script block** .</span><span class="sxs-lookup"><span data-stu-id="23271-204">Specifies an array of arguments, or parameter values, for the script that is specified by the **FilePath** parameter or a command specified with the **ScriptBlock** parameter.</span></span>

<span data-ttu-id="23271-205">Argument måste skickas till **argument List** som ett mat ris argument med en dimension.</span><span class="sxs-lookup"><span data-stu-id="23271-205">Arguments must be passed to **ArgumentList** as single-dimension array argument.</span></span> <span data-ttu-id="23271-206">Till exempel en kommaavgränsad lista.</span><span class="sxs-lookup"><span data-stu-id="23271-206">For example, a comma-separated list.</span></span> <span data-ttu-id="23271-207">Mer information om beteendet för **argument List** finns [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span><span class="sxs-lookup"><span data-stu-id="23271-207">For more information about the behavior of **ArgumentList**, see [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="23271-208">-Autentisering</span><span class="sxs-lookup"><span data-stu-id="23271-208">-Authentication</span></span>

<span data-ttu-id="23271-209">Anger den mekanism som används för att autentisera användarautentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="23271-209">Specifies the mechanism that is used to authenticate user credentials.</span></span>

<span data-ttu-id="23271-210">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="23271-210">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="23271-211">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="23271-211">Default</span></span>
- <span data-ttu-id="23271-212">Grundläggande</span><span class="sxs-lookup"><span data-stu-id="23271-212">Basic</span></span>
- <span data-ttu-id="23271-213">CredSSP</span><span class="sxs-lookup"><span data-stu-id="23271-213">Credssp</span></span>
- <span data-ttu-id="23271-214">Sammandrag</span><span class="sxs-lookup"><span data-stu-id="23271-214">Digest</span></span>
- <span data-ttu-id="23271-215">Kerberos</span><span class="sxs-lookup"><span data-stu-id="23271-215">Kerberos</span></span>
- <span data-ttu-id="23271-216">Negotiate</span><span class="sxs-lookup"><span data-stu-id="23271-216">Negotiate</span></span>
- <span data-ttu-id="23271-217">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="23271-217">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="23271-218">Standardvärdet är default.</span><span class="sxs-lookup"><span data-stu-id="23271-218">The default value is Default.</span></span>

<span data-ttu-id="23271-219">CredSSP-autentisering är endast tillgängligt i Windows Vista, Windows Server 2008 och senare versioner av Windows operativ system.</span><span class="sxs-lookup"><span data-stu-id="23271-219">CredSSP authentication is available only in Windows Vista, Windows Server 2008, and later versions of the Windows operating system.</span></span>

<span data-ttu-id="23271-220">Mer information om värdena för den här parametern finns i [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span><span class="sxs-lookup"><span data-stu-id="23271-220">For more information about the values of this parameter, see [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="23271-221">CredSSP-autentisering (Credential Security Support Provider), där användarens autentiseringsuppgifter skickas till en fjärrdator som ska autentiseras, är utformad för kommandon som kräver autentisering på fler än en resurs, till exempel åtkomst till en fjärran sluten nätverks resurs.</span><span class="sxs-lookup"><span data-stu-id="23271-221">Credential Security Support Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="23271-222">Den här mekanismen ökar säkerhets risken för Fjärråtgärden.</span><span class="sxs-lookup"><span data-stu-id="23271-222">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="23271-223">Om fjärrdatorn har komprometterats kan de autentiseringsuppgifter som skickas till den användas för att kontrol lera nätverks sessionen.</span><span class="sxs-lookup"><span data-stu-id="23271-223">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="23271-224">-Credential</span><span class="sxs-lookup"><span data-stu-id="23271-224">-Credential</span></span>

<span data-ttu-id="23271-225">Anger ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="23271-225">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="23271-226">Om parametern **Credential** inte anges använder kommandot den aktuella användarens autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="23271-226">If the **Credential** parameter isn't specified, the command uses the current user's credentials.</span></span>

<span data-ttu-id="23271-227">Ange ett användar namn, till exempel **user01** eller **Domain01\User01**, eller ange ett **PSCredential** -objekt som genererats av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="23271-227">Type a user name, such as **User01** or **Domain01\User01**, or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="23271-228">Om du anger ett användar namn uppmanas du att ange lösen ordet.</span><span class="sxs-lookup"><span data-stu-id="23271-228">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="23271-229">Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="23271-229">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="23271-230">Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="23271-230">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="23271-231">-DefinitionName</span><span class="sxs-lookup"><span data-stu-id="23271-231">-DefinitionName</span></span>

<span data-ttu-id="23271-232">Anger definitions namnet för det jobb som denna cmdlet startar.</span><span class="sxs-lookup"><span data-stu-id="23271-232">Specifies the definition name of the job that this cmdlet starts.</span></span> <span data-ttu-id="23271-233">Använd den här parametern för att starta anpassade jobb typer som har ett definitions namn, till exempel schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="23271-233">Use this parameter to start custom job types that have a definition name, such as scheduled jobs.</span></span>

<span data-ttu-id="23271-234">När du använder `Start-Job` för att starta en instans av ett schemalagt jobb startar jobbet omedelbart, oavsett jobb utlösare eller jobb alternativ.</span><span class="sxs-lookup"><span data-stu-id="23271-234">When you use `Start-Job` to start an instance of a scheduled job, the job starts immediately, regardless of job triggers or job options.</span></span> <span data-ttu-id="23271-235">Den resulterande jobb instansen är ett schemalagt jobb, men det sparas inte på disken som utlösta schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="23271-235">The resulting job instance is a scheduled job, but it isn't saved to disk like triggered scheduled jobs.</span></span> <span data-ttu-id="23271-236">Du kan inte använda parametern **argument List** för `Start-Job` för att ange värden för parametrar för skript som körs i ett schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="23271-236">You can't use the **ArgumentList** parameter of `Start-Job` to provide values for parameters of scripts that run in a scheduled job.</span></span>

<span data-ttu-id="23271-237">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="23271-237">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: DefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="23271-238">-DefinitionPath</span><span class="sxs-lookup"><span data-stu-id="23271-238">-DefinitionPath</span></span>

<span data-ttu-id="23271-239">Anger sökvägen till definitionen för jobbet som denna cmdlet startar.</span><span class="sxs-lookup"><span data-stu-id="23271-239">Specifies path of the definition for the job that this cmdlet starts.</span></span> <span data-ttu-id="23271-240">Ange definitions Sök vägen.</span><span class="sxs-lookup"><span data-stu-id="23271-240">Enter the definition path.</span></span> <span data-ttu-id="23271-241">Sammanfogningen av värdena för parametrarna **DefinitionPath** och **DefinitionName** är den fullständigt kvalificerade sökvägen för jobb definitionen.</span><span class="sxs-lookup"><span data-stu-id="23271-241">The concatenation of the values of the **DefinitionPath** and **DefinitionName** parameters is the fully qualified path of the job definition.</span></span> <span data-ttu-id="23271-242">Använd den här parametern för att starta anpassade jobb typer som har en definitions Sök väg, till exempel schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="23271-242">Use this parameter to start custom job types that have a definition path, such as scheduled jobs.</span></span>

<span data-ttu-id="23271-243">För schemalagda jobb är värdet för parametern **DefinitionPath** `$home\AppData\Local\Windows\PowerShell\ScheduledJob` .</span><span class="sxs-lookup"><span data-stu-id="23271-243">For scheduled jobs, the value of the **DefinitionPath** parameter is `$home\AppData\Local\Windows\PowerShell\ScheduledJob`.</span></span>

<span data-ttu-id="23271-244">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="23271-244">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: DefinitionName
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="23271-245">-Sökväg</span><span class="sxs-lookup"><span data-stu-id="23271-245">-FilePath</span></span>

<span data-ttu-id="23271-246">Anger ett lokalt skript som `Start-Job` körs som ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="23271-246">Specifies a local script that `Start-Job` runs as a background job.</span></span> <span data-ttu-id="23271-247">Ange sökvägen och fil namnet för skriptet eller Använd pipelinen för att skicka en skript Sök väg till `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="23271-247">Enter the path and file name of the script or use the pipeline to send a script path to `Start-Job`.</span></span> <span data-ttu-id="23271-248">Skriptet måste finnas på den lokala datorn eller i en mapp som den lokala datorn kan komma åt.</span><span class="sxs-lookup"><span data-stu-id="23271-248">The script must be on the local computer or in a folder that the local computer can access.</span></span>

<span data-ttu-id="23271-249">När du använder den här parametern konverterar PowerShell innehållet i den angivna skript filen till ett-skript block och kör skript blocket som ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="23271-249">When you use this parameter, PowerShell converts the contents of the specified script file to a script block and runs the script block as a background job.</span></span>

```yaml
Type: System.String
Parameter Sets: FilePathComputerName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="23271-250">-InitializationScript</span><span class="sxs-lookup"><span data-stu-id="23271-250">-InitializationScript</span></span>

<span data-ttu-id="23271-251">Anger kommandon som körs innan jobbet startas.</span><span class="sxs-lookup"><span data-stu-id="23271-251">Specifies commands that run before the job starts.</span></span> <span data-ttu-id="23271-252">Om du vill skapa ett skript block, omger du kommandona med klammerparenteser ( `{}` ).</span><span class="sxs-lookup"><span data-stu-id="23271-252">To create a script block, enclose the commands in curly braces (`{}`).</span></span>

<span data-ttu-id="23271-253">Använd den här parametern för att förbereda sessionen där jobbet körs.</span><span class="sxs-lookup"><span data-stu-id="23271-253">Use this parameter to prepare the session in which the job runs.</span></span> <span data-ttu-id="23271-254">Du kan till exempel använda den för att lägga till funktioner, snapin-moduler och moduler i sessionen.</span><span class="sxs-lookup"><span data-stu-id="23271-254">For example, you can use it to add functions, snap-ins, and modules to the session.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="23271-255">– InputObject</span><span class="sxs-lookup"><span data-stu-id="23271-255">-InputObject</span></span>

<span data-ttu-id="23271-256">Anger ininformation till kommandot.</span><span class="sxs-lookup"><span data-stu-id="23271-256">Specifies input to the command.</span></span> <span data-ttu-id="23271-257">Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som genererar objekten.</span><span class="sxs-lookup"><span data-stu-id="23271-257">Enter a variable that contains the objects, or type a command or expression that generates the objects.</span></span>

<span data-ttu-id="23271-258">I värdet för parametern **script block** använder du den `$input` automatiska variabeln för att representera objekten.</span><span class="sxs-lookup"><span data-stu-id="23271-258">In the value of the **ScriptBlock** parameter, use the `$input` automatic variable to represent the input objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="23271-259">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="23271-259">-LiteralPath</span></span>

<span data-ttu-id="23271-260">Anger ett lokalt skript som denna cmdlet kör som ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="23271-260">Specifies a local script that this cmdlet runs as a background job.</span></span> <span data-ttu-id="23271-261">Ange sökvägen till ett skript på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="23271-261">Enter the path of a script on the local computer.</span></span>

<span data-ttu-id="23271-262">`Start-Job` använder värdet för parametern **LiteralPath** exakt som den skrivs.</span><span class="sxs-lookup"><span data-stu-id="23271-262">`Start-Job` uses the value of the **LiteralPath** parameter exactly as it's typed.</span></span> <span data-ttu-id="23271-263">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="23271-263">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="23271-264">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="23271-264">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="23271-265">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="23271-265">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: LiteralFilePathComputerName
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="23271-266">-Name</span><span class="sxs-lookup"><span data-stu-id="23271-266">-Name</span></span>

<span data-ttu-id="23271-267">Anger ett eget namn för det nya jobbet.</span><span class="sxs-lookup"><span data-stu-id="23271-267">Specifies a friendly name for the new job.</span></span> <span data-ttu-id="23271-268">Du kan använda namnet för att identifiera jobbet till andra jobb-cmdlet: ar, till exempel `Stop-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="23271-268">You can use the name to identify the job to other job cmdlets, such as the `Stop-Job` cmdlet.</span></span>

<span data-ttu-id="23271-269">Det egna standard namnet är `Job#` , där `#` är ett ordnings tal som ökar för varje jobb.</span><span class="sxs-lookup"><span data-stu-id="23271-269">The default friendly name is `Job#`, where `#` is an ordinal number that is incremented for each job.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="23271-270">– PSVersion</span><span class="sxs-lookup"><span data-stu-id="23271-270">-PSVersion</span></span>

<span data-ttu-id="23271-271">Anger en version av PowerShell som ska användas för att köra jobbet.</span><span class="sxs-lookup"><span data-stu-id="23271-271">Specifies a version of PowerShell to use for running the job.</span></span>
<span data-ttu-id="23271-272">När värdet för **PSVersion** är **5,1** körs jobbet i en Windows PowerShell 5,1-session.</span><span class="sxs-lookup"><span data-stu-id="23271-272">When the value of **PSVersion** is **5.1** The job is run in a Windows PowerShell 5.1 session.</span></span>
<span data-ttu-id="23271-273">För andra värden körs jobbet med den aktuella versionen av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="23271-273">For any other value, the job is run using the current version of PowerShell.</span></span>

<span data-ttu-id="23271-274">Den här parametern lades till i PowerShell 7 och fungerar bara på Windows.</span><span class="sxs-lookup"><span data-stu-id="23271-274">This parameter was added in PowerShell 7 and only works on Windows.</span></span>

```yaml
Type: System.Version
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="23271-275">-RunAs32</span><span class="sxs-lookup"><span data-stu-id="23271-275">-RunAs32</span></span>

<span data-ttu-id="23271-276">Från och med PowerShell 7 fungerar inte **RunAs32** -parametern på 64-bitars PowerShell ( `pwsh` ).</span><span class="sxs-lookup"><span data-stu-id="23271-276">Beginning with PowerShell 7, the **RunAs32** parameter doesn't work on 64-bit PowerShell (`pwsh`).</span></span>
<span data-ttu-id="23271-277">Om **RunAs32** anges i 64-bitars PowerShell, `Start-Job` utlöses ett avslutande undantags fel.</span><span class="sxs-lookup"><span data-stu-id="23271-277">If **RunAs32** is specified in 64-bit PowerShell, `Start-Job` throws a terminating exception error.</span></span>
<span data-ttu-id="23271-278">Om du vill starta en 32-bitars PowerShell- `pwsh` process () med **RunAs32** måste du ha 32-bitars PowerShell installerat.</span><span class="sxs-lookup"><span data-stu-id="23271-278">To start a 32-bit PowerShell (`pwsh`) process with **RunAs32**, you need to have the 32-bit PowerShell installed.</span></span>

<span data-ttu-id="23271-279">I 32-bitars PowerShell tvingar **RunAs32** jobbet att köras i en 32-bitars process, även på ett 64-bitars operativ system.</span><span class="sxs-lookup"><span data-stu-id="23271-279">In 32-bit PowerShell, **RunAs32** forces the job to run in a 32-bit process, even on a 64-bit operating system.</span></span>

<span data-ttu-id="23271-280">I 64-bitars versioner av Windows 7 och Windows Server 2008 R2 kan `Start-Job` du inte använda parametern **Credential** för att ange autentiseringsuppgifterna för en annan användare när kommandot innehåller parametern **RunAs32** .</span><span class="sxs-lookup"><span data-stu-id="23271-280">On 64-bit versions of Windows 7 and Windows Server 2008 R2, when the `Start-Job` command includes the **RunAs32** parameter, you can't use the **Credential** parameter to specify the credentials of another user.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="23271-281">– Script block</span><span class="sxs-lookup"><span data-stu-id="23271-281">-ScriptBlock</span></span>

<span data-ttu-id="23271-282">Anger vilka kommandon som ska köras i bakgrunds jobbet.</span><span class="sxs-lookup"><span data-stu-id="23271-282">Specifies the commands to run in the background job.</span></span> <span data-ttu-id="23271-283">Om du vill skapa ett skript block, omger du kommandona med klammerparenteser ( `{}` ).</span><span class="sxs-lookup"><span data-stu-id="23271-283">To create a script block, enclose the commands in curly braces (`{}`).</span></span> <span data-ttu-id="23271-284">Använd den `$input` automatiska variabeln för att få åtkomst till värdet för parametern **InputObject** .</span><span class="sxs-lookup"><span data-stu-id="23271-284">Use the `$input` automatic variable to access the value of the **InputObject** parameter.</span></span> <span data-ttu-id="23271-285">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="23271-285">This parameter is required.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ComputerName
Aliases: Command

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="23271-286">-Typ</span><span class="sxs-lookup"><span data-stu-id="23271-286">-Type</span></span>

<span data-ttu-id="23271-287">Anger den anpassade typen för jobb som startas av `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="23271-287">Specifies the custom type for jobs started by `Start-Job`.</span></span> <span data-ttu-id="23271-288">Ange ett namn på en anpassad Jobbtyp, till exempel PSScheduledJob för schemalagda jobb eller PSWorkflowJob för arbets flödes jobb.</span><span class="sxs-lookup"><span data-stu-id="23271-288">Enter a custom job type name, such as PSScheduledJob for scheduled jobs or PSWorkflowJob for workflows jobs.</span></span> <span data-ttu-id="23271-289">Den här parametern är inte giltig för standard bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="23271-289">This parameter isn't valid for standard background jobs.</span></span>

<span data-ttu-id="23271-290">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="23271-290">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: DefinitionName
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="23271-291">– WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="23271-291">-WorkingDirectory</span></span>

<span data-ttu-id="23271-292">Anger bakgrunds jobbets ursprungliga arbets katalog.</span><span class="sxs-lookup"><span data-stu-id="23271-292">Specifies the initial working directory of the background job.</span></span> <span data-ttu-id="23271-293">Om parametern inte anges körs jobbet från standard platsen.</span><span class="sxs-lookup"><span data-stu-id="23271-293">If the parameter isn't specified, the job runs from the default location.</span></span> <span data-ttu-id="23271-294">Standard platsen är den aktuella arbets katalogen för den anropare som startade jobbet.</span><span class="sxs-lookup"><span data-stu-id="23271-294">The default location is the current working directory of the caller that started the job.</span></span>

<span data-ttu-id="23271-295">Den här parametern introducerades i PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="23271-295">This parameter was introduced in PowerShell 7.</span></span>

 ```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: $HOME on Unix (macOS, Linux) and $HOME\Documents on Windows
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="23271-296">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="23271-296">CommonParameters</span></span>

<span data-ttu-id="23271-297">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="23271-297">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="23271-298">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="23271-298">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="23271-299">INDATA</span><span class="sxs-lookup"><span data-stu-id="23271-299">INPUTS</span></span>

### <span data-ttu-id="23271-300">System. String</span><span class="sxs-lookup"><span data-stu-id="23271-300">System.String</span></span>

<span data-ttu-id="23271-301">Du kan använda pipelinen för att skicka ett objekt med egenskapen **Name** till parametern **Name** .</span><span class="sxs-lookup"><span data-stu-id="23271-301">You can use the pipeline to send an object with the **Name** property to the **Name** parameter.</span></span> <span data-ttu-id="23271-302">Du kan till exempel pipelina ett **fileinfo** -objekt från `Get-ChildItem` till `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="23271-302">For example, you can pipeline a **FileInfo** object from `Get-ChildItem` to `Start-Job`.</span></span>

## <span data-ttu-id="23271-303">UTDATA</span><span class="sxs-lookup"><span data-stu-id="23271-303">OUTPUTS</span></span>

### <span data-ttu-id="23271-304">System. Management. Automation. PSRemotingJob</span><span class="sxs-lookup"><span data-stu-id="23271-304">System.Management.Automation.PSRemotingJob</span></span>

<span data-ttu-id="23271-305">`Start-Job` Returnerar ett **PSRemotingJob** -objekt som representerar det jobb som startades.</span><span class="sxs-lookup"><span data-stu-id="23271-305">`Start-Job` returns a **PSRemotingJob** object that represents the job that it started.</span></span>

## <span data-ttu-id="23271-306">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="23271-306">NOTES</span></span>

<span data-ttu-id="23271-307">För att köra i bakgrunden `Start-Job` körs i en egen session i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="23271-307">To run in the background, `Start-Job` runs in its own session in the current session.</span></span> <span data-ttu-id="23271-308">När du använder `Invoke-Command` cmdleten för att köra ett `Start-Job` kommando i en session på en fjärrdator `Start-Job` körs i en session i fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="23271-308">When you use the `Invoke-Command` cmdlet to run a `Start-Job` command in a session on a remote computer, `Start-Job` runs in a session in the remote session.</span></span>

## <span data-ttu-id="23271-309">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="23271-309">RELATED LINKS</span></span>

[<span data-ttu-id="23271-310">about_Arrays</span><span class="sxs-lookup"><span data-stu-id="23271-310">about_Arrays</span></span>](./about/about_arrays.md)

[<span data-ttu-id="23271-311">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="23271-311">about_Automatic_Variables</span></span>](./about/about_automatic_variables.md)

[<span data-ttu-id="23271-312">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="23271-312">about_Jobs</span></span>](./About/about_Jobs.md)

[<span data-ttu-id="23271-313">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="23271-313">about_Job_Details</span></span>](./About/about_Job_Details.md)

[<span data-ttu-id="23271-314">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="23271-314">about_Remote_Jobs</span></span>](./About/about_Remote_Jobs.md)

[<span data-ttu-id="23271-315">Hämta jobb</span><span class="sxs-lookup"><span data-stu-id="23271-315">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="23271-316">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="23271-316">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="23271-317">Mottagning – jobb</span><span class="sxs-lookup"><span data-stu-id="23271-317">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="23271-318">Ta bort – jobb</span><span class="sxs-lookup"><span data-stu-id="23271-318">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="23271-319">Stoppa – jobb</span><span class="sxs-lookup"><span data-stu-id="23271-319">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="23271-320">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="23271-320">Wait-Job</span></span>](Wait-Job.md)
