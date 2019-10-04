---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Kapslingskonfigurationer
ms.openlocfilehash: 54162cd72d2d1e7773e3be636bfa681329854498
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942372"
---
# <a name="nesting-dsc-configurations"></a>Kapslar av DSC-konfigurationer

En kapslad konfiguration (även kallad sammansatt konfiguration) är en konfiguration som anropas i en annan konfiguration som om den vore en resurs.
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

I det här exemplet använder `FileConfig` två obligatoriska parametrar, **CopyFrom** och **CopyTo**, som används som värden för egenskaperna **SourcePath** och **DestinationPath** i resurs blocket `File`.
@No__t-0-konfigurations anrop `FileConfig` som om den vore en resurs.
Egenskaperna i resurs blocket `NestedConfig` (**CopyFrom** och **CopyTo**) är parametrarna för @no__t 3-konfigurationen.

## <a name="see-also"></a>Se även

- [Sammansatta resurser – använda en DSC-konfiguration som en resurs](../resources/authoringResourceComposite.md)