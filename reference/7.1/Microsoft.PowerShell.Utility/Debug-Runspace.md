---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/debug-runspace?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Debug-Runspace
ms.openlocfilehash: fd1da10b3a64e0fe9b43dfec1289eebaf31ed739
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266456"
---
# <span data-ttu-id="f7af0-103">Debug-Runspace</span><span class="sxs-lookup"><span data-stu-id="f7af0-103">Debug-Runspace</span></span>

## <span data-ttu-id="f7af0-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="f7af0-104">SYNOPSIS</span></span>
<span data-ttu-id="f7af0-105">Startar en interaktiv felsökningssession med en körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="f7af0-105">Starts an interactive debugging session with a runspace.</span></span>

## <span data-ttu-id="f7af0-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f7af0-106">SYNTAX</span></span>

### <span data-ttu-id="f7af0-107">RunspaceParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="f7af0-107">RunspaceParameterSet (Default)</span></span>

```
Debug-Runspace [-Runspace] <Runspace> [-BreakAll] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f7af0-108">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="f7af0-108">NameParameterSet</span></span>

```
Debug-Runspace [-Name] <String> [-BreakAll] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f7af0-109">IdParameterSet</span><span class="sxs-lookup"><span data-stu-id="f7af0-109">IdParameterSet</span></span>

```
Debug-Runspace [-Id] <Int32> [-BreakAll] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f7af0-110">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="f7af0-110">InstanceIdParameterSet</span></span>

```
Debug-Runspace [-InstanceId] <Guid> [-BreakAll] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="f7af0-111">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="f7af0-111">DESCRIPTION</span></span>

<span data-ttu-id="f7af0-112">`Debug-Runspace`Cmdleten startar en interaktiv felsökningssession med en lokal eller fjärran sluten Active-körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="f7af0-112">The `Debug-Runspace` cmdlet starts an interactive debugging session with a local or remote active runspace.</span></span> <span data-ttu-id="f7af0-113">Du kan hitta en körnings utrymme som du vill felsöka genom att först köra `Get-Process` för att hitta processer som är associerade med PowerShell, sedan `Enter-PSHostProcess` med process-ID: t som anges i **ID-** parametern för att ansluta till processen och sedan `Get-Runspace` Visa körnings utrymmen i PowerShell-värd processen.</span><span class="sxs-lookup"><span data-stu-id="f7af0-113">You can find a runspace that you want to debug by first running `Get-Process` to find processes associated with PowerShell, then `Enter-PSHostProcess` with the process ID specified in the **Id** parameter to attach to the process, and then `Get-Runspace` to list runspaces within the PowerShell host process.</span></span>

<span data-ttu-id="f7af0-114">När du har valt en körnings utrymme för fel sökning, om körnings utrymme för närvarande kör ett kommando eller skript, eller om skriptet har stoppats vid en Bryt punkt, öppnar PowerShell en fjärrfelsökning för körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="f7af0-114">After you have selected a runspace to debug, if the runspace is currently running a command or script, or if the script has stopped at a breakpoint, PowerShell opens a remote debugger session for the runspace.</span></span> <span data-ttu-id="f7af0-115">Du kan felsöka körnings utrymme-skriptet på samma sätt som skripten för fjärrsessioner felsöks.</span><span class="sxs-lookup"><span data-stu-id="f7af0-115">You can debug the runspace script in the same way remote session scripts are debugged.</span></span>

<span data-ttu-id="f7af0-116">Du kan bara ansluta till en PowerShell-värd process om du är administratör på datorn som kör processen eller om du kör skriptet som du vill felsöka.</span><span class="sxs-lookup"><span data-stu-id="f7af0-116">You can only attach to a PowerShell host process if you are an administrator on the computer that is running the process, or you are running the script that you want to debug.</span></span> <span data-ttu-id="f7af0-117">Du kan inte heller ange värd processen som kör den aktuella PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="f7af0-117">Also, you cannot enter the host process that is running the current PowerShell session.</span></span> <span data-ttu-id="f7af0-118">Du kan bara ange en värd process som kör en annan PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="f7af0-118">You can only enter a host process that is running a different PowerShell session.</span></span>

