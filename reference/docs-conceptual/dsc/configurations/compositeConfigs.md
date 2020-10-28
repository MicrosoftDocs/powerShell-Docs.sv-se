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
# <a name="nesting-dsc-configurations"></a><span data-ttu-id="6c502-104">Kapslar av DSC-konfigurationer</span><span class="sxs-lookup"><span data-stu-id="6c502-104">Nesting DSC configurations</span></span>

<span data-ttu-id="6c502-105">En kapslad konfiguration (även kallad sammansatt konfiguration) är en konfiguration som anropas i en annan konfiguration som om den vore en resurs.</span><span class="sxs-lookup"><span data-stu-id="6c502-105">A nested configuration (also called composite configuration) is a configuration that's called within another configuration as if it were a resource.</span></span> <span data-ttu-id="6c502-106">Båda konfigurationerna måste definieras i samma fil.</span><span class="sxs-lookup"><span data-stu-id="6c502-106">Both configurations must be defined in the same file.</span></span>

<span data-ttu-id="6c502-107">Nu ska vi titta på ett enkelt exempel:</span><span class="sxs-lookup"><span data-stu-id="6c502-107">Let's look at a simple example:</span></span>

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

<span data-ttu-id="6c502-108">I det här exemplet `FileConfig` krävs två obligatoriska parametrar, **CopyFrom** och **CopyTo** , som används som värden för egenskaperna **SourcePath** och **DestinationPath** i `File` resurs blocket.</span><span class="sxs-lookup"><span data-stu-id="6c502-108">In this example, `FileConfig` takes two mandatory parameters, **CopyFrom** and **CopyTo** , which are used as the values for the **SourcePath** and **DestinationPath** properties in the `File` resource block.</span></span> <span data-ttu-id="6c502-109">`NestedConfig`Konfigurationen anropas `FileConfig` som om den vore en resurs.</span><span class="sxs-lookup"><span data-stu-id="6c502-109">The `NestedConfig` configuration calls `FileConfig` as if it were a resource.</span></span> <span data-ttu-id="6c502-110">Egenskaperna i `NestedConfig` resurs blocket ( **CopyFrom** och **CopyTo** ) är parametrarna i `FileConfig` konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="6c502-110">The properties in the `NestedConfig` resource block ( **CopyFrom** and **CopyTo** ) are the parameters of the `FileConfig` configuration.</span></span>

<span data-ttu-id="6c502-111">DSC stöder för närvarande inte kapsling av konfigurationer i kapslade konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="6c502-111">DSC doesn't currently support nesting configurations within nested configurations.</span></span> <span data-ttu-id="6c502-112">Du kan bara kapsla en djup konfiguration av en nivå.</span><span class="sxs-lookup"><span data-stu-id="6c502-112">You can only nest a configuration one layer deep.</span></span>

## <a name="see-also"></a><span data-ttu-id="6c502-113">Se även</span><span class="sxs-lookup"><span data-stu-id="6c502-113">See Also</span></span>

- [<span data-ttu-id="6c502-114">Sammansatta resurser – använda en DSC-konfiguration som en resurs</span><span class="sxs-lookup"><span data-stu-id="6c502-114">Composite resources--Using a DSC configuration as a resource</span></span>](../resources/authoringResourceComposite.md)
