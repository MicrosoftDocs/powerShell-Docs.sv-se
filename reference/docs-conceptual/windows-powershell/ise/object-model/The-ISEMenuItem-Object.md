---
ms.date: 12/31/2019
title: ISEMenuItem-objektet
description: Ett ISEMenuItem-objekt är en instans av klassen Microsoft. PowerShell. Host. ISE. ISEMenuItem. Alla meny objekt på menyn **tilläggsprogram** är instanser av klassen ISEMenuItem.
ms.openlocfilehash: 15036e3551687a21dfbe50834a89247c80949656
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92663437"
---
# <a name="the-isemenuitem-object"></a><span data-ttu-id="260cb-104">ISEMenuItem-objektet</span><span class="sxs-lookup"><span data-stu-id="260cb-104">The ISEMenuItem Object</span></span>

<span data-ttu-id="260cb-105">Ett **ISEMenuItem** -objekt är en instans av klassen **Microsoft. PowerShell. Host. ISE. ISEMenuItem** .</span><span class="sxs-lookup"><span data-stu-id="260cb-105">An **ISEMenuItem** object is an instance of the **Microsoft.PowerShell.Host.ISE.ISEMenuItem** class.</span></span>
<span data-ttu-id="260cb-106">Alla meny objekt på menyn **tilläggsprogram** är instanser av klassen **Microsoft. PowerShell. Host. ISE. ISEMenuItem** .</span><span class="sxs-lookup"><span data-stu-id="260cb-106">All menu objects on the **Add-ons** menu are instances of the **Microsoft.PowerShell.Host.ISE.ISEMenuItem** class.</span></span>

## <a name="properties"></a><span data-ttu-id="260cb-107">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="260cb-107">Properties</span></span>

### <a name="displayname"></a><span data-ttu-id="260cb-108">DisplayName</span><span class="sxs-lookup"><span data-stu-id="260cb-108">DisplayName</span></span>

<span data-ttu-id="260cb-109">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="260cb-109">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="260cb-110">Den skrivskyddade egenskapen som hämtar meny alternativets visnings namn.</span><span class="sxs-lookup"><span data-stu-id="260cb-110">The read-only property that gets the display name of the menu item.</span></span>

```powershell
# Get the display name of the Add-ons menu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName
```

### <a name="action"></a><span data-ttu-id="260cb-111">Åtgärd</span><span class="sxs-lookup"><span data-stu-id="260cb-111">Action</span></span>

<span data-ttu-id="260cb-112">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="260cb-112">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="260cb-113">Den skrivskyddade egenskapen som hämtar skript blocket.</span><span class="sxs-lookup"><span data-stu-id="260cb-113">The read-only property that gets the block of script.</span></span> <span data-ttu-id="260cb-114">Den anropar åtgärden när du klickar på meny alternativet.</span><span class="sxs-lookup"><span data-stu-id="260cb-114">It invokes the action when you click the menu item.</span></span>

```powershell
# Get the action associated with the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action

# Invoke the script associated with the first submenu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action.Invoke()
```

### <a name="shortcut"></a><span data-ttu-id="260cb-115">Genvägar</span><span class="sxs-lookup"><span data-stu-id="260cb-115">Shortcut</span></span>

<span data-ttu-id="260cb-116">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="260cb-116">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="260cb-117">Den skrivskyddade egenskapen som hämtar kortkommandot för Windows-indatapanelen för meny alternativet.</span><span class="sxs-lookup"><span data-stu-id="260cb-117">The read-only property that gets the Windows input keyboard shortcut for the menu item.</span></span>

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

### <a name="submenus"></a><span data-ttu-id="260cb-118">Inga undermenyer</span><span class="sxs-lookup"><span data-stu-id="260cb-118">Submenus</span></span>

<span data-ttu-id="260cb-119">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="260cb-119">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="260cb-120">Den skrivskyddade egenskapen som hämtar listan över meny alternativets [undermenyer](The-ISEMenuItemCollection-Object.md) .</span><span class="sxs-lookup"><span data-stu-id="260cb-120">The read-only property that gets the [list of submenus](The-ISEMenuItemCollection-Object.md) of the menu item.</span></span>

```powershell
# List the submenus of the Add-ons menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus
```

## <a name="scripting-example"></a><span data-ttu-id="260cb-121">Skript exempel</span><span class="sxs-lookup"><span data-stu-id="260cb-121">Scripting example</span></span>

<span data-ttu-id="260cb-122">Läs igenom följande skript exempel om du vill veta mer om hur du använder menyn tillägg och dess skript bara egenskaper.</span><span class="sxs-lookup"><span data-stu-id="260cb-122">To better understand the use of the Add-ons menu and its scriptable properties, read through the following scripting example.</span></span>

```powershell
# This is a scripting example that shows the use of the Add-ons menu.
# Clear the Add-ons menu if any entries currently exist
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()

# Add an Add-ons menu item with an shortcut and fast access key.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add('_Process', {Get-Process}, 'Alt+P')
# Add a nested menu - a parent and a child submenu item.
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('Parent', $null, $null)
$parentAdded.SubMenus.Add('_Dir', {dir}, 'Alt+D')
```

## <a name="see-also"></a><span data-ttu-id="260cb-123">Se även</span><span class="sxs-lookup"><span data-stu-id="260cb-123">See Also</span></span>

- [<span data-ttu-id="260cb-124">ISEMenuItemCollection-objektet</span><span class="sxs-lookup"><span data-stu-id="260cb-124">The ISEMenuItemCollection Object</span></span>](The-ISEMenuItemCollection-Object.md)
- [<span data-ttu-id="260cb-125">Användningsområden för Windows PowerShell ISE-skriptobjektmodellen</span><span class="sxs-lookup"><span data-stu-id="260cb-125">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="260cb-126">Objekt modells-hierarkin för ISE</span><span class="sxs-lookup"><span data-stu-id="260cb-126">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
