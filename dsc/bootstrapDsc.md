---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: "Konfigurera en virtuella datorer på första uppstart med hjälp av DSC"
ms.openlocfilehash: a3592c50fa7f2232538fbec07129fac86c1d00b5
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
><span data-ttu-id="80ae4-103">Gäller för: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="80ae4-103">Applies To: Windows PowerShell 5.0</span></span>

><span data-ttu-id="80ae4-104">**Obs:** den **DSCAutomationHostEnabled** registernyckel som beskrivs i det här avsnittet är inte tillgänglig i PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="80ae4-104">**Note:** The **DSCAutomationHostEnabled** registry key described in this topic is not available in PowerShell 4.0.</span></span>
<span data-ttu-id="80ae4-105">Mer information om hur du konfigurerar nya virtuella datorer på första uppstart i PowerShell 4.0 finns [vill automatiskt konfigurera dina datorer med hjälp av DSC vid första uppstart?](https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)</span><span class="sxs-lookup"><span data-stu-id="80ae4-105">For information on how to configure new virtual machines at initial boot-up in PowerShell 4.0, see [Want to Automatically Configure Your Machines Using DSC at Initial Boot-up?](https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)</span></span>

# <a name="configure-a-virtual-machines-at-initial-boot-up-by-using-dsc"></a><span data-ttu-id="80ae4-106">Konfigurera en virtuella datorer på första uppstart med hjälp av DSC</span><span class="sxs-lookup"><span data-stu-id="80ae4-106">Configure a virtual machines at initial boot-up by using DSC</span></span>

## <a name="requirements"></a><span data-ttu-id="80ae4-107">Krav</span><span class="sxs-lookup"><span data-stu-id="80ae4-107">Requirements</span></span>

<span data-ttu-id="80ae4-108">Om du vill köra exemplen behöver du:</span><span class="sxs-lookup"><span data-stu-id="80ae4-108">To run these examples, you will need:</span></span>

