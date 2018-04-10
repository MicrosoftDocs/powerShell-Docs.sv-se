---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: Partiell PowerShell Desired State Configuration-konfigurationer
ms.openlocfilehash: cd2812724c2279a7effc4739f23193c1dc836ce5
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="powershell-desired-state-configuration-partial-configurations"></a><span data-ttu-id="4da60-103">Partiell PowerShell Desired State Configuration-konfigurationer</span><span class="sxs-lookup"><span data-stu-id="4da60-103">PowerShell Desired State Configuration partial configurations</span></span>

><span data-ttu-id="4da60-104">Gäller för: Windows PowerShell 5.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="4da60-104">Applies To: Windows PowerShell 5.0 and later.</span></span>

<span data-ttu-id="4da60-105">I PowerShell 5.0 kan önskad tillstånd Configuration (DSC) konfigurationer som ska levereras i fragment och från flera källor.</span><span class="sxs-lookup"><span data-stu-id="4da60-105">In PowerShell 5.0, Desired State Configuration (DSC) allows configurations to be delivered in fragments and from multiple sources.</span></span> <span data-ttu-id="4da60-106">Den lokala Configuration Manager (MGM) på målnoden sätter ihop fragment innan du tillämpar dem som en enda konfiguration.</span><span class="sxs-lookup"><span data-stu-id="4da60-106">The Local Configuration Manager (LCM) on the target node puts the fragments together before applying them as a single configuration.</span></span> <span data-ttu-id="4da60-107">Den här funktionen tillåter delning kontroll över konfiguration mellan olika team eller enskilda användare.</span><span class="sxs-lookup"><span data-stu-id="4da60-107">This capability allows sharing control of configuration between teams or individuals.</span></span>
<span data-ttu-id="4da60-108">Till exempel om två eller flera grupper med utvecklare samarbeta på en tjänst kan kanske de var vill skapa konfigurationer för att hantera sin del av tjänsten.</span><span class="sxs-lookup"><span data-stu-id="4da60-108">For example, if two or more teams of developers are collaborating on a service, they might each want to create configurations to manage their part of the service.</span></span> <span data-ttu-id="4da60-109">Var och en av de här konfigurationerna kan hämtas från olika pull-servrar och de gick att lägga till under de olika faserna i utvecklingen av.</span><span class="sxs-lookup"><span data-stu-id="4da60-109">Each of these configurations could be pulled from different pull servers, and they could be added at different stages of development.</span></span> <span data-ttu-id="4da60-110">Partiell konfigurationer kan också olika personer eller grupper för att styra olika aspekter av hur du konfigurerar noder utan att behöva koordinera redigering av ett enda dokument.</span><span class="sxs-lookup"><span data-stu-id="4da60-110">Partial configurations also allow different individuals or teams to control different aspects of configuring nodes without having to coordinate the editing of a single configuration document.</span></span> <span data-ttu-id="4da60-111">Ett team kan vara ansvariga för att distribuera en virtuell dator och operativsystem, medan ett annat team kan distribuera andra program och tjänster på den virtuella datorn.</span><span class="sxs-lookup"><span data-stu-id="4da60-111">For example, one team might be responsible for deploying a VM and operating system, while another team might deploy other applications and services on that VM.</span></span> <span data-ttu-id="4da60-112">Varje team kan skapa egna konfigurationer, utan någon av dem att i onödan komplicerade med partiellt konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="4da60-112">With partial configurations, each team can create its own configuration, without either of them being unnecessarily complicated.</span></span>

<span data-ttu-id="4da60-113">Du kan använda partiella konfigurationer i push-läge, pull-läge eller en kombination av båda.</span><span class="sxs-lookup"><span data-stu-id="4da60-113">You can use partial configurations in push mode, pull mode, or a combination of the two.</span></span>

