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
# <a name="nesting-dsc-configurations"></a><span data-ttu-id="68046-103">Kapslar av DSC-konfigurationer</span><span class="sxs-lookup"><span data-stu-id="68046-103">Nesting DSC configurations</span></span>

<span data-ttu-id="68046-104">En kapslad konfiguration (även kallad sammansatt konfiguration) är en konfiguration som anropas i en annan konfiguration som om den vore en resurs.</span><span class="sxs-lookup"><span data-stu-id="68046-104">A nested configuration (also called composite configuration) is a configuration that is called within another configuration as if it were a resource.</span></span>
<span data-ttu-id="68046-105">Båda konfigurationerna måste definieras i samma fil.</span><span class="sxs-lookup"><span data-stu-id="68046-105">Both configurations must be defined in the same file.</span></span>

<span data-ttu-id="68046-106">Nu ska vi titta på ett enkelt exempel:</span><span class="sxs-lookup"><span data-stu-id="68046-106">Let's look at a simple example:</span></span>

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

<span data-ttu-id="68046-107">I det här exemplet använder `FileConfig` två obligatoriska parametrar, **CopyFrom** och **CopyTo**, som används som värden för egenskaperna **SourcePath** och **DestinationPath** i resurs blocket `File`.</span><span class="sxs-lookup"><span data-stu-id="68046-107">In this example, `FileConfig` takes two mandatory parameters,  **CopyFrom** and **CopyTo**, which are used as the values for the **SourcePath** and **DestinationPath** properties in the `File` resource block.</span></span>
<span data-ttu-id="68046-108">@No__t-0-konfigurations anrop `FileConfig` som om den vore en resurs.</span><span class="sxs-lookup"><span data-stu-id="68046-108">The `NestedConfig` configuration calls `FileConfig` as if it were a resource.</span></span>
<span data-ttu-id="68046-109">Egenskaperna i resurs blocket `NestedConfig` (**CopyFrom** och **CopyTo**) är parametrarna för @no__t 3-konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="68046-109">The properties in the `NestedConfig` resource block (**CopyFrom** and **CopyTo**) are the parameters of the `FileConfig` configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="68046-110">Se även</span><span class="sxs-lookup"><span data-stu-id="68046-110">See Also</span></span>

- [<span data-ttu-id="68046-111">Sammansatta resurser – använda en DSC-konfiguration som en resurs</span><span class="sxs-lookup"><span data-stu-id="68046-111">Composite resources--Using a DSC configuration as a resource</span></span>](../resources/authoringResourceComposite.md)