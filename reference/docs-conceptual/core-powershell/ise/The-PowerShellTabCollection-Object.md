---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Objektet PowerShellTabCollection
ms.assetid: 81f4bf4a-83bf-415e-8378-1703792fbb58
ms.openlocfilehash: dcdc16ae126453b6ade64917ac4950cc05e5f8ad
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/03/2017
---
# <a name="the-powershelltabcollection-object"></a><span data-ttu-id="0854a-103">Objektet PowerShellTabCollection</span><span class="sxs-lookup"><span data-stu-id="0854a-103">The PowerShellTabCollection Object</span></span>
  <span data-ttu-id="0854a-104">Den **PowerShellTab** samlingsobjektet är en samling **PowerShellTab** objekt.</span><span class="sxs-lookup"><span data-stu-id="0854a-104">The **PowerShellTab** collection object is a collection of **PowerShellTab** objects.</span></span> <span data-ttu-id="0854a-105">Varje **PowerShellTab** objekt som fungerar som en separat körningsmiljö.</span><span class="sxs-lookup"><span data-stu-id="0854a-105">Each **PowerShellTab** object functions as a separate runtime environment.</span></span> <span data-ttu-id="0854a-106">Det är en instans av klassen Microsoft.PowerShell.Host.ISE.PowerShellTabs.</span><span class="sxs-lookup"><span data-stu-id="0854a-106">It is an instance of Microsoft.PowerShell.Host.ISE.PowerShellTabs class.</span></span> <span data-ttu-id="0854a-107">Ett exempel är den **$psISE.PowerShellTabs** objekt.</span><span class="sxs-lookup"><span data-stu-id="0854a-107">An example is the **$psISE.PowerShellTabs** object.</span></span>

## <a name="methods"></a><span data-ttu-id="0854a-108">Metoder</span><span class="sxs-lookup"><span data-stu-id="0854a-108">Methods</span></span>

### <a name="add"></a><span data-ttu-id="0854a-109">Lägg till\(\)</span><span class="sxs-lookup"><span data-stu-id="0854a-109">Add\(\)</span></span>
  <span data-ttu-id="0854a-110">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="0854a-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="0854a-111">Lägger till en ny PowerShell-flik i samlingen.</span><span class="sxs-lookup"><span data-stu-id="0854a-111">Adds a new PowerShell tab to the collection.</span></span> <span data-ttu-id="0854a-112">Returnerar den nytillagda fliken.</span><span class="sxs-lookup"><span data-stu-id="0854a-112">It returns the newly added tab.</span></span>

```
$NewTab=$psISE.PowerShellTabs.Add()
$newTab.DisplayName="Brand New Tab"
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="0854a-113">Ta bort\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="0854a-113">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>
  <span data-ttu-id="0854a-114">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="0854a-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="0854a-115">Tar bort fliken som anges av den **psTab** parameter.</span><span class="sxs-lookup"><span data-stu-id="0854a-115">Removes the tab that is specified by the **psTab** parameter.</span></span>

 <span data-ttu-id="0854a-116">**psTab** i PowerShell fliken om du vill ta bort.</span><span class="sxs-lookup"><span data-stu-id="0854a-116">**psTab** The PowerShell tab to remove.</span></span>

```

$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="This tab will go away in 5 seconds" 
sleep 5 
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="0854a-117">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="0854a-117">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>
  <span data-ttu-id="0854a-118">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="0854a-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="0854a-119">Väljer du fliken PowerShell som anges av den **psTab** parametern så att den aktiva PowerShell-fliken.</span><span class="sxs-lookup"><span data-stu-id="0854a-119">Selects the PowerShell tab that is specified by the **psTab** parameter to make it the currently active PowerShell tab.</span></span>

 <span data-ttu-id="0854a-120">**psTab** i PowerShell tab för att markera.</span><span class="sxs-lookup"><span data-stu-id="0854a-120">**psTab** The PowerShell tab to select.</span></span>

```
# Save the current tab in a variable and rename it
$OldTab = $psISE.CurrentPowerShellTab
$psISE.CurrentPowerShellTab.DisplayName="Old Tab"
# Create a new tab and give it a new display name
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName="Brand New Tab" 
# Switch back to the original tab
$psISE.PowerShellTabs.SelectedPowerShellTab=$oldtab
```

## <a name="see-also"></a><span data-ttu-id="0854a-121">Se även</span><span class="sxs-lookup"><span data-stu-id="0854a-121">See Also</span></span>
- [<span data-ttu-id="0854a-122">Objektet PowerShellTab</span><span class="sxs-lookup"><span data-stu-id="0854a-122">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md) 
- [<span data-ttu-id="0854a-123">Windows PowerShell ISE Scripting Object Model</span><span class="sxs-lookup"><span data-stu-id="0854a-123">The Windows PowerShell ISE Scripting Object Model</span></span>](../ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="0854a-124">Windows PowerShell ISE objektreferens modellen</span><span class="sxs-lookup"><span data-stu-id="0854a-124">Windows PowerShell ISE Object Model Reference</span></span>](../ise/Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="0854a-125">Modellen objekthierarkin ISE</span><span class="sxs-lookup"><span data-stu-id="0854a-125">The ISE Object Model Hierarchy</span></span>](../ise/The-ISE-Object-Model-Hierarchy.md)

  
