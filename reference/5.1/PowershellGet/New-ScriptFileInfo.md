---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/01/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/new-scriptfileinfo?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-ScriptFileInfo
ms.openlocfilehash: 551fe34d266cb9330e4f30e823972458255c7f49
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265989"
---
# <span data-ttu-id="52431-103">New-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="52431-103">New-ScriptFileInfo</span></span>

## <span data-ttu-id="52431-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="52431-104">SYNOPSIS</span></span>
<span data-ttu-id="52431-105">Skapar en skript fil med metadata.</span><span class="sxs-lookup"><span data-stu-id="52431-105">Creates a script file with metadata.</span></span>

## <span data-ttu-id="52431-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="52431-106">SYNTAX</span></span>

### <span data-ttu-id="52431-107">Alla</span><span class="sxs-lookup"><span data-stu-id="52431-107">All</span></span>

```
New-ScriptFileInfo [[-Path] <String>] [-Version <String>] [-Author <String>] -Description <String>
 [-Guid <Guid>] [-CompanyName <String>] [-Copyright <String>] [-RequiredModules <Object[]>]
 [-ExternalModuleDependencies <String[]>] [-RequiredScripts <String[]>]
 [-ExternalScriptDependencies <String[]>] [-Tags <String[]>] [-ProjectUri <Uri>] [-LicenseUri <Uri>]
 [-IconUri <Uri>] [-ReleaseNotes <String[]>] [-PrivateData <String>] [-PassThru] [-Force]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="52431-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="52431-108">DESCRIPTION</span></span>

<span data-ttu-id="52431-109">`New-ScriptFileInfo`Cmdleten skapar en PowerShell-skriptfil, inklusive metadata om skriptet.</span><span class="sxs-lookup"><span data-stu-id="52431-109">The `New-ScriptFileInfo` cmdlet creates a PowerShell script file, including metadata about the script.</span></span>

<span data-ttu-id="52431-110">Exemplen använder ihopbuntning för att skicka parametrar till `New-ScriptFileInfo` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="52431-110">The examples use splatting to pass parameters to the `New-ScriptFileInfo` cmdlet.</span></span> <span data-ttu-id="52431-111">Mer information finns i [about_Splatting](../Microsoft.Powershell.Core/About/about_splatting.md).</span><span class="sxs-lookup"><span data-stu-id="52431-111">For more information, see [about_Splatting](../Microsoft.Powershell.Core/About/about_splatting.md).</span></span>

## <span data-ttu-id="52431-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="52431-112">EXAMPLES</span></span>

### <span data-ttu-id="52431-113">Exempel 1: skapa en skript fil och ange dess version, författare och beskrivning</span><span class="sxs-lookup"><span data-stu-id="52431-113">Example 1: Create a script file and specify its version, author, and description</span></span>

<span data-ttu-id="52431-114">I det här exemplet skapas en skript fil och dess innehåll visas i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="52431-114">In this example, a script file is created and its contents are displayed in the PowerShell console.</span></span>

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

<span data-ttu-id="52431-115">`New-ScriptFileInfo`Cmdleten använder ihopbuntning för att konfigurera flera parametrar för skriptet.</span><span class="sxs-lookup"><span data-stu-id="52431-115">The `New-ScriptFileInfo` cmdlet uses splatting to configure several parameters for the script.</span></span>
<span data-ttu-id="52431-116">**Sökväg** anger platsen och namnet på skriptet.</span><span class="sxs-lookup"><span data-stu-id="52431-116">**Path** sets the location and name of the script.</span></span> <span data-ttu-id="52431-117">**Version** anger skriptets versions nummer.</span><span class="sxs-lookup"><span data-stu-id="52431-117">**Version** specifies the script's version number.</span></span> <span data-ttu-id="52431-118">**Author** är e-postadressen till den person som skapade skriptet.</span><span class="sxs-lookup"><span data-stu-id="52431-118">**Author** is the email address of the person who created the script.</span></span> <span data-ttu-id="52431-119">**Beskrivningen** förklarar skriptets syfte.</span><span class="sxs-lookup"><span data-stu-id="52431-119">**Description** explains the script's purpose.</span></span>

<span data-ttu-id="52431-120">När skriptet har skapats `Get-Content` använder parametern **Path** för att hitta skriptet.</span><span class="sxs-lookup"><span data-stu-id="52431-120">After the script is created, `Get-Content` uses the **Path** parameter to locate the script.</span></span> <span data-ttu-id="52431-121">Skriptets innehåll visas i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="52431-121">The script's contents are displayed in the PowerShell console.</span></span>

### <span data-ttu-id="52431-122">Exempel 2: testa en skript fil</span><span class="sxs-lookup"><span data-stu-id="52431-122">Example 2: Test a script file</span></span>

<span data-ttu-id="52431-123">I det här exemplet testas metadata för skriptet som skapats i **exempel 1** .</span><span class="sxs-lookup"><span data-stu-id="52431-123">In this example, the metadata for the script created in **Example 1** is tested.</span></span>

```powershell
Test-ScriptFileInfo -Path C:\Test\Temp-Scriptfile.ps1
```

```Output
Version   Name                  Author               Description
-------   ----                  ------               -----------
1.0       Temp-Scriptfile       pattif@contoso.com   My test script file description goes here
```

<span data-ttu-id="52431-124">`Test-ScriptFileInfo`Cmdleten använder parametern **Path** för att ange skript filens plats.</span><span class="sxs-lookup"><span data-stu-id="52431-124">The `Test-ScriptFileInfo` cmdlet uses the **Path** parameter to specify the script file's location.</span></span>

### <span data-ttu-id="52431-125">Exempel 3: skapa en skript fil med alla metadata-egenskaper</span><span class="sxs-lookup"><span data-stu-id="52431-125">Example 3: Create a script file with all the metadata properties</span></span>

<span data-ttu-id="52431-126">I det här exemplet används ihopbuntning för att skapa en skript fil med namnet `New-ScriptFile.ps1` som innehåller alla egenskaper för metadata.</span><span class="sxs-lookup"><span data-stu-id="52431-126">This example uses splatting to create a script file named `New-ScriptFile.ps1` that includes all its metadata properties.</span></span> <span data-ttu-id="52431-127">Den **utförliga** parametern anger att utförliga utdata visas när skriptet skapas.</span><span class="sxs-lookup"><span data-stu-id="52431-127">The **Verbose** parameter specifies that verbose output is displayed as the script is created.</span></span>

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

## <span data-ttu-id="52431-128">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="52431-128">PARAMETERS</span></span>

### <span data-ttu-id="52431-129">– Författare</span><span class="sxs-lookup"><span data-stu-id="52431-129">-Author</span></span>

<span data-ttu-id="52431-130">Anger skriptets författare.</span><span class="sxs-lookup"><span data-stu-id="52431-130">Specifies the script author.</span></span>

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

### <span data-ttu-id="52431-131">-Företags namn</span><span class="sxs-lookup"><span data-stu-id="52431-131">-CompanyName</span></span>

<span data-ttu-id="52431-132">Anger företaget eller leverantören som skapade skriptet.</span><span class="sxs-lookup"><span data-stu-id="52431-132">Specifies the company or vendor who created the script.</span></span>

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

### <span data-ttu-id="52431-133">-Confirm</span><span class="sxs-lookup"><span data-stu-id="52431-133">-Confirm</span></span>

<span data-ttu-id="52431-134">Du uppmanas att bekräfta innan du kör `New-ScriptFileInfo` .</span><span class="sxs-lookup"><span data-stu-id="52431-134">Prompts you for confirmation before running the `New-ScriptFileInfo`.</span></span>

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

### <span data-ttu-id="52431-135">– Copyright</span><span class="sxs-lookup"><span data-stu-id="52431-135">-Copyright</span></span>

<span data-ttu-id="52431-136">Anger en Copyright-instruktion för skriptet.</span><span class="sxs-lookup"><span data-stu-id="52431-136">Specifies a copyright statement for the script.</span></span>

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

### <span data-ttu-id="52431-137">-Beskrivning</span><span class="sxs-lookup"><span data-stu-id="52431-137">-Description</span></span>

<span data-ttu-id="52431-138">Anger en beskrivning av skriptet.</span><span class="sxs-lookup"><span data-stu-id="52431-138">Specifies a description for the script.</span></span>

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

### <span data-ttu-id="52431-139">-ExternalModuleDependencies</span><span class="sxs-lookup"><span data-stu-id="52431-139">-ExternalModuleDependencies</span></span>

<span data-ttu-id="52431-140">Anger en matris med beroenden för externa moduler.</span><span class="sxs-lookup"><span data-stu-id="52431-140">Specifies an array of external module dependencies.</span></span>

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

### <span data-ttu-id="52431-141">-ExternalScriptDependencies</span><span class="sxs-lookup"><span data-stu-id="52431-141">-ExternalScriptDependencies</span></span>

<span data-ttu-id="52431-142">Anger en matris med externa skript beroenden.</span><span class="sxs-lookup"><span data-stu-id="52431-142">Specifies an array of external script dependencies.</span></span>

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

### <span data-ttu-id="52431-143">-Force</span><span class="sxs-lookup"><span data-stu-id="52431-143">-Force</span></span>

<span data-ttu-id="52431-144">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="52431-144">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="52431-145">-GUID</span><span class="sxs-lookup"><span data-stu-id="52431-145">-Guid</span></span>

<span data-ttu-id="52431-146">Anger ett unikt ID för skriptet.</span><span class="sxs-lookup"><span data-stu-id="52431-146">Specifies a unique ID for the script.</span></span>

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

### <span data-ttu-id="52431-147">– IconUri</span><span class="sxs-lookup"><span data-stu-id="52431-147">-IconUri</span></span>

<span data-ttu-id="52431-148">Anger webb adressen till en ikon för skriptet.</span><span class="sxs-lookup"><span data-stu-id="52431-148">Specifies the URL of an icon for the script.</span></span> <span data-ttu-id="52431-149">Den angivna ikonen visas på Galleri webb sidan för skriptet.</span><span class="sxs-lookup"><span data-stu-id="52431-149">The specified icon is displayed on the gallery web page for the script.</span></span>

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

### <span data-ttu-id="52431-150">-LicenseUri</span><span class="sxs-lookup"><span data-stu-id="52431-150">-LicenseUri</span></span>

<span data-ttu-id="52431-151">Anger URL: en för licens villkoren.</span><span class="sxs-lookup"><span data-stu-id="52431-151">Specifies the URL of licensing terms.</span></span>

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

### <span data-ttu-id="52431-152">– PassThru</span><span class="sxs-lookup"><span data-stu-id="52431-152">-PassThru</span></span>

<span data-ttu-id="52431-153">Returnerar ett objekt som representerar det objekt som du arbetar med.</span><span class="sxs-lookup"><span data-stu-id="52431-153">Returns an object that represents the item with which you're working.</span></span> <span data-ttu-id="52431-154">Som standard `New-ScriptFileInfo` genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="52431-154">By default, `New-ScriptFileInfo` doesn't generate any output.</span></span>

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

### <span data-ttu-id="52431-155">-Path</span><span class="sxs-lookup"><span data-stu-id="52431-155">-Path</span></span>

<span data-ttu-id="52431-156">Anger den plats där skript filen sparas.</span><span class="sxs-lookup"><span data-stu-id="52431-156">Specifies the location where the script file is saved.</span></span>

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

### <span data-ttu-id="52431-157">-PrivateData</span><span class="sxs-lookup"><span data-stu-id="52431-157">-PrivateData</span></span>

<span data-ttu-id="52431-158">Anger privata data för skriptet.</span><span class="sxs-lookup"><span data-stu-id="52431-158">Specifies private data for the script.</span></span>

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

### <span data-ttu-id="52431-159">-ProjectUri</span><span class="sxs-lookup"><span data-stu-id="52431-159">-ProjectUri</span></span>

<span data-ttu-id="52431-160">Anger webb adressen till en webb sida om projektet.</span><span class="sxs-lookup"><span data-stu-id="52431-160">Specifies the URL of a web page about this project.</span></span>

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

### <span data-ttu-id="52431-161">-ReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="52431-161">-ReleaseNotes</span></span>

<span data-ttu-id="52431-162">Anger en sträng mat ris som innehåller viktig information eller kommentarer som du vill ska vara tillgängliga för användare av den här versionen av skriptet.</span><span class="sxs-lookup"><span data-stu-id="52431-162">Specifies a string array that contains release notes or comments that you want available to users of this version of the script.</span></span>

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

### <span data-ttu-id="52431-163">-RequiredModules</span><span class="sxs-lookup"><span data-stu-id="52431-163">-RequiredModules</span></span>

<span data-ttu-id="52431-164">Anger moduler som måste vara i det globala sessionstillståndet.</span><span class="sxs-lookup"><span data-stu-id="52431-164">Specifies modules that must be in the global session state.</span></span> <span data-ttu-id="52431-165">Om de moduler som krävs inte är i det globala sessionstillståndet importeras de av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="52431-165">If the required modules aren't in the global session state, PowerShell imports them.</span></span>

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

### <span data-ttu-id="52431-166">-RequiredScripts</span><span class="sxs-lookup"><span data-stu-id="52431-166">-RequiredScripts</span></span>

<span data-ttu-id="52431-167">Anger en matris med nödvändiga skript.</span><span class="sxs-lookup"><span data-stu-id="52431-167">Specifies an array of required scripts.</span></span>

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

### <span data-ttu-id="52431-168">– Taggar</span><span class="sxs-lookup"><span data-stu-id="52431-168">-Tags</span></span>

<span data-ttu-id="52431-169">Anger en matris med taggar.</span><span class="sxs-lookup"><span data-stu-id="52431-169">Specifies an array of tags.</span></span>

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

### <span data-ttu-id="52431-170">-Version</span><span class="sxs-lookup"><span data-stu-id="52431-170">-Version</span></span>

<span data-ttu-id="52431-171">Anger versionen för skriptet.</span><span class="sxs-lookup"><span data-stu-id="52431-171">Specifies the version of the script.</span></span>

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

### <span data-ttu-id="52431-172">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="52431-172">-WhatIf</span></span>

<span data-ttu-id="52431-173">Visar vad som händer om `New-ScriptFileInfo` körs.</span><span class="sxs-lookup"><span data-stu-id="52431-173">Shows what would happen if `New-ScriptFileInfo` runs.</span></span> <span data-ttu-id="52431-174">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="52431-174">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="52431-175">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="52431-175">CommonParameters</span></span>

<span data-ttu-id="52431-176">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="52431-176">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="52431-177">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="52431-177">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="52431-178">INDATA</span><span class="sxs-lookup"><span data-stu-id="52431-178">INPUTS</span></span>

## <span data-ttu-id="52431-179">UTDATA</span><span class="sxs-lookup"><span data-stu-id="52431-179">OUTPUTS</span></span>

## <span data-ttu-id="52431-180">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="52431-180">NOTES</span></span>

## <span data-ttu-id="52431-181">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="52431-181">RELATED LINKS</span></span>

[<span data-ttu-id="52431-182">about_Splatting</span><span class="sxs-lookup"><span data-stu-id="52431-182">about_Splatting</span></span>](../Microsoft.Powershell.Core/About/about_splatting.md)

[<span data-ttu-id="52431-183">Test-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="52431-183">Test-ScriptFileInfo</span></span>](Test-ScriptFileInfo.md)

[<span data-ttu-id="52431-184">Update-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="52431-184">Update-ScriptFileInfo</span></span>](Update-ScriptFileInfo.md)
