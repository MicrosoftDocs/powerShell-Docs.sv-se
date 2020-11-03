---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/debug-runspace?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Debug-Runspace
ms.openlocfilehash: 1f347afe89ed63d64e8a8156b7259509800d5d24
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262191"
---
# <span data-ttu-id="78b99-103">Debug-Runspace</span><span class="sxs-lookup"><span data-stu-id="78b99-103">Debug-Runspace</span></span>

## <span data-ttu-id="78b99-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="78b99-104">SYNOPSIS</span></span>
<span data-ttu-id="78b99-105">Startar en interaktiv felsökningssession med en körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="78b99-105">Starts an interactive debugging session with a runspace.</span></span>

## <span data-ttu-id="78b99-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="78b99-106">SYNTAX</span></span>

### <span data-ttu-id="78b99-107">RunspaceParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="78b99-107">RunspaceParameterSet (Default)</span></span>

```
Debug-Runspace [-Runspace] <Runspace> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="78b99-108">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="78b99-108">NameParameterSet</span></span>

```
Debug-Runspace [-Name] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="78b99-109">IdParameterSet</span><span class="sxs-lookup"><span data-stu-id="78b99-109">IdParameterSet</span></span>

```
Debug-Runspace [-Id] <Int32> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="78b99-110">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="78b99-110">InstanceIdParameterSet</span></span>

```
Debug-Runspace [-InstanceId] <Guid> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="78b99-111">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="78b99-111">DESCRIPTION</span></span>

<span data-ttu-id="78b99-112">`Debug-Runspace`Cmdleten startar en interaktiv felsökningssession med en lokal eller fjärran sluten Active-körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="78b99-112">The `Debug-Runspace` cmdlet starts an interactive debugging session with a local or remote active runspace.</span></span> <span data-ttu-id="78b99-113">Du kan hitta en körnings utrymme som du vill felsöka genom att först köra `Get-Process` för att hitta processer som är associerade med PowerShell, sedan `Enter-PSHostProcess` med process-ID: t som anges i **ID-** parametern för att ansluta till processen och sedan `Get-Runspace` Visa körnings utrymmen i PowerShell-värd processen.</span><span class="sxs-lookup"><span data-stu-id="78b99-113">You can find a runspace that you want to debug by first running `Get-Process` to find processes associated with PowerShell, then `Enter-PSHostProcess` with the process ID specified in the **Id** parameter to attach to the process, and then `Get-Runspace` to list runspaces within the PowerShell host process.</span></span>

<span data-ttu-id="78b99-114">När du har valt en körnings utrymme för fel sökning, om körnings utrymme för närvarande kör ett kommando eller skript, eller om skriptet har stoppats vid en Bryt punkt, öppnar PowerShell en fjärrfelsökning för körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="78b99-114">After you have selected a runspace to debug, if the runspace is currently running a command or script, or if the script has stopped at a breakpoint, PowerShell opens a remote debugger session for the runspace.</span></span> <span data-ttu-id="78b99-115">Du kan felsöka körnings utrymme-skriptet på samma sätt som skripten för fjärrsessioner felsöks.</span><span class="sxs-lookup"><span data-stu-id="78b99-115">You can debug the runspace script in the same way remote session scripts are debugged.</span></span>

<span data-ttu-id="78b99-116">Du kan bara ansluta till en PowerShell-värd process om du är administratör på datorn som kör processen eller om du kör skriptet som du vill felsöka.</span><span class="sxs-lookup"><span data-stu-id="78b99-116">You can only attach to a PowerShell host process if you are an administrator on the computer that is running the process, or you are running the script that you want to debug.</span></span> <span data-ttu-id="78b99-117">Du kan inte heller ange värd processen som kör den aktuella PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="78b99-117">Also, you cannot enter the host process that is running the current PowerShell session.</span></span> <span data-ttu-id="78b99-118">Du kan bara ange en värd process som kör en annan PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="78b99-118">You can only enter a host process that is running a different PowerShell session.</span></span>

## <span data-ttu-id="78b99-119">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="78b99-119">EXAMPLES</span></span>

### <span data-ttu-id="78b99-120">Exempel 1: Felsöka en fjärran sluten körnings utrymme</span><span class="sxs-lookup"><span data-stu-id="78b99-120">Example 1: Debug a remote runspace</span></span>

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

<span data-ttu-id="78b99-121">I det här exemplet ska du Felsöka en körnings utrymme som är öppen på en fjärrdator, WS10TestServer.</span><span class="sxs-lookup"><span data-stu-id="78b99-121">In this example, you debug a runspace that is open on a remote computer, WS10TestServer.</span></span> <span data-ttu-id="78b99-122">På den första raden i kommandot kan du köra `Get-Process` på fjärrdatorn och filtrera för Windows PowerShell-värd processer.</span><span class="sxs-lookup"><span data-stu-id="78b99-122">In the first line of the command, you run `Get-Process` on the remote computer, and filter for Windows PowerShell host processes.</span></span> <span data-ttu-id="78b99-123">I det här exemplet ska du felsöka process-ID 1152, Windows PowerShell ISE värd processen.</span><span class="sxs-lookup"><span data-stu-id="78b99-123">In this example, you want to debug process ID 1152, the Windows PowerShell ISE host process.</span></span>

