---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: ISEMenuItem-objektet
ms.assetid: a16660bd-0aee-46fd-ac17-3f022165d089
ms.openlocfilehash: 556f88117c07100b1734c8ffd8956dce6efe6fb1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62059057"
---
# <a name="the-isemenuitem-object"></a><span data-ttu-id="45e6d-103">ISEMenuItem-objektet</span><span class="sxs-lookup"><span data-stu-id="45e6d-103">The ISEMenuItem Object</span></span>

<span data-ttu-id="45e6d-104">En **ISEMenuItem** objekt är en instans av klassen Microsoft.PowerShell.Host.ISE.ISEMenuItem.</span><span class="sxs-lookup"><span data-stu-id="45e6d-104">An **ISEMenuItem** object is an instance of the Microsoft.PowerShell.Host.ISE.ISEMenuItem class.</span></span> <span data-ttu-id="45e6d-105">Alla menyobjekt på den **tillägg** menyn är instanser av den **Microsoft.PowerShell.Host.ISE.ISEMenuItem** klass.</span><span class="sxs-lookup"><span data-stu-id="45e6d-105">All menu objects on the **Add-ons** menu are instances of the **Microsoft.PowerShell.Host.ISE.ISEMenuItem** class.</span></span>

## <a name="properties"></a><span data-ttu-id="45e6d-106">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="45e6d-106">Properties</span></span>

### <a name="displayname"></a><span data-ttu-id="45e6d-107">Visningsnamn</span><span class="sxs-lookup"><span data-stu-id="45e6d-107">DisplayName</span></span>

<span data-ttu-id="45e6d-108">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="45e6d-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="45e6d-109">Den skrivskyddade egenskapen som hämtar visningsnamnet för menyalternativets.</span><span class="sxs-lookup"><span data-stu-id="45e6d-109">The read-only property that gets the display name of the menu item.</span></span>

```powershell
# Get the display name of the Add-ons menu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName
```

### <a name="action"></a><span data-ttu-id="45e6d-110">Åtgärd</span><span class="sxs-lookup"><span data-stu-id="45e6d-110">Action</span></span>

<span data-ttu-id="45e6d-111">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="45e6d-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="45e6d-112">Den skrivskyddade egenskapen som hämtar blockeringen av skriptet.</span><span class="sxs-lookup"><span data-stu-id="45e6d-112">The read-only property that gets the block of script.</span></span> <span data-ttu-id="45e6d-113">Den anropar åtgärden när du klickar på menyalternativet.</span><span class="sxs-lookup"><span data-stu-id="45e6d-113">It invokes the action when you click the menu item.</span></span>

```powershell
# Get the action associated with the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action

# Invoke the script associated with the first submenu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action.Invoke()
```

### <a name="shortcut"></a><span data-ttu-id="45e6d-114">Genväg</span><span class="sxs-lookup"><span data-stu-id="45e6d-114">Shortcut</span></span>

<span data-ttu-id="45e6d-115">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="45e6d-115">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="45e6d-116">Skrivskyddad egenskap som hämtar Windows ange kortkommandot för menyalternativets.</span><span class="sxs-lookup"><span data-stu-id="45e6d-116">The read-only property that gets the Windows input keyboard shortcut for the menu item.</span></span>

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

### <a name="submenus"></a><span data-ttu-id="45e6d-117">Submenus</span><span class="sxs-lookup"><span data-stu-id="45e6d-117">Submenus</span></span>

<span data-ttu-id="45e6d-118">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="45e6d-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="45e6d-119">Skrivskyddad egenskap som hämtar den [undermenyer](The-ISEMenuItemCollection-Object.md) menyalternativets.</span><span class="sxs-lookup"><span data-stu-id="45e6d-119">The read-only property that gets the [list of submenus](The-ISEMenuItemCollection-Object.md) of the menu item.</span></span>

```powershell
# List the submenus of the Add-ons menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus
```

## <a name="scripting-example"></a><span data-ttu-id="45e6d-120">Skript-exempel</span><span class="sxs-lookup"><span data-stu-id="45e6d-120">Scripting example</span></span>

<span data-ttu-id="45e6d-121">Läs igenom följande skript för att bättre förstå hur menyn tillägg och dess skriptbara egenskaper.</span><span class="sxs-lookup"><span data-stu-id="45e6d-121">To better understand the use of the Add-ons menu and its scriptable properties, read through the following scripting example.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="45e6d-122">Se även</span><span class="sxs-lookup"><span data-stu-id="45e6d-122">See Also</span></span>

- [<span data-ttu-id="45e6d-123">ISEMenuItemCollection-objektet</span><span class="sxs-lookup"><span data-stu-id="45e6d-123">The ISEMenuItemCollection Object</span></span>](The-ISEMenuItemCollection-Object.md)
- [<span data-ttu-id="45e6d-124">Syftet med den Windows PowerShell ISE-Skriptobjektmodellen</span><span class="sxs-lookup"><span data-stu-id="45e6d-124">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="45e6d-125">Hierarki för ISE-objektmodellen</span><span class="sxs-lookup"><span data-stu-id="45e6d-125">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)