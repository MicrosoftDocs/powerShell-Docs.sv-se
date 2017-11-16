---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: ISESnippetObject
ms.assetid: 98bc8113-c3cd-4201-bdb9-9d9bdb7e266c
ms.openlocfilehash: 6112f5252d2d1e868092da4a6cd04feb1875b597
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/31/2017
---
# <a name="the-isesnippetobject"></a><span data-ttu-id="8afb9-103">ISESnippetObject</span><span class="sxs-lookup"><span data-stu-id="8afb9-103">The ISESnippetObject</span></span>
  <span data-ttu-id="8afb9-104">En **ISESnippet** objekt är en instans av klassen Microsoft.PowerShell.Host.ISE.ISESnippet.</span><span class="sxs-lookup"><span data-stu-id="8afb9-104">An **ISESnippet** object is an instance of the Microsoft.PowerShell.Host.ISE.ISESnippet class.</span></span> <span data-ttu-id="8afb9-105">Medlemmarna i den **$psISE.CurrentPowerShellTab.Snippets** samling är alla exempel på **ISESnippet** objekt.</span><span class="sxs-lookup"><span data-stu-id="8afb9-105">The members of the **$psISE.CurrentPowerShellTab.Snippets** collection are all examples of **ISESnippet** objects.</span></span> <span data-ttu-id="8afb9-106">Det enklaste sättet att skapa en fragment är att använda den [ny IseSnippet & #91. PSITPro5_ISE & #93. ](https://technet.microsoft.com/en-us/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8afb9-106">The easiest way to create a snippet is to use the [New-IseSnippet&#91;PSITPro5_ISE&#93;](https://technet.microsoft.com/en-us/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) cmdlet.</span></span>

## <a name="properties"></a><span data-ttu-id="8afb9-107">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="8afb9-107">Properties</span></span>

### <a name="author"></a><span data-ttu-id="8afb9-108">författare</span><span class="sxs-lookup"><span data-stu-id="8afb9-108">Author</span></span>
  <span data-ttu-id="8afb9-109">Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="8afb9-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="8afb9-110">Den skrivskyddade egenskapen som hämtar namnet på författare för kodavsnittet.</span><span class="sxs-lookup"><span data-stu-id="8afb9-110">The read-only property that gets the name of the author of the snippet.</span></span>

```
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author

```

### <a name="codefragment"></a><span data-ttu-id="8afb9-111">CodeFragment</span><span class="sxs-lookup"><span data-stu-id="8afb9-111">CodeFragment</span></span>
  <span data-ttu-id="8afb9-112">Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="8afb9-112">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="8afb9-113">Den skrivskyddade egenskapen som hämtar koden som ska infogas i redigeraren.</span><span class="sxs-lookup"><span data-stu-id="8afb9-113">The read-only property that gets the code fragment to be inserted into the editor.</span></span>

```
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment

```

### <a name="shortcut"></a><span data-ttu-id="8afb9-114">Genväg</span><span class="sxs-lookup"><span data-stu-id="8afb9-114">Shortcut</span></span>
  <span data-ttu-id="8afb9-115">Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="8afb9-115">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="8afb9-116">Skrivskyddad egenskap som hämtar Windows kortkommando för menyalternativet.</span><span class="sxs-lookup"><span data-stu-id="8afb9-116">The read-only property that gets the Windows keyboard shortcut for the menu item.</span></span>

```
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a><span data-ttu-id="8afb9-117">Se även</span><span class="sxs-lookup"><span data-stu-id="8afb9-117">See Also</span></span>
- [<span data-ttu-id="8afb9-118">Objektet ISESnippetCollection</span><span class="sxs-lookup"><span data-stu-id="8afb9-118">The ISESnippetCollection Object</span></span>](The-ISESnippetCollection-Object.md) 
- [<span data-ttu-id="8afb9-119">Windows PowerShell ISE Scripting Object Model</span><span class="sxs-lookup"><span data-stu-id="8afb9-119">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="8afb9-120">Windows PowerShell ISE objektreferens modellen</span><span class="sxs-lookup"><span data-stu-id="8afb9-120">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="8afb9-121">Modellen objekthierarkin ISE</span><span class="sxs-lookup"><span data-stu-id="8afb9-121">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

  
