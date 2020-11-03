---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/09/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/update-scriptfileinfo?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-ScriptFileInfo
ms.openlocfilehash: bb36d5a1acc8331762513219e823bf91304b6b45
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265934"
---
# <span data-ttu-id="b5115-103">Update-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="b5115-103">Update-ScriptFileInfo</span></span>

## <span data-ttu-id="b5115-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="b5115-104">SYNOPSIS</span></span>
<span data-ttu-id="b5115-105">Uppdaterings information för ett skript.</span><span class="sxs-lookup"><span data-stu-id="b5115-105">Updates information for a script.</span></span>

## <span data-ttu-id="b5115-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b5115-106">SYNTAX</span></span>

### <span data-ttu-id="b5115-107">PathParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="b5115-107">PathParameterSet (Default)</span></span>

```
Update-ScriptFileInfo [-Path] <String> [-Version <String>] [-Author <String>] [-Guid <Guid>]
 [-Description <String>] [-CompanyName <String>] [-Copyright <String>] [-RequiredModules <Object[]>]
 [-ExternalModuleDependencies <String[]>] [-RequiredScripts <String[]>]
 [-ExternalScriptDependencies <String[]>] [-Tags <String[]>] [-ProjectUri <Uri>] [-LicenseUri <Uri>]
 [-IconUri <Uri>] [-ReleaseNotes <String[]>] [-PrivateData <String>] [-PassThru] [-Force] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b5115-108">LiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="b5115-108">LiteralPathParameterSet</span></span>

```
Update-ScriptFileInfo [-LiteralPath] <String> [-Version <String>] [-Author <String>] [-Guid <Guid>]
 [-Description <String>] [-CompanyName <String>] [-Copyright <String>] [-RequiredModules <Object[]>]
 [-ExternalModuleDependencies <String[]>] [-RequiredScripts <String[]>]
 [-ExternalScriptDependencies <String[]>] [-Tags <String[]>] [-ProjectUri <Uri>] [-LicenseUri <Uri>]
 [-IconUri <Uri>] [-ReleaseNotes <String[]>] [-PrivateData <String>] [-PassThru] [-Force] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="b5115-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="b5115-109">DESCRIPTION</span></span>

<span data-ttu-id="b5115-110">`Update-ScriptFileInfo`Cmdleten uppdaterar ett skripts egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="b5115-110">The `Update-ScriptFileInfo` cmdlet updates a script's property values.</span></span> <span data-ttu-id="b5115-111">Till exempel värden för version, författare eller beskrivning.</span><span class="sxs-lookup"><span data-stu-id="b5115-111">For example, the values for version, author, or description.</span></span>

## <span data-ttu-id="b5115-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="b5115-112">EXAMPLES</span></span>

### <span data-ttu-id="b5115-113">Exempel 1: uppdatera versionen av en skript fil</span><span class="sxs-lookup"><span data-stu-id="b5115-113">Example 1: Update the version of a script file</span></span>

<span data-ttu-id="b5115-114">I det här exemplet uppdateras en befintlig skript fil med nya egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="b5115-114">In this example, an existing script file is updated with new property values.</span></span>

<span data-ttu-id="b5115-115">Ihopbuntning används för att skicka parametrar till `Update-ScriptFileInfo` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b5115-115">Splatting is used to pass parameters to the `Update-ScriptFileInfo` cmdlet.</span></span> <span data-ttu-id="b5115-116">Mer information finns i [about_Splatting](../Microsoft.Powershell.Core/About/about_splatting.md).</span><span class="sxs-lookup"><span data-stu-id="b5115-116">For more information, see [about_Splatting](../Microsoft.Powershell.Core/About/about_splatting.md).</span></span>

```powershell
$Parms = @{
  Path = "C:\Test\Temp-Scriptfile.ps1"
  Version = "2.0"
  Author = "bob@contoso.com"
  CompanyName = "Contoso"
  Description = "This is the updated description"
  }
Update-ScriptFileInfo @Parms -PassThru
```