<span data-ttu-id="78b99-124">I det andra kommandot kör du `Enter-PSSession` för att öppna en fjärrsession på WS10TestServer.</span><span class="sxs-lookup"><span data-stu-id="78b99-124">In the second command, you run `Enter-PSSession` to open a remote session on WS10TestServer.</span></span> <span data-ttu-id="78b99-125">I det tredje kommandot ansluter du till Windows PowerShell ISE värd process som körs på fjärrservern genom att köra `Enter-PSHostProcess` och anger ID: t för den värd process som du fick i det första kommandot 1152.</span><span class="sxs-lookup"><span data-stu-id="78b99-125">In the third command, you attach to the Windows PowerShell ISE host process running on the remote server by running `Enter-PSHostProcess`, and specifying the ID of the host process that you obtained in the first command, 1152.</span></span>

<span data-ttu-id="78b99-126">I det fjärde kommandot visar en lista över tillgängliga körnings utrymmen för process-ID 1152 genom att köra `Get-Runspace` .</span><span class="sxs-lookup"><span data-stu-id="78b99-126">In the fourth command, you list available runspaces for process ID 1152 by running `Get-Runspace`.</span></span>
<span data-ttu-id="78b99-127">Du noterar ID-numret för den upptagna körnings utrymme; Det kör ett skript som du vill felsöka.</span><span class="sxs-lookup"><span data-stu-id="78b99-127">You note the ID number of the Busy runspace; it is running a script that you want to debug.</span></span>

<span data-ttu-id="78b99-128">I det sista kommandot börjar du Felsöka en öppen körnings utrymme som kör ett skript, TestWFVar1.ps1, genom `Debug-Runspace` att köra och identifiera körnings utrymme med ID, 2, genom att lägga till **ID-** parametern.</span><span class="sxs-lookup"><span data-stu-id="78b99-128">In the last command, you start debugging an opened runspace that is running a script, TestWFVar1.ps1, by running `Debug-Runspace`, and identifying the runspace by its ID, 2, by adding the **Id** parameter.</span></span> <span data-ttu-id="78b99-129">Eftersom det finns en Bryt punkt i skriptet öppnas fel söknings programmet.</span><span class="sxs-lookup"><span data-stu-id="78b99-129">Because there's a breakpoint in the script, the debugger opens.</span></span>

## <span data-ttu-id="78b99-130">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="78b99-130">PARAMETERS</span></span>

### <span data-ttu-id="78b99-131">-ID</span><span class="sxs-lookup"><span data-stu-id="78b99-131">-Id</span></span>

<span data-ttu-id="78b99-132">Anger ID-numret för en körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="78b99-132">Specifies the ID number of a runspace.</span></span> <span data-ttu-id="78b99-133">Du kan köra `Get-Runspace` för att Visa körnings utrymme-ID: n.</span><span class="sxs-lookup"><span data-stu-id="78b99-133">You can run `Get-Runspace` to show runspace IDs.</span></span>

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

### <span data-ttu-id="78b99-134">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="78b99-134">-InstanceId</span></span>

<span data-ttu-id="78b99-135">Anger en körnings utrymme med dess instans-ID, en GUID som du kan visa genom att köra `Get-Runspace` .</span><span class="sxs-lookup"><span data-stu-id="78b99-135">Specifies a runspace by its instance ID, a GUID that you can show by running `Get-Runspace`.</span></span>

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

### <span data-ttu-id="78b99-136">-Name</span><span class="sxs-lookup"><span data-stu-id="78b99-136">-Name</span></span>

<span data-ttu-id="78b99-137">Anger en körnings utrymme med hjälp av namnet.</span><span class="sxs-lookup"><span data-stu-id="78b99-137">Specifies a runspace by its name.</span></span> <span data-ttu-id="78b99-138">Du kan köra `Get-Runspace` för att visa namnen på körnings utrymmen.</span><span class="sxs-lookup"><span data-stu-id="78b99-138">You can run `Get-Runspace` to show the names of runspaces.</span></span>

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

### <span data-ttu-id="78b99-139">– Körnings utrymme</span><span class="sxs-lookup"><span data-stu-id="78b99-139">-Runspace</span></span>

<span data-ttu-id="78b99-140">Anger ett körnings utrymme-objekt.</span><span class="sxs-lookup"><span data-stu-id="78b99-140">Specifies a runspace object.</span></span> <span data-ttu-id="78b99-141">Det enklaste sättet att ange ett värde för den här parametern är att ange en variabel som innehåller resultatet av ett filtrerat `Get-Runspace` kommando.</span><span class="sxs-lookup"><span data-stu-id="78b99-141">The simplest way to provide a value for this parameter is to specify a variable that contains the results of a filtered `Get-Runspace` command.</span></span>

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

