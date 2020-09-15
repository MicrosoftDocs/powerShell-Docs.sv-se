---
ms.date: 08/03/2020
keywords: powershell,cmdlet
title: Bilaga 1 Kompatibilitetsalias
ms.openlocfilehash: e5bd170fea6b6109d2ef4fd58863d6cc8a0e3ae1
ms.sourcegitcommit: d3f78120bdc9096c72aa0dfdbdd91efaf254c738
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87758507"
---
# <a name="appendix-1---compatibility-aliases"></a>Bilaga 1 – kompatibilitets-alias

PowerShell har flera alias som låter **UNIX** -och **cmd.exe** användare använda välbekanta kommandon.
Kommandona och deras relaterade PowerShell-cmdlet och PowerShell-alias visas i följande tabell:

|            cmd.exe kommando            | UNIX-kommando | PowerShell-cmdlet | PowerShell-alias |
| ------------------------------------- | ------------ | ----------------- | ---------------- |
| **CD**, **chdir**                     | **installations**       | `Set-Location`    | `sl`             |
| **CLS**                               | **Rensa**    | `Clear-Host`      | `cls`            |
| **exemplar**                              | **CP**       | `Copy-Item`       | `cpi`            |
| **del**, **Radera**, **RD**, **rmdir** | **RM**       | `Remove-Item`     | `ri`             |
| **tillämpning**                               | **LS**       | `Get-ChildItem`   | `gci`            |
| **eko**                              | **eko**     | `Write-Output`    | `write`          |
| **MD**                                | **mkdir**    | `New-Item`        | `ni`             |
| **fart**                              | **MV**       | `Move-Item`       | `mi`             |
| **POPD**                              | **POPD**     | `Pop-Location`    | `popd`           |
| **PUSHD**                             | **PUSHD**    | `Push-Location`   | `pushd`          |
| **Outlook**                               | **MV**       | `Rename-Item`     | `rni`            |
| **bastyp**                              | **lat**      | `Get-Content`     | `gc`             |

Använd cmdleten [Get-alias](xref:Microsoft.PowerShell.Utility.Get-Alias) för att hitta PowerShell-alias. Om du vill visa en cmdlets alias använder du **definitions** parametern och anger namnet på cmdleten.
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
