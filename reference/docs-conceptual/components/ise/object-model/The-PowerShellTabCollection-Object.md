---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: PowerShellTabCollection-objektet
ms.openlocfilehash: 5a1318534ddce19c2f5faa0d2013e2b38d8b79e5
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030487"
---
# <a name="the-powershelltabcollection-object"></a>PowerShellTabCollection-objektet

Den **PowerShellTab** samlingsobjektet är en samling **PowerShellTab** objekt. Varje **PowerShellTab** objektet fungerar som en separat körningsmiljö. Det är en instans av klassen Microsoft.PowerShell.Host.ISE.PowerShellTabs. Ett exempel är den **$psISE.PowerShellTabs** objekt.

## <a name="methods"></a>Metoder

### <a name="add"></a>Lägg till\(\)

Stöds i Windows PowerShell ISE 2.0 och senare.

Lägger till en ny PowerShell-flik i samlingen. Returnerar den nya fliken.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a>Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)

Stöds i Windows PowerShell ISE 2.0 och senare.

Tar bort fliken som anges av den **psTab** parametern.

**psTab** PowerShell-flik för att ta bort.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a>SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)

Stöds i Windows PowerShell ISE 2.0 och senare.

Väljer fliken PowerShell som anges av den **psTab** parametern så att de blir aktiva PowerShell-flik.

**psTab** PowerShell-fliken väljer.

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

- [The PowerShellTab Object](The-PowerShellTab-Object.md)
- [Syftet med den Windows PowerShell ISE-Skriptobjektmodellen](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarki för ISE-objektmodellen](The-ISE-Object-Model-Hierarchy.md)
