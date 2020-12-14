---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/03/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/uninstall-script?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Uninstall-Script
ms.openlocfilehash: 2cd8b51e1d4ef11a0a5f9e3542ff89e094854d8c
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710033"
---
# <span data-ttu-id="0613e-102">Uninstall-Script</span><span class="sxs-lookup"><span data-stu-id="0613e-102">Uninstall-Script</span></span>

## <span data-ttu-id="0613e-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="0613e-103">SYNOPSIS</span></span>
<span data-ttu-id="0613e-104">Avinstallerar ett skript.</span><span class="sxs-lookup"><span data-stu-id="0613e-104">Uninstalls a script.</span></span>

## <span data-ttu-id="0613e-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0613e-105">SYNTAX</span></span>

### <span data-ttu-id="0613e-106">NameParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="0613e-106">NameParameterSet (Default)</span></span>

```
Uninstall-Script [-Name] <String[]> [-MinimumVersion <String>] [-RequiredVersion <String>]
 [-MaximumVersion <String>] [-Force] [-AllowPrerelease] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="0613e-107">InputObject</span><span class="sxs-lookup"><span data-stu-id="0613e-107">InputObject</span></span>

```
Uninstall-Script [-InputObject] <PSObject[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="0613e-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="0613e-108">DESCRIPTION</span></span>

<span data-ttu-id="0613e-109">`Uninstall-Script`Cmdleten avinstallerar ett angivet skript från den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="0613e-109">The `Uninstall-Script` cmdlet uninstalls a specified script from the local computer.</span></span>

## <span data-ttu-id="0613e-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="0613e-110">EXAMPLES</span></span>

### <span data-ttu-id="0613e-111">Exempel 1: Avinstallera ett skript</span><span class="sxs-lookup"><span data-stu-id="0613e-111">Example 1: Uninstall a script</span></span>

<span data-ttu-id="0613e-112">I det här exemplet avinstalleras ett skript.</span><span class="sxs-lookup"><span data-stu-id="0613e-112">This example uninstalls a script.</span></span>

```powershell
Uninstall-Script -Name UpdateManagement-Template
```

<span data-ttu-id="0613e-113">`Uninstall-Script` använder parametern **Name** för att ange det skript som ska avinstalleras från den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="0613e-113">`Uninstall-Script` uses the **Name** parameter to specify the script to uninstall from the local computer.</span></span>

### <span data-ttu-id="0613e-114">Exempel 2: Använd pipelinen för att avinstallera ett skript</span><span class="sxs-lookup"><span data-stu-id="0613e-114">Example 2: Use the pipeline to uninstall a script</span></span>

<span data-ttu-id="0613e-115">I det här exemplet används pipelinen för att avinstallera ett skript.</span><span class="sxs-lookup"><span data-stu-id="0613e-115">In this example, the pipeline is used to uninstall a script.</span></span>

```powershell
Get-InstalledScript -Name UpdateManagement-Template | Uninstall-Script
```

<span data-ttu-id="0613e-116">`Get-InstalledScript` använder parametern **Name** för att ange skriptet.</span><span class="sxs-lookup"><span data-stu-id="0613e-116">`Get-InstalledScript` uses the **Name** parameter to specify the script.</span></span> <span data-ttu-id="0613e-117">Objektet skickas ned i pipeline till `Uninstall-Script` och skriptet avinstalleras.</span><span class="sxs-lookup"><span data-stu-id="0613e-117">The object is sent down the pipeline to `Uninstall-Script` and the script is uninstalled.</span></span>

## <span data-ttu-id="0613e-118">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="0613e-118">PARAMETERS</span></span>

### <span data-ttu-id="0613e-119">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="0613e-119">-AllowPrerelease</span></span>

<span data-ttu-id="0613e-120">Gör att du kan avinstallera ett skript som marker ATS som en för hands version.</span><span class="sxs-lookup"><span data-stu-id="0613e-120">Allows you to uninstall a script marked as a prerelease.</span></span>

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

### <span data-ttu-id="0613e-121">-Confirm</span><span class="sxs-lookup"><span data-stu-id="0613e-121">-Confirm</span></span>

<span data-ttu-id="0613e-122">Du uppmanas att bekräfta innan du kör `Uninstall-Script` .</span><span class="sxs-lookup"><span data-stu-id="0613e-122">Prompts you for confirmation before running `Uninstall-Script`.</span></span>

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

### <span data-ttu-id="0613e-123">-Force</span><span class="sxs-lookup"><span data-stu-id="0613e-123">-Force</span></span>

<span data-ttu-id="0613e-124">Tvingar `Uninstall-Script` körning utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="0613e-124">Forces `Uninstall-Script` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="0613e-125">– InputObject</span><span class="sxs-lookup"><span data-stu-id="0613e-125">-InputObject</span></span>

<span data-ttu-id="0613e-126">Accepterar ett **PSRepositoryItemInfo** -objekt.</span><span class="sxs-lookup"><span data-stu-id="0613e-126">Accepts a **PSRepositoryItemInfo** object.</span></span> <span data-ttu-id="0613e-127">Till exempel, utdata `Get-InstalledScript` till en variabel och Använd variabeln som **InputObject** -argument.</span><span class="sxs-lookup"><span data-stu-id="0613e-127">For example, output `Get-InstalledScript` to a variable and use that variable as the **InputObject** argument.</span></span>

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

### <span data-ttu-id="0613e-128">– MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="0613e-128">-MaximumVersion</span></span>

<span data-ttu-id="0613e-129">Anger den maximala eller nyaste versionen av skriptet som ska avinstalleras.</span><span class="sxs-lookup"><span data-stu-id="0613e-129">Specifies the maximum, or newest, version of the script to uninstall.</span></span> <span data-ttu-id="0613e-130">Parametrarna **MaximumVersion** och **RequiredVersion** kan inte användas i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="0613e-130">The **MaximumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="0613e-131">– MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="0613e-131">-MinimumVersion</span></span>

<span data-ttu-id="0613e-132">Anger den lägsta versionen av skriptet som ska avinstalleras.</span><span class="sxs-lookup"><span data-stu-id="0613e-132">Specifies the minimum version of the script to uninstall.</span></span> <span data-ttu-id="0613e-133">Parametrarna **MinimumVersion** och **RequiredVersion** kan inte användas i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="0613e-133">The **MinimumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="0613e-134">-Name</span><span class="sxs-lookup"><span data-stu-id="0613e-134">-Name</span></span>

<span data-ttu-id="0613e-135">Anger en matris med skript namn att avinstallera.</span><span class="sxs-lookup"><span data-stu-id="0613e-135">Specifies an array of script names to uninstall.</span></span>

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

### <span data-ttu-id="0613e-136">– RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="0613e-136">-RequiredVersion</span></span>

<span data-ttu-id="0613e-137">Anger det exakta versions numret för det skript som ska avinstalleras.</span><span class="sxs-lookup"><span data-stu-id="0613e-137">Specifies the exact version number of the script to uninstall.</span></span>

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

### <span data-ttu-id="0613e-138">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="0613e-138">-WhatIf</span></span>

<span data-ttu-id="0613e-139">Visar vad som händer om `Uninstall-Script` körs.</span><span class="sxs-lookup"><span data-stu-id="0613e-139">Shows what would happen if `Uninstall-Script` runs.</span></span> <span data-ttu-id="0613e-140">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="0613e-140">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="0613e-141">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0613e-141">CommonParameters</span></span>

<span data-ttu-id="0613e-142">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0613e-142">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0613e-143">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="0613e-143">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0613e-144">INDATA</span><span class="sxs-lookup"><span data-stu-id="0613e-144">INPUTS</span></span>

### <span data-ttu-id="0613e-145">System.String[]</span><span class="sxs-lookup"><span data-stu-id="0613e-145">System.String[]</span></span>

### <span data-ttu-id="0613e-146">System. Management. Automation. PSObject []</span><span class="sxs-lookup"><span data-stu-id="0613e-146">System.Management.Automation.PSObject[]</span></span>

### <span data-ttu-id="0613e-147">System. String</span><span class="sxs-lookup"><span data-stu-id="0613e-147">System.String</span></span>

## <span data-ttu-id="0613e-148">UTDATA</span><span class="sxs-lookup"><span data-stu-id="0613e-148">OUTPUTS</span></span>

### <span data-ttu-id="0613e-149">System. Object</span><span class="sxs-lookup"><span data-stu-id="0613e-149">System.Object</span></span>

## <span data-ttu-id="0613e-150">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="0613e-150">NOTES</span></span>

## <span data-ttu-id="0613e-151">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="0613e-151">RELATED LINKS</span></span>

[<span data-ttu-id="0613e-152">Sök – skript</span><span class="sxs-lookup"><span data-stu-id="0613e-152">Find-Script</span></span>](Find-Script.md)

[<span data-ttu-id="0613e-153">Installera – skript</span><span class="sxs-lookup"><span data-stu-id="0613e-153">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="0613e-154">Publicera – skript</span><span class="sxs-lookup"><span data-stu-id="0613e-154">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="0613e-155">Spara – skript</span><span class="sxs-lookup"><span data-stu-id="0613e-155">Save-Script</span></span>](Save-Script.md)

[<span data-ttu-id="0613e-156">Uppdatera skript</span><span class="sxs-lookup"><span data-stu-id="0613e-156">Update-Script</span></span>](Update-Script.md)

