---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/02/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/save-script?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Save-Script
ms.openlocfilehash: 2f672cbb814b0641411bb11ffb17bd1ecef96dda
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94891862"
---
# <span data-ttu-id="07203-102">Save-Script</span><span class="sxs-lookup"><span data-stu-id="07203-102">Save-Script</span></span>

## <span data-ttu-id="07203-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="07203-103">SYNOPSIS</span></span>
<span data-ttu-id="07203-104">Sparar ett skript.</span><span class="sxs-lookup"><span data-stu-id="07203-104">Saves a script.</span></span>

## <span data-ttu-id="07203-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="07203-105">SYNTAX</span></span>

### <span data-ttu-id="07203-106">NameAndPathParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="07203-106">NameAndPathParameterSet (Default)</span></span>

```
Save-Script [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] [-Path] <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AllowPrerelease]
 [-AcceptLicense] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="07203-107">NameAndLiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="07203-107">NameAndLiteralPathParameterSet</span></span>

```
Save-Script [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] -LiteralPath <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AllowPrerelease]
 [-AcceptLicense] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="07203-108">InputObjectAndLiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="07203-108">InputObjectAndLiteralPathParameterSet</span></span>

```
Save-Script [-InputObject] <PSObject[]> -LiteralPath <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="07203-109">InputObjectAndPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="07203-109">InputObjectAndPathParameterSet</span></span>

```
Save-Script [-InputObject] <PSObject[]> [-Path] <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="07203-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="07203-110">DESCRIPTION</span></span>

<span data-ttu-id="07203-111">`Save-Script`Cmdlet: en sparar det angivna skriptet.</span><span class="sxs-lookup"><span data-stu-id="07203-111">The `Save-Script` cmdlet saves the specified script.</span></span>

## <span data-ttu-id="07203-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="07203-112">EXAMPLES</span></span>

### <span data-ttu-id="07203-113">Exempel 1: Spara ett skript och verifiera skriptets metadata</span><span class="sxs-lookup"><span data-stu-id="07203-113">Example 1: Save a script and validate the script's metadata</span></span>

<span data-ttu-id="07203-114">I det här exemplet sparas ett skript från en lagrings plats på den lokala datorn och skriptets metadata verifieras.</span><span class="sxs-lookup"><span data-stu-id="07203-114">In this example, a script from a repository is saved to the local computer and the script's metadata is validated.</span></span>

```powershell
Save-Script -Name Install-VSCode -Repository PSGallery -Path C:\Test\Scripts
Test-ScriptFileInfo -Path C:\Test\Scripts\Install-VSCode.ps1
```

```Output
Version   Name              Author      Description
-------   ----              ------      -----------
1.3       Install-VSCode    Microsoft   This script can be used to easily install Visual Studio Code
```

<span data-ttu-id="07203-115">`Save-Script` använder parametern **Name** för att ange skriptets namn.</span><span class="sxs-lookup"><span data-stu-id="07203-115">`Save-Script` uses the **Name** parameter to specify the script's name.</span></span> <span data-ttu-id="07203-116">Parametern **lagrings plats** anger var skriptet ska hittas.</span><span class="sxs-lookup"><span data-stu-id="07203-116">The **Repository** parameter specifies where to find the script.</span></span> <span data-ttu-id="07203-117">Skriptet sparas på den plats som anges i parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="07203-117">The script is saved in the location specified by the **Path** parameter.</span></span> <span data-ttu-id="07203-118">`Test-ScriptFileInfo` anger **sökvägen** och validerar skriptets metadata.</span><span class="sxs-lookup"><span data-stu-id="07203-118">`Test-ScriptFileInfo` specifies the **Path** and validates the script's metadata.</span></span>

## <span data-ttu-id="07203-119">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="07203-119">PARAMETERS</span></span>

### <span data-ttu-id="07203-120">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="07203-120">-AcceptLicense</span></span>

<span data-ttu-id="07203-121">Godkänn licens avtalet automatiskt om skriptet kräver det.</span><span class="sxs-lookup"><span data-stu-id="07203-121">Automatically accept the license agreement if the script requires it.</span></span>

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

### <span data-ttu-id="07203-122">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="07203-122">-AllowPrerelease</span></span>

<span data-ttu-id="07203-123">Gör att du kan spara ett skript som marker ATS som en för hands version.</span><span class="sxs-lookup"><span data-stu-id="07203-123">Allows you to save a script marked as a prerelease.</span></span>

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

### <span data-ttu-id="07203-124">-Confirm</span><span class="sxs-lookup"><span data-stu-id="07203-124">-Confirm</span></span>

