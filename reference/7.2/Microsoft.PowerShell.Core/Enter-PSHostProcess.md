---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pshostprocess?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enter-PSHostProcess
ms.openlocfilehash: 85cbc9d012781873dddaf2a7d220a0e478dcbda2
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709594"
---
# <span data-ttu-id="ee18f-102">Enter-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="ee18f-102">Enter-PSHostProcess</span></span>

## <span data-ttu-id="ee18f-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="ee18f-103">SYNOPSIS</span></span>
<span data-ttu-id="ee18f-104">Ansluter till och går in i en interaktiv session med en lokal process.</span><span class="sxs-lookup"><span data-stu-id="ee18f-104">Connects to and enters into an interactive session with a local process.</span></span>

## <span data-ttu-id="ee18f-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ee18f-105">SYNTAX</span></span>

### <span data-ttu-id="ee18f-106">ProcessIdParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="ee18f-106">ProcessIdParameterSet (Default)</span></span>

```
Enter-PSHostProcess [-Id] <Int32> [[-AppDomainName] <String>] [<CommonParameters>]
```

### <span data-ttu-id="ee18f-107">ProcessParameterSet</span><span class="sxs-lookup"><span data-stu-id="ee18f-107">ProcessParameterSet</span></span>

```
Enter-PSHostProcess [-Process] <Process> [[-AppDomainName] <String>] [<CommonParameters>]
```

### <span data-ttu-id="ee18f-108">ProcessNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="ee18f-108">ProcessNameParameterSet</span></span>

```
Enter-PSHostProcess [-Name] <String> [[-AppDomainName] <String>] [<CommonParameters>]
```

### <span data-ttu-id="ee18f-109">PSHostProcessInfoParameterSet</span><span class="sxs-lookup"><span data-stu-id="ee18f-109">PSHostProcessInfoParameterSet</span></span>

