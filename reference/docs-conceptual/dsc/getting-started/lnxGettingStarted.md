---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Kom igång med önskad tillstånds konfiguration (DSC) för Linux
description: Det här avsnittet beskriver hur du kommer igång med PowerShell-Desired State Configuration (DSC) för Linux.
ms.openlocfilehash: 826707654a297306c39d4dfcfd3941f56b7cf91d
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92651118"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-linux"></a><span data-ttu-id="57f0a-104">Kom igång med önskad tillstånds konfiguration (DSC) för Linux</span><span class="sxs-lookup"><span data-stu-id="57f0a-104">Get started with Desired State Configuration (DSC) for Linux</span></span>

<span data-ttu-id="57f0a-105">Det här avsnittet beskriver hur du kommer igång med PowerShell-Desired State Configuration (DSC) för Linux.</span><span class="sxs-lookup"><span data-stu-id="57f0a-105">This topic explains how to get started using PowerShell Desired State Configuration (DSC) for Linux.</span></span>
<span data-ttu-id="57f0a-106">Allmän information om DSC finns i [Kom igång med önskad tillstånds konfiguration i Windows PowerShell](../overview/overview.md).</span><span class="sxs-lookup"><span data-stu-id="57f0a-106">For general information about DSC, see [Get Started with Windows PowerShell Desired State Configuration](../overview/overview.md).</span></span>

## <a name="supported-linux-operation-system-versions"></a><span data-ttu-id="57f0a-107">System versioner för Linux operation som stöds</span><span class="sxs-lookup"><span data-stu-id="57f0a-107">Supported Linux operation system versions</span></span>

<span data-ttu-id="57f0a-108">Följande Linux-versioner av operativ systemet stöds av DSC för Linux.</span><span class="sxs-lookup"><span data-stu-id="57f0a-108">The following Linux operating system versions are supported by DSC for Linux.</span></span>

