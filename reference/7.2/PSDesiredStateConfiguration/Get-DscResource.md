---
external help file: PSDesiredStateConfiguration-help.xml
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/get-dscresource?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-DscResource
ms.openlocfilehash: dbc036562da0172dc4406f169891d2cd1c5e4098
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709354"
---
# <span data-ttu-id="361d7-102">Get-DscResource</span><span class="sxs-lookup"><span data-stu-id="361d7-102">Get-DscResource</span></span>

## <span data-ttu-id="361d7-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="361d7-103">SYNOPSIS</span></span>
<span data-ttu-id="361d7-104">Hämtar DSC-resurser (Desired State Configuration) som finns på datorn.</span><span class="sxs-lookup"><span data-stu-id="361d7-104">Gets Desired State Configuration (DSC) resources present on the computer.</span></span>

## <span data-ttu-id="361d7-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="361d7-105">SYNTAX</span></span>

```
Get-DscResource [[-Name] <String[]>] [[-Module] <Object>] [-Syntax] [<CommonParameters>]
```

## <span data-ttu-id="361d7-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="361d7-106">DESCRIPTION</span></span>

<span data-ttu-id="361d7-107">`Get-DscResource`Cmdlet: en hämtar de POWERSHELL DSC-resurser som finns på datorn.</span><span class="sxs-lookup"><span data-stu-id="361d7-107">The `Get-DscResource` cmdlet retrieves the PowerShell DSC resources present on the computer.</span></span> <span data-ttu-id="361d7-108">Den här cmdleten identifierar bara de resurser som är installerade i PSModulePath.</span><span class="sxs-lookup"><span data-stu-id="361d7-108">This cmdlet discovers only the resources installed in the PSModulePath.</span></span> <span data-ttu-id="361d7-109">Den visar information om inbyggda och anpassade providers som skapas av användaren.</span><span class="sxs-lookup"><span data-stu-id="361d7-109">It shows the details about built-in and custom providers, which are created by the user.</span></span> <span data-ttu-id="361d7-110">Denna cmdlet visar också information om sammansatta resurser, som är andra konfigurationer som paketeras som moduler eller som skapas vid körning i sessionen.</span><span class="sxs-lookup"><span data-stu-id="361d7-110">This cmdlet also shows details about composite resources, which are other configurations that are packaged as module or created at run time in the session.</span></span>

## <span data-ttu-id="361d7-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="361d7-111">EXAMPLES</span></span>

### <span data-ttu-id="361d7-112">Exempel 1: Hämta alla resurser på den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="361d7-112">Example 1: Get all resources on the local computer</span></span>

```powershell
Get-DscResource
```

<span data-ttu-id="361d7-113">Det här kommandot hämtar alla resurser på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="361d7-113">This command gets all the resources on the local computer.</span></span>

### <span data-ttu-id="361d7-114">Exempel 2: Hämta en resurs genom att ange namnet</span><span class="sxs-lookup"><span data-stu-id="361d7-114">Example 2: Get a resource by specifying the name</span></span>

```powershell
Get-DscResource -Name "WindowsFeature"
```

<span data-ttu-id="361d7-115">Det här kommandot hämtar WindowsFeature-resursen.</span><span class="sxs-lookup"><span data-stu-id="361d7-115">This command gets the WindowsFeature resource.</span></span>

### <span data-ttu-id="361d7-116">Exempel 3: Hämta alla resurser från en modul</span><span class="sxs-lookup"><span data-stu-id="361d7-116">Example 3: Get all the resources from a module</span></span>

```powershell
Get-DscResource -Module "xHyper-V"
```

<span data-ttu-id="361d7-117">Det här kommandot hämtar alla resurser från xHyper-V-modulen.</span><span class="sxs-lookup"><span data-stu-id="361d7-117">This command gets all the resources from the xHyper-V module.</span></span>

### <span data-ttu-id="361d7-118">Exempel 4: Hämta en resurs med hjälp av jokertecken</span><span class="sxs-lookup"><span data-stu-id="361d7-118">Example 4: Get a resource by using wildcard characters</span></span>

```powershell
Get-DscResource -Name P*,r*
```

<span data-ttu-id="361d7-119">Det här kommandot hämtar alla resurser som matchar jokertecknet som anges av **namn** parametern.</span><span class="sxs-lookup"><span data-stu-id="361d7-119">This command gets all resources that match the wildcard pattern specified by the **Name** parameter.</span></span>

### <span data-ttu-id="361d7-120">Exempel 5: Hämta en resurs-syntax</span><span class="sxs-lookup"><span data-stu-id="361d7-120">Example 5: Get a resource syntax</span></span>

```powershell
Get-DscResource -Name "WindowsFeature" -Syntax
```

<span data-ttu-id="361d7-121">Det här kommandot hämtar WindowsFeature-resursen och visar syntaxen för resursen.</span><span class="sxs-lookup"><span data-stu-id="361d7-121">This command gets the WindowsFeature resource, and shows the syntax for the resource.</span></span>

