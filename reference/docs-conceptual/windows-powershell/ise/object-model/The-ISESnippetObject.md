---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: ISESnippetObject
ms.openlocfilehash: f810e6b26f0ded04be15bdc37f336d7890e29dad
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83810934"
---
# <a name="the-isesnippetobject"></a><span data-ttu-id="5cf87-103">ISESnippetObject</span><span class="sxs-lookup"><span data-stu-id="5cf87-103">The ISESnippetObject</span></span>

<span data-ttu-id="5cf87-104">Ett **ISESnippet** -objekt är en instans av klassen Microsoft. PowerShell. Host. ISE. ISESnippet.</span><span class="sxs-lookup"><span data-stu-id="5cf87-104">An **ISESnippet** object is an instance of the Microsoft.PowerShell.Host.ISE.ISESnippet class.</span></span> <span data-ttu-id="5cf87-105">Medlemmarna i `$psISE.CurrentPowerShellTab.Snippets` samlingen är alla exempel på **ISESnippet** -objekt.</span><span class="sxs-lookup"><span data-stu-id="5cf87-105">The members of the `$psISE.CurrentPowerShellTab.Snippets` collection are all examples of **ISESnippet** objects.</span></span> <span data-ttu-id="5cf87-106">Det enklaste sättet att skapa ett kodfragment är att använda cmdleten [New-IseSnippet](/powershell/module/ISE/New-IseSnippet) .</span><span class="sxs-lookup"><span data-stu-id="5cf87-106">The easiest way to create a snippet is to use the [New-IseSnippet](/powershell/module/ISE/New-IseSnippet) cmdlet.</span></span>

## <a name="properties"></a><span data-ttu-id="5cf87-107">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="5cf87-107">Properties</span></span>

### <a name="author"></a><span data-ttu-id="5cf87-108">Författare</span><span class="sxs-lookup"><span data-stu-id="5cf87-108">Author</span></span>

<span data-ttu-id="5cf87-109">Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="5cf87-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="5cf87-110">Den skrivskyddade egenskapen som hämtar namnet på författaren till kodfragmentet.</span><span class="sxs-lookup"><span data-stu-id="5cf87-110">The read-only property that gets the name of the author of the snippet.</span></span>

```powershell
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author
```

### <a name="codefragment"></a><span data-ttu-id="5cf87-111">Defragmentera</span><span class="sxs-lookup"><span data-stu-id="5cf87-111">CodeFragment</span></span>

<span data-ttu-id="5cf87-112">Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="5cf87-112">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="5cf87-113">Den skrivskyddade egenskapen som hämtar kodfragmentet som ska infogas i redigeraren.</span><span class="sxs-lookup"><span data-stu-id="5cf87-113">The read-only property that gets the code fragment to be inserted into the editor.</span></span>

```powershell
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment
```

### <a name="shortcut"></a><span data-ttu-id="5cf87-114">Genvägar</span><span class="sxs-lookup"><span data-stu-id="5cf87-114">Shortcut</span></span>

<span data-ttu-id="5cf87-115">Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="5cf87-115">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="5cf87-116">Den skrivskyddade egenskapen som hämtar Windows-kortkommandon för meny alternativet.</span><span class="sxs-lookup"><span data-stu-id="5cf87-116">The read-only property that gets the Windows keyboard shortcut for the menu item.</span></span>

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a><span data-ttu-id="5cf87-117">Se även</span><span class="sxs-lookup"><span data-stu-id="5cf87-117">See Also</span></span>

- [<span data-ttu-id="5cf87-118">ISESnippetCollection-objektet</span><span class="sxs-lookup"><span data-stu-id="5cf87-118">The ISESnippetCollection Object</span></span>](The-ISESnippetCollection-Object.md)
- [<span data-ttu-id="5cf87-119">Användningsområden för Windows PowerShell ISE-skriptobjektmodellen</span><span class="sxs-lookup"><span data-stu-id="5cf87-119">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](purpose-of-the-windows-powershell-ise-scripting-object-model.md)
- [<span data-ttu-id="5cf87-120">Objekt modells-hierarkin för ISE</span><span class="sxs-lookup"><span data-stu-id="5cf87-120">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
