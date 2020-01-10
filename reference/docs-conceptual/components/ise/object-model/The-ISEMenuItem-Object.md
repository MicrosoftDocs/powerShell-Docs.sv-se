---
ms.date: 12/31/2019
keywords: PowerShell, cmdlet
title: ISEMenuItem-objektet
ms.openlocfilehash: c3ffe6e8f0b28987543fe0a873c552292dc5158a
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736989"
---
# <a name="the-isemenuitem-object"></a><span data-ttu-id="abf7f-103">ISEMenuItem-objektet</span><span class="sxs-lookup"><span data-stu-id="abf7f-103">The ISEMenuItem Object</span></span>

<span data-ttu-id="abf7f-104">Ett **ISEMenuItem** -objekt är en instans av klassen **Microsoft. PowerShell. Host. ISE. ISEMenuItem** .</span><span class="sxs-lookup"><span data-stu-id="abf7f-104">An **ISEMenuItem** object is an instance of the **Microsoft.PowerShell.Host.ISE.ISEMenuItem** class.</span></span>
<span data-ttu-id="abf7f-105">Alla meny objekt på menyn **tilläggsprogram** är instanser av klassen **Microsoft. PowerShell. Host. ISE. ISEMenuItem** .</span><span class="sxs-lookup"><span data-stu-id="abf7f-105">All menu objects on the **Add-ons** menu are instances of the **Microsoft.PowerShell.Host.ISE.ISEMenuItem** class.</span></span>

## <a name="properties"></a><span data-ttu-id="abf7f-106">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="abf7f-106">Properties</span></span>

### <a name="displayname"></a><span data-ttu-id="abf7f-107">Visningsnamn</span><span class="sxs-lookup"><span data-stu-id="abf7f-107">DisplayName</span></span>

<span data-ttu-id="abf7f-108">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="abf7f-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="abf7f-109">Den skrivskyddade egenskapen som hämtar meny alternativets visnings namn.</span><span class="sxs-lookup"><span data-stu-id="abf7f-109">The read-only property that gets the display name of the menu item.</span></span>

```powershell
# Get the display name of the Add-ons menu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName
```

### <a name="action"></a><span data-ttu-id="abf7f-110">Åtgärd</span><span class="sxs-lookup"><span data-stu-id="abf7f-110">Action</span></span>

<span data-ttu-id="abf7f-111">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="abf7f-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="abf7f-112">Den skrivskyddade egenskapen som hämtar skript blocket.</span><span class="sxs-lookup"><span data-stu-id="abf7f-112">The read-only property that gets the block of script.</span></span> <span data-ttu-id="abf7f-113">Den anropar åtgärden när du klickar på meny alternativet.</span><span class="sxs-lookup"><span data-stu-id="abf7f-113">It invokes the action when you click the menu item.</span></span>

```powershell
# Get the action associated with the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action

# Invoke the script associated with the first submenu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action.Invoke()
```

### <a name="shortcut"></a><span data-ttu-id="abf7f-114">Genvägar</span><span class="sxs-lookup"><span data-stu-id="abf7f-114">Shortcut</span></span>

<span data-ttu-id="abf7f-115">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="abf7f-115">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="abf7f-116">Den skrivskyddade egenskapen som hämtar kortkommandot för Windows-indatapanelen för meny alternativet.</span><span class="sxs-lookup"><span data-stu-id="abf7f-116">The read-only property that gets the Windows input keyboard shortcut for the menu item.</span></span>

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

### <a name="submenus"></a><span data-ttu-id="abf7f-117">Inga undermenyer</span><span class="sxs-lookup"><span data-stu-id="abf7f-117">Submenus</span></span>

<span data-ttu-id="abf7f-118">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="abf7f-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="abf7f-119">Den skrivskyddade egenskapen som hämtar listan över meny alternativets [undermenyer](The-ISEMenuItemCollection-Object.md) .</span><span class="sxs-lookup"><span data-stu-id="abf7f-119">The read-only property that gets the [list of submenus](The-ISEMenuItemCollection-Object.md) of the menu item.</span></span>

```powershell
# List the submenus of the Add-ons menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus
```

## <a name="scripting-example"></a><span data-ttu-id="abf7f-120">Skript exempel</span><span class="sxs-lookup"><span data-stu-id="abf7f-120">Scripting example</span></span>

<span data-ttu-id="abf7f-121">Läs igenom följande skript exempel om du vill veta mer om hur du använder menyn tillägg och dess skript bara egenskaper.</span><span class="sxs-lookup"><span data-stu-id="abf7f-121">To better understand the use of the Add-ons menu and its scriptable properties, read through the following scripting example.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="abf7f-122">Se även</span><span class="sxs-lookup"><span data-stu-id="abf7f-122">See Also</span></span>

- [<span data-ttu-id="abf7f-123">ISEMenuItemCollection-objektet</span><span class="sxs-lookup"><span data-stu-id="abf7f-123">The ISEMenuItemCollection Object</span></span>](The-ISEMenuItemCollection-Object.md)
- [<span data-ttu-id="abf7f-124">Syftet med Windows PowerShell ISE-skriptets objekt modell</span><span class="sxs-lookup"><span data-stu-id="abf7f-124">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="abf7f-125">Hierarki för ISE-objektmodellen</span><span class="sxs-lookup"><span data-stu-id="abf7f-125">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
