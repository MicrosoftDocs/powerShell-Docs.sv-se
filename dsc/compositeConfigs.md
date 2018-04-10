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
# <a name="nesting-dsc-configurations"></a><span data-ttu-id="92da1-103">För många kapslade DSC-konfigurationer</span><span class="sxs-lookup"><span data-stu-id="92da1-103">Nesting DSC configurations</span></span>

<span data-ttu-id="92da1-104">En kapslad konfiguration (även kallat sammansatt konfiguration) är en konfiguration som kallas inom en annan konfiguration som om det vore en resurs.</span><span class="sxs-lookup"><span data-stu-id="92da1-104">A nested configuration (also called composite configuration) is a configuration that is called within another configuration as if it were a resource.</span></span>
<span data-ttu-id="92da1-105">Båda konfigurationerna måste definieras i samma fil.</span><span class="sxs-lookup"><span data-stu-id="92da1-105">Both configurations must be defined in the same file.</span></span>

<span data-ttu-id="92da1-106">Nu ska vi titta på ett enkelt exempel:</span><span class="sxs-lookup"><span data-stu-id="92da1-106">Let's look at a simple example:</span></span>

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

<span data-ttu-id="92da1-107">I det här exemplet `FileConfig` har två obligatoriska parametrar, **CopyFrom** och **CopyTo**, som används som värden för den **SourcePath** och  **DestinationPath** egenskaper i den `File` resursen block.</span><span class="sxs-lookup"><span data-stu-id="92da1-107">In this example, `FileConfig` takes two mandatory parameters,  **CopyFrom** and **CopyTo**, which are used as the values for the **SourcePath** and **DestinationPath** properties in the `File` resource block.</span></span>
<span data-ttu-id="92da1-108">Den `NestedConfig` configuration anrop `FileConfig` som om det vore en resurs.</span><span class="sxs-lookup"><span data-stu-id="92da1-108">The `NestedConfig` configuration calls `FileConfig` as if it were a resource.</span></span>
<span data-ttu-id="92da1-109">Egenskaperna i den `NestedConfig` resurs block (**CopyFrom** och **CopyTo**) är parametrar för den `FileConfig` konfiguration.</span><span class="sxs-lookup"><span data-stu-id="92da1-109">The properties in the `NestedConfig` resource block (**CopyFrom** and **CopyTo**) are the parameters of the `FileConfig` configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="92da1-110">Se även</span><span class="sxs-lookup"><span data-stu-id="92da1-110">See Also</span></span>

- [<span data-ttu-id="92da1-111">Sammansatta resurser--med hjälp av DSC-konfigurationen som en resurs</span><span class="sxs-lookup"><span data-stu-id="92da1-111">Composite resources--Using a DSC configuration as a resource</span></span>](authoringResourceComposite.md)