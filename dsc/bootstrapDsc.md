---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Konfigurera en virtuell dator vid första uppstart med hjälp av DSC
ms.openlocfilehash: 2f228a38379d1e65b31c03594e876f7226474fc3
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893360"
---
# <a name="configure-a-virtual-machines-at-initial-boot-up-by-using-dsc"></a><span data-ttu-id="f1add-103">Konfigurera en virtuell dator vid första uppstart med hjälp av DSC</span><span class="sxs-lookup"><span data-stu-id="f1add-103">Configure a virtual machines at initial boot-up by using DSC</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f1add-104">Gäller för: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="f1add-104">Applies To: Windows PowerShell 5.0</span></span>

## <a name="requirements"></a><span data-ttu-id="f1add-105">Krav</span><span class="sxs-lookup"><span data-stu-id="f1add-105">Requirements</span></span>

> [!NOTE] 
> <span data-ttu-id="f1add-106">Den **DSCAutomationHostEnabled** registernyckel som beskrivs i det här avsnittet är inte tillgänglig i PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="f1add-106">The **DSCAutomationHostEnabled** registry key described in this topic is not available in PowerShell 4.0.</span></span>
> <span data-ttu-id="f1add-107">Information om hur du konfigurerar nya virtuella datorer vid första uppstart i PowerShell 4.0 finns i [vill du automatiskt konfigurera dina datorer med hjälp av DSC vid första uppstart?] > ()https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)</span><span class="sxs-lookup"><span data-stu-id="f1add-107">For information on how to configure new virtual machines at initial boot-up in PowerShell 4.0, see [Want to Automatically Configure Your Machines Using DSC at Initial Boot-up?]> (https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)</span></span>

<span data-ttu-id="f1add-108">För att köra exemplen, behöver du:</span><span class="sxs-lookup"><span data-stu-id="f1add-108">To run these examples, you will need:</span></span>