```Output
<#PSScriptInfo

.VERSION 2.0

.GUID 4609f00c-e850-4d3f-9c69-3741e56e4133

.AUTHOR bob@contoso.com

.COMPANYNAME Contoso

.COPYRIGHT

.TAGS

.LICENSEURI

.PROJECTURI

.ICONURI

.EXTERNALMODULEDEPENDENCIES

.REQUIREDSCRIPTS

.EXTERNALSCRIPTDEPENDENCIES

.RELEASENOTES

.PRIVATEDATA

#>

<#

.DESCRIPTION
This is the updated description

#>
Param()
```

<span data-ttu-id="b5115-117">`$Parms` lagrar parameter värden för **sökväg** , **version** , **författare** , **företags namn** och **Beskrivning**.</span><span class="sxs-lookup"><span data-stu-id="b5115-117">`$Parms` stores the parameter values for **Path** , **Version** , **Author** , **CompanyName** , and **Description**.</span></span> <span data-ttu-id="b5115-118">`Update-ScriptFileInfo` hämtar parameter värden från `@Parms` och uppdaterar skriptet.</span><span class="sxs-lookup"><span data-stu-id="b5115-118">`Update-ScriptFileInfo` gets the parameter values from `@Parms` and updates the script.</span></span> <span data-ttu-id="b5115-119">Parametern **Passthru** visar skriptets innehåll i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="b5115-119">The **PassThru** parameter displays the script's contents in the PowerShell console.</span></span>

## <span data-ttu-id="b5115-120">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="b5115-120">PARAMETERS</span></span>

### <span data-ttu-id="b5115-121">– Författare</span><span class="sxs-lookup"><span data-stu-id="b5115-121">-Author</span></span>

<span data-ttu-id="b5115-122">Anger skriptets författare.</span><span class="sxs-lookup"><span data-stu-id="b5115-122">Specifies the script author.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b5115-123">-Företags namn</span><span class="sxs-lookup"><span data-stu-id="b5115-123">-CompanyName</span></span>

<span data-ttu-id="b5115-124">Anger företaget eller leverantören som skapade skriptet.</span><span class="sxs-lookup"><span data-stu-id="b5115-124">Specifies the company or vendor who created the script.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b5115-125">-Confirm</span><span class="sxs-lookup"><span data-stu-id="b5115-125">-Confirm</span></span>

<span data-ttu-id="b5115-126">Du uppmanas att bekräfta innan du kör `Update-ScriptFileInfo` .</span><span class="sxs-lookup"><span data-stu-id="b5115-126">Prompts you for confirmation before running `Update-ScriptFileInfo`.</span></span>

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

### <span data-ttu-id="b5115-127">– Copyright</span><span class="sxs-lookup"><span data-stu-id="b5115-127">-Copyright</span></span>

<span data-ttu-id="b5115-128">Anger en Copyright-instruktion för skriptet.</span><span class="sxs-lookup"><span data-stu-id="b5115-128">Specifies a copyright statement for the script.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b5115-129">-Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b5115-129">-Description</span></span>

<span data-ttu-id="b5115-130">Anger en beskrivning av skriptet.</span><span class="sxs-lookup"><span data-stu-id="b5115-130">Specifies a description for the script.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b5115-131">-ExternalModuleDependencies</span><span class="sxs-lookup"><span data-stu-id="b5115-131">-ExternalModuleDependencies</span></span>

<span data-ttu-id="b5115-132">Anger en matris med beroenden för externa moduler.</span><span class="sxs-lookup"><span data-stu-id="b5115-132">Specifies an array of external module dependencies.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b5115-133">-ExternalScriptDependencies</span><span class="sxs-lookup"><span data-stu-id="b5115-133">-ExternalScriptDependencies</span></span>

