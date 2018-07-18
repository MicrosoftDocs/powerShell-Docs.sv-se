---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: PowerShell Desired State Configuration partiella konfigurationer
ms.openlocfilehash: 6d344b666421aba5745945f6148570e4c8229c1a
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093940"
---
# <a name="powershell-desired-state-configuration-partial-configurations"></a><span data-ttu-id="3266f-103">PowerShell Desired State Configuration partiella konfigurationer</span><span class="sxs-lookup"><span data-stu-id="3266f-103">PowerShell Desired State Configuration partial configurations</span></span>

> <span data-ttu-id="3266f-104">Gäller för: Windows PowerShell 5.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="3266f-104">Applies To: Windows PowerShell 5.0 and later.</span></span>

<span data-ttu-id="3266f-105">I PowerShell 5.0 kan Desired State Configuration (DSC) konfigurationer som ska levereras i fragment och från flera källor.</span><span class="sxs-lookup"><span data-stu-id="3266f-105">In PowerShell 5.0, Desired State Configuration (DSC) allows configurations to be delivered in fragments and from multiple sources.</span></span> <span data-ttu-id="3266f-106">Den lokala Configuration Manager (LCM) på målnoden placerar fragmenten tillsammans innan du tillämpar dem som en enda konfiguration.</span><span class="sxs-lookup"><span data-stu-id="3266f-106">The Local Configuration Manager (LCM) on the target node puts the fragments together before applying them as a single configuration.</span></span> <span data-ttu-id="3266f-107">Den här funktionen tillåter delning kontrollen över konfiguration mellan team eller enskilda användare.</span><span class="sxs-lookup"><span data-stu-id="3266f-107">This capability allows sharing control of configuration between teams or individuals.</span></span>
<span data-ttu-id="3266f-108">Till exempel om två eller flera team med utvecklare samarbetar med en tjänst, vilja de var skapa konfigurationer för att hantera sina ingår i tjänsten.</span><span class="sxs-lookup"><span data-stu-id="3266f-108">For example, if two or more teams of developers are collaborating on a service, they might each want to create configurations to manage their part of the service.</span></span> <span data-ttu-id="3266f-109">Var och en av de här konfigurationerna kan hämtas från olika pull-servrar och de kan läggas till under de olika faserna i utvecklingen av.</span><span class="sxs-lookup"><span data-stu-id="3266f-109">Each of these configurations could be pulled from different pull servers, and they could be added at different stages of development.</span></span> <span data-ttu-id="3266f-110">Partiella konfigurationer kan också olika individer eller team att styra olika aspekter av konfigurerat noder utan att behöva samordna redigering av ett enda configuration-dokument.</span><span class="sxs-lookup"><span data-stu-id="3266f-110">Partial configurations also allow different individuals or teams to control different aspects of configuring nodes without having to coordinate the editing of a single configuration document.</span></span> <span data-ttu-id="3266f-111">Till exempel kanske ett team ansvarar för att distribuera en virtuell dator och operativsystem, medan ett annat team kan distribuera andra program och tjänster på den virtuella datorn.</span><span class="sxs-lookup"><span data-stu-id="3266f-111">For example, one team might be responsible for deploying a VM and operating system, while another team might deploy other applications and services on that VM.</span></span> <span data-ttu-id="3266f-112">Varje team kan skapa egna konfigurationer, utan någon av dem är onödigt komplicerat med partiella konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="3266f-112">With partial configurations, each team can create its own configuration, without either of them being unnecessarily complicated.</span></span>

<span data-ttu-id="3266f-113">Du kan använda partiella konfigurationer i push-läge, pull-läge eller en kombination av båda.</span><span class="sxs-lookup"><span data-stu-id="3266f-113">You can use partial configurations in push mode, pull mode, or a combination of the two.</span></span>

## <a name="partial-configurations-in-push-mode"></a><span data-ttu-id="3266f-114">Partiella konfigurationer i push-läge</span><span class="sxs-lookup"><span data-stu-id="3266f-114">Partial configurations in push mode</span></span>