## <span data-ttu-id="f7af0-119">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="f7af0-119">EXAMPLES</span></span>

### <span data-ttu-id="f7af0-120">Exempel 1: Felsöka en fjärran sluten körnings utrymme</span><span class="sxs-lookup"><span data-stu-id="f7af0-120">Example 1: Debug a remote runspace</span></span>

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

<span data-ttu-id="f7af0-121">I det här exemplet ska du Felsöka en körnings utrymme som är öppen på en fjärrdator, WS10TestServer.</span><span class="sxs-lookup"><span data-stu-id="f7af0-121">In this example, you debug a runspace that is open on a remote computer, WS10TestServer.</span></span> <span data-ttu-id="f7af0-122">På den första raden i kommandot kan du köra `Get-Process` på fjärrdatorn och filtrera för Windows PowerShell-värd processer.</span><span class="sxs-lookup"><span data-stu-id="f7af0-122">In the first line of the command, you run `Get-Process` on the remote computer, and filter for Windows PowerShell host processes.</span></span> <span data-ttu-id="f7af0-123">I det här exemplet ska du felsöka process-ID 1152, Windows PowerShell ISE värd processen.</span><span class="sxs-lookup"><span data-stu-id="f7af0-123">In this example, you want to debug process ID 1152, the Windows PowerShell ISE host process.</span></span>

<span data-ttu-id="f7af0-124">I det andra kommandot kör du `Enter-PSSession` för att öppna en fjärrsession på WS10TestServer.</span><span class="sxs-lookup"><span data-stu-id="f7af0-124">In the second command, you run `Enter-PSSession` to open a remote session on WS10TestServer.</span></span> <span data-ttu-id="f7af0-125">I det tredje kommandot ansluter du till Windows PowerShell ISE värd process som körs på fjärrservern genom att köra `Enter-PSHostProcess` och anger ID: t för den värd process som du fick i det första kommandot 1152.</span><span class="sxs-lookup"><span data-stu-id="f7af0-125">In the third command, you attach to the Windows PowerShell ISE host process running on the remote server by running `Enter-PSHostProcess`, and specifying the ID of the host process that you obtained in the first command, 1152.</span></span>

<span data-ttu-id="f7af0-126">I det fjärde kommandot visar en lista över tillgängliga körnings utrymmen för process-ID 1152 genom att köra `Get-Runspace` .</span><span class="sxs-lookup"><span data-stu-id="f7af0-126">In the fourth command, you list available runspaces for process ID 1152 by running `Get-Runspace`.</span></span>
<span data-ttu-id="f7af0-127">Du noterar ID-numret för den upptagna körnings utrymme; Det kör ett skript som du vill felsöka.</span><span class="sxs-lookup"><span data-stu-id="f7af0-127">You note the ID number of the Busy runspace; it is running a script that you want to debug.</span></span>

<span data-ttu-id="f7af0-128">I det sista kommandot börjar du Felsöka en öppen körnings utrymme som kör ett skript, TestWFVar1.ps1, genom `Debug-Runspace` att köra och identifiera körnings utrymme med ID, 2, genom att lägga till **ID-** parametern.</span><span class="sxs-lookup"><span data-stu-id="f7af0-128">In the last command, you start debugging an opened runspace that is running a script, TestWFVar1.ps1, by running `Debug-Runspace`, and identifying the runspace by its ID, 2, by adding the **Id** parameter.</span></span> <span data-ttu-id="f7af0-129">Eftersom det finns en Bryt punkt i skriptet öppnas fel söknings programmet.</span><span class="sxs-lookup"><span data-stu-id="f7af0-129">Because there's a breakpoint in the script, the debugger opens.</span></span>

