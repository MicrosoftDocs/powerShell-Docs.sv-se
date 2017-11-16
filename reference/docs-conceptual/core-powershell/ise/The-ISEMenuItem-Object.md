---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Objektet ISEMenuItem
ms.assetid: a16660bd-0aee-46fd-ac17-3f022165d089
ms.openlocfilehash: 5561955040e56110a6af0619c286548f5812fb47
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/08/2017
---
# <a name="the-isemenuitem-object"></a><span data-ttu-id="0336b-103">Objektet ISEMenuItem</span><span class="sxs-lookup"><span data-stu-id="0336b-103">The ISEMenuItem Object</span></span>
  <span data-ttu-id="0336b-104">En **ISEMenuItem** objekt är en instans av klassen Microsoft.PowerShell.Host.ISE.ISEMenuItem.</span><span class="sxs-lookup"><span data-stu-id="0336b-104">An **ISEMenuItem** object is an instance of the Microsoft.PowerShell.Host.ISE.ISEMenuItem class.</span></span> <span data-ttu-id="0336b-105">Alla menyobjekt på den **tillägg** menyn är instanser av den **Microsoft.PowerShell.Host.ISE.ISEMenuItem** klass.</span><span class="sxs-lookup"><span data-stu-id="0336b-105">All menu objects on the **Add-ons** menu are instances of the **Microsoft.PowerShell.Host.ISE.ISEMenuItem** class.</span></span>

## <a name="properties"></a><span data-ttu-id="0336b-106">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="0336b-106">Properties</span></span>

### <a name="displayname"></a><span data-ttu-id="0336b-107">Visningsnamn</span><span class="sxs-lookup"><span data-stu-id="0336b-107">DisplayName</span></span>
  <span data-ttu-id="0336b-108">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="0336b-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="0336b-109">Den skrivskyddade egenskapen som hämtar visningsnamnet för menyalternativet.</span><span class="sxs-lookup"><span data-stu-id="0336b-109">The read-only property that gets the display name of the menu item.</span></span>

```
# Get the display name of the Add-ons menu item
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName

```

### <a name="action"></a><span data-ttu-id="0336b-110">Åtgärd</span><span class="sxs-lookup"><span data-stu-id="0336b-110">Action</span></span>
  <span data-ttu-id="0336b-111">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="0336b-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="0336b-112">Den skrivskyddade egenskapen som hämtar block med skript.</span><span class="sxs-lookup"><span data-stu-id="0336b-112">The read-only property that gets the block of script.</span></span> <span data-ttu-id="0336b-113">Åtgärden startar när du klickar på menyalternativet.</span><span class="sxs-lookup"><span data-stu-id="0336b-113">It invokes the action when you click the menu item.</span></span>

```
# Get the action associated with the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action

# Invoke the script associated with the first submenu item 
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action.Invoke()
```

### <a name="shortcut"></a><span data-ttu-id="0336b-114">Genväg</span><span class="sxs-lookup"><span data-stu-id="0336b-114">Shortcut</span></span>
  <span data-ttu-id="0336b-115">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="0336b-115">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="0336b-116">Skrivskyddad egenskap som hämtar Windows indata kortkommandot för menyalternativet.</span><span class="sxs-lookup"><span data-stu-id="0336b-116">The read-only property that gets the Windows input keyboard shortcut for the menu item.</span></span>

```
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

### <a name="submenus"></a><span data-ttu-id="0336b-117">Undermenyer</span><span class="sxs-lookup"><span data-stu-id="0336b-117">Submenus</span></span>
  <span data-ttu-id="0336b-118">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="0336b-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="0336b-119">Skrivskyddad egenskap som hämtar den [undermenyer](The-ISEMenuItemCollection-Object.md) på menyalternativet.</span><span class="sxs-lookup"><span data-stu-id="0336b-119">The read-only property that gets the [list of submenus](The-ISEMenuItemCollection-Object.md) of the menu item.</span></span>

```
# List the submenus of the Add-ons menu
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus
```

## <a name="scripting-example"></a><span data-ttu-id="0336b-120">Scripting exempel</span><span class="sxs-lookup"><span data-stu-id="0336b-120">Scripting example</span></span>
 <span data-ttu-id="0336b-121">Läs igenom följande skript exempel för att bättre förstå användningen av menyn tillägg och dess skriptbara egenskaper.</span><span class="sxs-lookup"><span data-stu-id="0336b-121">To better understand the use of the Add-ons menu and its scriptable properties, read through the following scripting example.</span></span>

```

# This is a scripting example that shows the use of the Add-ons menu.
# Clear the Add-ons menu if any entries currently exist
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()

# Add an Add-ons menu item with an shortcut and fast access key.
# Note the use of “_”  as opposed to the “&” for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P") 
# Add a nested menu - a parent and a child submenu item. 
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("Parent",$null,$null) 
$parentAdded.SubMenus.Add("_Dir",{dir},"Alt+D")

```

## <a name="see-also"></a><span data-ttu-id="0336b-122">Se även</span><span class="sxs-lookup"><span data-stu-id="0336b-122">See Also</span></span>
- [<span data-ttu-id="0336b-123">Objektet ISEMenuItemCollection</span><span class="sxs-lookup"><span data-stu-id="0336b-123">The ISEMenuItemCollection Object</span></span>](The-ISEMenuItemCollection-Object.md) 
- [<span data-ttu-id="0336b-124">Windows PowerShell ISE Scripting Object Model</span><span class="sxs-lookup"><span data-stu-id="0336b-124">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="0336b-125">Windows PowerShell ISE objektreferens modellen</span><span class="sxs-lookup"><span data-stu-id="0336b-125">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md)
- [<span data-ttu-id="0336b-126">Modellen objekthierarkin ISE</span><span class="sxs-lookup"><span data-stu-id="0336b-126">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