<span data-ttu-id="3266f-115">För att använda partiella konfigurationer i push-läge måste konfigurera du LCM på målnoden att ta emot partiella konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="3266f-115">To use partial configurations in push mode, you configure the LCM on the target node to receive the partial configurations.</span></span> <span data-ttu-id="3266f-116">Varje partiell konfiguration måste skickas till målet med hjälp av den `Publish-DSCConfiguration` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3266f-116">Each partial configuration must be pushed to the target by using the `Publish-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="3266f-117">Målnoden kombinerar sedan partiell konfiguration i en enda konfiguration och du kan tillämpa konfigurationen genom att anropa den [Start-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Start-DscConfiguration) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3266f-117">The target node then combines the partial configuration into a single configuration, and you can apply the configuration by calling the [Start-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Start-DscConfiguration) cmdlet.</span></span>

### <a name="configuring-the-lcm-for-push-mode-partial-configurations"></a><span data-ttu-id="3266f-118">Konfigurera LCM för push-läge partiella konfigurationer</span><span class="sxs-lookup"><span data-stu-id="3266f-118">Configuring the LCM for push-mode partial configurations</span></span>

<span data-ttu-id="3266f-119">Om du vill konfigurera LCM för partiella konfigurationer i push-läget, skapar du en **DSCLocalConfigurationManager** med en **PartialConfiguration** block för varje partiell konfiguration.</span><span class="sxs-lookup"><span data-stu-id="3266f-119">To configure the LCM for partial configurations in push mode, you create a **DSCLocalConfigurationManager** configuration with one **PartialConfiguration** block for each partial configuration.</span></span> <span data-ttu-id="3266f-120">Läs mer om hur du konfigurerar LCM [Windows konfigurerar den lokala Konfigurationshanteraren](/powershell/dsc/metaConfig).</span><span class="sxs-lookup"><span data-stu-id="3266f-120">For more information about configuring the LCM, see [Windows Configuring the Local Configuration Manager](/powershell/dsc/metaConfig).</span></span>
<span data-ttu-id="3266f-121">I följande exempel visas en LCM-konfiguration som förväntar sig två partiella konfigurationer – en som distribuerar Operativsystemet och en som distribuerar och konfigurerar SharePoint.</span><span class="sxs-lookup"><span data-stu-id="3266f-121">The following example shows an LCM configuration that expects two partial configurations—one that deploys the OS, and one that deploys and configures SharePoint.</span></span>

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

<span data-ttu-id="3266f-122">Den **RefreshMode** för varje partiell konfiguration är inställd på ”Push”.</span><span class="sxs-lookup"><span data-stu-id="3266f-122">The **RefreshMode** for each partial configuration is set to "Push".</span></span> <span data-ttu-id="3266f-123">Namnen på de **PartialConfiguration** block (i det här fallet ”ServiceAccountConfig” och ”SharePointConfig”) måste överensstämma exakt namnen på de konfigurationer som skickas till målnoden.</span><span class="sxs-lookup"><span data-stu-id="3266f-123">The names of the **PartialConfiguration** blocks (in this case, "ServiceAccountConfig" and "SharePointConfig") must match exactly the names of the configurations that are pushed to the target node.</span></span>

> [!Note]
> <span data-ttu-id="3266f-124">Namngivna för var och en **PartialConfiguration** block måste matcha namnet på konfigurationen som det anges i konfigurationsskript inte namnet på den MOF-fil som ska vara antingen namnet på målnoden eller `localhost`.</span><span class="sxs-lookup"><span data-stu-id="3266f-124">The named of each **PartialConfiguration** block must match the actual name of the configuration as it is specified in the configuration script, not the name of the MOF file, which should be either the name of the target node or `localhost`.</span></span>

### <a name="publishing-and-starting-push-mode-partial-configurations"></a><span data-ttu-id="3266f-125">Publicera och starta push-läge partiella konfigurationer</span><span class="sxs-lookup"><span data-stu-id="3266f-125">Publishing and starting push-mode partial configurations</span></span>

<span data-ttu-id="3266f-126">Du sedan anropa [publicera-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) för varje konfiguration kan skicka mapparna som innehåller configuration-dokument som de **sökväg** parametrar.</span><span class="sxs-lookup"><span data-stu-id="3266f-126">You then call [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) for each configuration, passing the folders that contain the configuration documents as the **Path** parameters.</span></span> <span data-ttu-id="3266f-127">`Publish-DSCConfiguration`placerar configuration MOF-filer till målnoder.</span><span class="sxs-lookup"><span data-stu-id="3266f-127">`Publish-DSCConfiguration`places the configuration MOF files to the target nodes.</span></span> <span data-ttu-id="3266f-128">När du har publicerat båda konfigurationerna kan du anropa `Start-DSCConfiguration –UseExisting` på målnoden.</span><span class="sxs-lookup"><span data-stu-id="3266f-128">After publishing both configurations, you can call `Start-DSCConfiguration –UseExisting` on the target node.</span></span>

