---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/09/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/update-scriptfileinfo?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-ScriptFileInfo
ms.openlocfilehash: de138a27ed9425057406dc6120a8354b72a3b8a3
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710734"
---
# <span data-ttu-id="b218e-102">Update-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="b218e-102">Update-ScriptFileInfo</span></span>

## <span data-ttu-id="b218e-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="b218e-103">SYNOPSIS</span></span>
<span data-ttu-id="b218e-104">Uppdaterings information för ett skript.</span><span class="sxs-lookup"><span data-stu-id="b218e-104">Updates information for a script.</span></span>

## <span data-ttu-id="b218e-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b218e-105">SYNTAX</span></span>

### <span data-ttu-id="b218e-106">PathParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="b218e-106">PathParameterSet (Default)</span></span>

```
Update-ScriptFileInfo [-Path] <String> [-Version <String>] [-Author <String>] [-Guid <Guid>]
 [-Description <String>] [-CompanyName <String>] [-Copyright <String>] [-RequiredModules <Object[]>]
 [-ExternalModuleDependencies <String[]>] [-RequiredScripts <String[]>]
 [-ExternalScriptDependencies <String[]>] [-Tags <String[]>] [-ProjectUri <Uri>] [-LicenseUri <Uri>]
 [-IconUri <Uri>] [-ReleaseNotes <String[]>] [-PrivateData <String>] [-PassThru] [-Force] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b218e-107">LiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="b218e-107">LiteralPathParameterSet</span></span>

```
Update-ScriptFileInfo [-LiteralPath] <String> [-Version <String>] [-Author <String>] [-Guid <Guid>]
 [-Description <String>] [-CompanyName <String>] [-Copyright <String>] [-RequiredModules <Object[]>]
 [-ExternalModuleDependencies <String[]>] [-RequiredScripts <String[]>]
 [-ExternalScriptDependencies <String[]>] [-Tags <String[]>] [-ProjectUri <Uri>] [-LicenseUri <Uri>]
 [-IconUri <Uri>] [-ReleaseNotes <String[]>] [-PrivateData <String>] [-PassThru] [-Force] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="b218e-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="b218e-108">DESCRIPTION</span></span>

<span data-ttu-id="b218e-109">`Update-ScriptFileInfo`Cmdleten uppdaterar ett skripts egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="b218e-109">The `Update-ScriptFileInfo` cmdlet updates a script's property values.</span></span> <span data-ttu-id="b218e-110">Till exempel värden för version, författare eller beskrivning.</span><span class="sxs-lookup"><span data-stu-id="b218e-110">For example, the values for version, author, or description.</span></span>

## <span data-ttu-id="b218e-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="b218e-111">EXAMPLES</span></span>

### <span data-ttu-id="b218e-112">Exempel 1: uppdatera versionen av en skript fil</span><span class="sxs-lookup"><span data-stu-id="b218e-112">Example 1: Update the version of a script file</span></span>

<span data-ttu-id="b218e-113">I det här exemplet uppdateras en befintlig skript fil med nya egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="b218e-113">In this example, an existing script file is updated with new property values.</span></span>

<span data-ttu-id="b218e-114">Ihopbuntning används för att skicka parametrar till `Update-ScriptFileInfo` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b218e-114">Splatting is used to pass parameters to the `Update-ScriptFileInfo` cmdlet.</span></span> <span data-ttu-id="b218e-115">Mer information finns i [about_Splatting](../Microsoft.Powershell.Core/About/about_splatting.md).</span><span class="sxs-lookup"><span data-stu-id="b218e-115">For more information, see [about_Splatting](../Microsoft.Powershell.Core/About/about_splatting.md).</span></span>

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

