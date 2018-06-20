---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: ISEMenuItem-objektet
ms.assetid: a16660bd-0aee-46fd-ac17-3f022165d089
ms.openlocfilehash: 556f88117c07100b1734c8ffd8956dce6efe6fb1
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
ms.locfileid: "30950717"
---
# <a name="the-isemenuitem-object"></a><span data-ttu-id="5393a-103">ISEMenuItem-objektet</span><span class="sxs-lookup"><span data-stu-id="5393a-103">The ISEMenuItem Object</span></span>

<span data-ttu-id="5393a-104">En **ISEMenuItem** objekt är en instans av klassen Microsoft.PowerShell.Host.ISE.ISEMenuItem.</span><span class="sxs-lookup"><span data-stu-id="5393a-104">An **ISEMenuItem** object is an instance of the Microsoft.PowerShell.Host.ISE.ISEMenuItem class.</span></span> <span data-ttu-id="5393a-105">Alla menyobjekt på den **tillägg** menyn är instanser av den **Microsoft.PowerShell.Host.ISE.ISEMenuItem** klass.</span><span class="sxs-lookup"><span data-stu-id="5393a-105">All menu objects on the **Add-ons** menu are instances of the **Microsoft.PowerShell.Host.ISE.ISEMenuItem** class.</span></span>

## <a name="properties"></a><span data-ttu-id="5393a-106">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="5393a-106">Properties</span></span>

### <a name="displayname"></a><span data-ttu-id="5393a-107">Visningsnamn</span><span class="sxs-lookup"><span data-stu-id="5393a-107">DisplayName</span></span>

<span data-ttu-id="5393a-108">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="5393a-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="5393a-109">Den skrivskyddade egenskapen som hämtar visningsnamnet för menyalternativet.</span><span class="sxs-lookup"><span data-stu-id="5393a-109">The read-only property that gets the display name of the menu item.</span></span>

```powershell
# Get the display name of the Add-ons menu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName
```

### <a name="action"></a><span data-ttu-id="5393a-110">Åtgärd</span><span class="sxs-lookup"><span data-stu-id="5393a-110">Action</span></span>

<span data-ttu-id="5393a-111">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="5393a-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="5393a-112">Den skrivskyddade egenskapen som hämtar block med skript.</span><span class="sxs-lookup"><span data-stu-id="5393a-112">The read-only property that gets the block of script.</span></span> <span data-ttu-id="5393a-113">Åtgärden startar när du klickar på menyalternativet.</span><span class="sxs-lookup"><span data-stu-id="5393a-113">It invokes the action when you click the menu item.</span></span>

```powershell
# Get the action associated with the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action

# Invoke the script associated with the first submenu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action.Invoke()
```

### <a name="shortcut"></a><span data-ttu-id="5393a-114">Genväg</span><span class="sxs-lookup"><span data-stu-id="5393a-114">Shortcut</span></span>

<span data-ttu-id="5393a-115">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="5393a-115">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="5393a-116">Skrivskyddad egenskap som hämtar Windows indata kortkommandot för menyalternativet.</span><span class="sxs-lookup"><span data-stu-id="5393a-116">The read-only property that gets the Windows input keyboard shortcut for the menu item.</span></span>

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

### <a name="submenus"></a><span data-ttu-id="5393a-117">Undermenyer</span><span class="sxs-lookup"><span data-stu-id="5393a-117">Submenus</span></span>

<span data-ttu-id="5393a-118">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="5393a-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="5393a-119">Skrivskyddad egenskap som hämtar den [undermenyer](The-ISEMenuItemCollection-Object.md) på menyalternativet.</span><span class="sxs-lookup"><span data-stu-id="5393a-119">The read-only property that gets the [list of submenus](The-ISEMenuItemCollection-Object.md) of the menu item.</span></span>

```powershell
# List the submenus of the Add-ons menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus
```

## <a name="scripting-example"></a><span data-ttu-id="5393a-120">Scripting exempel</span><span class="sxs-lookup"><span data-stu-id="5393a-120">Scripting example</span></span>

<span data-ttu-id="5393a-121">Läs igenom följande skript exempel för att bättre förstå användningen av menyn tillägg och dess skriptbara egenskaper.</span><span class="sxs-lookup"><span data-stu-id="5393a-121">To better understand the use of the Add-ons menu and its scriptable properties, read through the following scripting example.</span></span>

```powershell
# This is a scripting example that shows the use of the Add-ons menu.
# Clear the Add-ons menu if any entries currently exist
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()

# Add an Add-ons menu item with an shortcut and fast access key.
# Note the use of “_”  as opposed to the “&” for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add('_Process', {Get-Process}, 'Alt+P')
# Add a nested menu - a parent and a child submenu item.
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('Parent', $null, $null)
$parentAdded.SubMenus.Add('_Dir', {dir}, 'Alt+D')
```

## <a name="see-also"></a><span data-ttu-id="5393a-122">Se även</span><span class="sxs-lookup"><span data-stu-id="5393a-122">See Also</span></span>

- [<span data-ttu-id="5393a-123">Objektet ISEMenuItemCollection</span><span class="sxs-lookup"><span data-stu-id="5393a-123">The ISEMenuItemCollection Object</span></span>](The-ISEMenuItemCollection-Object.md)
- [<span data-ttu-id="5393a-124">Syftet med Windows PowerShell ISE Scripting Object Model</span><span class="sxs-lookup"><span data-stu-id="5393a-124">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="5393a-125">Hierarki för ISE-objektmodellen</span><span class="sxs-lookup"><span data-stu-id="5393a-125">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)