```
Enter-PSHostProcess [-HostProcessInfo] <PSHostProcessInfo> [[-AppDomainName] <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="ee18f-110">PipeNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="ee18f-110">PipeNameParameterSet</span></span>

```
Enter-PSHostProcess -CustomPipeName <String> [<CommonParameters>]
```

## <span data-ttu-id="ee18f-111">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="ee18f-111">DESCRIPTION</span></span>

<span data-ttu-id="ee18f-112">`Enter-PSHostProcess`Cmdleten ansluter till och går in i en interaktiv session med en lokal process.</span><span class="sxs-lookup"><span data-stu-id="ee18f-112">The `Enter-PSHostProcess` cmdlet connects to and enters into an interactive session with a local process.</span></span> <span data-ttu-id="ee18f-113">Från och med PowerShell 6,2 stöds denna cmdlet på plattformar som inte är Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="ee18f-113">Beginning in PowerShell 6.2, this cmdlet is supported on non-Windows platforms.</span></span>

<span data-ttu-id="ee18f-114">I stället för att skapa en ny process som är värd för PowerShell och köra en fjärrsession, körs den interaktiva sessionen i en befintlig process som redan kör PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ee18f-114">Instead of creating a new process to host PowerShell and run a remote session, the remote, interactive session is run in an existing process that is already running PowerShell.</span></span> <span data-ttu-id="ee18f-115">När du interagerar med en fjärrsession i en angiven process kan du räkna upp körnings körnings utrymmen och sedan välja en körnings utrymme för att felsöka genom att köra antingen `Debug-Runspace` eller `Enable-RunspaceDebug` .</span><span class="sxs-lookup"><span data-stu-id="ee18f-115">When you are interacting with a remote session on a specified process, you can enumerate running runspaces, and then select a runspace to debug by running either `Debug-Runspace` or `Enable-RunspaceDebug`.</span></span>

<span data-ttu-id="ee18f-116">Den process som du vill ange måste vara värd för PowerShell (System.Management.Automation.dll).</span><span class="sxs-lookup"><span data-stu-id="ee18f-116">The process that you want to enter must be hosting PowerShell (System.Management.Automation.dll).</span></span>
<span data-ttu-id="ee18f-117">Du måste antingen vara medlem i gruppen Administratörer på den dator där processen finns, eller så måste du vara den användare som kör skriptet som startade processen.</span><span class="sxs-lookup"><span data-stu-id="ee18f-117">You must be either a member of the Administrators group on the computer on which the process is found, or you must be the user who is running the script that started the process.</span></span>

<span data-ttu-id="ee18f-118">När du har valt en körnings utrymme för fel sökning öppnas en fjärrfelsökning för körnings utrymme om den antingen kör ett kommando eller stoppas i fel söknings programmet.</span><span class="sxs-lookup"><span data-stu-id="ee18f-118">After you have selected a runspace to debug, a remote debug session is opened for the runspace if it is either currently running a command or is stopped in the debugger.</span></span> <span data-ttu-id="ee18f-119">Du kan sedan felsöka körnings utrymme-skriptet på samma sätt som du felsöker andra skript för fjärrsessioner.</span><span class="sxs-lookup"><span data-stu-id="ee18f-119">You can then debug the runspace script in the same way you would debug other remote session scripts.</span></span>

<span data-ttu-id="ee18f-120">Koppla från en felsökningssession och sedan den interaktiva sessionen med processen, genom att avsluta två gånger, eller stoppa skript körningen genom att köra det befintliga fel söknings kommandot avsluta.</span><span class="sxs-lookup"><span data-stu-id="ee18f-120">Detach from a debugging session, and then the interactive session with the process, by running exit twice, or stop script execution by running the existing debugger quit command.</span></span>

<span data-ttu-id="ee18f-121">Om du anger en process med hjälp av **namn** parametern, och det bara finns en process med det angivna namnet, anges processen.</span><span class="sxs-lookup"><span data-stu-id="ee18f-121">If you specify a process by using the **Name** parameter, and there is only one process found with the specified name, the process is entered.</span></span> <span data-ttu-id="ee18f-122">Om mer än en process med det angivna namnet hittas returnerar PowerShell ett fel och visar en lista över alla processer med det angivna namnet.</span><span class="sxs-lookup"><span data-stu-id="ee18f-122">If more than one process with the specified name is found, PowerShell returns an error, and lists all processes found with the specified name.</span></span>

<span data-ttu-id="ee18f-123">För att stödja anslutning till processer på fjärrdatorer `Enter-PSHostProcess` är cmdleten aktive rad på en angiven fjärrdator, så att du kan ansluta till en lokal process inom en fjärran sluten PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="ee18f-123">To support attaching to processes on remote computers, the `Enter-PSHostProcess` cmdlet is enabled in a specified remote computer, so that you can attach to a local process within a remote PowerShell session.</span></span>

## <span data-ttu-id="ee18f-124">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="ee18f-124">EXAMPLES</span></span>

### <span data-ttu-id="ee18f-125">Exempel 1: starta fel sökning av en körnings utrymme i PowerShell ISE-processen</span><span class="sxs-lookup"><span data-stu-id="ee18f-125">Example 1: Start debugging a runspace within the PowerShell ISE process</span></span>

<span data-ttu-id="ee18f-126">I det här exemplet ska du köra `Enter-PSHostProcess` från PowerShell-konsolen för att ange POWERSHELL ISE-processen.</span><span class="sxs-lookup"><span data-stu-id="ee18f-126">In this example, you run `Enter-PSHostProcess` from within the PowerShell console to enter the PowerShell ISE process.</span></span> <span data-ttu-id="ee18f-127">I den resulterande interaktiva sessionen kan du hitta en körnings utrymme som du vill felsöka genom att köra `Get-Runspace` och sedan felsöka körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="ee18f-127">In the resulting interactive session, you can find a runspace that you want to debug by running `Get-Runspace`, and then debug the runspace.</span></span>

```
PS C:\> Enter-PSHostProcess -Name powershell_ise
[Process:1520]: PS C:\Test\Documents>

Next, get available runspaces within the process you have entered.
PS C:\> [Process:1520]: PS C:\>  Get-Runspace
Id    Name          InstanceId                               State           Availability
--    -------       -----------                              ------          -------------
1     Runspace1     2d91211d-9cce-42f0-ab0e-71ac258b32b5     Opened          Available
2     Runspace2     a3855043-cb16-424a-a616-685360c3763b     Opened          RemoteDebug
3     MyLocalRS     2236dbd8-2105-4dec-a15a-a27d0bfaacb5     Opened          LocalDebug
4     MyRunspace    771356e9-8c44-4b70-9de5-dd17cb41e48e     Opened          Busy
5     Runspace8     3e517382-a97a-49ba-9c3c-fd21f6664288     Broken          None

The runspace objects returned by Get-Runspace also have a NoteProperty called ScriptStackTrace of
the running command stack, if available.Next, debug runspace ID 4, that is running another user's
long-running script. From the list returned from Get-Runspace, note that the runspace state is
Opened, and Availability is Busy, meaning that the runspace is still running the long-running
script.

PS C:\> [Process:1520]: PS C:\>  (Get-Runspace -Id 4).ScriptStackTrace
Command                    Arguments                           Location
-------                    ---------                           --------
MyModuleWorkflowF1         {}                                  TestNoFile3.psm1: line 6
WFTest1                    {}                                  TestNoFile2.ps1: line 14
TestNoFile2.ps1            {}                                  TestNoFile2.ps1: line 22
<ScriptBlock>              {}                                  <No file>

Start an interactive debugging session with this runspace by running the Debug-Runspace cmdlet.

