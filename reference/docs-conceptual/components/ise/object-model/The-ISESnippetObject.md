---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: ISESnippetObject
ms.openlocfilehash: 62d470569deb051fca80005235d4c492319cf5ec
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "67028881"
---
# <a name="the-isesnippetobject"></a><span data-ttu-id="e824e-103">ISESnippetObject</span><span class="sxs-lookup"><span data-stu-id="e824e-103">The ISESnippetObject</span></span>

<span data-ttu-id="e824e-104">Ett **ISESnippet** -objekt är en instans av klassen Microsoft. PowerShell. Host. ISE. ISESnippet.</span><span class="sxs-lookup"><span data-stu-id="e824e-104">An **ISESnippet** object is an instance of the Microsoft.PowerShell.Host.ISE.ISESnippet class.</span></span> <span data-ttu-id="e824e-105">Medlemmarna i samlingen **$psISE. CurrentPowerShellTab. Fragments** är alla exempel på **ISESnippet** -objekt.</span><span class="sxs-lookup"><span data-stu-id="e824e-105">The members of the **$psISE.CurrentPowerShellTab.Snippets** collection are all examples of **ISESnippet** objects.</span></span> <span data-ttu-id="e824e-106">Det enklaste sättet att skapa ett kodfragment är att använda cmdleten [New-&#91;IseSnippet&#93; PSITPro5_ISE](https://technet.microsoft.com/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) .</span><span class="sxs-lookup"><span data-stu-id="e824e-106">The easiest way to create a snippet is to use the [New-IseSnippet&#91;PSITPro5_ISE&#93;](https://technet.microsoft.com/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) cmdlet.</span></span>

## <a name="properties"></a><span data-ttu-id="e824e-107">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="e824e-107">Properties</span></span>

### <a name="author"></a><span data-ttu-id="e824e-108">Författare</span><span class="sxs-lookup"><span data-stu-id="e824e-108">Author</span></span>

<span data-ttu-id="e824e-109">Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="e824e-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="e824e-110">Den skrivskyddade egenskapen som hämtar namnet på författaren till kodfragmentet.</span><span class="sxs-lookup"><span data-stu-id="e824e-110">The read-only property that gets the name of the author of the snippet.</span></span>

```powershell
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author
```

### <a name="codefragment"></a><span data-ttu-id="e824e-111">Defragmentera</span><span class="sxs-lookup"><span data-stu-id="e824e-111">CodeFragment</span></span>

<span data-ttu-id="e824e-112">Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="e824e-112">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="e824e-113">Den skrivskyddade egenskapen som hämtar kodfragmentet som ska infogas i redigeraren.</span><span class="sxs-lookup"><span data-stu-id="e824e-113">The read-only property that gets the code fragment to be inserted into the editor.</span></span>

```powershell
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment
```

### <a name="shortcut"></a><span data-ttu-id="e824e-114">Genvägar</span><span class="sxs-lookup"><span data-stu-id="e824e-114">Shortcut</span></span>

<span data-ttu-id="e824e-115">Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="e824e-115">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="e824e-116">Den skrivskyddade egenskapen som hämtar Windows-kortkommandon för meny alternativet.</span><span class="sxs-lookup"><span data-stu-id="e824e-116">The read-only property that gets the Windows keyboard shortcut for the menu item.</span></span>

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a><span data-ttu-id="e824e-117">Se även</span><span class="sxs-lookup"><span data-stu-id="e824e-117">See Also</span></span>

- [<span data-ttu-id="e824e-118">ISESnippetCollection-objektet</span><span class="sxs-lookup"><span data-stu-id="e824e-118">The ISESnippetCollection Object</span></span>](The-ISESnippetCollection-Object.md)
- [<span data-ttu-id="e824e-119">Syftet med Windows PowerShell ISE-skriptets objekt modell</span><span class="sxs-lookup"><span data-stu-id="e824e-119">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](purpose-of-the-windows-powershell-ise-scripting-object-model.md)
- [<span data-ttu-id="e824e-120">Hierarki för ISE-objektmodellen</span><span class="sxs-lookup"><span data-stu-id="e824e-120">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
