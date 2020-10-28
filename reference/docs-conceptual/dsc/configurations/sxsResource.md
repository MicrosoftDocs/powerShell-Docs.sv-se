---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Importera en specifik version av en installerad resurs
description: Den här artikeln visar hur du installerar och importerar vissa versioner av resurspooler till dina konfigurationer.
ms.openlocfilehash: bb7b3273a5a3fed94fecd90dd3ea1e623fbc332b
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92645050"
---
# <a name="import-a-specific-version-of-an-installed-resource"></a><span data-ttu-id="e378e-104">Importera en specifik version av en installerad resurs</span><span class="sxs-lookup"><span data-stu-id="e378e-104">Import a specific version of an installed resource</span></span>

> <span data-ttu-id="e378e-105">Gäller för: Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="e378e-105">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="e378e-106">I PowerShell 5,0 kan separata versioner av DSC-resurser installeras på en dator sida vid sida.</span><span class="sxs-lookup"><span data-stu-id="e378e-106">In PowerShell 5.0, separate versions of DSC resources can be installed on a computer side by side.</span></span> <span data-ttu-id="e378e-107">En resurs-modul kan lagra separata versioner av en resurs i versions namn mappar.</span><span class="sxs-lookup"><span data-stu-id="e378e-107">A resource module can store separate versions of a resource in version named folders.</span></span>

## <a name="installing-separate-resource-versions-side-by-side"></a><span data-ttu-id="e378e-108">Installera separata resurs versioner sida vid sida</span><span class="sxs-lookup"><span data-stu-id="e378e-108">Installing separate resource versions side by side</span></span>

<span data-ttu-id="e378e-109">Du kan använda parametrarna **MinimumVersion** , **MaximumVersion** och **RequiredVersion** för cmdleten [install-module](/powershell/module/PowershellGet/Install-Module) för att ange vilken version av en modul som ska installeras.</span><span class="sxs-lookup"><span data-stu-id="e378e-109">You can use the **MinimumVersion** , **MaximumVersion** , and **RequiredVersion** parameters of the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to specify which version of a module to install.</span></span> <span data-ttu-id="e378e-110">Att anropa **install-module** utan att ange en version installerar den senaste versionen.</span><span class="sxs-lookup"><span data-stu-id="e378e-110">Calling **Install-Module** without specifying a version installs the most recent version.</span></span>

<span data-ttu-id="e378e-111">Det finns till exempel flera versioner av **xFailOverCluster** -modulen, som var och en innehåller en **xCluster** -resurs.</span><span class="sxs-lookup"><span data-stu-id="e378e-111">For example, there are multiple versions of the **xFailOverCluster** module, each of which contains an **xCluster** resource.</span></span> <span data-ttu-id="e378e-112">Anrop av **install-module** utan att ange versions numret installerar den senaste versionen av modulen.</span><span class="sxs-lookup"><span data-stu-id="e378e-112">Calling **Install-Module** without specifying the version number installs the most recent version of the module.</span></span>

```powershell
PS> Install-Module xFailOverCluster
PS> Get-DscResource xCluster
```

```Output
ImplementedAs   Name          ModuleName           Version    Properties
-------------   ----          ----------           -------    ----------
PowerShell      xCluster      xFailOverCluster     1.2.0.0    {DomainAdministratorCredential, ...
```

<span data-ttu-id="e378e-113">Om du vill installera en angiven version av en modul anger du en **RequiredVersion** för 1.1.0.0.</span><span class="sxs-lookup"><span data-stu-id="e378e-113">To install a specific version of a module, specify a **RequiredVersion** of 1.1.0.0.</span></span> <span data-ttu-id="e378e-114">Detta installerar den angivna versionen sida vid sida med den installerade versionen.</span><span class="sxs-lookup"><span data-stu-id="e378e-114">This installs the specified version side by side with the installed version.</span></span>

```powershell
PS> Install-Module xFailOverCluster -RequiredVersion 1.1
```

