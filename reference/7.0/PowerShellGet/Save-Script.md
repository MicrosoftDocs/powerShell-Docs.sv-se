---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/02/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/save-script?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Save-Script
ms.openlocfilehash: 72c27ddbcdce935bdad3e424ebdf834b9a82a69c
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262095"
---
# <span data-ttu-id="34c7b-103">Save-Script</span><span class="sxs-lookup"><span data-stu-id="34c7b-103">Save-Script</span></span>

## <span data-ttu-id="34c7b-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="34c7b-104">SYNOPSIS</span></span>
<span data-ttu-id="34c7b-105">Sparar ett skript.</span><span class="sxs-lookup"><span data-stu-id="34c7b-105">Saves a script.</span></span>

## <span data-ttu-id="34c7b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="34c7b-106">SYNTAX</span></span>

### <span data-ttu-id="34c7b-107">NameAndPathParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="34c7b-107">NameAndPathParameterSet (Default)</span></span>

```
Save-Script [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] [-Path] <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AllowPrerelease]
 [-AcceptLicense] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="34c7b-108">NameAndLiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="34c7b-108">NameAndLiteralPathParameterSet</span></span>

```
Save-Script [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] -LiteralPath <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AllowPrerelease]
 [-AcceptLicense] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="34c7b-109">InputObjectAndLiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="34c7b-109">InputObjectAndLiteralPathParameterSet</span></span>

```
Save-Script [-InputObject] <PSObject[]> -LiteralPath <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="34c7b-110">InputObjectAndPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="34c7b-110">InputObjectAndPathParameterSet</span></span>

```
Save-Script [-InputObject] <PSObject[]> [-Path] <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="34c7b-111">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="34c7b-111">DESCRIPTION</span></span>

<span data-ttu-id="34c7b-112">`Save-Script`Cmdlet: en sparar det angivna skriptet.</span><span class="sxs-lookup"><span data-stu-id="34c7b-112">The `Save-Script` cmdlet saves the specified script.</span></span>

## <span data-ttu-id="34c7b-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="34c7b-113">EXAMPLES</span></span>

### <span data-ttu-id="34c7b-114">Exempel 1: Spara ett skript och verifiera skriptets metadata</span><span class="sxs-lookup"><span data-stu-id="34c7b-114">Example 1: Save a script and validate the script's metadata</span></span>

<span data-ttu-id="34c7b-115">I det här exemplet sparas ett skript från en lagrings plats på den lokala datorn och skriptets metadata verifieras.</span><span class="sxs-lookup"><span data-stu-id="34c7b-115">In this example, a script from a repository is saved to the local computer and the script's metadata is validated.</span></span>

```powershell
Save-Script -Name Install-VSCode -Repository PSGallery -Path C:\Test\Scripts
Test-ScriptFileInfo -Path C:\Test\Scripts\Install-VSCode.ps1
```

```Output
Version   Name              Author      Description
-------   ----              ------      -----------
1.3       Install-VSCode    Microsoft   This script can be used to easily install Visual Studio Code
```

<span data-ttu-id="34c7b-116">`Save-Script` använder parametern **Name** för att ange skriptets namn.</span><span class="sxs-lookup"><span data-stu-id="34c7b-116">`Save-Script` uses the **Name** parameter to specify the script's name.</span></span> <span data-ttu-id="34c7b-117">Parametern **lagrings plats** anger var skriptet ska hittas.</span><span class="sxs-lookup"><span data-stu-id="34c7b-117">The **Repository** parameter specifies where to find the script.</span></span> <span data-ttu-id="34c7b-118">Skriptet sparas på den plats som anges i parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="34c7b-118">The script is saved in the location specified by the **Path** parameter.</span></span> <span data-ttu-id="34c7b-119">`Test-ScriptFileInfo` anger **sökvägen** och validerar skriptets metadata.</span><span class="sxs-lookup"><span data-stu-id="34c7b-119">`Test-ScriptFileInfo` specifies the **Path** and validates the script's metadata.</span></span>

## <span data-ttu-id="34c7b-120">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="34c7b-120">PARAMETERS</span></span>

### <span data-ttu-id="34c7b-121">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="34c7b-121">-AcceptLicense</span></span>

<span data-ttu-id="34c7b-122">Godkänn licens avtalet automatiskt om skriptet kräver det.</span><span class="sxs-lookup"><span data-stu-id="34c7b-122">Automatically accept the license agreement if the script requires it.</span></span>

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

### <span data-ttu-id="34c7b-123">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="34c7b-123">-AllowPrerelease</span></span>

