---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/test-scriptfileinfo?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-ScriptFileInfo
ms.openlocfilehash: 4b02b853da5f42eb76d63ec38f77852df838bbe0
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264063"
---
# <span data-ttu-id="d8a0f-103">Test-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="d8a0f-103">Test-ScriptFileInfo</span></span>

## <span data-ttu-id="d8a0f-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="d8a0f-104">SYNOPSIS</span></span>
<span data-ttu-id="d8a0f-105">Verifierar ett kommentar block för ett skript.</span><span class="sxs-lookup"><span data-stu-id="d8a0f-105">Validates a comment block for a script.</span></span>

## <span data-ttu-id="d8a0f-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d8a0f-106">SYNTAX</span></span>

### <span data-ttu-id="d8a0f-107">PathParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="d8a0f-107">PathParameterSet (Default)</span></span>

```
Test-ScriptFileInfo [-Path] <String> [<CommonParameters>]
```

### <span data-ttu-id="d8a0f-108">LiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="d8a0f-108">LiteralPathParameterSet</span></span>

```
Test-ScriptFileInfo -LiteralPath <String> [<CommonParameters>]
```

## <span data-ttu-id="d8a0f-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="d8a0f-109">DESCRIPTION</span></span>

<span data-ttu-id="d8a0f-110">Cmdleten **test-ScriptFileInfo** verifierar kommentars blocket i början av ett skript som ska publiceras med Publish-Script-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="d8a0f-110">The **Test-ScriptFileInfo** cmdlet validates the comment block at the beginning of a script that will be published with the Publish-Script cmdlet.</span></span>
<span data-ttu-id="d8a0f-111">Om kommentars blocket innehåller ett fel, returnerar denna cmdlet information om var felet finns eller hur du korrigerar det.</span><span class="sxs-lookup"><span data-stu-id="d8a0f-111">If the comment block has an error, this cmdlet returns information about where the error is located or how to correct it.</span></span>

## <span data-ttu-id="d8a0f-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="d8a0f-112">EXAMPLES</span></span>

### <span data-ttu-id="d8a0f-113">Exempel 1: testa en skript fil</span><span class="sxs-lookup"><span data-stu-id="d8a0f-113">Example 1: Test a script file</span></span>

```
PS C:\> Test-ScriptFileInfo -Path "C:\temp\temp_scripts\New-ScriptFile.ps1"
Version    Name                      Author               Description
-------    ----                      ------               -----------
1.0        New-ScriptFile            pattif               my new script file test
```

<span data-ttu-id="d8a0f-114">Det här kommandot testar New-ScriptFile.ps1 skript filen och visar resultatet.</span><span class="sxs-lookup"><span data-stu-id="d8a0f-114">This command tests the New-ScriptFile.ps1 script file and displays the results.</span></span>
<span data-ttu-id="d8a0f-115">Skript filen innehåller giltiga metadata.</span><span class="sxs-lookup"><span data-stu-id="d8a0f-115">The script file includes valid metadata.</span></span>

### <span data-ttu-id="d8a0f-116">Exempel 2: testa en skript fil som innehåller värden för alla egenskaper för metadata</span><span class="sxs-lookup"><span data-stu-id="d8a0f-116">Example 2: Test a script file that has values for all metadata properties</span></span>

```
PS C:\> Test-ScriptFileInfo -Path "D:\code\Test-Runbook.ps1" | Format-List *
Name                       : Test-Runbook
Path                       : D:\code\Test-Runbook.ps1
ScriptBase                 : D:\code
ReleaseNotes               : {contoso script now supports following features, Feature 1, Feature 2, Feature 3...}
Version                    : 1.0
Guid                       : eb246b19-17da-4392-8c89-7c280f69ad0e
Author                     : pattif
CompanyName                : Microsoft Corporation
Copyright                  : 2015 Microsoft Corporation. All rights reserved.
Tags                       : {Tag1, Tag2, Tag3}
LicenseUri                 : https://contoso.com/License
ProjectUri                 : https://contoso.com/
IconUri                    : https://contoso.com/MyScriptIcon
ExternalModuleDependencies : ExternalModule1
RequiredScripts            : {Start-WFContosoServer, Stop-ContosoServerScript}
ExternalScriptDependencies : Stop-ContosoServerScript
Description                : Contoso Script example
RequiredModules            : {RequiredModule1, @{ ModuleName = 'RequiredModule2'; ModuleVersion = '1.0' }, @{ ModuleName = 'RequiredModule3'; RequiredVersion = '2.0' }, ExternalModule1}
ExportedCommands           : {Test-WebUri, ValidateAndAdd-PSScriptInfoEntry, Get-PSScriptInfo, My-Workflow...}
ExportedFunctions          : {Test-WebUri, ValidateAndAdd-PSScriptInfoEntry, Get-PSScriptInfo, My-AdvPSCmdlet}
ExportedWorkflows          : My-Workflow
```

