---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: ISESnippetCollection-objektet
ms.openlocfilehash: 6c392c08767fba004f63155d5a469777856a0b59
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030509"
---
# <a name="the-isesnippetcollection-object"></a><span data-ttu-id="dfc95-103">ISESnippetCollection-objektet</span><span class="sxs-lookup"><span data-stu-id="dfc95-103">The ISESnippetCollection Object</span></span>

<span data-ttu-id="dfc95-104">Den **ISESnippetCollection** objekt är en samling **ISESnippet** objekt.</span><span class="sxs-lookup"><span data-stu-id="dfc95-104">The **ISESnippetCollection** object is a collection of **ISESnippet** objects.</span></span> <span data-ttu-id="dfc95-105">Samlingen filer som är associerad med en **PowerShellTab** objektet är medlem i den här klassen.</span><span class="sxs-lookup"><span data-stu-id="dfc95-105">The files collection that is associated with a **PowerShellTab** object is a member of this class.</span></span> <span data-ttu-id="dfc95-106">Ett exempel är den **$psISE.CurrentPowerShellTab.Files** samling.</span><span class="sxs-lookup"><span data-stu-id="dfc95-106">An example is the **$psISE.CurrentPowerShellTab.Files** collection.</span></span>

## <a name="methods"></a><span data-ttu-id="dfc95-107">Metoder</span><span class="sxs-lookup"><span data-stu-id="dfc95-107">Methods</span></span>

### <a name="load-filepathname-"></a><span data-ttu-id="dfc95-108">Load\( FilePathName \)</span><span class="sxs-lookup"><span data-stu-id="dfc95-108">Load\( FilePathName \)</span></span>

<span data-ttu-id="dfc95-109">Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="dfc95-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="dfc95-110">Inläsningar en. snippets.ps1xml-fil som innehåller användardefinierade kodfragment.</span><span class="sxs-lookup"><span data-stu-id="dfc95-110">Loads a .snippets.ps1xml file that contains user-defined snippets.</span></span> <span data-ttu-id="dfc95-111">Det enklaste sättet att skapa kodfragment är att använda cmdleten New-IseSnippet, som automatiskt lagrar dem i profilmappen så att de har lästs in varje gång du startar Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="dfc95-111">The easiest way to create snippets is to use the New-IseSnippet cmdlet, which automatically stores them in your profile folder so that they are loaded every time that you start Windows PowerShell ISE.</span></span>

<span data-ttu-id="dfc95-112">**FilePathName** - sträng i sökväg och filnamn till en. snippets.ps1xml-filen som innehåller definitioner för kodfragment.</span><span class="sxs-lookup"><span data-stu-id="dfc95-112">**FilePathName** - String The path and file name to a .snippets.ps1xml file that contains snippet definitions.</span></span>

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a><span data-ttu-id="dfc95-113">Se även</span><span class="sxs-lookup"><span data-stu-id="dfc95-113">See Also</span></span>

- [<span data-ttu-id="dfc95-114">The ISESnippetObject</span><span class="sxs-lookup"><span data-stu-id="dfc95-114">The ISESnippetObject</span></span>](The-ISESnippetObject.md)
- [<span data-ttu-id="dfc95-115">Syftet med den Windows PowerShell ISE-Skriptobjektmodellen</span><span class="sxs-lookup"><span data-stu-id="dfc95-115">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="dfc95-116">Hierarki för ISE-objektmodellen</span><span class="sxs-lookup"><span data-stu-id="dfc95-116">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
