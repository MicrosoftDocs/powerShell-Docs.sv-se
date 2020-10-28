---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Konfigurera en virtuell dator vid första uppstart med hjälp av DSC
description: Den här artikeln explans hur du konfigurerar en virtuell dator vid första uppstarten med DSC
ms.openlocfilehash: 9fa8c4a21486aaef87e1c0a3097e5983a378d98d
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92656195"
---
# <a name="configure-a-virtual-machines-at-initial-boot-up-by-using-dsc"></a><span data-ttu-id="89965-104">Konfigurera en virtuell dator vid första uppstart med hjälp av DSC</span><span class="sxs-lookup"><span data-stu-id="89965-104">Configure a virtual machines at initial boot-up by using DSC</span></span>

> [!IMPORTANT]
> <span data-ttu-id="89965-105">Gäller för: Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="89965-105">Applies To: Windows PowerShell 5.0</span></span>

## <a name="requirements"></a><span data-ttu-id="89965-106">Krav</span><span class="sxs-lookup"><span data-stu-id="89965-106">Requirements</span></span>

> [!NOTE]
> <span data-ttu-id="89965-107">Register nyckeln **dscautomationhostenabled registernyckel** som beskrivs i det här avsnittet är inte tillgänglig i PowerShell 4,0.</span><span class="sxs-lookup"><span data-stu-id="89965-107">The **DSCAutomationHostEnabled** registry key described in this topic is not available in PowerShell 4.0.</span></span> <span data-ttu-id="89965-108">Information om hur du konfigurerar nya virtuella datorer vid första uppstart i PowerShell 4,0 finns i [vill konfigurera dina datorer automatiskt med DSC vid första uppstarten?](https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)</span><span class="sxs-lookup"><span data-stu-id="89965-108">For information on how to configure new virtual machines at initial boot-up in PowerShell 4.0, see [Want to Automatically Configure Your Machines Using DSC at Initial Boot-up?](https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)</span></span>

<span data-ttu-id="89965-109">Om du vill köra de här exemplen behöver du:</span><span class="sxs-lookup"><span data-stu-id="89965-109">To run these examples, you will need:</span></span>

