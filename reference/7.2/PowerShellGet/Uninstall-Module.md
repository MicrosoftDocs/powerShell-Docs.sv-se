---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/02/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/uninstall-module?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Uninstall-Module
ms.openlocfilehash: 0df911ad8b1f7b4516eef4a1c2b0180893013e3e
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710735"
---
# <span data-ttu-id="cc030-102">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="cc030-102">Uninstall-Module</span></span>

## <span data-ttu-id="cc030-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="cc030-103">SYNOPSIS</span></span>
<span data-ttu-id="cc030-104">Avinstallerar en modul.</span><span class="sxs-lookup"><span data-stu-id="cc030-104">Uninstalls a module.</span></span>

## <span data-ttu-id="cc030-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="cc030-105">SYNTAX</span></span>

### <span data-ttu-id="cc030-106">NameParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="cc030-106">NameParameterSet (Default)</span></span>

```
Uninstall-Module [-Name] <String[]> [-MinimumVersion <String>] [-RequiredVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-AllowPrerelease] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="cc030-107">InputObject</span><span class="sxs-lookup"><span data-stu-id="cc030-107">InputObject</span></span>

```
Uninstall-Module [-InputObject] <PSObject[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="cc030-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="cc030-108">DESCRIPTION</span></span>

<span data-ttu-id="cc030-109">`Uninstall-Module`Cmdleten avinstallerar en angiven modul från den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="cc030-109">The `Uninstall-Module` cmdlet uninstalls a specified module from the local computer.</span></span> <span data-ttu-id="cc030-110">Du kan inte avinstallera en modul om den har andra moduler som beroenden.</span><span class="sxs-lookup"><span data-stu-id="cc030-110">You can't uninstall a module if it has other modules as dependencies.</span></span>

## <span data-ttu-id="cc030-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="cc030-111">EXAMPLES</span></span>

### <span data-ttu-id="cc030-112">Exempel 1: avinstallera en modul</span><span class="sxs-lookup"><span data-stu-id="cc030-112">Example 1: Uninstall a module</span></span>

<span data-ttu-id="cc030-113">Det här exemplet avinstallerar en modul.</span><span class="sxs-lookup"><span data-stu-id="cc030-113">This example uninstalls a module.</span></span>

```powershell
Uninstall-Module -Name SpeculationControl
```

<span data-ttu-id="cc030-114">`Uninstall-Module` använder parametern **Name** för att ange den modul som ska avinstalleras från den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="cc030-114">`Uninstall-Module` uses the **Name** parameter to specify the module to uninstall from the local computer.</span></span>

### <span data-ttu-id="cc030-115">Exempel 2: Använd pipelinen för att avinstallera en modul</span><span class="sxs-lookup"><span data-stu-id="cc030-115">Example 2: Use the pipeline to uninstall a module</span></span>

<span data-ttu-id="cc030-116">I det här exemplet används pipelinen för att avinstallera en modul.</span><span class="sxs-lookup"><span data-stu-id="cc030-116">In this example, the pipeline is used to uninstall a module.</span></span>

```powershell
Get-InstalledModule -Name SpeculationControl | Uninstall-Module
```

<span data-ttu-id="cc030-117">`Get-InstalledModule` använder **Name** -parametern för att ange modulen.</span><span class="sxs-lookup"><span data-stu-id="cc030-117">`Get-InstalledModule` uses the **Name** parameter to specify the module.</span></span> <span data-ttu-id="cc030-118">Objektet skickas ned pipelinen till `Uninstall-Module` och avinstalleras.</span><span class="sxs-lookup"><span data-stu-id="cc030-118">The object is sent down the pipeline to `Uninstall-Module` and is uninstalled.</span></span>

## <span data-ttu-id="cc030-119">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="cc030-119">PARAMETERS</span></span>

### <span data-ttu-id="cc030-120">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="cc030-120">-AllowPrerelease</span></span>

<span data-ttu-id="cc030-121">Gör att du kan avinstallera en modul som är markerad som en för hands version.</span><span class="sxs-lookup"><span data-stu-id="cc030-121">Allows you to uninstall a module marked as a prerelease.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cc030-122">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="cc030-122">-AllVersions</span></span>

<span data-ttu-id="cc030-123">Anger att du vill inkludera alla tillgängliga versioner av en modul.</span><span class="sxs-lookup"><span data-stu-id="cc030-123">Specifies that you want to include all available versions of a module.</span></span> <span data-ttu-id="cc030-124">Du kan inte använda parametern **AllVersions** med parametrarna **MinimumVersion**, **MaximumVersion** eller **RequiredVersion** .</span><span class="sxs-lookup"><span data-stu-id="cc030-124">You can't use the **AllVersions** parameter with the **MinimumVersion**, **MaximumVersion**, or **RequiredVersion** parameters.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cc030-125">-Confirm</span><span class="sxs-lookup"><span data-stu-id="cc030-125">-Confirm</span></span>

<span data-ttu-id="cc030-126">Du uppmanas att bekräfta innan du kör `Uninstall-Module` .</span><span class="sxs-lookup"><span data-stu-id="cc030-126">Prompts you for confirmation before running the `Uninstall-Module`.</span></span>

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

### <span data-ttu-id="cc030-127">-Force</span><span class="sxs-lookup"><span data-stu-id="cc030-127">-Force</span></span>

<span data-ttu-id="cc030-128">Tvingar `Uninstall-Module` körning utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="cc030-128">Forces `Uninstall-Module` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="cc030-129">– InputObject</span><span class="sxs-lookup"><span data-stu-id="cc030-129">-InputObject</span></span>

<span data-ttu-id="cc030-130">Accepterar ett **PSRepositoryItemInfo** -objekt.</span><span class="sxs-lookup"><span data-stu-id="cc030-130">Accepts a **PSRepositoryItemInfo** object.</span></span> <span data-ttu-id="cc030-131">Till exempel, utdata `Get-InstalledModule` till en variabel och Använd variabeln som **InputObject** -argument.</span><span class="sxs-lookup"><span data-stu-id="cc030-131">For example, output `Get-InstalledModule` to a variable and use that variable as the **InputObject** argument.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="cc030-132">– MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="cc030-132">-MaximumVersion</span></span>

<span data-ttu-id="cc030-133">Anger den maximala eller nyaste versionen av modulen som ska avinstalleras.</span><span class="sxs-lookup"><span data-stu-id="cc030-133">Specifies the maximum, or newest, version of the module to uninstall.</span></span> <span data-ttu-id="cc030-134">Parametrarna **MaximumVersion** och **RequiredVersion** kan inte användas i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="cc030-134">The **MaximumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="cc030-135">– MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="cc030-135">-MinimumVersion</span></span>

<span data-ttu-id="cc030-136">Anger den lägsta version av modulen som ska avinstalleras.</span><span class="sxs-lookup"><span data-stu-id="cc030-136">Specifies the minimum version of the module to uninstall.</span></span> <span data-ttu-id="cc030-137">Parametrarna **MinimumVersion** och **RequiredVersion** kan inte användas i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="cc030-137">The **MinimumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="cc030-138">-Name</span><span class="sxs-lookup"><span data-stu-id="cc030-138">-Name</span></span>

<span data-ttu-id="cc030-139">Anger en matris med Modulnamn som ska avinstalleras.</span><span class="sxs-lookup"><span data-stu-id="cc030-139">Specifies an array of module names to uninstall.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="cc030-140">– RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="cc030-140">-RequiredVersion</span></span>

<span data-ttu-id="cc030-141">Anger det exakta versions numret för den modul som ska avinstalleras.</span><span class="sxs-lookup"><span data-stu-id="cc030-141">Specifies the exact version number of the module to uninstall.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="cc030-142">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="cc030-142">-WhatIf</span></span>

<span data-ttu-id="cc030-143">Visar vad som händer om `Uninstall-Module` körs.</span><span class="sxs-lookup"><span data-stu-id="cc030-143">Shows what would happen if `Uninstall-Module` runs.</span></span> <span data-ttu-id="cc030-144">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="cc030-144">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="cc030-145">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cc030-145">CommonParameters</span></span>

<span data-ttu-id="cc030-146">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="cc030-146">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cc030-147">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="cc030-147">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="cc030-148">INDATA</span><span class="sxs-lookup"><span data-stu-id="cc030-148">INPUTS</span></span>

### <span data-ttu-id="cc030-149">System.String[]</span><span class="sxs-lookup"><span data-stu-id="cc030-149">System.String[]</span></span>

### <span data-ttu-id="cc030-150">System. Management. Automation. PSObject []</span><span class="sxs-lookup"><span data-stu-id="cc030-150">System.Management.Automation.PSObject[]</span></span>

### <span data-ttu-id="cc030-151">System. String</span><span class="sxs-lookup"><span data-stu-id="cc030-151">System.String</span></span>

## <span data-ttu-id="cc030-152">UTDATA</span><span class="sxs-lookup"><span data-stu-id="cc030-152">OUTPUTS</span></span>

### <span data-ttu-id="cc030-153">System. Object</span><span class="sxs-lookup"><span data-stu-id="cc030-153">System.Object</span></span>

## <span data-ttu-id="cc030-154">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="cc030-154">NOTES</span></span>

## <span data-ttu-id="cc030-155">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="cc030-155">RELATED LINKS</span></span>

[<span data-ttu-id="cc030-156">Sök-modul</span><span class="sxs-lookup"><span data-stu-id="cc030-156">Find-Module</span></span>](Find-Module.md)

[<span data-ttu-id="cc030-157">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="cc030-157">Get-InstalledModule</span></span>](Get-InstalledModule.md)

[<span data-ttu-id="cc030-158">Publicera-modul</span><span class="sxs-lookup"><span data-stu-id="cc030-158">Publish-Module</span></span>](Publish-Module.md)

[<span data-ttu-id="cc030-159">Spara-modul</span><span class="sxs-lookup"><span data-stu-id="cc030-159">Save-Module</span></span>](Save-Module.md)

[<span data-ttu-id="cc030-160">Update-modul</span><span class="sxs-lookup"><span data-stu-id="cc030-160">Update-Module</span></span>](Update-Module.md)

