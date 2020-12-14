---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/01/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/new-scriptfileinfo?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-ScriptFileInfo
ms.openlocfilehash: d3e3c0ec257bd9c405accaf3051abd1ae4501f0f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710261"
---
# <span data-ttu-id="53cfb-102">New-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="53cfb-102">New-ScriptFileInfo</span></span>

## <span data-ttu-id="53cfb-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="53cfb-103">SYNOPSIS</span></span>
<span data-ttu-id="53cfb-104">Skapar en skript fil med metadata.</span><span class="sxs-lookup"><span data-stu-id="53cfb-104">Creates a script file with metadata.</span></span>

## <span data-ttu-id="53cfb-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="53cfb-105">SYNTAX</span></span>

### <span data-ttu-id="53cfb-106">Alla</span><span class="sxs-lookup"><span data-stu-id="53cfb-106">All</span></span>

```
New-ScriptFileInfo [[-Path] <String>] [-Version <String>] [-Author <String>] -Description <String>
 [-Guid <Guid>] [-CompanyName <String>] [-Copyright <String>] [-RequiredModules <Object[]>]
 [-ExternalModuleDependencies <String[]>] [-RequiredScripts <String[]>]
 [-ExternalScriptDependencies <String[]>] [-Tags <String[]>] [-ProjectUri <Uri>] [-LicenseUri <Uri>]
 [-IconUri <Uri>] [-ReleaseNotes <String[]>] [-PrivateData <String>] [-PassThru] [-Force] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="53cfb-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="53cfb-107">DESCRIPTION</span></span>

<span data-ttu-id="53cfb-108">`New-ScriptFileInfo`Cmdleten skapar en PowerShell-skriptfil, inklusive metadata om skriptet.</span><span class="sxs-lookup"><span data-stu-id="53cfb-108">The `New-ScriptFileInfo` cmdlet creates a PowerShell script file, including metadata about the script.</span></span>

<span data-ttu-id="53cfb-109">Exemplen använder ihopbuntning för att skicka parametrar till `New-ScriptFileInfo` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="53cfb-109">The examples use splatting to pass parameters to the `New-ScriptFileInfo` cmdlet.</span></span> <span data-ttu-id="53cfb-110">Mer information finns i [about_Splatting](../Microsoft.Powershell.Core/About/about_splatting.md).</span><span class="sxs-lookup"><span data-stu-id="53cfb-110">For more information, see [about_Splatting](../Microsoft.Powershell.Core/About/about_splatting.md).</span></span>

## <span data-ttu-id="53cfb-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="53cfb-111">EXAMPLES</span></span>

### <span data-ttu-id="53cfb-112">Exempel 1: skapa en skript fil och ange dess version, författare och beskrivning</span><span class="sxs-lookup"><span data-stu-id="53cfb-112">Example 1: Create a script file and specify its version, author, and description</span></span>

<span data-ttu-id="53cfb-113">I det här exemplet skapas en skript fil och dess innehåll visas i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="53cfb-113">In this example, a script file is created and its contents are displayed in the PowerShell console.</span></span>

```powershell
$Parms = @{
  Path = "C:\Test\Temp-Scriptfile.ps1"
  Version = "1.0"
  Author = "pattif@contoso.com"
  Description = "My test script file description goes here"
  }
New-ScriptFileInfo @Parms
Get-Content -Path C:\Test\Temp-Scriptfile.ps1
```

```Output
<#PSScriptInfo

.VERSION 1.0

.GUID 3bb10ee7-38c1-41b9-88ea-16899164fc19

.AUTHOR pattif@contoso.com

.COMPANYNAME

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
 My test script file description goes here

