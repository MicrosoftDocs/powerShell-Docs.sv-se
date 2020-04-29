---
ms.date: 09/09/2019
keywords: PowerShell, cmdlet
title: Bilaga 1 Kompatibilitetsalias
ms.openlocfilehash: 2351fdf23711fe1417f7e3fc3cca5b642d5a59fc
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "70848173"
---
# <a name="appendix-1---compatibility-aliases"></a>Bilaga 1 – kompatibilitets-alias

PowerShell har flera alias som gör att **UNIX** -och **cmd. exe** -användare kan använda välbekanta kommandon.
Kommandona och deras relaterade PowerShell-cmdlet och PowerShell-alias visas i följande tabell:

|cmd. exe-kommando|UNIX-kommando|PowerShell-cmdlet|PowerShell-alias|
|---------------|----------------|--------------|------------|
|**CLS**|**Rensa**|`Clear-Host`funktioner|`cls`|
|**exemplar**|**CP**|`Copy-Item`|`cpi`|
|**tillämpning**|**LS**|`Get-ChildItem`|`gci`|
|**bastyp**|**lat**|`Get-Content`|`gc`|
|**fart**|**MV**|`Move-Item`|`mi`|
|**MD**|**mkdir**|`New-Item`|`ni`|
|**PUSHD**|**PUSHD**|`Push-Location`|`pushd`|
|**POPD**|**POPD**|`Pop-Location`|`popd`|
|**del**, **Radera**, **RD**, **rmdir**|**RM**|`Remove-Item`|`ri`|
|**Outlook**|**MV**|`Rename-Item`|`rni`|
|**CD**, **chdir**|**installations**|`Set-Location`|`sl`|

Använd cmdleten [Get-alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) för att hitta PowerShell-alias. Om du vill visa en cmdlets alias använder du **definitions** parametern och anger namnet på cmdleten.
Eller, om du vill hitta ett Aliass cmdlet-namn, använder du parametern **Name** och anger aliaset.

```powershell
Get-Alias -Definition Get-ChildItem
```

```Output
CommandType     Name
-----------     ----
Alias           dir -> Get-ChildItem
Alias           gci -> Get-ChildItem
Alias           ls -> Get-ChildItem
```

```powershell
Get-Alias -Name gci
```

```Output
CommandType     Name
-----------     ----
Alias           gci -> Get-ChildItem
```