<span data-ttu-id="34c7b-124">Gör att du kan spara ett skript som marker ATS som en för hands version.</span><span class="sxs-lookup"><span data-stu-id="34c7b-124">Allows you to save a script marked as a prerelease.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="34c7b-125">-Confirm</span><span class="sxs-lookup"><span data-stu-id="34c7b-125">-Confirm</span></span>

<span data-ttu-id="34c7b-126">Du uppmanas att bekräfta innan du kör `Save-Script` .</span><span class="sxs-lookup"><span data-stu-id="34c7b-126">Prompts you for confirmation before running `Save-Script`.</span></span>

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

### <span data-ttu-id="34c7b-127">-Credential</span><span class="sxs-lookup"><span data-stu-id="34c7b-127">-Credential</span></span>

<span data-ttu-id="34c7b-128">Anger ett användar konto som har behörighet att spara ett skript.</span><span class="sxs-lookup"><span data-stu-id="34c7b-128">Specifies a user account that has permission to save a script.</span></span>

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

### <span data-ttu-id="34c7b-129">-Force</span><span class="sxs-lookup"><span data-stu-id="34c7b-129">-Force</span></span>

<span data-ttu-id="34c7b-130">Tvingar `Save-Script` körning utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="34c7b-130">Forces `Save-Script` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="34c7b-131">– InputObject</span><span class="sxs-lookup"><span data-stu-id="34c7b-131">-InputObject</span></span>

<span data-ttu-id="34c7b-132">Accepterar ett **PSRepositoryItemInfo** -objekt.</span><span class="sxs-lookup"><span data-stu-id="34c7b-132">Accepts a **PSRepositoryItemInfo** object.</span></span> <span data-ttu-id="34c7b-133">Till exempel, utdata `Find-Script` till en variabel och Använd variabeln som **InputObject** -argument.</span><span class="sxs-lookup"><span data-stu-id="34c7b-133">For example, output `Find-Script` to a variable and use that variable as the **InputObject** argument.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: InputObjectAndLiteralPathParameterSet, InputObjectAndPathParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="34c7b-134">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="34c7b-134">-LiteralPath</span></span>

<span data-ttu-id="34c7b-135">Anger en sökväg till en eller flera platser.</span><span class="sxs-lookup"><span data-stu-id="34c7b-135">Specifies a path to one or more locations.</span></span> <span data-ttu-id="34c7b-136">Värdet för parametern **LiteralPath** används precis som det anges.</span><span class="sxs-lookup"><span data-stu-id="34c7b-136">The value of the **LiteralPath** parameter is used exactly as entered.</span></span> <span data-ttu-id="34c7b-137">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="34c7b-137">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="34c7b-138">Om sökvägen innehåller escape-tecken, omger du sökvägen inom enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="34c7b-138">If the path includes escape characters, enclose the path within single quotation marks.</span></span> <span data-ttu-id="34c7b-139">PowerShell tolkar inte tecken som omges av enkla citat tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="34c7b-139">PowerShell doesn't interpret any characters enclosed in single quotation marks as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: NameAndLiteralPathParameterSet, InputObjectAndLiteralPathParameterSet
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="34c7b-140">– MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="34c7b-140">-MaximumVersion</span></span>

<span data-ttu-id="34c7b-141">Anger den maximala eller senaste versionen av skriptet som ska sparas.</span><span class="sxs-lookup"><span data-stu-id="34c7b-141">Specifies the maximum, or newest version of the script to save.</span></span> <span data-ttu-id="34c7b-142">Parametrarna **MaximumVersion** och **RequiredVersion** kan inte användas i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="34c7b-142">The **MaximumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="34c7b-143">– MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="34c7b-143">-MinimumVersion</span></span>

<span data-ttu-id="34c7b-144">Anger den lägsta versionen av ett skript som ska sparas.</span><span class="sxs-lookup"><span data-stu-id="34c7b-144">Specifies the minimum version of a script to save.</span></span> <span data-ttu-id="34c7b-145">Parametrarna **MinimumVersion** och **RequiredVersion** kan inte användas i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="34c7b-145">The **MinimumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="34c7b-146">-Name</span><span class="sxs-lookup"><span data-stu-id="34c7b-146">-Name</span></span>

<span data-ttu-id="34c7b-147">Anger en matris med skript namn att spara.</span><span class="sxs-lookup"><span data-stu-id="34c7b-147">Specifies an array of script names to save.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="34c7b-148">-Path</span><span class="sxs-lookup"><span data-stu-id="34c7b-148">-Path</span></span>

<span data-ttu-id="34c7b-149">Anger platsen på den lokala datorn där en sparad modul ska lagras.</span><span class="sxs-lookup"><span data-stu-id="34c7b-149">Specifies the location on the local computer to store a saved module.</span></span> <span data-ttu-id="34c7b-150">Accepterar jokertecken.</span><span class="sxs-lookup"><span data-stu-id="34c7b-150">Accepts wildcard characters.</span></span>

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, InputObjectAndPathParameterSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="34c7b-151">-Proxy</span><span class="sxs-lookup"><span data-stu-id="34c7b-151">-Proxy</span></span>