#>
Param()
```

<span data-ttu-id="53cfb-114">`New-ScriptFileInfo`Cmdleten använder ihopbuntning för att konfigurera flera parametrar för skriptet.</span><span class="sxs-lookup"><span data-stu-id="53cfb-114">The `New-ScriptFileInfo` cmdlet uses splatting to configure several parameters for the script.</span></span>
<span data-ttu-id="53cfb-115">**Sökväg** anger platsen och namnet på skriptet.</span><span class="sxs-lookup"><span data-stu-id="53cfb-115">**Path** sets the location and name of the script.</span></span> <span data-ttu-id="53cfb-116">**Version** anger skriptets versions nummer.</span><span class="sxs-lookup"><span data-stu-id="53cfb-116">**Version** specifies the script's version number.</span></span> <span data-ttu-id="53cfb-117">**Author** är e-postadressen till den person som skapade skriptet.</span><span class="sxs-lookup"><span data-stu-id="53cfb-117">**Author** is the email address of the person who created the script.</span></span> <span data-ttu-id="53cfb-118">**Beskrivningen** förklarar skriptets syfte.</span><span class="sxs-lookup"><span data-stu-id="53cfb-118">**Description** explains the script's purpose.</span></span>

<span data-ttu-id="53cfb-119">När skriptet har skapats `Get-Content` använder parametern **Path** för att hitta skriptet.</span><span class="sxs-lookup"><span data-stu-id="53cfb-119">After the script is created, `Get-Content` uses the **Path** parameter to locate the script.</span></span> <span data-ttu-id="53cfb-120">Skriptets innehåll visas i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="53cfb-120">The script's contents are displayed in the PowerShell console.</span></span>

### <span data-ttu-id="53cfb-121">Exempel 2: testa en skript fil</span><span class="sxs-lookup"><span data-stu-id="53cfb-121">Example 2: Test a script file</span></span>

<span data-ttu-id="53cfb-122">I det här exemplet testas metadata för skriptet som skapats i **exempel 1** .</span><span class="sxs-lookup"><span data-stu-id="53cfb-122">In this example, the metadata for the script created in **Example 1** is tested.</span></span>

```powershell
Test-ScriptFileInfo -Path C:\Test\Temp-Scriptfile.ps1
```

```Output
Version   Name                  Author               Description
-------   ----                  ------               -----------
1.0       Temp-Scriptfile       pattif@contoso.com   My test script file description goes here
```

<span data-ttu-id="53cfb-123">`Test-ScriptFileInfo`Cmdleten använder parametern **Path** för att ange skript filens plats.</span><span class="sxs-lookup"><span data-stu-id="53cfb-123">The `Test-ScriptFileInfo` cmdlet uses the **Path** parameter to specify the script file's location.</span></span>

### <span data-ttu-id="53cfb-124">Exempel 3: skapa en skript fil med alla metadata-egenskaper</span><span class="sxs-lookup"><span data-stu-id="53cfb-124">Example 3: Create a script file with all the metadata properties</span></span>

<span data-ttu-id="53cfb-125">I det här exemplet används ihopbuntning för att skapa en skript fil med namnet `New-ScriptFile.ps1` som innehåller alla egenskaper för metadata.</span><span class="sxs-lookup"><span data-stu-id="53cfb-125">This example uses splatting to create a script file named `New-ScriptFile.ps1` that includes all its metadata properties.</span></span> <span data-ttu-id="53cfb-126">Den **utförliga** parametern anger att utförliga utdata visas när skriptet skapas.</span><span class="sxs-lookup"><span data-stu-id="53cfb-126">The **Verbose** parameter specifies that verbose output is displayed as the script is created.</span></span>

```powershell
$Parms = @{
 Path = "C:\Test\New-ScriptFile.ps1"
 Verbose = $True
 Version = "1.0"
 Author = "pattif@contoso.com"
 Description = "My new script file test"
 CompanyName = "Contoso Corporation"
 Copyright = "2019 Contoso Corporation. All rights reserved."
 ExternalModuleDependencies = "ff","bb"
 RequiredScripts = "Start-WFContosoServer", "Stop-ContosoServerScript"
 ExternalScriptDependencies = "Stop-ContosoServerScript"
 Tags = @("Tag1", "Tag2", "Tag3")
 ProjectUri = "https://contoso.com"
 LicenseUri = "https://contoso.com/License"
 IconUri = "https://contoso.com/Icon"
 PassThru = $True
 ReleaseNotes = @("Contoso script now supports the following features:",
   "Feature 1",
   "Feature 2",
   "Feature 3",
   "Feature 4",
   "Feature 5")
 RequiredModules =
   "1",
   "2",
   "RequiredModule1",
   @{ModuleName="RequiredModule2";ModuleVersion="1.0"},
   @{ModuleName="RequiredModule3";RequiredVersion="2.0"},
   "ExternalModule1"
 }
