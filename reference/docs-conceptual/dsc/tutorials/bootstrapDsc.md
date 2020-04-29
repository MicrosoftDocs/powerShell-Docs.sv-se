---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Konfigurera en virtuell dator vid första uppstart med hjälp av DSC
ms.openlocfilehash: f9634c330832e23fb2c6f08c5b299b55a5505ac9
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71942407"
---
# <a name="configure-a-virtual-machines-at-initial-boot-up-by-using-dsc"></a><span data-ttu-id="c3406-103">Konfigurera en virtuell dator vid första uppstart med hjälp av DSC</span><span class="sxs-lookup"><span data-stu-id="c3406-103">Configure a virtual machines at initial boot-up by using DSC</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c3406-104">Gäller för: Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="c3406-104">Applies To: Windows PowerShell 5.0</span></span>

## <a name="requirements"></a><span data-ttu-id="c3406-105">Krav</span><span class="sxs-lookup"><span data-stu-id="c3406-105">Requirements</span></span>

> [!NOTE]
> <span data-ttu-id="c3406-106">Register nyckeln **dscautomationhostenabled registernyckel** som beskrivs i det här avsnittet är inte tillgänglig i PowerShell 4,0.</span><span class="sxs-lookup"><span data-stu-id="c3406-106">The **DSCAutomationHostEnabled** registry key described in this topic is not available in PowerShell 4.0.</span></span>
> <span data-ttu-id="c3406-107">Information om hur du konfigurerar nya virtuella datorer vid första uppstart i PowerShell 4,0 finns i [vill konfigurera dina datorer automatiskt med DSC vid första uppstarten?](https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)</span><span class="sxs-lookup"><span data-stu-id="c3406-107">For information on how to configure new virtual machines at initial boot-up in PowerShell 4.0, see [Want to Automatically Configure Your Machines Using DSC at Initial Boot-up?](https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)</span></span>

<span data-ttu-id="c3406-108">Om du vill köra de här exemplen behöver du:</span><span class="sxs-lookup"><span data-stu-id="c3406-108">To run these examples, you will need:</span></span>

