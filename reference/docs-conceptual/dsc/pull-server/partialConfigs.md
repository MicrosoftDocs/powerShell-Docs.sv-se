---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: PowerShell Desired State Configuration, delvis konfigurationer
ms.openlocfilehash: f25bdec54e0a028e94b8c7d7b623e53ff3e3c666
ms.sourcegitcommit: 36e4c79afda2ce11febd93951e143687245f0b50
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/02/2019
ms.locfileid: "73444520"
---
# <a name="powershell-desired-state-configuration-partial-configurations"></a><span data-ttu-id="99226-103">PowerShell Desired State Configuration, delvis konfigurationer</span><span class="sxs-lookup"><span data-stu-id="99226-103">PowerShell Desired State Configuration partial configurations</span></span>

<span data-ttu-id="99226-104">_Gäller för: Windows PowerShell 5,0 och senare._</span><span class="sxs-lookup"><span data-stu-id="99226-104">_Applies To: Windows PowerShell 5.0 and later._</span></span>

<span data-ttu-id="99226-105">I PowerShell 5,0 tillåter önskad tillstånds konfiguration (DSC) konfigurationer att levereras i fragment och från flera källor.</span><span class="sxs-lookup"><span data-stu-id="99226-105">In PowerShell 5.0, Desired State Configuration (DSC) allows configurations to be delivered in fragments and from multiple sources.</span></span> <span data-ttu-id="99226-106">Den lokala Configuration Manager (LCM) på målnoden placerar fragmenten tillsammans innan de tillämpas som en enda konfiguration.</span><span class="sxs-lookup"><span data-stu-id="99226-106">The Local Configuration Manager (LCM) on the target node puts the fragments together before applying them as a single configuration.</span></span> <span data-ttu-id="99226-107">Den här funktionen gör det möjligt att dela kontroll över konfigurationen mellan team eller individer.</span><span class="sxs-lookup"><span data-stu-id="99226-107">This capability allows sharing control of configuration between teams or individuals.</span></span> <span data-ttu-id="99226-108">Om två eller flera team utvecklare samarbetar med en tjänst kan de exempelvis var och en vilja skapa konfigurationer för att hantera sin del av tjänsten.</span><span class="sxs-lookup"><span data-stu-id="99226-108">For example, if two or more teams of developers are collaborating on a service, they might each want to create configurations to manage their part of the service.</span></span> <span data-ttu-id="99226-109">Var och en av dessa konfigurationer kan hämtas från olika hämtnings servrar och de kan läggas till i olika utvecklings steg.</span><span class="sxs-lookup"><span data-stu-id="99226-109">Each of these configurations could be pulled from different pull servers, and they could be added at different stages of development.</span></span> <span data-ttu-id="99226-110">Partiella konfigurationer gör det också möjligt för olika individer eller team att styra olika aspekter av konfigurering av noder utan att behöva koordinera redigeringen av ett enda konfigurations dokument.</span><span class="sxs-lookup"><span data-stu-id="99226-110">Partial configurations also allow different individuals or teams to control different aspects of configuring nodes without having to coordinate the editing of a single configuration document.</span></span> <span data-ttu-id="99226-111">Ett team kan till exempel vara ansvarigt för att distribuera en virtuell dator och ett operativ system, medan ett annat team kan distribuera andra program och tjänster på den virtuella datorn.</span><span class="sxs-lookup"><span data-stu-id="99226-111">For example, one team might be responsible for deploying a VM and operating system, while another team might deploy other applications and services on that VM.</span></span> <span data-ttu-id="99226-112">Med del konfigurationer kan varje team skapa en egen konfiguration, utan att något av dem är onödigt komplicerat.</span><span class="sxs-lookup"><span data-stu-id="99226-112">With partial configurations, each team can create its own configuration, without either of them being unnecessarily complicated.</span></span>

