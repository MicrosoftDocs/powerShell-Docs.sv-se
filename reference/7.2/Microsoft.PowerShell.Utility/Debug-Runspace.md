---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/debug-runspace?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Debug-Runspace
ms.openlocfilehash: 3f01b7624ffcbca472b09bdb83a7440f3526db43
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709816"
---
# <span data-ttu-id="e5a51-102">Debug-Runspace</span><span class="sxs-lookup"><span data-stu-id="e5a51-102">Debug-Runspace</span></span>

## <span data-ttu-id="e5a51-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="e5a51-103">SYNOPSIS</span></span>
<span data-ttu-id="e5a51-104">Startar en interaktiv felsökningssession med en körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="e5a51-104">Starts an interactive debugging session with a runspace.</span></span>

## <span data-ttu-id="e5a51-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e5a51-105">SYNTAX</span></span>

### <span data-ttu-id="e5a51-106">RunspaceParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="e5a51-106">RunspaceParameterSet (Default)</span></span>

```
Debug-Runspace [-Runspace] <Runspace> [-BreakAll] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="e5a51-107">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="e5a51-107">NameParameterSet</span></span>

```
Debug-Runspace [-Name] <String> [-BreakAll] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="e5a51-108">IdParameterSet</span><span class="sxs-lookup"><span data-stu-id="e5a51-108">IdParameterSet</span></span>

```
Debug-Runspace [-Id] <Int32> [-BreakAll] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="e5a51-109">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="e5a51-109">InstanceIdParameterSet</span></span>

```
Debug-Runspace [-InstanceId] <Guid> [-BreakAll] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="e5a51-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="e5a51-110">DESCRIPTION</span></span>

<span data-ttu-id="e5a51-111">`Debug-Runspace`Cmdleten startar en interaktiv felsökningssession med en lokal eller fjärran sluten Active-körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="e5a51-111">The `Debug-Runspace` cmdlet starts an interactive debugging session with a local or remote active runspace.</span></span> <span data-ttu-id="e5a51-112">Du kan hitta en körnings utrymme som du vill felsöka genom att först köra `Get-Process` för att hitta processer som är associerade med PowerShell, sedan `Enter-PSHostProcess` med process-ID: t som anges i **ID-** parametern för att ansluta till processen och sedan `Get-Runspace` Visa körnings utrymmen i PowerShell-värd processen.</span><span class="sxs-lookup"><span data-stu-id="e5a51-112">You can find a runspace that you want to debug by first running `Get-Process` to find processes associated with PowerShell, then `Enter-PSHostProcess` with the process ID specified in the **Id** parameter to attach to the process, and then `Get-Runspace` to list runspaces within the PowerShell host process.</span></span>

<span data-ttu-id="e5a51-113">När du har valt en körnings utrymme för fel sökning, om körnings utrymme för närvarande kör ett kommando eller skript, eller om skriptet har stoppats vid en Bryt punkt, öppnar PowerShell en fjärrfelsökning för körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="e5a51-113">After you have selected a runspace to debug, if the runspace is currently running a command or script, or if the script has stopped at a breakpoint, PowerShell opens a remote debugger session for the runspace.</span></span> <span data-ttu-id="e5a51-114">Du kan felsöka körnings utrymme-skriptet på samma sätt som skripten för fjärrsessioner felsöks.</span><span class="sxs-lookup"><span data-stu-id="e5a51-114">You can debug the runspace script in the same way remote session scripts are debugged.</span></span>

<span data-ttu-id="e5a51-115">Du kan bara ansluta till en PowerShell-värd process om du är administratör på datorn som kör processen eller om du kör skriptet som du vill felsöka.</span><span class="sxs-lookup"><span data-stu-id="e5a51-115">You can only attach to a PowerShell host process if you are an administrator on the computer that is running the process, or you are running the script that you want to debug.</span></span> <span data-ttu-id="e5a51-116">Du kan inte heller ange värd processen som kör den aktuella PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="e5a51-116">Also, you cannot enter the host process that is running the current PowerShell session.</span></span> <span data-ttu-id="e5a51-117">Du kan bara ange en värd process som kör en annan PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="e5a51-117">You can only enter a host process that is running a different PowerShell session.</span></span>