<span data-ttu-id="b218e-116">`$Parms` lagrar parameter värden för **sökväg**, **version**, **författare**, **företags namn** och **Beskrivning**.</span><span class="sxs-lookup"><span data-stu-id="b218e-116">`$Parms` stores the parameter values for **Path**, **Version**, **Author**, **CompanyName**, and **Description**.</span></span> <span data-ttu-id="b218e-117">`Update-ScriptFileInfo` hämtar parameter värden från `@Parms` och uppdaterar skriptet.</span><span class="sxs-lookup"><span data-stu-id="b218e-117">`Update-ScriptFileInfo` gets the parameter values from `@Parms` and updates the script.</span></span> <span data-ttu-id="b218e-118">Parametern **Passthru** visar skriptets innehåll i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="b218e-118">The **PassThru** parameter displays the script's contents in the PowerShell console.</span></span>

## <span data-ttu-id="b218e-119">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="b218e-119">PARAMETERS</span></span>

### <span data-ttu-id="b218e-120">– Författare</span><span class="sxs-lookup"><span data-stu-id="b218e-120">-Author</span></span>

<span data-ttu-id="b218e-121">Anger skriptets författare.</span><span class="sxs-lookup"><span data-stu-id="b218e-121">Specifies the script author.</span></span>

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

### <span data-ttu-id="b218e-122">-Företags namn</span><span class="sxs-lookup"><span data-stu-id="b218e-122">-CompanyName</span></span>

<span data-ttu-id="b218e-123">Anger företaget eller leverantören som skapade skriptet.</span><span class="sxs-lookup"><span data-stu-id="b218e-123">Specifies the company or vendor who created the script.</span></span>

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

### <span data-ttu-id="b218e-124">-Confirm</span><span class="sxs-lookup"><span data-stu-id="b218e-124">-Confirm</span></span>

<span data-ttu-id="b218e-125">Du uppmanas att bekräfta innan du kör `Update-ScriptFileInfo` .</span><span class="sxs-lookup"><span data-stu-id="b218e-125">Prompts you for confirmation before running `Update-ScriptFileInfo`.</span></span>

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

### <span data-ttu-id="b218e-126">– Copyright</span><span class="sxs-lookup"><span data-stu-id="b218e-126">-Copyright</span></span>

<span data-ttu-id="b218e-127">Anger en Copyright-instruktion för skriptet.</span><span class="sxs-lookup"><span data-stu-id="b218e-127">Specifies a copyright statement for the script.</span></span>

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

### <span data-ttu-id="b218e-128">-Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b218e-128">-Description</span></span>

<span data-ttu-id="b218e-129">Anger en beskrivning av skriptet.</span><span class="sxs-lookup"><span data-stu-id="b218e-129">Specifies a description for the script.</span></span>

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

### <span data-ttu-id="b218e-130">-ExternalModuleDependencies</span><span class="sxs-lookup"><span data-stu-id="b218e-130">-ExternalModuleDependencies</span></span>

<span data-ttu-id="b218e-131">Anger en matris med beroenden för externa moduler.</span><span class="sxs-lookup"><span data-stu-id="b218e-131">Specifies an array of external module dependencies.</span></span>

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

### <span data-ttu-id="b218e-132">-ExternalScriptDependencies</span><span class="sxs-lookup"><span data-stu-id="b218e-132">-ExternalScriptDependencies</span></span>

<span data-ttu-id="b218e-133">Anger en matris med externa skript beroenden.</span><span class="sxs-lookup"><span data-stu-id="b218e-133">Specifies an array of external script dependencies.</span></span>

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

### <span data-ttu-id="b218e-134">-Force</span><span class="sxs-lookup"><span data-stu-id="b218e-134">-Force</span></span>

<span data-ttu-id="b218e-135">Tvingar `Update-ScriptFileInfo` körning utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="b218e-135">Forces `Update-ScriptFileInfo` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="b218e-136">-GUID</span><span class="sxs-lookup"><span data-stu-id="b218e-136">-Guid</span></span>

<span data-ttu-id="b218e-137">Anger ett unikt ID för ett skript.</span><span class="sxs-lookup"><span data-stu-id="b218e-137">Specifies a unique ID for a script.</span></span>

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

