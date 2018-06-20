---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: ISESnippetCollection-objektet
ms.assetid: ae974955-4282-4cbc-8c42-0fff1904ef32
ms.openlocfilehash: bd5ed4a1f15e0a398b7c6a17f0071cad889be4a7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
ms.locfileid: "30950958"
---
# <a name="the-isesnippetcollection-object"></a><span data-ttu-id="84bbe-103">ISESnippetCollection-objektet</span><span class="sxs-lookup"><span data-stu-id="84bbe-103">The ISESnippetCollection Object</span></span>

<span data-ttu-id="84bbe-104">Den **ISESnippetCollection** objekt är en samling **ISESnippet** objekt.</span><span class="sxs-lookup"><span data-stu-id="84bbe-104">The **ISESnippetCollection** object is a collection of **ISESnippet** objects.</span></span> <span data-ttu-id="84bbe-105">Samlingen filer som är associerad med en **PowerShellTab** objektet är medlem i den här klassen.</span><span class="sxs-lookup"><span data-stu-id="84bbe-105">The files collection that is associated with a **PowerShellTab** object is a member of this class.</span></span> <span data-ttu-id="84bbe-106">Ett exempel är den **$psISE.CurrentPowerShellTab.Files** samling.</span><span class="sxs-lookup"><span data-stu-id="84bbe-106">An example is the **$psISE.CurrentPowerShellTab.Files** collection.</span></span>

## <a name="methods"></a><span data-ttu-id="84bbe-107">Metoder</span><span class="sxs-lookup"><span data-stu-id="84bbe-107">Methods</span></span>

### <a name="load-filepathname-"></a><span data-ttu-id="84bbe-108">Läs in\( FilePathName \)</span><span class="sxs-lookup"><span data-stu-id="84bbe-108">Load\( FilePathName \)</span></span>

<span data-ttu-id="84bbe-109">Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="84bbe-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="84bbe-110">Belastningar en. snippets.ps1xml-fil som innehåller användardefinierade kodavsnitt.</span><span class="sxs-lookup"><span data-stu-id="84bbe-110">Loads a .snippets.ps1xml file that contains user-defined snippets.</span></span> <span data-ttu-id="84bbe-111">Det enklaste sättet att skapa kodavsnitt är att använda cmdlet New-IseSnippet, som lagrar dem automatiskt i profilmappen så att de har lästs in varje gång du startar Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="84bbe-111">The easiest way to create snippets is to use the New-IseSnippet cmdlet, which automatically stores them in your profile folder so that they are loaded every time that you start Windows PowerShell ISE.</span></span>

<span data-ttu-id="84bbe-112">**FilePathName** - sträng sökväg och filnamn till en. snippets.ps1xml-filen som innehåller kodavsnitt definitioner.</span><span class="sxs-lookup"><span data-stu-id="84bbe-112">**FilePathName** - String The path and file name to a .snippets.ps1xml file that contains snippet definitions.</span></span>

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a><span data-ttu-id="84bbe-113">Se även</span><span class="sxs-lookup"><span data-stu-id="84bbe-113">See Also</span></span>

- [<span data-ttu-id="84bbe-114">ISESnippetObject</span><span class="sxs-lookup"><span data-stu-id="84bbe-114">The ISESnippetObject</span></span>](The-ISESnippetObject.md)
- [<span data-ttu-id="84bbe-115">Syftet med Windows PowerShell ISE Scripting Object Model</span><span class="sxs-lookup"><span data-stu-id="84bbe-115">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="84bbe-116">Hierarki för ISE-objektmodellen</span><span class="sxs-lookup"><span data-stu-id="84bbe-116">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)