---
ms.date: 06/05/2017
title: PowerShellTabCollection-objektet
description: PowerShellTab Collection-objektet är en samling PowerShellTab-objekt. Varje PowerShellTab-objekt fungerar som en separat körnings miljö.
ms.openlocfilehash: 60f8001f096b50bd8433a5685f1f70a350f07f61
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92658269"
---
# <a name="the-powershelltabcollection-object"></a>PowerShellTabCollection-objektet

**PowerShellTab** Collection-objektet är en samling **PowerShellTab** -objekt. Varje **PowerShellTab** -objekt fungerar som en separat körnings miljö. Det är en instans av klassen Microsoft. PowerShell. Host. ISE. PowerShellTabs. Ett exempel är `$psISE.PowerShellTabs` objektet.

## <a name="methods"></a>Metoder

### <a name="add"></a>Skapa\(\)

Stöds i Windows PowerShell ISE 2,0 och senare.

Lägger till en ny PowerShell-flik i samlingen. Den returnerar den nyligen tillagda fliken.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a>Ta bort \( Microsoft. PowerShell. Host. ISE. PowerShellTab psTab\)

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

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a>SetSelectedPowerShellTab \( Microsoft. PowerShell. Host. ISE. PowerShellTab psTab\)

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
- [Användningsområden för Windows PowerShell ISE-skriptobjektmodellen](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Objekt modells-hierarkin för ISE](The-ISE-Object-Model-Hierarchy.md)