- <span data-ttu-id="57f0a-109">CentOS 5, 6 och 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="57f0a-109">CentOS 5, 6, and 7 (x86/x64)</span></span>
- <span data-ttu-id="57f0a-110">Debian GNU/Linux 6, 7 och 8 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="57f0a-110">Debian GNU/Linux 6, 7 and 8 (x86/x64)</span></span>
- <span data-ttu-id="57f0a-111">Oracle Linux 5, 6 och 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="57f0a-111">Oracle Linux 5, 6 and 7 (x86/x64)</span></span>
- <span data-ttu-id="57f0a-112">Red Hat Enterprise Linux Server 5, 6 och 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="57f0a-112">Red Hat Enterprise Linux Server 5, 6 and 7 (x86/x64)</span></span>
- <span data-ttu-id="57f0a-113">SUSE Linux Enterprise Server 10, 11 och 12 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="57f0a-113">SUSE Linux Enterprise Server 10, 11 and 12 (x86/x64)</span></span>
- <span data-ttu-id="57f0a-114">Ubuntu Server 12,04 LTS, 14,04 LTS, 16,04 LTS (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="57f0a-114">Ubuntu Server 12.04 LTS, 14.04 LTS, 16.04 LTS (x86/x64)</span></span>

## <a name="installing-dsc-for-linux"></a><span data-ttu-id="57f0a-115">Installera DSC för Linux</span><span class="sxs-lookup"><span data-stu-id="57f0a-115">Installing DSC for Linux</span></span>

<span data-ttu-id="57f0a-116">Du måste installera [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi) innan du installerar DSC för Linux.</span><span class="sxs-lookup"><span data-stu-id="57f0a-116">You must install the [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi) before installing DSC for Linux.</span></span>

### <a name="installing-omi"></a><span data-ttu-id="57f0a-117">Installerar OMI</span><span class="sxs-lookup"><span data-stu-id="57f0a-117">Installing OMI</span></span>

<span data-ttu-id="57f0a-118">Önskad tillstånds konfiguration för Linux kräver att CIM-servern Open Management Infrastructure (OMI), version 1.0.8.1 eller senare.</span><span class="sxs-lookup"><span data-stu-id="57f0a-118">Desired State Configuration for Linux requires the Open Management Infrastructure (OMI) CIM server, version 1.0.8.1 or later.</span></span> <span data-ttu-id="57f0a-119">OMI kan laddas ned från den öppna gruppen: [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi).</span><span class="sxs-lookup"><span data-stu-id="57f0a-119">OMI can be downloaded from The Open Group: [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi).</span></span>

<span data-ttu-id="57f0a-120">Installera OMI genom att installera det paket som är lämpligt för Linux-systemet (. rpm eller. deb) och OpenSSL-versionen (ssl_098 eller ssl_100) och arkitekturen (x64/x86).</span><span class="sxs-lookup"><span data-stu-id="57f0a-120">To install OMI, install the package that is appropriate for your Linux system (.rpm or .deb) and OpenSSL version (ssl_098 or ssl_100), and architecture (x64/x86).</span></span> <span data-ttu-id="57f0a-121">RPM-paket är lämpliga för CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server och Oracle Linux.</span><span class="sxs-lookup"><span data-stu-id="57f0a-121">RPM packages are appropriate for CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server, and Oracle Linux.</span></span> <span data-ttu-id="57f0a-122">DEB-paket är lämpliga för Debian GNU/Linux och Ubuntu Server.</span><span class="sxs-lookup"><span data-stu-id="57f0a-122">DEB packages are appropriate for Debian GNU/Linux and Ubuntu Server.</span></span> <span data-ttu-id="57f0a-123">De ssl_098-paketen är lämpliga för datorer med OpenSSL 0.9.8 installerade medan ssl_100-paket är lämpliga för datorer med OpenSSL 1,0 installerat.</span><span class="sxs-lookup"><span data-stu-id="57f0a-123">The ssl_098 packages are appropriate for computers with OpenSSL 0.9.8 installed while the ssl_100 packages are appropriate for computers with OpenSSL 1.0 installed.</span></span>

> [!NOTE]
> <span data-ttu-id="57f0a-124">Om du vill fastställa den installerade OpenSSL-versionen kör du kommandot `openssl version` .</span><span class="sxs-lookup"><span data-stu-id="57f0a-124">To determine the installed OpenSSL version, run the command `openssl version`.</span></span>

<span data-ttu-id="57f0a-125">Kör följande kommando för att installera OMI på ett CentOS 7 x64-system.</span><span class="sxs-lookup"><span data-stu-id="57f0a-125">Run the following command to install OMI on a CentOS 7 x64 system.</span></span>

`# sudo rpm -Uvh omiserver-1.0.8.ssl_100.rpm`

### <a name="installing-dsc"></a><span data-ttu-id="57f0a-126">Installerar DSC</span><span class="sxs-lookup"><span data-stu-id="57f0a-126">Installing DSC</span></span>

<span data-ttu-id="57f0a-127">DSC för Linux är tillgängligt för nedladdning från [PowerShell-DSC-för-Linux](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/tag/v1.1.1-294) -lagringsplatsen i lagrings platsen.</span><span class="sxs-lookup"><span data-stu-id="57f0a-127">DSC for Linux is available for download from the [PowerShell-DSC-for-Linux](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/tag/v1.1.1-294) repository in the repository.</span></span>

<span data-ttu-id="57f0a-128">Installera DSC genom att installera det paket som är lämpligt för Linux-systemet (. rpm eller. deb) och OpenSSL-versionen (ssl_098 eller ssl_100) och arkitekturen (x64/x86).</span><span class="sxs-lookup"><span data-stu-id="57f0a-128">To install DSC, install the package that is appropriate for your Linux system (.rpm or .deb) and OpenSSL version (ssl_098 or ssl_100), and architecture (x64/x86).</span></span> <span data-ttu-id="57f0a-129">RPM-paket är lämpliga för CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server och Oracle Linux.</span><span class="sxs-lookup"><span data-stu-id="57f0a-129">RPM packages are appropriate for CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server, and Oracle Linux.</span></span> <span data-ttu-id="57f0a-130">DEB-paket är lämpliga för Debian GNU/Linux och Ubuntu Server.</span><span class="sxs-lookup"><span data-stu-id="57f0a-130">DEB packages are appropriate for Debian GNU/Linux and Ubuntu Server.</span></span> <span data-ttu-id="57f0a-131">De ssl_098-paketen är lämpliga för datorer med OpenSSL 0.9.8 installerade medan ssl_100-paket är lämpliga för datorer med OpenSSL 1,0 installerat.</span><span class="sxs-lookup"><span data-stu-id="57f0a-131">The ssl_098 packages are appropriate for computers with OpenSSL 0.9.8 installed while the ssl_100 packages are appropriate for computers with OpenSSL 1.0 installed.</span></span>

> [!NOTE]
> <span data-ttu-id="57f0a-132">För att fastställa den installerade OpenSSL-versionen kör du kommandot openssl-versionen.</span><span class="sxs-lookup"><span data-stu-id="57f0a-132">To determine the installed OpenSSL version, run the command openssl version.</span></span>

<span data-ttu-id="57f0a-133">Kör följande kommando för att installera DSC på ett CentOS 7 x64-system.</span><span class="sxs-lookup"><span data-stu-id="57f0a-133">Run the following command to install DSC on a CentOS 7 x64 system.</span></span>

`# sudo rpm -Uvh dsc-1.0.0-254.ssl_100.x64.rpm`

## <a name="using-dsc-for-linux"></a><span data-ttu-id="57f0a-134">Använda DSC för Linux</span><span class="sxs-lookup"><span data-stu-id="57f0a-134">Using DSC for Linux</span></span>

<span data-ttu-id="57f0a-135">I följande avsnitt beskrivs hur du skapar och kör DSC-konfigurationer på Linux-datorer.</span><span class="sxs-lookup"><span data-stu-id="57f0a-135">The following sections explain how to create and run DSC configurations on Linux computers.</span></span>

### <a name="creating-a-configuration-mof-document"></a><span data-ttu-id="57f0a-136">Skapa ett MOF-dokument för konfiguration</span><span class="sxs-lookup"><span data-stu-id="57f0a-136">Creating a configuration MOF document</span></span>

<span data-ttu-id="57f0a-137">Nyckelordet Windows PowerShell-konfiguration används för att skapa en konfiguration för Linux-datorer, precis som för Windows-datorer.</span><span class="sxs-lookup"><span data-stu-id="57f0a-137">The Windows PowerShell Configuration keyword is used to create a configuration for Linux computers, just like for Windows computers.</span></span> <span data-ttu-id="57f0a-138">Följande steg beskriver hur du skapar ett konfigurations dokument för en Linux-dator med hjälp av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="57f0a-138">The following steps describe the creation of a configuration document for a Linux computer using Windows PowerShell.</span></span>

1. <span data-ttu-id="57f0a-139">Importera NX-modulen.</span><span class="sxs-lookup"><span data-stu-id="57f0a-139">Import the nx module.</span></span> <span data-ttu-id="57f0a-140">Windows PowerShell-modulen NX innehåller schemat för Built-In resurser för DSC för Linux och måste installeras på den lokala datorn och importeras i konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="57f0a-140">The nx Windows PowerShell module contains the schema for Built-In resources for DSC for Linux, and must be installed to your local computer and imported in the configuration.</span></span>

   - <span data-ttu-id="57f0a-141">Om du vill installera NX-modulen kopierar du NX-modulens katalog till antingen `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` eller `$PSHOME\Modules` .</span><span class="sxs-lookup"><span data-stu-id="57f0a-141">To install the nx module, copy the nx module directory to either `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` or `$PSHOME\Modules`.</span></span> <span data-ttu-id="57f0a-142">NX-modulen ingår i installations paketet DSC för Linux.</span><span class="sxs-lookup"><span data-stu-id="57f0a-142">The nx module is included in the DSC for Linux installation package.</span></span> <span data-ttu-id="57f0a-143">Om du vill importera NX-modulen i konfigurationen använder du `Import-DSCResource` kommandot:</span><span class="sxs-lookup"><span data-stu-id="57f0a-143">To import the nx module in your configuration, use the `Import-DSCResource` command:</span></span>

   ```powershell
   Configuration ExampleConfiguration{

    Import-DSCResource -Module nx

   }
   ```

2. <span data-ttu-id="57f0a-144">Definiera en konfiguration och generera konfigurations dokumentet:</span><span class="sxs-lookup"><span data-stu-id="57f0a-144">Define a configuration and generate the configuration document:</span></span>

   ```powershell
   Configuration ExampleConfiguration
   {
        Import-DscResource -Module nx

        Node  "linuxhost.contoso.com"
        {
            nxFile ExampleFile
            {
                DestinationPath = "/tmp/example"
                Contents = "hello world `n"
                Ensure = "Present"
                Type = "File"
            }
        }
   }

   ExampleConfiguration -OutputPath:"C:\temp"
   ```

### <a name="push-the-configuration-to-the-linux-computer"></a><span data-ttu-id="57f0a-145">Push-överför konfigurationen till Linux-datorn</span><span class="sxs-lookup"><span data-stu-id="57f0a-145">Push the configuration to the Linux computer</span></span>

<span data-ttu-id="57f0a-146">Konfigurations dokument (MOF-filer) kan flyttas till Linux-datorn med cmdleten [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) .</span><span class="sxs-lookup"><span data-stu-id="57f0a-146">Configuration documents (MOF files) can be pushed to the Linux computer using the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="57f0a-147">För att kunna använda denna cmdlet, tillsammans med cmdletarna [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration), eller [test-DscConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) , via fjärr anslutning till en Linux-dator, måste du använda en CIMSession.</span><span class="sxs-lookup"><span data-stu-id="57f0a-147">In order to use this cmdlet, along with the [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration), or [Test-DscConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) cmdlets, remotely to a Linux computer, you must use a CIMSession.</span></span> <span data-ttu-id="57f0a-148">Cmdlet: en [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) används för att skapa en **CimSession** till Linux-datorn.</span><span class="sxs-lookup"><span data-stu-id="57f0a-148">The [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) cmdlet is used to create a **CIMSession** to the Linux computer.</span></span>

<span data-ttu-id="57f0a-149">Följande kod visar hur du skapar en CIMSession för DSC för Linux.</span><span class="sxs-lookup"><span data-stu-id="57f0a-149">The following code shows how to create a CIMSession for DSC for Linux.</span></span>

```powershell
$Node = "ostc-dsc-01"
$Credential = Get-Credential -UserName "root" -Message "Enter Password:"

