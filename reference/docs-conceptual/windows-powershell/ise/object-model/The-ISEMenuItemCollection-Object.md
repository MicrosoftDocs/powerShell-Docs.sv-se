---
ms.date: 12/31/2019
title: ISEMenuItemCollection-objektet
description: Ett ISEMenuItemCollection-objekt är en samling av ISEMenuItem-objekt.
ms.openlocfilehash: cd86768d13b1326a8f35c44f0391ab60669cee4f
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92655990"
---
# <a name="the-isemenuitemcollection-object"></a>ISEMenuItemCollection-objektet

Ett **ISEMenuItemCollection** -objekt är en samling av **ISEMenuItem** -objekt. Det är en instans av klassen **Microsoft. PowerShell. Host. ISE. ISEMenuItemCollection** . Ett exempel är det `$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus` objekt som används för att anpassa **tilläggs** menyn i Windows PowerShell &reg; Ise (Integrated Scripting Environment).

## <a name="method"></a>Metod

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a>Lägg till \( sträng DisplayName, system. Management. Automation. script block Action, system. Windows. inmatad. gest gen väg \)

Stöds i Windows PowerShell ISE 2,0 och senare.

Lägger till ett meny alternativ i samlingen.

**DisplayName** Visnings namnet för den meny som ska läggas till.

**Åtgärd** Objektet **system. Management. Automation. script block** som anger den åtgärd som är kopplad till det här meny alternativet.

**Genväg** Kortkommandot för åtgärden.

**Returnerar** Det **ISEMenuItem** -objekt som nyss lades till.

```powershell
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
```

### <a name="clear"></a>Rensa\(\)

Stöds i Windows PowerShell ISE 2,0 och senare.

Tar bort alla undermenyer från meny alternativet.

```powershell
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
```

## <a name="see-also"></a>Se även

- [ISEMenuItem-objektet](The-ISEMenuItem-Object.md)
- [Användningsområden för Windows PowerShell ISE-skriptobjektmodellen](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Objekt modells-hierarkin för ISE](The-ISE-Object-Model-Hierarchy.md)