<span data-ttu-id="34c7b-152">Anger en proxyserver för begäran, i stället för att ansluta direkt till en Internet resurs.</span><span class="sxs-lookup"><span data-stu-id="34c7b-152">Specifies a proxy server for the request, rather than connecting directly to an internet resource.</span></span>

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

### <span data-ttu-id="34c7b-153">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="34c7b-153">-ProxyCredential</span></span>

<span data-ttu-id="34c7b-154">Anger ett användar konto som har behörighet att använda den proxyserver som anges av parametern **proxy** .</span><span class="sxs-lookup"><span data-stu-id="34c7b-154">Specifies a user account that has permission to use the proxy server specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="34c7b-155">– Databas</span><span class="sxs-lookup"><span data-stu-id="34c7b-155">-Repository</span></span>

<span data-ttu-id="34c7b-156">Anger det egna namnet på en lagrings plats som har registrerats genom att köra `Register-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="34c7b-156">Specifies the friendly name of a repository that has been registered by running `Register-PSRepository`.</span></span> <span data-ttu-id="34c7b-157">Används `Get-PSRepository` för att visa registrerade databaser.</span><span class="sxs-lookup"><span data-stu-id="34c7b-157">Use `Get-PSRepository` to display registered repositories.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="34c7b-158">– RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="34c7b-158">-RequiredVersion</span></span>

<span data-ttu-id="34c7b-159">Anger det exakta versions numret för det skript som ska sparas.</span><span class="sxs-lookup"><span data-stu-id="34c7b-159">Specifies the exact version number of the script to save.</span></span>

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="34c7b-160">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="34c7b-160">-WhatIf</span></span>

<span data-ttu-id="34c7b-161">Visar vad som händer om `Save-Script` körs.</span><span class="sxs-lookup"><span data-stu-id="34c7b-161">Shows what would happen if `Save-Script` runs.</span></span> <span data-ttu-id="34c7b-162">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="34c7b-162">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="34c7b-163">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="34c7b-163">CommonParameters</span></span>

<span data-ttu-id="34c7b-164">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="34c7b-164">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="34c7b-165">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="34c7b-165">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="34c7b-166">INDATA</span><span class="sxs-lookup"><span data-stu-id="34c7b-166">INPUTS</span></span>

### <span data-ttu-id="34c7b-167">System.String[]</span><span class="sxs-lookup"><span data-stu-id="34c7b-167">System.String[]</span></span>

### <span data-ttu-id="34c7b-168">System. Management. Automation. PSObject []</span><span class="sxs-lookup"><span data-stu-id="34c7b-168">System.Management.Automation.PSObject[]</span></span>

### <span data-ttu-id="34c7b-169">System. String</span><span class="sxs-lookup"><span data-stu-id="34c7b-169">System.String</span></span>

### <span data-ttu-id="34c7b-170">System. URI</span><span class="sxs-lookup"><span data-stu-id="34c7b-170">System.Uri</span></span>

### <span data-ttu-id="34c7b-171">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="34c7b-171">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="34c7b-172">UTDATA</span><span class="sxs-lookup"><span data-stu-id="34c7b-172">OUTPUTS</span></span>

### <span data-ttu-id="34c7b-173">System. Object</span><span class="sxs-lookup"><span data-stu-id="34c7b-173">System.Object</span></span>

## <span data-ttu-id="34c7b-174">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="34c7b-174">NOTES</span></span>

## <span data-ttu-id="34c7b-175">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="34c7b-175">RELATED LINKS</span></span>

[<span data-ttu-id="34c7b-176">Sök – skript</span><span class="sxs-lookup"><span data-stu-id="34c7b-176">Find-Script</span></span>](Find-Script.md)

[<span data-ttu-id="34c7b-177">Installera – skript</span><span class="sxs-lookup"><span data-stu-id="34c7b-177">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="34c7b-178">Publicera – skript</span><span class="sxs-lookup"><span data-stu-id="34c7b-178">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="34c7b-179">Test-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="34c7b-179">Test-ScriptFileInfo</span></span>](Test-ScriptFileInfo.md)

[<span data-ttu-id="34c7b-180">Avinstallera – skript</span><span class="sxs-lookup"><span data-stu-id="34c7b-180">Uninstall-Script</span></span>](Uninstall-Script.md)

[<span data-ttu-id="34c7b-181">Uppdatera skript</span><span class="sxs-lookup"><span data-stu-id="34c7b-181">Update-Script</span></span>](Update-Script.md)