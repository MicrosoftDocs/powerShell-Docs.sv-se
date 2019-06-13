---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: PowerShellTabCollection-objektet
ms.openlocfilehash: 5a1318534ddce19c2f5faa0d2013e2b38d8b79e5
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030487"
---
# <a name="the-powershelltabcollection-object"></a><span data-ttu-id="d5839-103">PowerShellTabCollection-objektet</span><span class="sxs-lookup"><span data-stu-id="d5839-103">The PowerShellTabCollection Object</span></span>

<span data-ttu-id="d5839-104">Den **PowerShellTab** samlingsobjektet är en samling **PowerShellTab** objekt.</span><span class="sxs-lookup"><span data-stu-id="d5839-104">The **PowerShellTab** collection object is a collection of **PowerShellTab** objects.</span></span> <span data-ttu-id="d5839-105">Varje **PowerShellTab** objektet fungerar som en separat körningsmiljö.</span><span class="sxs-lookup"><span data-stu-id="d5839-105">Each **PowerShellTab** object functions as a separate runtime environment.</span></span> <span data-ttu-id="d5839-106">Det är en instans av klassen Microsoft.PowerShell.Host.ISE.PowerShellTabs.</span><span class="sxs-lookup"><span data-stu-id="d5839-106">It is an instance of Microsoft.PowerShell.Host.ISE.PowerShellTabs class.</span></span> <span data-ttu-id="d5839-107">Ett exempel är den **$psISE.PowerShellTabs** objekt.</span><span class="sxs-lookup"><span data-stu-id="d5839-107">An example is the **$psISE.PowerShellTabs** object.</span></span>

## <a name="methods"></a><span data-ttu-id="d5839-108">Metoder</span><span class="sxs-lookup"><span data-stu-id="d5839-108">Methods</span></span>

### <a name="add"></a><span data-ttu-id="d5839-109">Lägg till\(\)</span><span class="sxs-lookup"><span data-stu-id="d5839-109">Add\(\)</span></span>

<span data-ttu-id="d5839-110">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="d5839-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d5839-111">Lägger till en ny PowerShell-flik i samlingen.</span><span class="sxs-lookup"><span data-stu-id="d5839-111">Adds a new PowerShell tab to the collection.</span></span> <span data-ttu-id="d5839-112">Returnerar den nya fliken.</span><span class="sxs-lookup"><span data-stu-id="d5839-112">It returns the newly added tab.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="d5839-113">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="d5839-113">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>

<span data-ttu-id="d5839-114">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="d5839-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d5839-115">Tar bort fliken som anges av den **psTab** parametern.</span><span class="sxs-lookup"><span data-stu-id="d5839-115">Removes the tab that is specified by the **psTab** parameter.</span></span>

<span data-ttu-id="d5839-116">**psTab** PowerShell-flik för att ta bort.</span><span class="sxs-lookup"><span data-stu-id="d5839-116">**psTab** The PowerShell tab to remove.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="d5839-117">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="d5839-117">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>

<span data-ttu-id="d5839-118">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="d5839-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d5839-119">Väljer fliken PowerShell som anges av den **psTab** parametern så att de blir aktiva PowerShell-flik.</span><span class="sxs-lookup"><span data-stu-id="d5839-119">Selects the PowerShell tab that is specified by the **psTab** parameter to make it the currently active PowerShell tab.</span></span>

<span data-ttu-id="d5839-120">**psTab** PowerShell-fliken väljer.</span><span class="sxs-lookup"><span data-stu-id="d5839-120">**psTab** The PowerShell tab to select.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d5839-121">Se även</span><span class="sxs-lookup"><span data-stu-id="d5839-121">See Also</span></span>

- [<span data-ttu-id="d5839-122">The PowerShellTab Object</span><span class="sxs-lookup"><span data-stu-id="d5839-122">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="d5839-123">Syftet med den Windows PowerShell ISE-Skriptobjektmodellen</span><span class="sxs-lookup"><span data-stu-id="d5839-123">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="d5839-124">Hierarki för ISE-objektmodellen</span><span class="sxs-lookup"><span data-stu-id="d5839-124">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