<span data-ttu-id="99226-113">Du kan använda partiella konfigurationer i push-läge, pull-läge eller en kombination av de två.</span><span class="sxs-lookup"><span data-stu-id="99226-113">You can use partial configurations in push mode, pull mode, or a combination of the two.</span></span>

## <a name="partial-configurations-in-push-mode"></a><span data-ttu-id="99226-114">Partiella konfigurationer i push-läge</span><span class="sxs-lookup"><span data-stu-id="99226-114">Partial configurations in push mode</span></span>

<span data-ttu-id="99226-115">Om du vill använda partiella konfigurationer i push-läge konfigurerar du LCM på målnoden för att ta emot del konfigurationerna.</span><span class="sxs-lookup"><span data-stu-id="99226-115">To use partial configurations in push mode, you configure the LCM on the target node to receive the partial configurations.</span></span> <span data-ttu-id="99226-116">Varje del konfiguration måste flyttas till målet med hjälp av `Publish-DSCConfiguration`-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="99226-116">Each partial configuration must be pushed to the target by using the `Publish-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="99226-117">Målnoden kombinerar sedan den partiella konfigurationen till en enda konfiguration och du kan tillämpa konfigurationen genom att anropa cmdleten [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) .</span><span class="sxs-lookup"><span data-stu-id="99226-117">The target node then combines the partial configuration into a single configuration, and you can apply the configuration by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

### <a name="configuring-the-lcm-for-push-mode-partial-configurations"></a><span data-ttu-id="99226-118">Konfigurera LCM för ofullständiga konfigurationer i push-läge</span><span class="sxs-lookup"><span data-stu-id="99226-118">Configuring the LCM for push-mode partial configurations</span></span>

<span data-ttu-id="99226-119">Om du vill konfigurera LCM för partiella konfigurationer i push-läge, skapar du en **DSCLocalConfigurationManager** -konfiguration med ett **PartialConfiguration** -block för varje del konfiguration.</span><span class="sxs-lookup"><span data-stu-id="99226-119">To configure the LCM for partial configurations in push mode, you create a **DSCLocalConfigurationManager** configuration with one **PartialConfiguration** block for each partial configuration.</span></span> <span data-ttu-id="99226-120">Mer information om hur du konfigurerar LCM finns i [Windows konfigurera den lokala Configuration Manager](/powershell/dsc/metaConfig).</span><span class="sxs-lookup"><span data-stu-id="99226-120">For more information about configuring the LCM, see [Windows Configuring the Local Configuration Manager](/powershell/dsc/metaConfig).</span></span> <span data-ttu-id="99226-121">I följande exempel visas en LCM-konfiguration som förväntar sig två delar av konfigurationer – en som distribuerar operativ systemet och en som distribuerar och konfigurerar SharePoint.</span><span class="sxs-lookup"><span data-stu-id="99226-121">The following example shows an LCM configuration that expects two partial configurations—one that deploys the OS, and one that deploys and configures SharePoint.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemo
{
    Node localhost
    {

        PartialConfiguration ServiceAccountConfig
        {
            Description = 'Configuration to add the SharePoint service account to the Administrators group.'
            RefreshMode = 'Push'
        }
           PartialConfiguration SharePointConfig
        {
            Description = 'Configuration for the SharePoint server'
            RefreshMode = 'Push'
        }
    }
}

PartialConfigDemo
```

<span data-ttu-id="99226-122">**RefreshMode** för varje delvis konfiguration anges till "push".</span><span class="sxs-lookup"><span data-stu-id="99226-122">The **RefreshMode** for each partial configuration is set to "Push".</span></span> <span data-ttu-id="99226-123">Namnen på **PartialConfiguration** -blocken (i det här fallet "ServiceAccountConfig" och "SharePointConfig") måste matcha exakt namnen på de konfigurationer som flyttas till målnoden.</span><span class="sxs-lookup"><span data-stu-id="99226-123">The names of the **PartialConfiguration** blocks (in this case, "ServiceAccountConfig" and "SharePointConfig") must match exactly the names of the configurations that are pushed to the target node.</span></span>

