---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: galleriet, powershell, cmdlet, psget
title: Testa ScriptFileInfo
ms.openlocfilehash: 0f6951b86bba352e33abe91fc76e000b7df75b49
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="test-scriptfileinfo"></a><span data-ttu-id="cee49-103">Testa ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="cee49-103">Test-ScriptFileInfo</span></span>

<span data-ttu-id="cee49-104">Verifierar kommentarsblock metadata i en skriptfil.</span><span class="sxs-lookup"><span data-stu-id="cee49-104">Validates the metadata comment block of a script file.</span></span>

## <a name="description"></a><span data-ttu-id="cee49-105">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="cee49-105">Description</span></span>

<span data-ttu-id="cee49-106">Cmdleten Test-ScriptFileInfo verifierar kommentarsblock i början av ett skript som publiceras med cmdlet Publish-skript.</span><span class="sxs-lookup"><span data-stu-id="cee49-106">The Test-ScriptFileInfo cmdlet validates the comment block at the beginning of a script that will be published with the Publish-Script cmdlet.</span></span>
<span data-ttu-id="cee49-107">Om kommentarsblock metadata innehåller ett fel kan returnerar denna cmdlet information om var felet finns eller hur du korrigerar den.</span><span class="sxs-lookup"><span data-stu-id="cee49-107">If the metadata comment block has an error, this cmdlet returns information about where the error is located or how to correct it.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="cee49-108">Cmdlet-syntax</span><span class="sxs-lookup"><span data-stu-id="cee49-108">Cmdlet syntax</span></span>

```powershell
Get-Command -Name Test-ScriptFileInfo -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="cee49-109">Cmdlet-referens för onlinehjälp</span><span class="sxs-lookup"><span data-stu-id="cee49-109">Cmdlet online help reference</span></span>

[<span data-ttu-id="cee49-110">Testa ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="cee49-110">Test-ScriptFileInfo</span></span>](http://go.microsoft.com/fwlink/?LinkId=619791)

## <a name="example-commands"></a><span data-ttu-id="cee49-111">Exempel på kommandon</span><span class="sxs-lookup"><span data-stu-id="cee49-111">Example commands</span></span>
```powershell
# Create a new script file with minimum required metadata values
New-ScriptFileInfo -Path C:\ScriptSharingDemo\Demo-Script.ps1 -Description "Script file description goes here"

Get-Content -Path C:\ScriptSharingDemo\Demo-Script.ps1
<#PSScriptInfo
.VERSION 1.0
.GUID 926b47c3-6af2-4b18-b6f5-8b813a9e93ab
.AUTHOR manikb
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
#>
<#
.DESCRIPTION
Script file description goes here
#>
Param()

# Validate and get the script metadata
Test-ScriptFileInfo -Path C:\ScriptSharingDemo\Demo-Script.ps1
Version Name Author Description
------- ---- ------ -----------
1.0 Demo-Script manikb Script file description goes here

# This command tests the script file Test-Runbook.ps1 and uses the pipeline operator to pass the results to the Format-List cmdlet to format the results.
Test-ScriptFileInfo -Path D:\code\Test-Runbook.ps1 | Format-List *

# This command tests the script file Hello-World.ps1, which has no metadata associated with it.
Test-ScriptFileInfo -Path C:\code\Hello-World.ps1
Test-ScriptFileInfo : PSScriptInfo is not specified in the script file 'C:\code\Hello-World.ps1'. You can use the Update-ScriptFileInfo with -Force or New-ScriptFileInfo cmdlet to add the PSScriptInfo to the script file.
At line:1 char:1
+ Test-ScriptFileInfo -Path C:\code\Hello-World.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (C:\code\Hello-World.ps1:String) [Test-ScriptFileInfo], ArgumentException
    + FullyQualifiedErrorId : MissingPSScriptInfo,Test-ScriptFileInfo

```

