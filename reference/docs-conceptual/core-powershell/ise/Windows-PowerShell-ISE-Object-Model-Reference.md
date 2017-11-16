---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Windows PowerShell ISE objektreferens modellen
ms.assetid: e1a9e7d1-0fd5-47de-8d9b-f1be1ed13b0c
ms.openlocfilehash: 624ddca3895ba3e24bf52a27babdb07e8714baae
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/08/2017
---
# <a name="windows-powershell-ise-object-model-reference"></a>Windows PowerShell ISE objektreferens modellen
  
## <a name="object-model-reference"></a>Objektreferens för modellen
 Det här avsnittet innehåller en referens om de underliggande klasser som definierar de olika objekt inWindows PowerShell® Integrated Scripting Environment (ISE). Objekten ordnade i deras hierarki finns [i ISE modellen objekthierarkin](The-ISE-Object-Model-Hierarchy.md).

 [Objektet ISEAddOnTool](The-ISEAddOnTool-Object.md) exempel: $psISE.CurrentVisibleHorizontalTool, $psISE.CurrentVisibleVerticalTool.

 [Objektet ISEAddOnTool](The-ISEAddOnTool-Object.md) [ISEEditor objektet](The-ISEEditor-Object.md) exempel: $psISE.CurrentFile.Editor, $psISE.CurrentPowerShellTab.Output, $psISE.CurrentPowerShellTab.CommandPane.

 [Objektet ISEFile](The-ISEFile-Object.md) exempel: $psISE.CurrentFile, $psISE.PowerShellTabs.Files\[0\].

 [Objektet ISEFileCollection](The-ISEFileCollection-Object.md) exempel: $psISE.PowerShellTabs.Files.

 [Objektet ISEMenuItem](The-ISEMenuItem-Object.md) exempel: $psISE.CurrentPowerShellTab.AddOnsMenu, $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus\[0\].

 [Objektet ISEMenuItemCollection](The-ISEMenuItemCollection-Object.md) exempel: $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.

 [Objektet ISEOptions](The-ISEOptions-Object.md) exempel: $psISE.Options, $psISE.Options.DefaultOptions.

 [Objektet ObjectModelRoot](The-ObjectModelRoot-Object.md) exempel: rotobjektet $psISE.

 [Objektet PowerShellTab](The-PowerShellTab-Object.md) exempel: $psISE.CurrentPowerShellTab, $psISE.PowerShellTabs\[0\].

 [Objektet PowerShellTabCollection](The-PowerShellTabCollection-Object.md) exempel: $psISE.PowerShellTabs.

## <a name="see-also"></a>Se även
- [Windows PowerShell ISE Scripting Object Model](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
