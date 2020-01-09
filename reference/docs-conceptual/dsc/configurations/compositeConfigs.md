---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Kapslingskonfigurationer
ms.openlocfilehash: 07e4fb5b9d406153d2fbb4285e28b8d1f0dfdcf5
ms.sourcegitcommit: 1b88c280dd0799f225242608f0cbdab485357633
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/25/2019
ms.locfileid: "75417863"
---
# <a name="nesting-dsc-configurations"></a><span data-ttu-id="b4bf9-103">Kapslar av DSC-konfigurationer</span><span class="sxs-lookup"><span data-stu-id="b4bf9-103">Nesting DSC configurations</span></span>

<span data-ttu-id="b4bf9-104">En kapslad konfiguration (även kallad sammansatt konfiguration) är en konfiguration som anropas i en annan konfiguration som om den vore en resurs.</span><span class="sxs-lookup"><span data-stu-id="b4bf9-104">A nested configuration (also called composite configuration) is a configuration that's called within another configuration as if it were a resource.</span></span> <span data-ttu-id="b4bf9-105">Båda konfigurationerna måste definieras i samma fil.</span><span class="sxs-lookup"><span data-stu-id="b4bf9-105">Both configurations must be defined in the same file.</span></span>

<span data-ttu-id="b4bf9-106">Nu ska vi titta på ett enkelt exempel:</span><span class="sxs-lookup"><span data-stu-id="b4bf9-106">Let's look at a simple example:</span></span>

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

<span data-ttu-id="b4bf9-107">I det här exemplet tar `FileConfig` två obligatoriska parametrar, **CopyFrom** och **CopyTo**, som används som värden för egenskaperna **SourcePath** och **DestinationPath** i resurs blocket `File`.</span><span class="sxs-lookup"><span data-stu-id="b4bf9-107">In this example, `FileConfig` takes two mandatory parameters, **CopyFrom** and **CopyTo**, which are used as the values for the **SourcePath** and **DestinationPath** properties in the `File` resource block.</span></span> <span data-ttu-id="b4bf9-108">`NestedConfig` konfigurations anrop `FileConfig` som om det var en resurs.</span><span class="sxs-lookup"><span data-stu-id="b4bf9-108">The `NestedConfig` configuration calls `FileConfig` as if it were a resource.</span></span> <span data-ttu-id="b4bf9-109">Egenskaperna i `NestedConfig` Resource block (**CopyFrom** och **CopyTo**) är parametrarna i `FileConfig`-konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="b4bf9-109">The properties in the `NestedConfig` resource block (**CopyFrom** and **CopyTo**) are the parameters of the `FileConfig` configuration.</span></span>

<span data-ttu-id="b4bf9-110">DSC stöder för närvarande inte kapsling av konfigurationer i kapslade konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="b4bf9-110">DSC doesn't currently support nesting configurations within nested configurations.</span></span> <span data-ttu-id="b4bf9-111">Du kan bara kapsla en djup konfiguration av en nivå.</span><span class="sxs-lookup"><span data-stu-id="b4bf9-111">You can only nest a configuration one layer deep.</span></span>

## <a name="see-also"></a><span data-ttu-id="b4bf9-112">Se även</span><span class="sxs-lookup"><span data-stu-id="b4bf9-112">See Also</span></span>

- [<span data-ttu-id="b4bf9-113">Sammansatta resurser – använda en DSC-konfiguration som en resurs</span><span class="sxs-lookup"><span data-stu-id="b4bf9-113">Composite resources--Using a DSC configuration as a resource</span></span>](../resources/authoringResourceComposite.md)