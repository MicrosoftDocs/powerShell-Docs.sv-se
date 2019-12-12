---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: ISEFileCollection-objektet
ms.openlocfilehash: 96db51ee921cc0fa34803091d563bc6e118643b6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030528"
---
# <a name="the-isefilecollection-object"></a><span data-ttu-id="6dfd1-103">ISEFileCollection-objektet</span><span class="sxs-lookup"><span data-stu-id="6dfd1-103">The ISEFileCollection Object</span></span>

<span data-ttu-id="6dfd1-104">**ISEFileCollection** -objektet är en samling av **ISEFile** -objekt.</span><span class="sxs-lookup"><span data-stu-id="6dfd1-104">The **ISEFileCollection** object is a collection of **ISEFile** objects.</span></span> <span data-ttu-id="6dfd1-105">Ett exempel är samlingen $psISE. CurrentPowerShellTab. files.</span><span class="sxs-lookup"><span data-stu-id="6dfd1-105">An example is the $psISE.CurrentPowerShellTab.Files collection.</span></span>

## <a name="methods"></a><span data-ttu-id="6dfd1-106">Metoder</span><span class="sxs-lookup"><span data-stu-id="6dfd1-106">Methods</span></span>

### <a name="add-fullpath-"></a><span data-ttu-id="6dfd1-107">Lägg till\( \[fullPath\] \)</span><span class="sxs-lookup"><span data-stu-id="6dfd1-107">Add\( \[fullPath\] \)</span></span>

<span data-ttu-id="6dfd1-108">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="6dfd1-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="6dfd1-109">Skapar och returnerar en ny namnlös fil och lägger till den i samlingen.</span><span class="sxs-lookup"><span data-stu-id="6dfd1-109">Creates and returns a new untitled file and adds it to the collection.</span></span> <span data-ttu-id="6dfd1-110">**IsUntitled** -egenskapen för den nyligen skapade filen är **$True**.</span><span class="sxs-lookup"><span data-stu-id="6dfd1-110">The **IsUntitled** property of the newly created file is **$true**.</span></span>

<span data-ttu-id="6dfd1-111">**\[fullPath\]** – valfri sträng som anger filens fullständiga sökväg.</span><span class="sxs-lookup"><span data-stu-id="6dfd1-111">**\[fullPath\]** - Optional string The fully specified path of the file.</span></span> <span data-ttu-id="6dfd1-112">Ett undantag skapas om du inkluderar parametern **fullPath** och en relativ sökväg, eller om du använder ett fil namn i stället för den fullständiga sökvägen.</span><span class="sxs-lookup"><span data-stu-id="6dfd1-112">An exception is generated if you include the **fullPath** parameter and a relative path, or if you use a file name instead of the full path.</span></span>

```powershell
# Adds a new untitled file to the collection of files in the current PowerShell tab.
$newFile = $psISE.CurrentPowerShellTab.Files.Add()

# Adds a file specified by its full path to the collection of files in the current PowerShell tab.
$psISE.CurrentPowerShellTab.Files.Add("$pshome\Examples\profile.ps1")
```

### <a name="remove-file-force-"></a><span data-ttu-id="6dfd1-113">Ta bort\(-filen \[tvinga\] \)</span><span class="sxs-lookup"><span data-stu-id="6dfd1-113">Remove\( File, \[Force\] \)</span></span>

<span data-ttu-id="6dfd1-114">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="6dfd1-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="6dfd1-115">Tar bort en angiven fil från den aktuella PowerShell-fliken.</span><span class="sxs-lookup"><span data-stu-id="6dfd1-115">Removes a specified file from the current PowerShell tab.</span></span>

<span data-ttu-id="6dfd1-116">**Filsträng filen ISEFile** som du vill ta bort från samlingen.</span><span class="sxs-lookup"><span data-stu-id="6dfd1-116">**File** - String The ISEFile file that you want to remove from the collection.</span></span> <span data-ttu-id="6dfd1-117">Om filen inte har sparats, genererar den här metoden ett undantag.</span><span class="sxs-lookup"><span data-stu-id="6dfd1-117">If the file has not been saved, this method throws an exception.</span></span> <span data-ttu-id="6dfd1-118">Använd parametern **Framtvinga** växel för att tvinga borttagning av en fil som inte sparats.</span><span class="sxs-lookup"><span data-stu-id="6dfd1-118">Use the **Force** switch parameter to force the removal of an unsaved file.</span></span>

<span data-ttu-id="6dfd1-119">**\[tvinga\]** -valfria booleska om värdet är **$True**ger behörighet att ta bort filen även om den inte har sparats efter den senaste användningen.</span><span class="sxs-lookup"><span data-stu-id="6dfd1-119">**\[Force\]** - optional Boolean If set to **$true**, grants permission to remove the file even if it has not been saved after last use.</span></span> <span data-ttu-id="6dfd1-120">Standardvärdet är **$false**.</span><span class="sxs-lookup"><span data-stu-id="6dfd1-120">The default is **$false**.</span></span>

```powershell
# Removes the first opened file from the file collection associated with the current PowerShell tab.
# If the file has not yet been saved, then an exception is generated.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile)

# Removes the first opened file from the file collection associated with the current PowerShell tab, even if it has not been saved.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile, $true)
```

### <a name="setselectedfile-selectedfile-"></a><span data-ttu-id="6dfd1-121">SetSelectedFile\( selectedFile \)</span><span class="sxs-lookup"><span data-stu-id="6dfd1-121">SetSelectedFile\( selectedFile \)</span></span>

<span data-ttu-id="6dfd1-122">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="6dfd1-122">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="6dfd1-123">Väljer den fil som anges av parametern **selectedFile** .</span><span class="sxs-lookup"><span data-stu-id="6dfd1-123">Selects the file that is specified by the **selectedFile** parameter.</span></span>

<span data-ttu-id="6dfd1-124">**selectedFile** -Microsoft. PowerShell. Host. ISE. ISEFile den ISEFile-fil som du vill välja.</span><span class="sxs-lookup"><span data-stu-id="6dfd1-124">**selectedFile** - Microsoft.PowerShell.Host.ISE.ISEFile The ISEFile file that you want to select.</span></span>

```powershell
# Selects the specified file.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.SetSelectedFile($firstfile)
```

## <a name="see-also"></a><span data-ttu-id="6dfd1-125">Se även</span><span class="sxs-lookup"><span data-stu-id="6dfd1-125">See Also</span></span>

- [<span data-ttu-id="6dfd1-126">ISEFile-objektet</span><span class="sxs-lookup"><span data-stu-id="6dfd1-126">The ISEFile Object</span></span>](The-ISEFile-Object.md)
- [<span data-ttu-id="6dfd1-127">Syftet med Windows PowerShell ISE-skriptets objekt modell</span><span class="sxs-lookup"><span data-stu-id="6dfd1-127">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="6dfd1-128">Hierarki för ISE-objektmodellen</span><span class="sxs-lookup"><span data-stu-id="6dfd1-128">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