<span data-ttu-id="b5115-134">Anger en matris med externa skript beroenden.</span><span class="sxs-lookup"><span data-stu-id="b5115-134">Specifies an array of external script dependencies.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b5115-135">-Force</span><span class="sxs-lookup"><span data-stu-id="b5115-135">-Force</span></span>

<span data-ttu-id="b5115-136">Tvingar `Update-ScriptFileInfo` körning utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="b5115-136">Forces `Update-ScriptFileInfo` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="b5115-137">-GUID</span><span class="sxs-lookup"><span data-stu-id="b5115-137">-Guid</span></span>

<span data-ttu-id="b5115-138">Anger ett unikt ID för ett skript.</span><span class="sxs-lookup"><span data-stu-id="b5115-138">Specifies a unique ID for a script.</span></span>

```yaml
Type: System.Guid
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b5115-139">– IconUri</span><span class="sxs-lookup"><span data-stu-id="b5115-139">-IconUri</span></span>

<span data-ttu-id="b5115-140">Anger webb adressen till en ikon för skriptet.</span><span class="sxs-lookup"><span data-stu-id="b5115-140">Specifies the URL of an icon for the script.</span></span> <span data-ttu-id="b5115-141">Den angivna ikonen visas på Galleri webb sidan för skriptet.</span><span class="sxs-lookup"><span data-stu-id="b5115-141">The specified icon is displayed on the gallery web page for the script.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b5115-142">-LicenseUri</span><span class="sxs-lookup"><span data-stu-id="b5115-142">-LicenseUri</span></span>

<span data-ttu-id="b5115-143">Anger URL: en för licens villkoren.</span><span class="sxs-lookup"><span data-stu-id="b5115-143">Specifies the URL of licensing terms.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b5115-144">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="b5115-144">-LiteralPath</span></span>

<span data-ttu-id="b5115-145">Anger en sökväg till en eller flera platser.</span><span class="sxs-lookup"><span data-stu-id="b5115-145">Specifies a path to one or more locations.</span></span> <span data-ttu-id="b5115-146">Värdet för parametern **LiteralPath** används exakt som det anges.</span><span class="sxs-lookup"><span data-stu-id="b5115-146">The **LiteralPath** parameter's value is used exactly as it's entered.</span></span> <span data-ttu-id="b5115-147">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="b5115-147">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="b5115-148">Om sökvägen innehåller escape-tecken, omger du dem med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="b5115-148">If the path includes escape characters, enclose them in single quotation marks.</span></span> <span data-ttu-id="b5115-149">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="b5115-149">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: LiteralPathParameterSet
Aliases: PSPath

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b5115-150">– PassThru</span><span class="sxs-lookup"><span data-stu-id="b5115-150">-PassThru</span></span>

<span data-ttu-id="b5115-151">Returnerar ett objekt som representerar det objekt som du arbetar med.</span><span class="sxs-lookup"><span data-stu-id="b5115-151">Returns an object that represents the item with which you're working.</span></span> <span data-ttu-id="b5115-152">Som standard `Update-ScriptFileInfo` genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="b5115-152">By default, `Update-ScriptFileInfo` doesn't generate any output.</span></span>

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

### <span data-ttu-id="b5115-153">-Path</span><span class="sxs-lookup"><span data-stu-id="b5115-153">-Path</span></span>

<span data-ttu-id="b5115-154">Anger skript filens plats.</span><span class="sxs-lookup"><span data-stu-id="b5115-154">Specifies the script file's location.</span></span> <span data-ttu-id="b5115-155">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="b5115-155">Wildcards are permitted.</span></span>

```yaml
Type: System.String
Parameter Sets: PathParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="b5115-156">-PrivateData</span><span class="sxs-lookup"><span data-stu-id="b5115-156">-PrivateData</span></span>

<span data-ttu-id="b5115-157">Anger det privata data för skriptet.</span><span class="sxs-lookup"><span data-stu-id="b5115-157">Specifies the private data for the script.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b5115-158">-ProjectUri</span><span class="sxs-lookup"><span data-stu-id="b5115-158">-ProjectUri</span></span>

