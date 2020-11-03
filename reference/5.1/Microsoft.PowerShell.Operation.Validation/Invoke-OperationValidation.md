---
external help file: Microsoft.PowerShell.Operation.Validation-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Operation.Validation
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.operation.validation/invoke-operationvalidation?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-OperationValidation
ms.openlocfilehash: 6c9d4001392de48032a0fe1ba3667db90ea614fc
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265280"
---
# <span data-ttu-id="4c11e-103">Invoke-OperationValidation</span><span class="sxs-lookup"><span data-stu-id="4c11e-103">Invoke-OperationValidation</span></span>

## <span data-ttu-id="4c11e-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="4c11e-104">SYNOPSIS</span></span>

<span data-ttu-id="4c11e-105">Anropar tester för åtgärds validerings ramverk.</span><span class="sxs-lookup"><span data-stu-id="4c11e-105">Invokes Operation Validation Framework tests.</span></span>

## <span data-ttu-id="4c11e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4c11e-106">SYNTAX</span></span>

### <span data-ttu-id="4c11e-107">FileAndTest (standard)</span><span class="sxs-lookup"><span data-stu-id="4c11e-107">FileAndTest (Default)</span></span>

```
Invoke-OperationValidation [-TestInfo <PSObject[]>] [-IncludePesterOutput] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="4c11e-108">Sökväg</span><span class="sxs-lookup"><span data-stu-id="4c11e-108">Path</span></span>

```
Invoke-OperationValidation [-testFilePath <String[]>] [-IncludePesterOutput] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="4c11e-109">UseGetOperationTest</span><span class="sxs-lookup"><span data-stu-id="4c11e-109">UseGetOperationTest</span></span>

```
Invoke-OperationValidation [-ModuleName <String[]>] [-TestType <String[]>] [-IncludePesterOutput] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="4c11e-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="4c11e-110">DESCRIPTION</span></span>

<span data-ttu-id="4c11e-111">Cmdlet: en **Invoke-OperationValidation** anropar åtgärds validerings Ramverks test för en angiven modul.</span><span class="sxs-lookup"><span data-stu-id="4c11e-111">The **Invoke-OperationValidation** cmdlet invokes Operation Validation Framework tests for a specified module.</span></span>

## <span data-ttu-id="4c11e-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="4c11e-112">EXAMPLES</span></span>

### <span data-ttu-id="4c11e-113">Exempel 1: anropa ett verifierings test för åtgärden</span><span class="sxs-lookup"><span data-stu-id="4c11e-113">Example 1: Invoke an Operation Validation test</span></span>

```
PS C:\> Get-OperationValidation -ModuleName "OperationValidation" | Invoke-OperationValidation -IncludePesterOutput
Describing Simple Test Suite
 [+] first Operational test 20ms
 [+] second Operational test 19ms
 [+] third Operational test 9ms
Tests completed in 48ms
Passed: 3 Failed: 0 Skipped: 0 Pending: 0
Describing Scenario targeted tests
   Context The RemoteAccess service
    [+] The service is running 37ms
   Context The Firewall Rules
    [+] A rule for TCP port 3389 is enabled 1.19s
    [+] A rule for UDP port 3389 is enabled 11ms
Tests completed in 1.24s
Passed: 3 Failed: 0 Skipped: 0 Pending: 0




   Module: OperationValidation




Result  Name
------- --------
Passed  Simple Test Suite::first Operational test
Passed  Simple Test Suite::second Operational test
Passed  Simple Test Suite::third Operational test
Passed  Scenario targeted tests:The RemoteAccess service:The service is running
Passed  Scenario targeted tests:The Firewall Rules:A rule for TCP port 3389 is enabled
Passed  Scenario targeted tests:The Firewall Rules:A rule for UDP port 3389 is enabled
```

<span data-ttu-id="4c11e-114">Det här kommandot hämtar modulen med namnet OperationValidation och använder pipelinen för att skicka den till cmdleten **Invoke-OperationValidation** , som kör testet.</span><span class="sxs-lookup"><span data-stu-id="4c11e-114">This command gets the module named OperationValidation, and uses the pipeline operator to pass it to the **Invoke-OperationValidation** cmdlet, which runs the test.</span></span>

## <span data-ttu-id="4c11e-115">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="4c11e-115">PARAMETERS</span></span>

### <span data-ttu-id="4c11e-116">-IncludePesterOutput</span><span class="sxs-lookup"><span data-stu-id="4c11e-116">-IncludePesterOutput</span></span>

<span data-ttu-id="4c11e-117">Innehåller pester test-utdata.</span><span class="sxs-lookup"><span data-stu-id="4c11e-117">Includes Pester test output.</span></span>
<span data-ttu-id="4c11e-118">Standardvärdet är $False.</span><span class="sxs-lookup"><span data-stu-id="4c11e-118">The default is $False.</span></span>

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

### <span data-ttu-id="4c11e-119">-Modulnamn</span><span class="sxs-lookup"><span data-stu-id="4c11e-119">-ModuleName</span></span>

<span data-ttu-id="4c11e-120">Anger en matris med namn på moduler.</span><span class="sxs-lookup"><span data-stu-id="4c11e-120">Specifies an array of names of modules.</span></span>

```yaml
Type: System.String[]
Parameter Sets: UseGetOperationTest
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4c11e-121">-testFilePath</span><span class="sxs-lookup"><span data-stu-id="4c11e-121">-testFilePath</span></span>

