---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Kapslingskonfigurationer
description: Med DSC kan du skapa sammansatta konfigurationer genom att kapsla en konfiguration i en annan konfiguration.
ms.openlocfilehash: d7a81cb9673126e92e9185aacf19c5c7c17da8ca
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667427"
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

I det här exemplet `FileConfig` krävs två obligatoriska parametrar, **CopyFrom** och **CopyTo** , som används som värden för egenskaperna **SourcePath** och **DestinationPath** i `File` resurs blocket. `NestedConfig`Konfigurationen anropas `FileConfig` som om den vore en resurs. Egenskaperna i `NestedConfig` resurs blocket ( **CopyFrom** och **CopyTo** ) är parametrarna i `FileConfig` konfigurationen.

DSC stöder för närvarande inte kapsling av konfigurationer i kapslade konfigurationer. Du kan bara kapsla en djup konfiguration av en nivå.

## <a name="see-also"></a>Se även

- [Sammansatta resurser – använda en DSC-konfiguration som en resurs](../resources/authoringResourceComposite.md)
