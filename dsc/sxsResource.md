---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: "Använder resurser med flera versioner"
ms.openlocfilehash: c3397775a6767d74c182e15d07371e830f98e9a9
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="using-resources-with-multiple-versions"></a><span data-ttu-id="aaee5-103">Använder resurser med flera versioner</span><span class="sxs-lookup"><span data-stu-id="aaee5-103">Using resources with multiple versions</span></span>

> <span data-ttu-id="aaee5-104">Gäller för: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="aaee5-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="aaee5-105">I PowerShell 5.0 DSC-resurser kan ha flera versioner och versioner kan installeras på en dator sida-vid-sida.</span><span class="sxs-lookup"><span data-stu-id="aaee5-105">In PowerShell 5.0, DSC resources can have multiple versions, and versions can be installed on a computer side-by-side.</span></span> <span data-ttu-id="aaee5-106">Det har implementerats genom att låta flera versioner av en Resursmodul som ingår i samma modul mapp.</span><span class="sxs-lookup"><span data-stu-id="aaee5-106">This is implemented by having multiple versions of a resource module that are contained in the same module folder.</span></span>

## <a name="installing-multiple-resource-versions-side-by-side"></a><span data-ttu-id="aaee5-107">Installera flera resurs versioner sida-vid-sida</span><span class="sxs-lookup"><span data-stu-id="aaee5-107">Installing multiple resource versions side-by-side</span></span>

<span data-ttu-id="aaee5-108">Du kan använda den **MinimumVersion**, **MaximumVersion**, och **RequiredVersion** parametrarna för den [installera modulen](https://technet.microsoft.com/en-us/library/dn807162.aspx) för att ange vilken version av en modul som ska installeras.</span><span class="sxs-lookup"><span data-stu-id="aaee5-108">You can use the **MinimumVersion**, **MaximumVersion**, and **RequiredVersion** parameters of the [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) cmdlet to specify which version of a module to install.</span></span> <span data-ttu-id="aaee5-109">Anropar **installera modulen** utan att ange en version som installerar den senaste versionen.</span><span class="sxs-lookup"><span data-stu-id="aaee5-109">Calling **Install-Module** without specifying a version installs the most recent version.</span></span>

<span data-ttu-id="aaee5-110">Det finns till exempel flera versioner av den **xFailOverCluster** modul, som innehåller en **xCluster** resurs.</span><span class="sxs-lookup"><span data-stu-id="aaee5-110">For example, there are multiple versions of the **xFailOverCluster** module, each of which contains an **xCluster** resouce.</span></span> <span data-ttu-id="aaee5-111">Resultatet av anropar **installera modulen** utan att ange versionen numret är följande:</span><span class="sxs-lookup"><span data-stu-id="aaee5-111">The result of calling **Install-Module** without specifying the version number is as follows:</span></span>

```powershell
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Install-Module xFailOverCluster
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Get-DscResource xCluster

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, ...
```

<span data-ttu-id="aaee5-112">Nu om du anropar **installera modulen** igen, men anger en **RequiredVersion** av 1.1.0.0, den resulterar i följande:</span><span class="sxs-lookup"><span data-stu-id="aaee5-112">Now, if you call **Install-Module** again, but specify a **RequiredVersion** of 1.1.0.0, it results in the following:</span></span>

```powershell
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Install-Module xFailOverCluster -RequiredVersion 1.1
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Get-DscResource xCluster

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## <a name="specifying-a-resource-version-in-a-configuration"></a><span data-ttu-id="aaee5-113">Ange en resurs-version i en konfiguration</span><span class="sxs-lookup"><span data-stu-id="aaee5-113">Specifying a resource version in a configuration</span></span>

<span data-ttu-id="aaee5-114">Om du har flera resurser som är installerad på en dator, måste du ange versionen av den här resursen när du använder den i en konfiguration.</span><span class="sxs-lookup"><span data-stu-id="aaee5-114">If you have multiple resources installed on a computer, you must specify the version of that resource when you use it in a configuration.</span></span> <span data-ttu-id="aaee5-115">Det gör du genom att ange den **ModuleVersion** parameter för den **importera DscResource** nyckelord.</span><span class="sxs-lookup"><span data-stu-id="aaee5-115">You do this by specifying the **ModuleVersion** parameter of the **Import-DscResource** keyword.</span></span> <span data-ttu-id="aaee5-116">Om du inte ange version för en Resursmodul för en resurs som du har mer än en version som är installerad, genererar ett fel i konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="aaee5-116">If you fail to specify the version of a resource module of a resource of which you have more than one version installed, the configuration generates an error.</span></span>

<span data-ttu-id="aaee5-117">Följande konfiguration visas hur du anger versionen av resursen ska anropa:</span><span class="sxs-lookup"><span data-stu-id="aaee5-117">The following configuration shows how to specify the version of the resource to call:</span></span>

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

><span data-ttu-id="aaee5-118">Obs: Parametern ModuleVersion för Import-DscResource är inte tillgänglig i PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="aaee5-118">Note: The ModuleVersion parameter of Import-DscResource is not available in PowerShell 4.0.</span></span> <span data-ttu-id="aaee5-119">Du kan ange en Modulversion genom att skicka en specifikation Modulobjekt till ModuleName-parametern för Import-DscResource i PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="aaee5-119">In PowerShell 4.0, you can specify a module version by passing a module specification object to the ModuleName parameter of Import-DscResource.</span></span> <span data-ttu-id="aaee5-120">En modul specifikation objektet är en hash-tabell som innehåller Modulnamn och RequiredVersion nycklar.</span><span class="sxs-lookup"><span data-stu-id="aaee5-120">A module specification object is a hash table that contains ModuleName and RequiredVersion  keys.</span></span> <span data-ttu-id="aaee5-121">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="aaee5-121">For example:</span></span>

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

<span data-ttu-id="aaee5-122">Detta fungerar också i PowerShell 5.0, men det rekommenderas att du använder den **ModuleVersion** parameter.</span><span class="sxs-lookup"><span data-stu-id="aaee5-122">This will also work in PowerShell 5.0, but it is recommended that you use the **ModuleVersion** parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="aaee5-123">Se även</span><span class="sxs-lookup"><span data-stu-id="aaee5-123">See also</span></span>
* [<span data-ttu-id="aaee5-124">DSC-konfigurationer</span><span class="sxs-lookup"><span data-stu-id="aaee5-124">DSC Configurations</span></span>](configurations.md)
* [<span data-ttu-id="aaee5-125">DSC-resurser</span><span class="sxs-lookup"><span data-stu-id="aaee5-125">DSC Resources</span></span>](resources.md)

