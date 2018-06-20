---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: PowerShellTabCollection-objektet
ms.assetid: 81f4bf4a-83bf-415e-8378-1703792fbb58
ms.openlocfilehash: d9088b26de35360b8258d3f15924b3010a986d15
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
ms.locfileid: "30953080"
---
# <a name="the-powershelltabcollection-object"></a>PowerShellTabCollection-objektet

Den **PowerShellTab** samlingsobjektet är en samling **PowerShellTab** objekt. Varje **PowerShellTab** objekt som fungerar som en separat körningsmiljö. Det är en instans av klassen Microsoft.PowerShell.Host.ISE.PowerShellTabs. Ett exempel är den **$psISE.PowerShellTabs** objekt.

## <a name="methods"></a>Metoder

### <a name="add"></a>Lägg till\(\)

Stöds i Windows PowerShell ISE 2.0 och senare.

Lägger till en ny PowerShell-flik i samlingen. Returnerar den nytillagda fliken.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a>Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)

Stöds i Windows PowerShell ISE 2.0 och senare.

Tar bort fliken som anges av den **psTab** parameter.

**psTab** i PowerShell fliken om du vill ta bort.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a>SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)

Stöds i Windows PowerShell ISE 2.0 och senare.

Väljer du fliken PowerShell som anges av den **psTab** parametern så att den aktiva PowerShell-fliken.

**psTab** i PowerShell tab för att markera.

```powershell
# Save the current tab in a variable and rename it
$oldTab = $psISE.CurrentPowerShellTab
$psISE.CurrentPowerShellTab.DisplayName = 'Old Tab'
# Create a new tab and give it a new display name
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
# Switch back to the original tab
$psISE.PowerShellTabs.SelectedPowerShellTab = $oldTab
```

## <a name="see-also"></a>Se även

- [Objektet PowerShellTab](The-PowerShellTab-Object.md)
- [Syftet med Windows PowerShell ISE Scripting Object Model](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarki för ISE-objektmodellen](The-ISE-Object-Model-Hierarchy.md)