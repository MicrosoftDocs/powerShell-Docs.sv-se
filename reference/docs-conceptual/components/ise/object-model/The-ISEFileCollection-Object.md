---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: ISEFileCollection-objektet
ms.assetid: 0f86a427-ea38-4bce-85f8-06c98d30d508
ms.openlocfilehash: eb4b2784820cbe51f662fd2fd945d8760ef9dbff
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53406034"
---
# <a name="the-isefilecollection-object"></a><span data-ttu-id="3906e-103">ISEFileCollection-objektet</span><span class="sxs-lookup"><span data-stu-id="3906e-103">The ISEFileCollection Object</span></span>

<span data-ttu-id="3906e-104">Den **ISEFileCollection** objekt är en samling **ISEFile** objekt.</span><span class="sxs-lookup"><span data-stu-id="3906e-104">The **ISEFileCollection** object is a collection of **ISEFile** objects.</span></span> <span data-ttu-id="3906e-105">Ett exempel är $psISE.CurrentPowerShellTab.Files-samling.</span><span class="sxs-lookup"><span data-stu-id="3906e-105">An example is the $psISE.CurrentPowerShellTab.Files collection.</span></span>

## <a name="methods"></a><span data-ttu-id="3906e-106">Metoder</span><span class="sxs-lookup"><span data-stu-id="3906e-106">Methods</span></span>

### <a name="add-fullpath-"></a><span data-ttu-id="3906e-107">Lägg till\( \[fullPath\] \)</span><span class="sxs-lookup"><span data-stu-id="3906e-107">Add\( \[fullPath\] \)</span></span>

<span data-ttu-id="3906e-108">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="3906e-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="3906e-109">Skapar och returnerar en ny namnlös fil och lägger till den i samlingen.</span><span class="sxs-lookup"><span data-stu-id="3906e-109">Creates and returns a new untitled file and adds it to the collection.</span></span> <span data-ttu-id="3906e-110">Den **IsUntitled** egenskapen för den nyligen skapade filen är **$true**.</span><span class="sxs-lookup"><span data-stu-id="3906e-110">The **IsUntitled** property of the newly created file is **$true**.</span></span>

<span data-ttu-id="3906e-111">**\[fullPath\]**  – valfritt sträng fullständigt angivna sökvägen till filen.</span><span class="sxs-lookup"><span data-stu-id="3906e-111">**\[fullPath\]** - Optional string The fully specified path of the file.</span></span> <span data-ttu-id="3906e-112">Ett undantag genereras om du inkluderar den **fullPath** parameter och en relativ sökväg, eller om du använder ett filnamn i stället för den fullständiga sökvägen.</span><span class="sxs-lookup"><span data-stu-id="3906e-112">An exception is generated if you include the **fullPath** parameter and a relative path, or if you use a file name instead of the full path.</span></span>

```powershell
# Adds a new untitled file to the collection of files in the current PowerShell tab.
$newFile = $psISE.CurrentPowerShellTab.Files.Add()

# Adds a file specified by its full path to the collection of files in the current PowerShell tab.
$psISE.CurrentPowerShellTab.Files.Add("$pshome\Examples\profile.ps1")
```

### <a name="remove-file-force-"></a><span data-ttu-id="3906e-113">Ta bort\( filen \[kraft\] \)</span><span class="sxs-lookup"><span data-stu-id="3906e-113">Remove\( File, \[Force\] \)</span></span>

<span data-ttu-id="3906e-114">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="3906e-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="3906e-115">Tar bort en angiven fil från den aktuella PowerShell-fliken.</span><span class="sxs-lookup"><span data-stu-id="3906e-115">Removes a specified file from the current PowerShell tab.</span></span>

<span data-ttu-id="3906e-116">**Filen** -sträng The ISEFile-fil som du vill ta bort från samlingen.</span><span class="sxs-lookup"><span data-stu-id="3906e-116">**File** - String The ISEFile file that you want to remove from the collection.</span></span> <span data-ttu-id="3906e-117">Om filen inte har sparats, utlöser ett undantag i den här metoden.</span><span class="sxs-lookup"><span data-stu-id="3906e-117">If the file has not been saved, this method throws an exception.</span></span> <span data-ttu-id="3906e-118">Använd den **tvinga** växla parametern om du vill framtvinga borttagning av en ej sparade filer.</span><span class="sxs-lookup"><span data-stu-id="3906e-118">Use the **Force** switch parameter to force the removal of an unsaved file.</span></span>

<span data-ttu-id="3906e-119">**\[Framtvinga\]**  -valfritt booleskt om **$true**, ger behörighet att ta bort filen även om det inte har sparats efter senaste användning.</span><span class="sxs-lookup"><span data-stu-id="3906e-119">**\[Force\]** - optional Boolean If set to **$true**, grants permission to remove the file even if it has not been saved after last use.</span></span> <span data-ttu-id="3906e-120">Standardvärdet är **$false**.</span><span class="sxs-lookup"><span data-stu-id="3906e-120">The default is **$false**.</span></span>

```powershell
# Removes the first opened file from the file collection associated with the current PowerShell tab.
# If the file has not yet been saved, then an exception is generated.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile)

# Removes the first opened file from the file collection associated with the current PowerShell tab, even if it has not been saved.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile, $true)
```

### <a name="setselectedfile-selectedfile-"></a><span data-ttu-id="3906e-121">SetSelectedFile\( selectedFile \)</span><span class="sxs-lookup"><span data-stu-id="3906e-121">SetSelectedFile\( selectedFile \)</span></span>

<span data-ttu-id="3906e-122">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="3906e-122">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="3906e-123">Väljer den fil som anges av den **selectedFile** parametern.</span><span class="sxs-lookup"><span data-stu-id="3906e-123">Selects the file that is specified by the **selectedFile** parameter.</span></span>

<span data-ttu-id="3906e-124">**selectedFile** -Microsoft.PowerShell.Host.ISE.ISEFile The ISEFile-fil som du vill välja.</span><span class="sxs-lookup"><span data-stu-id="3906e-124">**selectedFile** - Microsoft.PowerShell.Host.ISE.ISEFile The ISEFile file that you want to select.</span></span>

```powershell
# Selects the specified file.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.SetSelectedFile($firstfile)
```

## <a name="see-also"></a><span data-ttu-id="3906e-125">Se även</span><span class="sxs-lookup"><span data-stu-id="3906e-125">See Also</span></span>

- [<span data-ttu-id="3906e-126">ISEFile-objektet</span><span class="sxs-lookup"><span data-stu-id="3906e-126">The ISEFile Object</span></span>](The-ISEFile-Object.md)
- [<span data-ttu-id="3906e-127">Syftet med den Windows PowerShell ISE-Skriptobjektmodellen</span><span class="sxs-lookup"><span data-stu-id="3906e-127">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="3906e-128">Hierarki för ISE-objektmodellen</span><span class="sxs-lookup"><span data-stu-id="3906e-128">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)