### <span data-ttu-id="b218e-138">– IconUri</span><span class="sxs-lookup"><span data-stu-id="b218e-138">-IconUri</span></span>

<span data-ttu-id="b218e-139">Anger webb adressen till en ikon för skriptet.</span><span class="sxs-lookup"><span data-stu-id="b218e-139">Specifies the URL of an icon for the script.</span></span> <span data-ttu-id="b218e-140">Den angivna ikonen visas på Galleri webb sidan för skriptet.</span><span class="sxs-lookup"><span data-stu-id="b218e-140">The specified icon is displayed on the gallery web page for the script.</span></span>

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

### <span data-ttu-id="b218e-141">-LicenseUri</span><span class="sxs-lookup"><span data-stu-id="b218e-141">-LicenseUri</span></span>

<span data-ttu-id="b218e-142">Anger URL: en för licens villkoren.</span><span class="sxs-lookup"><span data-stu-id="b218e-142">Specifies the URL of licensing terms.</span></span>

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

### <span data-ttu-id="b218e-143">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="b218e-143">-LiteralPath</span></span>

<span data-ttu-id="b218e-144">Anger en sökväg till en eller flera platser.</span><span class="sxs-lookup"><span data-stu-id="b218e-144">Specifies a path to one or more locations.</span></span> <span data-ttu-id="b218e-145">Värdet för parametern **LiteralPath** används exakt som det anges.</span><span class="sxs-lookup"><span data-stu-id="b218e-145">The **LiteralPath** parameter's value is used exactly as it's entered.</span></span> <span data-ttu-id="b218e-146">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="b218e-146">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="b218e-147">Om sökvägen innehåller escape-tecken, omger du dem med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="b218e-147">If the path includes escape characters, enclose them in single quotation marks.</span></span> <span data-ttu-id="b218e-148">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="b218e-148">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="b218e-149">– PassThru</span><span class="sxs-lookup"><span data-stu-id="b218e-149">-PassThru</span></span>

<span data-ttu-id="b218e-150">Returnerar ett objekt som representerar det objekt som du arbetar med.</span><span class="sxs-lookup"><span data-stu-id="b218e-150">Returns an object that represents the item with which you're working.</span></span> <span data-ttu-id="b218e-151">Som standard `Update-ScriptFileInfo` genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="b218e-151">By default, `Update-ScriptFileInfo` doesn't generate any output.</span></span>

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

### <span data-ttu-id="b218e-152">-Path</span><span class="sxs-lookup"><span data-stu-id="b218e-152">-Path</span></span>

<span data-ttu-id="b218e-153">Anger skript filens plats.</span><span class="sxs-lookup"><span data-stu-id="b218e-153">Specifies the script file's location.</span></span> <span data-ttu-id="b218e-154">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="b218e-154">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="b218e-155">-PrivateData</span><span class="sxs-lookup"><span data-stu-id="b218e-155">-PrivateData</span></span>

<span data-ttu-id="b218e-156">Anger det privata data för skriptet.</span><span class="sxs-lookup"><span data-stu-id="b218e-156">Specifies the private data for the script.</span></span>

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

### <span data-ttu-id="b218e-157">-ProjectUri</span><span class="sxs-lookup"><span data-stu-id="b218e-157">-ProjectUri</span></span>

<span data-ttu-id="b218e-158">Anger webb adressen till en webb sida om projektet.</span><span class="sxs-lookup"><span data-stu-id="b218e-158">Specifies the URL of a web page about this project.</span></span>

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

### <span data-ttu-id="b218e-159">-ReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="b218e-159">-ReleaseNotes</span></span>

<span data-ttu-id="b218e-160">Anger en sträng mat ris som innehåller viktig information eller kommentarer som du vill ska vara tillgängliga för den här versionen av skriptet.</span><span class="sxs-lookup"><span data-stu-id="b218e-160">Specifies a string array that contains release notes or comments that you want available for this version of the script.</span></span>

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

