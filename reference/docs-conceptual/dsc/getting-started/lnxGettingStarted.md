---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Kom igång med önskad tillstånds konfiguration (DSC) för Linux
ms.openlocfilehash: 523b91741dba57a98ac6e7ba660a776568af7065
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941903"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-linux"></a><span data-ttu-id="3f290-103">Kom igång med önskad tillstånds konfiguration (DSC) för Linux</span><span class="sxs-lookup"><span data-stu-id="3f290-103">Get started with Desired State Configuration (DSC) for Linux</span></span>

<span data-ttu-id="3f290-104">Det här avsnittet beskriver hur du kommer igång med PowerShell-Desired State Configuration (DSC) för Linux.</span><span class="sxs-lookup"><span data-stu-id="3f290-104">This topic explains how to get started using PowerShell Desired State Configuration (DSC) for Linux.</span></span> <span data-ttu-id="3f290-105">Allmän information om DSC finns i [Kom igång med önskad tillstånds konfiguration i Windows PowerShell](../overview/overview.md).</span><span class="sxs-lookup"><span data-stu-id="3f290-105">For general information about DSC, see [Get Started with Windows PowerShell Desired State Configuration](../overview/overview.md).</span></span>

## <a name="supported-linux-operation-system-versions"></a><span data-ttu-id="3f290-106">System versioner för Linux operation som stöds</span><span class="sxs-lookup"><span data-stu-id="3f290-106">Supported Linux operation system versions</span></span>

<span data-ttu-id="3f290-107">Följande Linux-versioner av operativ systemet stöds för DSC för Linux.</span><span class="sxs-lookup"><span data-stu-id="3f290-107">The following Linux operating system versions are supported for DSC for Linux.</span></span>

