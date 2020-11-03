---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/02/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/uninstall-module?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Uninstall-Module
ms.openlocfilehash: 77a89a9189d3ae8f7c3450bdddbe9456b4e941c7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264056"
---
# <span data-ttu-id="6d89f-103">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="6d89f-103">Uninstall-Module</span></span>

## <span data-ttu-id="6d89f-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="6d89f-104">SYNOPSIS</span></span>
<span data-ttu-id="6d89f-105">Avinstallerar en modul.</span><span class="sxs-lookup"><span data-stu-id="6d89f-105">Uninstalls a module.</span></span>

## <span data-ttu-id="6d89f-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6d89f-106">SYNTAX</span></span>

### <span data-ttu-id="6d89f-107">NameParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="6d89f-107">NameParameterSet (Default)</span></span>

```
Uninstall-Module [-Name] <String[]> [-MinimumVersion <String>] [-RequiredVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-AllowPrerelease] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="6d89f-108">InputObject</span><span class="sxs-lookup"><span data-stu-id="6d89f-108">InputObject</span></span>

```
Uninstall-Module [-InputObject] <PSObject[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="6d89f-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="6d89f-109">DESCRIPTION</span></span>

<span data-ttu-id="6d89f-110">`Uninstall-Module`Cmdleten avinstallerar en angiven modul från den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="6d89f-110">The `Uninstall-Module` cmdlet uninstalls a specified module from the local computer.</span></span> <span data-ttu-id="6d89f-111">Du kan inte avinstallera en modul om den har andra moduler som beroenden.</span><span class="sxs-lookup"><span data-stu-id="6d89f-111">You can't uninstall a module if it has other modules as dependencies.</span></span>

## <span data-ttu-id="6d89f-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="6d89f-112">EXAMPLES</span></span>

### <span data-ttu-id="6d89f-113">Exempel 1: avinstallera en modul</span><span class="sxs-lookup"><span data-stu-id="6d89f-113">Example 1: Uninstall a module</span></span>

<span data-ttu-id="6d89f-114">Det här exemplet avinstallerar en modul.</span><span class="sxs-lookup"><span data-stu-id="6d89f-114">This example uninstalls a module.</span></span>

```powershell
Uninstall-Module -Name SpeculationControl
```

<span data-ttu-id="6d89f-115">`Uninstall-Module` använder parametern **Name** för att ange den modul som ska avinstalleras från den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="6d89f-115">`Uninstall-Module` uses the **Name** parameter to specify the module to uninstall from the local computer.</span></span>

### <span data-ttu-id="6d89f-116">Exempel 2: Använd pipelinen för att avinstallera en modul</span><span class="sxs-lookup"><span data-stu-id="6d89f-116">Example 2: Use the pipeline to uninstall a module</span></span>

<span data-ttu-id="6d89f-117">I det här exemplet används pipelinen för att avinstallera en modul.</span><span class="sxs-lookup"><span data-stu-id="6d89f-117">In this example, the pipeline is used to uninstall a module.</span></span>

```powershell
Get-InstalledModule -Name SpeculationControl | Uninstall-Module
```

<span data-ttu-id="6d89f-118">`Get-InstalledModule` använder **Name** -parametern för att ange modulen.</span><span class="sxs-lookup"><span data-stu-id="6d89f-118">`Get-InstalledModule` uses the **Name** parameter to specify the module.</span></span> <span data-ttu-id="6d89f-119">Objektet skickas ned pipelinen till `Uninstall-Module` och avinstalleras.</span><span class="sxs-lookup"><span data-stu-id="6d89f-119">The object is sent down the pipeline to `Uninstall-Module` and is uninstalled.</span></span>

## <span data-ttu-id="6d89f-120">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="6d89f-120">PARAMETERS</span></span>

### <span data-ttu-id="6d89f-121">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="6d89f-121">-AllowPrerelease</span></span>

<span data-ttu-id="6d89f-122">Gör att du kan avinstallera en modul som är markerad som en för hands version.</span><span class="sxs-lookup"><span data-stu-id="6d89f-122">Allows you to uninstall a module marked as a prerelease.</span></span>

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

### <span data-ttu-id="6d89f-123">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="6d89f-123">-AllVersions</span></span>

<span data-ttu-id="6d89f-124">Anger att du vill inkludera alla tillgängliga versioner av en modul.</span><span class="sxs-lookup"><span data-stu-id="6d89f-124">Specifies that you want to include all available versions of a module.</span></span> <span data-ttu-id="6d89f-125">Du kan inte använda parametern **AllVersions** med parametrarna **MinimumVersion** , **MaximumVersion** eller **RequiredVersion** .</span><span class="sxs-lookup"><span data-stu-id="6d89f-125">You can't use the **AllVersions** parameter with the **MinimumVersion** , **MaximumVersion** , or **RequiredVersion** parameters.</span></span>

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

### <span data-ttu-id="6d89f-126">-Confirm</span><span class="sxs-lookup"><span data-stu-id="6d89f-126">-Confirm</span></span>

<span data-ttu-id="6d89f-127">Du uppmanas att bekräfta innan du kör `Uninstall-Module` .</span><span class="sxs-lookup"><span data-stu-id="6d89f-127">Prompts you for confirmation before running the `Uninstall-Module`.</span></span>

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

### <span data-ttu-id="6d89f-128">-Force</span><span class="sxs-lookup"><span data-stu-id="6d89f-128">-Force</span></span>

<span data-ttu-id="6d89f-129">Tvingar `Uninstall-Module` körning utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="6d89f-129">Forces `Uninstall-Module` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="6d89f-130">– InputObject</span><span class="sxs-lookup"><span data-stu-id="6d89f-130">-InputObject</span></span>

<span data-ttu-id="6d89f-131">Accepterar ett **PSRepositoryItemInfo** -objekt.</span><span class="sxs-lookup"><span data-stu-id="6d89f-131">Accepts a **PSRepositoryItemInfo** object.</span></span> <span data-ttu-id="6d89f-132">Till exempel, utdata `Get-InstalledModule` till en variabel och Använd variabeln som **InputObject** -argument.</span><span class="sxs-lookup"><span data-stu-id="6d89f-132">For example, output `Get-InstalledModule` to a variable and use that variable as the **InputObject** argument.</span></span>

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

### <span data-ttu-id="6d89f-133">– MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="6d89f-133">-MaximumVersion</span></span>

<span data-ttu-id="6d89f-134">Anger den maximala eller nyaste versionen av modulen som ska avinstalleras.</span><span class="sxs-lookup"><span data-stu-id="6d89f-134">Specifies the maximum, or newest, version of the module to uninstall.</span></span> <span data-ttu-id="6d89f-135">Parametrarna **MaximumVersion** och **RequiredVersion** kan inte användas i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="6d89f-135">The **MaximumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="6d89f-136">– MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="6d89f-136">-MinimumVersion</span></span>

<span data-ttu-id="6d89f-137">Anger den lägsta version av modulen som ska avinstalleras.</span><span class="sxs-lookup"><span data-stu-id="6d89f-137">Specifies the minimum version of the module to uninstall.</span></span> <span data-ttu-id="6d89f-138">Parametrarna **MinimumVersion** och **RequiredVersion** kan inte användas i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="6d89f-138">The **MinimumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="6d89f-139">-Name</span><span class="sxs-lookup"><span data-stu-id="6d89f-139">-Name</span></span>

<span data-ttu-id="6d89f-140">Anger en matris med Modulnamn som ska avinstalleras.</span><span class="sxs-lookup"><span data-stu-id="6d89f-140">Specifies an array of module names to uninstall.</span></span>

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

### <span data-ttu-id="6d89f-141">– RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="6d89f-141">-RequiredVersion</span></span>

<span data-ttu-id="6d89f-142">Anger det exakta versions numret för den modul som ska avinstalleras.</span><span class="sxs-lookup"><span data-stu-id="6d89f-142">Specifies the exact version number of the module to uninstall.</span></span>

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

### <span data-ttu-id="6d89f-143">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="6d89f-143">-WhatIf</span></span>

<span data-ttu-id="6d89f-144">Visar vad som händer om `Uninstall-Module` körs.</span><span class="sxs-lookup"><span data-stu-id="6d89f-144">Shows what would happen if `Uninstall-Module` runs.</span></span> <span data-ttu-id="6d89f-145">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="6d89f-145">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="6d89f-146">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6d89f-146">CommonParameters</span></span>

<span data-ttu-id="6d89f-147">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6d89f-147">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6d89f-148">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="6d89f-148">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6d89f-149">INDATA</span><span class="sxs-lookup"><span data-stu-id="6d89f-149">INPUTS</span></span>

### <span data-ttu-id="6d89f-150">System.String[]</span><span class="sxs-lookup"><span data-stu-id="6d89f-150">System.String[]</span></span>

### <span data-ttu-id="6d89f-151">System. Management. Automation. PSObject []</span><span class="sxs-lookup"><span data-stu-id="6d89f-151">System.Management.Automation.PSObject[]</span></span>

### <span data-ttu-id="6d89f-152">System. String</span><span class="sxs-lookup"><span data-stu-id="6d89f-152">System.String</span></span>

## <span data-ttu-id="6d89f-153">UTDATA</span><span class="sxs-lookup"><span data-stu-id="6d89f-153">OUTPUTS</span></span>

### <span data-ttu-id="6d89f-154">System. Object</span><span class="sxs-lookup"><span data-stu-id="6d89f-154">System.Object</span></span>

## <span data-ttu-id="6d89f-155">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="6d89f-155">NOTES</span></span>

## <span data-ttu-id="6d89f-156">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="6d89f-156">RELATED LINKS</span></span>

[<span data-ttu-id="6d89f-157">Sök-modul</span><span class="sxs-lookup"><span data-stu-id="6d89f-157">Find-Module</span></span>](Find-Module.md)

[<span data-ttu-id="6d89f-158">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="6d89f-158">Get-InstalledModule</span></span>](Get-InstalledModule.md)

[<span data-ttu-id="6d89f-159">Publicera-modul</span><span class="sxs-lookup"><span data-stu-id="6d89f-159">Publish-Module</span></span>](Publish-Module.md)

[<span data-ttu-id="6d89f-160">Spara-modul</span><span class="sxs-lookup"><span data-stu-id="6d89f-160">Save-Module</span></span>](Save-Module.md)

[<span data-ttu-id="6d89f-161">Update-modul</span><span class="sxs-lookup"><span data-stu-id="6d89f-161">Update-Module</span></span>](Update-Module.md)

