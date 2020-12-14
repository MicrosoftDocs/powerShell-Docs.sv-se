---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/debug-process?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Debug-Process
ms.openlocfilehash: 660d2b4845df8091ff8b69b28c4e7695af557122
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709529"
---
# <span data-ttu-id="5b000-102">Debug-Process</span><span class="sxs-lookup"><span data-stu-id="5b000-102">Debug-Process</span></span>

## <span data-ttu-id="5b000-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="5b000-103">SYNOPSIS</span></span>
<span data-ttu-id="5b000-104">Avbuggar en eller flera processer som körs på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="5b000-104">Debugs one or more processes running on the local computer.</span></span>

## <span data-ttu-id="5b000-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5b000-105">SYNTAX</span></span>

### <span data-ttu-id="5b000-106">Namn (standard)</span><span class="sxs-lookup"><span data-stu-id="5b000-106">Name (Default)</span></span>

```
Debug-Process [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="5b000-107">Id</span><span class="sxs-lookup"><span data-stu-id="5b000-107">Id</span></span>

```
Debug-Process [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="5b000-108">InputObject</span><span class="sxs-lookup"><span data-stu-id="5b000-108">InputObject</span></span>

```
Debug-Process -InputObject <Process[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="5b000-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="5b000-109">DESCRIPTION</span></span>

<span data-ttu-id="5b000-110">`Debug-Process`Cmdleten kopplar en fel sökare till en eller flera processer som körs på en lokal dator.</span><span class="sxs-lookup"><span data-stu-id="5b000-110">The `Debug-Process` cmdlet attaches a debugger to one or more running processes on a local computer.</span></span>
<span data-ttu-id="5b000-111">Du kan ange processer efter process namn eller process-ID (PID), eller så kan du skicka vidare process objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5b000-111">You can specify the processes by their process name or process ID (PID), or you can pipe process objects to this cmdlet.</span></span>

<span data-ttu-id="5b000-112">Den här cmdleten kopplar den fel sökare som för närvarande är registrerad för processen.</span><span class="sxs-lookup"><span data-stu-id="5b000-112">This cmdlet attaches the debugger that is currently registered for the process.</span></span> <span data-ttu-id="5b000-113">Innan du använder denna cmdlet måste du kontrol lera att en fel sökare har laddats ned och kon figurer ATS korrekt.</span><span class="sxs-lookup"><span data-stu-id="5b000-113">Before using this cmdlet, verify that a debugger is downloaded and correctly configured.</span></span>

## <span data-ttu-id="5b000-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="5b000-114">EXAMPLES</span></span>

### <span data-ttu-id="5b000-115">Exempel 1: koppla en fel sökare till en process på datorn</span><span class="sxs-lookup"><span data-stu-id="5b000-115">Example 1: Attach a debugger to a process on the computer</span></span>

```
PS C:\> Debug-Process -Name "Windows Powershell"
```

<span data-ttu-id="5b000-116">Det här kommandot kopplar en fel sökare till PowerShell-processen på datorn.</span><span class="sxs-lookup"><span data-stu-id="5b000-116">This command attaches a debugger to the PowerShell process on the computer.</span></span>

### <span data-ttu-id="5b000-117">Exempel 2: koppla en fel sökare till alla processer som börjar med den angivna strängen</span><span class="sxs-lookup"><span data-stu-id="5b000-117">Example 2: Attach a debugger to all processes that begin with the specified string</span></span>

```
PS C:\> Debug-Process -Name "SQL*"
```

<span data-ttu-id="5b000-118">Det här kommandot kopplar en fel sökare till alla processer som har namn som börjar med SQL.</span><span class="sxs-lookup"><span data-stu-id="5b000-118">This command attaches a debugger to all processes that have names that begin with SQL.</span></span>

### <span data-ttu-id="5b000-119">Exempel 3: koppla en fel sökare till flera processer</span><span class="sxs-lookup"><span data-stu-id="5b000-119">Example 3: Attach a debugger to multiple processes</span></span>

```
PS C:\> Debug-Process "Winlogon", "Explorer", "Outlook"
```

<span data-ttu-id="5b000-120">Det här kommandot kopplar en fel sökare till Winlogon-, Utforskare-och Outlook-processerna.</span><span class="sxs-lookup"><span data-stu-id="5b000-120">This command attaches a debugger to the Winlogon, Explorer, and Outlook processes.</span></span>

### <span data-ttu-id="5b000-121">Exempel 4: koppla en fel sökare till flera process-ID: n</span><span class="sxs-lookup"><span data-stu-id="5b000-121">Example 4: Attach a debugger to multiple process IDs</span></span>

```
PS C:\> Debug-Process -Id 1132, 2028
```

<span data-ttu-id="5b000-122">Det här kommandot kopplar en fel sökare till de processer som har process-ID 1132 och 2028.</span><span class="sxs-lookup"><span data-stu-id="5b000-122">This command attaches a debugger to the processes that have process IDs 1132 and 2028.</span></span>

### <span data-ttu-id="5b000-123">Exempel 5: Använd Get-Process för att få en process och koppla sedan en fel sökare till den</span><span class="sxs-lookup"><span data-stu-id="5b000-123">Example 5: Use Get-Process to get a process then attach a debugger to it</span></span>

```
PS C:\> Get-Process "Windows PowerShell" | Debug-Process
```

<span data-ttu-id="5b000-124">Det här kommandot kopplar en fel sökare till PowerShell-processerna på datorn.</span><span class="sxs-lookup"><span data-stu-id="5b000-124">This command attaches a debugger to the PowerShell processes on the computer.</span></span> <span data-ttu-id="5b000-125">Den använder `Get-Process` cmdleten för att hämta PowerShell-processer på datorn och använder en pipeline-operator ( `|` ) för att skicka processerna till `Debug-Process` cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="5b000-125">It uses the `Get-Process` cmdlet to get the PowerShell processes on the computer, and it uses a pipeline operator (`|`) to send the processes to the `Debug-Process` cmdlet.</span></span>

<span data-ttu-id="5b000-126">Om du vill ange en viss PowerShell-process använder du ID-parametern för `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="5b000-126">To specify a particular PowerShell process, use the ID parameter of `Get-Process`.</span></span>

### <span data-ttu-id="5b000-127">Exempel 6: koppla en fel sökare till en aktuell process på den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="5b000-127">Example 6: Attach a debugger to a current process on the local computer</span></span>

```
PS C:\> $PID | Debug-Process
```

<span data-ttu-id="5b000-128">Det här kommandot kopplar en fel sökare till de aktuella PowerShell-processerna på datorn.</span><span class="sxs-lookup"><span data-stu-id="5b000-128">This command attaches a debugger to the current PowerShell processes on the computer.</span></span>

<span data-ttu-id="5b000-129">Kommandot använder den `$PID` automatiska variabeln, som innehåller process-ID: t för den aktuella PowerShell-processen.</span><span class="sxs-lookup"><span data-stu-id="5b000-129">The command uses the `$PID` automatic variable, which contains the process ID of the current PowerShell process.</span></span> <span data-ttu-id="5b000-130">Sedan använder den en pipeline-operator ( `|` ) för att skicka process-ID: t till `Debug-Process` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="5b000-130">Then, it uses a pipeline operator (`|`) to send the process ID to the `Debug-Process` cmdlet.</span></span>

<span data-ttu-id="5b000-131">Mer information om den `$PID` automatiska variabeln finns i about_Automatic_Variables.</span><span class="sxs-lookup"><span data-stu-id="5b000-131">For more information about the `$PID` automatic variable, see about_Automatic_Variables.</span></span>

### <span data-ttu-id="5b000-132">Exempel 7: koppla en fel sökare till en process som använder parametern InputObject</span><span class="sxs-lookup"><span data-stu-id="5b000-132">Example 7: Attach a debugger to a process that uses the InputObject parameter</span></span>

```
PS C:\> $P = Get-Process "Windows PowerShell"
PS C:\> Debug-Process -InputObject $P
```

<span data-ttu-id="5b000-133">Det här kommandot kopplar en fel sökare till PowerShell-processerna på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="5b000-133">This command attaches a debugger to the PowerShell processes on the local computer.</span></span>

<span data-ttu-id="5b000-134">Det första kommandot använder `Get-Process` cmdleten för att hämta PowerShell-processer på datorn.</span><span class="sxs-lookup"><span data-stu-id="5b000-134">The first command uses the `Get-Process` cmdlet to get the PowerShell processes on the computer.</span></span> <span data-ttu-id="5b000-135">Det sparar det resulterande processobjektet i variabeln med namnet `$P` .</span><span class="sxs-lookup"><span data-stu-id="5b000-135">It saves the resulting process object in the variable named `$P`.</span></span>

<span data-ttu-id="5b000-136">Det andra kommandot använder **InputObject** -parametern för `Debug-Process` cmdleten för att skicka processobjektet i `$P` variabeln.</span><span class="sxs-lookup"><span data-stu-id="5b000-136">The second command uses the **InputObject** parameter of the `Debug-Process` cmdlet to submit the process object in the `$P` variable.</span></span>

## <span data-ttu-id="5b000-137">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="5b000-137">PARAMETERS</span></span>

### <span data-ttu-id="5b000-138">-ID</span><span class="sxs-lookup"><span data-stu-id="5b000-138">-Id</span></span>

<span data-ttu-id="5b000-139">Anger process-ID: n för de processer som ska felsökas.</span><span class="sxs-lookup"><span data-stu-id="5b000-139">Specifies the process IDs of the processes to be debugged.</span></span> <span data-ttu-id="5b000-140">**ID-** parameterns namn är valfritt.</span><span class="sxs-lookup"><span data-stu-id="5b000-140">The **Id** parameter name is optional.</span></span>

<span data-ttu-id="5b000-141">Om du vill hitta process-ID för en process skriver du `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="5b000-141">To find the process ID of a process, type `Get-Process`.</span></span>

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

### <span data-ttu-id="5b000-142">– InputObject</span><span class="sxs-lookup"><span data-stu-id="5b000-142">-InputObject</span></span>

<span data-ttu-id="5b000-143">Anger de process objekt som representerar processer som ska felsökas.</span><span class="sxs-lookup"><span data-stu-id="5b000-143">Specifies the process objects that represent processes to be debugged.</span></span> <span data-ttu-id="5b000-144">Ange en variabel som innehåller process objekt eller ett kommando som hämtar process objekt, t `Get-Process` . ex. cmdleten.</span><span class="sxs-lookup"><span data-stu-id="5b000-144">Enter a variable that contains the process objects or a command that gets the process objects, such as the `Get-Process` cmdlet.</span></span> <span data-ttu-id="5b000-145">Du kan också skicka process objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5b000-145">You can also pipe process objects to this cmdlet.</span></span>

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

### <span data-ttu-id="5b000-146">-Name</span><span class="sxs-lookup"><span data-stu-id="5b000-146">-Name</span></span>

<span data-ttu-id="5b000-147">Anger namnen på de processer som ska felsökas.</span><span class="sxs-lookup"><span data-stu-id="5b000-147">Specifies the names of the processes to be debugged.</span></span> <span data-ttu-id="5b000-148">Om det finns fler än en process med samma namn, kopplar denna cmdlet en fel sökare till alla processer med det namnet.</span><span class="sxs-lookup"><span data-stu-id="5b000-148">If there is more than one process with the same name, this cmdlet attaches a debugger to all processes with that name.</span></span> <span data-ttu-id="5b000-149">Parametern **Name** är valfri.</span><span class="sxs-lookup"><span data-stu-id="5b000-149">The **Name** parameter is optional.</span></span>

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

### <span data-ttu-id="5b000-150">-Confirm</span><span class="sxs-lookup"><span data-stu-id="5b000-150">-Confirm</span></span>

<span data-ttu-id="5b000-151">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="5b000-151">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="5b000-152">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="5b000-152">-WhatIf</span></span>

<span data-ttu-id="5b000-153">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="5b000-153">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="5b000-154">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="5b000-154">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="5b000-155">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5b000-155">CommonParameters</span></span>

<span data-ttu-id="5b000-156">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5b000-156">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5b000-157">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="5b000-157">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5b000-158">INDATA</span><span class="sxs-lookup"><span data-stu-id="5b000-158">INPUTS</span></span>

### <span data-ttu-id="5b000-159">System. Int32, system. Diagnostics. process, system. String</span><span class="sxs-lookup"><span data-stu-id="5b000-159">System.Int32, System.Diagnostics.Process, System.String</span></span>

<span data-ttu-id="5b000-160">Du kan skicka vidare ett process-ID (Int32), ett process objekt (system. Diagnostics. process) eller ett process namn (sträng) till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5b000-160">You can pipe a process ID (Int32), a process object (System.Diagnostics.Process), or a process name (String) to this cmdlet.</span></span>

## <span data-ttu-id="5b000-161">UTDATA</span><span class="sxs-lookup"><span data-stu-id="5b000-161">OUTPUTS</span></span>

### <span data-ttu-id="5b000-162">Inga</span><span class="sxs-lookup"><span data-stu-id="5b000-162">None</span></span>

<span data-ttu-id="5b000-163">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="5b000-163">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="5b000-164">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="5b000-164">NOTES</span></span>

<span data-ttu-id="5b000-165">Denna cmdlet använder metoden AttachDebugger i Win32_Process-klassen Windows Management Instrumentation (WMI).</span><span class="sxs-lookup"><span data-stu-id="5b000-165">This cmdlet uses the AttachDebugger method of the Windows Management Instrumentation (WMI) Win32_Process class.</span></span> <span data-ttu-id="5b000-166">Mer information om den här metoden finns i [AttachDebugger-metoden](https://go.microsoft.com/fwlink/?LinkId=143640) i MSDN-biblioteket.</span><span class="sxs-lookup"><span data-stu-id="5b000-166">For more information about this method, see [AttachDebugger method](https://go.microsoft.com/fwlink/?LinkId=143640) in the MSDN library.</span></span>

## <span data-ttu-id="5b000-167">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="5b000-167">RELATED LINKS</span></span>

[<span data-ttu-id="5b000-168">Fel sökning – process</span><span class="sxs-lookup"><span data-stu-id="5b000-168">Debug-Process</span></span>](Debug-Process.md)

[<span data-ttu-id="5b000-169">Hämta process</span><span class="sxs-lookup"><span data-stu-id="5b000-169">Get-Process</span></span>](Get-Process.md)

[<span data-ttu-id="5b000-170">Start process</span><span class="sxs-lookup"><span data-stu-id="5b000-170">Start-Process</span></span>](Start-Process.md)

[<span data-ttu-id="5b000-171">Stoppa – process</span><span class="sxs-lookup"><span data-stu-id="5b000-171">Stop-Process</span></span>](Stop-Process.md)

[<span data-ttu-id="5b000-172">Vänta-process</span><span class="sxs-lookup"><span data-stu-id="5b000-172">Wait-Process</span></span>](Wait-Process.md)