- <span data-ttu-id="80ae4-109">En startbar VHD att arbeta med.</span><span class="sxs-lookup"><span data-stu-id="80ae4-109">A bootable VHD to work with.</span></span> <span data-ttu-id="80ae4-110">Du kan ladda ned en ISO med en utvärderingsversion av Windows Server 2016 vid   [TechNet Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span><span class="sxs-lookup"><span data-stu-id="80ae4-110">You can download an ISO with an evaluation copy of Windows Server 2016 at   [TechNet Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span></span> <span data-ttu-id="80ae4-111">Du hittar anvisningar om hur du skapar en VHD från en ISO-avbildning på [skapa startbara virtuella hårddiskar](https://technet.microsoft.com/en-us/library/gg318049.aspx).</span><span class="sxs-lookup"><span data-stu-id="80ae4-111">You can find instructions on how to create a VHD from an ISO image at [Creating Bootable Virtual Hard Disks](https://technet.microsoft.com/en-us/library/gg318049.aspx).</span></span>
- <span data-ttu-id="80ae4-112">En värddator som har Hyper-V aktiverat.</span><span class="sxs-lookup"><span data-stu-id="80ae4-112">A host computer that has Hyper-V enabled.</span></span> <span data-ttu-id="80ae4-113">Mer information finns i [översikt över Hyper-V](https://technet.microsoft.com/library/hh831531.aspx).</span><span class="sxs-lookup"><span data-stu-id="80ae4-113">For information, see [Hyper-V overview](https://technet.microsoft.com/library/hh831531.aspx).</span></span>

<span data-ttu-id="80ae4-114">Med hjälp av DSC, kan du automatisera installationen och konfigurationen för en dator vid första uppstart.</span><span class="sxs-lookup"><span data-stu-id="80ae4-114">By using DSC, you can automate software installation and configuration for a computer at initial boot-up.</span></span>
<span data-ttu-id="80ae4-115">Det gör du genom att antingen Injicera en konfiguration MOF-dokument eller en metakonfigurationen i startbart medium (till exempel en virtuell Hårddisk) så att de körs under den första startprocessen.</span><span class="sxs-lookup"><span data-stu-id="80ae4-115">You do this by either injecting a configuration MOF document or a metaconfiguration into bootable media (such as a VHD) so that they are run during the initial boot-up process.</span></span>
<span data-ttu-id="80ae4-116">Det här beteendet anges av den [DSCAutomationHostEnabled registernyckeln](DSCAutomationHostEnabled.md) registernyckel under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies**.</span><span class="sxs-lookup"><span data-stu-id="80ae4-116">This behavior is specified by the [DSCAutomationHostEnabled registry key](DSCAutomationHostEnabled.md) registry key under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies**.</span></span>
<span data-ttu-id="80ae4-117">Som standard är värdet för den här nyckeln 2, vilket gör att DSC ska köras när datorn startas.</span><span class="sxs-lookup"><span data-stu-id="80ae4-117">By default, the value of this key is 2, which allows DSC to run at boot time.</span></span>

<span data-ttu-id="80ae4-118">Om du inte vill DSC ska köras vid starten, ange värdet för den [DSCAutomationHostEnabled registernyckeln](DSCAutomationHostEnabled.md) registernyckeln till 0.</span><span class="sxs-lookup"><span data-stu-id="80ae4-118">If you do not want DSC to run at boot time, set the value of the [DSCAutomationHostEnabled registry key](DSCAutomationHostEnabled.md) registry key to 0.</span></span>

- <span data-ttu-id="80ae4-119">Mata in ett konfiguration MOF-dokument i en virtuell Hårddisk</span><span class="sxs-lookup"><span data-stu-id="80ae4-119">Inject a configuration MOF document into a VHD</span></span>
- <span data-ttu-id="80ae4-120">Mata in en DSC-metakonfigurationen i en virtuell Hårddisk</span><span class="sxs-lookup"><span data-stu-id="80ae4-120">Inject a DSC metaconfiguration into a VHD</span></span>
- <span data-ttu-id="80ae4-121">Inaktivera DSC vid start</span><span class="sxs-lookup"><span data-stu-id="80ae4-121">Disable DSC at boot time</span></span>

><span data-ttu-id="80ae4-122">**Obs:** kan mata in både `Pending.mof` och `MetaConfig.mof` i en dator samtidigt.</span><span class="sxs-lookup"><span data-stu-id="80ae4-122">**Note:** You can inject both `Pending.mof` and `MetaConfig.mof` into a computer at the same time.</span></span>
<span data-ttu-id="80ae4-123">Om båda filerna finns inställningarna som anges i `MetaConfig.mof` företräde.</span><span class="sxs-lookup"><span data-stu-id="80ae4-123">If both files are present, the settings specified in `MetaConfig.mof` take precedence.</span></span>

## <a name="inject-a-configuration-mof-document-into-a-vhd"></a><span data-ttu-id="80ae4-124">Mata in ett konfiguration MOF-dokument i en virtuell Hårddisk</span><span class="sxs-lookup"><span data-stu-id="80ae4-124">Inject a configuration MOF document into a VHD</span></span>

<span data-ttu-id="80ae4-125">För att införa en konfiguration på första uppstart du mata in ett kompilerade configuration MOF-dokument i den virtuella Hårddisken som dess `Pending.mof` fil.</span><span class="sxs-lookup"><span data-stu-id="80ae4-125">To enact a configuration at initial boot-up, you can inject a compiled configuration MOF document into the VHD as its `Pending.mof` file.</span></span>
<span data-ttu-id="80ae4-126">Om den **DSCAutomationHostEnabled** registernyckeln har värdet 2 (standardvärdet), DSC gäller konfigurationen av `Pending.mof` när datorn startas för första gången.</span><span class="sxs-lookup"><span data-stu-id="80ae4-126">If the **DSCAutomationHostEnabled** registry key is set to 2 (the default value), DSC will apply the configuration defined by `Pending.mof` when the computer boots up for the first time.</span></span>

<span data-ttu-id="80ae4-127">I det här exemplet ska vi använda följande konfiguration, som kommer att installera IIS på den nya datorn:</span><span class="sxs-lookup"><span data-stu-id="80ae4-127">For this example, we will use the following configuration, which will install IIS on the new computer:</span></span>

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

### <a name="to-inject-the-configuration-mof-document-on-the-vhd"></a><span data-ttu-id="80ae4-128">Att mata in konfiguration MOF-dokument på den virtuella Hårddisken</span><span class="sxs-lookup"><span data-stu-id="80ae4-128">To inject the configuration MOF document on the VHD</span></span>

1. <span data-ttu-id="80ae4-129">Montera VHD: N som du vill mata in konfigurationen genom att anropa den [Montera VHD](https://technet.microsoft.com/library/hh848551.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="80ae4-129">Mount the VHD into which you want to inject the configuration by calling the [Mount-VHD](https://technet.microsoft.com/library/hh848551.aspx) cmdlet.</span></span> <span data-ttu-id="80ae4-130">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="80ae4-130">For example:</span></span>

    ```powershell
    Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```
2. <span data-ttu-id="80ae4-131">På en dator som kör PowerShell 5.0 eller senare, spara konfigurationen ovan (**SampleIISInstall**) som en PowerShell-skriptfil (.ps1).</span><span class="sxs-lookup"><span data-stu-id="80ae4-131">On a computer running PowerShell 5.0 or later, save the above configuration (**SampleIISInstall**) as a PowerShell script (.ps1) file.</span></span>

3. <span data-ttu-id="80ae4-132">Navigera till mappen där du sparade .ps1-fil i en PowerShell-konsol.</span><span class="sxs-lookup"><span data-stu-id="80ae4-132">In a PowerShell console, navigate to the folder where you saved the .ps1 file.</span></span>

4. <span data-ttu-id="80ae4-133">Kör följande PowerShell-kommandon för att kompilera MOF-dokumentet (information om kompilering av DSC-konfigurationer finns [DSC-konfigurationer](configurations.md):</span><span class="sxs-lookup"><span data-stu-id="80ae4-133">Run the following PowerShell commands to compile the MOF document (for information about compiling DSC configurations, see [DSC Configurations](configurations.md):</span></span>

    ```powershell
    . .\SampleIISInstall.ps1
    SampleIISInstall
    ```

5. <span data-ttu-id="80ae4-134">Detta skapar en `localhost.mof` fil i en ny mapp med namnet `SampleIISInstall`.</span><span class="sxs-lookup"><span data-stu-id="80ae4-134">This will create a `localhost.mof` file in a new folder named `SampleIISInstall`.</span></span>
<span data-ttu-id="80ae4-135">Byt namn på och flytta filen till rätt plats på den virtuella Hårddisken som `Pending.mof` med hjälp av den [flytta objekt](https://technet.microsoft.comlibrary/hh849852.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="80ae4-135">Rename and move that file into the proper location on the VHD as `Pending.mof` by using the [Move-Item](https://technet.microsoft.comlibrary/hh849852.aspx) cmdlet.</span></span> <span data-ttu-id="80ae4-136">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="80ae4-136">For example:</span></span>

    ```powershell
        Move-Item -Path C:\DSCTest\SampleIISInstall\localhost.mof -Destination E:\Windows\Sytem32\Configuration\Pending.mof
    ```
6. <span data-ttu-id="80ae4-137">Demontera den virtuella Hårddisken genom att anropa den [Dismount-VHD](https://technet.microsoft.com/library/hh848562.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="80ae4-137">Dismount the VHD by calling the [Dismount-VHD](https://technet.microsoft.com/library/hh848562.aspx) cmdlet.</span></span> <span data-ttu-id="80ae4-138">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="80ae4-138">For example:</span></span>

    ```powershell
    Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```

7. <span data-ttu-id="80ae4-139">Skapa en virtuell dator med hjälp av den virtuella Hårddisken där du installerade DSC MOF-dokumentet.</span><span class="sxs-lookup"><span data-stu-id="80ae4-139">Create a VM by using the VHD where you installed the DSC MOF document.</span></span> <span data-ttu-id="80ae4-140">Efter första uppstart och installation av operativsystemet, kommer IIS att installeras.</span><span class="sxs-lookup"><span data-stu-id="80ae4-140">After intial boot-up and operating system installation, IIS will be installed.</span></span>
<span data-ttu-id="80ae4-141">Du kan kontrollera detta genom att anropa den [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="80ae4-141">You can verify this by calling the [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx) cmdlet.</span></span>

## <a name="inject-a-dsc-metaconfiguration-into-a-vhd"></a><span data-ttu-id="80ae4-142">Mata in en DSC-metakonfigurationen i en virtuell Hårddisk</span><span class="sxs-lookup"><span data-stu-id="80ae4-142">Inject a DSC metaconfiguration into a VHD</span></span>

<span data-ttu-id="80ae4-143">Du kan också konfigurera en dator om du vill dra en konfiguration på första uppstart genom att injicera en metakonfigurationen (se [konfigurera den lokala Configuration Manager (MGM)](metaConfig.md)) till den virtuella Hårddisken som dess `MetaConfig.mof` fil.</span><span class="sxs-lookup"><span data-stu-id="80ae4-143">You can also configure a computer to pull a configuration at intial boot-up by injecting a metaconfiguration (see [Configuring the Local Configuration Manager (LCM)](metaConfig.md)) into the VHD as its `MetaConfig.mof` file.</span></span>
<span data-ttu-id="80ae4-144">Om den **DSCAutomationHostEnabled** registernyckeln har värdet 2 (standardvärdet) gäller DSC metakonfigurationen definieras av `MetaConfig.mof` till MGM när datorn startas för första gången.</span><span class="sxs-lookup"><span data-stu-id="80ae4-144">If the **DSCAutomationHostEnabled** registry key is set to 2 (the default value),  DSC will apply the metaconfiguration defined by `MetaConfig.mof` to the LCM when the computer boots up for the first time.</span></span>
<span data-ttu-id="80ae4-145">Om metakonfigurationen anger att MGM bör pull-konfigurationer från en pull-server, försöker datorn hämtar en konfiguration från den pull-servern vid första uppstart.</span><span class="sxs-lookup"><span data-stu-id="80ae4-145">If the metaconfiguration specifies that the LCM should pull configurations from a pull server, the computer will attempt to pull a configuration from that pull server at inital boot-up.</span></span>
<span data-ttu-id="80ae4-146">Information om hur du konfigurerar en DSC pull-server finns i [ställer in en pull webbserver DSC](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="80ae4-146">For information about setting up a DSC pull server, see [Setting up a DSC web pull server](pullServer.md).</span></span>

<span data-ttu-id="80ae4-147">I det här exemplet kommer vi att använda både konfigurationen som beskrivs i föregående avsnitt (**SampleIISInstall**), och följande metakonfigurationen:</span><span class="sxs-lookup"><span data-stu-id="80ae4-147">For this example, we will use both the configuration described in the previous section (**SampleIISInstall**), and the following metaconfiguration:</span></span>

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

### <a name="to-inject-the-metaconfiguration-mof-document-on-the-vhd"></a><span data-ttu-id="80ae4-148">Att mata in metakonfigurationen MOF-dokument på den virtuella Hårddisken</span><span class="sxs-lookup"><span data-stu-id="80ae4-148">To inject the metaconfiguration MOF document on the VHD</span></span>

1. <span data-ttu-id="80ae4-149">Montera VHD: N som du vill mata in metakonfigurationen genom att anropa den [Montera VHD](https://technet.microsoft.com/library/hh848551.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="80ae4-149">Mount the VHD into which you want to inject the metaconfiguration by calling the [Mount-VHD](https://technet.microsoft.com/library/hh848551.aspx) cmdlet.</span></span> <span data-ttu-id="80ae4-150">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="80ae4-150">For example:</span></span>

    ```powershell
    Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```

2. <span data-ttu-id="80ae4-151">[Konfigurera en pull-DSC webbserver](pullServer.md), och spara den **SampleIISInistall** konfiguration till rätt mapp.</span><span class="sxs-lookup"><span data-stu-id="80ae4-151">[Set up a DSC web pull server](pullServer.md), and save the **SampleIISInistall** configuration to the appropriate folder.</span></span>

3. <span data-ttu-id="80ae4-152">På en dator som kör PowerShell 5.0 eller senare, spara ovan metakonfigurationen (**PullClientBootstrap**) som en PowerShell-skriptfil (.ps1).</span><span class="sxs-lookup"><span data-stu-id="80ae4-152">On a computer running PowerShell 5.0 or later, save the above metaconfiguration (**PullClientBootstrap**) as a PowerShell script (.ps1) file.</span></span>

4. <span data-ttu-id="80ae4-153">Navigera till mappen där du sparade .ps1-fil i en PowerShell-konsol.</span><span class="sxs-lookup"><span data-stu-id="80ae4-153">In a PowerShell console, navigate to the folder where you saved the .ps1 file.</span></span>

5. <span data-ttu-id="80ae4-154">Kör följande PowerShell-kommandon för att kompilera MOF-dokumentet metakonfigurationen (information om kompilering av DSC-konfigurationer finns [DSC-konfigurationer](configurations.md):</span><span class="sxs-lookup"><span data-stu-id="80ae4-154">Run the following PowerShell commands to compile the  metaconfiguration MOF document (for information about compiling DSC configurations, see [DSC Configurations](configurations.md):</span></span>

    ```powershell
    . .\PullClientBootstrap.ps1
    PullClientBootstrap
    ```

6. <span data-ttu-id="80ae4-155">Detta skapar en `localhost.meta.mof` fil i en ny mapp med namnet `PullClientBootstrap`.</span><span class="sxs-lookup"><span data-stu-id="80ae4-155">This will create a `localhost.meta.mof` file in a new folder named `PullClientBootstrap`.</span></span>
<span data-ttu-id="80ae4-156">Byt namn på och flytta filen till rätt plats på den virtuella Hårddisken som `MetaConfig.mof` med hjälp av den [flytta objekt](https://technet.microsoft.comlibrary/hh849852.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="80ae4-156">Rename and move that file into the proper location on the VHD as `MetaConfig.mof` by using the [Move-Item](https://technet.microsoft.comlibrary/hh849852.aspx) cmdlet.</span></span>

    ```powershell
    Move-Item -Path C:\DSCTest\PullClientBootstrap\localhost.meta.mof -Destination E:\Windows\Sytem32\Configuration\MetaConfig.mof
    ```

7. <span data-ttu-id="80ae4-157">Demontera den virtuella Hårddisken genom att anropa den [Dismount-VHD](https://technet.microsoft.com/library/hh848562.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="80ae4-157">Dismount the VHD by calling the [Dismount-VHD](https://technet.microsoft.com/library/hh848562.aspx) cmdlet.</span></span> <span data-ttu-id="80ae4-158">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="80ae4-158">For example:</span></span>

    ```powershell
    Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```

8. <span data-ttu-id="80ae4-159">Skapa en virtuell dator med hjälp av den virtuella Hårddisken där du installerade DSC MOF-dokumentet.</span><span class="sxs-lookup"><span data-stu-id="80ae4-159">Create a VM by using the VHD where you installed the DSC MOF document.</span></span>
<span data-ttu-id="80ae4-160">Efter första uppstart och installation av operativsystemet, DSC hämtar konfigurationen från den pull-servern och IIS installeras.</span><span class="sxs-lookup"><span data-stu-id="80ae4-160">After intial boot-up and operating system installation, DSC will pull the configuration from the pull server, and IIS will be installed.</span></span>
<span data-ttu-id="80ae4-161">Du kan kontrollera detta genom att anropa den [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="80ae4-161">You can verify this by calling the [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx) cmdlet.</span></span>

## <a name="disable-dsc-at-boot-time"></a><span data-ttu-id="80ae4-162">Inaktivera DSC vid start</span><span class="sxs-lookup"><span data-stu-id="80ae4-162">Disable DSC at boot time</span></span>

<span data-ttu-id="80ae4-163">Som standard värdet för den **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\DSCAutomationHostEnabled** nyckeln anges till 2, vilket gör att en DSC-konfiguration för att köra om datorn är i väntande eller aktuella tillstånd.</span><span class="sxs-lookup"><span data-stu-id="80ae4-163">By default, the value of the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\DSCAutomationHostEnabled** key is set to 2, which allows a DSC configuration to run if the computer is in pending or current state.</span></span> <span data-ttu-id="80ae4-164">Om du inte vill att en konfiguration som ska köras vid första uppstart måste du ange värdet för den här nyckeln så till 0:</span><span class="sxs-lookup"><span data-stu-id="80ae4-164">If you do not want a configuration to run at initial boot-up, you need so set the value of this key to 0:</span></span>

1. <span data-ttu-id="80ae4-165">Montera VHD: N genom att anropa den [Montera VHD](https://technet.microsoft.com/library/hh848551.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="80ae4-165">Mount the VHD by calling the [Mount-VHD](https://technet.microsoft.com/library/hh848551.aspx) cmdlet.</span></span> <span data-ttu-id="80ae4-166">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="80ae4-166">For example:</span></span>

    ```powershell
    Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```

2. <span data-ttu-id="80ae4-167">Läsa in registret **HKLM\Software** undernycklar från den virtuella Hårddisken genom att anropa `reg load`.</span><span class="sxs-lookup"><span data-stu-id="80ae4-167">Load the registry **HKLM\Software** subkey from the VHD by calling `reg load`.</span></span>

    ```
    reg load HKLM\Vhd E:\Windows\System32\Config\Software`
    ```

3. <span data-ttu-id="80ae4-168">Navigera till den **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\***  med hjälp av PowerShell register-provider.</span><span class="sxs-lookup"><span data-stu-id="80ae4-168">Navigate to the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\*** by using the PowerShell Registry provider.</span></span>

    ```powershell
    Set-Location HKLM:\Software\Microsoft\Windows\CurrentVersion\Policies`
    ```

4. <span data-ttu-id="80ae4-169">Ändra värdet för `DSCAutomationHostEnabled` till 0.</span><span class="sxs-lookup"><span data-stu-id="80ae4-169">Change the value of `DSCAutomationHostEnabled` to 0.</span></span>

    ```powershell
    Set-ItemProperty -Path . -Name DSCAutomationHostEnabled -Value 0
    ```

5. <span data-ttu-id="80ae4-170">Ta bort registret genom att köra följande kommandon:</span><span class="sxs-lookup"><span data-stu-id="80ae4-170">Unload the registry by running the following commands:</span></span>

    ```powershell
    [gc]::Collect()
    reg unload HKLM\Vhd
    ```

## <a name="see-also"></a><span data-ttu-id="80ae4-171">Se även</span><span class="sxs-lookup"><span data-stu-id="80ae4-171">See Also</span></span>

- [<span data-ttu-id="80ae4-172">DSC-konfigurationer</span><span class="sxs-lookup"><span data-stu-id="80ae4-172">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="80ae4-173">DSCAutomationHostEnabled registernyckel</span><span class="sxs-lookup"><span data-stu-id="80ae4-173">DSCAutomationHostEnabled registry key</span></span>](DSCAutomationHostEnabled.md)
- [<span data-ttu-id="80ae4-174">Konfigurera den lokala Configuration Manager (MGM)</span><span class="sxs-lookup"><span data-stu-id="80ae4-174">Configuring the Local Configuration Manager (LCM)</span></span>](metaConfig.md)
- [<span data-ttu-id="80ae4-175">Ställer in en pull webbserver DSC</span><span class="sxs-lookup"><span data-stu-id="80ae4-175">Setting up a DSC web pull server</span></span>](pullServer.md)

