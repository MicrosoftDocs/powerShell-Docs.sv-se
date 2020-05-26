---
ms.date: 12/31/2019
keywords: powershell,cmdlet
title: ISEAddOnToolCollection-objektet
ms.openlocfilehash: e07a47169381307b50ac190165307c926b4ad94e
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83811032"
---
# <a name="the-iseaddontoolcollection-object"></a><span data-ttu-id="63dca-103">ISEAddOnToolCollection-objektet</span><span class="sxs-lookup"><span data-stu-id="63dca-103">The ISEAddOnToolCollection Object</span></span>

<span data-ttu-id="63dca-104">**ISEAddOnToolCollection** -objektet är en samling av **ISEAddOnTool** -objekt.</span><span class="sxs-lookup"><span data-stu-id="63dca-104">The **ISEAddOnToolCollection** object is a collection of **ISEAddOnTool** objects.</span></span> <span data-ttu-id="63dca-105">Ett exempel är `$psISE.CurrentPowerShellTab.VerticalAddOnTools` objektet.</span><span class="sxs-lookup"><span data-stu-id="63dca-105">An example is the `$psISE.CurrentPowerShellTab.VerticalAddOnTools` object.</span></span>

## <a name="methods"></a><span data-ttu-id="63dca-106">Metoder</span><span class="sxs-lookup"><span data-stu-id="63dca-106">Methods</span></span>

### <a name="add-name-controltype-isvisible-"></a><span data-ttu-id="63dca-107">Lägg till \( namn, ControlType, \[ IsVisible \]\)</span><span class="sxs-lookup"><span data-stu-id="63dca-107">Add\( Name, ControlType, \[IsVisible\] \)</span></span>

<span data-ttu-id="63dca-108">Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="63dca-108">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="63dca-109">Lägger till ett nytt tilläggs verktyg i samlingen.</span><span class="sxs-lookup"><span data-stu-id="63dca-109">Adds a new add-on tool to the collection.</span></span> <span data-ttu-id="63dca-110">Det returnerar det nyligen tillagda tilläggs verktyget.</span><span class="sxs-lookup"><span data-stu-id="63dca-110">It returns the newly added add-on tool.</span></span> <span data-ttu-id="63dca-111">Innan du kör det här kommandot måste du installera tilläggs verktyget på den lokala datorn och läsa in sammansättningen.</span><span class="sxs-lookup"><span data-stu-id="63dca-111">Before you run this command, you must install the add-on tool on the local computer and load the assembly.</span></span>

<span data-ttu-id="63dca-112">**Name** -sträng anger visnings namnet för det tilläggs verktyg som läggs till Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="63dca-112">**Name** - String Specifies the display name of the add-on tool that is added to Windows PowerShell ISE.</span></span>

<span data-ttu-id="63dca-113">**ControlType** – typ anger den kontroll som läggs till.</span><span class="sxs-lookup"><span data-stu-id="63dca-113">**ControlType** -Type Specifies the control that is added.</span></span>

<span data-ttu-id="63dca-114">\*\* \[ IsVisible \] \*\* – valfria booleska om det är inställt på `$true` , visas tilläggs verktyget direkt i det associerade verktygs fönstret.</span><span class="sxs-lookup"><span data-stu-id="63dca-114">**\[IsVisible\]** - optional Boolean If set to `$true`, the add-on tool is immediately visible in the associated tool pane.</span></span>

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="remove-item-"></a><span data-ttu-id="63dca-115">Ta bort \( objekt\)</span><span class="sxs-lookup"><span data-stu-id="63dca-115">Remove\( Item \)</span></span>

<span data-ttu-id="63dca-116">Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="63dca-116">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="63dca-117">Tar bort det angivna tilläggs verktyget från samlingen.</span><span class="sxs-lookup"><span data-stu-id="63dca-117">Removes the specified add-on tool from the collection.</span></span>

<span data-ttu-id="63dca-118">**Objekt** -Microsoft. PowerShell. Host. ISE. ISEAddOnTool anger det objekt som ska tas bort från Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="63dca-118">**Item** - Microsoft.PowerShell.Host.ISE.ISEAddOnTool Specifies the object to be removed from Windows PowerShell ISE.</span></span>

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="setselectedpowershelltab-pstab-"></a><span data-ttu-id="63dca-119">SetSelectedPowerShellTab \( psTab\)</span><span class="sxs-lookup"><span data-stu-id="63dca-119">SetSelectedPowerShellTab\( psTab \)</span></span>

<span data-ttu-id="63dca-120">Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="63dca-120">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="63dca-121">Väljer PowerShell-fliken som **psTab** -parametern anger.</span><span class="sxs-lookup"><span data-stu-id="63dca-121">Selects the PowerShell tab that the **psTab** parameter specifies.</span></span>

<span data-ttu-id="63dca-122">**psTab** -Microsoft. PowerShell. Host. ISE. PowerShellTab på PowerShell-fliken för att välja.</span><span class="sxs-lookup"><span data-stu-id="63dca-122">**psTab** - Microsoft.PowerShell.Host.ISE.PowerShellTab The PowerShell tab to select.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="remove-pstab-"></a><span data-ttu-id="63dca-123">Ta bort \( psTab\)</span><span class="sxs-lookup"><span data-stu-id="63dca-123">Remove\( psTab \)</span></span>

<span data-ttu-id="63dca-124">Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="63dca-124">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="63dca-125">Tar bort PowerShell-fliken som **psTab** -parametern anger.</span><span class="sxs-lookup"><span data-stu-id="63dca-125">Removes the PowerShell tab that the **psTab** parameter specifies.</span></span>

<span data-ttu-id="63dca-126">**psTab** -Microsoft. PowerShell. Host. ISE. PowerShellTab på PowerShell-fliken för att ta bort.</span><span class="sxs-lookup"><span data-stu-id="63dca-126">**psTab** - Microsoft.PowerShell.Host.ISE.PowerShellTab The PowerShell tab to remove.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

## <a name="see-also"></a><span data-ttu-id="63dca-127">Se även</span><span class="sxs-lookup"><span data-stu-id="63dca-127">See Also</span></span>

- [<span data-ttu-id="63dca-128">PowerShellTab-objektet</span><span class="sxs-lookup"><span data-stu-id="63dca-128">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="63dca-129">Användningsområden för Windows PowerShell ISE-skriptobjektmodellen</span><span class="sxs-lookup"><span data-stu-id="63dca-129">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="63dca-130">Objekt modells-hierarkin för ISE</span><span class="sxs-lookup"><span data-stu-id="63dca-130">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