## <a name="partial-configurations-in-push-mode"></a><span data-ttu-id="4da60-114">Partiell konfigurationer i push-läge</span><span class="sxs-lookup"><span data-stu-id="4da60-114">Partial configurations in push mode</span></span>
<span data-ttu-id="4da60-115">Om du vill använda delvis konfigurationer i push-läge, konfigurerar du MGM på målnoden för att ta emot de partiella konfigurationerna.</span><span class="sxs-lookup"><span data-stu-id="4da60-115">To use partial configurations in push mode, you configure the LCM on the target node to receive the partial configurations.</span></span> <span data-ttu-id="4da60-116">Varje partiella konfiguration måste skickas till målet med hjälp av cmdleten publicera DSCConfiguration.</span><span class="sxs-lookup"><span data-stu-id="4da60-116">Each partial configuration must be pushed to the target by using the Publish-DSCConfiguration cmdlet.</span></span> <span data-ttu-id="4da60-117">Målnoden kombinerar sedan partiella konfigurationen i konfigurationen för en och du kan använda konfigurationen genom att anropa den [Start DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4da60-117">The target node then combines the partial configuration into a single configuration, and you can apply the configuration by calling the [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) cmdlet.</span></span>

### <a name="configuring-the-lcm-for-push-mode-partial-configurations"></a><span data-ttu-id="4da60-118">Konfigurera MGM för push-läge partiella konfigurationer</span><span class="sxs-lookup"><span data-stu-id="4da60-118">Configuring the LCM for push-mode partial configurations</span></span>
<span data-ttu-id="4da60-119">Om du vill konfigurera MGM för partiellt konfigurationer i push-läge, som du skapar en **DSCLocalConfigurationManager** konfiguration med en **PartialConfiguration** block för varje partiella konfiguration.</span><span class="sxs-lookup"><span data-stu-id="4da60-119">To configure the LCM for partial configurations in push mode, you create a **DSCLocalConfigurationManager** configuration with one **PartialConfiguration** block for each partial configuration.</span></span> <span data-ttu-id="4da60-120">Mer information om hur du konfigurerar MGM finns [Windows konfigurera den lokala Configuration Manager](https://technet.microsoft.com/library/mt421188.aspx).</span><span class="sxs-lookup"><span data-stu-id="4da60-120">For more information about configuring the LCM, see [Windows Configuring the Local Configuration Manager](https://technet.microsoft.com/library/mt421188.aspx).</span></span>
<span data-ttu-id="4da60-121">I följande exempel visas en MGM konfiguration som förväntar sig konfigurationer av två delar, en som distribuerar Operativsystemet och en som distribuerar och konfigurerar SharePoint.</span><span class="sxs-lookup"><span data-stu-id="4da60-121">The following example shows an LCM configuration that expects two partial configurations—one that deploys the OS, and one that deploys and configures SharePoint.</span></span>

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

<span data-ttu-id="4da60-122">Den **RefreshMode** för varje partiella konfiguration har värdet ”Push”.</span><span class="sxs-lookup"><span data-stu-id="4da60-122">The **RefreshMode** for each partial configuration is set to "Push".</span></span> <span data-ttu-id="4da60-123">Namnen på de **PartialConfiguration** block (i det här fallet ”ServiceAccountConfig” och ”SharePointConfig”) måste matcha exakt namnen på de konfigurationer som pushas till målnoden.</span><span class="sxs-lookup"><span data-stu-id="4da60-123">The names of the **PartialConfiguration** blocks (in this case, "ServiceAccountConfig" and "SharePointConfig") must match exactly the names of the configurations that are pushed to the target node.</span></span>

><span data-ttu-id="4da60-124">**Obs:** namngivna för varje **PartialConfiguration** block måste matcha det faktiska namnet på konfigurationen som den har angetts i konfigurationsskript inte namnet på MOF-filen som ska vara antingen namnet på den målnoden eller `localhost`.</span><span class="sxs-lookup"><span data-stu-id="4da60-124">**Note:** The named of each **PartialConfiguration** block must match the actual name of the configuration as it is specified in the configuration script, not the name of the MOF file, which should be either the name of the target node or `localhost`.</span></span>

### <a name="publishing-and-starting-push-mode-partial-configurations"></a><span data-ttu-id="4da60-125">Publicera och starta partiella konfigurationer för push-läge</span><span class="sxs-lookup"><span data-stu-id="4da60-125">Publishing and starting push-mode partial configurations</span></span>

<span data-ttu-id="4da60-126">Sedan anropar [publicera DSCConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/psdesiredstateconfiguration/publish-dscconfiguration) för varje konfiguration kan skicka mapparna som innehåller configuration-dokument som den **sökväg** parametrar.</span><span class="sxs-lookup"><span data-stu-id="4da60-126">You then call [Publish-DSCConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/psdesiredstateconfiguration/publish-dscconfiguration) for each configuration, passing the folders that contain the configuration documents as the **Path** parameters.</span></span> <span data-ttu-id="4da60-127">`Publish-DSCConfiguration`placerar configuration MOF-filer till målnoder.</span><span class="sxs-lookup"><span data-stu-id="4da60-127">`Publish-DSCConfiguration`places the configuration MOF files to the target nodes.</span></span> <span data-ttu-id="4da60-128">När du har publicerat båda konfigurationerna kan du anropa `Start-DSCConfiguration –UseExisting` på målnoden.</span><span class="sxs-lookup"><span data-stu-id="4da60-128">After publishing both configurations, you can call `Start-DSCConfiguration –UseExisting` on the target node.</span></span>

<span data-ttu-id="4da60-129">Till exempel om du har sammanställt följande konfiguration MOF dokument på noden redigering:</span><span class="sxs-lookup"><span data-stu-id="4da60-129">For example, if you have compiled the following configuration MOF documents on the authoring node:</span></span>

```powershell
PS C:\PartialConfigTest> Get-ChildItem -Recurse


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

<span data-ttu-id="4da60-130">Du skulle publicera och köra konfigurationerna på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="4da60-130">You would publish and run the configurations as follows:</span></span>

```powershell
PS C:\PartialConfigTest> Publish-DscConfiguration .\ServiceAccountConfig -ComputerName 'TestVM'
PS C:\PartialConfigTest> Publish-DscConfiguration .\SharePointConfig -ComputerName 'TestVM'
PS C:\PartialConfigTest> Start-DscConfiguration -UseExisting -ComputerName 'TestVM'

Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
17     Job17           Configuratio... Running       True            TestVM            Start-DscConfiguration...
```

><span data-ttu-id="4da60-131">**Obs:** användaren som kör den [publicera DSCConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/psdesiredstateconfiguration/publish-dscconfiguration) cmdlet måste ha administratörsbehörighet på målnoden.</span><span class="sxs-lookup"><span data-stu-id="4da60-131">**Note:** The user running the [Publish-DSCConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/psdesiredstateconfiguration/publish-dscconfiguration) cmdlet must have administrator privileges on the target node.</span></span>

## <a name="partial-configurations-in-pull-mode"></a><span data-ttu-id="4da60-132">Partiell konfigurationer i pull-läge</span><span class="sxs-lookup"><span data-stu-id="4da60-132">Partial configurations in pull mode</span></span>

<span data-ttu-id="4da60-133">Partiell konfigurationer som kan hämtas från en eller flera pull-servrar (Mer information om pull-servrar finns [Windows PowerShell önskad tillstånd Pull Konfigurationsservrar](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="4da60-133">Partial configurations can be pulled from one or more pull servers (for more information about pull servers, see [Windows PowerShell Desired State Configuration Pull Servers](pullServer.md).</span></span> <span data-ttu-id="4da60-134">Du måste konfigurera MGM på målnoden till pull-konfigurationer som delar ett namn och hitta korrekt configuration-dokument på pull-servrar för att göra detta.</span><span class="sxs-lookup"><span data-stu-id="4da60-134">To do this, you have to configure the LCM on the target node to pull the partial configurations, and name and locate the configuration documents properly on the pull servers.</span></span>

### <a name="configuring-the-lcm-for-pull-node-configurations"></a><span data-ttu-id="4da60-135">Konfigurera MGM för pull-nodkonfigurationer</span><span class="sxs-lookup"><span data-stu-id="4da60-135">Configuring the LCM for pull node configurations</span></span>

<span data-ttu-id="4da60-136">Om du vill konfigurera MGM om du vill dra partiella konfigurationer från en pull-server du definierar pull-server i antingen en **ConfigurationRepositoryWeb** (för en HTTP-pull-server) eller **ConfigurationRepositoryShare** () för en SMB-pull-server) block.</span><span class="sxs-lookup"><span data-stu-id="4da60-136">To configure the LCM to pull partial configurations from a pull server, you define the pull server in either a **ConfigurationRepositoryWeb** (for an HTTP pull server) or **ConfigurationRepositoryShare** (for an SMB pull server) block.</span></span> <span data-ttu-id="4da60-137">Skapa sedan **PartialConfiguration** block som refererar till den pull-servern med hjälp av den **ConfigurationSource** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="4da60-137">You then create **PartialConfiguration** blocks that refer to the pull server by using the **ConfigurationSource** property.</span></span> <span data-ttu-id="4da60-138">Du måste också skapa en **inställningar** block vill ange att MGM om du använder pull-läge och ange den **ConfigurationNames** eller **ConfigurationID** som pull-server och mål nod Använd för att identifiera konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="4da60-138">You also need to create a **Settings** block to specify that the LCM uses pull mode, and to specify the **ConfigurationNames** or **ConfigurationID** that the pull server and target node use to identify the configurations.</span></span> <span data-ttu-id="4da60-139">Följande meta-konfiguration definierar en HTTP-pull-server med namnet CONTOSO PullSrv och två delar konfigurationer som använder som pull-server.</span><span class="sxs-lookup"><span data-stu-id="4da60-139">The following meta-configuration defines an HTTP pull server named CONTOSO-PullSrv and two partial configurations that use that pull server.</span></span>

<span data-ttu-id="4da60-140">Mer information om hur du konfigurerar MGM med **ConfigurationNames**, se [ställa in en pull-klient som använder konfigurationsnamn](pullClientConfigNames.md).</span><span class="sxs-lookup"><span data-stu-id="4da60-140">For more information about configuring the LCM using **ConfigurationNames**, see [Setting up a pull client using configuration names](pullClientConfigNames.md).</span></span>
<span data-ttu-id="4da60-141">Information om hur du konfigurerar MGM med **ConfigurationID**, se [installera en pull-klient med hjälp av konfigurations-ID](pullClientConfigID.md).</span><span class="sxs-lookup"><span data-stu-id="4da60-141">For information about configuring the LCM using **ConfigurationID**, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configuration-names"></a><span data-ttu-id="4da60-142">Konfigurera MGM för pull-läge konfigurationer med konfigurationsnamn</span><span class="sxs-lookup"><span data-stu-id="4da60-142">Configuring the LCM for pull mode configurations using configuration names</span></span>

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

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configurationid"></a><span data-ttu-id="4da60-143">Konfigurera MGM för pull-läge konfigurationer med hjälp av ConfigurationID</span><span class="sxs-lookup"><span data-stu-id="4da60-143">Configuring the LCM for pull mode configurations using ConfigurationID</span></span>

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

<span data-ttu-id="4da60-144">Du kan dra partiella konfigurationer från mer än en pull-server – du behöver bara definiera varje pull-server och referera till lämplig pull-server i varje **PartialConfiguration** block.</span><span class="sxs-lookup"><span data-stu-id="4da60-144">You can pull partial configurations from more than one pull server—you would just need to define each pull server, and then refer to the appropriate pull server in each **PartialConfiguration** block.</span></span>

<span data-ttu-id="4da60-145">När du har skapat meta-konfigurationen måste du köra det för att skapa ett configuration-dokument (en MOF-fil) och sedan anropa [Set DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621(v=wps.630).aspx) att konfigurera MGM.</span><span class="sxs-lookup"><span data-stu-id="4da60-145">After creating the meta-configuration, you must run it to create a configuration document (a MOF file), and then call [Set-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621(v=wps.630).aspx) to configure the LCM.</span></span>

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationnames"></a><span data-ttu-id="4da60-146">Namnge och placera configuration-dokument på hämtningsservern (ConfigurationNames)</span><span class="sxs-lookup"><span data-stu-id="4da60-146">Naming and placing the configuration documents on the pull server (ConfigurationNames)</span></span>

<span data-ttu-id="4da60-147">Partiell configuration-dokument måste placeras i den angivna mappen i den **ConfigurationPath** i den `web.config` -filen för pull-server (vanligtvis `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span><span class="sxs-lookup"><span data-stu-id="4da60-147">The partial configuration documents must be placed in the folder specified as the **ConfigurationPath** in the `web.config` file for the pull server (typically `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span></span>

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-51"></a><span data-ttu-id="4da60-148">Namnge configuration dokument på hämtningsservern i PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="4da60-148">Naming configuration documents on the pull server in PowerShell 5.1</span></span>

<span data-ttu-id="4da60-149">Om du hämtar bara en partiell konfiguration från en enskild hämtningsservern kan configuration dokumentet ha vilket namn.</span><span class="sxs-lookup"><span data-stu-id="4da60-149">If you are pulling only one partial configuration from an individual pull server, the configuration document can have any name.</span></span>
<span data-ttu-id="4da60-150">Om du hämtar mer än en partiell konfiguration från en pull-server configuration dokumentet kan namnges antingen `<ConfigurationName>.mof`, där _ConfigurationName_ är namnet på den partiella konfigurationen eller `<ConfigurationName>.<NodeName>.mof`, där  _ConfigurationName_ är namnet på den partiella konfigurationen och _nodnamn_ är namnet på målnoden.</span><span class="sxs-lookup"><span data-stu-id="4da60-150">If you are pulling more than one partial configuration from a pull server, the configuration document can be named either `<ConfigurationName>.mof`, where _ConfigurationName_ is the name of the partial configuration, or `<ConfigurationName>.<NodeName>.mof`, where  _ConfigurationName_ is the name of the partial configuration, and _NodeName_ is the name of the target node.</span></span>
<span data-ttu-id="4da60-151">Detta gör att du kan pull konfigurationer från hämtningsservern i Azure Automation DSC.</span><span class="sxs-lookup"><span data-stu-id="4da60-151">This allows you to pull configurations from Azure Automation DSC pull server.</span></span>


#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-50"></a><span data-ttu-id="4da60-152">Namnge configuration dokument på hämtningsservern i PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="4da60-152">Naming configuration documents on the pull server in PowerShell 5.0</span></span>

<span data-ttu-id="4da60-153">Av konfigurationsdokument måste ha namnet på följande sätt: `ConfigurationName.mof`, där _ConfigurationName_ är namnet på den partiella konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="4da60-153">The configuration documents must be named as follows: `ConfigurationName.mof`, where _ConfigurationName_ is the name of the partial configuration.</span></span> <span data-ttu-id="4da60-154">I vårt exempel bör konfigurationsdokument vara namnet på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="4da60-154">For our example, the configuration documents should be named as follows:</span></span>

```
ServiceAccountConfig.mof
ServiceAccountConfig.mof.checksum
SharePointConfig.mof
SharePointConfig.mof.checksum
```

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationid"></a><span data-ttu-id="4da60-155">Namnge och placera configuration-dokument på hämtningsservern (ConfigurationID)</span><span class="sxs-lookup"><span data-stu-id="4da60-155">Naming and placing the configuration documents on the pull server (ConfigurationID)</span></span>

<span data-ttu-id="4da60-156">Partiell configuration-dokument måste placeras i den angivna mappen i den **ConfigurationPath** i den `web.config` -filen för pull-server (vanligtvis `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span><span class="sxs-lookup"><span data-stu-id="4da60-156">The partial configuration documents must be placed in the folder specified as the **ConfigurationPath** in the `web.config` file for the pull server (typically `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span></span> <span data-ttu-id="4da60-157">Av konfigurationsdokument måste ha namnet på följande sätt: _ConfigurationName_.</span><span class="sxs-lookup"><span data-stu-id="4da60-157">The configuration documents must be named as follows: _ConfigurationName_.</span></span> <span data-ttu-id="4da60-158">_ConfigurationID_`.mof`, där _ConfigurationName_ är namnet på den partiella konfigurationen och _ConfigurationID_ definieras konfigurations-ID i MGM på måldatorn noden.</span><span class="sxs-lookup"><span data-stu-id="4da60-158">_ConfigurationID_`.mof`, where _ConfigurationName_ is the name of the partial configuration and _ConfigurationID_ is the configuration ID defined in the LCM on the target node.</span></span> <span data-ttu-id="4da60-159">I vårt exempel bör konfigurationsdokument vara namnet på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="4da60-159">For our example, the configuration documents should be named as follows:</span></span>

```
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
```


### <a name="running-partial-configurations-from-a-pull-server"></a><span data-ttu-id="4da60-160">Kör delvis konfigurationer från en pull-server</span><span class="sxs-lookup"><span data-stu-id="4da60-160">Running partial configurations from a pull server</span></span>

<span data-ttu-id="4da60-161">När MGM på målnoden har konfigurerats och konfigurationen dokument har skapats och korrekt med namnet på hämtningsservern målnoden hämtar partiella konfigurationer, kombinera dem och tillämpa den resulterande konfigurationen regelbundet intervall som anges av den **RefreshFrequencyMins** -egenskapen för MGM.</span><span class="sxs-lookup"><span data-stu-id="4da60-161">After the LCM on the target node has been configured, and the configuration documents have been created and properly named on the pull server, the target node will pull the partial configurations, combine them, and apply the resulting configuration at regular intervals as specified by the **RefreshFrequencyMins** property of the LCM.</span></span> <span data-ttu-id="4da60-162">Om du vill framtvinga en uppdatering kan du anropa den [uppdatering DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541.aspx) cmdlet hämtar konfigurationerna och sedan `Start-DSCConfiguration –UseExisting` tillämpa dem.</span><span class="sxs-lookup"><span data-stu-id="4da60-162">If you want to force a refresh, you can call the [Update-DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541.aspx) cmdlet, to pull the configurations, and then `Start-DSCConfiguration –UseExisting` to apply them.</span></span>


## <a name="partial-configurations-in-mixed-push-and-pull-modes"></a><span data-ttu-id="4da60-163">Partiell konfigurationer i blandat läge för sändning och mottagning</span><span class="sxs-lookup"><span data-stu-id="4da60-163">Partial configurations in mixed push and pull modes</span></span>

<span data-ttu-id="4da60-164">Du kan också blanda push och pull-lägen för partiellt konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="4da60-164">You can also mix push and pull modes for partial configurations.</span></span> <span data-ttu-id="4da60-165">Det vill säga kan du ha en partiell konfiguration som hämtas från en pull-server, medan en annan partiell konfiguration är nedtryckt.</span><span class="sxs-lookup"><span data-stu-id="4da60-165">That is, you could have one partial configuration that is pulled from a pull server, while another partial configuration is pushed.</span></span> <span data-ttu-id="4da60-166">Ange uppdatera-läge för varje partiella konfiguration enligt beskrivningen i föregående avsnitt.</span><span class="sxs-lookup"><span data-stu-id="4da60-166">Specify the refresh mode for each partial configuration as described in the previous sections.</span></span>
<span data-ttu-id="4da60-167">Till exempel följande meta-konfiguration beskriver det här exemplet med den `ServiceAccountConfig` partiella konfigurationen i pull-läge och `SharePointConfig` partiella konfigurationen i push-läge.</span><span class="sxs-lookup"><span data-stu-id="4da60-167">For example, the following meta-configuration describes the same example, with the `ServiceAccountConfig` partial configuration in pull mode and the `SharePointConfig` partial configuration in push mode.</span></span>

### <a name="mixed-push-and-pull-modes-using-configurationnames"></a><span data-ttu-id="4da60-168">Blandat sändnings- och mottagningsläge med ConfigurationNames</span><span class="sxs-lookup"><span data-stu-id="4da60-168">Mixed push and pull modes using ConfigurationNames</span></span>

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

### <a name="mixed-push-and-pull-modes-using-configurationid"></a><span data-ttu-id="4da60-169">Blandat sändnings- och mottagningsläge med ConfigurationID</span><span class="sxs-lookup"><span data-stu-id="4da60-169">Mixed push and pull modes using ConfigurationID</span></span>

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

<span data-ttu-id="4da60-170">Observera att den **RefreshMode** anges i inställningsblocket är ”dra”, men **RefreshMode** för den `SharePointConfig` partiella konfigurationen är ”Push”.</span><span class="sxs-lookup"><span data-stu-id="4da60-170">Note that the **RefreshMode** specified in the Settings block is "Pull", but the **RefreshMode** for the `SharePointConfig` partial configuration is "Push".</span></span>

<span data-ttu-id="4da60-171">Namn och hitta MOF konfigurationsfiler som beskrivs ovan för deras respektive uppdatering lägen.</span><span class="sxs-lookup"><span data-stu-id="4da60-171">Name and locate the configuration MOF files as described above for their respective refresh modes.</span></span> <span data-ttu-id="4da60-172">Anropa **publicera DSCConfiguration** att publicera den `SharePointConfig` partiella konfiguration och antingen vänta tills den `ServiceAccountConfig` konfigurationen som ska hämtas från servern pull eller framtvinga en uppdatering genom att anropa [ Uppdatera DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541(v=wps.630).aspx).</span><span class="sxs-lookup"><span data-stu-id="4da60-172">Call **Publish-DSCConfiguration** to publish the `SharePointConfig` partial configuration, and either wait for the `ServiceAccountConfig` configuration to be pulled from the pull server, or force a refresh by calling [Update-DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541(v=wps.630).aspx).</span></span>

## <a name="example-serviceaccountconfig-partial-configuration"></a><span data-ttu-id="4da60-173">ServiceAccountConfig partiell exempelkonfiguration</span><span class="sxs-lookup"><span data-stu-id="4da60-173">Example ServiceAccountConfig Partial Configuration</span></span>

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
## <a name="example-sharepointconfig-partial-configuration"></a><span data-ttu-id="4da60-174">SharePointConfig partiell exempelkonfiguration</span><span class="sxs-lookup"><span data-stu-id="4da60-174">Example SharePointConfig Partial Configuration</span></span>
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
##<a name="see-also"></a><span data-ttu-id="4da60-175">Se även</span><span class="sxs-lookup"><span data-stu-id="4da60-175">See Also</span></span>

<span data-ttu-id="4da60-176">**Begrepp**
[Windows PowerShell önskad Tillståndskonfiguration Pull-servrar](pullServer.md)</span><span class="sxs-lookup"><span data-stu-id="4da60-176">**Concepts**
[Windows PowerShell Desired State Configuration Pull Servers](pullServer.md)</span></span>

[<span data-ttu-id="4da60-177">Windows konfigurera den lokala Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="4da60-177">Windows Configuring the Local Configuration Manager</span></span>](https://technet.microsoft.com/library/mt421188.aspx)