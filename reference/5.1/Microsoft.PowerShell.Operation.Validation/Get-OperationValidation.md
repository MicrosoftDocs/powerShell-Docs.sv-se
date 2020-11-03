---
external help file: Microsoft.PowerShell.Operation.Validation-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Operation.Validation
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.operation.validation/get-operationvalidation?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-OperationValidation
ms.openlocfilehash: 22ff12848fb7aefaa7f684ee5d8723cc723a5879
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265281"
---
# <span data-ttu-id="267e8-103">Get-OperationValidation</span><span class="sxs-lookup"><span data-stu-id="267e8-103">Get-OperationValidation</span></span>

## <span data-ttu-id="267e8-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="267e8-104">SYNOPSIS</span></span>
<span data-ttu-id="267e8-105">Hämtar tester för åtgärds validerings ramverk.</span><span class="sxs-lookup"><span data-stu-id="267e8-105">Gets Operation Validation Framework tests.</span></span>

## <span data-ttu-id="267e8-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="267e8-106">SYNTAX</span></span>

```
Get-OperationValidation [[-ModuleName] <String[]>] [-TestType <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="267e8-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="267e8-107">DESCRIPTION</span></span>
<span data-ttu-id="267e8-108">**Get-OperationValidation** -cmdlet: en hämtar ett åtgärds validerings Ramverks test för installerade moduler.</span><span class="sxs-lookup"><span data-stu-id="267e8-108">The **Get-OperationValidation** cmdlet gets Operation Validation Framework tests for installed modules.</span></span>

<span data-ttu-id="267e8-109">Moduler som innehåller en diagnostik-mapp inspekteras för pester-tester i den enkla eller fullständiga undermappen, eller både och.</span><span class="sxs-lookup"><span data-stu-id="267e8-109">Modules that include a Diagnostics folder are inspected for Pester tests in the Simple or Comprehensive subfolder, or both.</span></span>

## <span data-ttu-id="267e8-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="267e8-110">EXAMPLES</span></span>

### <span data-ttu-id="267e8-111">Exempel 1: Hämta verifierings test för åtgärd</span><span class="sxs-lookup"><span data-stu-id="267e8-111">Example 1: Get Operation Validation tests</span></span>

```
PS C:\> Get-OperationValidation -ModuleName "C:\temp\modules\AddNumbers"
    Type:     Simple
    File:     addnum.tests.ps1
    FilePath: C:\temp\modules\AddNumbers\Diagnostics\Simple\addnum.tests.ps1
    Name:
        Add-Em
        Subtract em
        Add-Numbers
    Type:     Comprehensive
    File:     Comp.Adding.Tests.ps1
    FilePath: C:\temp\modules\AddNumbers\Diagnostics\Comprehensive\Comp.Adding.Tests.ps1
    Name:
        Comprehensive Adding Tests
        Comprehensive Subtracting Tests
        Comprehensive Examples
```

<span data-ttu-id="267e8-112">Med det här kommandot får du verifieringstester från modulen med namnet AddNumbers i mappen C:\temp\modules.</span><span class="sxs-lookup"><span data-stu-id="267e8-112">This command gets validation tests from the module named AddNumbers in the C:\temp\modules folder.</span></span>

## <span data-ttu-id="267e8-113">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="267e8-113">PARAMETERS</span></span>

### <span data-ttu-id="267e8-114">-Modulnamn</span><span class="sxs-lookup"><span data-stu-id="267e8-114">-ModuleName</span></span>
<span data-ttu-id="267e8-115">Anger en matris med namn på moduler.</span><span class="sxs-lookup"><span data-stu-id="267e8-115">Specifies an array of names of modules.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="267e8-116">-TestType</span><span class="sxs-lookup"><span data-stu-id="267e8-116">-TestType</span></span>
<span data-ttu-id="267e8-117">Anger en matris med test typer.</span><span class="sxs-lookup"><span data-stu-id="267e8-117">Specifies an array of test types.</span></span>
<span data-ttu-id="267e8-118">Giltiga värden är enkel, fullständig eller både och.</span><span class="sxs-lookup"><span data-stu-id="267e8-118">Valid values are Simple, Comprehensive, or both.</span></span>
<span data-ttu-id="267e8-119">Standardvärdet är "enkel, fullständig".</span><span class="sxs-lookup"><span data-stu-id="267e8-119">The default is "Simple,Comprehensive".</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: Simple, Comprehensive

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="267e8-120">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="267e8-120">CommonParameters</span></span>
<span data-ttu-id="267e8-121">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="267e8-121">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="267e8-122">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="267e8-122">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="267e8-123">INDATA</span><span class="sxs-lookup"><span data-stu-id="267e8-123">INPUTS</span></span>

### <span data-ttu-id="267e8-124">Inget</span><span class="sxs-lookup"><span data-stu-id="267e8-124">None</span></span>
<span data-ttu-id="267e8-125">Du kan inte skicka någon indatamängd till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="267e8-125">You cannot pipe any input to this cmdlet.</span></span>

## <span data-ttu-id="267e8-126">UTDATA</span><span class="sxs-lookup"><span data-stu-id="267e8-126">OUTPUTS</span></span>

### <span data-ttu-id="267e8-127">PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="267e8-127">PSCustomObject</span></span>
<span data-ttu-id="267e8-128">**PSCustomObject** beskriver verifieringen.</span><span class="sxs-lookup"><span data-stu-id="267e8-128">The **PSCustomObject** describes the validation.</span></span>

## <span data-ttu-id="267e8-129">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="267e8-129">NOTES</span></span>

## <span data-ttu-id="267e8-130">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="267e8-130">RELATED LINKS</span></span>

[<span data-ttu-id="267e8-131">Invoke-OperationValidation</span><span class="sxs-lookup"><span data-stu-id="267e8-131">Invoke-OperationValidation</span></span>](Invoke-OperationValidation.md)
