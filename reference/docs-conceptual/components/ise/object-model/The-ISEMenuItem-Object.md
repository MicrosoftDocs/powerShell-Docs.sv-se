---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: ISEMenuItem-objektet
ms.openlocfilehash: a513a3e9f2eb97f3955fa817faedbcbf4e0ed018
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "67028934"
---
# <a name="the-isemenuitem-object"></a><span data-ttu-id="c345b-103">ISEMenuItem-objektet</span><span class="sxs-lookup"><span data-stu-id="c345b-103">The ISEMenuItem Object</span></span>

<span data-ttu-id="c345b-104">Ett **ISEMenuItem** -objekt är en instans av klassen Microsoft. PowerShell. Host. ISE. ISEMenuItem.</span><span class="sxs-lookup"><span data-stu-id="c345b-104">An **ISEMenuItem** object is an instance of the Microsoft.PowerShell.Host.ISE.ISEMenuItem class.</span></span> <span data-ttu-id="c345b-105">Alla meny objekt på menyn **tilläggsprogram** är instanser av klassen **Microsoft. PowerShell. Host. ISE. ISEMenuItem** .</span><span class="sxs-lookup"><span data-stu-id="c345b-105">All menu objects on the **Add-ons** menu are instances of the **Microsoft.PowerShell.Host.ISE.ISEMenuItem** class.</span></span>

## <a name="properties"></a><span data-ttu-id="c345b-106">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="c345b-106">Properties</span></span>

### <a name="displayname"></a><span data-ttu-id="c345b-107">Visningsnamn</span><span class="sxs-lookup"><span data-stu-id="c345b-107">DisplayName</span></span>

<span data-ttu-id="c345b-108">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="c345b-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c345b-109">Den skrivskyddade egenskapen som hämtar meny alternativets visnings namn.</span><span class="sxs-lookup"><span data-stu-id="c345b-109">The read-only property that gets the display name of the menu item.</span></span>

```powershell
# Get the display name of the Add-ons menu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName
```

### <a name="action"></a><span data-ttu-id="c345b-110">Åtgärd</span><span class="sxs-lookup"><span data-stu-id="c345b-110">Action</span></span>

<span data-ttu-id="c345b-111">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="c345b-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c345b-112">Den skrivskyddade egenskapen som hämtar skript blocket.</span><span class="sxs-lookup"><span data-stu-id="c345b-112">The read-only property that gets the block of script.</span></span> <span data-ttu-id="c345b-113">Den anropar åtgärden när du klickar på meny alternativet.</span><span class="sxs-lookup"><span data-stu-id="c345b-113">It invokes the action when you click the menu item.</span></span>

```powershell
# Get the action associated with the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action

# Invoke the script associated with the first submenu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action.Invoke()
```

### <a name="shortcut"></a><span data-ttu-id="c345b-114">Genvägar</span><span class="sxs-lookup"><span data-stu-id="c345b-114">Shortcut</span></span>

<span data-ttu-id="c345b-115">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="c345b-115">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c345b-116">Den skrivskyddade egenskapen som hämtar kortkommandot för Windows-indatapanelen för meny alternativet.</span><span class="sxs-lookup"><span data-stu-id="c345b-116">The read-only property that gets the Windows input keyboard shortcut for the menu item.</span></span>

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

### <a name="submenus"></a><span data-ttu-id="c345b-117">Inga undermenyer</span><span class="sxs-lookup"><span data-stu-id="c345b-117">Submenus</span></span>

<span data-ttu-id="c345b-118">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="c345b-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c345b-119">Den skrivskyddade egenskapen som hämtar listan över meny alternativets [undermenyer](The-ISEMenuItemCollection-Object.md) .</span><span class="sxs-lookup"><span data-stu-id="c345b-119">The read-only property that gets the [list of submenus](The-ISEMenuItemCollection-Object.md) of the menu item.</span></span>

```powershell
# List the submenus of the Add-ons menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus
```

## <a name="scripting-example"></a><span data-ttu-id="c345b-120">Skript exempel</span><span class="sxs-lookup"><span data-stu-id="c345b-120">Scripting example</span></span>

<span data-ttu-id="c345b-121">Läs igenom följande skript exempel om du vill veta mer om hur du använder menyn tillägg och dess skript bara egenskaper.</span><span class="sxs-lookup"><span data-stu-id="c345b-121">To better understand the use of the Add-ons menu and its scriptable properties, read through the following scripting example.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c345b-122">Se även</span><span class="sxs-lookup"><span data-stu-id="c345b-122">See Also</span></span>

- [<span data-ttu-id="c345b-123">ISEMenuItemCollection-objektet</span><span class="sxs-lookup"><span data-stu-id="c345b-123">The ISEMenuItemCollection Object</span></span>](The-ISEMenuItemCollection-Object.md)
- [<span data-ttu-id="c345b-124">Syftet med Windows PowerShell ISE-skriptets objekt modell</span><span class="sxs-lookup"><span data-stu-id="c345b-124">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="c345b-125">Hierarki för ISE-objektmodellen</span><span class="sxs-lookup"><span data-stu-id="c345b-125">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
