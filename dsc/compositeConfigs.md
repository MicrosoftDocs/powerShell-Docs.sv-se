---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: Kapsling konfigurationer
ms.openlocfilehash: 4de53b94056df46d74923dda56e02841cfac2cd1
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="nesting-dsc-configurations"></a><span data-ttu-id="d4843-103">För många kapslade DSC-konfigurationer</span><span class="sxs-lookup"><span data-stu-id="d4843-103">Nesting DSC configurations</span></span>

<span data-ttu-id="d4843-104">En kapslad konfiguration (även kallat sammansatt konfiguration) är en konfiguration som kallas inom en annan konfiguration som om det vore en resurs.</span><span class="sxs-lookup"><span data-stu-id="d4843-104">A nested configuration (also called composite configuration) is a configuration that is called within another configuration as if it were a resource.</span></span>
<span data-ttu-id="d4843-105">Båda konfigurationerna måste definieras i samma fil.</span><span class="sxs-lookup"><span data-stu-id="d4843-105">Both configurations must be defined in the same file.</span></span>

<span data-ttu-id="d4843-106">Nu ska vi titta på ett enkelt exempel:</span><span class="sxs-lookup"><span data-stu-id="d4843-106">Let's look at a simple example:</span></span>

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

<span data-ttu-id="d4843-107">I det här exemplet `FileConfig` har två obligatoriska parametrar, **CopyFrom** och **CopyTo**, som används som värden för den **SourcePath** och  **DestinationPath** egenskaper i den `File` resursen block.</span><span class="sxs-lookup"><span data-stu-id="d4843-107">In this example, `FileConfig` takes two mandatory parameters,  **CopyFrom** and **CopyTo**, which are used as the values for the **SourcePath** and **DestinationPath** properties in the `File` resource block.</span></span> <span data-ttu-id="d4843-108">Den `NestedConfig` configuration anrop `FileConfig` som om det vore en resurs.</span><span class="sxs-lookup"><span data-stu-id="d4843-108">The `NestedConfig` configuration calls `FileConfig` as if it were a resource.</span></span>
<span data-ttu-id="d4843-109">Egenskaperna i den `NestedConfig` resurs block (**CopyFrom** och **CopyTo**) är parametrar för den `FileConfig` konfiguration.</span><span class="sxs-lookup"><span data-stu-id="d4843-109">The properties in the `NestedConfig` resource block (**CopyFrom** and **CopyTo**) are the parameters of the `FileConfig` configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="d4843-110">Se även</span><span class="sxs-lookup"><span data-stu-id="d4843-110">See Also</span></span>

- [<span data-ttu-id="d4843-111">Sammansatta resurser--med hjälp av DSC-konfigurationen som en resurs</span><span class="sxs-lookup"><span data-stu-id="d4843-111">Composite resources--Using a DSC configuration as a resource</span></span>](authoringResourceComposite.md)

