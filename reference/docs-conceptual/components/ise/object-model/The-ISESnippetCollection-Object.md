---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: ISESnippetCollection-objektet
ms.assetid: ae974955-4282-4cbc-8c42-0fff1904ef32
ms.openlocfilehash: bd5ed4a1f15e0a398b7c6a17f0071cad889be4a7
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53406013"
---
# <a name="the-isesnippetcollection-object"></a><span data-ttu-id="8104b-103">ISESnippetCollection-objektet</span><span class="sxs-lookup"><span data-stu-id="8104b-103">The ISESnippetCollection Object</span></span>

<span data-ttu-id="8104b-104">Den **ISESnippetCollection** objekt är en samling **ISESnippet** objekt.</span><span class="sxs-lookup"><span data-stu-id="8104b-104">The **ISESnippetCollection** object is a collection of **ISESnippet** objects.</span></span> <span data-ttu-id="8104b-105">Samlingen filer som är associerad med en **PowerShellTab** objektet är medlem i den här klassen.</span><span class="sxs-lookup"><span data-stu-id="8104b-105">The files collection that is associated with a **PowerShellTab** object is a member of this class.</span></span> <span data-ttu-id="8104b-106">Ett exempel är den **$psISE.CurrentPowerShellTab.Files** samling.</span><span class="sxs-lookup"><span data-stu-id="8104b-106">An example is the **$psISE.CurrentPowerShellTab.Files** collection.</span></span>

## <a name="methods"></a><span data-ttu-id="8104b-107">Metoder</span><span class="sxs-lookup"><span data-stu-id="8104b-107">Methods</span></span>

### <a name="load-filepathname-"></a><span data-ttu-id="8104b-108">Läs in\( FilePathName \)</span><span class="sxs-lookup"><span data-stu-id="8104b-108">Load\( FilePathName \)</span></span>

<span data-ttu-id="8104b-109">Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="8104b-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="8104b-110">Inläsningar en. snippets.ps1xml-fil som innehåller användardefinierade kodfragment.</span><span class="sxs-lookup"><span data-stu-id="8104b-110">Loads a .snippets.ps1xml file that contains user-defined snippets.</span></span> <span data-ttu-id="8104b-111">Det enklaste sättet att skapa kodfragment är att använda cmdleten New-IseSnippet, som automatiskt lagrar dem i profilmappen så att de har lästs in varje gång du startar Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="8104b-111">The easiest way to create snippets is to use the New-IseSnippet cmdlet, which automatically stores them in your profile folder so that they are loaded every time that you start Windows PowerShell ISE.</span></span>

<span data-ttu-id="8104b-112">**FilePathName** - sträng i sökväg och filnamn till en. snippets.ps1xml-filen som innehåller definitioner för kodfragment.</span><span class="sxs-lookup"><span data-stu-id="8104b-112">**FilePathName** - String The path and file name to a .snippets.ps1xml file that contains snippet definitions.</span></span>

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a><span data-ttu-id="8104b-113">Se även</span><span class="sxs-lookup"><span data-stu-id="8104b-113">See Also</span></span>

- [<span data-ttu-id="8104b-114">ISESnippetObject</span><span class="sxs-lookup"><span data-stu-id="8104b-114">The ISESnippetObject</span></span>](The-ISESnippetObject.md)
- [<span data-ttu-id="8104b-115">Syftet med den Windows PowerShell ISE-Skriptobjektmodellen</span><span class="sxs-lookup"><span data-stu-id="8104b-115">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="8104b-116">Hierarki för ISE-objektmodellen</span><span class="sxs-lookup"><span data-stu-id="8104b-116">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)