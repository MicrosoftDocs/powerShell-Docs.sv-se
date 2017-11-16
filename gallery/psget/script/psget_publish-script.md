---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: galleriet, powershell, cmdlet, psget
title: Publicera skript
ms.openlocfilehash: 0d2fd87645d2286e87e68198844adce8909739cb
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="publish-script"></a><span data-ttu-id="95234-103">Publicera skript</span><span class="sxs-lookup"><span data-stu-id="95234-103">Publish-Script</span></span>

<span data-ttu-id="95234-104">Cmdlet Publish-skriptet publicerar det angivna skriptet till online-galleriet.</span><span class="sxs-lookup"><span data-stu-id="95234-104">The Publish-Script cmdlet publishes the specified script to the online gallery.</span></span>

## <a name="description"></a><span data-ttu-id="95234-105">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="95234-105">Description</span></span>

<span data-ttu-id="95234-106">Publicera skript-cmdleten låter dig om du vill publicera skriptfilen med giltiga metadata som Version, Guid, författare och beskrivning, osv. Tvingad switchparametern på Publicera skript cmdlet startar NuGet.exe utan att fråga.</span><span class="sxs-lookup"><span data-stu-id="95234-106">Publish-Script cmdlet lets you to publish your script file with valid metadata like Version, Guid, Author, and Description, etc. Force switch parameter on Publish-Script cmdlet bootstraps the NuGet.exe without prompting.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="95234-107">Cmdlet-syntax</span><span class="sxs-lookup"><span data-stu-id="95234-107">Cmdlet syntax</span></span>

```powershell
Get-Command -Name Publish-Script -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="95234-108">Cmdlet-referens för onlinehjälp</span><span class="sxs-lookup"><span data-stu-id="95234-108">Cmdlet online help reference</span></span>

[<span data-ttu-id="95234-109">Publicera skript</span><span class="sxs-lookup"><span data-stu-id="95234-109">Publish-Script</span></span>](http://go.microsoft.com/fwlink/?LinkId=619788)

## <a name="example-commands"></a><span data-ttu-id="95234-110">Exempel på kommandon</span><span class="sxs-lookup"><span data-stu-id="95234-110">Example commands</span></span>

```powershell
# Publish the really basic script file with required metadata

Publish-Script -Path C:\ScriptSharingDemo\Demo-Script.ps1 -Repository GalleryINT -NuGetApiKey cad91af7-a49c-4026-9570-a4c16564e785 -Verbose

NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you
want PowerShellGet to install NuGet.exe now?
[Y] Yes [N] No [S] Suspend [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet.exe.
VERBOSE: GET http://go.microsoft.com/fwlink/?LinkID=690216&clcid=0x409 with 0-byte payload
VERBOSE: received 1686528-byte response of content type application/octet-stream
VERBOSE: Performing the operation "Publish-Script" on target "Version '1.0' of script 'Demo-Script'".
VERBOSE: Successfully published script 'Demo-Script' to the publish location 'https://customgallery.cloudapp.net/api/v2/package/'. Please allow few minutes for 'Demo-Script' to show up in the search results.

Find-Script -Repository GalleryINT -Name Demo-Script

Version Name Type Repository Description
------- ---- ---- ---------- -----------
1.0 Demo-Script Script GalleryINT Script file description goes here

Find-Script -Repository GalleryINT -Name Demo-Script | Format-List * -Force

Name : Demo-Script
Version : 1.0
Type : Script
Description : Script file description goes here
Author : manikb
CompanyName : manikb
Copyright :
PublishedDate : 11/16/2015 6:46:28 PM
LicenseUri :
ProjectUri :
IconUri :
Tags : {PSScript}
Includes : {Function, DscResource, Cmdlet, Workflow...}
PowerShellGetFormatVersion :
ReleaseNotes :
Dependencies : {}
RepositorySourceLocation : https://customgallery.cloudapp.net/api/v2/
Repository : GalleryINT
PackageManagementProvider : NuGet
AdditionalMetadata : {description, developmentDependency, tags, PackageManagementProvider...}

```

