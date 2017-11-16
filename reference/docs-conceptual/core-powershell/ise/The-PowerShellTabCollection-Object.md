---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Objektet PowerShellTabCollection
ms.assetid: 81f4bf4a-83bf-415e-8378-1703792fbb58
ms.openlocfilehash: dcdc16ae126453b6ade64917ac4950cc05e5f8ad
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/03/2017
---
# <a name="the-powershelltabcollection-object"></a>Objektet PowerShellTabCollection
  Den **PowerShellTab** samlingsobjektet är en samling **PowerShellTab** objekt. Varje **PowerShellTab** objekt som fungerar som en separat körningsmiljö. Det är en instans av klassen Microsoft.PowerShell.Host.ISE.PowerShellTabs. Ett exempel är den **$psISE.PowerShellTabs** objekt.

## <a name="methods"></a>Metoder

### <a name="add"></a>Lägg till\(\)
  Stöds i Windows PowerShell ISE 2.0 och senare. 

 Lägger till en ny PowerShell-flik i samlingen. Returnerar den nytillagda fliken.

```
$NewTab=$psISE.PowerShellTabs.Add()
$newTab.DisplayName="Brand New Tab"
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a>Ta bort\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)
  Stöds i Windows PowerShell ISE 2.0 och senare. 

 Tar bort fliken som anges av den **psTab** parameter.

 **psTab** i PowerShell fliken om du vill ta bort.

```

$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="This tab will go away in 5 seconds" 
sleep 5 
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a>SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)
  Stöds i Windows PowerShell ISE 2.0 och senare. 

 Väljer du fliken PowerShell som anges av den **psTab** parametern så att den aktiva PowerShell-fliken.

 **psTab** i PowerShell tab för att markera.

```
# Save the current tab in a variable and rename it
$OldTab = $psISE.CurrentPowerShellTab
$psISE.CurrentPowerShellTab.DisplayName="Old Tab"
# Create a new tab and give it a new display name
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName="Brand New Tab" 
# Switch back to the original tab
$psISE.PowerShellTabs.SelectedPowerShellTab=$oldtab
```

## <a name="see-also"></a>Se även
- [Objektet PowerShellTab](The-PowerShellTab-Object.md) 
- [Windows PowerShell ISE Scripting Object Model](../ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Windows PowerShell ISE objektreferens modellen](../ise/Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [Modellen objekthierarkin ISE](../ise/The-ISE-Object-Model-Hierarchy.md)

  
