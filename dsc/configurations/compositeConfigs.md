---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Kapslingskonfigurationer
ms.openlocfilehash: 54162cd72d2d1e7773e3be636bfa681329854498
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684558"
---
# <a name="nesting-dsc-configurations"></a><span data-ttu-id="339fc-103">Kapsling DSC-konfigurationer</span><span class="sxs-lookup"><span data-stu-id="339fc-103">Nesting DSC configurations</span></span>

<span data-ttu-id="339fc-104">En kapslad konfiguration (även kallat sammansatt configuration) är en konfiguration som ska anropas i en annan konfiguration som om det vore en resurs.</span><span class="sxs-lookup"><span data-stu-id="339fc-104">A nested configuration (also called composite configuration) is a configuration that is called within another configuration as if it were a resource.</span></span>
<span data-ttu-id="339fc-105">Båda konfigurationerna måste definieras i samma fil.</span><span class="sxs-lookup"><span data-stu-id="339fc-105">Both configurations must be defined in the same file.</span></span>

<span data-ttu-id="339fc-106">Låt oss titta på ett enkelt exempel:</span><span class="sxs-lookup"><span data-stu-id="339fc-106">Let's look at a simple example:</span></span>

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

<span data-ttu-id="339fc-107">I det här exemplet `FileConfig` har två obligatoriska parametrar, **CopyFrom** och **CopyTo**, som används som värden för den **SourcePath** och  **Målsökväg** egenskaper i den `File` resource block.</span><span class="sxs-lookup"><span data-stu-id="339fc-107">In this example, `FileConfig` takes two mandatory parameters,  **CopyFrom** and **CopyTo**, which are used as the values for the **SourcePath** and **DestinationPath** properties in the `File` resource block.</span></span>
<span data-ttu-id="339fc-108">Den `NestedConfig` configuration anrop `FileConfig` som om det vore en resurs.</span><span class="sxs-lookup"><span data-stu-id="339fc-108">The `NestedConfig` configuration calls `FileConfig` as if it were a resource.</span></span>
<span data-ttu-id="339fc-109">Egenskaperna i den `NestedConfig` resource block (**CopyFrom** och **CopyTo**) är parametrarna för den `FileConfig` konfiguration.</span><span class="sxs-lookup"><span data-stu-id="339fc-109">The properties in the `NestedConfig` resource block (**CopyFrom** and **CopyTo**) are the parameters of the `FileConfig` configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="339fc-110">Se även</span><span class="sxs-lookup"><span data-stu-id="339fc-110">See Also</span></span>

- [<span data-ttu-id="339fc-111">Sammansatta resurser – med hjälp av en DSC-konfiguration som en resurs</span><span class="sxs-lookup"><span data-stu-id="339fc-111">Composite resources--Using a DSC configuration as a resource</span></span>](../resources/authoringResourceComposite.md)