#Ignore SSL certificate validation
#$opt = New-CimSessionOption -UseSsl $true -SkipCACheck $true -SkipCNCheck $true -SkipRevocationCheck $true

#Options for a trusted SSL certificate
$opt = New-CimSessionOption -UseSsl $true
$Sess=New-CimSession -Credential $credential -ComputerName $Node -Port 5986 -Authentication basic -SessionOption $opt -OperationTimeoutSec 90
```

> [!NOTE]
> <span data-ttu-id="57f0a-150">För "push"-läge måste användarens autentiseringsuppgifter vara rot användaren på Linux-datorn.</span><span class="sxs-lookup"><span data-stu-id="57f0a-150">For "Push" mode, the user credential must be the root user on the Linux computer.</span></span> <span data-ttu-id="57f0a-151">Endast SSL/TLS-anslutningar stöds för DSC för Linux. `New-CimSession` måste användas med parametern – UseSSL inställd på $True.</span><span class="sxs-lookup"><span data-stu-id="57f0a-151">Only SSL/TLS connections are supported for DSC for Linux, the `New-CimSession` must be used with the –UseSSL parameter set to $true.</span></span> <span data-ttu-id="57f0a-152">SSL-certifikatet som används av OMI (för DSC) anges i filen: `/etc/opt/omi/conf/omiserver.conf` med egenskaperna: pemfile och KeyFile.</span><span class="sxs-lookup"><span data-stu-id="57f0a-152">The SSL certificate used by OMI (for DSC) is specified in the file: `/etc/opt/omi/conf/omiserver.conf` with the properties: pemfile and keyfile.</span></span> <span data-ttu-id="57f0a-153">Om det här certifikatet inte är betrott av Windows-datorn som du kör cmdleten [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) på, kan du välja att ignorera certifikat validering med alternativen för CimSession: `-SkipCACheck $true -SkipCNCheck $true -SkipRevocationCheck $true`</span><span class="sxs-lookup"><span data-stu-id="57f0a-153">If this certificate is not trusted by the Windows computer that you are running the [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) cmdlet on, you can choose to ignore certificate validation with the CIMSession Options: `-SkipCACheck $true -SkipCNCheck $true -SkipRevocationCheck $true`</span></span>

<span data-ttu-id="57f0a-154">Kör följande kommando för att skicka DSC-konfigurationen till Linux-noden.</span><span class="sxs-lookup"><span data-stu-id="57f0a-154">Run the following command to push the DSC configuration to the Linux node.</span></span>

`Start-DscConfiguration -Path:"C:\temp" -CimSession $Sess -Wait -Verbose`

### <a name="distribute-the-configuration-with-a-pull-server"></a><span data-ttu-id="57f0a-155">Distribuera konfigurationen med en hämtnings Server</span><span class="sxs-lookup"><span data-stu-id="57f0a-155">Distribute the configuration with a pull server</span></span>

<span data-ttu-id="57f0a-156">Konfigurationer kan distribueras till en Linux-dator med en pull-server, precis som för Windows-datorer.</span><span class="sxs-lookup"><span data-stu-id="57f0a-156">Configurations can be distributed to a Linux computer with a pull server, just like for Windows computers.</span></span> <span data-ttu-id="57f0a-157">Vägledning om hur du använder en hämtnings Server finns i [Windows PowerShell Desired State Configuration pull-servrar](../pull-server/pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="57f0a-157">For guidance on using a pull server, see [Windows PowerShell Desired State Configuration Pull Servers](../pull-server/pullServer.md).</span></span> <span data-ttu-id="57f0a-158">Mer information och begränsningar som rör användning av Linux-datorer med en hämtnings Server finns i versions anteckningar för önskad tillstånds konfiguration för Linux.</span><span class="sxs-lookup"><span data-stu-id="57f0a-158">For additional information and limitations related to using Linux computers with a pull server, see the Release Notes for Desired State Configuration for Linux.</span></span>

### <a name="working-with-configurations-locally"></a><span data-ttu-id="57f0a-159">Arbeta med konfigurationer lokalt</span><span class="sxs-lookup"><span data-stu-id="57f0a-159">Working with configurations locally</span></span>

<span data-ttu-id="57f0a-160">DSC för Linux innehåller skript för att arbeta med konfiguration från den lokala Linux-datorn.</span><span class="sxs-lookup"><span data-stu-id="57f0a-160">DSC for Linux includes scripts to work with configuration from the local Linux computer.</span></span> <span data-ttu-id="57f0a-161">Skripten hittar du i `/opt/microsoft/dsc/Scripts` och inkluderar följande:</span><span class="sxs-lookup"><span data-stu-id="57f0a-161">These scripts are locate in `/opt/microsoft/dsc/Scripts` and include the following:</span></span>

- <span data-ttu-id="57f0a-162">GetDscConfiguration.py</span><span class="sxs-lookup"><span data-stu-id="57f0a-162">GetDscConfiguration.py</span></span>

  <span data-ttu-id="57f0a-163">Returnerar den aktuella konfigurationen som tillämpas på datorn.</span><span class="sxs-lookup"><span data-stu-id="57f0a-163">Returns the current configuration applied to the computer.</span></span> <span data-ttu-id="57f0a-164">Liknar cmdlet: en för Windows PowerShell cmdlet `Get-DscConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="57f0a-164">Similar to the Windows PowerShell cmdlet `Get-DscConfiguration` cmdlet.</span></span>

  `# sudo ./GetDscConfiguration.py`

