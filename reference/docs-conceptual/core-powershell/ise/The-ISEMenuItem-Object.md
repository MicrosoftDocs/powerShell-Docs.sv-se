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
# <a name="the-isemenuitem-object"></a>Objektet ISEMenuItem
  En **ISEMenuItem** objekt är en instans av klassen Microsoft.PowerShell.Host.ISE.ISEMenuItem. Alla menyobjekt på den **tillägg** menyn är instanser av den **Microsoft.PowerShell.Host.ISE.ISEMenuItem** klass.

## <a name="properties"></a>Egenskaper

### <a name="displayname"></a>Visningsnamn
  Stöds i Windows PowerShell ISE 2.0 och senare. 

 Den skrivskyddade egenskapen som hämtar visningsnamnet för menyalternativet.

```
# Get the display name of the Add-ons menu item
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName

```

### <a name="action"></a>Åtgärd
  Stöds i Windows PowerShell ISE 2.0 och senare. 

 Den skrivskyddade egenskapen som hämtar block med skript. Åtgärden startar när du klickar på menyalternativet.

```
# Get the action associated with the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action

# Invoke the script associated with the first submenu item 
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action.Invoke()
```

### <a name="shortcut"></a>Genväg
  Stöds i Windows PowerShell ISE 2.0 och senare. 

 Skrivskyddad egenskap som hämtar Windows indata kortkommandot för menyalternativet.

```
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

### <a name="submenus"></a>Undermenyer
  Stöds i Windows PowerShell ISE 2.0 och senare. 

 Skrivskyddad egenskap som hämtar den [undermenyer](The-ISEMenuItemCollection-Object.md) på menyalternativet.

```
# List the submenus of the Add-ons menu
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus
```

## <a name="scripting-example"></a>Scripting exempel
 Läs igenom följande skript exempel för att bättre förstå användningen av menyn tillägg och dess skriptbara egenskaper.

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

## <a name="see-also"></a>Se även
- [Objektet ISEMenuItemCollection](The-ISEMenuItemCollection-Object.md) 
- [Windows PowerShell ISE Scripting Object Model](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Windows PowerShell ISE objektreferens modellen](Windows-PowerShell-ISE-Object-Model-Reference.md)
- [Modellen objekthierarkin ISE](The-ISE-Object-Model-Hierarchy.md)