PS C:\> [Process: 1520]: PS C:\>  Debug-Runspace -Id 4
Hit Line breakpoint on 'C:\TestWFVar1.ps1:83'

At C:\TestWFVar1.ps1:83 char:1
+ $scriptVar = "Script Variable"
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[Process: 1520]: [RSDBG: 4]: PS C:\> >

After you are finished debugging, allow the script to continue running without the debugger attached
by running the exit debugger command. Alternatively, you can quit the debugger with the q or Stop
commands.

PS C:\> [Process:346]: [RSDBG: 3]: PS C:\> > exit
[Process:1520]: PS C:\>

When you are finished working in the process, exit the process by running the Exit-PSHostProcess
cmdlet. This returns you to the PS C:\> prompt.

PS C:\> [Process:1520]: PS C:\>  Exit-PSHostProcess
PS C:\>
```

## <span data-ttu-id="ee18f-128">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="ee18f-128">PARAMETERS</span></span>

### <span data-ttu-id="ee18f-129">-AppDomainName</span><span class="sxs-lookup"><span data-stu-id="ee18f-129">-AppDomainName</span></span>

<span data-ttu-id="ee18f-130">Anger ett program domän namn som ska anslutas till om det utelämnas används **DefaultAppDomain**.</span><span class="sxs-lookup"><span data-stu-id="ee18f-130">Specifies an application domain name to connect to if omitted, uses **DefaultAppDomain**.</span></span> <span data-ttu-id="ee18f-131">Används `Get-PSHostProcessInfo` för att Visa programmets domän namn.</span><span class="sxs-lookup"><span data-stu-id="ee18f-131">Use `Get-PSHostProcessInfo` to display the application domain names.</span></span>

```yaml
Type: System.String
Parameter Sets: ProcessIdParameterSet, ProcessParameterSet, ProcessNameParameterSet, PSHostProcessInfoParameterSet
Aliases:

Required: False
Position: 1
Default value: DefaultAppDomain
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ee18f-132">-HostProcessInfo</span><span class="sxs-lookup"><span data-stu-id="ee18f-132">-HostProcessInfo</span></span>

<span data-ttu-id="ee18f-133">Anger ett **PSHostProcessInfo** -objekt som kan anslutas till med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ee18f-133">Specifies a **PSHostProcessInfo** object that can be connected to with PowerShell.</span></span> <span data-ttu-id="ee18f-134">Används `Get-PSHostProcessInfo` för att hämta objektet.</span><span class="sxs-lookup"><span data-stu-id="ee18f-134">Use `Get-PSHostProcessInfo` to get the object.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.PSHostProcessInfo
Parameter Sets: PSHostProcessInfoParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="ee18f-135">-ID</span><span class="sxs-lookup"><span data-stu-id="ee18f-135">-Id</span></span>

<span data-ttu-id="ee18f-136">Anger en process med process-ID.</span><span class="sxs-lookup"><span data-stu-id="ee18f-136">Specifies a process by the process ID.</span></span> <span data-ttu-id="ee18f-137">Kör cmdleten för att hämta ett process-ID `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="ee18f-137">To get a process ID, run the `Get-Process` cmdlet.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ProcessIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ee18f-138">-Name</span><span class="sxs-lookup"><span data-stu-id="ee18f-138">-Name</span></span>

<span data-ttu-id="ee18f-139">Anger en process efter process namnet.</span><span class="sxs-lookup"><span data-stu-id="ee18f-139">Specifies a process by the process name.</span></span> <span data-ttu-id="ee18f-140">Kör cmdleten för att få ett process namn `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="ee18f-140">To get a process name, run the `Get-Process` cmdlet.</span></span> <span data-ttu-id="ee18f-141">Du kan också hämta process namn från dialog rutan Egenskaper för en process i aktivitets hanteraren.</span><span class="sxs-lookup"><span data-stu-id="ee18f-141">You can also get process names from the Properties dialog box of a process in Task Manager.</span></span>

```yaml
Type: System.String
Parameter Sets: ProcessNameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ee18f-142">– Process</span><span class="sxs-lookup"><span data-stu-id="ee18f-142">-Process</span></span>

<span data-ttu-id="ee18f-143">Anger en process av objektet process.</span><span class="sxs-lookup"><span data-stu-id="ee18f-143">Specifies a process by the process object.</span></span> <span data-ttu-id="ee18f-144">Det enklaste sättet att använda den här parametern är att spara resultatet av ett `Get-Process` kommando som returnerar en process som du vill ange i en variabel och sedan ange variabeln som värde för den här parametern.</span><span class="sxs-lookup"><span data-stu-id="ee18f-144">The simplest way to use this parameter is to save the results of a `Get-Process` command that returns process that you want to enter in a variable, and then specify the variable as the value of this parameter.</span></span>

```yaml
Type: System.Diagnostics.Process
Parameter Sets: ProcessParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="ee18f-145">-CustomPipeName</span><span class="sxs-lookup"><span data-stu-id="ee18f-145">-CustomPipeName</span></span>

