---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Objektet ISESnippetCollection
ms.assetid: ae974955-4282-4cbc-8c42-0fff1904ef32
ms.openlocfilehash: b19c5b5c88f7c8bd0d0c466c7861fa9288bdc7a2
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/03/2017
---
# <a name="the-isesnippetcollection-object"></a><span data-ttu-id="3e785-103">Objektet ISESnippetCollection</span><span class="sxs-lookup"><span data-stu-id="3e785-103">The ISESnippetCollection Object</span></span>
  <span data-ttu-id="3e785-104">Den **ISESnippetCollection** objekt är en samling **ISESnippet** objekt.</span><span class="sxs-lookup"><span data-stu-id="3e785-104">The **ISESnippetCollection** object is a collection of **ISESnippet** objects.</span></span> <span data-ttu-id="3e785-105">Samlingen filer som är associerad med en **PowerShellTab** objektet är medlem i den här klassen.</span><span class="sxs-lookup"><span data-stu-id="3e785-105">The files collection that is associated with a **PowerShellTab** object is a member of this class.</span></span> <span data-ttu-id="3e785-106">Ett exempel är den **$psISE.CurrentPowerShellTab.Files** samling.</span><span class="sxs-lookup"><span data-stu-id="3e785-106">An example is the **$psISE.CurrentPowerShellTab.Files** collection.</span></span>

## <a name="methods"></a><span data-ttu-id="3e785-107">Metoder</span><span class="sxs-lookup"><span data-stu-id="3e785-107">Methods</span></span>

### <a name="load-filepathname-"></a><span data-ttu-id="3e785-108">Läs in\( FilePathName\)</span><span class="sxs-lookup"><span data-stu-id="3e785-108">Load\( FilePathName \)</span></span>
  <span data-ttu-id="3e785-109">Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="3e785-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="3e785-110">Belastningar en. snippets.ps1xml-fil som innehåller användardefinierade kodavsnitt.</span><span class="sxs-lookup"><span data-stu-id="3e785-110">Loads a .snippets.ps1xml file that contains user-defined snippets.</span></span> <span data-ttu-id="3e785-111">Det enklaste sättet att skapa kodavsnitt är att använda cmdlet New-IseSnippet, som lagrar dem automatiskt i profilmappen så att de har lästs in varje gång du startar Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="3e785-111">The easiest way to create snippets is to use the New-IseSnippet cmdlet, which automatically stores them in your profile folder so that they are loaded every time that you start Windows PowerShell ISE.</span></span>

 <span data-ttu-id="3e785-112">**FilePathName** - sträng sökväg och filnamn till en. snippets.ps1xml-filen som innehåller kodavsnitt definitioner.</span><span class="sxs-lookup"><span data-stu-id="3e785-112">**FilePathName** - String The path and file name to a .snippets.ps1xml file that contains snippet definitions.</span></span>

```
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) “Snippets\MySnips.snippets.ps1xml” $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)

```

## <a name="see-also"></a><span data-ttu-id="3e785-113">Se även</span><span class="sxs-lookup"><span data-stu-id="3e785-113">See Also</span></span>
- [<span data-ttu-id="3e785-114">ISESnippetObject</span><span class="sxs-lookup"><span data-stu-id="3e785-114">The ISESnippetObject</span></span>](The-ISESnippetObject.md) 
- [<span data-ttu-id="3e785-115">Windows PowerShell ISE Scripting Object Model</span><span class="sxs-lookup"><span data-stu-id="3e785-115">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="3e785-116">Windows PowerShell ISE objektreferens modellen</span><span class="sxs-lookup"><span data-stu-id="3e785-116">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="3e785-117">Modellen objekthierarkin ISE</span><span class="sxs-lookup"><span data-stu-id="3e785-117">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

  
