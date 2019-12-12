---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Importera en specifik version av en installerad resurs
ms.openlocfilehash: 5ed81e11aa67eb6590d958647f48a33b1b5f1c0e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71941973"
---
# <a name="import-a-specific-version-of-an-installed-resource"></a><span data-ttu-id="1cad6-103">Importera en specifik version av en installerad resurs</span><span class="sxs-lookup"><span data-stu-id="1cad6-103">Import a specific version of an installed resource</span></span>

> <span data-ttu-id="1cad6-104">Gäller för: Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="1cad6-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="1cad6-105">I PowerShell 5,0 kan separata versioner av DSC-resurser installeras på en dator sida vid sida.</span><span class="sxs-lookup"><span data-stu-id="1cad6-105">In PowerShell 5.0, separate versions of DSC resources can be installed on a computer side by side.</span></span> <span data-ttu-id="1cad6-106">En resurs-modul kan lagra separata versioner av en resurs i versions namn mappar.</span><span class="sxs-lookup"><span data-stu-id="1cad6-106">A resource module can store separate versions of a resource in version named folders.</span></span>

## <a name="installing-separate-resource-versions-side-by-side"></a><span data-ttu-id="1cad6-107">Installera separata resurs versioner sida vid sida</span><span class="sxs-lookup"><span data-stu-id="1cad6-107">Installing separate resource versions side by side</span></span>

<span data-ttu-id="1cad6-108">Du kan använda parametrarna **MinimumVersion**, **MaximumVersion**och **RequiredVersion** för cmdleten [install-module](/powershell/module/PowershellGet/Install-Module) för att ange vilken version av en modul som ska installeras.</span><span class="sxs-lookup"><span data-stu-id="1cad6-108">You can use the **MinimumVersion**, **MaximumVersion**, and **RequiredVersion** parameters of the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to specify which version of a module to install.</span></span> <span data-ttu-id="1cad6-109">Att anropa **install-module** utan att ange en version installerar den senaste versionen.</span><span class="sxs-lookup"><span data-stu-id="1cad6-109">Calling **Install-Module** without specifying a version installs the most recent version.</span></span>

<span data-ttu-id="1cad6-110">Det finns till exempel flera versioner av **xFailOverCluster** -modulen, som var och en innehåller en **xCluster** -resurs.</span><span class="sxs-lookup"><span data-stu-id="1cad6-110">For example, there are multiple versions of the **xFailOverCluster** module, each of which contains an **xCluster** resource.</span></span> <span data-ttu-id="1cad6-111">Anrop av **install-module** utan att ange versions numret installerar den senaste versionen av modulen.</span><span class="sxs-lookup"><span data-stu-id="1cad6-111">Calling **Install-Module** without specifying the version number installs the most recent version of the module.</span></span>

```powershell
PS> Install-Module xFailOverCluster
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, ...
```

<span data-ttu-id="1cad6-112">Om du vill installera en angiven version av en modul anger du en **RequiredVersion** för 1.1.0.0.</span><span class="sxs-lookup"><span data-stu-id="1cad6-112">To install a specific version of a module, specify a **RequiredVersion** of 1.1.0.0.</span></span> <span data-ttu-id="1cad6-113">Detta installerar den angivna versionen sida vid sida med den installerade versionen.</span><span class="sxs-lookup"><span data-stu-id="1cad6-113">This installs the specified version side by side with the installed version.</span></span>

```powershell
PS> Install-Module xFailOverCluster -RequiredVersion 1.1
```

<span data-ttu-id="1cad6-114">Nu ser du båda versionerna av modulen som visas när du använder `Get-DSCResource`.</span><span class="sxs-lookup"><span data-stu-id="1cad6-114">Now, you see both version of the module listed when you use `Get-DSCResource`.</span></span>

```powershell
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## <a name="specifying-a-resource-version-in-a-configuration"></a><span data-ttu-id="1cad6-115">Ange en resurs version i en konfiguration</span><span class="sxs-lookup"><span data-stu-id="1cad6-115">Specifying a resource version in a configuration</span></span>

<span data-ttu-id="1cad6-116">Om du har separata resurs versioner installerade på en dator måste du ange den här resursens version när du använder den i en konfiguration.</span><span class="sxs-lookup"><span data-stu-id="1cad6-116">If you have separate resource versions installed on a computer, you must specify the version of that resource when you use it in a configuration.</span></span> <span data-ttu-id="1cad6-117">Du gör detta genom att ange parametern **ModuleVersion** för nyckelordet **import-dscresource Keyword Supports** .</span><span class="sxs-lookup"><span data-stu-id="1cad6-117">You do this by specifying the **ModuleVersion** parameter of the **Import-DscResource** keyword.</span></span> <span data-ttu-id="1cad6-118">Om du inte anger versionen av en resurspool för en resurs där du har mer än en version installerad, genererar konfigurationen ett fel.</span><span class="sxs-lookup"><span data-stu-id="1cad6-118">If you fail to specify the version of a resource module of a resource of which you have more than one version installed, the configuration generates an error.</span></span>

<span data-ttu-id="1cad6-119">Följande konfiguration visar hur du anger vilken version av resursen som ska anropas:</span><span class="sxs-lookup"><span data-stu-id="1cad6-119">The following configuration shows how to specify the version of the resource to call:</span></span>

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

><span data-ttu-id="1cad6-120">Obs: ModuleVersion-parametern för import-Dscresource Keyword Supports är inte tillgänglig i PowerShell 4,0.</span><span class="sxs-lookup"><span data-stu-id="1cad6-120">Note: The ModuleVersion parameter of Import-DscResource is not available in PowerShell 4.0.</span></span> <span data-ttu-id="1cad6-121">I PowerShell 4,0 kan du ange en modul version genom att skicka ett modul Specifikations objekt till Modulnamn-parametern för import-Dscresource Keyword Supports.</span><span class="sxs-lookup"><span data-stu-id="1cad6-121">In PowerShell 4.0, you can specify a module version by passing a module specification object to the ModuleName parameter of Import-DscResource.</span></span> <span data-ttu-id="1cad6-122">Ett modul Specifikations objekt är en hash-tabell som innehåller Modulnamn-och RequiredVersion-nycklar.</span><span class="sxs-lookup"><span data-stu-id="1cad6-122">A module specification object is a hash table that contains ModuleName and RequiredVersion  keys.</span></span> <span data-ttu-id="1cad6-123">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="1cad6-123">For example:</span></span>

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

<span data-ttu-id="1cad6-124">Detta fungerar även i PowerShell 5,0, men vi rekommenderar att du använder parametern **ModuleVersion** .</span><span class="sxs-lookup"><span data-stu-id="1cad6-124">This will also work in PowerShell 5.0, but it is recommended that you use the **ModuleVersion** parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="1cad6-125">Se även</span><span class="sxs-lookup"><span data-stu-id="1cad6-125">See also</span></span>

- [<span data-ttu-id="1cad6-126">DSC-konfigurationer</span><span class="sxs-lookup"><span data-stu-id="1cad6-126">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="1cad6-127">DSC-resurser</span><span class="sxs-lookup"><span data-stu-id="1cad6-127">DSC Resources</span></span>](../resources/resources.md)
