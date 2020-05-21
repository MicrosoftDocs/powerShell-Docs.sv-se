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
# <a name="nesting-dsc-configurations"></a><span data-ttu-id="f32a5-103">Kapslar av DSC-konfigurationer</span><span class="sxs-lookup"><span data-stu-id="f32a5-103">Nesting DSC configurations</span></span>

<span data-ttu-id="f32a5-104">En kapslad konfiguration (även kallad sammansatt konfiguration) är en konfiguration som anropas i en annan konfiguration som om den vore en resurs.</span><span class="sxs-lookup"><span data-stu-id="f32a5-104">A nested configuration (also called composite configuration) is a configuration that's called within another configuration as if it were a resource.</span></span> <span data-ttu-id="f32a5-105">Båda konfigurationerna måste definieras i samma fil.</span><span class="sxs-lookup"><span data-stu-id="f32a5-105">Both configurations must be defined in the same file.</span></span>

<span data-ttu-id="f32a5-106">Nu ska vi titta på ett enkelt exempel:</span><span class="sxs-lookup"><span data-stu-id="f32a5-106">Let's look at a simple example:</span></span>

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

<span data-ttu-id="f32a5-107">I det här exemplet `FileConfig` krävs två obligatoriska parametrar, **CopyFrom** och **CopyTo**, som används som värden för egenskaperna **SourcePath** och **DestinationPath** i `File` resurs blocket.</span><span class="sxs-lookup"><span data-stu-id="f32a5-107">In this example, `FileConfig` takes two mandatory parameters, **CopyFrom** and **CopyTo**, which are used as the values for the **SourcePath** and **DestinationPath** properties in the `File` resource block.</span></span> <span data-ttu-id="f32a5-108">`NestedConfig`Konfigurationen anropas `FileConfig` som om den vore en resurs.</span><span class="sxs-lookup"><span data-stu-id="f32a5-108">The `NestedConfig` configuration calls `FileConfig` as if it were a resource.</span></span> <span data-ttu-id="f32a5-109">Egenskaperna i `NestedConfig` resurs blocket (**CopyFrom** och **CopyTo**) är parametrarna i `FileConfig` konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="f32a5-109">The properties in the `NestedConfig` resource block (**CopyFrom** and **CopyTo**) are the parameters of the `FileConfig` configuration.</span></span>

<span data-ttu-id="f32a5-110">DSC stöder för närvarande inte kapsling av konfigurationer i kapslade konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="f32a5-110">DSC doesn't currently support nesting configurations within nested configurations.</span></span> <span data-ttu-id="f32a5-111">Du kan bara kapsla en djup konfiguration av en nivå.</span><span class="sxs-lookup"><span data-stu-id="f32a5-111">You can only nest a configuration one layer deep.</span></span>

## <a name="see-also"></a><span data-ttu-id="f32a5-112">Se även</span><span class="sxs-lookup"><span data-stu-id="f32a5-112">See Also</span></span>

- [<span data-ttu-id="f32a5-113">Sammansatta resurser – använda en DSC-konfiguration som en resurs</span><span class="sxs-lookup"><span data-stu-id="f32a5-113">Composite resources--Using a DSC configuration as a resource</span></span>](../resources/authoringResourceComposite.md)
