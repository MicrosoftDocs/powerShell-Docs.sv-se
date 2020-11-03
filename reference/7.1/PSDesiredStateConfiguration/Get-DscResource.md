---
external help file: PSDesiredStateConfiguration-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/get-dscresource?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-DscResource
ms.openlocfilehash: a572efd12b35705ebac34d304d2b9ef0a3b1ab60
ms.sourcegitcommit: 9dddf1d2e91ebcd347fcfb7bf6ef670d49a12ab7
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/24/2020
ms.locfileid: "93268743"
---
# <span data-ttu-id="9e2b9-103">Get-DscResource</span><span class="sxs-lookup"><span data-stu-id="9e2b9-103">Get-DscResource</span></span>

## <span data-ttu-id="9e2b9-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="9e2b9-104">SYNOPSIS</span></span>
<span data-ttu-id="9e2b9-105">Hämtar DSC-resurser (Desired State Configuration) som finns på datorn.</span><span class="sxs-lookup"><span data-stu-id="9e2b9-105">Gets Desired State Configuration (DSC) resources present on the computer.</span></span>

## <span data-ttu-id="9e2b9-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9e2b9-106">SYNTAX</span></span>

```
Get-DscResource [[-Name] <String[]>] [[-Module] <Object>] [-Syntax] [<CommonParameters>]
```

## <span data-ttu-id="9e2b9-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="9e2b9-107">DESCRIPTION</span></span>

<span data-ttu-id="9e2b9-108">`Get-DscResource`Cmdlet: en hämtar de POWERSHELL DSC-resurser som finns på datorn.</span><span class="sxs-lookup"><span data-stu-id="9e2b9-108">The `Get-DscResource` cmdlet retrieves the PowerShell DSC resources present on the computer.</span></span> <span data-ttu-id="9e2b9-109">Den här cmdleten identifierar bara de resurser som är installerade i PSModulePath.</span><span class="sxs-lookup"><span data-stu-id="9e2b9-109">This cmdlet discovers only the resources installed in the PSModulePath.</span></span> <span data-ttu-id="9e2b9-110">Den visar information om inbyggda och anpassade providers som skapas av användaren.</span><span class="sxs-lookup"><span data-stu-id="9e2b9-110">It shows the details about built-in and custom providers, which are created by the user.</span></span> <span data-ttu-id="9e2b9-111">Denna cmdlet visar också information om sammansatta resurser, som är andra konfigurationer som paketeras som moduler eller som skapas vid körning i sessionen.</span><span class="sxs-lookup"><span data-stu-id="9e2b9-111">This cmdlet also shows details about composite resources, which are other configurations that are packaged as module or created at run time in the session.</span></span>

## <span data-ttu-id="9e2b9-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="9e2b9-112">EXAMPLES</span></span>

### <span data-ttu-id="9e2b9-113">Exempel 1: Hämta alla resurser på den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="9e2b9-113">Example 1: Get all resources on the local computer</span></span>

```powershell
Get-DscResource
```

<span data-ttu-id="9e2b9-114">Det här kommandot hämtar alla resurser på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="9e2b9-114">This command gets all the resources on the local computer.</span></span>

### <span data-ttu-id="9e2b9-115">Exempel 2: Hämta en resurs genom att ange namnet</span><span class="sxs-lookup"><span data-stu-id="9e2b9-115">Example 2: Get a resource by specifying the name</span></span>

```powershell
Get-DscResource -Name "WindowsFeature"
```

<span data-ttu-id="9e2b9-116">Det här kommandot hämtar WindowsFeature-resursen.</span><span class="sxs-lookup"><span data-stu-id="9e2b9-116">This command gets the WindowsFeature resource.</span></span>

### <span data-ttu-id="9e2b9-117">Exempel 3: Hämta alla resurser från en modul</span><span class="sxs-lookup"><span data-stu-id="9e2b9-117">Example 3: Get all the resources from a module</span></span>

```powershell
Get-DscResource -Module "xHyper-V"
```

<span data-ttu-id="9e2b9-118">Det här kommandot hämtar alla resurser från xHyper-V-modulen.</span><span class="sxs-lookup"><span data-stu-id="9e2b9-118">This command gets all the resources from the xHyper-V module.</span></span>

### <span data-ttu-id="9e2b9-119">Exempel 4: Hämta en resurs med hjälp av jokertecken</span><span class="sxs-lookup"><span data-stu-id="9e2b9-119">Example 4: Get a resource by using wildcard characters</span></span>

```powershell
Get-DscResource -Name P*,r*
```

<span data-ttu-id="9e2b9-120">Det här kommandot hämtar alla resurser som matchar jokertecknet som anges av **namn** parametern.</span><span class="sxs-lookup"><span data-stu-id="9e2b9-120">This command gets all resources that match the wildcard pattern specified by the **Name** parameter.</span></span>

### <span data-ttu-id="9e2b9-121">Exempel 5: Hämta en resurs-syntax</span><span class="sxs-lookup"><span data-stu-id="9e2b9-121">Example 5: Get a resource syntax</span></span>

```powershell
Get-DscResource -Name "WindowsFeature" -Syntax
```