- <span data-ttu-id="f1add-109">En startbar virtuell Hårddisk att arbeta med.</span><span class="sxs-lookup"><span data-stu-id="f1add-109">A bootable VHD to work with.</span></span> <span data-ttu-id="f1add-110">Du kan hämta en ISO med ett utvärderingsexemplar av Windows Server 2016 på [TechNet Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span><span class="sxs-lookup"><span data-stu-id="f1add-110">You can download an ISO with an evaluation copy of Windows Server 2016 at [TechNet Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span></span> <span data-ttu-id="f1add-111">Du hittar anvisningar om hur du skapar en virtuell Hårddisk från en ISO-avbildning på [skapa startbara virtuella hårddiskar](/previous-versions/windows/it-pro/windows-7/gg318049(v=ws.10)).</span><span class="sxs-lookup"><span data-stu-id="f1add-111">You can find instructions on how to create a VHD from an ISO image at [Creating Bootable Virtual Hard Disks](/previous-versions/windows/it-pro/windows-7/gg318049(v=ws.10)).</span></span>
- <span data-ttu-id="f1add-112">En värddator som har Hyper-V aktiverat.</span><span class="sxs-lookup"><span data-stu-id="f1add-112">A host computer that has Hyper-V enabled.</span></span> <span data-ttu-id="f1add-113">Mer information finns i [översikt över Hyper-V](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831531(v=ws.11)).</span><span class="sxs-lookup"><span data-stu-id="f1add-113">For information, see [Hyper-V overview](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831531(v=ws.11)).</span></span>

  <span data-ttu-id="f1add-114">Du kan automatisera installationen och konfigurationen för en dator vid första uppstart med hjälp av DSC.</span><span class="sxs-lookup"><span data-stu-id="f1add-114">By using DSC, you can automate software installation and configuration for a computer at initial boot-up.</span></span>
  <span data-ttu-id="f1add-115">Du kan göra detta genom att antingen infogar ett konfiguration MOF-dokument eller en metaconfiguration i startbara media (till exempel en virtuell Hårddisk) så att de körs under den ursprungliga startprocessen.</span><span class="sxs-lookup"><span data-stu-id="f1add-115">You do this by either injecting a configuration MOF document or a metaconfiguration into bootable media (such as a VHD) so that they are run during the initial boot-up process.</span></span>
  <span data-ttu-id="f1add-116">Det här beteendet anges av den [DSCAutomationHostEnabled-registernyckel](DSCAutomationHostEnabled.md) registernyckel under `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies`.</span><span class="sxs-lookup"><span data-stu-id="f1add-116">This behavior is specified by the [DSCAutomationHostEnabled registry key](DSCAutomationHostEnabled.md) registry key under `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies`.</span></span>
  <span data-ttu-id="f1add-117">Som standard är värdet för den här nyckeln 2, vilket gör att DSC ska köras när datorn startas.</span><span class="sxs-lookup"><span data-stu-id="f1add-117">By default, the value of this key is 2, which allows DSC to run at boot time.</span></span>

  <span data-ttu-id="f1add-118">Om du inte vill att DSC ska köras när datorn startas, ange värdet för den [DSCAutomationHostEnabled-registernyckel](DSCAutomationHostEnabled.md) registernyckeln på 0.</span><span class="sxs-lookup"><span data-stu-id="f1add-118">If you do not want DSC to run at boot time, set the value of the [DSCAutomationHostEnabled registry key](DSCAutomationHostEnabled.md) registry key to 0.</span></span>

- <span data-ttu-id="f1add-119">Mata in en konfiguration MOF-dokument i en virtuell Hårddisk</span><span class="sxs-lookup"><span data-stu-id="f1add-119">Inject a configuration MOF document into a VHD</span></span>
- <span data-ttu-id="f1add-120">Mata in en DSC-metaconfiguration i en virtuell Hårddisk</span><span class="sxs-lookup"><span data-stu-id="f1add-120">Inject a DSC metaconfiguration into a VHD</span></span>
- <span data-ttu-id="f1add-121">Inaktivera DSC när datorn startas</span><span class="sxs-lookup"><span data-stu-id="f1add-121">Disable DSC at boot time</span></span>

> [!NOTE]
> <span data-ttu-id="f1add-122">Du kan mata in båda `Pending.mof` och `MetaConfig.mof` till en dator samtidigt.</span><span class="sxs-lookup"><span data-stu-id="f1add-122">You can inject both `Pending.mof` and `MetaConfig.mof` into a computer at the same time.</span></span>
> <span data-ttu-id="f1add-123">Om båda filerna finns inställningarna som anges i `MetaConfig.mof` företräde.</span><span class="sxs-lookup"><span data-stu-id="f1add-123">If both files are present, the settings specified in `MetaConfig.mof` take precedence.</span></span>

## <a name="inject-a-configuration-mof-document-into-a-vhd"></a><span data-ttu-id="f1add-124">Mata in en konfiguration MOF-dokument i en virtuell Hårddisk</span><span class="sxs-lookup"><span data-stu-id="f1add-124">Inject a configuration MOF document into a VHD</span></span>

<span data-ttu-id="f1add-125">För att införa en konfiguration vid första uppstart, kan du mata in en kompilerad konfiguration MOF-dokument i den virtuella Hårddisken som dess `Pending.mof` fil.</span><span class="sxs-lookup"><span data-stu-id="f1add-125">To enact a configuration at initial boot-up, you can inject a compiled configuration MOF document into the VHD as its `Pending.mof` file.</span></span>
<span data-ttu-id="f1add-126">Om den **DSCAutomationHostEnabled** registernyckeln har angetts till 2 (standardvärde), DSC gäller konfigurationen av `Pending.mof` när datorn startas för första gången.</span><span class="sxs-lookup"><span data-stu-id="f1add-126">If the **DSCAutomationHostEnabled** registry key is set to 2 (the default value), DSC will apply the configuration defined by `Pending.mof` when the computer boots up for the first time.</span></span>

<span data-ttu-id="f1add-127">I det här exemplet ska vi använda följande konfiguration, som installerar IIS på den nya datorn:</span><span class="sxs-lookup"><span data-stu-id="f1add-127">For this example, we will use the following configuration, which will install IIS on the new computer:</span></span>

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

### <a name="to-inject-the-configuration-mof-document-on-the-vhd"></a><span data-ttu-id="f1add-128">Att mata in konfiguration MOF-dokument på den virtuella Hårddisken</span><span class="sxs-lookup"><span data-stu-id="f1add-128">To inject the configuration MOF document on the VHD</span></span>

1. <span data-ttu-id="f1add-129">Montera den virtuella Hårddisken som du vill att mata in konfigurationen genom att anropa den [Montera VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f1add-129">Mount the VHD into which you want to inject the configuration by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="f1add-130">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="f1add-130">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. <span data-ttu-id="f1add-131">På en dator med PowerShell 5.0 eller senare, spara konfigurationen ovan (**SampleIISInstall**) som en PowerShell-skriptfil (.ps1).</span><span class="sxs-lookup"><span data-stu-id="f1add-131">On a computer running PowerShell 5.0 or later, save the above configuration (**SampleIISInstall**) as a PowerShell script (.ps1) file.</span></span>

3. <span data-ttu-id="f1add-132">Navigera till mappen där du sparade .ps1-fil i en PowerShell-konsol.</span><span class="sxs-lookup"><span data-stu-id="f1add-132">In a PowerShell console, navigate to the folder where you saved the .ps1 file.</span></span>

4. <span data-ttu-id="f1add-133">Kör följande PowerShell-kommandon för att kompilera MOF-dokument (information om kompilering av DSC-konfigurationer finns i [DSC-konfigurationer](configurations.md):</span><span class="sxs-lookup"><span data-stu-id="f1add-133">Run the following PowerShell commands to compile the MOF document (for information about compiling DSC configurations, see [DSC Configurations](configurations.md):</span></span>

   ```powershell
   . .\SampleIISInstall.ps1
   SampleIISInstall
   ```

5. <span data-ttu-id="f1add-134">Detta skapar en `localhost.mof` fil i en ny mapp med namnet `SampleIISInstall`.</span><span class="sxs-lookup"><span data-stu-id="f1add-134">This will create a `localhost.mof` file in a new folder named `SampleIISInstall`.</span></span>
   <span data-ttu-id="f1add-135">Byt namn på och flytta filen till rätt plats på den virtuella Hårddisken som `Pending.mof` med hjälp av den [flytta objekt](https://technet.microsoft.comlibrary/hh849852.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f1add-135">Rename and move that file into the proper location on the VHD as `Pending.mof` by using the [Move-Item](https://technet.microsoft.comlibrary/hh849852.aspx) cmdlet.</span></span> <span data-ttu-id="f1add-136">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="f1add-136">For example:</span></span>

   ```powershell
       Move-Item -Path C:\DSCTest\SampleIISInstall\localhost.mof -Destination E:\Windows\System32\Configuration\Pending.mof
   ```

6. <span data-ttu-id="f1add-137">Demontera den virtuella Hårddisken genom att anropa den [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f1add-137">Dismount the VHD by calling the [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet.</span></span> <span data-ttu-id="f1add-138">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="f1add-138">For example:</span></span>

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

7. <span data-ttu-id="f1add-139">Skapa en virtuell dator med hjälp av den virtuella Hårddisken där du installerade DSC MOF-dokument.</span><span class="sxs-lookup"><span data-stu-id="f1add-139">Create a VM by using the VHD where you installed the DSC MOF document.</span></span>

<span data-ttu-id="f1add-140">När du första uppstart och installationen av operativsystemet, kommer IIS att installeras.</span><span class="sxs-lookup"><span data-stu-id="f1add-140">After intial boot-up and operating system installation, IIS will be installed.</span></span>
<span data-ttu-id="f1add-141">Du kan kontrollera detta genom att anropa den [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f1add-141">You can verify this by calling the [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx) cmdlet.</span></span>

## <a name="inject-a-dsc-metaconfiguration-into-a-vhd"></a><span data-ttu-id="f1add-142">Mata in en DSC-metaconfiguration i en virtuell Hårddisk</span><span class="sxs-lookup"><span data-stu-id="f1add-142">Inject a DSC metaconfiguration into a VHD</span></span>

<span data-ttu-id="f1add-143">Du kan också konfigurera en dator för att hämta en konfiguration vid första uppstart genom att placera en metaconfiguration (se [konfigurerar den lokala Configuration Manager (LCM)](metaConfig.md)) till den virtuella Hårddisken som dess `MetaConfig.mof` fil.</span><span class="sxs-lookup"><span data-stu-id="f1add-143">You can also configure a computer to pull a configuration at intial boot-up by injecting a metaconfiguration (see [Configuring the Local Configuration Manager (LCM)](metaConfig.md)) into the VHD as its `MetaConfig.mof` file.</span></span>
<span data-ttu-id="f1add-144">Om den **DSCAutomationHostEnabled** registernyckeln har angetts till 2 (standardvärde), DSC ska gälla metaconfiguration som definieras av `MetaConfig.mof` till LCM när datorn startas för första gången.</span><span class="sxs-lookup"><span data-stu-id="f1add-144">If the **DSCAutomationHostEnabled** registry key is set to 2 (the default value),  DSC will apply the metaconfiguration defined by `MetaConfig.mof` to the LCM when the computer boots up for the first time.</span></span>
<span data-ttu-id="f1add-145">Om metaconfiguration anger att LCM ska hämta konfigurationer från en pull-server, försöker datorn hämta en konfiguration från den pull-servern vid första uppstart.</span><span class="sxs-lookup"><span data-stu-id="f1add-145">If the metaconfiguration specifies that the LCM should pull configurations from a pull server, the computer will attempt to pull a configuration from that pull server at inital boot-up.</span></span>
<span data-ttu-id="f1add-146">Information om hur du konfigurerar en DSC-hämtningsserver finns i [att konfigurera en DSC-webbpullserver](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="f1add-146">For information about setting up a DSC pull server, see [Setting up a DSC web pull server](pullServer.md).</span></span>

<span data-ttu-id="f1add-147">I det här exemplet ska vi använda båda konfigurationen som beskrivs i föregående avsnitt (**SampleIISInstall**), och följande metaconfiguration:</span><span class="sxs-lookup"><span data-stu-id="f1add-147">For this example, we will use both the configuration described in the previous section (**SampleIISInstall**), and the following metaconfiguration:</span></span>

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

### <a name="to-inject-the-metaconfiguration-mof-document-on-the-vhd"></a><span data-ttu-id="f1add-148">Att mata in metaconfiguration MOF-dokument på den virtuella Hårddisken</span><span class="sxs-lookup"><span data-stu-id="f1add-148">To inject the metaconfiguration MOF document on the VHD</span></span>

1. <span data-ttu-id="f1add-149">Montera den virtuella Hårddisken som du vill infoga metaconfiguration genom att anropa den [Montera VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f1add-149">Mount the VHD into which you want to inject the metaconfiguration by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="f1add-150">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="f1add-150">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. <span data-ttu-id="f1add-151">[Konfigurera en DSC-webbpullserver](pullServer.md), och spara den **SampleIISInistall** konfiguration till rätt mapp.</span><span class="sxs-lookup"><span data-stu-id="f1add-151">[Set up a DSC web pull server](pullServer.md), and save the **SampleIISInistall** configuration to the appropriate folder.</span></span>

3. <span data-ttu-id="f1add-152">På en dator med PowerShell 5.0 eller senare, spara ovan metaconfiguration (**PullClientBootstrap**) som en PowerShell-skriptfil (.ps1).</span><span class="sxs-lookup"><span data-stu-id="f1add-152">On a computer running PowerShell 5.0 or later, save the above metaconfiguration (**PullClientBootstrap**) as a PowerShell script (.ps1) file.</span></span>

4. <span data-ttu-id="f1add-153">Navigera till mappen där du sparade .ps1-fil i en PowerShell-konsol.</span><span class="sxs-lookup"><span data-stu-id="f1add-153">In a PowerShell console, navigate to the folder where you saved the .ps1 file.</span></span>

5. <span data-ttu-id="f1add-154">Kör följande PowerShell-kommandon för att kompilera MOF-dokument metaconfiguration (information om kompilering av DSC-konfigurationer finns i [DSC-konfigurationer](configurations.md):</span><span class="sxs-lookup"><span data-stu-id="f1add-154">Run the following PowerShell commands to compile the  metaconfiguration MOF document (for information about compiling DSC configurations, see [DSC Configurations](configurations.md):</span></span>

   ```powershell
   . .\PullClientBootstrap.ps1
   PullClientBootstrap
   ```

6. <span data-ttu-id="f1add-155">Detta skapar en `localhost.meta.mof` fil i en ny mapp med namnet `PullClientBootstrap`.</span><span class="sxs-lookup"><span data-stu-id="f1add-155">This will create a `localhost.meta.mof` file in a new folder named `PullClientBootstrap`.</span></span>
   <span data-ttu-id="f1add-156">Byt namn på och flytta filen till rätt plats på den virtuella Hårddisken som `MetaConfig.mof` med hjälp av den [flytta objekt](https://technet.microsoft.comlibrary/hh849852.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f1add-156">Rename and move that file into the proper location on the VHD as `MetaConfig.mof` by using the [Move-Item](https://technet.microsoft.comlibrary/hh849852.aspx) cmdlet.</span></span>

   ```powershell
   Move-Item -Path C:\DSCTest\PullClientBootstrap\localhost.meta.mof -Destination E:\Windows\System32\Configuration\MetaConfig.mof
   ```

7. <span data-ttu-id="f1add-157">Demontera den virtuella Hårddisken genom att anropa den [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f1add-157">Dismount the VHD by calling the [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet.</span></span> <span data-ttu-id="f1add-158">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="f1add-158">For example:</span></span>

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

8. <span data-ttu-id="f1add-159">Skapa en virtuell dator med hjälp av den virtuella Hårddisken där du installerade DSC MOF-dokument.</span><span class="sxs-lookup"><span data-stu-id="f1add-159">Create a VM by using the VHD where you installed the DSC MOF document.</span></span>

<span data-ttu-id="f1add-160">När du första uppstart och installationen av operativsystemet, DSC hämtar konfigurationen från hämtningsservern och IIS ska installeras.</span><span class="sxs-lookup"><span data-stu-id="f1add-160">After intial boot-up and operating system installation, DSC will pull the configuration from the pull server, and IIS will be installed.</span></span>
<span data-ttu-id="f1add-161">Du kan kontrollera detta genom att anropa den [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f1add-161">You can verify this by calling the [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx) cmdlet.</span></span>

## <a name="disable-dsc-at-boot-time"></a><span data-ttu-id="f1add-162">Inaktivera DSC när datorn startas</span><span class="sxs-lookup"><span data-stu-id="f1add-162">Disable DSC at boot time</span></span>

<span data-ttu-id="f1add-163">Som standard, värdet för den `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\DSCAutomationHostEnabled` nyckeln har angetts till 2, vilket gör att en DSC-konfiguration för att köra om datorn är i väntande eller aktuella tillstånd.</span><span class="sxs-lookup"><span data-stu-id="f1add-163">By default, the value of the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\DSCAutomationHostEnabled` key is set to 2, which allows a DSC configuration to run if the computer is in pending or current state.</span></span> <span data-ttu-id="f1add-164">Om du inte vill att en konfiguration körs vid första uppstart måste du därför ange värdet för den här nyckeln till 0:</span><span class="sxs-lookup"><span data-stu-id="f1add-164">If you do not want a configuration to run at initial boot-up, you need so set the value of this key to 0:</span></span>

1. <span data-ttu-id="f1add-165">Montera den virtuella Hårddisken genom att anropa den [Montera VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f1add-165">Mount the VHD by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="f1add-166">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="f1add-166">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. <span data-ttu-id="f1add-167">Läsa in registret `HKLM\Software` undernycklar från den virtuella Hårddisken genom att anropa `reg load`.</span><span class="sxs-lookup"><span data-stu-id="f1add-167">Load the registry `HKLM\Software` subkey from the VHD by calling `reg load`.</span></span>

   ```powershell
   reg load HKLM\Vhd E:\Windows\System32\Config\Software`
   ```

3. <span data-ttu-id="f1add-168">Navigera till den `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\*` med hjälp av PowerShell register-provider.</span><span class="sxs-lookup"><span data-stu-id="f1add-168">Navigate to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\*` by using the PowerShell Registry provider.</span></span>

   ```powershell
   Set-Location HKLM:\Software\Microsoft\Windows\CurrentVersion\Policies`
   ```

4. <span data-ttu-id="f1add-169">Ändra värdet för `DSCAutomationHostEnabled` till 0.</span><span class="sxs-lookup"><span data-stu-id="f1add-169">Change the value of `DSCAutomationHostEnabled` to 0.</span></span>

   ```powershell
   Set-ItemProperty -Path . -Name DSCAutomationHostEnabled -Value 0
   ```

5. <span data-ttu-id="f1add-170">Ta bort registret genom att köra följande kommandon:</span><span class="sxs-lookup"><span data-stu-id="f1add-170">Unload the registry by running the following commands:</span></span>

   ```powershell
   [gc]::Collect()
   reg unload HKLM\Vhd
   ```

## <a name="see-also"></a><span data-ttu-id="f1add-171">Se även</span><span class="sxs-lookup"><span data-stu-id="f1add-171">See Also</span></span>

[<span data-ttu-id="f1add-172">DSC-konfigurationer</span><span class="sxs-lookup"><span data-stu-id="f1add-172">DSC Configurations</span></span>](configurations.md)

[<span data-ttu-id="f1add-173">DSCAutomationHostEnabled-registernyckel</span><span class="sxs-lookup"><span data-stu-id="f1add-173">DSCAutomationHostEnabled registry key</span></span>](DSCAutomationHostEnabled.md)

[<span data-ttu-id="f1add-174">Konfigurera den lokala konfigurationshanteraren (LCM)</span><span class="sxs-lookup"><span data-stu-id="f1add-174">Configuring the Local Configuration Manager (LCM)</span></span>](metaConfig.md)

[<span data-ttu-id="f1add-175">Konfigurera en DSC-webbpullserver</span><span class="sxs-lookup"><span data-stu-id="f1add-175">Setting up a DSC web pull server</span></span>](pullServer.md)
