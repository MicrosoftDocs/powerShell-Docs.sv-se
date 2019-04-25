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
# <a name="the-isemenuitem-object"></a>ISEMenuItem-objektet

En **ISEMenuItem** objekt är en instans av klassen Microsoft.PowerShell.Host.ISE.ISEMenuItem. Alla menyobjekt på den **tillägg** menyn är instanser av den **Microsoft.PowerShell.Host.ISE.ISEMenuItem** klass.

## <a name="properties"></a>Egenskaper

### <a name="displayname"></a>Visningsnamn

Stöds i Windows PowerShell ISE 2.0 och senare.

Den skrivskyddade egenskapen som hämtar visningsnamnet för menyalternativets.

```powershell
# Get the display name of the Add-ons menu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName
```

### <a name="action"></a>Åtgärd

Stöds i Windows PowerShell ISE 2.0 och senare.

Den skrivskyddade egenskapen som hämtar blockeringen av skriptet. Den anropar åtgärden när du klickar på menyalternativet.

```powershell
# Get the action associated with the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action

# Invoke the script associated with the first submenu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action.Invoke()
```

### <a name="shortcut"></a>Genväg

Stöds i Windows PowerShell ISE 2.0 och senare.

Skrivskyddad egenskap som hämtar Windows ange kortkommandot för menyalternativets.

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

### <a name="submenus"></a>Submenus

Stöds i Windows PowerShell ISE 2.0 och senare.

Skrivskyddad egenskap som hämtar den [undermenyer](The-ISEMenuItemCollection-Object.md) menyalternativets.

```powershell
# List the submenus of the Add-ons menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus
```

## <a name="scripting-example"></a>Skript-exempel

Läs igenom följande skript för att bättre förstå hur menyn tillägg och dess skriptbara egenskaper.

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

## <a name="see-also"></a>Se även

- [ISEMenuItemCollection-objektet](The-ISEMenuItemCollection-Object.md)
- [Syftet med den Windows PowerShell ISE-Skriptobjektmodellen](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarki för ISE-objektmodellen](The-ISE-Object-Model-Hierarchy.md)