<span data-ttu-id="3266f-129">Exempel: Om du har skapat i följande konfiguration MOF-dokument på noden redigering:</span><span class="sxs-lookup"><span data-stu-id="3266f-129">For example, if you have compiled the following configuration MOF documents on the authoring node:</span></span>

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

    Directory: C:\DscTests\SharePointConfig

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       11/17/2016   4:14 PM           1930 TestVM.mof
```

<span data-ttu-id="3266f-130">Du skulle publicera och köra konfigurationerna som på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="3266f-130">You would publish and run the configurations as follows:</span></span>

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
> <span data-ttu-id="3266f-131">Användaren som kör den [publicera-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet måste ha administratörsbehörighet på målnoden.</span><span class="sxs-lookup"><span data-stu-id="3266f-131">The user running the [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet must have administrator privileges on the target node.</span></span>

## <a name="partial-configurations-in-pull-mode"></a><span data-ttu-id="3266f-132">Partiella konfigurationer i pull-läge</span><span class="sxs-lookup"><span data-stu-id="3266f-132">Partial configurations in pull mode</span></span>

<span data-ttu-id="3266f-133">Partiella konfigurationer kan hämtas från en eller flera pull-servrar (Mer information om pull-servrar finns i [Windows PowerShell Desired State Configuration Pull servrar](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="3266f-133">Partial configurations can be pulled from one or more pull servers (for more information about pull servers, see [Windows PowerShell Desired State Configuration Pull Servers](pullServer.md).</span></span> <span data-ttu-id="3266f-134">Om du vill göra detta måste behöva du konfigurera LCM på målnoden att hämta partiella konfigurationer och namnge och hitta korrekt configuration-dokument på pull-servrar.</span><span class="sxs-lookup"><span data-stu-id="3266f-134">To do this, you have to configure the LCM on the target node to pull the partial configurations, and name and locate the configuration documents properly on the pull servers.</span></span>

### <a name="configuring-the-lcm-for-pull-node-configurations"></a><span data-ttu-id="3266f-135">Konfigurera LCM för pull-nodkonfigurationer</span><span class="sxs-lookup"><span data-stu-id="3266f-135">Configuring the LCM for pull node configurations</span></span>

<span data-ttu-id="3266f-136">Om du vill konfigurera MGM om du vill dra partiella konfigurationer från en pull-server du definierar hämtningsservern i antingen en **ConfigurationRepositoryWeb** (för en HTTP-pull-server) eller **ConfigurationRepositoryShare** () för en SMB-pullserver) block.</span><span class="sxs-lookup"><span data-stu-id="3266f-136">To configure the LCM to pull partial configurations from a pull server, you define the pull server in either a **ConfigurationRepositoryWeb** (for an HTTP pull server) or **ConfigurationRepositoryShare** (for an SMB pull server) block.</span></span> <span data-ttu-id="3266f-137">Du kan sedan skapa **PartialConfiguration** block som refererar till den pull-servern med hjälp av den **ConfigurationSource** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="3266f-137">You then create **PartialConfiguration** blocks that refer to the pull server by using the **ConfigurationSource** property.</span></span> <span data-ttu-id="3266f-138">Du måste också skapa en **inställningar** block anger att LCM använder pull-läge och ange den **ConfigurationNames** eller **ConfigurationID** som hämtningsservern och mål noden används för att identifiera konfigurationerna.</span><span class="sxs-lookup"><span data-stu-id="3266f-138">You also need to create a **Settings** block to specify that the LCM uses pull mode, and to specify the **ConfigurationNames** or **ConfigurationID** that the pull server and target node use to identify the configurations.</span></span> <span data-ttu-id="3266f-139">Följande meta-konfigurationen definierar en HTTP-pull-server med namnet CONTOSO PullSrv och två partiella konfigurationer som använder som pull-servern.</span><span class="sxs-lookup"><span data-stu-id="3266f-139">The following meta-configuration defines an HTTP pull server named CONTOSO-PullSrv and two partial configurations that use that pull server.</span></span>

<span data-ttu-id="3266f-140">Mer information om hur du konfigurerar en LCM med hjälp av **ConfigurationNames**, se [konfigurera en hämtningsklient med konfigurationsnamn](pullClientConfigNames.md).</span><span class="sxs-lookup"><span data-stu-id="3266f-140">For more information about configuring the LCM using **ConfigurationNames**, see [Setting up a pull client using configuration names](pullClientConfigNames.md).</span></span>
<span data-ttu-id="3266f-141">Information om hur du konfigurerar en LCM med hjälp av **ConfigurationID**, se [konfigurera en hämtningsklient med konfigurations-ID](pullClientConfigID.md).</span><span class="sxs-lookup"><span data-stu-id="3266f-141">For information about configuring the LCM using **ConfigurationID**, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configuration-names"></a><span data-ttu-id="3266f-142">Konfigurera LCM för pull-läge konfigurationer med konfigurationsnamn</span><span class="sxs-lookup"><span data-stu-id="3266f-142">Configuring the LCM for pull mode configurations using configuration names</span></span>

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

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configurationid"></a><span data-ttu-id="3266f-143">Konfigurera LCM för pull-läge konfigurationer med hjälp av ConfigurationID</span><span class="sxs-lookup"><span data-stu-id="3266f-143">Configuring the LCM for pull mode configurations using ConfigurationID</span></span>

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

<span data-ttu-id="3266f-144">Du kan hämta partiella konfigurationer från mer än en pull-server – du behöver bara definiera varje pull-server och sedan referera till lämplig hämtningsservern i varje **PartialConfiguration** block.</span><span class="sxs-lookup"><span data-stu-id="3266f-144">You can pull partial configurations from more than one pull server—you would just need to define each pull server, and then refer to the appropriate pull server in each **PartialConfiguration** block.</span></span>

<span data-ttu-id="3266f-145">När du har skapat meta-konfigurationen, måste du köra det för att skapa en konfigurationsdokumentet (en MOF-fil) och sedan anropa [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) konfigurera LCM.</span><span class="sxs-lookup"><span data-stu-id="3266f-145">After creating the meta-configuration, you must run it to create a configuration document (a MOF file), and then call [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) to configure the LCM.</span></span>

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationnames"></a><span data-ttu-id="3266f-146">Namnge och placera configuration-dokument på hämtningsservern (ConfigurationNames)</span><span class="sxs-lookup"><span data-stu-id="3266f-146">Naming and placing the configuration documents on the pull server (ConfigurationNames)</span></span>

<span data-ttu-id="3266f-147">Partiell konfigurationsdokument måste placeras i den angivna mappen i den **ConfigurationPath** i den `web.config` -filen för hämtningsservern (vanligtvis `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span><span class="sxs-lookup"><span data-stu-id="3266f-147">The partial configuration documents must be placed in the folder specified as the **ConfigurationPath** in the `web.config` file for the pull server (typically `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span></span>

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-51"></a><span data-ttu-id="3266f-148">Namnge configuration dokument på hämtningsservern i PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="3266f-148">Naming configuration documents on the pull server in PowerShell 5.1</span></span>

<span data-ttu-id="3266f-149">Om du hämtar bara en partiell konfiguration från en enskild pull-server kan configuration dokumentet ha vilket namn.</span><span class="sxs-lookup"><span data-stu-id="3266f-149">If you are pulling only one partial configuration from an individual pull server, the configuration document can have any name.</span></span>
<span data-ttu-id="3266f-150">Om du hämtar mer än en partiell konfiguration från en pull-server configuration dokumentet döpa antingen `<ConfigurationName>.mof`, där *ConfigurationName* är namnet på partiell konfiguration eller `<ConfigurationName>.<NodeName>.mof`, där  *ConfigurationName* är namnet på partiell konfiguration och *nodnamn* är namnet på målnoden.</span><span class="sxs-lookup"><span data-stu-id="3266f-150">If you are pulling more than one partial configuration from a pull server, the configuration document can be named either `<ConfigurationName>.mof`, where *ConfigurationName* is the name of the partial configuration, or `<ConfigurationName>.<NodeName>.mof`, where  *ConfigurationName* is the name of the partial configuration, and *NodeName* is the name of the target node.</span></span>
<span data-ttu-id="3266f-151">Detta kan du pull konfigurationer från Azure Automation DSC-hämtningsservern.</span><span class="sxs-lookup"><span data-stu-id="3266f-151">This allows you to pull configurations from Azure Automation DSC pull server.</span></span>

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-50"></a><span data-ttu-id="3266f-152">Namnge configuration dokument på hämtningsservern i PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="3266f-152">Naming configuration documents on the pull server in PowerShell 5.0</span></span>

<span data-ttu-id="3266f-153">Av konfigurationsdokument måste ha namnet på följande sätt: `ConfigurationName.mof`, där *ConfigurationName* är namnet på partiell konfiguration.</span><span class="sxs-lookup"><span data-stu-id="3266f-153">The configuration documents must be named as follows: `ConfigurationName.mof`, where *ConfigurationName* is the name of the partial configuration.</span></span> <span data-ttu-id="3266f-154">I vårt exempel ska configuration dokument namnges enligt följande:</span><span class="sxs-lookup"><span data-stu-id="3266f-154">For our example, the configuration documents should be named as follows:</span></span>

```
ServiceAccountConfig.mof
ServiceAccountConfig.mof.checksum
SharePointConfig.mof
SharePointConfig.mof.checksum
```

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationid"></a><span data-ttu-id="3266f-155">Namnge och placera configuration-dokument på hämtningsservern (ConfigurationID)</span><span class="sxs-lookup"><span data-stu-id="3266f-155">Naming and placing the configuration documents on the pull server (ConfigurationID)</span></span>

<span data-ttu-id="3266f-156">Partiell konfigurationsdokument måste placeras i den angivna mappen i den **ConfigurationPath** i den `web.config` -filen för hämtningsservern (vanligtvis `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span><span class="sxs-lookup"><span data-stu-id="3266f-156">The partial configuration documents must be placed in the folder specified as the **ConfigurationPath** in the `web.config` file for the pull server (typically `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span></span> <span data-ttu-id="3266f-157">Av konfigurationsdokument måste ha namnet på följande sätt: _ConfigurationName_.</span><span class="sxs-lookup"><span data-stu-id="3266f-157">The configuration documents must be named as follows: _ConfigurationName_.</span></span> <span data-ttu-id="3266f-158">\* ConfigurationID8`.mof`, där _ConfigurationName_ är namnet på partiell konfiguration och _ConfigurationID_ definieras konfigurations-ID i LCM på målnoden.</span><span class="sxs-lookup"><span data-stu-id="3266f-158">\*ConfigurationID8`.mof`, where _ConfigurationName_ is the name of the partial configuration and _ConfigurationID_ is the configuration ID defined in the LCM on the target node.</span></span> <span data-ttu-id="3266f-159">I vårt exempel ska configuration dokument namnges enligt följande:</span><span class="sxs-lookup"><span data-stu-id="3266f-159">For our example, the configuration documents should be named as follows:</span></span>

```
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
```

### <a name="running-partial-configurations-from-a-pull-server"></a><span data-ttu-id="3266f-160">Kör partiella konfigurationer från en pull-server</span><span class="sxs-lookup"><span data-stu-id="3266f-160">Running partial configurations from a pull server</span></span>

<span data-ttu-id="3266f-161">När LCM på målnoden har konfigurerats och konfigurationen dokument har skapats och rätt namn på hämtningsservern målnoden hämtar partiella konfigurationer kan kombinera dem och tillämpa den resulterande konfigurationen enligt de vanliga intervall som anges av den **RefreshFrequencyMins** egenskapen för LCM.</span><span class="sxs-lookup"><span data-stu-id="3266f-161">After the LCM on the target node has been configured, and the configuration documents have been created and properly named on the pull server, the target node will pull the partial configurations, combine them, and apply the resulting configuration at regular intervals as specified by the **RefreshFrequencyMins** property of the LCM.</span></span> <span data-ttu-id="3266f-162">Om du vill framtvinga en uppdatering kan du anropa den [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration) cmdleten för att hämta konfigurationer, och sedan `Start-DSCConfiguration –UseExisting` att de ska appliceras.</span><span class="sxs-lookup"><span data-stu-id="3266f-162">If you want to force a refresh, you can call the [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration) cmdlet, to pull the configurations, and then `Start-DSCConfiguration –UseExisting` to apply them.</span></span>

## <a name="partial-configurations-in-mixed-push-and-pull-modes"></a><span data-ttu-id="3266f-163">Partiella konfigurationer i blandat sändnings- och mottagningsläge</span><span class="sxs-lookup"><span data-stu-id="3266f-163">Partial configurations in mixed push and pull modes</span></span>

<span data-ttu-id="3266f-164">Du kan även blanda push och pull-lägen för partiella konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="3266f-164">You can also mix push and pull modes for partial configurations.</span></span> <span data-ttu-id="3266f-165">Det vill säga att du kan ha en partiell konfiguration som hämtas från en pull-server, medan en annan partiell konfiguration skickas.</span><span class="sxs-lookup"><span data-stu-id="3266f-165">That is, you could have one partial configuration that is pulled from a pull server, while another partial configuration is pushed.</span></span> <span data-ttu-id="3266f-166">Ange uppdatering för varje partiell konfiguration enligt beskrivningen i föregående avsnitt.</span><span class="sxs-lookup"><span data-stu-id="3266f-166">Specify the refresh mode for each partial configuration as described in the previous sections.</span></span>
<span data-ttu-id="3266f-167">Till exempel följande meta-konfiguration beskriver det här exemplet med den `ServiceAccountConfig` partiell konfiguration i pull-läge och `SharePointConfig` partiell konfiguration i push-läget.</span><span class="sxs-lookup"><span data-stu-id="3266f-167">For example, the following meta-configuration describes the same example, with the `ServiceAccountConfig` partial configuration in pull mode and the `SharePointConfig` partial configuration in push mode.</span></span>

### <a name="mixed-push-and-pull-modes-using-configurationnames"></a><span data-ttu-id="3266f-168">Blandade sändnings- och mottagningsläge med ConfigurationNames</span><span class="sxs-lookup"><span data-stu-id="3266f-168">Mixed push and pull modes using ConfigurationNames</span></span>

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

### <a name="mixed-push-and-pull-modes-using-configurationid"></a><span data-ttu-id="3266f-169">Blandade sändnings- och mottagningsläge med ConfigurationID</span><span class="sxs-lookup"><span data-stu-id="3266f-169">Mixed push and pull modes using ConfigurationID</span></span>

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

<span data-ttu-id="3266f-170">Observera att den **RefreshMode** anges i inställningsblocket är ”Pull”, men **RefreshMode** för den `SharePointConfig` partiell konfiguration är ”Push”.</span><span class="sxs-lookup"><span data-stu-id="3266f-170">Note that the **RefreshMode** specified in the Settings block is "Pull", but the **RefreshMode** for the `SharePointConfig` partial configuration is "Push".</span></span>

<span data-ttu-id="3266f-171">Namnge och leta upp configuration MOF-filer enligt beskrivningen ovan för sina respektive uppdatering lägen.</span><span class="sxs-lookup"><span data-stu-id="3266f-171">Name and locate the configuration MOF files as described above for their respective refresh modes.</span></span> <span data-ttu-id="3266f-172">Anropa `Publish-DSCConfiguration` att publicera den `SharePointConfig` partiell konfiguration och antingen vänta tills den `ServiceAccountConfig` konfigurationen som ska hämtas från hämtningsservern eller tvingar fram en uppdatering genom att anropa [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration).</span><span class="sxs-lookup"><span data-stu-id="3266f-172">Call `Publish-DSCConfiguration` to publish the `SharePointConfig` partial configuration, and either wait for the `ServiceAccountConfig` configuration to be pulled from the pull server, or force a refresh by calling [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration).</span></span>

## <a name="example-serviceaccountconfig-partial-configuration"></a><span data-ttu-id="3266f-173">ServiceAccountConfig partiellt exempelkonfiguration</span><span class="sxs-lookup"><span data-stu-id="3266f-173">Example ServiceAccountConfig Partial Configuration</span></span>

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

## <a name="example-sharepointconfig-partial-configuration"></a><span data-ttu-id="3266f-174">SharePointConfig partiellt exempelkonfiguration</span><span class="sxs-lookup"><span data-stu-id="3266f-174">Example SharePointConfig Partial Configuration</span></span>

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

## <a name="see-also"></a><span data-ttu-id="3266f-175">Se även</span><span class="sxs-lookup"><span data-stu-id="3266f-175">See Also</span></span>

[<span data-ttu-id="3266f-176">Windows PowerShell Desired State Configuration Pull-servrar</span><span class="sxs-lookup"><span data-stu-id="3266f-176">Windows PowerShell Desired State Configuration Pull Servers</span></span>](pullServer.md)

[<span data-ttu-id="3266f-177">Windows som konfigurerar den lokala Konfigurationshanteraren</span><span class="sxs-lookup"><span data-stu-id="3266f-177">Windows Configuring the Local Configuration Manager</span></span>](/powershell/dsc/metaConfig)