### <span data-ttu-id="361d7-122">Exempel 6: Hämta alla egenskaper för en resurs</span><span class="sxs-lookup"><span data-stu-id="361d7-122">Example 6: Get all the properties for a resource</span></span>

```powershell
Get-DscResource -Name "User" | Select-Object -ExpandProperty Properties
```

<span data-ttu-id="361d7-123">Det här kommandot hämtar användar resursen och använder sedan pipeline-operatorn för att returnera alla egenskaper för användar resursen.</span><span class="sxs-lookup"><span data-stu-id="361d7-123">This command gets the User resource, and then uses the pipeline operator to return all the properties for the User resource.</span></span>

### <span data-ttu-id="361d7-124">Exempel 7: Hämta alla resurser från en angiven modul med en angiven version</span><span class="sxs-lookup"><span data-stu-id="361d7-124">Example 7: Get all the resources from a specified module with a specified version</span></span>

```powershell
Get-DscResource -Module @{ModuleName='xHyper-V';RequiredVersion='3.0.0.0'}
```

<span data-ttu-id="361d7-125">Det här kommandot hämtar alla resurser från xHyper-V-modulen med version 3.0.0.0.</span><span class="sxs-lookup"><span data-stu-id="361d7-125">This command gets all the resources from xHyper-V module with version 3.0.0.0.</span></span>

## <span data-ttu-id="361d7-126">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="361d7-126">PARAMETERS</span></span>

### <span data-ttu-id="361d7-127">– Modul</span><span class="sxs-lookup"><span data-stu-id="361d7-127">-Module</span></span>

<span data-ttu-id="361d7-128">Anger namnet eller det fullständigt kvalificerade namnet på den modul som du vill visa DSC-resursen för.</span><span class="sxs-lookup"><span data-stu-id="361d7-128">Specifies the name or fully qualified name of the module for which to view the DSC resource.</span></span>

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

### <span data-ttu-id="361d7-129">-Name</span><span class="sxs-lookup"><span data-stu-id="361d7-129">-Name</span></span>

<span data-ttu-id="361d7-130">Anger en matris med namnen på den DSC-resurs som ska visas.</span><span class="sxs-lookup"><span data-stu-id="361d7-130">Specifies an array of names of the DSC resource to view.</span></span>

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

### <span data-ttu-id="361d7-131">-Syntax</span><span class="sxs-lookup"><span data-stu-id="361d7-131">-Syntax</span></span>

<span data-ttu-id="361d7-132">Anger att cmdleten returnerar kommandosyntaxen för de angivna DSC-resurserna.</span><span class="sxs-lookup"><span data-stu-id="361d7-132">Indicates that the cmdlet returns the syntax view of the specified DSC resources.</span></span> <span data-ttu-id="361d7-133">Den returnerade syntaxen visar hur du använder resurserna i ett PowerShell-skript.</span><span class="sxs-lookup"><span data-stu-id="361d7-133">The returned syntax shows how to use the resources in a PowerShell script.</span></span>

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

### <span data-ttu-id="361d7-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="361d7-134">CommonParameters</span></span>

<span data-ttu-id="361d7-135">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="361d7-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="361d7-136">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="361d7-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="361d7-137">INDATA</span><span class="sxs-lookup"><span data-stu-id="361d7-137">INPUTS</span></span>

### <span data-ttu-id="361d7-138">System.String[]</span><span class="sxs-lookup"><span data-stu-id="361d7-138">System.String[]</span></span>

### <span data-ttu-id="361d7-139">System. Object</span><span class="sxs-lookup"><span data-stu-id="361d7-139">System.Object</span></span>

## <span data-ttu-id="361d7-140">UTDATA</span><span class="sxs-lookup"><span data-stu-id="361d7-140">OUTPUTS</span></span>

### <span data-ttu-id="361d7-141">Microsoft. PowerShell. DesiredStateConfiguration. DscResourceInfo []</span><span class="sxs-lookup"><span data-stu-id="361d7-141">Microsoft.PowerShell.DesiredStateConfiguration.DscResourceInfo[]</span></span>

### <span data-ttu-id="361d7-142">sträng []</span><span class="sxs-lookup"><span data-stu-id="361d7-142">string[]</span></span>

## <span data-ttu-id="361d7-143">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="361d7-143">NOTES</span></span>

## <span data-ttu-id="361d7-144">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="361d7-144">RELATED LINKS</span></span>

[<span data-ttu-id="361d7-145">Översikt över Desired State Configuration för PowerShell</span><span class="sxs-lookup"><span data-stu-id="361d7-145">PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/overview)

[<span data-ttu-id="361d7-146">Invoke-Dscresource Keyword Supports</span><span class="sxs-lookup"><span data-stu-id="361d7-146">Invoke-DscResource</span></span>](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource)

