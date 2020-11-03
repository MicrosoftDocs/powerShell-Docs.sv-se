---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/09/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/update-script?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-Script
ms.openlocfilehash: 5a43e3382990209c365bb8fe5c0b320624ddfe18
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266679"
---
# <span data-ttu-id="cba46-103">Update-Script</span><span class="sxs-lookup"><span data-stu-id="cba46-103">Update-Script</span></span>

## <span data-ttu-id="cba46-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="cba46-104">SYNOPSIS</span></span>
<span data-ttu-id="cba46-105">Uppdaterar ett skript.</span><span class="sxs-lookup"><span data-stu-id="cba46-105">Updates a script.</span></span>

## <span data-ttu-id="cba46-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="cba46-106">SYNTAX</span></span>

### <span data-ttu-id="cba46-107">Alla</span><span class="sxs-lookup"><span data-stu-id="cba46-107">All</span></span>

```
Update-Script [[-Name] <String[]>] [-RequiredVersion <String>] [-MaximumVersion <String>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force]
 [-AllowPrerelease] [-AcceptLicense] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="cba46-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="cba46-108">DESCRIPTION</span></span>

<span data-ttu-id="cba46-109">`Update-Script`Cmdlet: en uppdaterar ett skript som är installerat på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="cba46-109">The `Update-Script` cmdlet updates a script that is installed on the local computer.</span></span> <span data-ttu-id="cba46-110">Det uppdaterade skriptet hämtas från samma databas som den installerade versionen.</span><span class="sxs-lookup"><span data-stu-id="cba46-110">The updated script is downloaded from the same repository as the installed version.</span></span>

## <span data-ttu-id="cba46-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="cba46-111">EXAMPLES</span></span>

### <span data-ttu-id="cba46-112">Exempel 1: uppdatera det angivna skriptet</span><span class="sxs-lookup"><span data-stu-id="cba46-112">Example 1: Update the specified script</span></span>

<span data-ttu-id="cba46-113">I det här exemplet uppdateras ett installerat skript och den uppdaterade versionen visas.</span><span class="sxs-lookup"><span data-stu-id="cba46-113">This example updates an installed script and displays the updated version.</span></span>

```powershell
Update-Script -Name UpdateManagement-Template -RequiredVersion 1.1
Get-InstalledScript -Name UpdateManagement-Template
```

```Output
Version   Name                       Repository   Description
-------   ----                       ----------   -----------
1.1       UpdateManagement-Template  PSGallery    This is a template script for Update Management...
```

<span data-ttu-id="cba46-114">`Update-Script` använder parametern **Name** för att ange det skript som ska uppdateras.</span><span class="sxs-lookup"><span data-stu-id="cba46-114">`Update-Script` uses the **Name** parameter to specify the script to update.</span></span> <span data-ttu-id="cba46-115">Parametern **RequiredVersion** anger skript versionen.</span><span class="sxs-lookup"><span data-stu-id="cba46-115">The **RequiredVersion** parameter specifies the script version.</span></span> <span data-ttu-id="cba46-116">`Get-InstalledScript` visar den uppdaterade versionen av skriptet.</span><span class="sxs-lookup"><span data-stu-id="cba46-116">`Get-InstalledScript` displays the updated version of the script.</span></span>

## <span data-ttu-id="cba46-117">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="cba46-117">PARAMETERS</span></span>

### <span data-ttu-id="cba46-118">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="cba46-118">-AcceptLicense</span></span>

<span data-ttu-id="cba46-119">Godkänn licens avtalet automatiskt under installationen om paketet kräver det.</span><span class="sxs-lookup"><span data-stu-id="cba46-119">Automatically accept the license agreement during installation if the package requires it.</span></span>

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

### <span data-ttu-id="cba46-120">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="cba46-120">-AllowPrerelease</span></span>

<span data-ttu-id="cba46-121">Gör att du kan uppdatera ett skript med det nyare skriptet markerat som en för hands version.</span><span class="sxs-lookup"><span data-stu-id="cba46-121">Allows you to update a script with the newer script marked as a prerelease.</span></span>

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

### <span data-ttu-id="cba46-122">-Confirm</span><span class="sxs-lookup"><span data-stu-id="cba46-122">-Confirm</span></span>

<span data-ttu-id="cba46-123">Du uppmanas att bekräfta innan du kör `Update-Script` .</span><span class="sxs-lookup"><span data-stu-id="cba46-123">Prompts you for confirmation before running `Update-Script`.</span></span>

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

### <span data-ttu-id="cba46-124">-Credential</span><span class="sxs-lookup"><span data-stu-id="cba46-124">-Credential</span></span>

<span data-ttu-id="cba46-125">Anger ett användar konto som har behörighet att uppdatera ett skript.</span><span class="sxs-lookup"><span data-stu-id="cba46-125">Specifies a user account that has permission to update a script.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="cba46-126">-Force</span><span class="sxs-lookup"><span data-stu-id="cba46-126">-Force</span></span>

<span data-ttu-id="cba46-127">Tvingar `Update-Script` körning utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="cba46-127">Forces `Update-Script` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="cba46-128">– MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="cba46-128">-MaximumVersion</span></span>

<span data-ttu-id="cba46-129">Anger den maximala eller nyaste versionen av skriptet som ska uppdateras.</span><span class="sxs-lookup"><span data-stu-id="cba46-129">Specifies the maximum, or newest, version of the script to update.</span></span> <span data-ttu-id="cba46-130">Parametrarna **MaximumVersion** och **RequiredVersion** kan inte användas i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="cba46-130">The **MaximumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="cba46-131">-Name</span><span class="sxs-lookup"><span data-stu-id="cba46-131">-Name</span></span>

<span data-ttu-id="cba46-132">Anger ett skript namn eller en matris med skript namn som ska uppdateras.</span><span class="sxs-lookup"><span data-stu-id="cba46-132">Specifies one script name or an array of script names to update.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="cba46-133">– PassThru</span><span class="sxs-lookup"><span data-stu-id="cba46-133">-PassThru</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cba46-134">-Proxy</span><span class="sxs-lookup"><span data-stu-id="cba46-134">-Proxy</span></span>

<span data-ttu-id="cba46-135">Anger en proxyserver för begäran i stället för att ansluta direkt till en Internet resurs.</span><span class="sxs-lookup"><span data-stu-id="cba46-135">Specifies a proxy server for the request rather than connecting directly to an internet resource.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="cba46-136">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="cba46-136">-ProxyCredential</span></span>

<span data-ttu-id="cba46-137">Anger ett användar konto som har behörighet att använda den proxyserver som anges av parametern **proxy** .</span><span class="sxs-lookup"><span data-stu-id="cba46-137">Specifies a user account that has permission to use the proxy server specified by the **Proxy** parameter.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="cba46-138">– RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="cba46-138">-RequiredVersion</span></span>

<span data-ttu-id="cba46-139">Anger det exakta versions numret för skriptet som ska uppdateras.</span><span class="sxs-lookup"><span data-stu-id="cba46-139">Specifies the exact version number of the script to update.</span></span> <span data-ttu-id="cba46-140">Parametrarna **MinimumVersion** och **RequiredVersion** kan inte användas i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="cba46-140">The **MinimumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="cba46-141">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="cba46-141">-WhatIf</span></span>

<span data-ttu-id="cba46-142">Visar vad som händer om `Update-Script` körs.</span><span class="sxs-lookup"><span data-stu-id="cba46-142">Shows what would happen if `Update-Script` runs.</span></span> <span data-ttu-id="cba46-143">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="cba46-143">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="cba46-144">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cba46-144">CommonParameters</span></span>

<span data-ttu-id="cba46-145">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="cba46-145">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cba46-146">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="cba46-146">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="cba46-147">INDATA</span><span class="sxs-lookup"><span data-stu-id="cba46-147">INPUTS</span></span>

## <span data-ttu-id="cba46-148">UTDATA</span><span class="sxs-lookup"><span data-stu-id="cba46-148">OUTPUTS</span></span>

## <span data-ttu-id="cba46-149">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="cba46-149">NOTES</span></span>

## <span data-ttu-id="cba46-150">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="cba46-150">RELATED LINKS</span></span>

[<span data-ttu-id="cba46-151">Sök – skript</span><span class="sxs-lookup"><span data-stu-id="cba46-151">Find-Script</span></span>](Find-Script.md)

[<span data-ttu-id="cba46-152">Installera – skript</span><span class="sxs-lookup"><span data-stu-id="cba46-152">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="cba46-153">Publicera – skript</span><span class="sxs-lookup"><span data-stu-id="cba46-153">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="cba46-154">Spara – skript</span><span class="sxs-lookup"><span data-stu-id="cba46-154">Save-Script</span></span>](Save-Script.md)

[<span data-ttu-id="cba46-155">Avinstallera – skript</span><span class="sxs-lookup"><span data-stu-id="cba46-155">Uninstall-Script</span></span>](Uninstall-Script.md)