## <span data-ttu-id="f7af0-130">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="f7af0-130">PARAMETERS</span></span>

### <span data-ttu-id="f7af0-131">-ID</span><span class="sxs-lookup"><span data-stu-id="f7af0-131">-Id</span></span>

<span data-ttu-id="f7af0-132">Anger ID-numret för en körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="f7af0-132">Specifies the ID number of a runspace.</span></span> <span data-ttu-id="f7af0-133">Du kan köra `Get-Runspace` för att Visa körnings utrymme-ID: n.</span><span class="sxs-lookup"><span data-stu-id="f7af0-133">You can run `Get-Runspace` to show runspace IDs.</span></span>

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

### <span data-ttu-id="f7af0-134">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="f7af0-134">-InstanceId</span></span>

<span data-ttu-id="f7af0-135">Anger en körnings utrymme med dess instans-ID, en GUID som du kan visa genom att köra `Get-Runspace` .</span><span class="sxs-lookup"><span data-stu-id="f7af0-135">Specifies a runspace by its instance ID, a GUID that you can show by running `Get-Runspace`.</span></span>

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

### <span data-ttu-id="f7af0-136">-Name</span><span class="sxs-lookup"><span data-stu-id="f7af0-136">-Name</span></span>

<span data-ttu-id="f7af0-137">Anger en körnings utrymme med hjälp av namnet.</span><span class="sxs-lookup"><span data-stu-id="f7af0-137">Specifies a runspace by its name.</span></span> <span data-ttu-id="f7af0-138">Du kan köra `Get-Runspace` för att visa namnen på körnings utrymmen.</span><span class="sxs-lookup"><span data-stu-id="f7af0-138">You can run `Get-Runspace` to show the names of runspaces.</span></span>

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

### <span data-ttu-id="f7af0-139">– Körnings utrymme</span><span class="sxs-lookup"><span data-stu-id="f7af0-139">-Runspace</span></span>

<span data-ttu-id="f7af0-140">Anger ett körnings utrymme-objekt.</span><span class="sxs-lookup"><span data-stu-id="f7af0-140">Specifies a runspace object.</span></span> <span data-ttu-id="f7af0-141">Det enklaste sättet att ange ett värde för den här parametern är att ange en variabel som innehåller resultatet av ett filtrerat `Get-Runspace` kommando.</span><span class="sxs-lookup"><span data-stu-id="f7af0-141">The simplest way to provide a value for this parameter is to specify a variable that contains the results of a filtered `Get-Runspace` command.</span></span>

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

### <span data-ttu-id="f7af0-142">-Confirm</span><span class="sxs-lookup"><span data-stu-id="f7af0-142">-Confirm</span></span>

<span data-ttu-id="f7af0-143">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="f7af0-143">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="f7af0-144">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="f7af0-144">-WhatIf</span></span>

<span data-ttu-id="f7af0-145">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="f7af0-145">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="f7af0-146">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="f7af0-146">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="f7af0-147">-BreakAll</span><span class="sxs-lookup"><span data-stu-id="f7af0-147">-BreakAll</span></span>

<span data-ttu-id="f7af0-148">{{Fill BreakAll-Beskrivning}}</span><span class="sxs-lookup"><span data-stu-id="f7af0-148">{{ Fill BreakAll Description }}</span></span>

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

### <span data-ttu-id="f7af0-149">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f7af0-149">CommonParameters</span></span>

<span data-ttu-id="f7af0-150">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f7af0-150">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f7af0-151">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="f7af0-151">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f7af0-152">INDATA</span><span class="sxs-lookup"><span data-stu-id="f7af0-152">INPUTS</span></span>

### <span data-ttu-id="f7af0-153">System. Management. Automation. körnings utrymmen. körnings utrymme</span><span class="sxs-lookup"><span data-stu-id="f7af0-153">System.Management.Automation.Runspaces.Runspace</span></span>