> [!Note]
> <span data-ttu-id="99226-124">Namnet på varje **PartialConfiguration** -block måste matcha det faktiska namnet på konfigurationen som det anges i konfigurations skriptet, inte namnet på MOF-filen, som antingen ska vara namnet på målnoden eller `localhost`.</span><span class="sxs-lookup"><span data-stu-id="99226-124">The named of each **PartialConfiguration** block must match the actual name of the configuration as it is specified in the configuration script, not the name of the MOF file, which should be either the name of the target node or `localhost`.</span></span>

### <a name="publishing-and-starting-push-mode-partial-configurations"></a><span data-ttu-id="99226-125">Publicera och starta partiella konfigurationer i push-läge</span><span class="sxs-lookup"><span data-stu-id="99226-125">Publishing and starting push-mode partial configurations</span></span>

<span data-ttu-id="99226-126">Sedan anropar du [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) för varje konfiguration och skickar mapparna som innehåller konfigurations dokumenten som **Sök vägs** parametrar.</span><span class="sxs-lookup"><span data-stu-id="99226-126">You then call [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) for each configuration, passing the folders that contain the configuration documents as the **Path** parameters.</span></span> <span data-ttu-id="99226-127">`Publish-DSCConfiguration`placerar MOF-filerna för konfiguration på målnoden.</span><span class="sxs-lookup"><span data-stu-id="99226-127">`Publish-DSCConfiguration`places the configuration MOF files to the target nodes.</span></span> <span data-ttu-id="99226-128">När du har publicerat båda konfigurationerna kan du anropa `Start-DSCConfiguration –UseExisting` på målnoden.</span><span class="sxs-lookup"><span data-stu-id="99226-128">After publishing both configurations, you can call `Start-DSCConfiguration –UseExisting` on the target node.</span></span>

<span data-ttu-id="99226-129">Om du till exempel har kompilerat följande konfiguration MOF-dokument på noden redigering:</span><span class="sxs-lookup"><span data-stu-id="99226-129">For example, if you have compiled the following configuration MOF documents on the authoring node:</span></span>

```powershell
Get-ChildItem -Recurse
```

```output
    Directory: C:\PartialConfigTest

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        8/11/2016   1:55 PM                ServiceAccountConfig
d-----       11/17/2016   4:14 PM                SharePointConfig

    Directory: C:\PartialConfigTest\ServiceAccountConfig

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        8/11/2016   2:02 PM           2034 TestVM.mof

    Directory: C:\PartialConfigTest\SharePointConfig

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       11/17/2016   4:14 PM           1930 TestVM.mof
```

<span data-ttu-id="99226-130">Du publicerar och kör konfigurationerna på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="99226-130">You would publish and run the configurations as follows:</span></span>

