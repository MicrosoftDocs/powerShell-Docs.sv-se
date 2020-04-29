---
ms.date: 12/31/2019
keywords: PowerShell, cmdlet
title: ISEMenuItemCollection-objektet
ms.openlocfilehash: 39e8547c9b19ba323d4b224a46eda416542b2807
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "75736180"
---
# <a name="the-isemenuitemcollection-object"></a><span data-ttu-id="6ac27-103">ISEMenuItemCollection-objektet</span><span class="sxs-lookup"><span data-stu-id="6ac27-103">The ISEMenuItemCollection Object</span></span>

<span data-ttu-id="6ac27-104">Ett **ISEMenuItemCollection** -objekt är en samling av **ISEMenuItem** -objekt.</span><span class="sxs-lookup"><span data-stu-id="6ac27-104">An **ISEMenuItemCollection** object is a collection of **ISEMenuItem** objects.</span></span> <span data-ttu-id="6ac27-105">Det är en instans av klassen **Microsoft. PowerShell. Host. ISE. ISEMenuItemCollection** .</span><span class="sxs-lookup"><span data-stu-id="6ac27-105">It is an instance of the **Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection** class.</span></span> <span data-ttu-id="6ac27-106">Ett exempel är det `$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus` objekt som används för att anpassa **tilläggs** menyn i Windows PowerShell® ISE (Integrated Scripting Environment).</span><span class="sxs-lookup"><span data-stu-id="6ac27-106">An example is the `$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus` object that is used to customize the **Add-On** menu in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span>

## <a name="method"></a><span data-ttu-id="6ac27-107">Metod</span><span class="sxs-lookup"><span data-stu-id="6ac27-107">Method</span></span>

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a><span data-ttu-id="6ac27-108">Lägg\(till sträng DisplayName, system. Management. Automation. script block Action, system. Windows. inmatad. gest gen väg\)</span><span class="sxs-lookup"><span data-stu-id="6ac27-108">Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)</span></span>

<span data-ttu-id="6ac27-109">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="6ac27-109">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="6ac27-110">Lägger till ett meny alternativ i samlingen.</span><span class="sxs-lookup"><span data-stu-id="6ac27-110">Adds a menu item to the collection.</span></span>

<span data-ttu-id="6ac27-111">**DisplayName** Visnings namnet för den meny som ska läggas till.</span><span class="sxs-lookup"><span data-stu-id="6ac27-111">**DisplayName** The display name of the menu to be added.</span></span>

<span data-ttu-id="6ac27-112">**Åtgärd** Objektet **system. Management. Automation. script block** som anger den åtgärd som är kopplad till det här meny alternativet.</span><span class="sxs-lookup"><span data-stu-id="6ac27-112">**Action** The **System.Management.Automation.ScriptBlock** object that specifies the action that is associated with this menu item.</span></span>

<span data-ttu-id="6ac27-113">**Genväg** Kortkommandot för åtgärden.</span><span class="sxs-lookup"><span data-stu-id="6ac27-113">**Shortcut** The keyboard shortcut for the action.</span></span>

<span data-ttu-id="6ac27-114">**Returnerar** Det **ISEMenuItem** -objekt som nyss lades till.</span><span class="sxs-lookup"><span data-stu-id="6ac27-114">**Returns** The **ISEMenuItem** object that was just added.</span></span>

```powershell
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
```

### <a name="clear"></a><span data-ttu-id="6ac27-115">Rensa\(\)</span><span class="sxs-lookup"><span data-stu-id="6ac27-115">Clear\(\)</span></span>

<span data-ttu-id="6ac27-116">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="6ac27-116">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="6ac27-117">Tar bort alla undermenyer från meny alternativet.</span><span class="sxs-lookup"><span data-stu-id="6ac27-117">Removes all submenus from the menu item.</span></span>

```powershell
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
```

## <a name="see-also"></a><span data-ttu-id="6ac27-118">Se även</span><span class="sxs-lookup"><span data-stu-id="6ac27-118">See Also</span></span>

- [<span data-ttu-id="6ac27-119">ISEMenuItem-objektet</span><span class="sxs-lookup"><span data-stu-id="6ac27-119">The ISEMenuItem Object</span></span>](The-ISEMenuItem-Object.md)
- [<span data-ttu-id="6ac27-120">Användningsområden för Windows PowerShell ISE-skriptobjektmodellen</span><span class="sxs-lookup"><span data-stu-id="6ac27-120">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="6ac27-121">Objekt modells-hierarkin för ISE</span><span class="sxs-lookup"><span data-stu-id="6ac27-121">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
