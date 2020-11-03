---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/03/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/uninstall-script?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Uninstall-Script
ms.openlocfilehash: 812ff0b9ea57e2aa3ccb1f24656a94d4de9c641b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266937"
---
# <span data-ttu-id="7c50f-103">Uninstall-Script</span><span class="sxs-lookup"><span data-stu-id="7c50f-103">Uninstall-Script</span></span>

## <span data-ttu-id="7c50f-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="7c50f-104">SYNOPSIS</span></span>
<span data-ttu-id="7c50f-105">Avinstallerar ett skript.</span><span class="sxs-lookup"><span data-stu-id="7c50f-105">Uninstalls a script.</span></span>

## <span data-ttu-id="7c50f-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7c50f-106">SYNTAX</span></span>

### <span data-ttu-id="7c50f-107">NameParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="7c50f-107">NameParameterSet (Default)</span></span>

```
Uninstall-Script [-Name] <String[]> [-MinimumVersion <String>] [-RequiredVersion <String>]
 [-MaximumVersion <String>] [-Force] [-AllowPrerelease] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="7c50f-108">InputObject</span><span class="sxs-lookup"><span data-stu-id="7c50f-108">InputObject</span></span>

```
Uninstall-Script [-InputObject] <PSObject[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="7c50f-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="7c50f-109">DESCRIPTION</span></span>

<span data-ttu-id="7c50f-110">`Uninstall-Script`Cmdleten avinstallerar ett angivet skript från den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="7c50f-110">The `Uninstall-Script` cmdlet uninstalls a specified script from the local computer.</span></span>

## <span data-ttu-id="7c50f-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="7c50f-111">EXAMPLES</span></span>

### <span data-ttu-id="7c50f-112">Exempel 1: Avinstallera ett skript</span><span class="sxs-lookup"><span data-stu-id="7c50f-112">Example 1: Uninstall a script</span></span>

<span data-ttu-id="7c50f-113">I det här exemplet avinstalleras ett skript.</span><span class="sxs-lookup"><span data-stu-id="7c50f-113">This example uninstalls a script.</span></span>

```powershell
Uninstall-Script -Name UpdateManagement-Template
```

<span data-ttu-id="7c50f-114">`Uninstall-Script` använder parametern **Name** för att ange det skript som ska avinstalleras från den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="7c50f-114">`Uninstall-Script` uses the **Name** parameter to specify the script to uninstall from the local computer.</span></span>

### <span data-ttu-id="7c50f-115">Exempel 2: Använd pipelinen för att avinstallera ett skript</span><span class="sxs-lookup"><span data-stu-id="7c50f-115">Example 2: Use the pipeline to uninstall a script</span></span>

<span data-ttu-id="7c50f-116">I det här exemplet används pipelinen för att avinstallera ett skript.</span><span class="sxs-lookup"><span data-stu-id="7c50f-116">In this example, the pipeline is used to uninstall a script.</span></span>

```powershell
Get-InstalledScript -Name UpdateManagement-Template | Uninstall-Script
```

<span data-ttu-id="7c50f-117">`Get-InstalledScript` använder parametern **Name** för att ange skriptet.</span><span class="sxs-lookup"><span data-stu-id="7c50f-117">`Get-InstalledScript` uses the **Name** parameter to specify the script.</span></span> <span data-ttu-id="7c50f-118">Objektet skickas ned i pipeline till `Uninstall-Script` och skriptet avinstalleras.</span><span class="sxs-lookup"><span data-stu-id="7c50f-118">The object is sent down the pipeline to `Uninstall-Script` and the script is uninstalled.</span></span>

## <span data-ttu-id="7c50f-119">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="7c50f-119">PARAMETERS</span></span>

### <span data-ttu-id="7c50f-120">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="7c50f-120">-AllowPrerelease</span></span>

<span data-ttu-id="7c50f-121">Gör att du kan avinstallera ett skript som marker ATS som en för hands version.</span><span class="sxs-lookup"><span data-stu-id="7c50f-121">Allows you to uninstall a script marked as a prerelease.</span></span>

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

### <span data-ttu-id="7c50f-122">-Confirm</span><span class="sxs-lookup"><span data-stu-id="7c50f-122">-Confirm</span></span>

<span data-ttu-id="7c50f-123">Du uppmanas att bekräfta innan du kör `Uninstall-Script` .</span><span class="sxs-lookup"><span data-stu-id="7c50f-123">Prompts you for confirmation before running `Uninstall-Script`.</span></span>

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

### <span data-ttu-id="7c50f-124">-Force</span><span class="sxs-lookup"><span data-stu-id="7c50f-124">-Force</span></span>

<span data-ttu-id="7c50f-125">Tvingar `Uninstall-Script` körning utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="7c50f-125">Forces `Uninstall-Script` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="7c50f-126">– InputObject</span><span class="sxs-lookup"><span data-stu-id="7c50f-126">-InputObject</span></span>

<span data-ttu-id="7c50f-127">Accepterar ett **PSRepositoryItemInfo** -objekt.</span><span class="sxs-lookup"><span data-stu-id="7c50f-127">Accepts a **PSRepositoryItemInfo** object.</span></span> <span data-ttu-id="7c50f-128">Till exempel, utdata `Get-InstalledScript` till en variabel och Använd variabeln som **InputObject** -argument.</span><span class="sxs-lookup"><span data-stu-id="7c50f-128">For example, output `Get-InstalledScript` to a variable and use that variable as the **InputObject** argument.</span></span>

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

### <span data-ttu-id="7c50f-129">– MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="7c50f-129">-MaximumVersion</span></span>

<span data-ttu-id="7c50f-130">Anger den maximala eller nyaste versionen av skriptet som ska avinstalleras.</span><span class="sxs-lookup"><span data-stu-id="7c50f-130">Specifies the maximum, or newest, version of the script to uninstall.</span></span> <span data-ttu-id="7c50f-131">Parametrarna **MaximumVersion** och **RequiredVersion** kan inte användas i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="7c50f-131">The **MaximumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="7c50f-132">– MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="7c50f-132">-MinimumVersion</span></span>

<span data-ttu-id="7c50f-133">Anger den lägsta versionen av skriptet som ska avinstalleras.</span><span class="sxs-lookup"><span data-stu-id="7c50f-133">Specifies the minimum version of the script to uninstall.</span></span> <span data-ttu-id="7c50f-134">Parametrarna **MinimumVersion** och **RequiredVersion** kan inte användas i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="7c50f-134">The **MinimumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="7c50f-135">-Name</span><span class="sxs-lookup"><span data-stu-id="7c50f-135">-Name</span></span>

<span data-ttu-id="7c50f-136">Anger en matris med skript namn att avinstallera.</span><span class="sxs-lookup"><span data-stu-id="7c50f-136">Specifies an array of script names to uninstall.</span></span>

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

### <span data-ttu-id="7c50f-137">– RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="7c50f-137">-RequiredVersion</span></span>

<span data-ttu-id="7c50f-138">Anger det exakta versions numret för det skript som ska avinstalleras.</span><span class="sxs-lookup"><span data-stu-id="7c50f-138">Specifies the exact version number of the script to uninstall.</span></span>

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

### <span data-ttu-id="7c50f-139">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="7c50f-139">-WhatIf</span></span>

<span data-ttu-id="7c50f-140">Visar vad som händer om `Uninstall-Script` körs.</span><span class="sxs-lookup"><span data-stu-id="7c50f-140">Shows what would happen if `Uninstall-Script` runs.</span></span> <span data-ttu-id="7c50f-141">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="7c50f-141">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="7c50f-142">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7c50f-142">CommonParameters</span></span>

<span data-ttu-id="7c50f-143">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7c50f-143">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7c50f-144">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="7c50f-144">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7c50f-145">INDATA</span><span class="sxs-lookup"><span data-stu-id="7c50f-145">INPUTS</span></span>

### <span data-ttu-id="7c50f-146">System.String[]</span><span class="sxs-lookup"><span data-stu-id="7c50f-146">System.String[]</span></span>

### <span data-ttu-id="7c50f-147">System. Management. Automation. PSObject []</span><span class="sxs-lookup"><span data-stu-id="7c50f-147">System.Management.Automation.PSObject[]</span></span>

### <span data-ttu-id="7c50f-148">System. String</span><span class="sxs-lookup"><span data-stu-id="7c50f-148">System.String</span></span>

## <span data-ttu-id="7c50f-149">UTDATA</span><span class="sxs-lookup"><span data-stu-id="7c50f-149">OUTPUTS</span></span>

### <span data-ttu-id="7c50f-150">System. Object</span><span class="sxs-lookup"><span data-stu-id="7c50f-150">System.Object</span></span>

## <span data-ttu-id="7c50f-151">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="7c50f-151">NOTES</span></span>

## <span data-ttu-id="7c50f-152">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="7c50f-152">RELATED LINKS</span></span>

[<span data-ttu-id="7c50f-153">Sök – skript</span><span class="sxs-lookup"><span data-stu-id="7c50f-153">Find-Script</span></span>](Find-Script.md)

[<span data-ttu-id="7c50f-154">Installera – skript</span><span class="sxs-lookup"><span data-stu-id="7c50f-154">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="7c50f-155">Publicera – skript</span><span class="sxs-lookup"><span data-stu-id="7c50f-155">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="7c50f-156">Spara – skript</span><span class="sxs-lookup"><span data-stu-id="7c50f-156">Save-Script</span></span>](Save-Script.md)

[<span data-ttu-id="7c50f-157">Uppdatera skript</span><span class="sxs-lookup"><span data-stu-id="7c50f-157">Update-Script</span></span>](Update-Script.md)
