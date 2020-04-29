---
ms.date: 12/31/2019
keywords: PowerShell, cmdlet
title: ISESnippetCollection-objektet
ms.openlocfilehash: 6cdc43dd1d82e94f66122d7f7b313c02e755fed7
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "75736053"
---
# <a name="the-isesnippetcollection-object"></a><span data-ttu-id="03459-103">ISESnippetCollection-objektet</span><span class="sxs-lookup"><span data-stu-id="03459-103">The ISESnippetCollection Object</span></span>

<span data-ttu-id="03459-104">**ISESnippetCollection** -objektet är en samling av **ISESnippet** -objekt.</span><span class="sxs-lookup"><span data-stu-id="03459-104">The **ISESnippetCollection** object is a collection of **ISESnippet** objects.</span></span> <span data-ttu-id="03459-105">Den fil samling som är associerad med ett **PowerShellTab** -objekt är medlem i den här klassen.</span><span class="sxs-lookup"><span data-stu-id="03459-105">The files collection that is associated with a **PowerShellTab** object is a member of this class.</span></span> <span data-ttu-id="03459-106">Ett exempel är `$psISE.CurrentPowerShellTab.Files` samlingen.</span><span class="sxs-lookup"><span data-stu-id="03459-106">An example is the `$psISE.CurrentPowerShellTab.Files` collection.</span></span>

## <a name="methods"></a><span data-ttu-id="03459-107">Metoder</span><span class="sxs-lookup"><span data-stu-id="03459-107">Methods</span></span>

### <a name="load-filepathname-"></a><span data-ttu-id="03459-108">Läs\( in FilePathName\)</span><span class="sxs-lookup"><span data-stu-id="03459-108">Load\( FilePathName \)</span></span>

<span data-ttu-id="03459-109">Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="03459-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="03459-110">Läser in `.snippets.ps1xml` en fil som innehåller användardefinierade kod avsnitt.</span><span class="sxs-lookup"><span data-stu-id="03459-110">Loads a `.snippets.ps1xml` file that contains user-defined snippets.</span></span> <span data-ttu-id="03459-111">Det enklaste sättet att skapa kodfragment är att använda `New-IseSnippet` cmdleten, som automatiskt lagrar dem i din profilmappar så att de läses in varje gång som du startar Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="03459-111">The easiest way to create snippets is to use the `New-IseSnippet` cmdlet, which automatically stores them in your profile folder so that they are loaded every time that you start Windows PowerShell ISE.</span></span>

<span data-ttu-id="03459-112">**FilePathName** -sträng med sökvägen och fil namnet till en. ps1xml-fil som innehåller kod avsnitts definitioner.</span><span class="sxs-lookup"><span data-stu-id="03459-112">**FilePathName** - String The path and file name to a .snippets.ps1xml file that contains snippet definitions.</span></span>

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a><span data-ttu-id="03459-113">Se även</span><span class="sxs-lookup"><span data-stu-id="03459-113">See Also</span></span>

- [<span data-ttu-id="03459-114">ISESnippetObject</span><span class="sxs-lookup"><span data-stu-id="03459-114">The ISESnippetObject</span></span>](The-ISESnippetObject.md)
- [<span data-ttu-id="03459-115">Användningsområden för Windows PowerShell ISE-skriptobjektmodellen</span><span class="sxs-lookup"><span data-stu-id="03459-115">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="03459-116">Objekt modells-hierarkin för ISE</span><span class="sxs-lookup"><span data-stu-id="03459-116">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