New-ScriptFileInfo @Parms
```

```Output
VERBOSE: Performing the operation "Creating the 'C:\Test\New-ScriptFile.ps1'
  PowerShell Script file" on target "C:\Test\New-ScriptFile.ps1".

<#PSScriptInfo

.VERSION 1.0

.GUID 4fabe8c7-7862-45b1-a72e-1352a433b77d

.AUTHOR pattif@contoso.com

.COMPANYNAME Contoso Corporation

.COPYRIGHT 2019 Contoso Corporation. All rights reserved.

.TAGS Tag1 Tag2 Tag3

.LICENSEURI https://contoso.com/License

.PROJECTURI https://contoso.com/

.ICONURI https://contoso.com/Icon

.EXTERNALMODULEDEPENDENCIES ff,bb

.REQUIREDSCRIPTS Start-WFContosoServer,Stop-ContosoServerScript

.EXTERNALSCRIPTDEPENDENCIES Stop-ContosoServerScript

.RELEASENOTES
Contoso script now supports the following features:
Feature 1
Feature 2
Feature 3
Feature 4
Feature 5

.PRIVATEDATA

#>

#Requires -Module 1
#Requires -Module 2
#Requires -Module RequiredModule1
#Requires -Module @{ModuleName = 'RequiredModule2'; ModuleVersion = '1.0'}
#Requires -Module @{RequiredVersion = '2.0'; ModuleName = 'RequiredModule3'}
#Requires -Module ExternalModule1

<#

.DESCRIPTION
 My new script file test

