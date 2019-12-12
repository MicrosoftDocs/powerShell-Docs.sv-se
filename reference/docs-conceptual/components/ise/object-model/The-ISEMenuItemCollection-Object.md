---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: ISEMenuItemCollection-objektet
ms.openlocfilehash: b3795af1a6ed61ed6e371e5fc20cc4e95f643fd4
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030541"
---
# <a name="the-isemenuitemcollection-object"></a>ISEMenuItemCollection-objektet

Ett **ISEMenuItemCollection** -objekt är en samling av **ISEMenuItem** -objekt. Det är en instans av klassen Microsoft. PowerShell. Host. ISE. ISEMenuItemCollection. Ett exempel är objektet **$psISE. CurrentPowerShellTab. AddOnsMenu. undermenyer** som används för att anpassa **tilläggs** menyn i Windows PowerShell® Integrated Scripting Environment (ISE).

## <a name="method"></a>Metod

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a>Lägg till\(sträng DisplayName, system. Management. Automation. script block Action, system. Windows. inmatad. gest kortkommando \)

Stöds i Windows PowerShell ISE 2,0 och senare.

Lägger till ett meny alternativ i samlingen.

**DisplayName** Visnings namnet för den meny som ska läggas till.

**Åtgärd** Objektet **system. Management. Automation. script block** som anger den åtgärd som är kopplad till det här meny alternativet.

**Genväg** Kortkommandot för åtgärden.

**Returnerar** Det ISEMenuItem-objekt som nyss lades till.

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
- [Syftet med Windows PowerShell ISE-skriptets objekt modell](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarki för ISE-objektmodellen](The-ISE-Object-Model-Hierarchy.md)