<span data-ttu-id="e378e-115">Nu ser du båda versionerna av modulen som visas när du använder `Get-DSCResource` .</span><span class="sxs-lookup"><span data-stu-id="e378e-115">Now, you see both version of the module listed when you use `Get-DSCResource`.</span></span>

```powershell
PS> Get-DscResource xCluster
```

```Output
ImplementedAs   Name          ModuleName            Version    Properties
-------------   ----          ----------            -------    ----------
PowerShell      xCluster      xFailOverCluster      1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster      xFailOverCluster      1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## <a name="specifying-a-resource-version-in-a-configuration"></a><span data-ttu-id="e378e-116">Ange en resurs version i en konfiguration</span><span class="sxs-lookup"><span data-stu-id="e378e-116">Specifying a resource version in a configuration</span></span>

<span data-ttu-id="e378e-117">Om du har separata resurs versioner installerade på en dator måste du ange den här resursens version när du använder den i en konfiguration.</span><span class="sxs-lookup"><span data-stu-id="e378e-117">If you have separate resource versions installed on a computer, you must specify the version of that resource when you use it in a configuration.</span></span> <span data-ttu-id="e378e-118">Du gör detta genom att ange parametern **ModuleVersion** för nyckelordet **import-dscresource Keyword Supports** .</span><span class="sxs-lookup"><span data-stu-id="e378e-118">You do this by specifying the **ModuleVersion** parameter of the **Import-DscResource** keyword.</span></span> <span data-ttu-id="e378e-119">Om du inte anger versionen av en resurspool för en resurs där du har mer än en version installerad, genererar konfigurationen ett fel.</span><span class="sxs-lookup"><span data-stu-id="e378e-119">If you fail to specify the version of a resource module of a resource of which you have more than one version installed, the configuration generates an error.</span></span>

<span data-ttu-id="e378e-120">Följande konfiguration visar hur du anger vilken version av resursen som ska anropas:</span><span class="sxs-lookup"><span data-stu-id="e378e-120">The following configuration shows how to specify the version of the resource to call:</span></span>

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

<span data-ttu-id="e378e-121">ModuleVersion-parametern för Import-DscResource är inte tillgänglig i PowerShell 4,0.</span><span class="sxs-lookup"><span data-stu-id="e378e-121">The ModuleVersion parameter of Import-DscResource is not available in PowerShell 4.0.</span></span> <span data-ttu-id="e378e-122">I PowerShell 4,0 kan du ange en modul version genom att skicka ett modul Specifikations objekt till Modulnamn-parametern för import-Dscresource Keyword Supports.</span><span class="sxs-lookup"><span data-stu-id="e378e-122">In PowerShell 4.0, you can specify a module version by passing a module specification object to the ModuleName parameter of Import-DscResource.</span></span> <span data-ttu-id="e378e-123">Ett modul Specifikations objekt är en hash-tabell som innehåller Modulnamn-och RequiredVersion-nycklar.</span><span class="sxs-lookup"><span data-stu-id="e378e-123">A module specification object is a hash table that contains ModuleName and RequiredVersion keys.</span></span> <span data-ttu-id="e378e-124">Exempel:</span><span class="sxs-lookup"><span data-stu-id="e378e-124">For example:</span></span>

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

<span data-ttu-id="e378e-125">Detta fungerar även i PowerShell 5,0, men vi rekommenderar att du använder parametern **ModuleVersion** .</span><span class="sxs-lookup"><span data-stu-id="e378e-125">This will also work in PowerShell 5.0, but it is recommended that you use the **ModuleVersion** parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="e378e-126">Se även</span><span class="sxs-lookup"><span data-stu-id="e378e-126">See also</span></span>

- [<span data-ttu-id="e378e-127">DSC-konfigurationer</span><span class="sxs-lookup"><span data-stu-id="e378e-127">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="e378e-128">DSC-resurser</span><span class="sxs-lookup"><span data-stu-id="e378e-128">DSC Resources</span></span>](../resources/resources.md)