<span data-ttu-id="ee18f-146">Hämtar eller anger namnet på den anpassade namngivna pipe som ska anslutas till.</span><span class="sxs-lookup"><span data-stu-id="ee18f-146">Gets or sets the custom named pipe name to connect to.</span></span> <span data-ttu-id="ee18f-147">Detta används vanligt vis tillsammans med `pwsh -CustomPipeName` .</span><span class="sxs-lookup"><span data-stu-id="ee18f-147">This is usually used in conjunction with `pwsh -CustomPipeName`.</span></span>

<span data-ttu-id="ee18f-148">Den här parametern introducerades i PowerShell 6,2.</span><span class="sxs-lookup"><span data-stu-id="ee18f-148">This parameter was introduced in PowerShell 6.2.</span></span>

```yaml
Type: System.String
Parameter Sets: PipeNameParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ee18f-149">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ee18f-149">CommonParameters</span></span>

<span data-ttu-id="ee18f-150">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ee18f-150">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ee18f-151">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="ee18f-151">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ee18f-152">INDATA</span><span class="sxs-lookup"><span data-stu-id="ee18f-152">INPUTS</span></span>

### <span data-ttu-id="ee18f-153">System. Diagnostics. process</span><span class="sxs-lookup"><span data-stu-id="ee18f-153">System.Diagnostics.Process</span></span>

## <span data-ttu-id="ee18f-154">UTDATA</span><span class="sxs-lookup"><span data-stu-id="ee18f-154">OUTPUTS</span></span>

## <span data-ttu-id="ee18f-155">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="ee18f-155">NOTES</span></span>

<span data-ttu-id="ee18f-156">`Enter-PSHostProcess` Det går inte att ange processen för PowerShell-sessionen där du kör kommandot.</span><span class="sxs-lookup"><span data-stu-id="ee18f-156">`Enter-PSHostProcess` cannot enter the process of the PowerShell session in which you are running the command.</span></span> <span data-ttu-id="ee18f-157">Du kan dock ange processen för en annan PowerShell-session eller en PowerShell ISE-session som körs samtidigt som den session där du kör `Enter-PSHostProcess` .</span><span class="sxs-lookup"><span data-stu-id="ee18f-157">You can, however, enter the process of another PowerShell session, or a PowerShell ISE session that is running at the same time as the session in which you are running `Enter-PSHostProcess`.</span></span>

<span data-ttu-id="ee18f-158">`Enter-PSHostProcess` kan bara ange de processer som är värdar för PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ee18f-158">`Enter-PSHostProcess` can enter only those processes that are hosting PowerShell.</span></span> <span data-ttu-id="ee18f-159">Det vill säga att de har läst in PowerShell-motorn.</span><span class="sxs-lookup"><span data-stu-id="ee18f-159">That is, they have loaded the PowerShell engine.</span></span>

<span data-ttu-id="ee18f-160">Om du vill avsluta en process inifrån processen skriver du **exit** och trycker på <kbd>RETUR</kbd>.</span><span class="sxs-lookup"><span data-stu-id="ee18f-160">To exit a process from within the process, type **exit**, and then press <kbd>Enter</kbd>.</span></span>

<span data-ttu-id="ee18f-161">Före PowerShell 7,1 har fjärr kommunikation via SSH inte stöd för andra hopp-fjärrsessioner.</span><span class="sxs-lookup"><span data-stu-id="ee18f-161">Prior to PowerShell 7.1, remoting over SSH did not support second-hop remote sessions.</span></span> <span data-ttu-id="ee18f-162">Den här funktionen var begränsad till sessioner som använder WinRM.</span><span class="sxs-lookup"><span data-stu-id="ee18f-162">This capability was limited to sessions using WinRM.</span></span> <span data-ttu-id="ee18f-163">PowerShell 7,1 tillåter `Enter-PSSession` och `Enter-PSHostProcess` fungerar inifrån en interaktiv fjärrsession.</span><span class="sxs-lookup"><span data-stu-id="ee18f-163">PowerShell 7.1 allows `Enter-PSSession` and `Enter-PSHostProcess` to work from within any interactive remote session.</span></span>

## <span data-ttu-id="ee18f-164">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="ee18f-164">RELATED LINKS</span></span>

[<span data-ttu-id="ee18f-165">Avsluta-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="ee18f-165">Exit-PSHostProcess</span></span>](Exit-PSHostProcess.md)

[<span data-ttu-id="ee18f-166">Get-PSHostProcessInfo</span><span class="sxs-lookup"><span data-stu-id="ee18f-166">Get-PSHostProcessInfo</span></span>](Get-PSHostProcessInfo.md)

