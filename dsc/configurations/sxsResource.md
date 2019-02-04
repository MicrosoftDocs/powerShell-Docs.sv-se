---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Importera en specifik version av en installerad resurs
ms.openlocfilehash: 5ed81e11aa67eb6590d958647f48a33b1b5f1c0e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55683886"
---
# <a name="import-a-specific-version-of-an-installed-resource"></a><span data-ttu-id="6041d-103">Importera en specifik version av en installerad resurs</span><span class="sxs-lookup"><span data-stu-id="6041d-103">Import a specific version of an installed resource</span></span>

> <span data-ttu-id="6041d-104">Gäller för: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="6041d-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="6041d-105">Olika versioner av DSC-resurser kan installeras på en dator sida vid sida i PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="6041d-105">In PowerShell 5.0, separate versions of DSC resources can be installed on a computer side by side.</span></span> <span data-ttu-id="6041d-106">En Resursmodul kan lagra olika versioner av en resurs i version med namnet mappar.</span><span class="sxs-lookup"><span data-stu-id="6041d-106">A resource module can store separate versions of a resource in version named folders.</span></span>

## <a name="installing-separate-resource-versions-side-by-side"></a><span data-ttu-id="6041d-107">Installation av separat resurs versioner sida vid sida</span><span class="sxs-lookup"><span data-stu-id="6041d-107">Installing separate resource versions side by side</span></span>

<span data-ttu-id="6041d-108">Du kan använda den **MinimumVersion**, **MaximumVersion**, och **RequiredVersion** parametrarna för den [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet för att ange vilken version av en modul för att installera.</span><span class="sxs-lookup"><span data-stu-id="6041d-108">You can use the **MinimumVersion**, **MaximumVersion**, and **RequiredVersion** parameters of the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to specify which version of a module to install.</span></span> <span data-ttu-id="6041d-109">Anropa **Install-Module** utan att ange en version som installerar den senaste versionen.</span><span class="sxs-lookup"><span data-stu-id="6041d-109">Calling **Install-Module** without specifying a version installs the most recent version.</span></span>

<span data-ttu-id="6041d-110">Exempel: det finns flera versioner av den **xFailOverCluster** modulen, som innehåller en **xCluster** resurs.</span><span class="sxs-lookup"><span data-stu-id="6041d-110">For example, there are multiple versions of the **xFailOverCluster** module, each of which contains an **xCluster** resource.</span></span> <span data-ttu-id="6041d-111">Anropa **Install-Module** utan att ange versionen tal installerar den senaste versionen av modulen.</span><span class="sxs-lookup"><span data-stu-id="6041d-111">Calling **Install-Module** without specifying the version number installs the most recent version of the module.</span></span>

```powershell
PS> Install-Module xFailOverCluster
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, ...
```

<span data-ttu-id="6041d-112">Om du vill installera en specifik version av en modul, ange en **RequiredVersion** av 1.1.0.0.</span><span class="sxs-lookup"><span data-stu-id="6041d-112">To install a specific version of a module, specify a **RequiredVersion** of 1.1.0.0.</span></span> <span data-ttu-id="6041d-113">Då installeras den angivna versionen sida vid sida med den installerade versionen.</span><span class="sxs-lookup"><span data-stu-id="6041d-113">This installs the specified version side by side with the installed version.</span></span>

```powershell
PS> Install-Module xFailOverCluster -RequiredVersion 1.1
```

<span data-ttu-id="6041d-114">Nu kan du se både versionen av modulen visas när du använder `Get-DSCResource`.</span><span class="sxs-lookup"><span data-stu-id="6041d-114">Now, you see both version of the module listed when you use `Get-DSCResource`.</span></span>

```powershell
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## <a name="specifying-a-resource-version-in-a-configuration"></a><span data-ttu-id="6041d-115">Ange en resurs-version i en konfiguration</span><span class="sxs-lookup"><span data-stu-id="6041d-115">Specifying a resource version in a configuration</span></span>

<span data-ttu-id="6041d-116">Om du har en separat resurs versioner installerade på en dator, måste du ange vilken version av den här resursen när du använder den i en konfiguration.</span><span class="sxs-lookup"><span data-stu-id="6041d-116">If you have separate resource versions installed on a computer, you must specify the version of that resource when you use it in a configuration.</span></span> <span data-ttu-id="6041d-117">Du gör detta genom att ange den **ModuleVersion** -parametern för den **Import-DscResource** nyckelord.</span><span class="sxs-lookup"><span data-stu-id="6041d-117">You do this by specifying the **ModuleVersion** parameter of the **Import-DscResource** keyword.</span></span> <span data-ttu-id="6041d-118">Om du inte ange versionen av en Resursmodul för en resurs som du har mer än en version som är installerad, genereras ett fel i konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="6041d-118">If you fail to specify the version of a resource module of a resource of which you have more than one version installed, the configuration generates an error.</span></span>

<span data-ttu-id="6041d-119">Följande konfiguration visar hur du anger versionen av resursen att anropa:</span><span class="sxs-lookup"><span data-stu-id="6041d-119">The following configuration shows how to specify the version of the resource to call:</span></span>

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName xFailOverCluster -ModuleVersion 1.1

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}
```

><span data-ttu-id="6041d-120">Anm ModuleVersion-parametern för Import-DscResource är inte tillgänglig i PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="6041d-120">Note: The ModuleVersion parameter of Import-DscResource is not available in PowerShell 4.0.</span></span> <span data-ttu-id="6041d-121">Du kan ange en Modulversion genom att skicka ett objekt för specifikation av modulen till ModuleName-parametern för Import-DscResource i PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="6041d-121">In PowerShell 4.0, you can specify a module version by passing a module specification object to the ModuleName parameter of Import-DscResource.</span></span> <span data-ttu-id="6041d-122">Ett objekt för specifikation av modulen är en hashtabell som innehåller ModuleName och RequiredVersion nycklar.</span><span class="sxs-lookup"><span data-stu-id="6041d-122">A module specification object is a hash table that contains ModuleName and RequiredVersion  keys.</span></span> <span data-ttu-id="6041d-123">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="6041d-123">For example:</span></span>

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName (@{ModuleName='xFailOverCluster'; RequiredVersion='1.1'} )

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}
```

<span data-ttu-id="6041d-124">Detta fungerar även i PowerShell 5.0, men vi rekommenderar att du använder den **ModuleVersion** parametern.</span><span class="sxs-lookup"><span data-stu-id="6041d-124">This will also work in PowerShell 5.0, but it is recommended that you use the **ModuleVersion** parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="6041d-125">Se även</span><span class="sxs-lookup"><span data-stu-id="6041d-125">See also</span></span>

- [<span data-ttu-id="6041d-126">DSC-konfigurationer</span><span class="sxs-lookup"><span data-stu-id="6041d-126">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="6041d-127">DSC-resurser</span><span class="sxs-lookup"><span data-stu-id="6041d-127">DSC Resources</span></span>](../resources/resources.md)