```powershell
Publish-DscConfiguration .\ServiceAccountConfig -ComputerName 'TestVM'
Publish-DscConfiguration .\SharePointConfig -ComputerName 'TestVM'
Start-DscConfiguration -UseExisting -ComputerName 'TestVM'
```

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
17     Job17           Configuratio... Running       True            TestVM            Start-DscConfiguration...
```

> [!Note]
> <span data-ttu-id="99226-131">Användaren som kör cmdleten [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) måste ha administratörs behörighet på målnoden.</span><span class="sxs-lookup"><span data-stu-id="99226-131">The user running the [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet must have administrator privileges on the target node.</span></span>

## <a name="partial-configurations-in-pull-mode"></a><span data-ttu-id="99226-132">Partiella konfigurationer i pull-läge</span><span class="sxs-lookup"><span data-stu-id="99226-132">Partial configurations in pull mode</span></span>

<span data-ttu-id="99226-133">Partiella konfigurationer kan hämtas från en eller flera hämtnings servrar (mer information om hämtnings servrar finns i [Windows PowerShell Desired State Configuration pull-servrar](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="99226-133">Partial configurations can be pulled from one or more pull servers (for more information about pull servers, see [Windows PowerShell Desired State Configuration Pull Servers](pullServer.md).</span></span> <span data-ttu-id="99226-134">Om du vill göra detta måste du konfigurera LCM på målnoden för att hämta de partiella konfigurationerna och namnge och hitta de konfigurations dokument som är korrekt på pull-servrarna.</span><span class="sxs-lookup"><span data-stu-id="99226-134">To do this, you have to configure the LCM on the target node to pull the partial configurations, and name and locate the configuration documents properly on the pull servers.</span></span>

### <a name="configuring-the-lcm-for-pull-node-configurations"></a><span data-ttu-id="99226-135">Konfigurera LCM för pull-nodkonfigurationer</span><span class="sxs-lookup"><span data-stu-id="99226-135">Configuring the LCM for pull node configurations</span></span>

<span data-ttu-id="99226-136">Om du vill konfigurera LCM för att hämta partiella konfigurationer från en pull-server definierar du hämtnings servern i antingen en **ConfigurationRepositoryWeb** (för en http-pull-server) eller **CONFIGURATIONREPOSITORYSHARE** (för SMB pull server)-block.</span><span class="sxs-lookup"><span data-stu-id="99226-136">To configure the LCM to pull partial configurations from a pull server, you define the pull server in either a **ConfigurationRepositoryWeb** (for an HTTP pull server) or **ConfigurationRepositoryShare** (for an SMB pull server) block.</span></span> <span data-ttu-id="99226-137">Sedan skapar du **PartialConfiguration** -block som refererar till pull-servern med hjälp av egenskapen **ConfigurationSource** .</span><span class="sxs-lookup"><span data-stu-id="99226-137">You then create **PartialConfiguration** blocks that refer to the pull server by using the **ConfigurationSource** property.</span></span> <span data-ttu-id="99226-138">Du måste också skapa ett **inställnings** block för att ange att LCM använder pull-läge och för att ange **ConfigurationNames** eller **ConfigurationID** som pull-servern och mål-noden använder för att identifiera konfigurationerna.</span><span class="sxs-lookup"><span data-stu-id="99226-138">You also need to create a **Settings** block to specify that the LCM uses pull mode, and to specify the **ConfigurationNames** or **ConfigurationID** that the pull server and target node use to identify the configurations.</span></span> <span data-ttu-id="99226-139">Följande meta-konfiguration definierar en HTTP pull-server med namnet CONTOSO-PullSrv och två ofullständiga konfigurationer som använder den hämtnings servern.</span><span class="sxs-lookup"><span data-stu-id="99226-139">The following meta-configuration defines an HTTP pull server named CONTOSO-PullSrv and two partial configurations that use that pull server.</span></span>

<span data-ttu-id="99226-140">Mer information om hur du konfigurerar LCM med hjälp av **ConfigurationNames**finns i [Konfigurera en pull-klient med hjälp av konfigurations namn](pullClientConfigNames.md).</span><span class="sxs-lookup"><span data-stu-id="99226-140">For more information about configuring the LCM using **ConfigurationNames**, see [Setting up a pull client using configuration names](pullClientConfigNames.md).</span></span> <span data-ttu-id="99226-141">Information om hur du konfigurerar LCM med hjälp av **ConfigurationID**finns i [Konfigurera en pull-klient med konfigurations-ID](pullClientConfigID.md).</span><span class="sxs-lookup"><span data-stu-id="99226-141">For information about configuring the LCM using **ConfigurationID**, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configuration-names"></a><span data-ttu-id="99226-142">Konfigurera LCM för pull-läge-konfigurationer med hjälp av konfigurations namn</span><span class="sxs-lookup"><span data-stu-id="99226-142">Configuring the LCM for pull mode configurations using configuration names</span></span>

```powershell
[DscLocalConfigurationManager()]
Configuration PartialConfigDemoConfigNames
{
        Settings
        {
            RefreshFrequencyMins            = 30;
            RefreshMode                     = "PULL";
            ConfigurationMode               ="ApplyAndAutocorrect";
            AllowModuleOverwrite            = $true;
            RebootNodeIfNeeded              = $true;
            ConfigurationModeFrequencyMins  = 60;
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey                 = 5b41f4e6-5e6d-45f5-8102-f2227468ef38
            ConfigurationNames              = @("ServiceAccountConfig", "SharePointConfig")
        }

        PartialConfiguration ServiceAccountConfig
        {
            Description                     = "ServiceAccountConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
        }

        PartialConfiguration SharePointConfig
        {
            Description                     = "SharePointConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
        }
}
```

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configurationid"></a><span data-ttu-id="99226-143">Konfigurera LCM för pull-läge-konfigurationer med ConfigurationID</span><span class="sxs-lookup"><span data-stu-id="99226-143">Configuring the LCM for pull mode configurations using ConfigurationID</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemoConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode                     = 'Pull'
            ConfigurationID                 = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins            = 30
            RebootNodeIfNeeded              = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

           PartialConfiguration ServiceAccountConfig
        {
            Description                     = 'Configuration for the Base OS'
            ConfigurationSource             = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            RefreshMode                     = 'Pull'
        }
           PartialConfiguration SharePointConfig
        {
            Description                     = 'Configuration for the Sharepoint Server'
            ConfigurationSource             = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode                     = 'Pull'
        }
    }
}
PartialConfigDemo
```

