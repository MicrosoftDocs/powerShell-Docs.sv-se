---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: ISEMenuItemCollection-objektet
ms.assetid: 0c0f5484-3320-408e-8534-5bd1c8e48512
ms.openlocfilehash: 7e5030416df394aaa9e9d3f63978e204a7faabf1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086705"
---
# <a name="the-isemenuitemcollection-object"></a>ISEMenuItemCollection-objektet

En **ISEMenuItemCollection** objekt är en samling **ISEMenuItem** objekt. Det är en instans av klassen Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection. Ett exempel är den **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** objekt som används för att anpassa den **tillägg** menyn i Windows PowerShell® Integrated Scripting Environment (ISE).

## <a name="method"></a>Metod

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a>Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)

Stöds i Windows PowerShell ISE 2.0 och senare.

Lägger till ett menyalternativ till i samlingen.

**DisplayName** visningsnamnet på menyn som ska läggas till.

**Åtgärden** den **System.Management.Automation.ScriptBlock** objekt som anger vad som är associerad med det här menyobjektet.

**Genväg** kortkommandot för åtgärden.

**Returnerar** The ISEMenuItem-objektet just har lagt till.

```powershell
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
```

### <a name="clear"></a>Rensa\(\)

Stöds i Windows PowerShell ISE 2.0 och senare.

Tar bort alla undermenyer från menyalternativet.

```powershell
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
```

## <a name="see-also"></a>Se även

- [ISEMenuItem-objektet](The-ISEMenuItem-Object.md)
- [Syftet med den Windows PowerShell ISE-Skriptobjektmodellen](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarki för ISE-objektmodellen](The-ISE-Object-Model-Hierarchy.md)