- <span data-ttu-id="57f0a-165">GetDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="57f0a-165">GetDscLocalConfigurationManager.py</span></span>

  <span data-ttu-id="57f0a-166">Returnerar den aktuella meta-konfigurationen som tillämpas på datorn.</span><span class="sxs-lookup"><span data-stu-id="57f0a-166">Returns the current meta-configuration applied to the computer.</span></span> <span data-ttu-id="57f0a-167">Liknar cmdlet [Get-DSCLocalConfigurationManager-](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) cmdleten.</span><span class="sxs-lookup"><span data-stu-id="57f0a-167">Similar to the cmdlet [Get-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) cmdlet.</span></span>

  `# sudo ./GetDscLocalConfigurationManager.py`

- <span data-ttu-id="57f0a-168">InstallModule.py</span><span class="sxs-lookup"><span data-stu-id="57f0a-168">InstallModule.py</span></span>

  <span data-ttu-id="57f0a-169">Installerar en anpassad DSC-resurs-modul.</span><span class="sxs-lookup"><span data-stu-id="57f0a-169">Installs a custom DSC resource module.</span></span> <span data-ttu-id="57f0a-170">Kräver sökvägen till en. zip-fil som innehåller modulen delade objekt bibliotek och schema MOF-filer.</span><span class="sxs-lookup"><span data-stu-id="57f0a-170">Requires the path to a .zip file containing the module shared object library and schema MOF files.</span></span>

 `# sudo ./InstallModule.py /tmp/cnx_Resource.zip`

