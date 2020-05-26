---
ms.date: 12/31/2019
keywords: powershell,cmdlet
title: ISEAddOnToolCollection-objektet
ms.openlocfilehash: e07a47169381307b50ac190165307c926b4ad94e
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83811032"
---
# <a name="the-iseaddontoolcollection-object"></a>ISEAddOnToolCollection-objektet

**ISEAddOnToolCollection** -objektet är en samling av **ISEAddOnTool** -objekt. Ett exempel är `$psISE.CurrentPowerShellTab.VerticalAddOnTools` objektet.

## <a name="methods"></a>Metoder

### <a name="add-name-controltype-isvisible-"></a>Lägg till \( namn, ControlType, \[ IsVisible \]\)

Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.

Lägger till ett nytt tilläggs verktyg i samlingen. Det returnerar det nyligen tillagda tilläggs verktyget. Innan du kör det här kommandot måste du installera tilläggs verktyget på den lokala datorn och läsa in sammansättningen.

**Name** -sträng anger visnings namnet för det tilläggs verktyg som läggs till Windows PowerShell ISE.

**ControlType** – typ anger den kontroll som läggs till.

** \[ IsVisible \] ** – valfria booleska om det är inställt på `$true` , visas tilläggs verktyget direkt i det associerade verktygs fönstret.

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="remove-item-"></a>Ta bort \( objekt\)

Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.

Tar bort det angivna tilläggs verktyget från samlingen.

**Objekt** -Microsoft. PowerShell. Host. ISE. ISEAddOnTool anger det objekt som ska tas bort från Windows PowerShell ISE.

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="setselectedpowershelltab-pstab-"></a>SetSelectedPowerShellTab \( psTab\)

Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.

Väljer PowerShell-fliken som **psTab** -parametern anger.

**psTab** -Microsoft. PowerShell. Host. ISE. PowerShellTab på PowerShell-fliken för att välja.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="remove-pstab-"></a>Ta bort \( psTab\)

Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.

Tar bort PowerShell-fliken som **psTab** -parametern anger.

**psTab** -Microsoft. PowerShell. Host. ISE. PowerShellTab på PowerShell-fliken för att ta bort.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

## <a name="see-also"></a>Se även

- [PowerShellTab-objektet](The-PowerShellTab-Object.md)
- [Användningsområden för Windows PowerShell ISE-skriptobjektmodellen](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Objekt modells-hierarkin för ISE](The-ISE-Object-Model-Hierarchy.md)
