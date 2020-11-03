---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/debug-process?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Debug-Process
ms.openlocfilehash: 1cc0b0f51d84f3471bc3f54a91daba10f3528a8a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266211"
---
# <span data-ttu-id="71ff1-103">Debug-Process</span><span class="sxs-lookup"><span data-stu-id="71ff1-103">Debug-Process</span></span>

## <span data-ttu-id="71ff1-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="71ff1-104">SYNOPSIS</span></span>
<span data-ttu-id="71ff1-105">Avbuggar en eller flera processer som körs på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="71ff1-105">Debugs one or more processes running on the local computer.</span></span>

## <span data-ttu-id="71ff1-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="71ff1-106">SYNTAX</span></span>

### <span data-ttu-id="71ff1-107">Namn (standard)</span><span class="sxs-lookup"><span data-stu-id="71ff1-107">Name (Default)</span></span>

```
Debug-Process [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="71ff1-108">Id</span><span class="sxs-lookup"><span data-stu-id="71ff1-108">Id</span></span>

```
Debug-Process [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="71ff1-109">InputObject</span><span class="sxs-lookup"><span data-stu-id="71ff1-109">InputObject</span></span>

```
Debug-Process -InputObject <Process[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="71ff1-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="71ff1-110">DESCRIPTION</span></span>
<span data-ttu-id="71ff1-111">Cmdleten **Debug-process** kopplar en fel sökare till en eller flera processer som körs på en lokal dator.</span><span class="sxs-lookup"><span data-stu-id="71ff1-111">The **Debug-Process** cmdlet attaches a debugger to one or more running processes on a local computer.</span></span>
<span data-ttu-id="71ff1-112">Du kan ange processer efter process namn eller process-ID (PID), eller så kan du skicka vidare process objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="71ff1-112">You can specify the processes by their process name or process ID (PID), or you can pipe process objects to this cmdlet.</span></span>

<span data-ttu-id="71ff1-113">Den här cmdleten kopplar den fel sökare som för närvarande är registrerad för processen.</span><span class="sxs-lookup"><span data-stu-id="71ff1-113">This cmdlet attaches the debugger that is currently registered for the process.</span></span>
<span data-ttu-id="71ff1-114">Innan du använder denna cmdlet måste du kontrol lera att en fel sökare har laddats ned och kon figurer ATS korrekt.</span><span class="sxs-lookup"><span data-stu-id="71ff1-114">Before using this cmdlet, verify that a debugger is downloaded and correctly configured.</span></span>

## <span data-ttu-id="71ff1-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="71ff1-115">EXAMPLES</span></span>

### <span data-ttu-id="71ff1-116">Exempel 1: koppla en fel sökare till en process på datorn</span><span class="sxs-lookup"><span data-stu-id="71ff1-116">Example 1: Attach a debugger to a process on the computer</span></span>

```
PS C:\> Debug-Process -Name "Windows Powershell"
```

<span data-ttu-id="71ff1-117">Det här kommandot kopplar en fel sökare till Windows PowerShell-processen på datorn.</span><span class="sxs-lookup"><span data-stu-id="71ff1-117">This command attaches a debugger to the Windows PowerShell process on the computer.</span></span>

### <span data-ttu-id="71ff1-118">Exempel 2: koppla en fel sökare till alla processer som börjar med den angivna strängen</span><span class="sxs-lookup"><span data-stu-id="71ff1-118">Example 2: Attach a debugger to all processes that begin with the specified string</span></span>

```
PS C:\> Debug-Process -Name "SQL*"
```

<span data-ttu-id="71ff1-119">Det här kommandot kopplar en fel sökare till alla processer som har namn som börjar med SQL.</span><span class="sxs-lookup"><span data-stu-id="71ff1-119">This command attaches a debugger to all processes that have names that begin with SQL.</span></span>

### <span data-ttu-id="71ff1-120">Exempel 3: koppla en fel sökare till flera processer</span><span class="sxs-lookup"><span data-stu-id="71ff1-120">Example 3: Attach a debugger to multiple processes</span></span>

```
PS C:\> Debug-Process "Winlogon", "Explorer", "Outlook"
```

<span data-ttu-id="71ff1-121">Det här kommandot kopplar en fel sökare till Winlogon-, Utforskare-och Outlook-processerna.</span><span class="sxs-lookup"><span data-stu-id="71ff1-121">This command attaches a debugger to the Winlogon, Explorer, and Outlook processes.</span></span>

### <span data-ttu-id="71ff1-122">Exempel 4: koppla en fel sökare till flera process-ID: n</span><span class="sxs-lookup"><span data-stu-id="71ff1-122">Example 4: Attach a debugger to multiple process IDs</span></span>

```
PS C:\> Debug-Process -Id 1132, 2028
```

<span data-ttu-id="71ff1-123">Det här kommandot kopplar en fel sökare till de processer som har process-ID 1132 och 2028.</span><span class="sxs-lookup"><span data-stu-id="71ff1-123">This command attaches a debugger to the processes that have process IDs 1132 and 2028.</span></span>

### <span data-ttu-id="71ff1-124">Exempel 5: Använd Get-Process för att få en process och koppla sedan en fel sökare till den</span><span class="sxs-lookup"><span data-stu-id="71ff1-124">Example 5: Use Get-Process to get a process then attach a debugger to it</span></span>

```
PS C:\> Get-Process "Windows PowerShell" | Debug-Process
```

<span data-ttu-id="71ff1-125">Det här kommandot kopplar en fel sökare till Windows PowerShell-processer på datorn.</span><span class="sxs-lookup"><span data-stu-id="71ff1-125">This command attaches a debugger to the Windows PowerShell processes on the computer.</span></span>
<span data-ttu-id="71ff1-126">Den använder cmdleten **Get-process** för att hämta Windows PowerShell-processer på datorn och använder en pipeline-operator (|) för att skicka processerna till **Debug-process-** cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="71ff1-126">It uses the **Get-Process** cmdlet to get the Windows PowerShell processes on the computer, and it uses a pipeline operator (|) to send the processes to the **Debug-Process** cmdlet.</span></span>

<span data-ttu-id="71ff1-127">Om du vill ange en viss PowerShell-process använder du ID-parametern för **Get-process**.</span><span class="sxs-lookup"><span data-stu-id="71ff1-127">To specify a particular PowerShell process, use the ID parameter of **Get-Process**.</span></span>

### <span data-ttu-id="71ff1-128">Exempel 6: koppla en fel sökare till en aktuell process på den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="71ff1-128">Example 6: Attach a debugger to a current process on the local computer</span></span>

```
PS C:\> $PID | Debug-Process
```

<span data-ttu-id="71ff1-129">Det här kommandot kopplar en fel sökare till de aktuella Windows PowerShell-processerna på datorn.</span><span class="sxs-lookup"><span data-stu-id="71ff1-129">This command attaches a debugger to the current Windows PowerShell processes on the computer.</span></span>

<span data-ttu-id="71ff1-130">Kommandot använder den automatiska variabeln $PID, som innehåller process-ID: t för den aktuella Windows PowerShell-processen.</span><span class="sxs-lookup"><span data-stu-id="71ff1-130">The command uses the $PID automatic variable, which contains the process ID of the current Windows PowerShell process.</span></span>
<span data-ttu-id="71ff1-131">Sedan använder den en pipeline-operator (|) för att skicka process-ID: t till cmdleten **Debug-process** .</span><span class="sxs-lookup"><span data-stu-id="71ff1-131">Then, it uses a pipeline operator (|) to send the process ID to the **Debug-Process** cmdlet.</span></span>

<span data-ttu-id="71ff1-132">Mer information om den automatiska variabeln $PID finns about_Automatic_Variables.</span><span class="sxs-lookup"><span data-stu-id="71ff1-132">For more information about the $PID automatic variable, see about_Automatic_Variables.</span></span>

### <span data-ttu-id="71ff1-133">Exempel 7: koppla en fel sökare till den angivna processen på flera datorer</span><span class="sxs-lookup"><span data-stu-id="71ff1-133">Example 7: Attach a debugger to the specified process on multiple computers</span></span>

```
PS C:\> Get-Process -ComputerName "Server01", "Server02" -Name "MyApp" | Debug-Process
```

<span data-ttu-id="71ff1-134">Det här kommandot kopplar en fel sökare till MyApp-processerna på Server01-och Server02-datorerna.</span><span class="sxs-lookup"><span data-stu-id="71ff1-134">This command attaches a debugger to the MyApp processes on the Server01 and Server02 computers.</span></span>

<span data-ttu-id="71ff1-135">Kommandot använder cmdleten **Get-process** för att hämta MyApp-processerna på Server01-och Server02-datorerna.</span><span class="sxs-lookup"><span data-stu-id="71ff1-135">The command uses the **Get-Process** cmdlet to get the MyApp processes on the Server01 and Server02 computers.</span></span>
<span data-ttu-id="71ff1-136">Den använder en pipeline-operator för att skicka processerna till Debug-Process-cmdlet, som kopplar fel sökningarna.</span><span class="sxs-lookup"><span data-stu-id="71ff1-136">It uses a pipeline operator to send the processes to the Debug-Process cmdlet, which attaches the debuggers.</span></span>

### <span data-ttu-id="71ff1-137">Exempel 8: koppla en fel sökare till en process som använder parametern InputObject</span><span class="sxs-lookup"><span data-stu-id="71ff1-137">Example 8: Attach a debugger to a process that uses the InputObject parameter</span></span>

```
PS C:\> $P = Get-Process "Windows PowerShell"
PS C:\> Debug-Process -InputObject $P
```

<span data-ttu-id="71ff1-138">Det här kommandot kopplar en fel sökare till Windows PowerShell-processer på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="71ff1-138">This command attaches a debugger to the Windows PowerShell processes on the local computer.</span></span>

<span data-ttu-id="71ff1-139">Det första kommandot använder cmdleten **Get-process** för att hämta Windows PowerShell-processer på datorn.</span><span class="sxs-lookup"><span data-stu-id="71ff1-139">The first command uses the **Get-Process** cmdlet to get the Windows PowerShell processes on the computer.</span></span>
<span data-ttu-id="71ff1-140">Det sparar det resulterande processobjektet i variabeln med namnet $P.</span><span class="sxs-lookup"><span data-stu-id="71ff1-140">It saves the resulting process object in the variable named $P.</span></span>

<span data-ttu-id="71ff1-141">Det andra kommandot använder parametern *InputObject* i cmdleten **Debug-process** för att skicka processobjektet i variabeln $P.</span><span class="sxs-lookup"><span data-stu-id="71ff1-141">The second command uses the *InputObject* parameter of the **Debug-Process** cmdlet to submit the process object in the $P variable.</span></span>

## <span data-ttu-id="71ff1-142">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="71ff1-142">PARAMETERS</span></span>

### <span data-ttu-id="71ff1-143">-ID</span><span class="sxs-lookup"><span data-stu-id="71ff1-143">-Id</span></span>
<span data-ttu-id="71ff1-144">Anger process-ID: n för de processer som ska felsökas.</span><span class="sxs-lookup"><span data-stu-id="71ff1-144">Specifies the process IDs of the processes to be debugged.</span></span>
<span data-ttu-id="71ff1-145">*ID-* parameterns namn är valfritt.</span><span class="sxs-lookup"><span data-stu-id="71ff1-145">The *Id* parameter name is optional.</span></span>

<span data-ttu-id="71ff1-146">Om du vill hitta process-ID för en process skriver du `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="71ff1-146">To find the process ID of a process, type `Get-Process`.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases: PID, ProcessId

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="71ff1-147">– InputObject</span><span class="sxs-lookup"><span data-stu-id="71ff1-147">-InputObject</span></span>
<span data-ttu-id="71ff1-148">Anger de process objekt som representerar processer som ska felsökas.</span><span class="sxs-lookup"><span data-stu-id="71ff1-148">Specifies the process objects that represent processes to be debugged.</span></span>
<span data-ttu-id="71ff1-149">Ange en variabel som innehåller process objekt eller ett kommando som hämtar process objekt, till exempel Get-Process-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="71ff1-149">Enter a variable that contains the process objects or a command that gets the process objects, such as the Get-Process cmdlet.</span></span>
<span data-ttu-id="71ff1-150">Du kan också skicka process objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="71ff1-150">You can also pipe process objects to this cmdlet.</span></span>

```yaml
Type: System.Diagnostics.Process[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="71ff1-151">-Name</span><span class="sxs-lookup"><span data-stu-id="71ff1-151">-Name</span></span>
<span data-ttu-id="71ff1-152">Anger namnen på de processer som ska felsökas.</span><span class="sxs-lookup"><span data-stu-id="71ff1-152">Specifies the names of the processes to be debugged.</span></span>
<span data-ttu-id="71ff1-153">Om det finns fler än en process med samma namn, kopplar denna cmdlet en fel sökare till alla processer med det namnet.</span><span class="sxs-lookup"><span data-stu-id="71ff1-153">If there is more than one process with the same name, this cmdlet attaches a debugger to all processes with that name.</span></span>
<span data-ttu-id="71ff1-154">Parametern *Name* är valfri.</span><span class="sxs-lookup"><span data-stu-id="71ff1-154">The *Name* parameter is optional.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases: ProcessName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="71ff1-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="71ff1-155">-Confirm</span></span>
<span data-ttu-id="71ff1-156">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="71ff1-156">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="71ff1-157">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="71ff1-157">-WhatIf</span></span>
<span data-ttu-id="71ff1-158">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="71ff1-158">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="71ff1-159">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="71ff1-159">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="71ff1-160">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="71ff1-160">CommonParameters</span></span>
<span data-ttu-id="71ff1-161">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="71ff1-161">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="71ff1-162">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="71ff1-162">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="71ff1-163">INDATA</span><span class="sxs-lookup"><span data-stu-id="71ff1-163">INPUTS</span></span>

### <span data-ttu-id="71ff1-164">System. Int32, system. Diagnostics. process, system. String</span><span class="sxs-lookup"><span data-stu-id="71ff1-164">System.Int32, System.Diagnostics.Process, System.String</span></span>
<span data-ttu-id="71ff1-165">Du kan skicka vidare ett process-ID (Int32), ett process objekt (system. Diagnostics. process) eller ett process namn (sträng) till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="71ff1-165">You can pipe a process ID (Int32), a process object (System.Diagnostics.Process), or a process name (String) to this cmdlet.</span></span>

## <span data-ttu-id="71ff1-166">UTDATA</span><span class="sxs-lookup"><span data-stu-id="71ff1-166">OUTPUTS</span></span>

### <span data-ttu-id="71ff1-167">Inget</span><span class="sxs-lookup"><span data-stu-id="71ff1-167">None</span></span>
<span data-ttu-id="71ff1-168">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="71ff1-168">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="71ff1-169">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="71ff1-169">NOTES</span></span>

* <span data-ttu-id="71ff1-170">Denna cmdlet använder metoden AttachDebugger i Win32_Process-klassen Windows Management Instrumentation (WMI).</span><span class="sxs-lookup"><span data-stu-id="71ff1-170">This cmdlet uses the AttachDebugger method of the Windows Management Instrumentation (WMI) Win32_Process class.</span></span> <span data-ttu-id="71ff1-171">Mer information om den här metoden finns i [AttachDebugger-metoden](https://go.microsoft.com/fwlink/?LinkId=143640) i MSDN-biblioteket.</span><span class="sxs-lookup"><span data-stu-id="71ff1-171">For more information about this method, see [AttachDebugger method](https://go.microsoft.com/fwlink/?LinkId=143640) in the MSDN library.</span></span>

## <span data-ttu-id="71ff1-172">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="71ff1-172">RELATED LINKS</span></span>

[<span data-ttu-id="71ff1-173">Fel sökning – process</span><span class="sxs-lookup"><span data-stu-id="71ff1-173">Debug-Process</span></span>](Debug-Process.md)

[<span data-ttu-id="71ff1-174">Hämta process</span><span class="sxs-lookup"><span data-stu-id="71ff1-174">Get-Process</span></span>](Get-Process.md)

[<span data-ttu-id="71ff1-175">Start process</span><span class="sxs-lookup"><span data-stu-id="71ff1-175">Start-Process</span></span>](Start-Process.md)

[<span data-ttu-id="71ff1-176">Stoppa – process</span><span class="sxs-lookup"><span data-stu-id="71ff1-176">Stop-Process</span></span>](Stop-Process.md)

[<span data-ttu-id="71ff1-177">Vänta-process</span><span class="sxs-lookup"><span data-stu-id="71ff1-177">Wait-Process</span></span>](Wait-Process.md)
