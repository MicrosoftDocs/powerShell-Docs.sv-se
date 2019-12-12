---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: PowerShellTabCollection-objektet
ms.openlocfilehash: 5a1318534ddce19c2f5faa0d2013e2b38d8b79e5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030487"
---
# <a name="the-powershelltabcollection-object"></a>PowerShellTabCollection-objektet

**PowerShellTab** Collection-objektet är en samling **PowerShellTab** -objekt. Varje **PowerShellTab** -objekt fungerar som en separat körnings miljö. Det är en instans av klassen Microsoft. PowerShell. Host. ISE. PowerShellTabs. Ett exempel är **$psISE. PowerShellTabs** -objektet.

## <a name="methods"></a>Metoder

### <a name="add"></a>Lägg till\(\)

Stöds i Windows PowerShell ISE 2,0 och senare.

Lägger till en ny PowerShell-flik i samlingen. Den returnerar den nyligen tillagda fliken.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a>Ta bort\(Microsoft. PowerShell. Host. ISE. PowerShellTab psTab\)

Stöds i Windows PowerShell ISE 2,0 och senare.

Tar bort den flik som anges av parametern **psTab** .

**psTab** PowerShell-fliken som ska tas bort.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a>SetSelectedPowerShellTab\(Microsoft. PowerShell. Host. ISE. PowerShellTab psTab\)

Stöds i Windows PowerShell ISE 2,0 och senare.

Väljer den PowerShell-flik som anges av parametern **psTab** för att göra den till den aktuella aktiva PowerShell-fliken.

**psTab** På fliken PowerShell väljer du.

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

- [PowerShellTab-objektet](The-PowerShellTab-Object.md)
- [Syftet med Windows PowerShell ISE-skriptets objekt modell](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarki för ISE-objektmodellen](The-ISE-Object-Model-Hierarchy.md)
