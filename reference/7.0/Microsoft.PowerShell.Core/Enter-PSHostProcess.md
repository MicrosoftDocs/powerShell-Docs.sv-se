---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 11/04/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pshostprocess?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enter-PSHostProcess
ms.openlocfilehash: eb20101fda394b97fc6470e32a8a70665101471b
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262634"
---
# <span data-ttu-id="20376-103">Enter-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="20376-103">Enter-PSHostProcess</span></span>

## <span data-ttu-id="20376-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="20376-104">SYNOPSIS</span></span>
<span data-ttu-id="20376-105">Ansluter till och går in i en interaktiv session med en lokal process.</span><span class="sxs-lookup"><span data-stu-id="20376-105">Connects to and enters into an interactive session with a local process.</span></span>

## <span data-ttu-id="20376-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="20376-106">SYNTAX</span></span>

### <span data-ttu-id="20376-107">ProcessIdParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="20376-107">ProcessIdParameterSet (Default)</span></span>

```
Enter-PSHostProcess [-Id] <Int32> [[-AppDomainName] <String>] [<CommonParameters>]
```

### <span data-ttu-id="20376-108">ProcessParameterSet</span><span class="sxs-lookup"><span data-stu-id="20376-108">ProcessParameterSet</span></span>

```
Enter-PSHostProcess [-Process] <Process> [[-AppDomainName] <String>] [<CommonParameters>]
```

### <span data-ttu-id="20376-109">ProcessNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="20376-109">ProcessNameParameterSet</span></span>

```
Enter-PSHostProcess [-Name] <String> [[-AppDomainName] <String>] [<CommonParameters>]
```

### <span data-ttu-id="20376-110">PSHostProcessInfoParameterSet</span><span class="sxs-lookup"><span data-stu-id="20376-110">PSHostProcessInfoParameterSet</span></span>