<span data-ttu-id="b5115-159">Anger webb adressen till en webb sida om projektet.</span><span class="sxs-lookup"><span data-stu-id="b5115-159">Specifies the URL of a web page about this project.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b5115-160">-ReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="b5115-160">-ReleaseNotes</span></span>

<span data-ttu-id="b5115-161">Anger en sträng mat ris som innehåller viktig information eller kommentarer som du vill ska vara tillgängliga för den här versionen av skriptet.</span><span class="sxs-lookup"><span data-stu-id="b5115-161">Specifies a string array that contains release notes or comments that you want available for this version of the script.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b5115-162">-RequiredModules</span><span class="sxs-lookup"><span data-stu-id="b5115-162">-RequiredModules</span></span>

<span data-ttu-id="b5115-163">Anger moduler som måste vara i det globala sessionstillståndet.</span><span class="sxs-lookup"><span data-stu-id="b5115-163">Specifies modules that must be in the global session state.</span></span> <span data-ttu-id="b5115-164">Om de moduler som krävs inte är i det globala sessionstillståndet importeras de av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b5115-164">If the required modules aren't in the global session state, PowerShell imports them.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b5115-165">-RequiredScripts</span><span class="sxs-lookup"><span data-stu-id="b5115-165">-RequiredScripts</span></span>

<span data-ttu-id="b5115-166">Anger en matris med nödvändiga skript.</span><span class="sxs-lookup"><span data-stu-id="b5115-166">Specifies an array of required scripts.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b5115-167">– Taggar</span><span class="sxs-lookup"><span data-stu-id="b5115-167">-Tags</span></span>

<span data-ttu-id="b5115-168">Anger en matris med taggar.</span><span class="sxs-lookup"><span data-stu-id="b5115-168">Specifies an array of tags.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b5115-169">-Version</span><span class="sxs-lookup"><span data-stu-id="b5115-169">-Version</span></span>

<span data-ttu-id="b5115-170">Anger skriptets version.</span><span class="sxs-lookup"><span data-stu-id="b5115-170">Specifies the script's version.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b5115-171">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="b5115-171">-WhatIf</span></span>

<span data-ttu-id="b5115-172">Visar vad som händer om `Update-ScriptFileInfo` körs.</span><span class="sxs-lookup"><span data-stu-id="b5115-172">Shows what would happen if `Update-ScriptFileInfo` runs.</span></span> <span data-ttu-id="b5115-173">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="b5115-173">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="b5115-174">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b5115-174">CommonParameters</span></span>

<span data-ttu-id="b5115-175">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b5115-175">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b5115-176">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b5115-176">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b5115-177">INDATA</span><span class="sxs-lookup"><span data-stu-id="b5115-177">INPUTS</span></span>

## <span data-ttu-id="b5115-178">UTDATA</span><span class="sxs-lookup"><span data-stu-id="b5115-178">OUTPUTS</span></span>

## <span data-ttu-id="b5115-179">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="b5115-179">NOTES</span></span>

<span data-ttu-id="b5115-180">Använd `Test-ScriptFileInfo` cmdleten för att validera metadata för ett skript.</span><span class="sxs-lookup"><span data-stu-id="b5115-180">Use the `Test-ScriptFileInfo` cmdlet to validate a script's metadata.</span></span> <span data-ttu-id="b5115-181">Skript måste innehålla värden för version, GUID, beskrivning och författare.</span><span class="sxs-lookup"><span data-stu-id="b5115-181">Scripts must include values for version, GUID, description, and author.</span></span>

## <span data-ttu-id="b5115-182">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="b5115-182">RELATED LINKS</span></span>

[<span data-ttu-id="b5115-183">New-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="b5115-183">New-ScriptFileInfo</span></span>](New-ScriptFileInfo.md)

[<span data-ttu-id="b5115-184">Test-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="b5115-184">Test-ScriptFileInfo</span></span>](Test-ScriptFileInfo.md)
