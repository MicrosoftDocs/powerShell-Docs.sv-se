---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Objektet ISEFileCollection
ms.assetid: 0f86a427-ea38-4bce-85f8-06c98d30d508
ms.openlocfilehash: 60bf4dae33f3a71c31e7fdbed0f4fd6ab27a8bd1
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/08/2017
---
# <a name="the-isefilecollection-object"></a><span data-ttu-id="1ea22-103">Objektet ISEFileCollection</span><span class="sxs-lookup"><span data-stu-id="1ea22-103">The ISEFileCollection Object</span></span>
  <span data-ttu-id="1ea22-104">Den **ISEFileCollection** objekt är en samling **ISEFile** objekt.</span><span class="sxs-lookup"><span data-stu-id="1ea22-104">The **ISEFileCollection** object is a collection of **ISEFile** objects.</span></span> <span data-ttu-id="1ea22-105">Ett exempel är $psISE.CurrentPowerShellTab.Files-samling.</span><span class="sxs-lookup"><span data-stu-id="1ea22-105">An example is the $psISE.CurrentPowerShellTab.Files collection.</span></span>

## <a name="methods"></a><span data-ttu-id="1ea22-106">Metoder</span><span class="sxs-lookup"><span data-stu-id="1ea22-106">Methods</span></span>

### <a name="add-fullpath-"></a><span data-ttu-id="1ea22-107">Lägg till\( \[fullPath\]\)</span><span class="sxs-lookup"><span data-stu-id="1ea22-107">Add\( \[fullPath\] \)</span></span>
  <span data-ttu-id="1ea22-108">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="1ea22-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="1ea22-109">Skapar och returnerar en ny namnlös fil och lägger till den samlingen.</span><span class="sxs-lookup"><span data-stu-id="1ea22-109">Creates and returns a new untitled file and adds it to the collection.</span></span> <span data-ttu-id="1ea22-110">Den **IsUntitled** egenskapen för den nya filen är **$true**.</span><span class="sxs-lookup"><span data-stu-id="1ea22-110">The **IsUntitled** property of the newly created file is **$true**.</span></span>

 <span data-ttu-id="1ea22-111">**\[fullPath\]**  – valfritt string fullständigt angiven sökväg till filen.</span><span class="sxs-lookup"><span data-stu-id="1ea22-111">**\[fullPath\]** - Optional string The fully specified path of the file.</span></span> <span data-ttu-id="1ea22-112">Ett undantag genereras om du inkluderar den **fullPath** parametern och en relativ sökväg, eller om du använder ett filnamn i stället för den fullständiga sökvägen.</span><span class="sxs-lookup"><span data-stu-id="1ea22-112">An exception is generated if you include the **fullPath** parameter and a relative path, or if you use a file name instead of the full path.</span></span>

```
# Adds a new untitled file to the collection of files in the current PowerShell tab.
$newFile = $psISE.CurrentPowerShellTab.Files.Add()

# Adds a file specified by its full path to the collection of files in the current PowerShell tab.
$psISE.CurrentPowerShellTab.Files.Add("$pshome\Examples\profile.ps1")

```

### <a name="remove-file-force-"></a><span data-ttu-id="1ea22-113">Ta bort\( filen \[kraft\]\)</span><span class="sxs-lookup"><span data-stu-id="1ea22-113">Remove\( File, \[Force\] \)</span></span>
  <span data-ttu-id="1ea22-114">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="1ea22-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="1ea22-115">Tar bort en fil från den aktuella PowerShell-fliken.</span><span class="sxs-lookup"><span data-stu-id="1ea22-115">Removes a specified file from the current PowerShell tab.</span></span>

 <span data-ttu-id="1ea22-116">**Filen** -sträng i ISEFile-fil som du vill ta bort från samlingen.</span><span class="sxs-lookup"><span data-stu-id="1ea22-116">**File** - String The ISEFile file that you want to remove from the collection.</span></span> <span data-ttu-id="1ea22-117">Om filen inte har sparats, genereras ett undantag i den här metoden.</span><span class="sxs-lookup"><span data-stu-id="1ea22-117">If the file has not been saved, this method throws an exception.</span></span> <span data-ttu-id="1ea22-118">Använd den **tvinga** växla parametern om du vill framtvinga borttagning av en fil som inte har sparats.</span><span class="sxs-lookup"><span data-stu-id="1ea22-118">Use the **Force** switch parameter to force the removal of an unsaved file.</span></span>

 <span data-ttu-id="1ea22-119">**\[Framtvinga\]**  -valfritt booleskt om **$true**, ger behörighet att ta bort filen även om den inte har sparats efter senaste användning.</span><span class="sxs-lookup"><span data-stu-id="1ea22-119">**\[Force\]** - optional Boolean If set to **$true**, grants permission to remove the file even if it has not been saved after last use.</span></span> <span data-ttu-id="1ea22-120">Standardvärdet är **$false**.</span><span class="sxs-lookup"><span data-stu-id="1ea22-120">The default is **$false**.</span></span>

```
# Removes the first opened file from the file collection associated with the current PowerShell tab.
# If the file has not yet been saved, then an exception is generated.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile)

# Removes the first opened file from the file collection associated with the current PowerShell tab, even if it has not been saved.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile, $true)
```

### <a name="setselectedfile-selectedfile-"></a><span data-ttu-id="1ea22-121">SetSelectedFile\( selectedFile\)</span><span class="sxs-lookup"><span data-stu-id="1ea22-121">SetSelectedFile\( selectedFile \)</span></span>
  <span data-ttu-id="1ea22-122">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="1ea22-122">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="1ea22-123">Väljer du den fil som anges av den **selectedFile** parameter.</span><span class="sxs-lookup"><span data-stu-id="1ea22-123">Selects the file that is specified by the **selectedFile** parameter.</span></span>

 <span data-ttu-id="1ea22-124">**selectedFile** -Microsoft.PowerShell.Host.ISE.ISEFile i ISEFile-fil som du vill välja.</span><span class="sxs-lookup"><span data-stu-id="1ea22-124">**selectedFile** - Microsoft.PowerShell.Host.ISE.ISEFile The ISEFile file that you want to select.</span></span>

```

# Selects the specified file.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.SetSelectedFile($firstfile)

```

## <a name="see-also"></a><span data-ttu-id="1ea22-125">Se även</span><span class="sxs-lookup"><span data-stu-id="1ea22-125">See Also</span></span>
- [<span data-ttu-id="1ea22-126">Objektet ISEFile</span><span class="sxs-lookup"><span data-stu-id="1ea22-126">The ISEFile Object</span></span>](The-ISEFile-Object.md) 
- [<span data-ttu-id="1ea22-127">Windows PowerShell ISE Scripting Object Model</span><span class="sxs-lookup"><span data-stu-id="1ea22-127">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="1ea22-128">Windows PowerShell ISE objektreferens modellen</span><span class="sxs-lookup"><span data-stu-id="1ea22-128">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="1ea22-129">Modellen objekthierarkin ISE</span><span class="sxs-lookup"><span data-stu-id="1ea22-129">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
