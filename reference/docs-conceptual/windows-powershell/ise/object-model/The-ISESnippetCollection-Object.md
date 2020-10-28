---
ms.date: 12/31/2019
title: ISESnippetCollection-objektet
description: ISESnippetCollection-objektet är en samling av ISESnippet-objekt. Den fil samling som är associerad med ett PowerShellTab-objekt är medlem i den här klassen.
ms.openlocfilehash: e6170ddf72d5ead840aa3015d4de1dcb21dbfeff
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92655974"
---
# <a name="the-isesnippetcollection-object"></a><span data-ttu-id="d5b00-104">ISESnippetCollection-objektet</span><span class="sxs-lookup"><span data-stu-id="d5b00-104">The ISESnippetCollection Object</span></span>

<span data-ttu-id="d5b00-105">**ISESnippetCollection** -objektet är en samling av **ISESnippet** -objekt.</span><span class="sxs-lookup"><span data-stu-id="d5b00-105">The **ISESnippetCollection** object is a collection of **ISESnippet** objects.</span></span> <span data-ttu-id="d5b00-106">Den fil samling som är associerad med ett **PowerShellTab** -objekt är medlem i den här klassen.</span><span class="sxs-lookup"><span data-stu-id="d5b00-106">The files collection that is associated with a **PowerShellTab** object is a member of this class.</span></span> <span data-ttu-id="d5b00-107">Ett exempel är `$psISE.CurrentPowerShellTab.Files` samlingen.</span><span class="sxs-lookup"><span data-stu-id="d5b00-107">An example is the `$psISE.CurrentPowerShellTab.Files` collection.</span></span>

## <a name="methods"></a><span data-ttu-id="d5b00-108">Metoder</span><span class="sxs-lookup"><span data-stu-id="d5b00-108">Methods</span></span>

### <a name="load-filepathname-"></a><span data-ttu-id="d5b00-109">Läs in \( FilePathName \)</span><span class="sxs-lookup"><span data-stu-id="d5b00-109">Load\( FilePathName \)</span></span>

<span data-ttu-id="d5b00-110">Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="d5b00-110">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="d5b00-111">Läser in en `.snippets.ps1xml` fil som innehåller användardefinierade kod avsnitt.</span><span class="sxs-lookup"><span data-stu-id="d5b00-111">Loads a `.snippets.ps1xml` file that contains user-defined snippets.</span></span> <span data-ttu-id="d5b00-112">Det enklaste sättet att skapa kodfragment är att använda `New-IseSnippet` cmdleten, som automatiskt lagrar dem i din profilmappar så att de läses in varje gång som du startar Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="d5b00-112">The easiest way to create snippets is to use the `New-IseSnippet` cmdlet, which automatically stores them in your profile folder so that they are loaded every time that you start Windows PowerShell ISE.</span></span>

<span data-ttu-id="d5b00-113">**FilePathName** – sträng sökvägen och fil namnet till en .snippets.ps1XML-fil som innehåller definitions definitioner för kodfragment.</span><span class="sxs-lookup"><span data-stu-id="d5b00-113">**FilePathName** - String The path and file name to a .snippets.ps1xml file that contains snippet definitions.</span></span>

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a><span data-ttu-id="d5b00-114">Se även</span><span class="sxs-lookup"><span data-stu-id="d5b00-114">See Also</span></span>

- [<span data-ttu-id="d5b00-115">ISESnippetObject</span><span class="sxs-lookup"><span data-stu-id="d5b00-115">The ISESnippetObject</span></span>](The-ISESnippetObject.md)
- [<span data-ttu-id="d5b00-116">Användningsområden för Windows PowerShell ISE-skriptobjektmodellen</span><span class="sxs-lookup"><span data-stu-id="d5b00-116">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="d5b00-117">Objekt modells-hierarkin för ISE</span><span class="sxs-lookup"><span data-stu-id="d5b00-117">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
