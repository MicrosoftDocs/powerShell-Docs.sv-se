---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/debug-process?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Debug-Process
ms.openlocfilehash: 05075a00074eb69a0fe492da95c28c2ad912c291
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94389053"
---
# <span data-ttu-id="ed421-103">Debug-Process</span><span class="sxs-lookup"><span data-stu-id="ed421-103">Debug-Process</span></span>

## <span data-ttu-id="ed421-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="ed421-104">SYNOPSIS</span></span>
<span data-ttu-id="ed421-105">Avbuggar en eller flera processer som körs på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="ed421-105">Debugs one or more processes running on the local computer.</span></span>

## <span data-ttu-id="ed421-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ed421-106">SYNTAX</span></span>

### <span data-ttu-id="ed421-107">Namn (standard)</span><span class="sxs-lookup"><span data-stu-id="ed421-107">Name (Default)</span></span>

```
Debug-Process [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ed421-108">Id</span><span class="sxs-lookup"><span data-stu-id="ed421-108">Id</span></span>

```
Debug-Process [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ed421-109">InputObject</span><span class="sxs-lookup"><span data-stu-id="ed421-109">InputObject</span></span>

```
Debug-Process -InputObject <Process[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="ed421-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="ed421-110">DESCRIPTION</span></span>

<span data-ttu-id="ed421-111">`Debug-Process`Cmdleten kopplar en fel sökare till en eller flera processer som körs på en lokal dator.</span><span class="sxs-lookup"><span data-stu-id="ed421-111">The `Debug-Process` cmdlet attaches a debugger to one or more running processes on a local computer.</span></span>
<span data-ttu-id="ed421-112">Du kan ange processer efter process namn eller process-ID (PID), eller så kan du skicka vidare process objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ed421-112">You can specify the processes by their process name or process ID (PID), or you can pipe process objects to this cmdlet.</span></span>

<span data-ttu-id="ed421-113">Den här cmdleten kopplar den fel sökare som för närvarande är registrerad för processen.</span><span class="sxs-lookup"><span data-stu-id="ed421-113">This cmdlet attaches the debugger that is currently registered for the process.</span></span> <span data-ttu-id="ed421-114">Innan du använder denna cmdlet måste du kontrol lera att en fel sökare har laddats ned och kon figurer ATS korrekt.</span><span class="sxs-lookup"><span data-stu-id="ed421-114">Before using this cmdlet, verify that a debugger is downloaded and correctly configured.</span></span>

## <span data-ttu-id="ed421-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="ed421-115">EXAMPLES</span></span>

### <span data-ttu-id="ed421-116">Exempel 1: koppla en fel sökare till en process på datorn</span><span class="sxs-lookup"><span data-stu-id="ed421-116">Example 1: Attach a debugger to a process on the computer</span></span>

```
PS C:\> Debug-Process -Name "Windows Powershell"
```

<span data-ttu-id="ed421-117">Det här kommandot kopplar en fel sökare till PowerShell-processen på datorn.</span><span class="sxs-lookup"><span data-stu-id="ed421-117">This command attaches a debugger to the PowerShell process on the computer.</span></span>

### <span data-ttu-id="ed421-118">Exempel 2: koppla en fel sökare till alla processer som börjar med den angivna strängen</span><span class="sxs-lookup"><span data-stu-id="ed421-118">Example 2: Attach a debugger to all processes that begin with the specified string</span></span>

```
PS C:\> Debug-Process -Name "SQL*"
```

<span data-ttu-id="ed421-119">Det här kommandot kopplar en fel sökare till alla processer som har namn som börjar med SQL.</span><span class="sxs-lookup"><span data-stu-id="ed421-119">This command attaches a debugger to all processes that have names that begin with SQL.</span></span>

### <span data-ttu-id="ed421-120">Exempel 3: koppla en fel sökare till flera processer</span><span class="sxs-lookup"><span data-stu-id="ed421-120">Example 3: Attach a debugger to multiple processes</span></span>

```
PS C:\> Debug-Process "Winlogon", "Explorer", "Outlook"
```

<span data-ttu-id="ed421-121">Det här kommandot kopplar en fel sökare till Winlogon-, Utforskare-och Outlook-processerna.</span><span class="sxs-lookup"><span data-stu-id="ed421-121">This command attaches a debugger to the Winlogon, Explorer, and Outlook processes.</span></span>

### <span data-ttu-id="ed421-122">Exempel 4: koppla en fel sökare till flera process-ID: n</span><span class="sxs-lookup"><span data-stu-id="ed421-122">Example 4: Attach a debugger to multiple process IDs</span></span>

```
PS C:\> Debug-Process -Id 1132, 2028
```

<span data-ttu-id="ed421-123">Det här kommandot kopplar en fel sökare till de processer som har process-ID 1132 och 2028.</span><span class="sxs-lookup"><span data-stu-id="ed421-123">This command attaches a debugger to the processes that have process IDs 1132 and 2028.</span></span>

### <span data-ttu-id="ed421-124">Exempel 5: Använd Get-Process för att få en process och koppla sedan en fel sökare till den</span><span class="sxs-lookup"><span data-stu-id="ed421-124">Example 5: Use Get-Process to get a process then attach a debugger to it</span></span>

```
PS C:\> Get-Process "Windows PowerShell" | Debug-Process
```

<span data-ttu-id="ed421-125">Det här kommandot kopplar en fel sökare till PowerShell-processerna på datorn.</span><span class="sxs-lookup"><span data-stu-id="ed421-125">This command attaches a debugger to the PowerShell processes on the computer.</span></span> <span data-ttu-id="ed421-126">Den använder `Get-Process` cmdleten för att hämta PowerShell-processer på datorn och använder en pipeline-operator ( `|` ) för att skicka processerna till `Debug-Process` cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="ed421-126">It uses the `Get-Process` cmdlet to get the PowerShell processes on the computer, and it uses a pipeline operator (`|`) to send the processes to the `Debug-Process` cmdlet.</span></span>

<span data-ttu-id="ed421-127">Om du vill ange en viss PowerShell-process använder du ID-parametern för `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="ed421-127">To specify a particular PowerShell process, use the ID parameter of `Get-Process`.</span></span>

### <span data-ttu-id="ed421-128">Exempel 6: koppla en fel sökare till en aktuell process på den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="ed421-128">Example 6: Attach a debugger to a current process on the local computer</span></span>

```
PS C:\> $PID | Debug-Process
```

<span data-ttu-id="ed421-129">Det här kommandot kopplar en fel sökare till de aktuella PowerShell-processerna på datorn.</span><span class="sxs-lookup"><span data-stu-id="ed421-129">This command attaches a debugger to the current PowerShell processes on the computer.</span></span>

<span data-ttu-id="ed421-130">Kommandot använder den `$PID` automatiska variabeln, som innehåller process-ID: t för den aktuella PowerShell-processen.</span><span class="sxs-lookup"><span data-stu-id="ed421-130">The command uses the `$PID` automatic variable, which contains the process ID of the current PowerShell process.</span></span> <span data-ttu-id="ed421-131">Sedan använder den en pipeline-operator ( `|` ) för att skicka process-ID: t till `Debug-Process` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ed421-131">Then, it uses a pipeline operator (`|`) to send the process ID to the `Debug-Process` cmdlet.</span></span>

<span data-ttu-id="ed421-132">Mer information om den `$PID` automatiska variabeln finns i about_Automatic_Variables.</span><span class="sxs-lookup"><span data-stu-id="ed421-132">For more information about the `$PID` automatic variable, see about_Automatic_Variables.</span></span>

### <span data-ttu-id="ed421-133">Exempel 7: koppla en fel sökare till en process som använder parametern InputObject</span><span class="sxs-lookup"><span data-stu-id="ed421-133">Example 7: Attach a debugger to a process that uses the InputObject parameter</span></span>

```
PS C:\> $P = Get-Process "Windows PowerShell"
PS C:\> Debug-Process -InputObject $P
```

<span data-ttu-id="ed421-134">Det här kommandot kopplar en fel sökare till PowerShell-processerna på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="ed421-134">This command attaches a debugger to the PowerShell processes on the local computer.</span></span>

<span data-ttu-id="ed421-135">Det första kommandot använder `Get-Process` cmdleten för att hämta PowerShell-processer på datorn.</span><span class="sxs-lookup"><span data-stu-id="ed421-135">The first command uses the `Get-Process` cmdlet to get the PowerShell processes on the computer.</span></span> <span data-ttu-id="ed421-136">Det sparar det resulterande processobjektet i variabeln med namnet `$P` .</span><span class="sxs-lookup"><span data-stu-id="ed421-136">It saves the resulting process object in the variable named `$P`.</span></span>

<span data-ttu-id="ed421-137">Det andra kommandot använder **InputObject** -parametern för `Debug-Process` cmdleten för att skicka processobjektet i `$P` variabeln.</span><span class="sxs-lookup"><span data-stu-id="ed421-137">The second command uses the **InputObject** parameter of the `Debug-Process` cmdlet to submit the process object in the `$P` variable.</span></span>

## <span data-ttu-id="ed421-138">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="ed421-138">PARAMETERS</span></span>

### <span data-ttu-id="ed421-139">-ID</span><span class="sxs-lookup"><span data-stu-id="ed421-139">-Id</span></span>

<span data-ttu-id="ed421-140">Anger process-ID: n för de processer som ska felsökas.</span><span class="sxs-lookup"><span data-stu-id="ed421-140">Specifies the process IDs of the processes to be debugged.</span></span> <span data-ttu-id="ed421-141">**ID-** parameterns namn är valfritt.</span><span class="sxs-lookup"><span data-stu-id="ed421-141">The **Id** parameter name is optional.</span></span>

<span data-ttu-id="ed421-142">Om du vill hitta process-ID för en process skriver du `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="ed421-142">To find the process ID of a process, type `Get-Process`.</span></span>

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

### <span data-ttu-id="ed421-143">– InputObject</span><span class="sxs-lookup"><span data-stu-id="ed421-143">-InputObject</span></span>

<span data-ttu-id="ed421-144">Anger de process objekt som representerar processer som ska felsökas.</span><span class="sxs-lookup"><span data-stu-id="ed421-144">Specifies the process objects that represent processes to be debugged.</span></span> <span data-ttu-id="ed421-145">Ange en variabel som innehåller process objekt eller ett kommando som hämtar process objekt, t `Get-Process` . ex. cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ed421-145">Enter a variable that contains the process objects or a command that gets the process objects, such as the `Get-Process` cmdlet.</span></span> <span data-ttu-id="ed421-146">Du kan också skicka process objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ed421-146">You can also pipe process objects to this cmdlet.</span></span>

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

### <span data-ttu-id="ed421-147">-Name</span><span class="sxs-lookup"><span data-stu-id="ed421-147">-Name</span></span>

<span data-ttu-id="ed421-148">Anger namnen på de processer som ska felsökas.</span><span class="sxs-lookup"><span data-stu-id="ed421-148">Specifies the names of the processes to be debugged.</span></span> <span data-ttu-id="ed421-149">Om det finns fler än en process med samma namn, kopplar denna cmdlet en fel sökare till alla processer med det namnet.</span><span class="sxs-lookup"><span data-stu-id="ed421-149">If there is more than one process with the same name, this cmdlet attaches a debugger to all processes with that name.</span></span> <span data-ttu-id="ed421-150">Parametern **Name** är valfri.</span><span class="sxs-lookup"><span data-stu-id="ed421-150">The **Name** parameter is optional.</span></span>

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

### <span data-ttu-id="ed421-151">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ed421-151">-Confirm</span></span>

<span data-ttu-id="ed421-152">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ed421-152">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="ed421-153">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ed421-153">-WhatIf</span></span>

<span data-ttu-id="ed421-154">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="ed421-154">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="ed421-155">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="ed421-155">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="ed421-156">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ed421-156">CommonParameters</span></span>

<span data-ttu-id="ed421-157">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ed421-157">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ed421-158">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="ed421-158">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ed421-159">INDATA</span><span class="sxs-lookup"><span data-stu-id="ed421-159">INPUTS</span></span>

### <span data-ttu-id="ed421-160">System. Int32, system. Diagnostics. process, system. String</span><span class="sxs-lookup"><span data-stu-id="ed421-160">System.Int32, System.Diagnostics.Process, System.String</span></span>

<span data-ttu-id="ed421-161">Du kan skicka vidare ett process-ID (Int32), ett process objekt (system. Diagnostics. process) eller ett process namn (sträng) till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ed421-161">You can pipe a process ID (Int32), a process object (System.Diagnostics.Process), or a process name (String) to this cmdlet.</span></span>

## <span data-ttu-id="ed421-162">UTDATA</span><span class="sxs-lookup"><span data-stu-id="ed421-162">OUTPUTS</span></span>

### <span data-ttu-id="ed421-163">Inget</span><span class="sxs-lookup"><span data-stu-id="ed421-163">None</span></span>

<span data-ttu-id="ed421-164">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="ed421-164">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="ed421-165">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="ed421-165">NOTES</span></span>

<span data-ttu-id="ed421-166">Denna cmdlet använder metoden AttachDebugger i Win32_Process-klassen Windows Management Instrumentation (WMI).</span><span class="sxs-lookup"><span data-stu-id="ed421-166">This cmdlet uses the AttachDebugger method of the Windows Management Instrumentation (WMI) Win32_Process class.</span></span> <span data-ttu-id="ed421-167">Mer information om den här metoden finns i [AttachDebugger-metoden](https://go.microsoft.com/fwlink/?LinkId=143640) i MSDN-biblioteket.</span><span class="sxs-lookup"><span data-stu-id="ed421-167">For more information about this method, see [AttachDebugger method](https://go.microsoft.com/fwlink/?LinkId=143640) in the MSDN library.</span></span>

## <span data-ttu-id="ed421-168">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="ed421-168">RELATED LINKS</span></span>

[<span data-ttu-id="ed421-169">Fel sökning – process</span><span class="sxs-lookup"><span data-stu-id="ed421-169">Debug-Process</span></span>](Debug-Process.md)

[<span data-ttu-id="ed421-170">Hämta process</span><span class="sxs-lookup"><span data-stu-id="ed421-170">Get-Process</span></span>](Get-Process.md)

[<span data-ttu-id="ed421-171">Start process</span><span class="sxs-lookup"><span data-stu-id="ed421-171">Start-Process</span></span>](Start-Process.md)

[<span data-ttu-id="ed421-172">Stoppa – process</span><span class="sxs-lookup"><span data-stu-id="ed421-172">Stop-Process</span></span>](Stop-Process.md)

[<span data-ttu-id="ed421-173">Vänta-process</span><span class="sxs-lookup"><span data-stu-id="ed421-173">Wait-Process</span></span>](Wait-Process.md)