#>
Param()
```

## <span data-ttu-id="53cfb-127">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="53cfb-127">PARAMETERS</span></span>

### <span data-ttu-id="53cfb-128">– Författare</span><span class="sxs-lookup"><span data-stu-id="53cfb-128">-Author</span></span>

<span data-ttu-id="53cfb-129">Anger skriptets författare.</span><span class="sxs-lookup"><span data-stu-id="53cfb-129">Specifies the script author.</span></span>

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

### <span data-ttu-id="53cfb-130">-Företags namn</span><span class="sxs-lookup"><span data-stu-id="53cfb-130">-CompanyName</span></span>

<span data-ttu-id="53cfb-131">Anger företaget eller leverantören som skapade skriptet.</span><span class="sxs-lookup"><span data-stu-id="53cfb-131">Specifies the company or vendor who created the script.</span></span>

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

### <span data-ttu-id="53cfb-132">-Confirm</span><span class="sxs-lookup"><span data-stu-id="53cfb-132">-Confirm</span></span>

<span data-ttu-id="53cfb-133">Du uppmanas att bekräfta innan du kör `New-ScriptFileInfo` .</span><span class="sxs-lookup"><span data-stu-id="53cfb-133">Prompts you for confirmation before running the `New-ScriptFileInfo`.</span></span>

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

### <span data-ttu-id="53cfb-134">– Copyright</span><span class="sxs-lookup"><span data-stu-id="53cfb-134">-Copyright</span></span>

<span data-ttu-id="53cfb-135">Anger en Copyright-instruktion för skriptet.</span><span class="sxs-lookup"><span data-stu-id="53cfb-135">Specifies a copyright statement for the script.</span></span>

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

### <span data-ttu-id="53cfb-136">-Beskrivning</span><span class="sxs-lookup"><span data-stu-id="53cfb-136">-Description</span></span>

<span data-ttu-id="53cfb-137">Anger en beskrivning av skriptet.</span><span class="sxs-lookup"><span data-stu-id="53cfb-137">Specifies a description for the script.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="53cfb-138">-ExternalModuleDependencies</span><span class="sxs-lookup"><span data-stu-id="53cfb-138">-ExternalModuleDependencies</span></span>

<span data-ttu-id="53cfb-139">Anger en matris med beroenden för externa moduler.</span><span class="sxs-lookup"><span data-stu-id="53cfb-139">Specifies an array of external module dependencies.</span></span>

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

### <span data-ttu-id="53cfb-140">-ExternalScriptDependencies</span><span class="sxs-lookup"><span data-stu-id="53cfb-140">-ExternalScriptDependencies</span></span>

<span data-ttu-id="53cfb-141">Anger en matris med externa skript beroenden.</span><span class="sxs-lookup"><span data-stu-id="53cfb-141">Specifies an array of external script dependencies.</span></span>

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

### <span data-ttu-id="53cfb-142">-Force</span><span class="sxs-lookup"><span data-stu-id="53cfb-142">-Force</span></span>

<span data-ttu-id="53cfb-143">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="53cfb-143">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="53cfb-144">-GUID</span><span class="sxs-lookup"><span data-stu-id="53cfb-144">-Guid</span></span>

<span data-ttu-id="53cfb-145">Anger ett unikt ID för skriptet.</span><span class="sxs-lookup"><span data-stu-id="53cfb-145">Specifies a unique ID for the script.</span></span>

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

### <span data-ttu-id="53cfb-146">– IconUri</span><span class="sxs-lookup"><span data-stu-id="53cfb-146">-IconUri</span></span>

<span data-ttu-id="53cfb-147">Anger webb adressen till en ikon för skriptet.</span><span class="sxs-lookup"><span data-stu-id="53cfb-147">Specifies the URL of an icon for the script.</span></span> <span data-ttu-id="53cfb-148">Den angivna ikonen visas på Galleri webb sidan för skriptet.</span><span class="sxs-lookup"><span data-stu-id="53cfb-148">The specified icon is displayed on the gallery web page for the script.</span></span>

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

### <span data-ttu-id="53cfb-149">-LicenseUri</span><span class="sxs-lookup"><span data-stu-id="53cfb-149">-LicenseUri</span></span>

<span data-ttu-id="53cfb-150">Anger URL: en för licens villkoren.</span><span class="sxs-lookup"><span data-stu-id="53cfb-150">Specifies the URL of licensing terms.</span></span>

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

### <span data-ttu-id="53cfb-151">– PassThru</span><span class="sxs-lookup"><span data-stu-id="53cfb-151">-PassThru</span></span>

<span data-ttu-id="53cfb-152">Returnerar ett objekt som representerar det objekt som du arbetar med.</span><span class="sxs-lookup"><span data-stu-id="53cfb-152">Returns an object that represents the item with which you're working.</span></span> <span data-ttu-id="53cfb-153">Som standard `New-ScriptFileInfo` genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="53cfb-153">By default, `New-ScriptFileInfo` doesn't generate any output.</span></span>

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

### <span data-ttu-id="53cfb-154">-Path</span><span class="sxs-lookup"><span data-stu-id="53cfb-154">-Path</span></span>

<span data-ttu-id="53cfb-155">Anger den plats där skript filen sparas.</span><span class="sxs-lookup"><span data-stu-id="53cfb-155">Specifies the location where the script file is saved.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="53cfb-156">-PrivateData</span><span class="sxs-lookup"><span data-stu-id="53cfb-156">-PrivateData</span></span>

<span data-ttu-id="53cfb-157">Anger privata data för skriptet.</span><span class="sxs-lookup"><span data-stu-id="53cfb-157">Specifies private data for the script.</span></span>

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

### <span data-ttu-id="53cfb-158">-ProjectUri</span><span class="sxs-lookup"><span data-stu-id="53cfb-158">-ProjectUri</span></span>

<span data-ttu-id="53cfb-159">Anger webb adressen till en webb sida om projektet.</span><span class="sxs-lookup"><span data-stu-id="53cfb-159">Specifies the URL of a web page about this project.</span></span>

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

### <span data-ttu-id="53cfb-160">-ReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="53cfb-160">-ReleaseNotes</span></span>

<span data-ttu-id="53cfb-161">Anger en sträng mat ris som innehåller viktig information eller kommentarer som du vill ska vara tillgängliga för användare av den här versionen av skriptet.</span><span class="sxs-lookup"><span data-stu-id="53cfb-161">Specifies a string array that contains release notes or comments that you want available to users of this version of the script.</span></span>

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

### <span data-ttu-id="53cfb-162">-RequiredModules</span><span class="sxs-lookup"><span data-stu-id="53cfb-162">-RequiredModules</span></span>

<span data-ttu-id="53cfb-163">Anger moduler som måste vara i det globala sessionstillståndet.</span><span class="sxs-lookup"><span data-stu-id="53cfb-163">Specifies modules that must be in the global session state.</span></span> <span data-ttu-id="53cfb-164">Om de moduler som krävs inte är i det globala sessionstillståndet importeras de av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="53cfb-164">If the required modules aren't in the global session state, PowerShell imports them.</span></span>

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

### <span data-ttu-id="53cfb-165">-RequiredScripts</span><span class="sxs-lookup"><span data-stu-id="53cfb-165">-RequiredScripts</span></span>

<span data-ttu-id="53cfb-166">Anger en matris med nödvändiga skript.</span><span class="sxs-lookup"><span data-stu-id="53cfb-166">Specifies an array of required scripts.</span></span>

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

### <span data-ttu-id="53cfb-167">– Taggar</span><span class="sxs-lookup"><span data-stu-id="53cfb-167">-Tags</span></span>

<span data-ttu-id="53cfb-168">Anger en matris med taggar.</span><span class="sxs-lookup"><span data-stu-id="53cfb-168">Specifies an array of tags.</span></span>

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

### <span data-ttu-id="53cfb-169">-Version</span><span class="sxs-lookup"><span data-stu-id="53cfb-169">-Version</span></span>

<span data-ttu-id="53cfb-170">Anger versionen för skriptet.</span><span class="sxs-lookup"><span data-stu-id="53cfb-170">Specifies the version of the script.</span></span>

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

### <span data-ttu-id="53cfb-171">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="53cfb-171">-WhatIf</span></span>

<span data-ttu-id="53cfb-172">Visar vad som händer om `New-ScriptFileInfo` körs.</span><span class="sxs-lookup"><span data-stu-id="53cfb-172">Shows what would happen if `New-ScriptFileInfo` runs.</span></span> <span data-ttu-id="53cfb-173">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="53cfb-173">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="53cfb-174">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="53cfb-174">CommonParameters</span></span>

<span data-ttu-id="53cfb-175">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="53cfb-175">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="53cfb-176">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="53cfb-176">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="53cfb-177">INDATA</span><span class="sxs-lookup"><span data-stu-id="53cfb-177">INPUTS</span></span>

### <span data-ttu-id="53cfb-178">System. String</span><span class="sxs-lookup"><span data-stu-id="53cfb-178">System.String</span></span>

## <span data-ttu-id="53cfb-179">UTDATA</span><span class="sxs-lookup"><span data-stu-id="53cfb-179">OUTPUTS</span></span>

### <span data-ttu-id="53cfb-180">System. Object</span><span class="sxs-lookup"><span data-stu-id="53cfb-180">System.Object</span></span>

## <span data-ttu-id="53cfb-181">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="53cfb-181">NOTES</span></span>

## <span data-ttu-id="53cfb-182">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="53cfb-182">RELATED LINKS</span></span>

[<span data-ttu-id="53cfb-183">about_Splatting</span><span class="sxs-lookup"><span data-stu-id="53cfb-183">about_Splatting</span></span>](../Microsoft.Powershell.Core/About/about_splatting.md)

[<span data-ttu-id="53cfb-184">Test-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="53cfb-184">Test-ScriptFileInfo</span></span>](Test-ScriptFileInfo.md)

[<span data-ttu-id="53cfb-185">Update-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="53cfb-185">Update-ScriptFileInfo</span></span>](Update-ScriptFileInfo.md)