### <span data-ttu-id="78b99-142">-Confirm</span><span class="sxs-lookup"><span data-stu-id="78b99-142">-Confirm</span></span>

<span data-ttu-id="78b99-143">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="78b99-143">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="78b99-144">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="78b99-144">-WhatIf</span></span>

<span data-ttu-id="78b99-145">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="78b99-145">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="78b99-146">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="78b99-146">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="78b99-147">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="78b99-147">CommonParameters</span></span>

<span data-ttu-id="78b99-148">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="78b99-148">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="78b99-149">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="78b99-149">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="78b99-150">INDATA</span><span class="sxs-lookup"><span data-stu-id="78b99-150">INPUTS</span></span>

### <span data-ttu-id="78b99-151">System. Management. Automation. körnings utrymmen. körnings utrymme</span><span class="sxs-lookup"><span data-stu-id="78b99-151">System.Management.Automation.Runspaces.Runspace</span></span>

<span data-ttu-id="78b99-152">Du kan skicka vidare resultatet av ett `Get-Runspace` kommando för att **Felsöka-körnings utrymme.**</span><span class="sxs-lookup"><span data-stu-id="78b99-152">You can pipe the results of a `Get-Runspace` command to **Debug-Runspace.**</span></span>

## <span data-ttu-id="78b99-153">UTDATA</span><span class="sxs-lookup"><span data-stu-id="78b99-153">OUTPUTS</span></span>

## <span data-ttu-id="78b99-154">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="78b99-154">NOTES</span></span>

<span data-ttu-id="78b99-155">`Debug-Runspace` fungerar på körnings utrymmen som är i öppet tillstånd.</span><span class="sxs-lookup"><span data-stu-id="78b99-155">`Debug-Runspace` works on runspaces that are in the Opened state.</span></span> <span data-ttu-id="78b99-156">Om ett körnings utrymme tillstånd ändras från öppnat till ett annat tillstånd, tas körnings utrymme bort automatiskt från listan som körs.</span><span class="sxs-lookup"><span data-stu-id="78b99-156">If a runspace state changes from Opened to another state, that runspace is automatically removed from the running list.</span></span> <span data-ttu-id="78b99-157">En körnings utrymme läggs bara till i den aktiva listan om den uppfyller följande kriterier.</span><span class="sxs-lookup"><span data-stu-id="78b99-157">A runspace is added to the running list only if it meets the following criteria.</span></span>

- <span data-ttu-id="78b99-158">Om det kommer från Invoke-Command; Det har ett `Invoke-Command` GUID-ID.</span><span class="sxs-lookup"><span data-stu-id="78b99-158">If it is coming from Invoke-Command; that is, it has an `Invoke-Command` GUID ID.</span></span>
- <span data-ttu-id="78b99-159">Om det kommer från `Debug-Runspace` , det har ett `Debug-Runspace` GUID-ID.</span><span class="sxs-lookup"><span data-stu-id="78b99-159">If it is coming from `Debug-Runspace`; that is, it has a `Debug-Runspace` GUID ID.</span></span>
- <span data-ttu-id="78b99-160">Om det kommer från ett PowerShell-arbetsflöde och dess jobb-ID för arbets flöde är detsamma som det aktuella aktiva fel söknings jobbets ID för arbets flöde.</span><span class="sxs-lookup"><span data-stu-id="78b99-160">If it is coming from a PowerShell workflow, and its workflow job ID is the same as the current active debugger workflow job ID.</span></span>

## <span data-ttu-id="78b99-161">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="78b99-161">RELATED LINKS</span></span>

[<span data-ttu-id="78b99-162">about_Debuggers</span><span class="sxs-lookup"><span data-stu-id="78b99-162">about_Debuggers</span></span>](../Microsoft.PowerShell.Core/About/about_Debuggers.md)

[<span data-ttu-id="78b99-163">Fel sökning – jobb</span><span class="sxs-lookup"><span data-stu-id="78b99-163">Debug-Job</span></span>](../Microsoft.PowerShell.Core/Debug-Job.md)

[<span data-ttu-id="78b99-164">Get-körnings utrymme</span><span class="sxs-lookup"><span data-stu-id="78b99-164">Get-Runspace</span></span>](Get-Runspace.md)

[<span data-ttu-id="78b99-165">Hämta process</span><span class="sxs-lookup"><span data-stu-id="78b99-165">Get-Process</span></span>](../Microsoft.PowerShell.Management/Get-Process.md)

[<span data-ttu-id="78b99-166">Retur-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="78b99-166">Enter-PSHostProcess</span></span>](../Microsoft.PowerShell.Core/Enter-PSHostProcess.md)

[<span data-ttu-id="78b99-167">Retur-PSSession</span><span class="sxs-lookup"><span data-stu-id="78b99-167">Enter-PSSession</span></span>](../Microsoft.PowerShell.Core/Enter-PSSession.md)
