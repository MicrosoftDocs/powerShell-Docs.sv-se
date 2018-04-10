---
ms.date: 10/17/2017
contributor: keithb
ms.topic: reference
keywords: galleriet, powershell, cmdlet, psget
title: Spara skriptet
ms.openlocfilehash: 67697fc0e70fb31cad9ad5ae7ce01debef160b81
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="save-script"></a><span data-ttu-id="07c57-103">Spara skriptet</span><span class="sxs-lookup"><span data-stu-id="07c57-103">Save-Script</span></span>

<span data-ttu-id="07c57-104">Spara skriptet cmdlet kan du granska skriptfilen genom att spara den på en angiven plats.</span><span class="sxs-lookup"><span data-stu-id="07c57-104">Save-Script cmdlet lets you to review the script file by saving it to a specified location.</span></span>

## <a name="description"></a><span data-ttu-id="07c57-105">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="07c57-105">Description</span></span>

<span data-ttu-id="07c57-106">Spara skriptet cmdlet sparar det angivna skriptet.</span><span class="sxs-lookup"><span data-stu-id="07c57-106">The Save-Script cmdlet saves the specified script.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="07c57-107">Cmdlet-syntax</span><span class="sxs-lookup"><span data-stu-id="07c57-107">Cmdlet syntax</span></span>

```powershell
Get-Command -Name Save-Script -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="07c57-108">Cmdlet-referens för onlinehjälp</span><span class="sxs-lookup"><span data-stu-id="07c57-108">Cmdlet online help reference</span></span>

[<span data-ttu-id="07c57-109">Save-Script</span><span class="sxs-lookup"><span data-stu-id="07c57-109">Save-Script</span></span>](http://go.microsoft.com/fwlink/?LinkId=619786)

## <a name="example-commands"></a><span data-ttu-id="07c57-110">Exempel på kommandon</span><span class="sxs-lookup"><span data-stu-id="07c57-110">Example commands</span></span>

### <a name="example-1-save-a-script-from-a-repository"></a><span data-ttu-id="07c57-111">Exempel 1: Spara ett skript från en databas</span><span class="sxs-lookup"><span data-stu-id="07c57-111">Example 1: Save a script from a repository</span></span>
<span data-ttu-id="07c57-112">Detta kommando sparar den senaste versionen av skriptet Fabrikam-ClientScript från GalleryINT databasen till den lokala mappen C:\ScriptSharingDemo</span><span class="sxs-lookup"><span data-stu-id="07c57-112">This command saves the latest version of the script Fabrikam-ClientScript from GalleryINT repository to the local folder C:\ScriptSharingDemo</span></span>

```powershell
Save-Script -Name Fabrikam-ClientScript -Repository GalleryINT -Path C:\ScriptSharingDemo
```

### <a name="example-2-save-a-version-of-a-script-by-piping-from-the-find-script-cmdlet"></a><span data-ttu-id="07c57-113">Exempel 2: Spara en version av ett skript genom att rörnät från cmdleten Sök-skript</span><span class="sxs-lookup"><span data-stu-id="07c57-113">Example 2: Save a version of a script by piping from the Find-Script cmdlet</span></span>

<span data-ttu-id="07c57-114">Det första kommandot hittar version 1.5 för Fabrikam-ClientScript från databasen GalleryINT och sparar den i mappen C:\ScriptSharingDemo</span><span class="sxs-lookup"><span data-stu-id="07c57-114">The first command finds version 1.5 of Fabrikam-ClientScript from the repository GalleryINT and saves it to the folder C:\ScriptSharingDemo</span></span>

<span data-ttu-id="07c57-115">Det andra kommandot verifierar sparat skriptmetadata.</span><span class="sxs-lookup"><span data-stu-id="07c57-115">The second command validates the saved script metadata.</span></span>

```powershell
Find-Script -Name Fabrikam-ClientScript -Repository GalleryINT -RequiredVersion 1.5 | Save-Script -Path C:\\ScriptSharingDemo
Test-ScriptFileInfo C:\\ScriptSharingDemo\\Fabrikam-ClientScript.ps1

Version Name Author Description
------- ---- ------ -----------
1.5 Fabrikam-ClientScript manikb Description for the Fabrikam-ClientScript script
```

### <a name="example-3-save-a-prerelease-version-of-a-script-from-a-repository"></a><span data-ttu-id="07c57-116">Exempel 3: Spara en förhandsversion av ett skript från en databas</span><span class="sxs-lookup"><span data-stu-id="07c57-116">Example 3: Save a prerelease version of a script from a repository</span></span>
<span data-ttu-id="07c57-117">Detta kommando sparar den senaste versionen av skriptet Fabrikam-ClientScript från GalleryINT databasen till den lokala mappen C:\ScriptSharingDemo</span><span class="sxs-lookup"><span data-stu-id="07c57-117">This command saves the latest version of the script Fabrikam-ClientScript from GalleryINT repository to the local folder C:\ScriptSharingDemo</span></span>

```powershell
Save-Script -Name Fabrikam-ClientScript -Path C:\ScriptSharingDemo -AllowPrerelease
```