---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Objektet ISEMenuItemCollection
ms.assetid: 0c0f5484-3320-408e-8534-5bd1c8e48512
ms.openlocfilehash: 7ce9132021d4d5e755503e0adb355beb388a625a
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/03/2017
---
# <a name="the-isemenuitemcollection-object"></a><span data-ttu-id="27cc4-103">Objektet ISEMenuItemCollection</span><span class="sxs-lookup"><span data-stu-id="27cc4-103">The ISEMenuItemCollection Object</span></span>
  <span data-ttu-id="27cc4-104">En **ISEMenuItemCollection** objekt är en samling **ISEMenuItem** objekt.</span><span class="sxs-lookup"><span data-stu-id="27cc4-104">An **ISEMenuItemCollection** object is a collection of **ISEMenuItem** objects.</span></span> <span data-ttu-id="27cc4-105">Det är en instans av klassen Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection.</span><span class="sxs-lookup"><span data-stu-id="27cc4-105">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection class.</span></span> <span data-ttu-id="27cc4-106">Ett exempel är den **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** objekt som används för att anpassa den **tillägg** menyn i Windows PowerShell® Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="27cc4-106">An example is the **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** object that is used to customize the **Add-On** menu in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span>

## <a name="method"></a><span data-ttu-id="27cc4-107">Metod</span><span class="sxs-lookup"><span data-stu-id="27cc4-107">Method</span></span>

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a><span data-ttu-id="27cc4-108">Lägg till\(string DisplayName, System.Management.Automation.ScriptBlock åtgärd System.Windows.Input.KeyGesture genväg\)</span><span class="sxs-lookup"><span data-stu-id="27cc4-108">Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)</span></span>
  <span data-ttu-id="27cc4-109">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="27cc4-109">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="27cc4-110">Lägger till ett menyalternativ till samlingen.</span><span class="sxs-lookup"><span data-stu-id="27cc4-110">Adds a menu item to the collection.</span></span>

 <span data-ttu-id="27cc4-111">**DisplayName** visningsnamnet för menyn som ska läggas till.</span><span class="sxs-lookup"><span data-stu-id="27cc4-111">**DisplayName** The display name of the menu to be added.</span></span>

 <span data-ttu-id="27cc4-112">**Åtgärden** den **System.Management.Automation.ScriptBlock** objekt som anger vad som är associerad med det här menyalternativet.</span><span class="sxs-lookup"><span data-stu-id="27cc4-112">**Action** The **System.Management.Automation.ScriptBlock** object that specifies the action that is associated with this menu item.</span></span>

 <span data-ttu-id="27cc4-113">**Genväg** kortkommandot för åtgärden.</span><span class="sxs-lookup"><span data-stu-id="27cc4-113">**Shortcut** The keyboard shortcut for the action.</span></span>

 <span data-ttu-id="27cc4-114">**Returnerar** det ISEMenuItem objektet just har lagt till.</span><span class="sxs-lookup"><span data-stu-id="27cc4-114">**Returns** The ISEMenuItem object that was just added.</span></span>

```
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
```

### <a name="clear"></a><span data-ttu-id="27cc4-115">Rensa\(\)</span><span class="sxs-lookup"><span data-stu-id="27cc4-115">Clear\(\)</span></span>
  <span data-ttu-id="27cc4-116">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="27cc4-116">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="27cc4-117">Tar bort alla undermenyer från menyalternativet.</span><span class="sxs-lookup"><span data-stu-id="27cc4-117">Removes all submenus from the menu item.</span></span>

```
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()

```

## <a name="see-also"></a><span data-ttu-id="27cc4-118">Se även</span><span class="sxs-lookup"><span data-stu-id="27cc4-118">See Also</span></span>
- [<span data-ttu-id="27cc4-119">Objektet ISEMenuItem</span><span class="sxs-lookup"><span data-stu-id="27cc4-119">The ISEMenuItem Object</span></span>](The-ISEMenuItem-Object.md) 
- [<span data-ttu-id="27cc4-120">Windows PowerShell ISE Scripting Object Model</span><span class="sxs-lookup"><span data-stu-id="27cc4-120">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="27cc4-121">Windows PowerShell ISE objektreferens modellen</span><span class="sxs-lookup"><span data-stu-id="27cc4-121">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="27cc4-122">Modellen objekthierarkin ISE</span><span class="sxs-lookup"><span data-stu-id="27cc4-122">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

  