<span data-ttu-id="99226-144">Du kan hämta delvis konfigurationer från fler än en pull-server – du behöver bara definiera varje pull-server och sedan referera till lämplig pull-server i varje **PartialConfiguration** -block.</span><span class="sxs-lookup"><span data-stu-id="99226-144">You can pull partial configurations from more than one pull server—you would just need to define each pull server, and then refer to the appropriate pull server in each **PartialConfiguration** block.</span></span>

<span data-ttu-id="99226-145">När du har skapat meta-konfigurationen måste du köra den för att skapa ett konfigurations dokument (en MOF-fil) och sedan anropa [set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) för att konfigurera LCM.</span><span class="sxs-lookup"><span data-stu-id="99226-145">After creating the meta-configuration, you must run it to create a configuration document (a MOF file), and then call [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) to configure the LCM.</span></span>

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationnames"></a><span data-ttu-id="99226-146">Namnge och placera konfigurations dokumenten på pull-servern (ConfigurationNames)</span><span class="sxs-lookup"><span data-stu-id="99226-146">Naming and placing the configuration documents on the pull server (ConfigurationNames)</span></span>

<span data-ttu-id="99226-147">De partiella konfigurations dokumenten måste placeras i den mapp som anges som **ConfigurationPath** i `web.config`-filen för pull-servern (vanligt vis `C:\Program
Files\WindowsPowerShell\DscService\Configuration`).</span><span class="sxs-lookup"><span data-stu-id="99226-147">The partial configuration documents must be placed in the folder specified as the **ConfigurationPath** in the `web.config` file for the pull server (typically `C:\Program
Files\WindowsPowerShell\DscService\Configuration`).</span></span>

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-51"></a><span data-ttu-id="99226-148">Namnge konfigurations dokument på hämtnings servern i PowerShell 5,1</span><span class="sxs-lookup"><span data-stu-id="99226-148">Naming configuration documents on the pull server in PowerShell 5.1</span></span>