```
Enter-PSHostProcess [-HostProcessInfo] <PSHostProcessInfo> [[-AppDomainName] <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="20376-111">PipeNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="20376-111">PipeNameParameterSet</span></span>

```
Enter-PSHostProcess -CustomPipeName <String> [<CommonParameters>]
```

## <span data-ttu-id="20376-112">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="20376-112">DESCRIPTION</span></span>

<span data-ttu-id="20376-113">`Enter-PSHostProcess`Cmdleten ansluter till och går in i en interaktiv session med en lokal process.</span><span class="sxs-lookup"><span data-stu-id="20376-113">The `Enter-PSHostProcess` cmdlet connects to and enters into an interactive session with a local process.</span></span> <span data-ttu-id="20376-114">Från och med PowerShell 6,2 stöds denna cmdlet på plattformar som inte är Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="20376-114">Beginning in PowerShell 6.2, this cmdlet is supported on non-Windows platforms.</span></span>

<span data-ttu-id="20376-115">I stället för att skapa en ny process som är värd för PowerShell och köra en fjärrsession, körs den interaktiva sessionen i en befintlig process som redan kör PowerShell.</span><span class="sxs-lookup"><span data-stu-id="20376-115">Instead of creating a new process to host PowerShell and run a remote session, the remote, interactive session is run in an existing process that is already running PowerShell.</span></span> <span data-ttu-id="20376-116">När du interagerar med en fjärrsession i en angiven process kan du räkna upp körnings körnings utrymmen och sedan välja en körnings utrymme för att felsöka genom att köra antingen `Debug-Runspace` eller `Enable-RunspaceDebug` .</span><span class="sxs-lookup"><span data-stu-id="20376-116">When you are interacting with a remote session on a specified process, you can enumerate running runspaces, and then select a runspace to debug by running either `Debug-Runspace` or `Enable-RunspaceDebug`.</span></span>

<span data-ttu-id="20376-117">Den process som du vill ange måste vara värd för PowerShell (System.Management.Automation.dll).</span><span class="sxs-lookup"><span data-stu-id="20376-117">The process that you want to enter must be hosting PowerShell (System.Management.Automation.dll).</span></span>
<span data-ttu-id="20376-118">Du måste antingen vara medlem i gruppen Administratörer på den dator där processen finns, eller så måste du vara den användare som kör skriptet som startade processen.</span><span class="sxs-lookup"><span data-stu-id="20376-118">You must be either a member of the Administrators group on the computer on which the process is found, or you must be the user who is running the script that started the process.</span></span>

<span data-ttu-id="20376-119">När du har valt en körnings utrymme för fel sökning öppnas en fjärrfelsökning för körnings utrymme om den antingen kör ett kommando eller stoppas i fel söknings programmet.</span><span class="sxs-lookup"><span data-stu-id="20376-119">After you have selected a runspace to debug, a remote debug session is opened for the runspace if it is either currently running a command or is stopped in the debugger.</span></span> <span data-ttu-id="20376-120">Du kan sedan felsöka körnings utrymme-skriptet på samma sätt som du felsöker andra skript för fjärrsessioner.</span><span class="sxs-lookup"><span data-stu-id="20376-120">You can then debug the runspace script in the same way you would debug other remote session scripts.</span></span>

<span data-ttu-id="20376-121">Koppla från en felsökningssession och sedan den interaktiva sessionen med processen, genom att avsluta två gånger, eller stoppa skript körningen genom att köra det befintliga fel söknings kommandot avsluta.</span><span class="sxs-lookup"><span data-stu-id="20376-121">Detach from a debugging session, and then the interactive session with the process, by running exit twice, or stop script execution by running the existing debugger quit command.</span></span>

<span data-ttu-id="20376-122">Om du anger en process med hjälp av **namn** parametern, och det bara finns en process med det angivna namnet, anges processen.</span><span class="sxs-lookup"><span data-stu-id="20376-122">If you specify a process by using the **Name** parameter, and there is only one process found with the specified name, the process is entered.</span></span> <span data-ttu-id="20376-123">Om mer än en process med det angivna namnet hittas returnerar PowerShell ett fel och visar en lista över alla processer med det angivna namnet.</span><span class="sxs-lookup"><span data-stu-id="20376-123">If more than one process with the specified name is found, PowerShell returns an error, and lists all processes found with the specified name.</span></span>

<span data-ttu-id="20376-124">För att stödja anslutning till processer på fjärrdatorer `Enter-PSHostProcess` är cmdleten aktive rad på en angiven fjärrdator, så att du kan ansluta till en lokal process inom en fjärran sluten PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="20376-124">To support attaching to processes on remote computers, the `Enter-PSHostProcess` cmdlet is enabled in a specified remote computer, so that you can attach to a local process within a remote PowerShell session.</span></span>

## <span data-ttu-id="20376-125">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="20376-125">EXAMPLES</span></span>

### <span data-ttu-id="20376-126">Exempel 1: starta fel sökning av en körnings utrymme i PowerShell ISE-processen</span><span class="sxs-lookup"><span data-stu-id="20376-126">Example 1: Start debugging a runspace within the PowerShell ISE process</span></span>

<span data-ttu-id="20376-127">I det här exemplet ska du köra `Enter-PSHostProcess` från PowerShell-konsolen för att ange POWERSHELL ISE-processen.</span><span class="sxs-lookup"><span data-stu-id="20376-127">In this example, you run `Enter-PSHostProcess` from within the PowerShell console to enter the PowerShell ISE process.</span></span> <span data-ttu-id="20376-128">I den resulterande interaktiva sessionen kan du hitta en körnings utrymme som du vill felsöka genom att köra `Get-Runspace` och sedan felsöka körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="20376-128">In the resulting interactive session, you can find a runspace that you want to debug by running `Get-Runspace`, and then debug the runspace.</span></span>

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

## <span data-ttu-id="20376-129">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="20376-129">PARAMETERS</span></span>

### <span data-ttu-id="20376-130">-AppDomainName</span><span class="sxs-lookup"><span data-stu-id="20376-130">-AppDomainName</span></span>

<span data-ttu-id="20376-131">Anger ett program domän namn som ska anslutas till om det utelämnas används **DefaultAppDomain**.</span><span class="sxs-lookup"><span data-stu-id="20376-131">Specifies an application domain name to connect to if omitted, uses **DefaultAppDomain**.</span></span> <span data-ttu-id="20376-132">Används `Get-PSHostProcessInfo` för att Visa programmets domän namn.</span><span class="sxs-lookup"><span data-stu-id="20376-132">Use `Get-PSHostProcessInfo` to display the application domain names.</span></span>

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

### <span data-ttu-id="20376-133">-HostProcessInfo</span><span class="sxs-lookup"><span data-stu-id="20376-133">-HostProcessInfo</span></span>

<span data-ttu-id="20376-134">Anger ett **PSHostProcessInfo** -objekt som kan anslutas till med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="20376-134">Specifies a **PSHostProcessInfo** object that can be connected to with PowerShell.</span></span> <span data-ttu-id="20376-135">Används `Get-PSHostProcessInfo` för att hämta objektet.</span><span class="sxs-lookup"><span data-stu-id="20376-135">Use `Get-PSHostProcessInfo` to get the object.</span></span>

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

### <span data-ttu-id="20376-136">-ID</span><span class="sxs-lookup"><span data-stu-id="20376-136">-Id</span></span>

<span data-ttu-id="20376-137">Anger en process med process-ID.</span><span class="sxs-lookup"><span data-stu-id="20376-137">Specifies a process by the process ID.</span></span> <span data-ttu-id="20376-138">Kör cmdleten för att hämta ett process-ID `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="20376-138">To get a process ID, run the `Get-Process` cmdlet.</span></span>

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

### <span data-ttu-id="20376-139">-Name</span><span class="sxs-lookup"><span data-stu-id="20376-139">-Name</span></span>

