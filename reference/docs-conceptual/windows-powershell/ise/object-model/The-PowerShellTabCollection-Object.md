---
ms.date: 06/05/2017
title: PowerShellTabCollection-objektet
description: PowerShellTab Collection-objektet är en samling PowerShellTab-objekt. Varje PowerShellTab-objekt fungerar som en separat körnings miljö.
ms.openlocfilehash: 60f8001f096b50bd8433a5685f1f70a350f07f61
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92658269"
---
# <a name="the-powershelltabcollection-object"></a><span data-ttu-id="b2cd7-104">PowerShellTabCollection-objektet</span><span class="sxs-lookup"><span data-stu-id="b2cd7-104">The PowerShellTabCollection Object</span></span>

<span data-ttu-id="b2cd7-105">**PowerShellTab** Collection-objektet är en samling **PowerShellTab** -objekt.</span><span class="sxs-lookup"><span data-stu-id="b2cd7-105">The **PowerShellTab** collection object is a collection of **PowerShellTab** objects.</span></span> <span data-ttu-id="b2cd7-106">Varje **PowerShellTab** -objekt fungerar som en separat körnings miljö.</span><span class="sxs-lookup"><span data-stu-id="b2cd7-106">Each **PowerShellTab** object functions as a separate runtime environment.</span></span> <span data-ttu-id="b2cd7-107">Det är en instans av klassen Microsoft. PowerShell. Host. ISE. PowerShellTabs.</span><span class="sxs-lookup"><span data-stu-id="b2cd7-107">It is an instance of Microsoft.PowerShell.Host.ISE.PowerShellTabs class.</span></span> <span data-ttu-id="b2cd7-108">Ett exempel är `$psISE.PowerShellTabs` objektet.</span><span class="sxs-lookup"><span data-stu-id="b2cd7-108">An example is the `$psISE.PowerShellTabs` object.</span></span>

## <a name="methods"></a><span data-ttu-id="b2cd7-109">Metoder</span><span class="sxs-lookup"><span data-stu-id="b2cd7-109">Methods</span></span>

### <a name="add"></a><span data-ttu-id="b2cd7-110">Skapa\(\)</span><span class="sxs-lookup"><span data-stu-id="b2cd7-110">Add\(\)</span></span>

<span data-ttu-id="b2cd7-111">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="b2cd7-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="b2cd7-112">Lägger till en ny PowerShell-flik i samlingen.</span><span class="sxs-lookup"><span data-stu-id="b2cd7-112">Adds a new PowerShell tab to the collection.</span></span> <span data-ttu-id="b2cd7-113">Den returnerar den nyligen tillagda fliken.</span><span class="sxs-lookup"><span data-stu-id="b2cd7-113">It returns the newly added tab.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="b2cd7-114">Ta bort \( Microsoft. PowerShell. Host. ISE. PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="b2cd7-114">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>

<span data-ttu-id="b2cd7-115">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="b2cd7-115">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="b2cd7-116">Tar bort den flik som anges av parametern **psTab** .</span><span class="sxs-lookup"><span data-stu-id="b2cd7-116">Removes the tab that is specified by the **psTab** parameter.</span></span>

<span data-ttu-id="b2cd7-117">**psTab** PowerShell-fliken som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="b2cd7-117">**psTab** The PowerShell tab to remove.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="b2cd7-118">SetSelectedPowerShellTab \( Microsoft. PowerShell. Host. ISE. PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="b2cd7-118">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>

<span data-ttu-id="b2cd7-119">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="b2cd7-119">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="b2cd7-120">Väljer den PowerShell-flik som anges av parametern **psTab** för att göra den till den aktuella aktiva PowerShell-fliken.</span><span class="sxs-lookup"><span data-stu-id="b2cd7-120">Selects the PowerShell tab that is specified by the **psTab** parameter to make it the currently active PowerShell tab.</span></span>

<span data-ttu-id="b2cd7-121">**psTab** På fliken PowerShell väljer du.</span><span class="sxs-lookup"><span data-stu-id="b2cd7-121">**psTab** The PowerShell tab to select.</span></span>

```powershell
# Save the current tab in a variable and rename it
$oldTab = $psISE.CurrentPowerShellTab
$psISE.CurrentPowerShellTab.DisplayName = 'Old Tab'
# Create a new tab and give it a new display name
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
# Switch back to the original tab
$psISE.PowerShellTabs.SelectedPowerShellTab = $oldTab
```

## <a name="see-also"></a><span data-ttu-id="b2cd7-122">Se även</span><span class="sxs-lookup"><span data-stu-id="b2cd7-122">See Also</span></span>

- [<span data-ttu-id="b2cd7-123">PowerShellTab-objektet</span><span class="sxs-lookup"><span data-stu-id="b2cd7-123">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="b2cd7-124">Användningsområden för Windows PowerShell ISE-skriptobjektmodellen</span><span class="sxs-lookup"><span data-stu-id="b2cd7-124">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="b2cd7-125">Objekt modells-hierarkin för ISE</span><span class="sxs-lookup"><span data-stu-id="b2cd7-125">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
