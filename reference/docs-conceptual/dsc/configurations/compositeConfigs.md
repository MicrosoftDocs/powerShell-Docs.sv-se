---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Kapslingskonfigurationer
ms.openlocfilehash: e74c0fe1d7f7b198c2d6f796c0bf120eb0ec21d9
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83564025"
---
# <a name="nesting-dsc-configurations"></a>Kapslar av DSC-konfigurationer

En kapslad konfiguration (även kallad sammansatt konfiguration) är en konfiguration som anropas i en annan konfiguration som om den vore en resurs. Båda konfigurationerna måste definieras i samma fil.

Nu ska vi titta på ett enkelt exempel:

```powershell
Configuration FileConfig
{
    param (
        [Parameter(Mandatory = $true)]
        [String] $CopyFrom,

        [Parameter(Mandatory = $true)]
        [String] $CopyTo
    )

    Import-DscResource -ModuleName PSDesiredStateConfiguration

    File FileTest
    {
        SourcePath = $CopyFrom
        DestinationPath = $CopyTo
        Ensure = 'Present'
    }
}

Configuration NestedFileConfig
{
    Node localhost
    {
        FileConfig NestedConfig
        {
            CopyFrom = 'C:\Test\TestFile.txt'
            CopyTo = 'C:\Test2'
        }
    }
}
```

I det här exemplet `FileConfig` krävs två obligatoriska parametrar, **CopyFrom** och **CopyTo**, som används som värden för egenskaperna **SourcePath** och **DestinationPath** i `File` resurs blocket. `NestedConfig`Konfigurationen anropas `FileConfig` som om den vore en resurs. Egenskaperna i `NestedConfig` resurs blocket (**CopyFrom** och **CopyTo**) är parametrarna i `FileConfig` konfigurationen.

DSC stöder för närvarande inte kapsling av konfigurationer i kapslade konfigurationer. Du kan bara kapsla en djup konfiguration av en nivå.

## <a name="see-also"></a>Se även

- [Sammansatta resurser – använda en DSC-konfiguration som en resurs](../resources/authoringResourceComposite.md)