<span data-ttu-id="d8a0f-117">Det här kommandot testar skript filen Test-Runbook.ps1 och använder pipelinen för att skicka resultaten till Format-List-cmdlet för att formatera resultaten.</span><span class="sxs-lookup"><span data-stu-id="d8a0f-117">This command tests the script file Test-Runbook.ps1 and uses the pipeline operator to pass the results to the Format-List cmdlet to format the results.</span></span>

### <span data-ttu-id="d8a0f-118">Exempel 3: testa en skript fil som saknar metadata</span><span class="sxs-lookup"><span data-stu-id="d8a0f-118">Example 3: Test a script file that has no metadata</span></span>

```
PS C:\> Test-ScriptFileInfo -Path "D:\code\Hello-World.ps1"
Test-ScriptFileInfo : Script 'D:\code\Hello-World.ps1' is missing required metadata properties. Verify that the script file has Version, Description
and Author properties. You can use the Update-ScriptFileInfo or New-ScriptFileInfo cmdlet to add or update the PSScriptInfo to the script file.
At line:1 char:1
+ Test-ScriptFileInfo D:\code\Hello-World.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : InvalidArgument: (D:\code\Hello-World.ps1:String) [Test-ScriptFileInfo], ArgumentException

+ FullyQualifiedErrorId : MissingRequiredPSScriptInfoProperties,Test-ScriptFile
```

<span data-ttu-id="d8a0f-119">Det här kommandot testar skript filen Hello-World.ps1, som inte har några associerade metadata.</span><span class="sxs-lookup"><span data-stu-id="d8a0f-119">This command tests the script file Hello-World.ps1, which has no metadata associated with it.</span></span>

## <span data-ttu-id="d8a0f-120">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="d8a0f-120">PARAMETERS</span></span>

### <span data-ttu-id="d8a0f-121">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="d8a0f-121">-LiteralPath</span></span>

<span data-ttu-id="d8a0f-122">Anger en sökväg till en eller flera platser.</span><span class="sxs-lookup"><span data-stu-id="d8a0f-122">Specifies a path to one or more locations.</span></span>
<span data-ttu-id="d8a0f-123">Till skillnad från parametern *Path* används värdet för parametern *LiteralPath* exakt som den anges.</span><span class="sxs-lookup"><span data-stu-id="d8a0f-123">Unlike the *Path* parameter, the value of the *LiteralPath* parameter is used exactly as it is entered.</span></span>
<span data-ttu-id="d8a0f-124">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="d8a0f-124">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="d8a0f-125">Om sökvägen innehåller escape-tecken, omger du dem med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="d8a0f-125">If the path includes escape characters, enclose them in single quotation marks.</span></span>
<span data-ttu-id="d8a0f-126">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="d8a0f-126">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: LiteralPathParameterSet
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d8a0f-127">-Path</span><span class="sxs-lookup"><span data-stu-id="d8a0f-127">-Path</span></span>

<span data-ttu-id="d8a0f-128">Anger en sökväg till en eller flera platser.</span><span class="sxs-lookup"><span data-stu-id="d8a0f-128">Specifies a path to one or more locations.</span></span>
<span data-ttu-id="d8a0f-129">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="d8a0f-129">Wildcards are permitted.</span></span>
<span data-ttu-id="d8a0f-130">Standard platsen är den aktuella katalogen (.).</span><span class="sxs-lookup"><span data-stu-id="d8a0f-130">The default location is the current directory (.).</span></span>

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

### <span data-ttu-id="d8a0f-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d8a0f-131">CommonParameters</span></span>

<span data-ttu-id="d8a0f-132">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d8a0f-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d8a0f-133">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="d8a0f-133">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d8a0f-134">INDATA</span><span class="sxs-lookup"><span data-stu-id="d8a0f-134">INPUTS</span></span>

### <span data-ttu-id="d8a0f-135">System. String</span><span class="sxs-lookup"><span data-stu-id="d8a0f-135">System.String</span></span>

## <span data-ttu-id="d8a0f-136">UTDATA</span><span class="sxs-lookup"><span data-stu-id="d8a0f-136">OUTPUTS</span></span>

### <span data-ttu-id="d8a0f-137">System. Object</span><span class="sxs-lookup"><span data-stu-id="d8a0f-137">System.Object</span></span>

## <span data-ttu-id="d8a0f-138">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="d8a0f-138">NOTES</span></span>

## <span data-ttu-id="d8a0f-139">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="d8a0f-139">RELATED LINKS</span></span>

[<span data-ttu-id="d8a0f-140">New-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="d8a0f-140">New-ScriptFileInfo</span></span>](New-ScriptFileInfo.md)

[<span data-ttu-id="d8a0f-141">Publicera – skript</span><span class="sxs-lookup"><span data-stu-id="d8a0f-141">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="d8a0f-142">Update-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="d8a0f-142">Update-ScriptFileInfo</span></span>](Update-ScriptFileInfo.md)