- <span data-ttu-id="89965-110">En startbar virtuell hård disk att arbeta med.</span><span class="sxs-lookup"><span data-stu-id="89965-110">A bootable VHD to work with.</span></span> <span data-ttu-id="89965-111">Du kan ladda ned en ISO-fil med en utvärderings version av Windows Server 2016 på [TechNet Evaluation Center](https://www.microsoft.com/evalcenter/evaluate-windows-server-2016).</span><span class="sxs-lookup"><span data-stu-id="89965-111">You can download an ISO with an evaluation copy of Windows Server 2016 at [TechNet Evaluation Center](https://www.microsoft.com/evalcenter/evaluate-windows-server-2016).</span></span>
  <span data-ttu-id="89965-112">Du hittar instruktioner om hur du skapar en virtuell hård disk från en ISO-avbildning vid [skapande av startbara virtuella hård diskar](/previous-versions/windows/it-pro/windows-7/gg318049(v=ws.10)).</span><span class="sxs-lookup"><span data-stu-id="89965-112">You can find instructions on how to create a VHD from an ISO image at [Creating Bootable Virtual Hard Disks](/previous-versions/windows/it-pro/windows-7/gg318049(v=ws.10)).</span></span>
- <span data-ttu-id="89965-113">En värddator som har Hyper-V aktiverat.</span><span class="sxs-lookup"><span data-stu-id="89965-113">A host computer that has Hyper-V enabled.</span></span> <span data-ttu-id="89965-114">Mer information finns i [Översikt över Hyper-V](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831531(v=ws.11)).</span><span class="sxs-lookup"><span data-stu-id="89965-114">For information, see [Hyper-V overview](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831531(v=ws.11)).</span></span>

  <span data-ttu-id="89965-115">Genom att använda DSC kan du automatisera program varu installation och konfiguration för en dator vid första uppstarten.</span><span class="sxs-lookup"><span data-stu-id="89965-115">By using DSC, you can automate software installation and configuration for a computer at initial boot-up.</span></span> <span data-ttu-id="89965-116">Du gör detta genom att antingen mata in ett MOF-dokument eller en metaconfiguration till startbara media (till exempel en virtuell hård disk) så att de körs under den första start processen.</span><span class="sxs-lookup"><span data-stu-id="89965-116">You do this by either injecting a configuration MOF document or a metaconfiguration into bootable media (such as a VHD) so that they are run during the initial boot-up process.</span></span> <span data-ttu-id="89965-117">Det här beteendet anges i register nyckeln register [nyckeln dscautomationhostenabled registernyckel](DSCAutomationHostEnabled.md) under `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System` .</span><span class="sxs-lookup"><span data-stu-id="89965-117">This behavior is specified by the [DSCAutomationHostEnabled registry key](DSCAutomationHostEnabled.md) registry key under `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System`.</span></span>
  <span data-ttu-id="89965-118">Som standard är värdet för den här nyckeln 2, vilket tillåter DSC att köras vid start.</span><span class="sxs-lookup"><span data-stu-id="89965-118">By default, the value of this key is 2, which allows DSC to run at boot time.</span></span>

  <span data-ttu-id="89965-119">Om du inte vill att DSC ska köras vid start anger du värdet för register nyckeln [dscautomationhostenabled registernyckel register nyckel](DSCAutomationHostEnabled.md) till 0.</span><span class="sxs-lookup"><span data-stu-id="89965-119">If you do not want DSC to run at boot time, set the value of the [DSCAutomationHostEnabled registry key](DSCAutomationHostEnabled.md) registry key to 0.</span></span>

- <span data-ttu-id="89965-120">Mata in ett konfigurations-MOF-dokument till en virtuell hård disk</span><span class="sxs-lookup"><span data-stu-id="89965-120">Inject a configuration MOF document into a VHD</span></span>
- <span data-ttu-id="89965-121">Mata in en DSC-metaconfiguration i en virtuell hård disk</span><span class="sxs-lookup"><span data-stu-id="89965-121">Inject a DSC metaconfiguration into a VHD</span></span>
- <span data-ttu-id="89965-122">Inaktivera DSC vid start tid</span><span class="sxs-lookup"><span data-stu-id="89965-122">Disable DSC at boot time</span></span>

> [!NOTE]
> <span data-ttu-id="89965-123">Du kan mata in både `Pending.mof` och `MetaConfig.mof` i en dator på samma tidpunkt.</span><span class="sxs-lookup"><span data-stu-id="89965-123">You can inject both `Pending.mof` and `MetaConfig.mof` into a computer at the same time.</span></span>
> <span data-ttu-id="89965-124">Om båda filerna finns är inställningarna som anges i `MetaConfig.mof` prioritera.</span><span class="sxs-lookup"><span data-stu-id="89965-124">If both files are present, the settings specified in `MetaConfig.mof` take precedence.</span></span>

## <a name="inject-a-configuration-mof-document-into-a-vhd"></a><span data-ttu-id="89965-125">Mata in ett konfigurations-MOF-dokument till en virtuell hård disk</span><span class="sxs-lookup"><span data-stu-id="89965-125">Inject a configuration MOF document into a VHD</span></span>

<span data-ttu-id="89965-126">För att införa en konfiguration vid första uppstarten kan du mata in ett kompilerat MOF-dokument i den virtuella hård disken som dess `Pending.mof` fil.</span><span class="sxs-lookup"><span data-stu-id="89965-126">To enact a configuration at initial boot-up, you can inject a compiled configuration MOF document into the VHD as its `Pending.mof` file.</span></span> <span data-ttu-id="89965-127">Om register nyckeln **dscautomationhostenabled registernyckel** har angetts till 2 (standardvärdet) kommer DSC att tillämpa den konfiguration som definierats av `Pending.mof` när datorn startas för första gången.</span><span class="sxs-lookup"><span data-stu-id="89965-127">If the **DSCAutomationHostEnabled** registry key is set to 2 (the default value), DSC will apply the configuration defined by `Pending.mof` when the computer boots up for the first time.</span></span>

<span data-ttu-id="89965-128">I det här exemplet kommer vi att använda följande konfiguration, som kommer att installera IIS på den nya datorn:</span><span class="sxs-lookup"><span data-stu-id="89965-128">For this example, we will use the following configuration, which will install IIS on the new computer:</span></span>

```powershell
Configuration SampleIISInstall
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    node ('localhost')
    {
        WindowsFeature IIS
        {
            Ensure = 'Present'
            Name   = 'Web-Server'
        }
    }
}
```

### <a name="to-inject-the-configuration-mof-document-on-the-vhd"></a><span data-ttu-id="89965-129">Så här infogar du MOF-dokumentet för konfiguration på den virtuella hård disken</span><span class="sxs-lookup"><span data-stu-id="89965-129">To inject the configuration MOF document on the VHD</span></span>

1. <span data-ttu-id="89965-130">Montera den virtuella hård disken som du vill använda för att mata in konfigurationen genom att anropa cmdleten [Mount-VHD](/powershell/module/hyper-v/mount-vhd) .</span><span class="sxs-lookup"><span data-stu-id="89965-130">Mount the VHD into which you want to inject the configuration by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="89965-131">Exempel:</span><span class="sxs-lookup"><span data-stu-id="89965-131">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

1. <span data-ttu-id="89965-132">På en dator som kör PowerShell 5,0 eller senare sparar du konfigurationen ovan ( **SampleIISInstall** ) som en PowerShell-skript fil (. ps1).</span><span class="sxs-lookup"><span data-stu-id="89965-132">On a computer running PowerShell 5.0 or later, save the above configuration ( **SampleIISInstall** ) as a PowerShell script (.ps1) file.</span></span>

1. <span data-ttu-id="89965-133">I en PowerShell-konsol navigerar du till mappen där du sparade. ps1-filen.</span><span class="sxs-lookup"><span data-stu-id="89965-133">In a PowerShell console, navigate to the folder where you saved the .ps1 file.</span></span>

1. <span data-ttu-id="89965-134">Kör följande PowerShell-kommandon för att kompilera MOF-dokumentet (information om hur du kompilerar DSC-konfigurationer finns i [DSC-konfigurationer](../configurations/configurations.md):</span><span class="sxs-lookup"><span data-stu-id="89965-134">Run the following PowerShell commands to compile the MOF document (for information about compiling DSC configurations, see [DSC Configurations](../configurations/configurations.md):</span></span>

   ```powershell
   . .\SampleIISInstall.ps1
   SampleIISInstall
   ```

1. <span data-ttu-id="89965-135">Då skapas en `localhost.mof` fil i en ny mapp med namnet `SampleIISInstall` .</span><span class="sxs-lookup"><span data-stu-id="89965-135">This will create a `localhost.mof` file in a new folder named `SampleIISInstall`.</span></span> <span data-ttu-id="89965-136">Byt namn på och flytta filen till rätt plats på den virtuella hård disken med `Pending.mof` hjälp av cmdleten [Move-item](/powershell/module/microsoft.powershell.management/move-item) .</span><span class="sxs-lookup"><span data-stu-id="89965-136">Rename and move that file into the proper location on the VHD as `Pending.mof` by using the [Move-Item](/powershell/module/microsoft.powershell.management/move-item) cmdlet.</span></span> <span data-ttu-id="89965-137">Exempel:</span><span class="sxs-lookup"><span data-stu-id="89965-137">For example:</span></span>

   ```powershell
   Move-Item -Path C:\DSCTest\SampleIISInstall\localhost.mof -Destination E:\Windows\System32\Configuration\Pending.mof
   ```

1. <span data-ttu-id="89965-138">Demontera den virtuella hård disken genom att anropa cmdleten [demontera-VHD](/powershell/module/hyper-v/dismount-vhd) .</span><span class="sxs-lookup"><span data-stu-id="89965-138">Dismount the VHD by calling the [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet.</span></span>
   <span data-ttu-id="89965-139">Exempel:</span><span class="sxs-lookup"><span data-stu-id="89965-139">For example:</span></span>

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

1. <span data-ttu-id="89965-140">Skapa en virtuell dator med hjälp av den virtuella hård disk där du har installerat DSC MOF-dokumentet.</span><span class="sxs-lookup"><span data-stu-id="89965-140">Create a VM by using the VHD where you installed the DSC MOF document.</span></span>

<span data-ttu-id="89965-141">Efter den första starten och operativ system installationen installeras IIS.</span><span class="sxs-lookup"><span data-stu-id="89965-141">After initial boot-up and operating system installation, IIS will be installed.</span></span> <span data-ttu-id="89965-142">Du kan kontrol lera detta genom att anropa cmdleten [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) .</span><span class="sxs-lookup"><span data-stu-id="89965-142">You can verify this by calling the [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) cmdlet.</span></span>

## <a name="inject-a-dsc-metaconfiguration-into-a-vhd"></a><span data-ttu-id="89965-143">Mata in en DSC-metaconfiguration i en virtuell hård disk</span><span class="sxs-lookup"><span data-stu-id="89965-143">Inject a DSC metaconfiguration into a VHD</span></span>

<span data-ttu-id="89965-144">Du kan också konfigurera en dator för att hämta en konfiguration vid första uppstarten genom att mata in en metaconfiguration (mer information finns i [Konfigurera den lokala Configuration Manager (LCM)](../managing-nodes/metaConfig.md)) i den virtuella hård disken som dess `MetaConfig.mof` fil.</span><span class="sxs-lookup"><span data-stu-id="89965-144">You can also configure a computer to pull a configuration at initial boot-up by injecting a metaconfiguration (see [Configuring the Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md)) into the VHD as its `MetaConfig.mof` file.</span></span> <span data-ttu-id="89965-145">Om register nyckeln **dscautomationhostenabled registernyckel** har angetts till 2 (standardvärdet) kommer DSC att tillämpa metaconfiguration som definieras av `MetaConfig.mof` till LCM när datorn startas för första gången.</span><span class="sxs-lookup"><span data-stu-id="89965-145">If the **DSCAutomationHostEnabled** registry key is set to 2 (the default value), DSC will apply the metaconfiguration defined by `MetaConfig.mof` to the LCM when the computer boots up for the first time.</span></span> <span data-ttu-id="89965-146">Om metaconfiguration anger att LCM ska hämta konfigurationer från en pull-server kommer datorn att försöka hämta en konfiguration från den hämtnings servern vid första uppstarten.</span><span class="sxs-lookup"><span data-stu-id="89965-146">If the metaconfiguration specifies that the LCM should pull configurations from a pull server, the computer will attempt to pull a configuration from that pull server at initial boot-up.</span></span> <span data-ttu-id="89965-147">Information om hur du konfigurerar en DSC-pull-server finns i [Konfigurera en DSC-webb hämtnings Server](../pull-server/pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="89965-147">For information about setting up a DSC pull server, see [Setting up a DSC web pull server](../pull-server/pullServer.md).</span></span>

<span data-ttu-id="89965-148">I det här exemplet kommer vi att använda både konfigurationen som beskrivs i föregående avsnitt ( **SampleIISInstall** ) och följande metaconfiguration:</span><span class="sxs-lookup"><span data-stu-id="89965-148">For this example, we will use both the configuration described in the previous section ( **SampleIISInstall** ), and the following metaconfiguration:</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientBootstrap
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('SampleIISInstall')
        }
    }
}
```

### <a name="to-inject-the-metaconfiguration-mof-document-on-the-vhd"></a><span data-ttu-id="89965-149">För att mata in MOF-dokumentet metaconfiguration på den virtuella hård disken</span><span class="sxs-lookup"><span data-stu-id="89965-149">To inject the metaconfiguration MOF document on the VHD</span></span>

1. <span data-ttu-id="89965-150">Montera den virtuella hård disken där du vill mata in metaconfiguration genom att anropa cmdleten [Mount-VHD](/powershell/module/hyper-v/mount-vhd) .</span><span class="sxs-lookup"><span data-stu-id="89965-150">Mount the VHD into which you want to inject the metaconfiguration by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="89965-151">Exempel:</span><span class="sxs-lookup"><span data-stu-id="89965-151">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

1. <span data-ttu-id="89965-152">[Konfigurera en DSC-webb hämtnings Server](../pull-server/pullServer.md)och spara **SampleIISInstall** -konfigurationen till lämplig mapp.</span><span class="sxs-lookup"><span data-stu-id="89965-152">[Set up a DSC web pull server](../pull-server/pullServer.md), and save the **SampleIISInstall** configuration to the appropriate folder.</span></span>

1. <span data-ttu-id="89965-153">På en dator som kör PowerShell 5,0 eller senare sparar du ovanstående metaconfiguration ( **PullClientBootstrap** ) som en PowerShell-skript fil (. ps1).</span><span class="sxs-lookup"><span data-stu-id="89965-153">On a computer running PowerShell 5.0 or later, save the above metaconfiguration ( **PullClientBootstrap** ) as a PowerShell script (.ps1) file.</span></span>

1. <span data-ttu-id="89965-154">I en PowerShell-konsol navigerar du till mappen där du sparade. ps1-filen.</span><span class="sxs-lookup"><span data-stu-id="89965-154">In a PowerShell console, navigate to the folder where you saved the .ps1 file.</span></span>

1. <span data-ttu-id="89965-155">Kör följande PowerShell-kommandon för att kompilera MOF-dokumentet för metaconfiguration (information om hur du kompilerar DSC-konfigurationer finns i [DSC-konfigurationer](../configurations/configurations.md):</span><span class="sxs-lookup"><span data-stu-id="89965-155">Run the following PowerShell commands to compile the metaconfiguration MOF document (for information about compiling DSC configurations, see [DSC Configurations](../configurations/configurations.md):</span></span>

   ```powershell
   . .\PullClientBootstrap.ps1
   PullClientBootstrap
   ```

1. <span data-ttu-id="89965-156">Då skapas en `localhost.meta.mof` fil i en ny mapp med namnet `PullClientBootstrap` .</span><span class="sxs-lookup"><span data-stu-id="89965-156">This will create a `localhost.meta.mof` file in a new folder named `PullClientBootstrap`.</span></span> <span data-ttu-id="89965-157">Byt namn på och flytta filen till rätt plats på den virtuella hård disken med `MetaConfig.mof` hjälp av cmdleten [Move-item](/powershell/module/microsoft.powershell.management/move-item) .</span><span class="sxs-lookup"><span data-stu-id="89965-157">Rename and move that file into the proper location on the VHD as `MetaConfig.mof` by using the [Move-Item](/powershell/module/microsoft.powershell.management/move-item) cmdlet.</span></span>

   ```powershell
   Move-Item -Path C:\DSCTest\PullClientBootstrap\localhost.meta.mof -Destination E:\Windows\System32\Configuration\MetaConfig.mof
   ```

1. <span data-ttu-id="89965-158">Demontera den virtuella hård disken genom att anropa cmdleten [demontera-VHD](/powershell/module/hyper-v/dismount-vhd) .</span><span class="sxs-lookup"><span data-stu-id="89965-158">Dismount the VHD by calling the [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet.</span></span>
   <span data-ttu-id="89965-159">Exempel:</span><span class="sxs-lookup"><span data-stu-id="89965-159">For example:</span></span>

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

1. <span data-ttu-id="89965-160">Skapa en virtuell dator med hjälp av den virtuella hård disk där du har installerat DSC MOF-dokumentet.</span><span class="sxs-lookup"><span data-stu-id="89965-160">Create a VM by using the VHD where you installed the DSC MOF document.</span></span>

<span data-ttu-id="89965-161">Efter den första starten och operativ system installationen kommer DSC att hämta konfigurationen från hämtnings servern och IIS installeras.</span><span class="sxs-lookup"><span data-stu-id="89965-161">After initial boot-up and operating system installation, DSC will pull the configuration from the pull server, and IIS will be installed.</span></span> <span data-ttu-id="89965-162">Du kan kontrol lera detta genom att anropa cmdleten [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) .</span><span class="sxs-lookup"><span data-stu-id="89965-162">You can verify this by calling the [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) cmdlet.</span></span>

## <a name="disable-dsc-at-boot-time"></a><span data-ttu-id="89965-163">Inaktivera DSC vid start tid</span><span class="sxs-lookup"><span data-stu-id="89965-163">Disable DSC at boot time</span></span>

<span data-ttu-id="89965-164">Som standard är värdet för `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\DSCAutomationHostEnabled`</span><span class="sxs-lookup"><span data-stu-id="89965-164">By default, the value of the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\DSCAutomationHostEnabled`</span></span>
<span data-ttu-id="89965-165">nyckeln har angetts till 2, vilket gör att en DSC-konfiguration kan köras om datorn är i vänte läge eller nuvarande tillstånd.</span><span class="sxs-lookup"><span data-stu-id="89965-165">key is set to 2, which allows a DSC configuration to run if the computer is in pending or current state.</span></span> <span data-ttu-id="89965-166">Om du inte vill att en konfiguration ska köras vid första uppstarten måste du ange värdet för den här nyckeln till 0:</span><span class="sxs-lookup"><span data-stu-id="89965-166">If you do not want a configuration to run at initial boot-up, you need so set the value of this key to 0:</span></span>

1. <span data-ttu-id="89965-167">Montera den virtuella hård disken genom att anropa cmdleten [Mount-VHD](/powershell/module/hyper-v/mount-vhd) .</span><span class="sxs-lookup"><span data-stu-id="89965-167">Mount the VHD by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="89965-168">Exempel:</span><span class="sxs-lookup"><span data-stu-id="89965-168">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

1. <span data-ttu-id="89965-169">Läs in register `HKLM\Software` under nyckeln från den virtuella hård disken genom att anropa `reg load` .</span><span class="sxs-lookup"><span data-stu-id="89965-169">Load the registry `HKLM\Software` subkey from the VHD by calling `reg load`.</span></span>

   ```powershell
   reg load HKLM\Vhd E:\Windows\System32\Config\Software`
   ```

1. <span data-ttu-id="89965-170">Navigera till `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System` med hjälp av PowerShell-huvudprovidern.</span><span class="sxs-lookup"><span data-stu-id="89965-170">Navigate to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System` by using the PowerShell Registry provider.</span></span>

   ```powershell
   Set-Location HKLM:\Software\Microsoft\Windows\CurrentVersion\Policies\System`
   ```

1. <span data-ttu-id="89965-171">Ändra värdet `DSCAutomationHostEnabled` till 0.</span><span class="sxs-lookup"><span data-stu-id="89965-171">Change the value of `DSCAutomationHostEnabled` to 0.</span></span>

   ```powershell
   Set-ItemProperty -Path . -Name DSCAutomationHostEnabled -Value 0
   ```

5. <span data-ttu-id="89965-172">Ta bort registret genom att köra följande kommandon:</span><span class="sxs-lookup"><span data-stu-id="89965-172">Unload the registry by running the following commands:</span></span>

   ```powershell
   [gc]::Collect()
   reg unload HKLM\Vhd
   ```

## <a name="see-also"></a><span data-ttu-id="89965-173">Se även</span><span class="sxs-lookup"><span data-stu-id="89965-173">See Also</span></span>

[<span data-ttu-id="89965-174">DSC-konfigurationer</span><span class="sxs-lookup"><span data-stu-id="89965-174">DSC Configurations</span></span>](../configurations/configurations.md)

[<span data-ttu-id="89965-175">DSCAutomationHostEnabled-registernyckel</span><span class="sxs-lookup"><span data-stu-id="89965-175">DSCAutomationHostEnabled registry key</span></span>](DSCAutomationHostEnabled.md)

[<span data-ttu-id="89965-176">Konfigurera den lokala konfigurationshanteraren (LCM)</span><span class="sxs-lookup"><span data-stu-id="89965-176">Configuring the Local Configuration Manager (LCM)</span></span>](../managing-nodes/metaConfig.md)

[<span data-ttu-id="89965-177">Konfigurera en DSC-webb hämtnings Server</span><span class="sxs-lookup"><span data-stu-id="89965-177">Setting up a DSC web pull server</span></span>](../pull-server/pullServer.md)