<span data-ttu-id="4c11e-122">Anger sökvägen till en test fil för åtgärds validerings ramverk.</span><span class="sxs-lookup"><span data-stu-id="4c11e-122">Specifies the path of an Operation Validation Framework test file.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4c11e-123">-TestInfo</span><span class="sxs-lookup"><span data-stu-id="4c11e-123">-TestInfo</span></span>

<span data-ttu-id="4c11e-124">Anger ett anpassat objekt som anger sökvägen till filen och namnet på testet som ska köras.</span><span class="sxs-lookup"><span data-stu-id="4c11e-124">Specifies a custom object that specifies the path to the file and the name of the test to run.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: FileAndTest
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="4c11e-125">-TestType</span><span class="sxs-lookup"><span data-stu-id="4c11e-125">-TestType</span></span>

<span data-ttu-id="4c11e-126">Anger en matris med test typer.</span><span class="sxs-lookup"><span data-stu-id="4c11e-126">Specifies an array of test types.</span></span>
<span data-ttu-id="4c11e-127">Giltiga värden är enkel, fullständig eller både och.</span><span class="sxs-lookup"><span data-stu-id="4c11e-127">Valid values are Simple, Comprehensive, or both.</span></span>
<span data-ttu-id="4c11e-128">Standardvärdet är "enkel, fullständig".</span><span class="sxs-lookup"><span data-stu-id="4c11e-128">The default is "Simple,Comprehensive".</span></span>

```yaml
Type: System.String[]
Parameter Sets: UseGetOperationTest
Aliases:
Accepted values: Simple, Comprehensive

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4c11e-129">-Confirm</span><span class="sxs-lookup"><span data-stu-id="4c11e-129">-Confirm</span></span>

<span data-ttu-id="4c11e-130">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="4c11e-130">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="4c11e-131">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="4c11e-131">-WhatIf</span></span>

<span data-ttu-id="4c11e-132">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="4c11e-132">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="4c11e-133">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="4c11e-133">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="4c11e-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4c11e-134">CommonParameters</span></span>
<span data-ttu-id="4c11e-135">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4c11e-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4c11e-136">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="4c11e-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4c11e-137">INDATA</span><span class="sxs-lookup"><span data-stu-id="4c11e-137">INPUTS</span></span>

### <span data-ttu-id="4c11e-138">PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="4c11e-138">PSCustomObject</span></span>

<span data-ttu-id="4c11e-139">Du kan skicka vidare utdata från **Get-OperationValidation** till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4c11e-139">You can pipe the output of **Get-OperationValidation** to this cmdlet.</span></span>

## <span data-ttu-id="4c11e-140">UTDATA</span><span class="sxs-lookup"><span data-stu-id="4c11e-140">OUTPUTS</span></span>

### <span data-ttu-id="4c11e-141">PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="4c11e-141">PSCustomObject</span></span>

<span data-ttu-id="4c11e-142">**PSCustomObject** beskriver huruvida verifieringen lyckades.</span><span class="sxs-lookup"><span data-stu-id="4c11e-142">The **PSCustomObject** describes whether the validation was successful.</span></span>

## <span data-ttu-id="4c11e-143">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="4c11e-143">NOTES</span></span>

## <span data-ttu-id="4c11e-144">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="4c11e-144">RELATED LINKS</span></span>

[<span data-ttu-id="4c11e-145">Get-OperationValidation</span><span class="sxs-lookup"><span data-stu-id="4c11e-145">Get-OperationValidation</span></span>](Get-OperationValidation.md)