- <span data-ttu-id="3f290-108">CentOS 5, 6 och 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="3f290-108">CentOS 5, 6, and 7 (x86/x64)</span></span>
- <span data-ttu-id="3f290-109">Debian GNU/Linux 6, 7 och 8 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="3f290-109">Debian GNU/Linux 6, 7 and 8 (x86/x64)</span></span>
- <span data-ttu-id="3f290-110">Oracle Linux 5, 6 och 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="3f290-110">Oracle Linux 5, 6 and 7 (x86/x64)</span></span>
- <span data-ttu-id="3f290-111">Red Hat Enterprise Linux Server 5, 6 och 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="3f290-111">Red Hat Enterprise Linux Server 5, 6 and 7 (x86/x64)</span></span>
- <span data-ttu-id="3f290-112">SUSE Linux Enterprise Server 10, 11 och 12 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="3f290-112">SUSE Linux Enterprise Server 10, 11 and 12 (x86/x64)</span></span>
- <span data-ttu-id="3f290-113">Ubuntu Server 12,04 LTS, 14,04 LTS och 16,04 LTS (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="3f290-113">Ubuntu Server 12.04 LTS, 14.04 LTS and 16.04 LTS (x86/x64)</span></span>

<span data-ttu-id="3f290-114">I följande tabell beskrivs de nödvändiga paket beroendena för DSC för Linux.</span><span class="sxs-lookup"><span data-stu-id="3f290-114">The following table describes the required package dependencies for DSC for Linux.</span></span>

|  <span data-ttu-id="3f290-115">Nödvändigt paket</span><span class="sxs-lookup"><span data-stu-id="3f290-115">Required package</span></span> |  <span data-ttu-id="3f290-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="3f290-116">Description</span></span> |  <span data-ttu-id="3f290-117">Lägsta version</span><span class="sxs-lookup"><span data-stu-id="3f290-117">Minimum version</span></span> |
|---|---|---|
| <span data-ttu-id="3f290-118">glibc</span><span class="sxs-lookup"><span data-stu-id="3f290-118">glibc</span></span>| <span data-ttu-id="3f290-119">GNU-bibliotek</span><span class="sxs-lookup"><span data-stu-id="3f290-119">GNU Library</span></span>| <span data-ttu-id="3f290-120">2…4 – 31.30</span><span class="sxs-lookup"><span data-stu-id="3f290-120">2…4 – 31.30</span></span>|
| <span data-ttu-id="3f290-121">Python</span><span class="sxs-lookup"><span data-stu-id="3f290-121">python</span></span>| <span data-ttu-id="3f290-122">Python</span><span class="sxs-lookup"><span data-stu-id="3f290-122">Python</span></span>| <span data-ttu-id="3f290-123">2.4 – 3.4</span><span class="sxs-lookup"><span data-stu-id="3f290-123">2.4 – 3.4</span></span>|
| <span data-ttu-id="3f290-124">omiserver</span><span class="sxs-lookup"><span data-stu-id="3f290-124">omiserver</span></span>| <span data-ttu-id="3f290-125">Öppna hanterings infrastruktur</span><span class="sxs-lookup"><span data-stu-id="3f290-125">Open Management Infrastructure</span></span>| <span data-ttu-id="3f290-126">1.0.8.1</span><span class="sxs-lookup"><span data-stu-id="3f290-126">1.0.8.1</span></span>|
| <span data-ttu-id="3f290-127">openssl</span><span class="sxs-lookup"><span data-stu-id="3f290-127">openssl</span></span>| <span data-ttu-id="3f290-128">OpenSSL-bibliotek</span><span class="sxs-lookup"><span data-stu-id="3f290-128">OpenSSL Libraries</span></span>| <span data-ttu-id="3f290-129">0.9.8 eller 1,0</span><span class="sxs-lookup"><span data-stu-id="3f290-129">0.9.8 or 1.0</span></span>|
| <span data-ttu-id="3f290-130">ctypes</span><span class="sxs-lookup"><span data-stu-id="3f290-130">ctypes</span></span>| <span data-ttu-id="3f290-131">Python CTypes-bibliotek</span><span class="sxs-lookup"><span data-stu-id="3f290-131">Python CTypes library</span></span>| <span data-ttu-id="3f290-132">Måste matcha python-version</span><span class="sxs-lookup"><span data-stu-id="3f290-132">Must match Python version</span></span>|
| <span data-ttu-id="3f290-133">lib-sväng</span><span class="sxs-lookup"><span data-stu-id="3f290-133">libcurl</span></span>| <span data-ttu-id="3f290-134">klient bibliotek för spiral-http</span><span class="sxs-lookup"><span data-stu-id="3f290-134">cURL http client library</span></span>| <span data-ttu-id="3f290-135">7.15.1</span><span class="sxs-lookup"><span data-stu-id="3f290-135">7.15.1</span></span>|

## <a name="installing-dsc-for-linux"></a><span data-ttu-id="3f290-136">Installera DSC för Linux</span><span class="sxs-lookup"><span data-stu-id="3f290-136">Installing DSC for Linux</span></span>

<span data-ttu-id="3f290-137">Du måste installera [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi) innan du installerar DSC för Linux.</span><span class="sxs-lookup"><span data-stu-id="3f290-137">You must install the [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi) before installing DSC for Linux.</span></span>

### <a name="installing-omi"></a><span data-ttu-id="3f290-138">Installerar OMI</span><span class="sxs-lookup"><span data-stu-id="3f290-138">Installing OMI</span></span>

<span data-ttu-id="3f290-139">Önskad tillstånds konfiguration för Linux kräver att CIM-servern Open Management Infrastructure (OMI), version 1.0.8.1 eller senare.</span><span class="sxs-lookup"><span data-stu-id="3f290-139">Desired State Configuration for Linux requires the Open Management Infrastructure (OMI) CIM server, version 1.0.8.1 or later.</span></span> <span data-ttu-id="3f290-140">OMI kan laddas ned från den öppna gruppen: [Öppna hanterings infrastruktur (OMI)](https://github.com/Microsoft/omi).</span><span class="sxs-lookup"><span data-stu-id="3f290-140">OMI can be downloaded from The Open Group: [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi).</span></span>

<span data-ttu-id="3f290-141">Installera OMI genom att installera det paket som är lämpligt för Linux-systemet (. rpm eller. deb) och OpenSSL-version (ssl_098 eller ssl_100) och arkitektur (x64/x86).</span><span class="sxs-lookup"><span data-stu-id="3f290-141">To install OMI, install the package that is appropriate for your Linux system (.rpm or .deb) and OpenSSL version (ssl_098 or ssl_100), and architecture (x64/x86).</span></span> <span data-ttu-id="3f290-142">RPM-paket är lämpliga för CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server och Oracle Linux.</span><span class="sxs-lookup"><span data-stu-id="3f290-142">RPM packages are appropriate for CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server, and Oracle Linux.</span></span> <span data-ttu-id="3f290-143">DEB-paket är lämpliga för Debian GNU/Linux och Ubuntu Server.</span><span class="sxs-lookup"><span data-stu-id="3f290-143">DEB packages are appropriate for Debian GNU/Linux and Ubuntu Server.</span></span> <span data-ttu-id="3f290-144">Ssl_098-paketen är lämpliga för datorer med OpenSSL 0.9.8 installerade medan ssl_100-paketen är lämpliga för datorer med OpenSSL 1,0 installerat.</span><span class="sxs-lookup"><span data-stu-id="3f290-144">The ssl_098 packages are appropriate for computers with OpenSSL 0.9.8 installed while the ssl_100 packages are appropriate for computers with OpenSSL 1.0 installed.</span></span>

> [!NOTE]
> <span data-ttu-id="3f290-145">Om du vill fastställa den installerade OpenSSL-versionen kör `openssl version`du kommandot.</span><span class="sxs-lookup"><span data-stu-id="3f290-145">To determine the installed OpenSSL version, run the command `openssl version`.</span></span>

<span data-ttu-id="3f290-146">Kör följande kommando för att installera OMI på ett CentOS 7 x64-system.</span><span class="sxs-lookup"><span data-stu-id="3f290-146">Run the following command to install OMI on a CentOS 7 x64 system.</span></span>

`# sudo rpm -Uvh omiserver-1.0.8.ssl_100.rpm`

### <a name="installing-dsc"></a><span data-ttu-id="3f290-147">Installerar DSC</span><span class="sxs-lookup"><span data-stu-id="3f290-147">Installing DSC</span></span>

<span data-ttu-id="3f290-148">DSC för Linux är tillgängligt för hämtning [här](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/tag/v1.1.1-294).</span><span class="sxs-lookup"><span data-stu-id="3f290-148">DSC for Linux is available for download [here](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/tag/v1.1.1-294).</span></span>

<span data-ttu-id="3f290-149">Installera DSC genom att installera det paket som är lämpligt för Linux-systemet (. rpm eller. deb) och OpenSSL-versionen (ssl_098 eller ssl_100) och arkitekturen (x64/x86).</span><span class="sxs-lookup"><span data-stu-id="3f290-149">To install DSC, install the package that is appropriate for your Linux system (.rpm or .deb) and OpenSSL version (ssl_098 or ssl_100), and architecture (x64/x86).</span></span> <span data-ttu-id="3f290-150">RPM-paket är lämpliga för CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server och Oracle Linux.</span><span class="sxs-lookup"><span data-stu-id="3f290-150">RPM packages are appropriate for CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server, and Oracle Linux.</span></span> <span data-ttu-id="3f290-151">DEB-paket är lämpliga för Debian GNU/Linux och Ubuntu Server.</span><span class="sxs-lookup"><span data-stu-id="3f290-151">DEB packages are appropriate for Debian GNU/Linux and Ubuntu Server.</span></span> <span data-ttu-id="3f290-152">Ssl_098-paketen är lämpliga för datorer med OpenSSL 0.9.8 installerade medan ssl_100-paketen är lämpliga för datorer med OpenSSL 1,0 installerat.</span><span class="sxs-lookup"><span data-stu-id="3f290-152">The ssl_098 packages are appropriate for computers with OpenSSL 0.9.8 installed while the ssl_100 packages are appropriate for computers with OpenSSL 1.0 installed.</span></span>

> [!NOTE]
> <span data-ttu-id="3f290-153">För att fastställa den installerade OpenSSL-versionen kör du kommandot openssl-versionen.</span><span class="sxs-lookup"><span data-stu-id="3f290-153">To determine the installed OpenSSL version, run the command openssl version.</span></span>

<span data-ttu-id="3f290-154">Kör följande kommando för att installera DSC på ett CentOS 7 x64-system.</span><span class="sxs-lookup"><span data-stu-id="3f290-154">Run the following command to install DSC on a CentOS 7 x64 system.</span></span>

`# sudo rpm -Uvh dsc-1.0.0-254.ssl_100.x64.rpm`

## <a name="using-dsc-for-linux"></a><span data-ttu-id="3f290-155">Använda DSC för Linux</span><span class="sxs-lookup"><span data-stu-id="3f290-155">Using DSC for Linux</span></span>

<span data-ttu-id="3f290-156">I följande avsnitt beskrivs hur du skapar och kör DSC-konfigurationer på Linux-datorer.</span><span class="sxs-lookup"><span data-stu-id="3f290-156">The following sections explain how to create and run DSC configurations on Linux computers.</span></span>

### <a name="creating-a-configuration-mof-document"></a><span data-ttu-id="3f290-157">Skapa ett MOF-dokument för konfiguration</span><span class="sxs-lookup"><span data-stu-id="3f290-157">Creating a configuration MOF document</span></span>

<span data-ttu-id="3f290-158">Nyckelordet Windows PowerShell-konfiguration används för att skapa en konfiguration för Linux-datorer, precis som för Windows-datorer.</span><span class="sxs-lookup"><span data-stu-id="3f290-158">The Windows PowerShell Configuration keyword is used to create a configuration for Linux computers, just like for Windows computers.</span></span> <span data-ttu-id="3f290-159">Följande steg beskriver hur du skapar ett konfigurations dokument för en Linux-dator med hjälp av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3f290-159">The following steps describe the creation of a configuration document for a Linux computer using Windows PowerShell.</span></span>

1. <span data-ttu-id="3f290-160">Importera NX-modulen.</span><span class="sxs-lookup"><span data-stu-id="3f290-160">Import the nx module.</span></span> <span data-ttu-id="3f290-161">Windows PowerShell-modulen NX innehåller schemat för inbyggda resurser för DSC för Linux och måste installeras på den lokala datorn och importeras i konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="3f290-161">The nx Windows PowerShell module contains the schema for Built-In resources for DSC for Linux, and must be installed to your local computer and imported in the configuration.</span></span>

   - <span data-ttu-id="3f290-162">Om du vill installera NX-modulen kopierar du NX-modulens `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` katalog `$PSHOME\Modules`till antingen eller.</span><span class="sxs-lookup"><span data-stu-id="3f290-162">To install the nx module, copy the nx module directory to either `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` or `$PSHOME\Modules`.</span></span> <span data-ttu-id="3f290-163">NX-modulen ingår i installations paketet DSC för Linux.</span><span class="sxs-lookup"><span data-stu-id="3f290-163">The nx module is included in the DSC for Linux installation package.</span></span> <span data-ttu-id="3f290-164">Om du vill importera NX-modulen i konfigurationen använder du `Import-DSCResource` kommandot:</span><span class="sxs-lookup"><span data-stu-id="3f290-164">To import the nx module in your configuration, use the `Import-DSCResource` command:</span></span>

   ```powershell
   Configuration ExampleConfiguration{

    Import-DSCResource -Module nx

   }
   ```

2. <span data-ttu-id="3f290-165">Definiera en konfiguration och generera konfigurations dokumentet:</span><span class="sxs-lookup"><span data-stu-id="3f290-165">Define a configuration and generate the configuration document:</span></span>

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

### <a name="push-the-configuration-to-the-linux-computer"></a><span data-ttu-id="3f290-166">Push-överför konfigurationen till Linux-datorn</span><span class="sxs-lookup"><span data-stu-id="3f290-166">Push the configuration to the Linux computer</span></span>

<span data-ttu-id="3f290-167">Konfigurations dokument (MOF-filer) kan flyttas till Linux-datorn med cmdleten [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) .</span><span class="sxs-lookup"><span data-stu-id="3f290-167">Configuration documents (MOF files) can be pushed to the Linux computer using the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="3f290-168">För att kunna använda denna cmdlet, tillsammans med cmdletarna [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration), eller [test-DscConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) , via fjärr anslutning till en Linux-dator, måste du använda en CIMSession.</span><span class="sxs-lookup"><span data-stu-id="3f290-168">In order to use this cmdlet, along with the [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration), or [Test-DscConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) cmdlets, remotely to a Linux computer, you must use a CIMSession.</span></span> <span data-ttu-id="3f290-169">Cmdlet: en [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) används för att skapa en CimSession till Linux-datorn.</span><span class="sxs-lookup"><span data-stu-id="3f290-169">The [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) cmdlet is used to create a CIMSession to the Linux computer.</span></span>

<span data-ttu-id="3f290-170">Följande kod visar hur du skapar en CIMSession för DSC för Linux.</span><span class="sxs-lookup"><span data-stu-id="3f290-170">The following code shows how to create a CIMSession for DSC for Linux.</span></span>

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
> <span data-ttu-id="3f290-171">För "push"-läge måste användarens autentiseringsuppgifter vara rot användaren på Linux-datorn.</span><span class="sxs-lookup"><span data-stu-id="3f290-171">For "Push" mode, the user credential must be the root user on the Linux computer.</span></span>
> <span data-ttu-id="3f290-172">Endast SSL/TLS-anslutningar stöds för DSC för Linux. `New-CimSession` måste användas med parametern – UseSSL inställd på $True.</span><span class="sxs-lookup"><span data-stu-id="3f290-172">Only SSL/TLS connections are supported for DSC for Linux, the `New-CimSession` must be used with the –UseSSL parameter set to $true.</span></span>
> <span data-ttu-id="3f290-173">SSL-certifikatet som används av OMI (för DSC) anges i filen: `/opt/omi/etc/omiserver.conf` med egenskaperna: pemfile och KeyFile.</span><span class="sxs-lookup"><span data-stu-id="3f290-173">The SSL certificate used by OMI (for DSC) is specified in the file: `/opt/omi/etc/omiserver.conf` with the properties: pemfile and keyfile.</span></span>
> <span data-ttu-id="3f290-174">Om det här certifikatet inte är betrott av Windows-datorn som du kör cmdleten [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) på, kan du välja att ignorera certifikat validering med alternativen för CimSession:`-SkipCACheck $true -SkipCNCheck $true -SkipRevocationCheck $true`</span><span class="sxs-lookup"><span data-stu-id="3f290-174">If this certificate is not trusted by the Windows computer that you are running the [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) cmdlet on, you can choose to ignore certificate validation with the CIMSession Options: `-SkipCACheck $true -SkipCNCheck $true -SkipRevocationCheck $true`</span></span>

<span data-ttu-id="3f290-175">Kör följande kommando för att skicka DSC-konfigurationen till Linux-noden.</span><span class="sxs-lookup"><span data-stu-id="3f290-175">Run the following command to push the DSC configuration to the Linux node.</span></span>

`Start-DscConfiguration -Path:"C:\temp" -CimSession $Sess -Wait -Verbose`

### <a name="distribute-the-configuration-with-a-pull-server"></a><span data-ttu-id="3f290-176">Distribuera konfigurationen med en hämtnings Server</span><span class="sxs-lookup"><span data-stu-id="3f290-176">Distribute the configuration with a pull server</span></span>

<span data-ttu-id="3f290-177">Konfigurationer kan distribueras till en Linux-dator med en pull-server, precis som för Windows-datorer.</span><span class="sxs-lookup"><span data-stu-id="3f290-177">Configurations can be distributed to a Linux computer with a pull server, just like for Windows computers.</span></span> <span data-ttu-id="3f290-178">Vägledning om hur du använder en hämtnings Server finns i [Windows PowerShell Desired State Configuration pull-servrar](../pull-server/pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="3f290-178">For guidance on using a pull server, see [Windows PowerShell Desired State Configuration Pull Servers](../pull-server/pullServer.md).</span></span> <span data-ttu-id="3f290-179">Mer information och begränsningar som rör användning av Linux-datorer med en hämtnings Server finns i versions anteckningar för önskad tillstånds konfiguration för Linux.</span><span class="sxs-lookup"><span data-stu-id="3f290-179">For additional information and limitations related to using Linux computers with a pull server, see the Release Notes for Desired State Configuration for Linux.</span></span>

### <a name="working-with-configurations-locally"></a><span data-ttu-id="3f290-180">Arbeta med konfigurationer lokalt</span><span class="sxs-lookup"><span data-stu-id="3f290-180">Working with configurations locally</span></span>

<span data-ttu-id="3f290-181">DSC för Linux innehåller skript för att arbeta med konfiguration från den lokala Linux-datorn.</span><span class="sxs-lookup"><span data-stu-id="3f290-181">DSC for Linux includes scripts to work with configuration from the local Linux computer.</span></span> <span data-ttu-id="3f290-182">Skripten hittar du i `/opt/microsoft/dsc/Scripts` och inkluderar följande:</span><span class="sxs-lookup"><span data-stu-id="3f290-182">These scripts are locate in `/opt/microsoft/dsc/Scripts` and include the following:</span></span>

- <span data-ttu-id="3f290-183">GetDscConfiguration.py</span><span class="sxs-lookup"><span data-stu-id="3f290-183">GetDscConfiguration.py</span></span>

<span data-ttu-id="3f290-184">Returnerar den aktuella konfigurationen som tillämpas på datorn.</span><span class="sxs-lookup"><span data-stu-id="3f290-184">Returns the current configuration applied to the computer.</span></span> <span data-ttu-id="3f290-185">Liknar cmdlet: en för Windows `Get-DscConfiguration` PowerShell cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3f290-185">Similar to the Windows PowerShell cmdlet `Get-DscConfiguration` cmdlet.</span></span>

`# sudo ./GetDscConfiguration.py`

- <span data-ttu-id="3f290-186">GetDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="3f290-186">GetDscLocalConfigurationManager.py</span></span>

<span data-ttu-id="3f290-187">Returnerar den aktuella meta-konfigurationen som tillämpas på datorn.</span><span class="sxs-lookup"><span data-stu-id="3f290-187">Returns the current meta-configuration applied to the computer.</span></span> <span data-ttu-id="3f290-188">Liknar cmdlet [Get-DSCLocalConfigurationManager-](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) cmdleten.</span><span class="sxs-lookup"><span data-stu-id="3f290-188">Similar to the cmdlet [Get-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) cmdlet.</span></span>

`# sudo ./GetDscLocalConfigurationManager.py`

- <span data-ttu-id="3f290-189">InstallModule.py</span><span class="sxs-lookup"><span data-stu-id="3f290-189">InstallModule.py</span></span>

<span data-ttu-id="3f290-190">Installerar en anpassad DSC-resurs-modul.</span><span class="sxs-lookup"><span data-stu-id="3f290-190">Installs a custom DSC resource module.</span></span> <span data-ttu-id="3f290-191">Kräver sökvägen till en. zip-fil som innehåller modulen delade objekt bibliotek och schema MOF-filer.</span><span class="sxs-lookup"><span data-stu-id="3f290-191">Requires the path to a .zip file containing the module shared object library and schema MOF files.</span></span>

`# sudo ./InstallModule.py /tmp/cnx_Resource.zip`

- <span data-ttu-id="3f290-192">RemoveModule.py</span><span class="sxs-lookup"><span data-stu-id="3f290-192">RemoveModule.py</span></span>

<span data-ttu-id="3f290-193">Tar bort en anpassad DSC-resurs-modul.</span><span class="sxs-lookup"><span data-stu-id="3f290-193">Removes a custom DSC resource module.</span></span> <span data-ttu-id="3f290-194">Namnet på den modul som ska tas bort krävs.</span><span class="sxs-lookup"><span data-stu-id="3f290-194">Requires the name of the module to remove.</span></span>

`# sudo ./RemoveModule.py cnx_Resource`

- <span data-ttu-id="3f290-195">StartDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="3f290-195">StartDscLocalConfigurationManager.py</span></span>

<span data-ttu-id="3f290-196">Tillämpar en konfigurations-MOF-fil på datorn.</span><span class="sxs-lookup"><span data-stu-id="3f290-196">Applies a configuration MOF file to the computer.</span></span> <span data-ttu-id="3f290-197">Liknar cmdleten [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) .</span><span class="sxs-lookup"><span data-stu-id="3f290-197">Similar to the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="3f290-198">Kräver att sökvägen till konfigurations-MOF tillämpas.</span><span class="sxs-lookup"><span data-stu-id="3f290-198">Requires the path to the configuration MOF to apply.</span></span>

`# sudo ./StartDscLocalConfigurationManager.py –configurationmof /tmp/localhost.mof`

- <span data-ttu-id="3f290-199">SetDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="3f290-199">SetDscLocalConfigurationManager.py</span></span>

<span data-ttu-id="3f290-200">Använder en MOF-fil för meta-konfiguration på datorn.</span><span class="sxs-lookup"><span data-stu-id="3f290-200">Applies a Meta Configuration MOF file to the computer.</span></span> <span data-ttu-id="3f290-201">Liknar cmdleten [set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) .</span><span class="sxs-lookup"><span data-stu-id="3f290-201">Similar to the [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) cmdlet.</span></span> <span data-ttu-id="3f290-202">Kräver att sökvägen till MOF-filen för meta-konfiguration tillämpas.</span><span class="sxs-lookup"><span data-stu-id="3f290-202">Requires the path to the Meta Configuration MOF to apply.</span></span>

`# sudo ./SetDscLocalConfigurationManager.py –configurationmof /tmp/localhost.meta.mof`

## <a name="powershell-desired-state-configuration-for-linux-log-files"></a><span data-ttu-id="3f290-203">PowerShell Desired State Configuration för Linux-loggfiler</span><span class="sxs-lookup"><span data-stu-id="3f290-203">PowerShell Desired State Configuration for Linux Log Files</span></span>

<span data-ttu-id="3f290-204">Följande loggfiler genereras för DSC-meddelanden för Linux.</span><span class="sxs-lookup"><span data-stu-id="3f290-204">The following log files are generated for DSC for Linux messages.</span></span>

|<span data-ttu-id="3f290-205">Loggfil</span><span class="sxs-lookup"><span data-stu-id="3f290-205">Log file</span></span>|<span data-ttu-id="3f290-206">Katalog</span><span class="sxs-lookup"><span data-stu-id="3f290-206">Directory</span></span>|<span data-ttu-id="3f290-207">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="3f290-207">Description</span></span>|
|---|---|---|
|<span data-ttu-id="3f290-208">**omiserver. log**</span><span class="sxs-lookup"><span data-stu-id="3f290-208">**omiserver.log**</span></span>|`/var/opt/omi/log`|<span data-ttu-id="3f290-209">Meddelanden som rör OMI CIM-serverns funktion.</span><span class="sxs-lookup"><span data-stu-id="3f290-209">Messages relating to the operation of the OMI CIM server.</span></span>|
|<span data-ttu-id="3f290-210">**DSC. log**</span><span class="sxs-lookup"><span data-stu-id="3f290-210">**dsc.log**</span></span>|`/var/opt/omi/log`|<span data-ttu-id="3f290-211">Meddelanden som rör åtgärden för den lokala Configuration Manager (LCM) och DSC-resurs åtgärder.</span><span class="sxs-lookup"><span data-stu-id="3f290-211">Messages relating to the operation of the Local Configuration Manager (LCM) and DSC resource operations.</span></span>|