## <span data-ttu-id="e5a51-118">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="e5a51-118">EXAMPLES</span></span>

### <span data-ttu-id="e5a51-119">Exempel 1: Felsöka en fjärran sluten körnings utrymme</span><span class="sxs-lookup"><span data-stu-id="e5a51-119">Example 1: Debug a remote runspace</span></span>

```
PS C:\> Get-Process -ComputerName "WS10TestServer" -Name "*powershell*"

Handles      WS(K)   VM(M)      CPU(s)    Id  ProcessName
-------      -----   -----      ------    --  -----------
    377      69912     63     2.09      2420  powershell
    399     123396    829     4.48      1152  powershell_ise

PS C:\> Enter-PSSession -ComputerName "WS10TestServer"
[WS10TestServer]:PS C:\> Enter-PSHostProcess -Id 1152
[WS10TestServer:][Process:1152]: PS C:\Users\Test\Documents> Get-Runspace

Id Name            ComputerName    Type          State         Availability
-- ----            ------------    ----          -----         ------------
 1 Runspace1       WS10TestServer  Remote        Opened        Available
 2 RemoteHost      WS10TestServer  Remote        Opened        Busy

PS C:\> [WS10TestServer][Process:1152]: PS C:\Users\Test\Documents> Debug-Runspace -Id 2

Hit Line breakpoint on 'C:\TestWFVar1.ps1:83'
At C:\TestWFVar1.ps1:83 char:1
+ $scriptVar = "Script Variable"
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
[Process:1152]: [RSDBG: 2]: PS C:\> >
```

<span data-ttu-id="e5a51-120">I det här exemplet ska du Felsöka en körnings utrymme som är öppen på en fjärrdator, WS10TestServer.</span><span class="sxs-lookup"><span data-stu-id="e5a51-120">In this example, you debug a runspace that is open on a remote computer, WS10TestServer.</span></span> <span data-ttu-id="e5a51-121">På den första raden i kommandot kan du köra `Get-Process` på fjärrdatorn och filtrera för Windows PowerShell-värd processer.</span><span class="sxs-lookup"><span data-stu-id="e5a51-121">In the first line of the command, you run `Get-Process` on the remote computer, and filter for Windows PowerShell host processes.</span></span> <span data-ttu-id="e5a51-122">I det här exemplet ska du felsöka process-ID 1152, Windows PowerShell ISE värd processen.</span><span class="sxs-lookup"><span data-stu-id="e5a51-122">In this example, you want to debug process ID 1152, the Windows PowerShell ISE host process.</span></span>

<span data-ttu-id="e5a51-123">I det andra kommandot kör du `Enter-PSSession` för att öppna en fjärrsession på WS10TestServer.</span><span class="sxs-lookup"><span data-stu-id="e5a51-123">In the second command, you run `Enter-PSSession` to open a remote session on WS10TestServer.</span></span> <span data-ttu-id="e5a51-124">I det tredje kommandot ansluter du till Windows PowerShell ISE värd process som körs på fjärrservern genom att köra `Enter-PSHostProcess` och anger ID: t för den värd process som du fick i det första kommandot 1152.</span><span class="sxs-lookup"><span data-stu-id="e5a51-124">In the third command, you attach to the Windows PowerShell ISE host process running on the remote server by running `Enter-PSHostProcess`, and specifying the ID of the host process that you obtained in the first command, 1152.</span></span>

<span data-ttu-id="e5a51-125">I det fjärde kommandot visar en lista över tillgängliga körnings utrymmen för process-ID 1152 genom att köra `Get-Runspace` .</span><span class="sxs-lookup"><span data-stu-id="e5a51-125">In the fourth command, you list available runspaces for process ID 1152 by running `Get-Runspace`.</span></span>
<span data-ttu-id="e5a51-126">Du noterar ID-numret för den upptagna körnings utrymme; Det kör ett skript som du vill felsöka.</span><span class="sxs-lookup"><span data-stu-id="e5a51-126">You note the ID number of the Busy runspace; it is running a script that you want to debug.</span></span>