<span data-ttu-id="f7af0-154">Du kan skicka vidare resultatet av ett `Get-Runspace` kommando för att **Felsöka-körnings utrymme.**</span><span class="sxs-lookup"><span data-stu-id="f7af0-154">You can pipe the results of a `Get-Runspace` command to **Debug-Runspace.**</span></span>

## <span data-ttu-id="f7af0-155">UTDATA</span><span class="sxs-lookup"><span data-stu-id="f7af0-155">OUTPUTS</span></span>

## <span data-ttu-id="f7af0-156">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="f7af0-156">NOTES</span></span>

<span data-ttu-id="f7af0-157">`Debug-Runspace` fungerar på körnings utrymmen som är i öppet tillstånd.</span><span class="sxs-lookup"><span data-stu-id="f7af0-157">`Debug-Runspace` works on runspaces that are in the Opened state.</span></span> <span data-ttu-id="f7af0-158">Om ett körnings utrymme tillstånd ändras från öppnat till ett annat tillstånd, tas körnings utrymme bort automatiskt från listan som körs.</span><span class="sxs-lookup"><span data-stu-id="f7af0-158">If a runspace state changes from Opened to another state, that runspace is automatically removed from the running list.</span></span> <span data-ttu-id="f7af0-159">En körnings utrymme läggs bara till i den aktiva listan om den uppfyller följande kriterier.</span><span class="sxs-lookup"><span data-stu-id="f7af0-159">A runspace is added to the running list only if it meets the following criteria.</span></span>

- <span data-ttu-id="f7af0-160">Om det kommer från Invoke-Command; Det har ett `Invoke-Command` GUID-ID.</span><span class="sxs-lookup"><span data-stu-id="f7af0-160">If it is coming from Invoke-Command; that is, it has an `Invoke-Command` GUID ID.</span></span>
- <span data-ttu-id="f7af0-161">Om det kommer från `Debug-Runspace` , det har ett `Debug-Runspace` GUID-ID.</span><span class="sxs-lookup"><span data-stu-id="f7af0-161">If it is coming from `Debug-Runspace`; that is, it has a `Debug-Runspace` GUID ID.</span></span>
- <span data-ttu-id="f7af0-162">Om det kommer från ett PowerShell-arbetsflöde och dess jobb-ID för arbets flöde är detsamma som det aktuella aktiva fel söknings jobbets ID för arbets flöde.</span><span class="sxs-lookup"><span data-stu-id="f7af0-162">If it is coming from a PowerShell workflow, and its workflow job ID is the same as the current active debugger workflow job ID.</span></span>

## <span data-ttu-id="f7af0-163">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="f7af0-163">RELATED LINKS</span></span>

[<span data-ttu-id="f7af0-164">about_Debuggers</span><span class="sxs-lookup"><span data-stu-id="f7af0-164">about_Debuggers</span></span>](../Microsoft.PowerShell.Core/About/about_Debuggers.md)

[<span data-ttu-id="f7af0-165">Fel sökning – jobb</span><span class="sxs-lookup"><span data-stu-id="f7af0-165">Debug-Job</span></span>](../Microsoft.PowerShell.Core/Debug-Job.md)

[<span data-ttu-id="f7af0-166">Get-körnings utrymme</span><span class="sxs-lookup"><span data-stu-id="f7af0-166">Get-Runspace</span></span>](Get-Runspace.md)

[<span data-ttu-id="f7af0-167">Hämta process</span><span class="sxs-lookup"><span data-stu-id="f7af0-167">Get-Process</span></span>](../Microsoft.PowerShell.Management/Get-Process.md)

[<span data-ttu-id="f7af0-168">Retur-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="f7af0-168">Enter-PSHostProcess</span></span>](../Microsoft.PowerShell.Core/Enter-PSHostProcess.md)

[<span data-ttu-id="f7af0-169">Retur-PSSession</span><span class="sxs-lookup"><span data-stu-id="f7af0-169">Enter-PSSession</span></span>](../Microsoft.PowerShell.Core/Enter-PSSession.md)

