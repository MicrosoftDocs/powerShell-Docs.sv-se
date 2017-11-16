---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: galleriet, powershell, cmdlet, psget
title: Spara skriptet
ms.openlocfilehash: 7b692d33e3f86a89505b8d37c0da4177f3dff2c2
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="save-script"></a><span data-ttu-id="0065b-103">Spara skriptet</span><span class="sxs-lookup"><span data-stu-id="0065b-103">Save-Script</span></span>

<span data-ttu-id="0065b-104">Spara skriptet cmdlet kan du granska skriptfilen genom att spara den på en angiven plats.</span><span class="sxs-lookup"><span data-stu-id="0065b-104">Save-Script cmdlet lets you to review the script file by saving it to a specified location.</span></span>

## <a name="description"></a><span data-ttu-id="0065b-105">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0065b-105">Description</span></span>

<span data-ttu-id="0065b-106">Spara skriptet cmdlet sparar det angivna skriptet.</span><span class="sxs-lookup"><span data-stu-id="0065b-106">The Save-Script cmdlet saves the specified script.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="0065b-107">Cmdlet-syntax</span><span class="sxs-lookup"><span data-stu-id="0065b-107">Cmdlet syntax</span></span>

```powershell
Get-Command -Name Save-Script -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="0065b-108">Cmdlet-referens för onlinehjälp</span><span class="sxs-lookup"><span data-stu-id="0065b-108">Cmdlet online help reference</span></span>

[<span data-ttu-id="0065b-109">Spara skriptet</span><span class="sxs-lookup"><span data-stu-id="0065b-109">Save-Script</span></span>](http://go.microsoft.com/fwlink/?LinkId=619786)

## <a name="example-commands"></a><span data-ttu-id="0065b-110">Exempel på kommandon</span><span class="sxs-lookup"><span data-stu-id="0065b-110">Example commands</span></span>

### <a name="example-1-save-a-script-from-a-repository"></a><span data-ttu-id="0065b-111">Exempel 1: Spara ett skript från en databas</span><span class="sxs-lookup"><span data-stu-id="0065b-111">Example 1: Save a script from a repository</span></span>
<span data-ttu-id="0065b-112">Detta kommando sparar den senaste versionen av skriptet Fabrikam-ClientScript från GalleryINT databasen till den lokala mappen C:\ScriptSharingDemo</span><span class="sxs-lookup"><span data-stu-id="0065b-112">This command saves the latest version of the script Fabrikam-ClientScript from GalleryINT repository to the local folder C:\ScriptSharingDemo</span></span>

```powershell
Save-Script -Name Fabrikam-ClientScript -Repository GalleryINT -Path C:\ScriptSharingDemo
```

### <a name="example-2-save-a-version-of-a-script-by-piping-from-the-find-script-cmdlet"></a><span data-ttu-id="0065b-113">Exempel 2: Spara en version av ett skript genom att rörnät från cmdleten Sök-skript</span><span class="sxs-lookup"><span data-stu-id="0065b-113">Example 2: Save a version of a script by piping from the Find-Script cmdlet</span></span>

<span data-ttu-id="0065b-114">Det första kommandot hittar version 1.5 för Fabrikam-ClientScript från databasen GalleryINT och sparar den i mappen C:\ScriptSharingDemo</span><span class="sxs-lookup"><span data-stu-id="0065b-114">The first command finds version 1.5 of Fabrikam-ClientScript from the repository GalleryINT and saves it to the folder C:\ScriptSharingDemo</span></span>

<span data-ttu-id="0065b-115">Det andra kommandot verifierar sparat skriptmetadata.</span><span class="sxs-lookup"><span data-stu-id="0065b-115">The second command validates the saved script metadata.</span></span>

```powershell
Find-Script -Name Fabrikam-ClientScript -Repository GalleryINT -RequiredVersion 1.5 | Save-Script -Path C:\\ScriptSharingDemo
Test-ScriptFileInfo C:\\ScriptSharingDemo\\Fabrikam-ClientScript.ps1

Version Name Author Description
------- ---- ------ -----------
1.5 Fabrikam-ClientScript manikb Description for the Fabrikam-ClientScript script
```

