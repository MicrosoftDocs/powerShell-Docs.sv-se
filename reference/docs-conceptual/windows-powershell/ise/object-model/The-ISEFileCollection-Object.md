---
ms.date: 12/31/2019
title: ISEFileCollection-objektet
description: ISEFileCollection-objektet är en samling av ISEFile-objekt.
ms.openlocfilehash: 2feef1200c611d5181bcbc55d5464a0bd390084e
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92646750"
---
# <a name="the-isefilecollection-object"></a><span data-ttu-id="4ccf9-103">ISEFileCollection-objektet</span><span class="sxs-lookup"><span data-stu-id="4ccf9-103">The ISEFileCollection Object</span></span>

<span data-ttu-id="4ccf9-104">**ISEFileCollection** -objektet är en samling av **ISEFile** -objekt.</span><span class="sxs-lookup"><span data-stu-id="4ccf9-104">The **ISEFileCollection** object is a collection of **ISEFile** objects.</span></span> <span data-ttu-id="4ccf9-105">Ett exempel är `$psISE.CurrentPowerShellTab.Files` samlingen.</span><span class="sxs-lookup"><span data-stu-id="4ccf9-105">An example is the `$psISE.CurrentPowerShellTab.Files` collection.</span></span>

## <a name="methods"></a><span data-ttu-id="4ccf9-106">Metoder</span><span class="sxs-lookup"><span data-stu-id="4ccf9-106">Methods</span></span>

### <a name="add-fullpath-"></a><span data-ttu-id="4ccf9-107">Lägg till \( \[ fullpath \]\)</span><span class="sxs-lookup"><span data-stu-id="4ccf9-107">Add\( \[FullPath\] \)</span></span>

<span data-ttu-id="4ccf9-108">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="4ccf9-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="4ccf9-109">Skapar och returnerar en ny namnlös fil och lägger till den i samlingen.</span><span class="sxs-lookup"><span data-stu-id="4ccf9-109">Creates and returns a new untitled file and adds it to the collection.</span></span> <span data-ttu-id="4ccf9-110">**IsUntitled** -egenskapen för den nyligen skapade filen är `$true` .</span><span class="sxs-lookup"><span data-stu-id="4ccf9-110">The **IsUntitled** property of the newly created file is `$true`.</span></span>

<span data-ttu-id="4ccf9-111">**\[ Fullpath \]** – valfri sträng som är den fullständigt angivna sökvägen till filen.</span><span class="sxs-lookup"><span data-stu-id="4ccf9-111">**\[FullPath\]** - Optional string The fully specified path of the file.</span></span> <span data-ttu-id="4ccf9-112">Ett undantag skapas om du inkluderar parametern **fullpath** och en relativ sökväg, eller om du använder ett fil namn i stället för den fullständiga sökvägen.</span><span class="sxs-lookup"><span data-stu-id="4ccf9-112">An exception is generated if you include the **FullPath** parameter and a relative path, or if you use a file name instead of the full path.</span></span>

```powershell
# Adds a new untitled file to the collection of files in the current PowerShell tab.
$newFile = $psISE.CurrentPowerShellTab.Files.Add()

# Adds a file specified by its full path to the collection of files in the current PowerShell tab.
$psISE.CurrentPowerShellTab.Files.Add("$pshome\Examples\profile.ps1")
```

### <a name="remove-file-force-"></a><span data-ttu-id="4ccf9-113">Ta bort \( fil, \[ tvinga \]\)</span><span class="sxs-lookup"><span data-stu-id="4ccf9-113">Remove\( File, \[Force\] \)</span></span>

<span data-ttu-id="4ccf9-114">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="4ccf9-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="4ccf9-115">Tar bort en angiven fil från den aktuella PowerShell-fliken.</span><span class="sxs-lookup"><span data-stu-id="4ccf9-115">Removes a specified file from the current PowerShell tab.</span></span>

<span data-ttu-id="4ccf9-116">**Filsträng filen ISEFile** som du vill ta bort från samlingen.</span><span class="sxs-lookup"><span data-stu-id="4ccf9-116">**File** - String The ISEFile file that you want to remove from the collection.</span></span> <span data-ttu-id="4ccf9-117">Om filen inte har sparats, genererar den här metoden ett undantag.</span><span class="sxs-lookup"><span data-stu-id="4ccf9-117">If the file has not been saved, this method throws an exception.</span></span> <span data-ttu-id="4ccf9-118">Använd parametern **Framtvinga** växel för att tvinga borttagning av en fil som inte sparats.</span><span class="sxs-lookup"><span data-stu-id="4ccf9-118">Use the **Force** switch parameter to force the removal of an unsaved file.</span></span>

<span data-ttu-id="4ccf9-119">**\[ \] Tvingande** -valfria booleska om det är inställt på `$true` , ger behörighet att ta bort filen även om den inte har sparats efter den senaste användningen.</span><span class="sxs-lookup"><span data-stu-id="4ccf9-119">**\[Force\]** - optional Boolean If set to `$true`, grants permission to remove the file even if it has not been saved after last use.</span></span> <span data-ttu-id="4ccf9-120">Standardvärdet är `$false`.</span><span class="sxs-lookup"><span data-stu-id="4ccf9-120">The default is `$false`.</span></span>

```powershell
# Removes the first opened file from the file collection associated with the current PowerShell tab.
# If the file has not yet been saved, then an exception is generated.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile)

# Removes the first opened file from the file collection associated with the current PowerShell tab, even if it has not been saved.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile, $true)
```

### <a name="setselectedfile-selectedfile-"></a><span data-ttu-id="4ccf9-121">SetSelectedFile \( selectedFile \)</span><span class="sxs-lookup"><span data-stu-id="4ccf9-121">SetSelectedFile\( selectedFile \)</span></span>

<span data-ttu-id="4ccf9-122">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="4ccf9-122">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="4ccf9-123">Väljer den fil som anges av parametern **SelectedFile** .</span><span class="sxs-lookup"><span data-stu-id="4ccf9-123">Selects the file that is specified by the **SelectedFile** parameter.</span></span>

<span data-ttu-id="4ccf9-124">**SelectedFile** -Microsoft. PowerShell. Host. ISE. ISEFile den ISEFile-fil som du vill välja.</span><span class="sxs-lookup"><span data-stu-id="4ccf9-124">**SelectedFile** - Microsoft.PowerShell.Host.ISE.ISEFile The ISEFile file that you want to select.</span></span>

```powershell
# Selects the specified file.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.SetSelectedFile($firstfile)
```

## <a name="see-also"></a><span data-ttu-id="4ccf9-125">Se även</span><span class="sxs-lookup"><span data-stu-id="4ccf9-125">See Also</span></span>

- [<span data-ttu-id="4ccf9-126">ISEFile-objektet</span><span class="sxs-lookup"><span data-stu-id="4ccf9-126">The ISEFile Object</span></span>](The-ISEFile-Object.md)
- [<span data-ttu-id="4ccf9-127">Användningsområden för Windows PowerShell ISE-skriptobjektmodellen</span><span class="sxs-lookup"><span data-stu-id="4ccf9-127">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="4ccf9-128">Objekt modells-hierarkin för ISE</span><span class="sxs-lookup"><span data-stu-id="4ccf9-128">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
