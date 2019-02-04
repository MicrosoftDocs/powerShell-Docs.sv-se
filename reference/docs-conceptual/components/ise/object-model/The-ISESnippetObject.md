---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: ISESnippetObject
ms.assetid: 98bc8113-c3cd-4201-bdb9-9d9bdb7e266c
ms.openlocfilehash: f80080f4207cf226fb7466c4842446d08c081347
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685454"
---
# <a name="the-isesnippetobject"></a><span data-ttu-id="55d87-103">ISESnippetObject</span><span class="sxs-lookup"><span data-stu-id="55d87-103">The ISESnippetObject</span></span>

<span data-ttu-id="55d87-104">En **ISESnippet** objekt är en instans av klassen Microsoft.PowerShell.Host.ISE.ISESnippet.</span><span class="sxs-lookup"><span data-stu-id="55d87-104">An **ISESnippet** object is an instance of the Microsoft.PowerShell.Host.ISE.ISESnippet class.</span></span> <span data-ttu-id="55d87-105">Medlemmarna i den **$psISE.CurrentPowerShellTab.Snippets** samling är alla exempel på **ISESnippet** objekt.</span><span class="sxs-lookup"><span data-stu-id="55d87-105">The members of the **$psISE.CurrentPowerShellTab.Snippets** collection are all examples of **ISESnippet** objects.</span></span> <span data-ttu-id="55d87-106">Det enklaste sättet att skapa ett fragment är att använda den [New-IseSnippet&#91;PSITPro5_ISE&#93; ](https://technet.microsoft.com/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="55d87-106">The easiest way to create a snippet is to use the [New-IseSnippet&#91;PSITPro5_ISE&#93;](https://technet.microsoft.com/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) cmdlet.</span></span>

## <a name="properties"></a><span data-ttu-id="55d87-107">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="55d87-107">Properties</span></span>

### <a name="author"></a><span data-ttu-id="55d87-108">Författare</span><span class="sxs-lookup"><span data-stu-id="55d87-108">Author</span></span>

<span data-ttu-id="55d87-109">Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="55d87-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="55d87-110">Den skrivskyddade egenskapen som hämtar namnet på författaren kodfragmentet.</span><span class="sxs-lookup"><span data-stu-id="55d87-110">The read-only property that gets the name of the author of the snippet.</span></span>

```powershell
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author
```

### <a name="codefragment"></a><span data-ttu-id="55d87-111">CodeFragment</span><span class="sxs-lookup"><span data-stu-id="55d87-111">CodeFragment</span></span>

<span data-ttu-id="55d87-112">Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="55d87-112">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="55d87-113">Den skrivskyddade egenskapen som hämtar kodfragment som ska infogas i redigeraren.</span><span class="sxs-lookup"><span data-stu-id="55d87-113">The read-only property that gets the code fragment to be inserted into the editor.</span></span>

```powershell
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment
```

### <a name="shortcut"></a><span data-ttu-id="55d87-114">Genväg</span><span class="sxs-lookup"><span data-stu-id="55d87-114">Shortcut</span></span>

<span data-ttu-id="55d87-115">Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="55d87-115">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="55d87-116">Skrivskyddad egenskap som hämtar Windows kortkommando för menyalternativets.</span><span class="sxs-lookup"><span data-stu-id="55d87-116">The read-only property that gets the Windows keyboard shortcut for the menu item.</span></span>

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a><span data-ttu-id="55d87-117">Se även</span><span class="sxs-lookup"><span data-stu-id="55d87-117">See Also</span></span>

- [<span data-ttu-id="55d87-118">ISESnippetCollection-objektet</span><span class="sxs-lookup"><span data-stu-id="55d87-118">The ISESnippetCollection Object</span></span>](The-ISESnippetCollection-Object.md)
- [<span data-ttu-id="55d87-119">Syftet med den Windows PowerShell ISE-Skriptobjektmodellen</span><span class="sxs-lookup"><span data-stu-id="55d87-119">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](purpose-of-the-windows-powershell-ise-scripting-object-model.md)
- [<span data-ttu-id="55d87-120">Hierarki för ISE-objektmodellen</span><span class="sxs-lookup"><span data-stu-id="55d87-120">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)