<span data-ttu-id="20376-140">Anger en process efter process namnet.</span><span class="sxs-lookup"><span data-stu-id="20376-140">Specifies a process by the process name.</span></span> <span data-ttu-id="20376-141">Kör cmdleten för att få ett process namn `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="20376-141">To get a process name, run the `Get-Process` cmdlet.</span></span> <span data-ttu-id="20376-142">Du kan också hämta process namn från dialog rutan Egenskaper för en process i aktivitets hanteraren.</span><span class="sxs-lookup"><span data-stu-id="20376-142">You can also get process names from the Properties dialog box of a process in Task Manager.</span></span>

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

### <span data-ttu-id="20376-143">– Process</span><span class="sxs-lookup"><span data-stu-id="20376-143">-Process</span></span>

<span data-ttu-id="20376-144">Anger en process av objektet process.</span><span class="sxs-lookup"><span data-stu-id="20376-144">Specifies a process by the process object.</span></span> <span data-ttu-id="20376-145">Det enklaste sättet att använda den här parametern är att spara resultatet av ett `Get-Process` kommando som returnerar en process som du vill ange i en variabel och sedan ange variabeln som värde för den här parametern.</span><span class="sxs-lookup"><span data-stu-id="20376-145">The simplest way to use this parameter is to save the results of a `Get-Process` command that returns process that you want to enter in a variable, and then specify the variable as the value of this parameter.</span></span>

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

### <span data-ttu-id="20376-146">-CustomPipeName</span><span class="sxs-lookup"><span data-stu-id="20376-146">-CustomPipeName</span></span>

<span data-ttu-id="20376-147">Hämtar eller anger namnet på den anpassade namngivna pipe som ska anslutas till.</span><span class="sxs-lookup"><span data-stu-id="20376-147">Gets or sets the custom named pipe name to connect to.</span></span> <span data-ttu-id="20376-148">Detta används vanligt vis tillsammans med `pwsh -CustomPipeName` .</span><span class="sxs-lookup"><span data-stu-id="20376-148">This is usually used in conjunction with `pwsh -CustomPipeName`.</span></span>

<span data-ttu-id="20376-149">Den här parametern introducerades i PowerShell 6,2.</span><span class="sxs-lookup"><span data-stu-id="20376-149">This parameter was introduced in PowerShell 6.2.</span></span>

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

### <span data-ttu-id="20376-150">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="20376-150">CommonParameters</span></span>

<span data-ttu-id="20376-151">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="20376-151">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="20376-152">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="20376-152">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="20376-153">INDATA</span><span class="sxs-lookup"><span data-stu-id="20376-153">INPUTS</span></span>

### <span data-ttu-id="20376-154">System. Diagnostics. process</span><span class="sxs-lookup"><span data-stu-id="20376-154">System.Diagnostics.Process</span></span>

## <span data-ttu-id="20376-155">UTDATA</span><span class="sxs-lookup"><span data-stu-id="20376-155">OUTPUTS</span></span>

## <span data-ttu-id="20376-156">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="20376-156">NOTES</span></span>

<span data-ttu-id="20376-157">`Enter-PSHostProcess` Det går inte att ange processen för PowerShell-sessionen där du kör kommandot.</span><span class="sxs-lookup"><span data-stu-id="20376-157">`Enter-PSHostProcess` cannot enter the process of the PowerShell session in which you are running the command.</span></span> <span data-ttu-id="20376-158">Du kan dock ange processen för en annan PowerShell-session eller en PowerShell ISE-session som körs samtidigt som den session där du kör `Enter-PSHostProcess` .</span><span class="sxs-lookup"><span data-stu-id="20376-158">You can, however, enter the process of another PowerShell session, or a PowerShell ISE session that is running at the same time as the session in which you are running `Enter-PSHostProcess`.</span></span>

<span data-ttu-id="20376-159">`Enter-PSHostProcess` kan bara ange de processer som är värdar för PowerShell.</span><span class="sxs-lookup"><span data-stu-id="20376-159">`Enter-PSHostProcess` can enter only those processes that are hosting PowerShell.</span></span> <span data-ttu-id="20376-160">Det vill säga att de har läst in PowerShell-motorn.</span><span class="sxs-lookup"><span data-stu-id="20376-160">That is, they have loaded the PowerShell engine.</span></span>

<span data-ttu-id="20376-161">Om du vill avsluta en process inifrån processen skriver du **exit** och trycker på <kbd>RETUR</kbd>.</span><span class="sxs-lookup"><span data-stu-id="20376-161">To exit a process from within the process, type **exit** , and then press <kbd>Enter</kbd>.</span></span>

## <span data-ttu-id="20376-162">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="20376-162">RELATED LINKS</span></span>

[<span data-ttu-id="20376-163">Avsluta-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="20376-163">Exit-PSHostProcess</span></span>](Exit-PSHostProcess.md)

[<span data-ttu-id="20376-164">Get-PSHostProcessInfo</span><span class="sxs-lookup"><span data-stu-id="20376-164">Get-PSHostProcessInfo</span></span>](Get-PSHostProcessInfo.md)