- <span data-ttu-id="57f0a-171">RemoveModule.py</span><span class="sxs-lookup"><span data-stu-id="57f0a-171">RemoveModule.py</span></span>

  <span data-ttu-id="57f0a-172">Tar bort en anpassad DSC-resurs-modul.</span><span class="sxs-lookup"><span data-stu-id="57f0a-172">Removes a custom DSC resource module.</span></span> <span data-ttu-id="57f0a-173">Namnet på den modul som ska tas bort krävs.</span><span class="sxs-lookup"><span data-stu-id="57f0a-173">Requires the name of the module to remove.</span></span>

  `# sudo ./RemoveModule.py cnx_Resource`

- <span data-ttu-id="57f0a-174">StartDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="57f0a-174">StartDscLocalConfigurationManager.py</span></span>

  <span data-ttu-id="57f0a-175">Tillämpar en konfigurations-MOF-fil på datorn.</span><span class="sxs-lookup"><span data-stu-id="57f0a-175">Applies a configuration MOF file to the computer.</span></span> <span data-ttu-id="57f0a-176">Liknar cmdleten [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) .</span><span class="sxs-lookup"><span data-stu-id="57f0a-176">Similar to the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="57f0a-177">Kräver att sökvägen till konfigurations-MOF tillämpas.</span><span class="sxs-lookup"><span data-stu-id="57f0a-177">Requires the path to the configuration MOF to apply.</span></span>

  `# sudo ./StartDscLocalConfigurationManager.py –configurationmof /tmp/localhost.mof`