<span data-ttu-id="9e2b9-122">Det här kommandot hämtar WindowsFeature-resursen och visar syntaxen för resursen.</span><span class="sxs-lookup"><span data-stu-id="9e2b9-122">This command gets the WindowsFeature resource, and shows the syntax for the resource.</span></span>

### <span data-ttu-id="9e2b9-123">Exempel 6: Hämta alla egenskaper för en resurs</span><span class="sxs-lookup"><span data-stu-id="9e2b9-123">Example 6: Get all the properties for a resource</span></span>

```powershell
Get-DscResource -Name "User" | Select-Object -ExpandProperty Properties
```

<span data-ttu-id="9e2b9-124">Det här kommandot hämtar användar resursen och använder sedan pipeline-operatorn för att returnera alla egenskaper för användar resursen.</span><span class="sxs-lookup"><span data-stu-id="9e2b9-124">This command gets the User resource, and then uses the pipeline operator to return all the properties for the User resource.</span></span>

### <span data-ttu-id="9e2b9-125">Exempel 7: Hämta alla resurser från en angiven modul med en angiven version</span><span class="sxs-lookup"><span data-stu-id="9e2b9-125">Example 7: Get all the resources from a specified module with a specified version</span></span>

```powershell
Get-DscResource -Module @{ModuleName='xHyper-V';RequiredVersion='3.0.0.0'}
```

<span data-ttu-id="9e2b9-126">Det här kommandot hämtar alla resurser från xHyper-V-modulen med version 3.0.0.0.</span><span class="sxs-lookup"><span data-stu-id="9e2b9-126">This command gets all the resources from xHyper-V module with version 3.0.0.0.</span></span>

## <span data-ttu-id="9e2b9-127">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="9e2b9-127">PARAMETERS</span></span>

### <span data-ttu-id="9e2b9-128">– Modul</span><span class="sxs-lookup"><span data-stu-id="9e2b9-128">-Module</span></span>

<span data-ttu-id="9e2b9-129">Anger namnet eller det fullständigt kvalificerade namnet på den modul som du vill visa DSC-resursen för.</span><span class="sxs-lookup"><span data-stu-id="9e2b9-129">Specifies the name or fully qualified name of the module for which to view the DSC resource.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="9e2b9-130">-Name</span><span class="sxs-lookup"><span data-stu-id="9e2b9-130">-Name</span></span>

<span data-ttu-id="9e2b9-131">Anger en matris med namnen på den DSC-resurs som ska visas.</span><span class="sxs-lookup"><span data-stu-id="9e2b9-131">Specifies an array of names of the DSC resource to view.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="9e2b9-132">-Syntax</span><span class="sxs-lookup"><span data-stu-id="9e2b9-132">-Syntax</span></span>

<span data-ttu-id="9e2b9-133">Anger att cmdleten returnerar kommandosyntaxen för de angivna DSC-resurserna.</span><span class="sxs-lookup"><span data-stu-id="9e2b9-133">Indicates that the cmdlet returns the syntax view of the specified DSC resources.</span></span> <span data-ttu-id="9e2b9-134">Den returnerade syntaxen visar hur du använder resurserna i ett PowerShell-skript.</span><span class="sxs-lookup"><span data-stu-id="9e2b9-134">The returned syntax shows how to use the resources in a PowerShell script.</span></span>

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

### <span data-ttu-id="9e2b9-135">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9e2b9-135">CommonParameters</span></span>

<span data-ttu-id="9e2b9-136">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9e2b9-136">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9e2b9-137">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="9e2b9-137">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9e2b9-138">INDATA</span><span class="sxs-lookup"><span data-stu-id="9e2b9-138">INPUTS</span></span>

### <span data-ttu-id="9e2b9-139">System.String[]</span><span class="sxs-lookup"><span data-stu-id="9e2b9-139">System.String[]</span></span>

### <span data-ttu-id="9e2b9-140">System. Object</span><span class="sxs-lookup"><span data-stu-id="9e2b9-140">System.Object</span></span>

## <span data-ttu-id="9e2b9-141">UTDATA</span><span class="sxs-lookup"><span data-stu-id="9e2b9-141">OUTPUTS</span></span>

### <span data-ttu-id="9e2b9-142">Microsoft. PowerShell. DesiredStateConfiguration. DscResourceInfo []</span><span class="sxs-lookup"><span data-stu-id="9e2b9-142">Microsoft.PowerShell.DesiredStateConfiguration.DscResourceInfo[]</span></span>

### <span data-ttu-id="9e2b9-143">sträng []</span><span class="sxs-lookup"><span data-stu-id="9e2b9-143">string[]</span></span>

## <span data-ttu-id="9e2b9-144">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="9e2b9-144">NOTES</span></span>

## <span data-ttu-id="9e2b9-145">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="9e2b9-145">RELATED LINKS</span></span>

[<span data-ttu-id="9e2b9-146">Översikt över Desired State Configuration för PowerShell</span><span class="sxs-lookup"><span data-stu-id="9e2b9-146">PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/overview)

[<span data-ttu-id="9e2b9-147">Invoke-Dscresource Keyword Supports</span><span class="sxs-lookup"><span data-stu-id="9e2b9-147">Invoke-DscResource</span></span>](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource)