- <span data-ttu-id="c3406-109">En startbar virtuell hård disk att arbeta med.</span><span class="sxs-lookup"><span data-stu-id="c3406-109">A bootable VHD to work with.</span></span> <span data-ttu-id="c3406-110">Du kan ladda ned en ISO-fil med en utvärderings version av Windows Server 2016 på [TechNet Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span><span class="sxs-lookup"><span data-stu-id="c3406-110">You can download an ISO with an evaluation copy of Windows Server 2016 at [TechNet Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span></span>
  <span data-ttu-id="c3406-111">Du hittar instruktioner om hur du skapar en virtuell hård disk från en ISO-avbildning vid [skapande av startbara virtuella hård diskar](/previous-versions/windows/it-pro/windows-7/gg318049(v=ws.10)).</span><span class="sxs-lookup"><span data-stu-id="c3406-111">You can find instructions on how to create a VHD from an ISO image at [Creating Bootable Virtual Hard Disks](/previous-versions/windows/it-pro/windows-7/gg318049(v=ws.10)).</span></span>
- <span data-ttu-id="c3406-112">En värddator som har Hyper-V aktiverat.</span><span class="sxs-lookup"><span data-stu-id="c3406-112">A host computer that has Hyper-V enabled.</span></span> <span data-ttu-id="c3406-113">Mer information finns i [Översikt över Hyper-V](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831531(v=ws.11)).</span><span class="sxs-lookup"><span data-stu-id="c3406-113">For information, see [Hyper-V overview](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831531(v=ws.11)).</span></span>

  <span data-ttu-id="c3406-114">Genom att använda DSC kan du automatisera program varu installation och konfiguration för en dator vid första uppstarten.</span><span class="sxs-lookup"><span data-stu-id="c3406-114">By using DSC, you can automate software installation and configuration for a computer at initial boot-up.</span></span>
  <span data-ttu-id="c3406-115">Du gör detta genom att antingen mata in ett MOF-dokument eller en metaconfiguration till startbara media (till exempel en virtuell hård disk) så att de körs under den första start processen.</span><span class="sxs-lookup"><span data-stu-id="c3406-115">You do this by either injecting a configuration MOF document or a metaconfiguration into bootable media (such as a VHD) so that they are run during the initial boot-up process.</span></span>
  <span data-ttu-id="c3406-116">Det här beteendet anges i register nyckeln register [nyckeln dscautomationhostenabled registernyckel](DSCAutomationHostEnabled.md) under `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System`.</span><span class="sxs-lookup"><span data-stu-id="c3406-116">This behavior is specified by the [DSCAutomationHostEnabled registry key](DSCAutomationHostEnabled.md) registry key under `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System`.</span></span>
  <span data-ttu-id="c3406-117">Som standard är värdet för den här nyckeln 2, vilket tillåter DSC att köras vid start.</span><span class="sxs-lookup"><span data-stu-id="c3406-117">By default, the value of this key is 2, which allows DSC to run at boot time.</span></span>

  <span data-ttu-id="c3406-118">Om du inte vill att DSC ska köras vid start anger du värdet för register nyckeln [dscautomationhostenabled registernyckel register nyckel](DSCAutomationHostEnabled.md) till 0.</span><span class="sxs-lookup"><span data-stu-id="c3406-118">If you do not want DSC to run at boot time, set the value of the [DSCAutomationHostEnabled registry key](DSCAutomationHostEnabled.md) registry key to 0.</span></span>

- <span data-ttu-id="c3406-119">Mata in ett konfigurations-MOF-dokument till en virtuell hård disk</span><span class="sxs-lookup"><span data-stu-id="c3406-119">Inject a configuration MOF document into a VHD</span></span>
- <span data-ttu-id="c3406-120">Mata in en DSC-metaconfiguration i en virtuell hård disk</span><span class="sxs-lookup"><span data-stu-id="c3406-120">Inject a DSC metaconfiguration into a VHD</span></span>
- <span data-ttu-id="c3406-121">Inaktivera DSC vid start tid</span><span class="sxs-lookup"><span data-stu-id="c3406-121">Disable DSC at boot time</span></span>

> [!NOTE]
> <span data-ttu-id="c3406-122">Du kan mata in `Pending.mof` både `MetaConfig.mof` och i en dator på samma tidpunkt.</span><span class="sxs-lookup"><span data-stu-id="c3406-122">You can inject both `Pending.mof` and `MetaConfig.mof` into a computer at the same time.</span></span>
> <span data-ttu-id="c3406-123">Om båda filerna finns är inställningarna som anges i `MetaConfig.mof` prioritera.</span><span class="sxs-lookup"><span data-stu-id="c3406-123">If both files are present, the settings specified in `MetaConfig.mof` take precedence.</span></span>

## <a name="inject-a-configuration-mof-document-into-a-vhd"></a><span data-ttu-id="c3406-124">Mata in ett konfigurations-MOF-dokument till en virtuell hård disk</span><span class="sxs-lookup"><span data-stu-id="c3406-124">Inject a configuration MOF document into a VHD</span></span>

<span data-ttu-id="c3406-125">För att införa en konfiguration vid första uppstarten kan du mata in ett kompilerat MOF-dokument i den virtuella `Pending.mof` hård disken som dess fil.</span><span class="sxs-lookup"><span data-stu-id="c3406-125">To enact a configuration at initial boot-up, you can inject a compiled configuration MOF document into the VHD as its `Pending.mof` file.</span></span>
<span data-ttu-id="c3406-126">Om register nyckeln **dscautomationhostenabled registernyckel** har angetts till 2 (standardvärdet) kommer DSC att tillämpa den konfiguration som definierats `Pending.mof` av när datorn startas för första gången.</span><span class="sxs-lookup"><span data-stu-id="c3406-126">If the **DSCAutomationHostEnabled** registry key is set to 2 (the default value), DSC will apply the configuration defined by `Pending.mof` when the computer boots up for the first time.</span></span>

<span data-ttu-id="c3406-127">I det här exemplet kommer vi att använda följande konfiguration, som kommer att installera IIS på den nya datorn:</span><span class="sxs-lookup"><span data-stu-id="c3406-127">For this example, we will use the following configuration, which will install IIS on the new computer:</span></span>

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

### <a name="to-inject-the-configuration-mof-document-on-the-vhd"></a><span data-ttu-id="c3406-128">Så här infogar du MOF-dokumentet för konfiguration på den virtuella hård disken</span><span class="sxs-lookup"><span data-stu-id="c3406-128">To inject the configuration MOF document on the VHD</span></span>

1. <span data-ttu-id="c3406-129">Montera den virtuella hård disken som du vill använda för att mata in konfigurationen genom att anropa cmdleten [Mount-VHD](/powershell/module/hyper-v/mount-vhd) .</span><span class="sxs-lookup"><span data-stu-id="c3406-129">Mount the VHD into which you want to inject the configuration by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="c3406-130">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="c3406-130">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. <span data-ttu-id="c3406-131">På en dator som kör PowerShell 5,0 eller senare sparar du konfigurationen ovan (**SampleIISInstall**) som en PowerShell-skript fil (. ps1).</span><span class="sxs-lookup"><span data-stu-id="c3406-131">On a computer running PowerShell 5.0 or later, save the above configuration (**SampleIISInstall**) as a PowerShell script (.ps1) file.</span></span>

3. <span data-ttu-id="c3406-132">I en PowerShell-konsol navigerar du till mappen där du sparade. ps1-filen.</span><span class="sxs-lookup"><span data-stu-id="c3406-132">In a PowerShell console, navigate to the folder where you saved the .ps1 file.</span></span>

4. <span data-ttu-id="c3406-133">Kör följande PowerShell-kommandon för att kompilera MOF-dokumentet (information om hur du kompilerar DSC-konfigurationer finns i [DSC-konfigurationer](../configurations/configurations.md):</span><span class="sxs-lookup"><span data-stu-id="c3406-133">Run the following PowerShell commands to compile the MOF document (for information about compiling DSC configurations, see [DSC Configurations](../configurations/configurations.md):</span></span>

   ```powershell
   . .\SampleIISInstall.ps1
   SampleIISInstall
   ```

5. <span data-ttu-id="c3406-134">Då skapas en `localhost.mof` fil i en ny mapp med namnet `SampleIISInstall`.</span><span class="sxs-lookup"><span data-stu-id="c3406-134">This will create a `localhost.mof` file in a new folder named `SampleIISInstall`.</span></span>
   <span data-ttu-id="c3406-135">Byt namn på och flytta filen till rätt plats på den virtuella hård `Pending.mof` disken med hjälp av cmdleten [Move-item](/powershell/module/microsoft.powershell.management/move-item) .</span><span class="sxs-lookup"><span data-stu-id="c3406-135">Rename and move that file into the proper location on the VHD as `Pending.mof` by using the [Move-Item](/powershell/module/microsoft.powershell.management/move-item) cmdlet.</span></span> <span data-ttu-id="c3406-136">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="c3406-136">For example:</span></span>

   ```powershell
       Move-Item -Path C:\DSCTest\SampleIISInstall\localhost.mof -Destination E:\Windows\System32\Configuration\Pending.mof
   ```

6. <span data-ttu-id="c3406-137">Demontera den virtuella hård disken genom att anropa cmdleten [demontera-VHD](/powershell/module/hyper-v/dismount-vhd) .</span><span class="sxs-lookup"><span data-stu-id="c3406-137">Dismount the VHD by calling the [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet.</span></span> <span data-ttu-id="c3406-138">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="c3406-138">For example:</span></span>

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

7. <span data-ttu-id="c3406-139">Skapa en virtuell dator med hjälp av den virtuella hård disk där du har installerat DSC MOF-dokumentet.</span><span class="sxs-lookup"><span data-stu-id="c3406-139">Create a VM by using the VHD where you installed the DSC MOF document.</span></span>

<span data-ttu-id="c3406-140">Efter den första starten och operativ system installationen installeras IIS.</span><span class="sxs-lookup"><span data-stu-id="c3406-140">After initial boot-up and operating system installation, IIS will be installed.</span></span>
<span data-ttu-id="c3406-141">Du kan kontrol lera detta genom att anropa cmdleten [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) .</span><span class="sxs-lookup"><span data-stu-id="c3406-141">You can verify this by calling the [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) cmdlet.</span></span>

## <a name="inject-a-dsc-metaconfiguration-into-a-vhd"></a><span data-ttu-id="c3406-142">Mata in en DSC-metaconfiguration i en virtuell hård disk</span><span class="sxs-lookup"><span data-stu-id="c3406-142">Inject a DSC metaconfiguration into a VHD</span></span>

<span data-ttu-id="c3406-143">Du kan också konfigurera en dator för att hämta en konfiguration vid första uppstarten genom att mata in en metaconfiguration (mer information finns i [Konfigurera den lokala Configuration Manager (LCM)](../managing-nodes/metaConfig.md)) `MetaConfig.mof` i den virtuella hård disken som dess fil.</span><span class="sxs-lookup"><span data-stu-id="c3406-143">You can also configure a computer to pull a configuration at initial boot-up by injecting a metaconfiguration (see [Configuring the Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md)) into the VHD as its `MetaConfig.mof` file.</span></span>
<span data-ttu-id="c3406-144">Om register nyckeln **dscautomationhostenabled registernyckel** har angetts till 2 (standardvärdet) kommer DSC att tillämpa metaconfiguration som definieras av `MetaConfig.mof` till LCM när datorn startas för första gången.</span><span class="sxs-lookup"><span data-stu-id="c3406-144">If the **DSCAutomationHostEnabled** registry key is set to 2 (the default value),  DSC will apply the metaconfiguration defined by `MetaConfig.mof` to the LCM when the computer boots up for the first time.</span></span>
<span data-ttu-id="c3406-145">Om metaconfiguration anger att LCM ska hämta konfigurationer från en pull-server kommer datorn att försöka hämta en konfiguration från den hämtnings servern vid första uppstarten.</span><span class="sxs-lookup"><span data-stu-id="c3406-145">If the metaconfiguration specifies that the LCM should pull configurations from a pull server, the computer will attempt to pull a configuration from that pull server at initial boot-up.</span></span>
<span data-ttu-id="c3406-146">Information om hur du konfigurerar en DSC-pull-server finns i [Konfigurera en DSC-webb hämtnings Server](../pull-server/pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="c3406-146">For information about setting up a DSC pull server, see [Setting up a DSC web pull server](../pull-server/pullServer.md).</span></span>

<span data-ttu-id="c3406-147">I det här exemplet kommer vi att använda både konfigurationen som beskrivs i föregående avsnitt (**SampleIISInstall**) och följande metaconfiguration:</span><span class="sxs-lookup"><span data-stu-id="c3406-147">For this example, we will use both the configuration described in the previous section (**SampleIISInstall**), and the following metaconfiguration:</span></span>

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

### <a name="to-inject-the-metaconfiguration-mof-document-on-the-vhd"></a><span data-ttu-id="c3406-148">För att mata in MOF-dokumentet metaconfiguration på den virtuella hård disken</span><span class="sxs-lookup"><span data-stu-id="c3406-148">To inject the metaconfiguration MOF document on the VHD</span></span>

1. <span data-ttu-id="c3406-149">Montera den virtuella hård disken där du vill mata in metaconfiguration genom att anropa cmdleten [Mount-VHD](/powershell/module/hyper-v/mount-vhd) .</span><span class="sxs-lookup"><span data-stu-id="c3406-149">Mount the VHD into which you want to inject the metaconfiguration by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="c3406-150">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="c3406-150">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. <span data-ttu-id="c3406-151">[Konfigurera en DSC-webb hämtnings Server](../pull-server/pullServer.md)och spara **SampleIISInstall** -konfigurationen till lämplig mapp.</span><span class="sxs-lookup"><span data-stu-id="c3406-151">[Set up a DSC web pull server](../pull-server/pullServer.md), and save the **SampleIISInstall** configuration to the appropriate folder.</span></span>

3. <span data-ttu-id="c3406-152">På en dator som kör PowerShell 5,0 eller senare sparar du ovanstående metaconfiguration (**PullClientBootstrap**) som en PowerShell-skript fil (. ps1).</span><span class="sxs-lookup"><span data-stu-id="c3406-152">On a computer running PowerShell 5.0 or later, save the above metaconfiguration (**PullClientBootstrap**) as a PowerShell script (.ps1) file.</span></span>

4. <span data-ttu-id="c3406-153">I en PowerShell-konsol navigerar du till mappen där du sparade. ps1-filen.</span><span class="sxs-lookup"><span data-stu-id="c3406-153">In a PowerShell console, navigate to the folder where you saved the .ps1 file.</span></span>

5. <span data-ttu-id="c3406-154">Kör följande PowerShell-kommandon för att kompilera MOF-dokumentet för metaconfiguration (information om hur du kompilerar DSC-konfigurationer finns i [DSC-konfigurationer](../configurations/configurations.md):</span><span class="sxs-lookup"><span data-stu-id="c3406-154">Run the following PowerShell commands to compile the  metaconfiguration MOF document (for information about compiling DSC configurations, see [DSC Configurations](../configurations/configurations.md):</span></span>

   ```powershell
   . .\PullClientBootstrap.ps1
   PullClientBootstrap
   ```

6. <span data-ttu-id="c3406-155">Då skapas en `localhost.meta.mof` fil i en ny mapp med namnet `PullClientBootstrap`.</span><span class="sxs-lookup"><span data-stu-id="c3406-155">This will create a `localhost.meta.mof` file in a new folder named `PullClientBootstrap`.</span></span>
   <span data-ttu-id="c3406-156">Byt namn på och flytta filen till rätt plats på den virtuella hård `MetaConfig.mof` disken med hjälp av cmdleten [Move-item](/powershell/module/microsoft.powershell.management/move-item) .</span><span class="sxs-lookup"><span data-stu-id="c3406-156">Rename and move that file into the proper location on the VHD as `MetaConfig.mof` by using the [Move-Item](/powershell/module/microsoft.powershell.management/move-item) cmdlet.</span></span>

   ```powershell
   Move-Item -Path C:\DSCTest\PullClientBootstrap\localhost.meta.mof -Destination E:\Windows\System32\Configuration\MetaConfig.mof
   ```

7. <span data-ttu-id="c3406-157">Demontera den virtuella hård disken genom att anropa cmdleten [demontera-VHD](/powershell/module/hyper-v/dismount-vhd) .</span><span class="sxs-lookup"><span data-stu-id="c3406-157">Dismount the VHD by calling the [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet.</span></span> <span data-ttu-id="c3406-158">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="c3406-158">For example:</span></span>

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

8. <span data-ttu-id="c3406-159">Skapa en virtuell dator med hjälp av den virtuella hård disk där du har installerat DSC MOF-dokumentet.</span><span class="sxs-lookup"><span data-stu-id="c3406-159">Create a VM by using the VHD where you installed the DSC MOF document.</span></span>

<span data-ttu-id="c3406-160">Efter den första starten och operativ system installationen kommer DSC att hämta konfigurationen från hämtnings servern och IIS installeras.</span><span class="sxs-lookup"><span data-stu-id="c3406-160">After initial boot-up and operating system installation, DSC will pull the configuration from the pull server, and IIS will be installed.</span></span>
<span data-ttu-id="c3406-161">Du kan kontrol lera detta genom att anropa cmdleten [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) .</span><span class="sxs-lookup"><span data-stu-id="c3406-161">You can verify this by calling the [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) cmdlet.</span></span>

## <a name="disable-dsc-at-boot-time"></a><span data-ttu-id="c3406-162">Inaktivera DSC vid start tid</span><span class="sxs-lookup"><span data-stu-id="c3406-162">Disable DSC at boot time</span></span>

<span data-ttu-id="c3406-163">Som standard är värdet för `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\DSCAutomationHostEnabled` nyckeln inställt på 2, vilket gör att en DSC-konfiguration kan köras om datorn är i vänte läge eller nuvarande tillstånd.</span><span class="sxs-lookup"><span data-stu-id="c3406-163">By default, the value of the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\DSCAutomationHostEnabled` key is set to 2, which allows a DSC configuration to run if the computer is in pending or current state.</span></span> <span data-ttu-id="c3406-164">Om du inte vill att en konfiguration ska köras vid första uppstarten måste du ange värdet för den här nyckeln till 0:</span><span class="sxs-lookup"><span data-stu-id="c3406-164">If you do not want a configuration to run at initial boot-up, you need so set the value of this key to 0:</span></span>

1. <span data-ttu-id="c3406-165">Montera den virtuella hård disken genom att anropa cmdleten [Mount-VHD](/powershell/module/hyper-v/mount-vhd) .</span><span class="sxs-lookup"><span data-stu-id="c3406-165">Mount the VHD by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="c3406-166">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="c3406-166">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. <span data-ttu-id="c3406-167">Läs in register `HKLM\Software` under nyckeln från den virtuella hård `reg load`disken genom att anropa.</span><span class="sxs-lookup"><span data-stu-id="c3406-167">Load the registry `HKLM\Software` subkey from the VHD by calling `reg load`.</span></span>

   ```powershell
   reg load HKLM\Vhd E:\Windows\System32\Config\Software`
   ```

3. <span data-ttu-id="c3406-168">Navigera till `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System` med hjälp av PowerShell-huvudprovidern.</span><span class="sxs-lookup"><span data-stu-id="c3406-168">Navigate to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System` by using the PowerShell Registry provider.</span></span>

   ```powershell
   Set-Location HKLM:\Software\Microsoft\Windows\CurrentVersion\Policies\System`
   ```

4. <span data-ttu-id="c3406-169">Ändra värdet `DSCAutomationHostEnabled` till 0.</span><span class="sxs-lookup"><span data-stu-id="c3406-169">Change the value of `DSCAutomationHostEnabled` to 0.</span></span>

   ```powershell
   Set-ItemProperty -Path . -Name DSCAutomationHostEnabled -Value 0
   ```

5. <span data-ttu-id="c3406-170">Ta bort registret genom att köra följande kommandon:</span><span class="sxs-lookup"><span data-stu-id="c3406-170">Unload the registry by running the following commands:</span></span>

   ```powershell
   [gc]::Collect()
   reg unload HKLM\Vhd
   ```

## <a name="see-also"></a><span data-ttu-id="c3406-171">Se även</span><span class="sxs-lookup"><span data-stu-id="c3406-171">See Also</span></span>

[<span data-ttu-id="c3406-172">DSC-konfigurationer</span><span class="sxs-lookup"><span data-stu-id="c3406-172">DSC Configurations</span></span>](../configurations/configurations.md)

[<span data-ttu-id="c3406-173">DSCAutomationHostEnabled-registernyckel</span><span class="sxs-lookup"><span data-stu-id="c3406-173">DSCAutomationHostEnabled registry key</span></span>](DSCAutomationHostEnabled.md)

[<span data-ttu-id="c3406-174">Konfigurera den lokala konfigurationshanteraren (LCM)</span><span class="sxs-lookup"><span data-stu-id="c3406-174">Configuring the Local Configuration Manager (LCM)</span></span>](../managing-nodes/metaConfig.md)

[<span data-ttu-id="c3406-175">Konfigurera en DSC-webb hämtnings Server</span><span class="sxs-lookup"><span data-stu-id="c3406-175">Setting up a DSC web pull server</span></span>](../pull-server/pullServer.md)
