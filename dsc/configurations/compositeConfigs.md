---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Kapslingskonfigurationer
ms.openlocfilehash: 54162cd72d2d1e7773e3be636bfa681329854498
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404744"
---
# <a name="nesting-dsc-configurations"></a>Kapsling DSC-konfigurationer

En kapslad konfiguration (även kallat sammansatt configuration) är en konfiguration som ska anropas i en annan konfiguration som om det vore en resurs.
Båda konfigurationerna måste definieras i samma fil.

Låt oss titta på ett enkelt exempel:

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

I det här exemplet `FileConfig` har två obligatoriska parametrar, **CopyFrom** och **CopyTo**, som används som värden för den **SourcePath** och  **Målsökväg** egenskaper i den `File` resource block.
Den `NestedConfig` configuration anrop `FileConfig` som om det vore en resurs.
Egenskaperna i den `NestedConfig` resource block (**CopyFrom** och **CopyTo**) är parametrarna för den `FileConfig` konfiguration.

## <a name="see-also"></a>Se även

- [Sammansatta resurser – med hjälp av en DSC-konfiguration som en resurs](../resources/authoringResourceComposite.md)