<span data-ttu-id="07203-125">Du uppmanas att bekräfta innan du kör `Save-Script` .</span><span class="sxs-lookup"><span data-stu-id="07203-125">Prompts you for confirmation before running `Save-Script`.</span></span>

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

### <span data-ttu-id="07203-126">-Credential</span><span class="sxs-lookup"><span data-stu-id="07203-126">-Credential</span></span>

<span data-ttu-id="07203-127">Anger ett användar konto som har behörighet att spara ett skript.</span><span class="sxs-lookup"><span data-stu-id="07203-127">Specifies a user account that has permission to save a script.</span></span>

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

### <span data-ttu-id="07203-128">-Force</span><span class="sxs-lookup"><span data-stu-id="07203-128">-Force</span></span>

<span data-ttu-id="07203-129">Tvingar `Save-Script` körning utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="07203-129">Forces `Save-Script` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="07203-130">– InputObject</span><span class="sxs-lookup"><span data-stu-id="07203-130">-InputObject</span></span>

<span data-ttu-id="07203-131">Accepterar ett **PSRepositoryItemInfo** -objekt.</span><span class="sxs-lookup"><span data-stu-id="07203-131">Accepts a **PSRepositoryItemInfo** object.</span></span> <span data-ttu-id="07203-132">Till exempel, utdata `Find-Script` till en variabel och Använd variabeln som **InputObject** -argument.</span><span class="sxs-lookup"><span data-stu-id="07203-132">For example, output `Find-Script` to a variable and use that variable as the **InputObject** argument.</span></span>

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

### <span data-ttu-id="07203-133">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="07203-133">-LiteralPath</span></span>

<span data-ttu-id="07203-134">Anger en sökväg till en eller flera platser.</span><span class="sxs-lookup"><span data-stu-id="07203-134">Specifies a path to one or more locations.</span></span> <span data-ttu-id="07203-135">Värdet för parametern **LiteralPath** används precis som det anges.</span><span class="sxs-lookup"><span data-stu-id="07203-135">The value of the **LiteralPath** parameter is used exactly as entered.</span></span> <span data-ttu-id="07203-136">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="07203-136">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="07203-137">Om sökvägen innehåller escape-tecken, omger du sökvägen inom enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="07203-137">If the path includes escape characters, enclose the path within single quotation marks.</span></span> <span data-ttu-id="07203-138">PowerShell tolkar inte tecken som omges av enkla citat tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="07203-138">PowerShell doesn't interpret any characters enclosed in single quotation marks as escape sequences.</span></span>

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

### <span data-ttu-id="07203-139">– MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="07203-139">-MaximumVersion</span></span>

<span data-ttu-id="07203-140">Anger den maximala eller senaste versionen av skriptet som ska sparas.</span><span class="sxs-lookup"><span data-stu-id="07203-140">Specifies the maximum, or newest version of the script to save.</span></span> <span data-ttu-id="07203-141">Parametrarna **MaximumVersion** och **RequiredVersion** kan inte användas i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="07203-141">The **MaximumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="07203-142">– MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="07203-142">-MinimumVersion</span></span>

<span data-ttu-id="07203-143">Anger den lägsta versionen av ett skript som ska sparas.</span><span class="sxs-lookup"><span data-stu-id="07203-143">Specifies the minimum version of a script to save.</span></span> <span data-ttu-id="07203-144">Parametrarna **MinimumVersion** och **RequiredVersion** kan inte användas i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="07203-144">The **MinimumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="07203-145">-Name</span><span class="sxs-lookup"><span data-stu-id="07203-145">-Name</span></span>

<span data-ttu-id="07203-146">Anger en matris med skript namn att spara.</span><span class="sxs-lookup"><span data-stu-id="07203-146">Specifies an array of script names to save.</span></span>

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

### <span data-ttu-id="07203-147">-Path</span><span class="sxs-lookup"><span data-stu-id="07203-147">-Path</span></span>

<span data-ttu-id="07203-148">Anger platsen på den lokala datorn där en sparad modul ska lagras.</span><span class="sxs-lookup"><span data-stu-id="07203-148">Specifies the location on the local computer to store a saved module.</span></span> <span data-ttu-id="07203-149">Accepterar jokertecken.</span><span class="sxs-lookup"><span data-stu-id="07203-149">Accepts wildcard characters.</span></span>

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

### <span data-ttu-id="07203-150">-Proxy</span><span class="sxs-lookup"><span data-stu-id="07203-150">-Proxy</span></span>

<span data-ttu-id="07203-151">Anger en proxyserver för begäran, i stället för att ansluta direkt till en Internet resurs.</span><span class="sxs-lookup"><span data-stu-id="07203-151">Specifies a proxy server for the request, rather than connecting directly to an internet resource.</span></span>

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

