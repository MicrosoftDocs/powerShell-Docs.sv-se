---
ms.date: 06/05/2017
title: ISESnippetObject
description: Ett ISESnippet-objekt är en instans av klassen Microsoft. PowerShell. Host. ISE. ISESnippet.
ms.openlocfilehash: 602b344686cbcfb1e994914d4e26438ff7e4b1de
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92663400"
---
# <a name="the-isesnippetobject"></a><span data-ttu-id="d0c79-103">ISESnippetObject</span><span class="sxs-lookup"><span data-stu-id="d0c79-103">The ISESnippetObject</span></span>

<span data-ttu-id="d0c79-104">Ett **ISESnippet** -objekt är en instans av klassen Microsoft. PowerShell. Host. ISE. ISESnippet.</span><span class="sxs-lookup"><span data-stu-id="d0c79-104">An **ISESnippet** object is an instance of the Microsoft.PowerShell.Host.ISE.ISESnippet class.</span></span> <span data-ttu-id="d0c79-105">Medlemmarna i `$psISE.CurrentPowerShellTab.Snippets` samlingen är alla exempel på **ISESnippet** -objekt.</span><span class="sxs-lookup"><span data-stu-id="d0c79-105">The members of the `$psISE.CurrentPowerShellTab.Snippets` collection are all examples of **ISESnippet** objects.</span></span> <span data-ttu-id="d0c79-106">Det enklaste sättet att skapa ett kodfragment är att använda cmdleten [New-IseSnippet](/powershell/module/ISE/New-IseSnippet) .</span><span class="sxs-lookup"><span data-stu-id="d0c79-106">The easiest way to create a snippet is to use the [New-IseSnippet](/powershell/module/ISE/New-IseSnippet) cmdlet.</span></span>

## <a name="properties"></a><span data-ttu-id="d0c79-107">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="d0c79-107">Properties</span></span>

### <a name="author"></a><span data-ttu-id="d0c79-108">Författare</span><span class="sxs-lookup"><span data-stu-id="d0c79-108">Author</span></span>

<span data-ttu-id="d0c79-109">Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="d0c79-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="d0c79-110">Den skrivskyddade egenskapen som hämtar namnet på författaren till kodfragmentet.</span><span class="sxs-lookup"><span data-stu-id="d0c79-110">The read-only property that gets the name of the author of the snippet.</span></span>

```powershell
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author
```

### <a name="codefragment"></a><span data-ttu-id="d0c79-111">Defragmentera</span><span class="sxs-lookup"><span data-stu-id="d0c79-111">CodeFragment</span></span>

<span data-ttu-id="d0c79-112">Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="d0c79-112">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="d0c79-113">Den skrivskyddade egenskapen som hämtar kodfragmentet som ska infogas i redigeraren.</span><span class="sxs-lookup"><span data-stu-id="d0c79-113">The read-only property that gets the code fragment to be inserted into the editor.</span></span>

```powershell
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment
```

### <a name="shortcut"></a><span data-ttu-id="d0c79-114">Genvägar</span><span class="sxs-lookup"><span data-stu-id="d0c79-114">Shortcut</span></span>

<span data-ttu-id="d0c79-115">Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="d0c79-115">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="d0c79-116">Den skrivskyddade egenskapen som hämtar Windows-kortkommandon för meny alternativet.</span><span class="sxs-lookup"><span data-stu-id="d0c79-116">The read-only property that gets the Windows keyboard shortcut for the menu item.</span></span>

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a><span data-ttu-id="d0c79-117">Se även</span><span class="sxs-lookup"><span data-stu-id="d0c79-117">See Also</span></span>

- [<span data-ttu-id="d0c79-118">ISESnippetCollection-objektet</span><span class="sxs-lookup"><span data-stu-id="d0c79-118">The ISESnippetCollection Object</span></span>](The-ISESnippetCollection-Object.md)
- [<span data-ttu-id="d0c79-119">Användningsområden för Windows PowerShell ISE-skriptobjektmodellen</span><span class="sxs-lookup"><span data-stu-id="d0c79-119">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](purpose-of-the-windows-powershell-ise-scripting-object-model.md)
- [<span data-ttu-id="d0c79-120">Objekt modells-hierarkin för ISE</span><span class="sxs-lookup"><span data-stu-id="d0c79-120">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
