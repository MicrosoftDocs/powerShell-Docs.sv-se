---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Objektet ISEAddOnToolCollection
ms.assetid: 634eab89-0845-4016-974b-361b09bb8f7b
ms.openlocfilehash: ba8b4e0e3952226407f00dea8b32785633256089
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/03/2017
---
# <a name="the-iseaddontoolcollection-object"></a>Objektet ISEAddOnToolCollection
  Den **ISEAddOnToolCollection** objekt är en samling **ISEAddOnTool** objekt. Ett exempel är den **$psISE.CurrentPowerShellTab.VerticalAddOnTools** objekt.

## <a name="methods"></a>Metoder

### <a name="add-name-controltype-isvisible-"></a>Lägg till\( namn, kontrolltyp, \[IsVisible\]\)
  Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner. 

 Lägger till ett nytt tilläggsverktyg i samlingen. Returnerar den nytillagda tilläggsverktyg. Innan du kör det här kommandot måste du installera verktyget tillägg på den lokala datorn och att läsa in sammansättningen.

 **Namnet** -sträng Anger visningsnamnet för verktyget tillägg som har lagts till i Windows PowerShell ISE.

 **Kontrolltyp** -typen anger den kontroll som har lagts till.

 **\[IsVisible\]**  -valfritt booleskt om **$true**, verktyget tillägg visas omedelbart i associerade verktygsfönstret.

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="remove-item-"></a>Ta bort\( objekt\)
  Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner. 

 Tar bort den angivna tilläggsverktyg från samlingen.

 **Objektet** -Microsoft.PowerShell.Host.ISE.ISEAddOnTool anger objektet som ska tas bort från Windows PowerShell ISE.

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="setselectedpowershelltab-pstab-"></a>SetSelectedPowerShellTab\( psTab\)
  Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner. 

 Väljer du PowerShell fliken som den **psTab** parametern anger.

 **psTab** -Microsoft.PowerShell.Host.ISE.PowerShellTab i PowerShell tab för att markera.

```powershell
      $newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="Brand New Tab"
```

### <a name="remove-pstab-"></a>Ta bort\( psTab\)
  Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner. 

 Tar bort PowerShell fliken som den **psTab** parametern anger.

 **psTab** -Microsoft.PowerShell.Host.ISE.PowerShellTab i PowerShell fliken om du vill ta bort.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="This tab will go away in 5 seconds" 
sleep 5 
$psISE.PowerShellTabs.Remove($newTab)
```

## <a name="see-also"></a>Se även
- [Objektet PowerShellTab](The-PowerShellTab-Object.md) 
- [Windows PowerShell ISE Scripting Object Model](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Windows PowerShell ISE objektreferens modellen](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [Modellen objekthierarkin ISE](The-ISE-Object-Model-Hierarchy.md)

  