<span data-ttu-id="99226-149">Om du bara hämtar en delvis konfiguration från en enskild hämtnings Server kan konfigurations dokumentet ha ett namn.</span><span class="sxs-lookup"><span data-stu-id="99226-149">If you are pulling only one partial configuration from an individual pull server, the configuration document can have any name.</span></span> <span data-ttu-id="99226-150">Om du hämtar fler än en partiell konfiguration från en pull-server, kan konfigurations dokumentet kallas antingen `<ConfigurationName>.mof`, där *ConfigurationName* är namnet på den partiella konfigurationen eller `<ConfigurationName>.<NodeName>.mof`där *ConfigurationName* är namnet på den partiella konfigurationen och *nodnamn* är namnet på målnoden.</span><span class="sxs-lookup"><span data-stu-id="99226-150">If you are pulling more than one partial configuration from a pull server, the configuration document can be named either `<ConfigurationName>.mof`, where *ConfigurationName* is the name of the partial configuration, or `<ConfigurationName>.<NodeName>.mof`, where *ConfigurationName* is the name of the partial configuration, and *NodeName* is the name of the target node.</span></span> <span data-ttu-id="99226-151">På så sätt kan du hämta konfigurationer från Azure Automation DSC-pull-server.</span><span class="sxs-lookup"><span data-stu-id="99226-151">This allows you to pull configurations from Azure Automation DSC pull server.</span></span>

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-50"></a><span data-ttu-id="99226-152">Namnge konfigurations dokument på hämtnings servern i PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="99226-152">Naming configuration documents on the pull server in PowerShell 5.0</span></span>

<span data-ttu-id="99226-153">Konfigurations dokumenten måste ha följande namn: `ConfigurationName.mof`, där *ConfigurationName* är namnet på den partiella konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="99226-153">The configuration documents must be named as follows: `ConfigurationName.mof`, where *ConfigurationName* is the name of the partial configuration.</span></span> <span data-ttu-id="99226-154">I vårt exempel ska konfigurations dokumenten namnges enligt följande:</span><span class="sxs-lookup"><span data-stu-id="99226-154">For our example, the configuration documents should be named as follows:</span></span>

```
ServiceAccountConfig.mof
ServiceAccountConfig.mof.checksum
SharePointConfig.mof
SharePointConfig.mof.checksum
```

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationid"></a><span data-ttu-id="99226-155">Namnge och placera konfigurations dokumenten på pull-servern (ConfigurationID)</span><span class="sxs-lookup"><span data-stu-id="99226-155">Naming and placing the configuration documents on the pull server (ConfigurationID)</span></span>

