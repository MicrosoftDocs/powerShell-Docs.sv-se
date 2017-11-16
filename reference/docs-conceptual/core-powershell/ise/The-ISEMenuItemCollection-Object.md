---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Objektet ISEMenuItemCollection
ms.assetid: 0c0f5484-3320-408e-8534-5bd1c8e48512
ms.openlocfilehash: 7ce9132021d4d5e755503e0adb355beb388a625a
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/03/2017
---
# <a name="the-isemenuitemcollection-object"></a>Objektet ISEMenuItemCollection
  En **ISEMenuItemCollection** objekt är en samling **ISEMenuItem** objekt. Det är en instans av klassen Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection. Ett exempel är den **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** objekt som används för att anpassa den **tillägg** menyn i Windows PowerShell® Integrated Scripting Environment (ISE).

## <a name="method"></a>Metod

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a>Lägg till\(string DisplayName, System.Management.Automation.ScriptBlock åtgärd System.Windows.Input.KeyGesture genväg\)
  Stöds i Windows PowerShell ISE 2.0 och senare. 

 Lägger till ett menyalternativ till samlingen.

 **DisplayName** visningsnamnet för menyn som ska läggas till.

 **Åtgärden** den **System.Management.Automation.ScriptBlock** objekt som anger vad som är associerad med det här menyalternativet.

 **Genväg** kortkommandot för åtgärden.

 **Returnerar** det ISEMenuItem objektet just har lagt till.

```
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
```

### <a name="clear"></a>Rensa\(\)
  Stöds i Windows PowerShell ISE 2.0 och senare. 

 Tar bort alla undermenyer från menyalternativet.

```
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()

```

## <a name="see-also"></a>Se även
- [Objektet ISEMenuItem](The-ISEMenuItem-Object.md) 
- [Windows PowerShell ISE Scripting Object Model](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Windows PowerShell ISE objektreferens modellen](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [Modellen objekthierarkin ISE](The-ISE-Object-Model-Hierarchy.md)

  
