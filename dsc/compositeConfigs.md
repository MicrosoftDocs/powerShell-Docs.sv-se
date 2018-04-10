---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: Kapslingskonfigurationer
ms.openlocfilehash: 9c6dbce462f7481e5714039a95ae85f85be0072e
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="nesting-dsc-configurations"></a>För många kapslade DSC-konfigurationer

En kapslad konfiguration (även kallat sammansatt konfiguration) är en konfiguration som kallas inom en annan konfiguration som om det vore en resurs.
Båda konfigurationerna måste definieras i samma fil.

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

I det här exemplet `FileConfig` har två obligatoriska parametrar, **CopyFrom** och **CopyTo**, som används som värden för den **SourcePath** och  **DestinationPath** egenskaper i den `File` resursen block.
Den `NestedConfig` configuration anrop `FileConfig` som om det vore en resurs.
Egenskaperna i den `NestedConfig` resurs block (**CopyFrom** och **CopyTo**) är parametrar för den `FileConfig` konfiguration.

## <a name="see-also"></a>Se även

- [Sammansatta resurser--med hjälp av DSC-konfigurationen som en resurs](authoringResourceComposite.md)