### <span data-ttu-id="07203-152">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="07203-152">-ProxyCredential</span></span>

<span data-ttu-id="07203-153">Anger ett användar konto som har behörighet att använda den proxyserver som anges av parametern **proxy** .</span><span class="sxs-lookup"><span data-stu-id="07203-153">Specifies a user account that has permission to use the proxy server specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="07203-154">– Databas</span><span class="sxs-lookup"><span data-stu-id="07203-154">-Repository</span></span>

<span data-ttu-id="07203-155">Anger det egna namnet på en lagrings plats som har registrerats genom att köra `Register-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="07203-155">Specifies the friendly name of a repository that has been registered by running `Register-PSRepository`.</span></span> <span data-ttu-id="07203-156">Används `Get-PSRepository` för att visa registrerade databaser.</span><span class="sxs-lookup"><span data-stu-id="07203-156">Use `Get-PSRepository` to display registered repositories.</span></span>

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

### <span data-ttu-id="07203-157">– RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="07203-157">-RequiredVersion</span></span>

<span data-ttu-id="07203-158">Anger det exakta versions numret för det skript som ska sparas.</span><span class="sxs-lookup"><span data-stu-id="07203-158">Specifies the exact version number of the script to save.</span></span>

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

### <span data-ttu-id="07203-159">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="07203-159">-WhatIf</span></span>

<span data-ttu-id="07203-160">Visar vad som händer om `Save-Script` körs.</span><span class="sxs-lookup"><span data-stu-id="07203-160">Shows what would happen if `Save-Script` runs.</span></span> <span data-ttu-id="07203-161">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="07203-161">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="07203-162">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="07203-162">CommonParameters</span></span>

<span data-ttu-id="07203-163">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="07203-163">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="07203-164">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="07203-164">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="07203-165">INDATA</span><span class="sxs-lookup"><span data-stu-id="07203-165">INPUTS</span></span>

### <span data-ttu-id="07203-166">System.String[]</span><span class="sxs-lookup"><span data-stu-id="07203-166">System.String[]</span></span>

### <span data-ttu-id="07203-167">System. Management. Automation. PSObject []</span><span class="sxs-lookup"><span data-stu-id="07203-167">System.Management.Automation.PSObject[]</span></span>

### <span data-ttu-id="07203-168">System. String</span><span class="sxs-lookup"><span data-stu-id="07203-168">System.String</span></span>

### <span data-ttu-id="07203-169">System. URI</span><span class="sxs-lookup"><span data-stu-id="07203-169">System.Uri</span></span>

### <span data-ttu-id="07203-170">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="07203-170">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="07203-171">UTDATA</span><span class="sxs-lookup"><span data-stu-id="07203-171">OUTPUTS</span></span>

### <span data-ttu-id="07203-172">System. Object</span><span class="sxs-lookup"><span data-stu-id="07203-172">System.Object</span></span>

## <span data-ttu-id="07203-173">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="07203-173">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="07203-174">Från och med april 2020 stöder PowerShell-galleriet inte längre Transport Layer Security (TLS), version 1,0 och 1,1.</span><span class="sxs-lookup"><span data-stu-id="07203-174">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="07203-175">Om du inte använder TLS 1,2 eller senare visas ett fel meddelande när du försöker få åtkomst till PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="07203-175">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="07203-176">Använd följande kommando för att se till att du använder TLS 1,2:</span><span class="sxs-lookup"><span data-stu-id="07203-176">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="07203-177">Mer information finns i [meddelandet](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) i PowerShell-bloggen.</span><span class="sxs-lookup"><span data-stu-id="07203-177">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="07203-178">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="07203-178">RELATED LINKS</span></span>

[<span data-ttu-id="07203-179">Sök – skript</span><span class="sxs-lookup"><span data-stu-id="07203-179">Find-Script</span></span>](Find-Script.md)

[<span data-ttu-id="07203-180">Installera – skript</span><span class="sxs-lookup"><span data-stu-id="07203-180">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="07203-181">Publicera – skript</span><span class="sxs-lookup"><span data-stu-id="07203-181">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="07203-182">Test-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="07203-182">Test-ScriptFileInfo</span></span>](Test-ScriptFileInfo.md)

[<span data-ttu-id="07203-183">Avinstallera – skript</span><span class="sxs-lookup"><span data-stu-id="07203-183">Uninstall-Script</span></span>](Uninstall-Script.md)

[<span data-ttu-id="07203-184">Uppdatera skript</span><span class="sxs-lookup"><span data-stu-id="07203-184">Update-Script</span></span>](Update-Script.md)