### <span data-ttu-id="b218e-161">-RequiredModules</span><span class="sxs-lookup"><span data-stu-id="b218e-161">-RequiredModules</span></span>

<span data-ttu-id="b218e-162">Anger moduler som måste vara i det globala sessionstillståndet.</span><span class="sxs-lookup"><span data-stu-id="b218e-162">Specifies modules that must be in the global session state.</span></span> <span data-ttu-id="b218e-163">Om de moduler som krävs inte är i det globala sessionstillståndet importeras de av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b218e-163">If the required modules aren't in the global session state, PowerShell imports them.</span></span>

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

### <span data-ttu-id="b218e-164">-RequiredScripts</span><span class="sxs-lookup"><span data-stu-id="b218e-164">-RequiredScripts</span></span>

<span data-ttu-id="b218e-165">Anger en matris med nödvändiga skript.</span><span class="sxs-lookup"><span data-stu-id="b218e-165">Specifies an array of required scripts.</span></span>

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

### <span data-ttu-id="b218e-166">– Taggar</span><span class="sxs-lookup"><span data-stu-id="b218e-166">-Tags</span></span>

<span data-ttu-id="b218e-167">Anger en matris med taggar.</span><span class="sxs-lookup"><span data-stu-id="b218e-167">Specifies an array of tags.</span></span>

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

### <span data-ttu-id="b218e-168">-Version</span><span class="sxs-lookup"><span data-stu-id="b218e-168">-Version</span></span>

<span data-ttu-id="b218e-169">Anger skriptets version.</span><span class="sxs-lookup"><span data-stu-id="b218e-169">Specifies the script's version.</span></span>

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

### <span data-ttu-id="b218e-170">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="b218e-170">-WhatIf</span></span>

<span data-ttu-id="b218e-171">Visar vad som händer om `Update-ScriptFileInfo` körs.</span><span class="sxs-lookup"><span data-stu-id="b218e-171">Shows what would happen if `Update-ScriptFileInfo` runs.</span></span> <span data-ttu-id="b218e-172">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="b218e-172">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="b218e-173">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b218e-173">CommonParameters</span></span>

<span data-ttu-id="b218e-174">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b218e-174">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b218e-175">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b218e-175">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b218e-176">INDATA</span><span class="sxs-lookup"><span data-stu-id="b218e-176">INPUTS</span></span>

### <span data-ttu-id="b218e-177">System. String</span><span class="sxs-lookup"><span data-stu-id="b218e-177">System.String</span></span>

## <span data-ttu-id="b218e-178">UTDATA</span><span class="sxs-lookup"><span data-stu-id="b218e-178">OUTPUTS</span></span>

### <span data-ttu-id="b218e-179">System. Object</span><span class="sxs-lookup"><span data-stu-id="b218e-179">System.Object</span></span>

## <span data-ttu-id="b218e-180">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="b218e-180">NOTES</span></span>

<span data-ttu-id="b218e-181">Använd `Test-ScriptFileInfo` cmdleten för att validera metadata för ett skript.</span><span class="sxs-lookup"><span data-stu-id="b218e-181">Use the `Test-ScriptFileInfo` cmdlet to validate a script's metadata.</span></span> <span data-ttu-id="b218e-182">Skript måste innehålla värden för version, GUID, beskrivning och författare.</span><span class="sxs-lookup"><span data-stu-id="b218e-182">Scripts must include values for version, GUID, description, and author.</span></span>

## <span data-ttu-id="b218e-183">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="b218e-183">RELATED LINKS</span></span>

[<span data-ttu-id="b218e-184">New-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="b218e-184">New-ScriptFileInfo</span></span>](New-ScriptFileInfo.md)

[<span data-ttu-id="b218e-185">Test-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="b218e-185">Test-ScriptFileInfo</span></span>](Test-ScriptFileInfo.md)