- <span data-ttu-id="57f0a-178">SetDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="57f0a-178">SetDscLocalConfigurationManager.py</span></span>

  <span data-ttu-id="57f0a-179">Använder en MOF-fil för meta-konfiguration på datorn.</span><span class="sxs-lookup"><span data-stu-id="57f0a-179">Applies a Meta Configuration MOF file to the computer.</span></span> <span data-ttu-id="57f0a-180">Liknar cmdleten [set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) .</span><span class="sxs-lookup"><span data-stu-id="57f0a-180">Similar to the [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) cmdlet.</span></span> <span data-ttu-id="57f0a-181">Kräver att sökvägen till MOF-filen för meta-konfiguration tillämpas.</span><span class="sxs-lookup"><span data-stu-id="57f0a-181">Requires the path to the Meta Configuration MOF to apply.</span></span>

  `# sudo ./SetDscLocalConfigurationManager.py –configurationmof /tmp/localhost.meta.mof`

## <a name="powershell-desired-state-configuration-for-linux-log-files"></a><span data-ttu-id="57f0a-182">PowerShell Desired State Configuration för Linux-loggfiler</span><span class="sxs-lookup"><span data-stu-id="57f0a-182">PowerShell Desired State Configuration for Linux Log Files</span></span>

<span data-ttu-id="57f0a-183">Följande loggfiler genereras för DSC-meddelanden för Linux.</span><span class="sxs-lookup"><span data-stu-id="57f0a-183">The following log files are generated for DSC for Linux messages.</span></span>

|     <span data-ttu-id="57f0a-184">Loggfil</span><span class="sxs-lookup"><span data-stu-id="57f0a-184">Log file</span></span>      |     <span data-ttu-id="57f0a-185">Katalog</span><span class="sxs-lookup"><span data-stu-id="57f0a-185">Directory</span></span>      |                                               <span data-ttu-id="57f0a-186">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="57f0a-186">Description</span></span>                                                |
| ----------------- | ------------------ | -------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="57f0a-187">**omiserver. log**</span><span class="sxs-lookup"><span data-stu-id="57f0a-187">**omiserver.log**</span></span> | `/var/opt/omi/log` | <span data-ttu-id="57f0a-188">Meddelanden som rör OMI CIM-serverns funktion.</span><span class="sxs-lookup"><span data-stu-id="57f0a-188">Messages relating to the operation of the OMI CIM server.</span></span>                                                |
| <span data-ttu-id="57f0a-189">**DSC. log**</span><span class="sxs-lookup"><span data-stu-id="57f0a-189">**dsc.log**</span></span>       | `/var/opt/omi/log` | <span data-ttu-id="57f0a-190">Meddelanden som rör åtgärden för den lokala Configuration Manager (LCM) och DSC-resurs åtgärder.</span><span class="sxs-lookup"><span data-stu-id="57f0a-190">Messages relating to the operation of the Local Configuration Manager (LCM) and DSC resource operations.</span></span> |