<span data-ttu-id="e5a51-127">I det sista kommandot börjar du Felsöka en öppen körnings utrymme som kör ett skript, TestWFVar1.ps1, genom `Debug-Runspace` att köra och identifiera körnings utrymme med ID, 2, genom att lägga till **ID-** parametern.</span><span class="sxs-lookup"><span data-stu-id="e5a51-127">In the last command, you start debugging an opened runspace that is running a script, TestWFVar1.ps1, by running `Debug-Runspace`, and identifying the runspace by its ID, 2, by adding the **Id** parameter.</span></span> <span data-ttu-id="e5a51-128">Eftersom det finns en Bryt punkt i skriptet öppnas fel söknings programmet.</span><span class="sxs-lookup"><span data-stu-id="e5a51-128">Because there's a breakpoint in the script, the debugger opens.</span></span>

## <span data-ttu-id="e5a51-129">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="e5a51-129">PARAMETERS</span></span>

### <span data-ttu-id="e5a51-130">-ID</span><span class="sxs-lookup"><span data-stu-id="e5a51-130">-Id</span></span>

<span data-ttu-id="e5a51-131">Anger ID-numret för en körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="e5a51-131">Specifies the ID number of a runspace.</span></span> <span data-ttu-id="e5a51-132">Du kan köra `Get-Runspace` för att Visa körnings utrymme-ID: n.</span><span class="sxs-lookup"><span data-stu-id="e5a51-132">You can run `Get-Runspace` to show runspace IDs.</span></span>

```yaml
Type: System.Int32
Parameter Sets: IdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e5a51-133">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="e5a51-133">-InstanceId</span></span>

<span data-ttu-id="e5a51-134">Anger en körnings utrymme med dess instans-ID, en GUID som du kan visa genom att köra `Get-Runspace` .</span><span class="sxs-lookup"><span data-stu-id="e5a51-134">Specifies a runspace by its instance ID, a GUID that you can show by running `Get-Runspace`.</span></span>

```yaml
Type: System.Guid
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e5a51-135">-Name</span><span class="sxs-lookup"><span data-stu-id="e5a51-135">-Name</span></span>

<span data-ttu-id="e5a51-136">Anger en körnings utrymme med hjälp av namnet.</span><span class="sxs-lookup"><span data-stu-id="e5a51-136">Specifies a runspace by its name.</span></span> <span data-ttu-id="e5a51-137">Du kan köra `Get-Runspace` för att visa namnen på körnings utrymmen.</span><span class="sxs-lookup"><span data-stu-id="e5a51-137">You can run `Get-Runspace` to show the names of runspaces.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e5a51-138">– Körnings utrymme</span><span class="sxs-lookup"><span data-stu-id="e5a51-138">-Runspace</span></span>

<span data-ttu-id="e5a51-139">Anger ett körnings utrymme-objekt.</span><span class="sxs-lookup"><span data-stu-id="e5a51-139">Specifies a runspace object.</span></span> <span data-ttu-id="e5a51-140">Det enklaste sättet att ange ett värde för den här parametern är att ange en variabel som innehåller resultatet av ett filtrerat `Get-Runspace` kommando.</span><span class="sxs-lookup"><span data-stu-id="e5a51-140">The simplest way to provide a value for this parameter is to specify a variable that contains the results of a filtered `Get-Runspace` command.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.Runspace
Parameter Sets: RunspaceParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="e5a51-141">-Confirm</span><span class="sxs-lookup"><span data-stu-id="e5a51-141">-Confirm</span></span>

<span data-ttu-id="e5a51-142">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e5a51-142">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e5a51-143">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="e5a51-143">-WhatIf</span></span>

<span data-ttu-id="e5a51-144">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="e5a51-144">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="e5a51-145">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="e5a51-145">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e5a51-146">-BreakAll</span><span class="sxs-lookup"><span data-stu-id="e5a51-146">-BreakAll</span></span>

<span data-ttu-id="e5a51-147">{{Fill BreakAll-Beskrivning}}</span><span class="sxs-lookup"><span data-stu-id="e5a51-147">{{ Fill BreakAll Description }}</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e5a51-148">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e5a51-148">CommonParameters</span></span>

<span data-ttu-id="e5a51-149">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e5a51-149">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e5a51-150">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="e5a51-150">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e5a51-151">INDATA</span><span class="sxs-lookup"><span data-stu-id="e5a51-151">INPUTS</span></span>