<span data-ttu-id="99226-156">De partiella konfigurations dokumenten måste placeras i den mapp som anges som **ConfigurationPath** i `web.config`-filen för pull-servern (vanligt vis `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span><span class="sxs-lookup"><span data-stu-id="99226-156">The partial configuration documents must be placed in the folder specified as the **ConfigurationPath** in the `web.config` file for the pull server (typically `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span></span> <span data-ttu-id="99226-157">Konfigurations dokumenten måste namnges enligt följande: `<ConfigurationName>.<ConfigurationID>.mof`, där _ConfigurationName_ är namnet på den partiella konfigurationen och _ConfigurationID_ är det konfigurations-ID som definierats i LCM på målnoden.</span><span class="sxs-lookup"><span data-stu-id="99226-157">The configuration documents must be named as follows: `<ConfigurationName>.<ConfigurationID>.mof`, where _ConfigurationName_ is the name of the partial configuration and _ConfigurationID_ is the configuration ID defined in the LCM on the target node.</span></span> <span data-ttu-id="99226-158">I vårt exempel ska konfigurations dokumenten namnges enligt följande:</span><span class="sxs-lookup"><span data-stu-id="99226-158">For our example, the configuration documents should be named as follows:</span></span>

```
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
```

### <a name="running-partial-configurations-from-a-pull-server"></a><span data-ttu-id="99226-159">Köra partiella konfigurationer från en hämtnings Server</span><span class="sxs-lookup"><span data-stu-id="99226-159">Running partial configurations from a pull server</span></span>

<span data-ttu-id="99226-160">När LCM på mål-noden har kon figurer ATS och konfigurations dokumenten har skapats och på rätt sätt har namngetts på hämtnings servern, hämtar målnoden de ofullständiga konfigurationerna, kombinerar dem och tillämpar den resulterande konfigurationen på vanligt sätt. intervall som anges av egenskapen **RefreshFrequencyMins** för LCM.</span><span class="sxs-lookup"><span data-stu-id="99226-160">After the LCM on the target node has been configured, and the configuration documents have been created and properly named on the pull server, the target node will pull the partial configurations, combine them, and apply the resulting configuration at regular intervals as specified by the **RefreshFrequencyMins** property of the LCM.</span></span> <span data-ttu-id="99226-161">Om du vill framtvinga en uppdatering kan du anropa cmdleten [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration) för att hämta konfigurationerna och sedan `Start-DSCConfiguration –UseExisting` tillämpa dem.</span><span class="sxs-lookup"><span data-stu-id="99226-161">If you want to force a refresh, you can call the [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration) cmdlet, to pull the configurations, and then `Start-DSCConfiguration –UseExisting` to apply them.</span></span>

## <a name="partial-configurations-in-mixed-push-and-pull-modes"></a><span data-ttu-id="99226-162">Partiella konfigurationer i blandade push-och pull-lägen</span><span class="sxs-lookup"><span data-stu-id="99226-162">Partial configurations in mixed push and pull modes</span></span>

<span data-ttu-id="99226-163">Du kan också blanda push-och pull-lägen för partiella konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="99226-163">You can also mix push and pull modes for partial configurations.</span></span> <span data-ttu-id="99226-164">Det innebär att du kan ha en delvis konfiguration som hämtas från en pull-server, medan en annan del av konfigurationen skickas.</span><span class="sxs-lookup"><span data-stu-id="99226-164">That is, you could have one partial configuration that is pulled from a pull server, while another partial configuration is pushed.</span></span> <span data-ttu-id="99226-165">Ange uppdaterings läget för varje partiell konfiguration enligt beskrivningen i föregående avsnitt.</span><span class="sxs-lookup"><span data-stu-id="99226-165">Specify the refresh mode for each partial configuration as described in the previous sections.</span></span> <span data-ttu-id="99226-166">Följande meta-konfiguration beskriver till exempel samma exempel, med `ServiceAccountConfig` partiell konfiguration i pull-läge och `SharePointConfig` partiell konfiguration i push-läge.</span><span class="sxs-lookup"><span data-stu-id="99226-166">For example, the following meta-configuration describes the same example, with the `ServiceAccountConfig` partial configuration in pull mode and the `SharePointConfig` partial configuration in push mode.</span></span>

### <a name="mixed-push-and-pull-modes-using-configurationnames"></a><span data-ttu-id="99226-167">Blandade push-och pull-lägen med ConfigurationNames</span><span class="sxs-lookup"><span data-stu-id="99226-167">Mixed push and pull modes using ConfigurationNames</span></span>

```powershell
[DscLocalConfigurationManager()]
Configuration PartialConfigDemoConfigNames
{
        Settings
        {
            RefreshFrequencyMins            = 30;
            RefreshMode                     = "PULL";
            ConfigurationMode               = "ApplyAndAutocorrect";
            AllowModuleOverwrite            = $true;
            RebootNodeIfNeeded              = $true;
            ConfigurationModeFrequencyMins  = 60;
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey                 = 5b41f4e6-5e6d-45f5-8102-f2227468ef38
            ConfigurationNames              = @("ServiceAccountConfig", "SharePointConfig")
        }

        PartialConfiguration ServiceAccountConfig
        {
            Description                     = "ServiceAccountConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
            RefreshMode                     = 'Pull'
        }

        PartialConfiguration SharePointConfig
        {
            Description                     = "SharePointConfig"
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode                     = 'Push'
        }

}
```

### <a name="mixed-push-and-pull-modes-using-configurationid"></a><span data-ttu-id="99226-168">Blandade push-och pull-lägen med ConfigurationID</span><span class="sxs-lookup"><span data-stu-id="99226-168">Mixed push and pull modes using ConfigurationID</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemo
{
    Node localhost
    {
        Settings
        {
            RefreshMode             = 'Pull'
            ConfigurationID         = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins    = 30
            RebootNodeIfNeeded      = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL               = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

           PartialConfiguration ServiceAccountConfig
        {
            Description             = 'Configuration for the Base OS'
            ConfigurationSource     = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            RefreshMode             = 'Pull'
        }
           PartialConfiguration SharePointConfig
        {
            Description             = 'Configuration for the Sharepoint Server'
            DependsOn               = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode             = 'Push'
        }
    }
}
PartialConfigDemo
```

<span data-ttu-id="99226-169">Observera att **RefreshMode** som anges i inställnings blocket är "pull", men **RefreshMode** för `SharePointConfig` partiella konfigurationen är "push".</span><span class="sxs-lookup"><span data-stu-id="99226-169">Note that the **RefreshMode** specified in the Settings block is "Pull", but the **RefreshMode** for the `SharePointConfig` partial configuration is "Push".</span></span>

<span data-ttu-id="99226-170">Namnge och leta upp MOF-filerna för konfigurationen enligt beskrivningen ovan för respektive uppdaterings läge.</span><span class="sxs-lookup"><span data-stu-id="99226-170">Name and locate the configuration MOF files as described above for their respective refresh modes.</span></span>
<span data-ttu-id="99226-171">Anropa `Publish-DSCConfiguration` för att publicera `SharePointConfig` partiella konfigurationen och antingen väntar på att `ServiceAccountConfig` konfigurationen ska hämtas från hämtnings servern eller framtvinga en uppdatering genom att anropa [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration).</span><span class="sxs-lookup"><span data-stu-id="99226-171">Call `Publish-DSCConfiguration` to publish the `SharePointConfig` partial configuration, and either wait for the `ServiceAccountConfig` configuration to be pulled from the pull server, or force a refresh by calling [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration).</span></span>

## <a name="example-serviceaccountconfig-partial-configuration"></a><span data-ttu-id="99226-172">Exempel ServiceAccountConfig delvis konfiguration</span><span class="sxs-lookup"><span data-stu-id="99226-172">Example ServiceAccountConfig Partial Configuration</span></span>

```powershell
Configuration ServiceAccountConfig
{
    Param (
        [Parameter(Mandatory,
                   HelpMessage="Domain credentials required to add domain\sharepoint_svc to the local Administrators group.")]
        [ValidateNotNullOrEmpty()]
        [pscredential]$Credential
    )

    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost
    {
        Group LocalAdmins
        {
            GroupName           = 'Administrators'
            MembersToInclude    = 'domain\sharepoint_svc',
                                  'admins@example.domain'
            Ensure              = 'Present'
            Credential          = $Credential
        }

        WindowsFeature Telnet
        {
            Name                = 'Telnet-Server'
            Ensure              = 'Absent'
        }
    }
}
ServiceAccountConfig
```

## <a name="example-sharepointconfig-partial-configuration"></a><span data-ttu-id="99226-173">Exempel SharePointConfig delvis konfiguration</span><span class="sxs-lookup"><span data-stu-id="99226-173">Example SharePointConfig Partial Configuration</span></span>

```powershell
Configuration SharePointConfig
{
    Param (
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [pscredential]$ProductKey
    )

    Import-DscResource -ModuleName xSharePoint

    Node localhost
    {
        xSPInstall SharePointDefault
        {
            Ensure      = 'Present'
            BinaryDir   = '\\FileServer\Installers\Sharepoint\'
            ProductKey  = $ProductKey
        }
    }
}
SharePointConfig
```

## <a name="see-also"></a><span data-ttu-id="99226-174">Se även</span><span class="sxs-lookup"><span data-stu-id="99226-174">See Also</span></span>

[<span data-ttu-id="99226-175">Hämtnings servrar för önskad tillstånds konfiguration i Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="99226-175">Windows PowerShell Desired State Configuration Pull Servers</span></span>](pullServer.md)

[<span data-ttu-id="99226-176">Windows konfigurerar den lokala Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="99226-176">Windows Configuring the Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
