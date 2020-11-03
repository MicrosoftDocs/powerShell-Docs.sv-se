---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/start-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Job
ms.openlocfilehash: 116e007cc28a91e3c97fd980cc27461932390b7c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264141"
---
# <span data-ttu-id="2045d-103">Start-Job</span><span class="sxs-lookup"><span data-stu-id="2045d-103">Start-Job</span></span>

## <span data-ttu-id="2045d-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="2045d-104">SYNOPSIS</span></span>
<span data-ttu-id="2045d-105">Startar ett PowerShell-bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="2045d-105">Starts a PowerShell background job.</span></span>

## <span data-ttu-id="2045d-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2045d-106">SYNTAX</span></span>

### <span data-ttu-id="2045d-107">ComputerName (standard)</span><span class="sxs-lookup"><span data-stu-id="2045d-107">ComputerName (Default)</span></span>

```
Start-Job [-Name <String>] [-ScriptBlock] <ScriptBlock> [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>] [-RunAs32]
 [-PSVersion <Version>] [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="2045d-108">DefinitionName</span><span class="sxs-lookup"><span data-stu-id="2045d-108">DefinitionName</span></span>

```
Start-Job [-DefinitionName] <String> [[-DefinitionPath] <String>] [[-Type] <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="2045d-109">FilePathComputerName</span><span class="sxs-lookup"><span data-stu-id="2045d-109">FilePathComputerName</span></span>

```
Start-Job [-Name <String>] [-Credential <PSCredential>] [-FilePath] <String>
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>] [-RunAs32]
 [-PSVersion <Version>] [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="2045d-110">LiteralFilePathComputerName</span><span class="sxs-lookup"><span data-stu-id="2045d-110">LiteralFilePathComputerName</span></span>

```
Start-Job [-Name <String>] [-Credential <PSCredential>] -LiteralPath <String>
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>] [-RunAs32]
 [-PSVersion <Version>] [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

## <span data-ttu-id="2045d-111">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="2045d-111">DESCRIPTION</span></span>

<span data-ttu-id="2045d-112">`Start-Job`Cmdleten startar ett PowerShell-bakgrunds jobb på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="2045d-112">The `Start-Job` cmdlet starts a PowerShell background job on the local computer.</span></span>

<span data-ttu-id="2045d-113">Ett PowerShell-bakgrunds jobb kör ett kommando utan att interagera med den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="2045d-113">A PowerShell background job runs a command without interacting with the current session.</span></span> <span data-ttu-id="2045d-114">När du startar ett bakgrunds jobb returnerar ett Job-objekt omedelbart, även om jobbet tar lång tid att slutföra.</span><span class="sxs-lookup"><span data-stu-id="2045d-114">When you start a background job, a job object returns immediately, even if the job takes an extended time to finish.</span></span> <span data-ttu-id="2045d-115">Du kan fortsätta att arbeta i sessionen utan avbrott medan jobbet körs.</span><span class="sxs-lookup"><span data-stu-id="2045d-115">You can continue to work in the session without interruption while the job runs.</span></span>

<span data-ttu-id="2045d-116">Jobbobjektet innehåller användbar information om jobbet, men det innehåller inte jobb resultatet.</span><span class="sxs-lookup"><span data-stu-id="2045d-116">The job object contains useful information about the job, but it doesn't contain the job results.</span></span>
<span data-ttu-id="2045d-117">När jobbet har slutförts använder du `Receive-Job` cmdleten för att hämta resultatet av jobbet.</span><span class="sxs-lookup"><span data-stu-id="2045d-117">When the job finishes, use the `Receive-Job` cmdlet to get the results of the job.</span></span> <span data-ttu-id="2045d-118">Mer information om bakgrunds jobb finns [about_Jobs](./About/about_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="2045d-118">For more information about background jobs, see [about_Jobs](./About/about_Jobs.md).</span></span>

<span data-ttu-id="2045d-119">Om du vill köra ett bakgrunds jobb på en fjärrdator använder du parametern **AsJob** som är tillgänglig på många cmdletar eller använder `Invoke-Command` cmdleten för att köra ett `Start-Job` kommando på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="2045d-119">To run a background job on a remote computer, use the **AsJob** parameter that is available on many cmdlets, or use the `Invoke-Command` cmdlet to run a `Start-Job` command on the remote computer.</span></span> <span data-ttu-id="2045d-120">Mer information finns i [about_Remote_Jobs](./About/about_Remote_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="2045d-120">For more information, see [about_Remote_Jobs](./About/about_Remote_Jobs.md).</span></span>

<span data-ttu-id="2045d-121">Från och med PowerShell 3,0 `Start-Job` kan instanser av anpassade jobb typer startas, till exempel schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="2045d-121">Starting in PowerShell 3.0, `Start-Job` can start instances of custom job types, such as scheduled jobs.</span></span> <span data-ttu-id="2045d-122">Information om hur du använder `Start-Job` för att starta jobb med anpassade typer finns i hjälp dokumenten för funktionen jobb typ.</span><span class="sxs-lookup"><span data-stu-id="2045d-122">For information about how to use `Start-Job` to start jobs with custom types, see the help documents for the job type feature.</span></span>

<span data-ttu-id="2045d-123">Standard arbets katalogen för jobb är hårdkodad.</span><span class="sxs-lookup"><span data-stu-id="2045d-123">The default working directory for jobs is hardcoded.</span></span> <span data-ttu-id="2045d-124">Windows standard är `$HOME\Documents` och på Linux eller MacOS som standard är `$HOME` .</span><span class="sxs-lookup"><span data-stu-id="2045d-124">The Windows default is `$HOME\Documents` and on Linux or macOS the default is `$HOME`.</span></span> <span data-ttu-id="2045d-125">Skript koden som körs i bakgrunds jobbet måste hantera arbets katalogen efter behov.</span><span class="sxs-lookup"><span data-stu-id="2045d-125">The script code running in the background job needs to manage the working directory as needed.</span></span>

## <span data-ttu-id="2045d-126">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="2045d-126">EXAMPLES</span></span>

### <span data-ttu-id="2045d-127">Exempel 1: starta ett bakgrunds jobb</span><span class="sxs-lookup"><span data-stu-id="2045d-127">Example 1: Start a background job</span></span>

<span data-ttu-id="2045d-128">I det här exemplet startas ett bakgrunds jobb som körs på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="2045d-128">This example starts a background job that runs on the local computer.</span></span>

```powershell
Start-Job -ScriptBlock { Get-Process -Name powershell }
```

```Output
Id  Name   PSJobTypeName   State     HasMoreData   Location    Command
--  ----   -------------   -----     -----------   --------    -------
1   Job1   BackgroundJob   Running   True          localhost   Get-Process -Name powershell
```

<span data-ttu-id="2045d-129">`Start-Job` använder parametern **script block** för att köras `Get-Process` som ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="2045d-129">`Start-Job` uses the **ScriptBlock** parameter to run `Get-Process` as a background job.</span></span> <span data-ttu-id="2045d-130">Parametern **Name** anger för att hitta PowerShell-processer `powershell` .</span><span class="sxs-lookup"><span data-stu-id="2045d-130">The **Name** parameter specifies to find PowerShell processes, `powershell`.</span></span> <span data-ttu-id="2045d-131">Jobb informationen visas och PowerShell återgår till en prompt medan jobbet körs i bakgrunden.</span><span class="sxs-lookup"><span data-stu-id="2045d-131">The job information is displayed and PowerShell returns to a prompt while the job runs in the background.</span></span>

<span data-ttu-id="2045d-132">Om du vill visa jobbets utdata använder du `Receive-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="2045d-132">To view the job's output, use the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="2045d-133">Till exempel `Receive-Job -Id 1`.</span><span class="sxs-lookup"><span data-stu-id="2045d-133">For example, `Receive-Job -Id 1`.</span></span>

### <span data-ttu-id="2045d-134">Exempel 2: starta ett jobb med Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="2045d-134">Example 2: Start a job using Invoke-Command</span></span>

<span data-ttu-id="2045d-135">I det här exemplet körs ett jobb på flera datorer.</span><span class="sxs-lookup"><span data-stu-id="2045d-135">This example runs a job on multiple computers.</span></span> <span data-ttu-id="2045d-136">Jobbet lagras i en variabel och körs med hjälp av variabel namnet på PowerShell-kommandoraden.</span><span class="sxs-lookup"><span data-stu-id="2045d-136">The job is stored in a variable and is executed by using the variable name on the PowerShell command line.</span></span>

```powershell
$jobWRM = Invoke-Command -ComputerName (Get-Content -Path C:\Servers.txt) -ScriptBlock {
   Get-Service -Name WinRM } -JobName WinRM -ThrottleLimit 16 -AsJob
```

<span data-ttu-id="2045d-137">Ett jobb som använder `Invoke-Command` skapas och lagras i `$jobWRM` variabeln.</span><span class="sxs-lookup"><span data-stu-id="2045d-137">A job that uses `Invoke-Command` is created and stored in the `$jobWRM` variable.</span></span> <span data-ttu-id="2045d-138">`Invoke-Command` använder parametern **computername** för att ange de datorer där jobbet körs.</span><span class="sxs-lookup"><span data-stu-id="2045d-138">`Invoke-Command` uses the **ComputerName** parameter to specify the computers where the job runs.</span></span> <span data-ttu-id="2045d-139">`Get-Content` hämtar Server namnen från `C:\Servers.txt` filen.</span><span class="sxs-lookup"><span data-stu-id="2045d-139">`Get-Content` gets the server names from the `C:\Servers.txt` file.</span></span>

<span data-ttu-id="2045d-140">Parametern **script block** anger ett kommando som `Get-Service` hämtar **WinRM** -tjänsten.</span><span class="sxs-lookup"><span data-stu-id="2045d-140">The **ScriptBlock** parameter specifies a command that `Get-Service` gets the **WinRM** service.</span></span> <span data-ttu-id="2045d-141">Parametern **JobName** anger ett eget namn för jobbet, **WinRM**.</span><span class="sxs-lookup"><span data-stu-id="2045d-141">The **JobName** parameter specifies a friendly name for the job, **WinRM**.</span></span> <span data-ttu-id="2045d-142">Parametern **ThrottleLimit** begränsar antalet samtidiga kommandon till 16.</span><span class="sxs-lookup"><span data-stu-id="2045d-142">The **ThrottleLimit** parameter limits the number of concurrent commands to 16.</span></span> <span data-ttu-id="2045d-143">Parametern **AsJob** startar ett bakgrunds jobb som kör kommandot på servrarna.</span><span class="sxs-lookup"><span data-stu-id="2045d-143">The **AsJob** parameter starts a background job that runs the command on the servers.</span></span>

### <span data-ttu-id="2045d-144">Exempel 3: Hämta jobb information</span><span class="sxs-lookup"><span data-stu-id="2045d-144">Example 3: Get job information</span></span>

<span data-ttu-id="2045d-145">I det här exemplet får du information om ett jobb och visar resultatet av ett slutfört jobb som kördes på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="2045d-145">This example gets information about a job and displays the results of a completed job that was run on the local computer.</span></span>

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

<span data-ttu-id="2045d-146">`Start-Job` använder parametern **script block** för att köra ett kommando som anger `Get-WinEvent` för att hämta **system** loggen.</span><span class="sxs-lookup"><span data-stu-id="2045d-146">`Start-Job` uses the **ScriptBlock** parameter to run a command that specifies `Get-WinEvent` to get the **System** log.</span></span> <span data-ttu-id="2045d-147">Parametern **Credential** anger ett domän användar konto med behörighet att köra jobbet på datorn.</span><span class="sxs-lookup"><span data-stu-id="2045d-147">The **Credential** parameter specifies a domain user account with permission to run the job on the computer.</span></span> <span data-ttu-id="2045d-148">Jobbobjektet lagras i `$j` variabeln.</span><span class="sxs-lookup"><span data-stu-id="2045d-148">The job object is stored in the `$j` variable.</span></span>

<span data-ttu-id="2045d-149">Objektet i `$j` variabeln skickas nedåt i pipeline till `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="2045d-149">The object in the `$j` variable is sent down the pipeline to `Select-Object`.</span></span> <span data-ttu-id="2045d-150">**Egenskaps** parametern anger en asterisk ( `*` ) för att visa alla jobb objekt egenskaper.</span><span class="sxs-lookup"><span data-stu-id="2045d-150">The **Property** parameter specifies an asterisk (`*`) to display all the job object's properties.</span></span>

### <span data-ttu-id="2045d-151">Exempel 4: kör ett skript som ett bakgrunds jobb</span><span class="sxs-lookup"><span data-stu-id="2045d-151">Example 4: Run a script as a background job</span></span>

<span data-ttu-id="2045d-152">I det här exemplet körs ett skript på den lokala datorn som ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="2045d-152">In this example, a script on the local computer is run as a background job.</span></span>

```powershell
Start-Job -FilePath C:\Scripts\Sample.ps1
```

<span data-ttu-id="2045d-153">`Start-Job` använder parametern **sökväg** för att ange en skript fil som är lagrad på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="2045d-153">`Start-Job` uses the **FilePath** parameter to specify a script file that's stored on the local computer.</span></span>

### <span data-ttu-id="2045d-154">Exempel 5: få en process med ett bakgrunds jobb</span><span class="sxs-lookup"><span data-stu-id="2045d-154">Example 5: Get a process using a background job</span></span>

<span data-ttu-id="2045d-155">I det här exemplet används ett bakgrunds jobb för att hämta en angiven process efter namn.</span><span class="sxs-lookup"><span data-stu-id="2045d-155">This example uses a background job to get a specified process by name.</span></span>

```powershell
Start-Job -Name PShellJob -ScriptBlock { Get-Process -Name PowerShell }
```

<span data-ttu-id="2045d-156">`Start-Job` använder **namn** parametern för att ange ett eget jobbnamn, **PShellJob**.</span><span class="sxs-lookup"><span data-stu-id="2045d-156">`Start-Job` uses the **Name** parameter to specify a friendly job name, **PShellJob**.</span></span> <span data-ttu-id="2045d-157">Parametern **script block** anger `Get-Process` för att hämta processer med namnet **PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="2045d-157">The **ScriptBlock** parameter specifies `Get-Process` to get processes with the name **PowerShell**.</span></span>

### <span data-ttu-id="2045d-158">Exempel 6: samla in och spara data med hjälp av ett bakgrunds jobb</span><span class="sxs-lookup"><span data-stu-id="2045d-158">Example 6: Collect and save data by using a background job</span></span>

<span data-ttu-id="2045d-159">I det här exemplet startas ett jobb som samlar in en stor mängd kartdata och sparar den sedan i en `.tif` fil.</span><span class="sxs-lookup"><span data-stu-id="2045d-159">This example starts a job that collects a large amount of map data and then saves it in a `.tif` file.</span></span>

```powershell
Start-Job -Name GetMappingFiles -InitializationScript {Import-Module MapFunctions} -ScriptBlock {
   Get-Map -Name * | Set-Content -Path D:\Maps.tif } -RunAs32
```

<span data-ttu-id="2045d-160">`Start-Job` använder **namn** parametern för att ange ett eget jobbnamn, **GetMappingFiles**.</span><span class="sxs-lookup"><span data-stu-id="2045d-160">`Start-Job` uses the **Name** parameter to specify a friendly job name, **GetMappingFiles**.</span></span> <span data-ttu-id="2045d-161">Parametern **InitializationScript** kör ett skript block som importerar **MapFunctions** -modulen.</span><span class="sxs-lookup"><span data-stu-id="2045d-161">The **InitializationScript** parameter runs a script block that imports the **MapFunctions** module.</span></span> <span data-ttu-id="2045d-162">Parametern **script block** körs `Get-Map` och `Set-Content` sparar data på den plats som anges i parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="2045d-162">The **ScriptBlock** parameter runs `Get-Map` and `Set-Content` saves the data in the location specified by the **Path** parameter.</span></span> <span data-ttu-id="2045d-163">Parametern **RunAs32** kör processen som 32-bit, även på ett 64-bitars operativ system.</span><span class="sxs-lookup"><span data-stu-id="2045d-163">The **RunAs32** parameter runs the process as 32-bit, even on a 64-bit operating system.</span></span>

### <span data-ttu-id="2045d-164">Exempel 7: skicka in ininformation till ett bakgrunds jobb</span><span class="sxs-lookup"><span data-stu-id="2045d-164">Example 7: Pass input to a background job</span></span>

<span data-ttu-id="2045d-165">I det här exemplet används den `$input` automatiska variabeln för att bearbeta ett indatamängds objekt.</span><span class="sxs-lookup"><span data-stu-id="2045d-165">This example uses the `$input` automatic variable to process an input object.</span></span> <span data-ttu-id="2045d-166">Används `Receive-Job` för att Visa jobbets utdata.</span><span class="sxs-lookup"><span data-stu-id="2045d-166">Use `Receive-Job` to view the job's output.</span></span>

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

<span data-ttu-id="2045d-167">`Start-Job` använder parametern **script block** för att köra `Get-Content` med den `$input` automatiska variabeln.</span><span class="sxs-lookup"><span data-stu-id="2045d-167">`Start-Job` uses the **ScriptBlock** parameter to run `Get-Content` with the `$input` automatic variable.</span></span> <span data-ttu-id="2045d-168">`$input`Variabeln hämtar objekt från **InputObject** -parametern.</span><span class="sxs-lookup"><span data-stu-id="2045d-168">The `$input` variable gets objects from the **InputObject** parameter.</span></span> <span data-ttu-id="2045d-169">`Receive-Job` använder parametern **Name** för att ange jobbet och ger resultatet utdata.</span><span class="sxs-lookup"><span data-stu-id="2045d-169">`Receive-Job` uses the **Name** parameter to specify the job and outputs the results.</span></span> <span data-ttu-id="2045d-170">Parametern **Keep** sparar jobbets utdata så att den kan visas igen under PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="2045d-170">The **Keep** parameter saves the job output so it can be viewed again during the PowerShell session.</span></span>

### <span data-ttu-id="2045d-171">Exempel 8: Använd parametern argument list för att ange en matris</span><span class="sxs-lookup"><span data-stu-id="2045d-171">Example 8: Use the ArgumentList parameter to specify an array</span></span>

<span data-ttu-id="2045d-172">I det här exemplet används parametern **argument List** för att ange en matris med argument.</span><span class="sxs-lookup"><span data-stu-id="2045d-172">This example uses the **ArgumentList** parameter to specify an array of arguments.</span></span> <span data-ttu-id="2045d-173">Matrisen är en kommaavgränsad lista med process namn.</span><span class="sxs-lookup"><span data-stu-id="2045d-173">The array is a comma-separated list of process names.</span></span>

```powershell
Start-Job -ScriptBlock { Get-Process -Name $args } -ArgumentList powershell, pwsh, notepad
```

```Output
Id     Name      PSJobTypeName   State       HasMoreData     Location     Command
--     ----      -------------   -----       -----------     --------     -------
1      Job1      BackgroundJob   Running     True            localhost    Get-Process -Name $args
```

<span data-ttu-id="2045d-174">`Start-Job`Cmdleten använder parametern **script block** för att köra ett kommando.</span><span class="sxs-lookup"><span data-stu-id="2045d-174">The `Start-Job` cmdlet uses the **ScriptBlock** parameter to run a command.</span></span> <span data-ttu-id="2045d-175">`Get-Process` använder parametern **Name** för att ange den automatiska variabeln `$args` .</span><span class="sxs-lookup"><span data-stu-id="2045d-175">`Get-Process` uses the **Name** parameter to specify the automatic variable `$args`.</span></span> <span data-ttu-id="2045d-176">Parametern **argument List** skickar matrisen med process namn till `$args` .</span><span class="sxs-lookup"><span data-stu-id="2045d-176">The **ArgumentList** parameter passes the array of process names to `$args`.</span></span> <span data-ttu-id="2045d-177">Process namnen PowerShell, pwsh och Notepad är processer som körs på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="2045d-177">The process names powershell, pwsh, and notepad are processes running on the local computer.</span></span>

<span data-ttu-id="2045d-178">Om du vill visa jobbets utdata använder du `Receive-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="2045d-178">To view the job's output, use the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="2045d-179">Till exempel `Receive-Job -Id 1`.</span><span class="sxs-lookup"><span data-stu-id="2045d-179">For example, `Receive-Job -Id 1`.</span></span>

## <span data-ttu-id="2045d-180">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="2045d-180">PARAMETERS</span></span>

### <span data-ttu-id="2045d-181">– Argument List</span><span class="sxs-lookup"><span data-stu-id="2045d-181">-ArgumentList</span></span>

<span data-ttu-id="2045d-182">Anger en matris med argument, eller parameter värden, för det skript som anges av parametern för **Sök väg** eller ett kommando som anges med parametern **script block** .</span><span class="sxs-lookup"><span data-stu-id="2045d-182">Specifies an array of arguments, or parameter values, for the script that is specified by the **FilePath** parameter or a command specified with the **ScriptBlock** parameter.</span></span>

<span data-ttu-id="2045d-183">Argument måste skickas till **argument List** som ett mat ris argument med en dimension.</span><span class="sxs-lookup"><span data-stu-id="2045d-183">Arguments must be passed to **ArgumentList** as single-dimension array argument.</span></span> <span data-ttu-id="2045d-184">Till exempel en kommaavgränsad lista.</span><span class="sxs-lookup"><span data-stu-id="2045d-184">For example, a comma-separated list.</span></span> <span data-ttu-id="2045d-185">Mer information om beteendet för **argument List** finns [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span><span class="sxs-lookup"><span data-stu-id="2045d-185">For more information about the behavior of **ArgumentList** , see [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: ComputerName, LiteralFilePathComputerName, FilePathComputerName
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2045d-186">-Autentisering</span><span class="sxs-lookup"><span data-stu-id="2045d-186">-Authentication</span></span>

<span data-ttu-id="2045d-187">Anger den mekanism som används för att autentisera användarautentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="2045d-187">Specifies the mechanism that is used to authenticate user credentials.</span></span>

<span data-ttu-id="2045d-188">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="2045d-188">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="2045d-189">Default</span><span class="sxs-lookup"><span data-stu-id="2045d-189">Default</span></span>
- <span data-ttu-id="2045d-190">Basic</span><span class="sxs-lookup"><span data-stu-id="2045d-190">Basic</span></span>
- <span data-ttu-id="2045d-191">CredSSP</span><span class="sxs-lookup"><span data-stu-id="2045d-191">Credssp</span></span>
- <span data-ttu-id="2045d-192">Sammandrag</span><span class="sxs-lookup"><span data-stu-id="2045d-192">Digest</span></span>
- <span data-ttu-id="2045d-193">Kerberos</span><span class="sxs-lookup"><span data-stu-id="2045d-193">Kerberos</span></span>
- <span data-ttu-id="2045d-194">Negotiate</span><span class="sxs-lookup"><span data-stu-id="2045d-194">Negotiate</span></span>
- <span data-ttu-id="2045d-195">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="2045d-195">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="2045d-196">Standardvärdet är default.</span><span class="sxs-lookup"><span data-stu-id="2045d-196">The default value is Default.</span></span>

<span data-ttu-id="2045d-197">CredSSP-autentisering är endast tillgängligt i Windows Vista, Windows Server 2008 och senare versioner av Windows operativ system.</span><span class="sxs-lookup"><span data-stu-id="2045d-197">CredSSP authentication is available only in Windows Vista, Windows Server 2008, and later versions of the Windows operating system.</span></span>

<span data-ttu-id="2045d-198">Mer information om värdena för den här parametern finns i [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span><span class="sxs-lookup"><span data-stu-id="2045d-198">For more information about the values of this parameter, see [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="2045d-199">CredSSP-autentisering (Credential Security Support Provider), där användarens autentiseringsuppgifter skickas till en fjärrdator som ska autentiseras, är utformad för kommandon som kräver autentisering på fler än en resurs, till exempel åtkomst till en fjärran sluten nätverks resurs.</span><span class="sxs-lookup"><span data-stu-id="2045d-199">Credential Security Support Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="2045d-200">Den här mekanismen ökar säkerhets risken för Fjärråtgärden.</span><span class="sxs-lookup"><span data-stu-id="2045d-200">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="2045d-201">Om fjärrdatorn har komprometterats kan de autentiseringsuppgifter som skickas till den användas för att kontrol lera nätverks sessionen.</span><span class="sxs-lookup"><span data-stu-id="2045d-201">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerName, LiteralFilePathComputerName, FilePathComputerName
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2045d-202">-Credential</span><span class="sxs-lookup"><span data-stu-id="2045d-202">-Credential</span></span>

<span data-ttu-id="2045d-203">Anger ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="2045d-203">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="2045d-204">Om parametern **Credential** inte anges använder kommandot den aktuella användarens autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="2045d-204">If the **Credential** parameter isn't specified, the command uses the current user's credentials.</span></span>

<span data-ttu-id="2045d-205">Ange ett användar namn, till exempel **user01** eller **Domain01\User01** , eller ange ett **PSCredential** -objekt som genererats av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="2045d-205">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="2045d-206">Om du anger ett användar namn uppmanas du att ange lösen ordet.</span><span class="sxs-lookup"><span data-stu-id="2045d-206">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="2045d-207">Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="2045d-207">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="2045d-208">Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="2045d-208">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerName, LiteralFilePathComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2045d-209">-DefinitionName</span><span class="sxs-lookup"><span data-stu-id="2045d-209">-DefinitionName</span></span>

<span data-ttu-id="2045d-210">Anger definitions namnet för det jobb som denna cmdlet startar.</span><span class="sxs-lookup"><span data-stu-id="2045d-210">Specifies the definition name of the job that this cmdlet starts.</span></span> <span data-ttu-id="2045d-211">Använd den här parametern för att starta anpassade jobb typer som har ett definitions namn, till exempel schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="2045d-211">Use this parameter to start custom job types that have a definition name, such as scheduled jobs.</span></span>

<span data-ttu-id="2045d-212">När du använder `Start-Job` för att starta en instans av ett schemalagt jobb startar jobbet omedelbart, oavsett jobb utlösare eller jobb alternativ.</span><span class="sxs-lookup"><span data-stu-id="2045d-212">When you use `Start-Job` to start an instance of a scheduled job, the job starts immediately, regardless of job triggers or job options.</span></span> <span data-ttu-id="2045d-213">Den resulterande jobb instansen är ett schemalagt jobb, men det sparas inte på disken som utlösta schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="2045d-213">The resulting job instance is a scheduled job, but it isn't saved to disk like triggered scheduled jobs.</span></span> <span data-ttu-id="2045d-214">Du kan inte använda parametern **argument List** för `Start-Job` för att ange värden för parametrar för skript som körs i ett schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="2045d-214">You can't use the **ArgumentList** parameter of `Start-Job` to provide values for parameters of scripts that run in a scheduled job.</span></span> <span data-ttu-id="2045d-215">Mer information finns i [about_Scheduled_Jobs](../PSScheduledJob/About/about_Scheduled_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="2045d-215">For more information, see [about_Scheduled_Jobs](../PSScheduledJob/About/about_Scheduled_Jobs.md).</span></span>

<span data-ttu-id="2045d-216">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="2045d-216">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="2045d-217">-DefinitionPath</span><span class="sxs-lookup"><span data-stu-id="2045d-217">-DefinitionPath</span></span>

<span data-ttu-id="2045d-218">Anger sökvägen till definitionen för jobbet som denna cmdlet startar.</span><span class="sxs-lookup"><span data-stu-id="2045d-218">Specifies path of the definition for the job that this cmdlet starts.</span></span> <span data-ttu-id="2045d-219">Ange definitions Sök vägen.</span><span class="sxs-lookup"><span data-stu-id="2045d-219">Enter the definition path.</span></span> <span data-ttu-id="2045d-220">Sammanfogningen av värdena för parametrarna **DefinitionPath** och **DefinitionName** är den fullständigt kvalificerade sökvägen för jobb definitionen.</span><span class="sxs-lookup"><span data-stu-id="2045d-220">The concatenation of the values of the **DefinitionPath** and **DefinitionName** parameters is the fully qualified path of the job definition.</span></span> <span data-ttu-id="2045d-221">Använd den här parametern för att starta anpassade jobb typer som har en definitions Sök väg, till exempel schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="2045d-221">Use this parameter to start custom job types that have a definition path, such as scheduled jobs.</span></span>

<span data-ttu-id="2045d-222">För schemalagda jobb är värdet för parametern **DefinitionPath** `$home\AppData\Local\Windows\PowerShell\ScheduledJob` .</span><span class="sxs-lookup"><span data-stu-id="2045d-222">For scheduled jobs, the value of the **DefinitionPath** parameter is `$home\AppData\Local\Windows\PowerShell\ScheduledJob`.</span></span>

<span data-ttu-id="2045d-223">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="2045d-223">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="2045d-224">-Sökväg</span><span class="sxs-lookup"><span data-stu-id="2045d-224">-FilePath</span></span>

<span data-ttu-id="2045d-225">Anger ett lokalt skript som `Start-Job` körs som ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="2045d-225">Specifies a local script that `Start-Job` runs as a background job.</span></span> <span data-ttu-id="2045d-226">Ange sökvägen och fil namnet för skriptet eller Använd pipelinen för att skicka en skript Sök väg till `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="2045d-226">Enter the path and file name of the script or use the pipeline to send a script path to `Start-Job`.</span></span> <span data-ttu-id="2045d-227">Skriptet måste finnas på den lokala datorn eller i en mapp som den lokala datorn kan komma åt.</span><span class="sxs-lookup"><span data-stu-id="2045d-227">The script must be on the local computer or in a folder that the local computer can access.</span></span>

<span data-ttu-id="2045d-228">När du använder den här parametern konverterar PowerShell innehållet i den angivna skript filen till ett-skript block och kör skript blocket som ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="2045d-228">When you use this parameter, PowerShell converts the contents of the specified script file to a script block and runs the script block as a background job.</span></span>

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

### <span data-ttu-id="2045d-229">-InitializationScript</span><span class="sxs-lookup"><span data-stu-id="2045d-229">-InitializationScript</span></span>

<span data-ttu-id="2045d-230">Anger kommandon som körs innan jobbet startas.</span><span class="sxs-lookup"><span data-stu-id="2045d-230">Specifies commands that run before the job starts.</span></span> <span data-ttu-id="2045d-231">Om du vill skapa ett skript block, omger du kommandona med klammerparenteser ( `{}` ).</span><span class="sxs-lookup"><span data-stu-id="2045d-231">To create a script block, enclose the commands in curly braces (`{}`).</span></span>

<span data-ttu-id="2045d-232">Använd den här parametern för att förbereda sessionen där jobbet körs.</span><span class="sxs-lookup"><span data-stu-id="2045d-232">Use this parameter to prepare the session in which the job runs.</span></span> <span data-ttu-id="2045d-233">Du kan till exempel använda den för att lägga till funktioner, snapin-moduler och moduler i sessionen.</span><span class="sxs-lookup"><span data-stu-id="2045d-233">For example, you can use it to add functions, snap-ins, and modules to the session.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ComputerName, LiteralFilePathComputerName, FilePathComputerName
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2045d-234">– InputObject</span><span class="sxs-lookup"><span data-stu-id="2045d-234">-InputObject</span></span>

<span data-ttu-id="2045d-235">Anger ininformation till kommandot.</span><span class="sxs-lookup"><span data-stu-id="2045d-235">Specifies input to the command.</span></span> <span data-ttu-id="2045d-236">Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som genererar objekten.</span><span class="sxs-lookup"><span data-stu-id="2045d-236">Enter a variable that contains the objects, or type a command or expression that generates the objects.</span></span>

<span data-ttu-id="2045d-237">I värdet för parametern **script block** använder du den `$input` automatiska variabeln för att representera objekten.</span><span class="sxs-lookup"><span data-stu-id="2045d-237">In the value of the **ScriptBlock** parameter, use the `$input` automatic variable to represent the input objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ComputerName, LiteralFilePathComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="2045d-238">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="2045d-238">-LiteralPath</span></span>

<span data-ttu-id="2045d-239">Anger ett lokalt skript som denna cmdlet kör som ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="2045d-239">Specifies a local script that this cmdlet runs as a background job.</span></span> <span data-ttu-id="2045d-240">Ange sökvägen till ett skript på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="2045d-240">Enter the path of a script on the local computer.</span></span>

<span data-ttu-id="2045d-241">`Start-Job` använder värdet för parametern **LiteralPath** exakt som den skrivs.</span><span class="sxs-lookup"><span data-stu-id="2045d-241">`Start-Job` uses the value of the **LiteralPath** parameter exactly as it's typed.</span></span> <span data-ttu-id="2045d-242">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="2045d-242">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="2045d-243">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="2045d-243">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="2045d-244">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="2045d-244">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: LiteralFilePathComputerName
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2045d-245">-Name</span><span class="sxs-lookup"><span data-stu-id="2045d-245">-Name</span></span>

<span data-ttu-id="2045d-246">Anger ett eget namn för det nya jobbet.</span><span class="sxs-lookup"><span data-stu-id="2045d-246">Specifies a friendly name for the new job.</span></span> <span data-ttu-id="2045d-247">Du kan använda namnet för att identifiera jobbet till andra jobb-cmdlet: ar, till exempel `Stop-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="2045d-247">You can use the name to identify the job to other job cmdlets, such as the `Stop-Job` cmdlet.</span></span>

<span data-ttu-id="2045d-248">Det egna standard namnet är `Job#` , där `#` är ett ordnings tal som ökar för varje jobb.</span><span class="sxs-lookup"><span data-stu-id="2045d-248">The default friendly name is `Job#`, where `#` is an ordinal number that is incremented for each job.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName, LiteralFilePathComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2045d-249">– PSVersion</span><span class="sxs-lookup"><span data-stu-id="2045d-249">-PSVersion</span></span>

<span data-ttu-id="2045d-250">Anger en version.</span><span class="sxs-lookup"><span data-stu-id="2045d-250">Specifies a version.</span></span> <span data-ttu-id="2045d-251">`Start-Job` Kör jobbet med PowerShell-versionen.</span><span class="sxs-lookup"><span data-stu-id="2045d-251">`Start-Job` runs the job with the version of PowerShell.</span></span> <span data-ttu-id="2045d-252">De acceptabla värdena för den här parametern är: `2.0` och `3.0` .</span><span class="sxs-lookup"><span data-stu-id="2045d-252">The acceptable values for this parameter are: `2.0` and `3.0`.</span></span>

<span data-ttu-id="2045d-253">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="2045d-253">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Version
Parameter Sets: ComputerName, LiteralFilePathComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2045d-254">-RunAs32</span><span class="sxs-lookup"><span data-stu-id="2045d-254">-RunAs32</span></span>

<span data-ttu-id="2045d-255">Anger att `Start-Job` jobbet körs i en 32-bitars process.</span><span class="sxs-lookup"><span data-stu-id="2045d-255">Indicates that `Start-Job` runs the job in a 32-bit process.</span></span> <span data-ttu-id="2045d-256">**RunAs32** tvingar jobbet att köras i en 32-bitars process, även på ett 64-bitars operativ system.</span><span class="sxs-lookup"><span data-stu-id="2045d-256">**RunAs32** forces the job to run in a 32-bit process, even on a 64-bit operating system.</span></span>

<span data-ttu-id="2045d-257">I 64-bitars versioner av Windows 7 och Windows Server 2008 R2 kan `Start-Job` du inte använda parametern **Credential** för att ange autentiseringsuppgifterna för en annan användare när kommandot innehåller parametern **RunAs32** .</span><span class="sxs-lookup"><span data-stu-id="2045d-257">On 64-bit versions of Windows 7 and Windows Server 2008 R2, when the `Start-Job` command includes the **RunAs32** parameter, you can't use the **Credential** parameter to specify the credentials of another user.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, LiteralFilePathComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2045d-258">– Script block</span><span class="sxs-lookup"><span data-stu-id="2045d-258">-ScriptBlock</span></span>

<span data-ttu-id="2045d-259">Anger vilka kommandon som ska köras i bakgrunds jobbet.</span><span class="sxs-lookup"><span data-stu-id="2045d-259">Specifies the commands to run in the background job.</span></span> <span data-ttu-id="2045d-260">Om du vill skapa ett skript block, omger du kommandona med klammerparenteser ( `{}` ).</span><span class="sxs-lookup"><span data-stu-id="2045d-260">To create a script block, enclose the commands in curly braces (`{}`).</span></span> <span data-ttu-id="2045d-261">Använd den `$input` automatiska variabeln för att få åtkomst till värdet för parametern **InputObject** .</span><span class="sxs-lookup"><span data-stu-id="2045d-261">Use the `$input` automatic variable to access the value of the **InputObject** parameter.</span></span> <span data-ttu-id="2045d-262">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="2045d-262">This parameter is required.</span></span>

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

### <span data-ttu-id="2045d-263">-Typ</span><span class="sxs-lookup"><span data-stu-id="2045d-263">-Type</span></span>

<span data-ttu-id="2045d-264">Anger den anpassade typen för jobb som startas av `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="2045d-264">Specifies the custom type for jobs started by `Start-Job`.</span></span> <span data-ttu-id="2045d-265">Ange ett namn på en anpassad Jobbtyp, till exempel PSScheduledJob för schemalagda jobb eller PSWorkflowJob för arbets flödes jobb.</span><span class="sxs-lookup"><span data-stu-id="2045d-265">Enter a custom job type name, such as PSScheduledJob for scheduled jobs or PSWorkflowJob for workflows jobs.</span></span> <span data-ttu-id="2045d-266">Den här parametern är inte giltig för standard bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="2045d-266">This parameter isn't valid for standard background jobs.</span></span>

<span data-ttu-id="2045d-267">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="2045d-267">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="2045d-268">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2045d-268">CommonParameters</span></span>

<span data-ttu-id="2045d-269">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2045d-269">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2045d-270">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="2045d-270">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2045d-271">INDATA</span><span class="sxs-lookup"><span data-stu-id="2045d-271">INPUTS</span></span>

### <span data-ttu-id="2045d-272">System. String</span><span class="sxs-lookup"><span data-stu-id="2045d-272">System.String</span></span>

<span data-ttu-id="2045d-273">Du kan använda pipelinen för att skicka ett objekt med egenskapen **Name** till parametern **Name** .</span><span class="sxs-lookup"><span data-stu-id="2045d-273">You can use the pipeline to send an object with the **Name** property to the **Name** parameter.</span></span> <span data-ttu-id="2045d-274">Du kan till exempel pipelina ett **fileinfo** -objekt från `Get-ChildItem` till `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="2045d-274">For example, you can pipeline a **FileInfo** object from `Get-ChildItem` to `Start-Job`.</span></span>

## <span data-ttu-id="2045d-275">UTDATA</span><span class="sxs-lookup"><span data-stu-id="2045d-275">OUTPUTS</span></span>

### <span data-ttu-id="2045d-276">System. Management. Automation. PSRemotingJob</span><span class="sxs-lookup"><span data-stu-id="2045d-276">System.Management.Automation.PSRemotingJob</span></span>

<span data-ttu-id="2045d-277">`Start-Job` Returnerar ett **PSRemotingJob** -objekt som representerar det jobb som startades.</span><span class="sxs-lookup"><span data-stu-id="2045d-277">`Start-Job` returns a **PSRemotingJob** object that represents the job that it started.</span></span>

## <span data-ttu-id="2045d-278">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="2045d-278">NOTES</span></span>

<span data-ttu-id="2045d-279">För att köra i bakgrunden `Start-Job` körs i en egen session i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="2045d-279">To run in the background, `Start-Job` runs in its own session in the current session.</span></span> <span data-ttu-id="2045d-280">När du använder `Invoke-Command` cmdleten för att köra ett `Start-Job` kommando i en session på en fjärrdator `Start-Job` körs i en session i fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="2045d-280">When you use the `Invoke-Command` cmdlet to run a `Start-Job` command in a session on a remote computer, `Start-Job` runs in a session in the remote session.</span></span>

## <span data-ttu-id="2045d-281">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="2045d-281">RELATED LINKS</span></span>

[<span data-ttu-id="2045d-282">about_Arrays</span><span class="sxs-lookup"><span data-stu-id="2045d-282">about_Arrays</span></span>](./about/about_arrays.md)

[<span data-ttu-id="2045d-283">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="2045d-283">about_Automatic_Variables</span></span>](./about/about_automatic_variables.md)

[<span data-ttu-id="2045d-284">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="2045d-284">about_Jobs</span></span>](./About/about_Jobs.md)

[<span data-ttu-id="2045d-285">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="2045d-285">about_Job_Details</span></span>](./About/about_Job_Details.md)

[<span data-ttu-id="2045d-286">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="2045d-286">about_Remote_Jobs</span></span>](./About/about_Remote_Jobs.md)

[<span data-ttu-id="2045d-287">Hämta jobb</span><span class="sxs-lookup"><span data-stu-id="2045d-287">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="2045d-288">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="2045d-288">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="2045d-289">Mottagning – jobb</span><span class="sxs-lookup"><span data-stu-id="2045d-289">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="2045d-290">Ta bort – jobb</span><span class="sxs-lookup"><span data-stu-id="2045d-290">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="2045d-291">Återuppta – jobb</span><span class="sxs-lookup"><span data-stu-id="2045d-291">Resume-Job</span></span>](Resume-Job.md)

[<span data-ttu-id="2045d-292">Stoppa – jobb</span><span class="sxs-lookup"><span data-stu-id="2045d-292">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="2045d-293">Pausa – jobb</span><span class="sxs-lookup"><span data-stu-id="2045d-293">Suspend-Job</span></span>](Suspend-Job.md)

[<span data-ttu-id="2045d-294">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="2045d-294">Wait-Job</span></span>](Wait-Job.md)