### <span data-ttu-id="e5a51-152">System. Management. Automation. körnings utrymmen. körnings utrymme</span><span class="sxs-lookup"><span data-stu-id="e5a51-152">System.Management.Automation.Runspaces.Runspace</span></span>

<span data-ttu-id="e5a51-153">Du kan skicka vidare resultatet av ett `Get-Runspace` kommando för att **Felsöka-körnings utrymme.**</span><span class="sxs-lookup"><span data-stu-id="e5a51-153">You can pipe the results of a `Get-Runspace` command to **Debug-Runspace.**</span></span>

## <span data-ttu-id="e5a51-154">UTDATA</span><span class="sxs-lookup"><span data-stu-id="e5a51-154">OUTPUTS</span></span>

## <span data-ttu-id="e5a51-155">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="e5a51-155">NOTES</span></span>

<span data-ttu-id="e5a51-156">`Debug-Runspace` fungerar på körnings utrymmen som är i öppet tillstånd.</span><span class="sxs-lookup"><span data-stu-id="e5a51-156">`Debug-Runspace` works on runspaces that are in the Opened state.</span></span> <span data-ttu-id="e5a51-157">Om ett körnings utrymme tillstånd ändras från öppnat till ett annat tillstånd, tas körnings utrymme bort automatiskt från listan som körs.</span><span class="sxs-lookup"><span data-stu-id="e5a51-157">If a runspace state changes from Opened to another state, that runspace is automatically removed from the running list.</span></span> <span data-ttu-id="e5a51-158">En körnings utrymme läggs bara till i den aktiva listan om den uppfyller följande kriterier.</span><span class="sxs-lookup"><span data-stu-id="e5a51-158">A runspace is added to the running list only if it meets the following criteria.</span></span>

- <span data-ttu-id="e5a51-159">Om det kommer från Invoke-Command; Det har ett `Invoke-Command` GUID-ID.</span><span class="sxs-lookup"><span data-stu-id="e5a51-159">If it is coming from Invoke-Command; that is, it has an `Invoke-Command` GUID ID.</span></span>
- <span data-ttu-id="e5a51-160">Om det kommer från `Debug-Runspace` , det har ett `Debug-Runspace` GUID-ID.</span><span class="sxs-lookup"><span data-stu-id="e5a51-160">If it is coming from `Debug-Runspace`; that is, it has a `Debug-Runspace` GUID ID.</span></span>
- <span data-ttu-id="e5a51-161">Om det kommer från ett PowerShell-arbetsflöde och dess jobb-ID för arbets flöde är detsamma som det aktuella aktiva fel söknings jobbets ID för arbets flöde.</span><span class="sxs-lookup"><span data-stu-id="e5a51-161">If it is coming from a PowerShell workflow, and its workflow job ID is the same as the current active debugger workflow job ID.</span></span>

## <span data-ttu-id="e5a51-162">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="e5a51-162">RELATED LINKS</span></span>

[<span data-ttu-id="e5a51-163">about_Debuggers</span><span class="sxs-lookup"><span data-stu-id="e5a51-163">about_Debuggers</span></span>](../Microsoft.PowerShell.Core/About/about_Debuggers.md)

[<span data-ttu-id="e5a51-164">Fel sökning – jobb</span><span class="sxs-lookup"><span data-stu-id="e5a51-164">Debug-Job</span></span>](../Microsoft.PowerShell.Core/Debug-Job.md)

[<span data-ttu-id="e5a51-165">Get-körnings utrymme</span><span class="sxs-lookup"><span data-stu-id="e5a51-165">Get-Runspace</span></span>](Get-Runspace.md)

[<span data-ttu-id="e5a51-166">Hämta process</span><span class="sxs-lookup"><span data-stu-id="e5a51-166">Get-Process</span></span>](../Microsoft.PowerShell.Management/Get-Process.md)

[<span data-ttu-id="e5a51-167">Retur-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="e5a51-167">Enter-PSHostProcess</span></span>](../Microsoft.PowerShell.Core/Enter-PSHostProcess.md)

[<span data-ttu-id="e5a51-168">Retur-PSSession</span><span class="sxs-lookup"><span data-stu-id="e5a51-168">Enter-PSSession</span></span>](../Microsoft.PowerShell.Core/Enter-PSSession.md)

