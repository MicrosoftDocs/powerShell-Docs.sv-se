---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Kom igång med önskad (DSC tillstånd Configuration) för Linux
ms.openlocfilehash: 0534cede979eb2917adb608dba622539fe4bdc45
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
---
# <a name="get-started-with-desired-state-configuration-dsc-for-linux"></a><span data-ttu-id="2d7d2-103">Kom igång med önskad (DSC tillstånd Configuration) för Linux</span><span class="sxs-lookup"><span data-stu-id="2d7d2-103">Get started with Desired State Configuration (DSC) for Linux</span></span>

<span data-ttu-id="2d7d2-104">Det här avsnittet beskriver hur du kommer igång med hjälp av PowerShell önskad tillstånd Configuration (DSC) för Linux.</span><span class="sxs-lookup"><span data-stu-id="2d7d2-104">This topic explains how to get started using PowerShell Desired State Configuration (DSC) for Linux.</span></span> <span data-ttu-id="2d7d2-105">Allmän information om DSC finns [Kom igång med Windows PowerShell Desired State Configuration](overview.md).</span><span class="sxs-lookup"><span data-stu-id="2d7d2-105">For general information about DSC, see [Get Started with Windows PowerShell Desired State Configuration](overview.md).</span></span>

## <a name="supported-linux-operation-system-versions"></a><span data-ttu-id="2d7d2-106">Linux åtgärden system-versioner som stöds</span><span class="sxs-lookup"><span data-stu-id="2d7d2-106">Supported Linux operation system versions</span></span>

<span data-ttu-id="2d7d2-107">Följande versioner av Linux-operativsystemet stöds för DSC för Linux.</span><span class="sxs-lookup"><span data-stu-id="2d7d2-107">The following Linux operating system versions are supported for DSC for Linux.</span></span>
- <span data-ttu-id="2d7d2-108">CentOS 5, 6 och 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="2d7d2-108">CentOS 5, 6, and 7 (x86/x64)</span></span>
- <span data-ttu-id="2d7d2-109">Debian GNU/Linux 6, 7 och 8 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="2d7d2-109">Debian GNU/Linux 6, 7 and 8 (x86/x64)</span></span>
- <span data-ttu-id="2d7d2-110">Oracle Linux 5, 6 och 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="2d7d2-110">Oracle Linux 5, 6 and 7 (x86/x64)</span></span>
- <span data-ttu-id="2d7d2-111">Red Hat Enterprise Linux Server 5, 6 och 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="2d7d2-111">Red Hat Enterprise Linux Server 5, 6 and 7 (x86/x64)</span></span>
- <span data-ttu-id="2d7d2-112">SUSE Linux Enterprise Server 10, 11 och 12 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="2d7d2-112">SUSE Linux Enterprise Server 10, 11 and 12 (x86/x64)</span></span>
- <span data-ttu-id="2d7d2-113">Ubuntu Server 12.04 LTS, 14.04 LTS och 16.04 LTS (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="2d7d2-113">Ubuntu Server 12.04 LTS, 14.04 LTS and 16.04 LTS (x86/x64)</span></span>

<span data-ttu-id="2d7d2-114">I följande tabell beskrivs paket som krävs beroenden för DSC för Linux.</span><span class="sxs-lookup"><span data-stu-id="2d7d2-114">The following table describes the required package dependencies for DSC for Linux.</span></span>

|  <span data-ttu-id="2d7d2-115">Nödvändigt paket</span><span class="sxs-lookup"><span data-stu-id="2d7d2-115">Required package</span></span> |  <span data-ttu-id="2d7d2-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="2d7d2-116">Description</span></span> |  <span data-ttu-id="2d7d2-117">Lägsta version</span><span class="sxs-lookup"><span data-stu-id="2d7d2-117">Minimum version</span></span> |
|---|---|---|
| <span data-ttu-id="2d7d2-118">Glibc</span><span class="sxs-lookup"><span data-stu-id="2d7d2-118">glibc</span></span>| <span data-ttu-id="2d7d2-119">GNU Library</span><span class="sxs-lookup"><span data-stu-id="2d7d2-119">GNU Library</span></span>| <span data-ttu-id="2d7d2-120">2... 4 – 31.30</span><span class="sxs-lookup"><span data-stu-id="2d7d2-120">2…4 – 31.30</span></span>|
| <span data-ttu-id="2d7d2-121">Python</span><span class="sxs-lookup"><span data-stu-id="2d7d2-121">python</span></span>| <span data-ttu-id="2d7d2-122">Python</span><span class="sxs-lookup"><span data-stu-id="2d7d2-122">Python</span></span>| <span data-ttu-id="2d7d2-123">2.4 – 3.4</span><span class="sxs-lookup"><span data-stu-id="2d7d2-123">2.4 – 3.4</span></span>|
| <span data-ttu-id="2d7d2-124">omiserver</span><span class="sxs-lookup"><span data-stu-id="2d7d2-124">omiserver</span></span>| <span data-ttu-id="2d7d2-125">Open Management Infrastructure</span><span class="sxs-lookup"><span data-stu-id="2d7d2-125">Open Management Infrastructure</span></span>| <span data-ttu-id="2d7d2-126">1.0.8.1</span><span class="sxs-lookup"><span data-stu-id="2d7d2-126">1.0.8.1</span></span>|
| <span data-ttu-id="2d7d2-127">Openssl</span><span class="sxs-lookup"><span data-stu-id="2d7d2-127">openssl</span></span>| <span data-ttu-id="2d7d2-128">OpenSSL-bibliotek</span><span class="sxs-lookup"><span data-stu-id="2d7d2-128">OpenSSL Libraries</span></span>| <span data-ttu-id="2d7d2-129">0.9.8 eller 1.0</span><span class="sxs-lookup"><span data-stu-id="2d7d2-129">0.9.8 or 1.0</span></span>|
| <span data-ttu-id="2d7d2-130">ctypes</span><span class="sxs-lookup"><span data-stu-id="2d7d2-130">ctypes</span></span>| <span data-ttu-id="2d7d2-131">Python CTypes bibliotek</span><span class="sxs-lookup"><span data-stu-id="2d7d2-131">Python CTypes library</span></span>| <span data-ttu-id="2d7d2-132">Måste matcha versionen av Python</span><span class="sxs-lookup"><span data-stu-id="2d7d2-132">Must match Python version</span></span>|
| <span data-ttu-id="2d7d2-133">libcurl</span><span class="sxs-lookup"><span data-stu-id="2d7d2-133">libcurl</span></span>| <span data-ttu-id="2d7d2-134">cURL http-klientbibliotek</span><span class="sxs-lookup"><span data-stu-id="2d7d2-134">cURL http client library</span></span>| <span data-ttu-id="2d7d2-135">7.15.1</span><span class="sxs-lookup"><span data-stu-id="2d7d2-135">7.15.1</span></span>|

## <a name="installing-dsc-for-linux"></a><span data-ttu-id="2d7d2-136">Installera DSC för Linux</span><span class="sxs-lookup"><span data-stu-id="2d7d2-136">Installing DSC for Linux</span></span>

<span data-ttu-id="2d7d2-137">Du måste installera den [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi) innan du installerar DSC för Linux.</span><span class="sxs-lookup"><span data-stu-id="2d7d2-137">You must install the [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi) before installing DSC for Linux.</span></span>

### <a name="installing-omi"></a><span data-ttu-id="2d7d2-138">Installera OMI</span><span class="sxs-lookup"><span data-stu-id="2d7d2-138">Installing OMI</span></span>

<span data-ttu-id="2d7d2-139">Desired State Configuration för Linux kräver Open Management Infrastructure (OMI) CIM-servern, version 1.0.8.1 eller senare.</span><span class="sxs-lookup"><span data-stu-id="2d7d2-139">Desired State Configuration for Linux requires the Open Management Infrastructure (OMI) CIM server, version 1.0.8.1 or later.</span></span> <span data-ttu-id="2d7d2-140">OMI kan hämtas från Open Group: [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi).</span><span class="sxs-lookup"><span data-stu-id="2d7d2-140">OMI can be downloaded from The Open Group: [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi).</span></span>

<span data-ttu-id="2d7d2-141">Installera OMI installera det paket som är lämpliga för ditt Linux-system (.rpm eller .deb) och OpenSSL version (ssl_098 eller ssl_100) och arkitektur (x64/x86).</span><span class="sxs-lookup"><span data-stu-id="2d7d2-141">To install OMI, install the package that is appropriate for your Linux system (.rpm or .deb) and OpenSSL version (ssl_098 or ssl_100), and architecture (x64/x86).</span></span> <span data-ttu-id="2d7d2-142">RPM-paket är lämpliga för CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server och Oracle Linux.</span><span class="sxs-lookup"><span data-stu-id="2d7d2-142">RPM packages are appropriate for CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server, and Oracle Linux.</span></span> <span data-ttu-id="2d7d2-143">DEB-paket är lämpliga för Debian GNU/Linux- och Ubuntu Server.</span><span class="sxs-lookup"><span data-stu-id="2d7d2-143">DEB packages are appropriate for Debian GNU/Linux and Ubuntu Server.</span></span> <span data-ttu-id="2d7d2-144">Ssl_098-paket är lämpliga för datorer med OpenSSL 0.9.8 installerat under ssl_100-paket är lämpliga för datorer med OpenSSL 1.0 installeras.</span><span class="sxs-lookup"><span data-stu-id="2d7d2-144">The ssl_098 packages are appropriate for computers with OpenSSL 0.9.8 installed while the ssl_100 packages are appropriate for computers with OpenSSL 1.0 installed.</span></span>

> <span data-ttu-id="2d7d2-145">**Obs**: för att fastställa den installerade versionen av OpenSSL, kör du kommandot `openssl version`.</span><span class="sxs-lookup"><span data-stu-id="2d7d2-145">**Note**: To determine the installed OpenSSL version, run the command `openssl version`.</span></span>

<span data-ttu-id="2d7d2-146">Kör följande kommando för att installera OMI på ett CentOS 7 x64 system.</span><span class="sxs-lookup"><span data-stu-id="2d7d2-146">Run the following command to install OMI on a CentOS 7 x64 system.</span></span>

`# sudo rpm -Uvh omiserver-1.0.8.ssl_100.rpm`

### <a name="installing-dsc"></a><span data-ttu-id="2d7d2-147">Installera DSC</span><span class="sxs-lookup"><span data-stu-id="2d7d2-147">Installing DSC</span></span>

<span data-ttu-id="2d7d2-148">DSC för Linux finns att hämta [här](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/latest).</span><span class="sxs-lookup"><span data-stu-id="2d7d2-148">DSC for Linux is available for download [here](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/latest).</span></span>

<span data-ttu-id="2d7d2-149">Installera DSC, installera det paket som är lämpliga för ditt Linux-system (.rpm eller .deb) och OpenSSL version (ssl_098 eller ssl_100) och arkitektur (x64/x86).</span><span class="sxs-lookup"><span data-stu-id="2d7d2-149">To install DSC, install the package that is appropriate for your Linux system (.rpm or .deb) and OpenSSL version (ssl_098 or ssl_100), and architecture (x64/x86).</span></span> <span data-ttu-id="2d7d2-150">RPM-paket är lämpliga för CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server och Oracle Linux.</span><span class="sxs-lookup"><span data-stu-id="2d7d2-150">RPM packages are appropriate for CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server, and Oracle Linux.</span></span> <span data-ttu-id="2d7d2-151">DEB-paket är lämpliga för Debian GNU/Linux- och Ubuntu Server.</span><span class="sxs-lookup"><span data-stu-id="2d7d2-151">DEB packages are appropriate for Debian GNU/Linux and Ubuntu Server.</span></span> <span data-ttu-id="2d7d2-152">Ssl_098-paket är lämpliga för datorer med OpenSSL 0.9.8 installerat under ssl_100-paket är lämpliga för datorer med OpenSSL 1.0 installeras.</span><span class="sxs-lookup"><span data-stu-id="2d7d2-152">The ssl_098 packages are appropriate for computers with OpenSSL 0.9.8 installed while the ssl_100 packages are appropriate for computers with OpenSSL 1.0 installed.</span></span>

> <span data-ttu-id="2d7d2-153">**Obs**: för att fastställa den installerade versionen av OpenSSL, kör du kommandot openssl version.</span><span class="sxs-lookup"><span data-stu-id="2d7d2-153">**Note**: To determine the installed OpenSSL version, run the command openssl version.</span></span>

<span data-ttu-id="2d7d2-154">Kör följande kommando för att installera DSC på ett CentOS 7 x64 system.</span><span class="sxs-lookup"><span data-stu-id="2d7d2-154">Run the following command to install DSC on a CentOS 7 x64 system.</span></span>

`# sudo rpm -Uvh dsc-1.0.0-254.ssl_100.x64.rpm`


## <a name="using-dsc-for-linux"></a><span data-ttu-id="2d7d2-155">Använder DSC för Linux</span><span class="sxs-lookup"><span data-stu-id="2d7d2-155">Using DSC for Linux</span></span>

<span data-ttu-id="2d7d2-156">I följande avsnitt beskrivs hur du skapar och kör DSC-konfigurationer på Linux-datorer.</span><span class="sxs-lookup"><span data-stu-id="2d7d2-156">The following sections explain how to create and run DSC configurations on Linux computers.</span></span>

### <a name="creating-a-configuration-mof-document"></a><span data-ttu-id="2d7d2-157">Skapa ett configuration MOF-dokument</span><span class="sxs-lookup"><span data-stu-id="2d7d2-157">Creating a configuration MOF document</span></span>

<span data-ttu-id="2d7d2-158">Nyckelordet Windows PowerShell-konfigurationen används för att skapa en konfiguration för Linux-datorer precis som för Windows-datorer.</span><span class="sxs-lookup"><span data-stu-id="2d7d2-158">The Windows PowerShell Configuration keyword is used to create a configuration for Linux computers, just like for Windows computers.</span></span> <span data-ttu-id="2d7d2-159">Följande steg beskriver skapandet av ett konfigurationsdokument för en Linux-dator med Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2d7d2-159">The following steps describe the creation of a configuration document for a Linux computer using Windows PowerShell.</span></span>

1. <span data-ttu-id="2d7d2-160">Importera modulen nx.</span><span class="sxs-lookup"><span data-stu-id="2d7d2-160">Import the nx module.</span></span> <span data-ttu-id="2d7d2-161">Windows PowerShell-modulen nx måste innehåller schemat för inbyggda resurser för DSC för Linux och installeras på den lokala datorn och importeras i konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="2d7d2-161">The nx Windows PowerShell module contains the schema for Built-In resources for DSC for Linux, and must be installed to your local computer and imported in the configuration.</span></span>

    <span data-ttu-id="2d7d2-162">-Om du vill installera modulen nx kopiera modulkatalogen nx antingen `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` eller `$PSHOME\Modules`.</span><span class="sxs-lookup"><span data-stu-id="2d7d2-162">-To install the nx module, copy the nx module directory to either `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` or `$PSHOME\Modules`.</span></span> <span data-ttu-id="2d7d2-163">Modulen nx ingår i DSC för installationspaketet för Linux (MSI).</span><span class="sxs-lookup"><span data-stu-id="2d7d2-163">The nx module is included in the DSC for Linux installation package (MSI).</span></span> <span data-ttu-id="2d7d2-164">Importera modulen nx i din konfiguration genom att använda den __importera DSCResource__ kommando:</span><span class="sxs-lookup"><span data-stu-id="2d7d2-164">To import the nx module in your configuration, use the __Import-DSCResource__ command:</span></span>

```powershell
Configuration ExampleConfiguration{

    Import-DSCResource -Module nx

}
```
2. <span data-ttu-id="2d7d2-165">Definierar en konfiguration och generera konfigurationsdokument:</span><span class="sxs-lookup"><span data-stu-id="2d7d2-165">Define a configuration and generate the configuration document:</span></span>

```powershell
Configuration ExampleConfiguration{

    Import-DscResource -Module nx

    Node  "linuxhost.contoso.com"{
    nxFile ExampleFile {

        DestinationPath = "/tmp/example"
        Contents = "hello world `n"
        Ensure = "Present"
        Type = "File"
    }

    }
}
ExampleConfiguration -OutputPath:"C:\temp"
```

### <a name="push-the-configuration-to-the-linux-computer"></a><span data-ttu-id="2d7d2-166">Push-konfigurationen till Linux-dator</span><span class="sxs-lookup"><span data-stu-id="2d7d2-166">Push the configuration to the Linux computer</span></span>

<span data-ttu-id="2d7d2-167">Av konfigurationsdokument (MOF) flyttas till Linux-datorn med den [Start DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2d7d2-167">Configuration documents (MOF files) can be pushed to the Linux computer using the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet.</span></span> <span data-ttu-id="2d7d2-168">För att kunna använda denna cmdlet, tillsammans med den [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx), eller [Test DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlets, via en fjärranslutning till en Linux-dator, du måste använda en CIMSession.</span><span class="sxs-lookup"><span data-stu-id="2d7d2-168">In order to use this cmdlet, along with the [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx), or [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlets, remotely to a Linux computer, you must use a CIMSession.</span></span> <span data-ttu-id="2d7d2-169">Den [New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) cmdlet som används för att skapa en CIMSession till Linux-datorn.</span><span class="sxs-lookup"><span data-stu-id="2d7d2-169">The [New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) cmdlet is used to create a CIMSession to the Linux computer.</span></span>

<span data-ttu-id="2d7d2-170">Följande kod visar hur du skapar en CIMSession för DSC för Linux.</span><span class="sxs-lookup"><span data-stu-id="2d7d2-170">The following code shows how to create a CIMSession for DSC for Linux.</span></span>

```powershell
$Node = "ostc-dsc-01"
$Credential = Get-Credential -UserName:"root" -Message:"Enter Password:"

#Ignore SSL certificate validation
#$opt = New-CimSessionOption -UseSsl:$true -SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true

#Options for a trusted SSL certificate
$opt = New-CimSessionOption -UseSsl:$true
$Sess=New-CimSession -Credential:$credential -ComputerName:$Node -Port:5986 -Authentication:basic -SessionOption:$opt -OperationTimeoutSec:90
```

> <span data-ttu-id="2d7d2-171">**Obs**:</span><span class="sxs-lookup"><span data-stu-id="2d7d2-171">**Note**:</span></span>
* <span data-ttu-id="2d7d2-172">Användarens autentiseringsuppgifter måste vara rotanvändaren på Linux-dator för ”Push” läge.</span><span class="sxs-lookup"><span data-stu-id="2d7d2-172">For “Push” mode, the user credential must be the root user on the Linux computer.</span></span>
* <span data-ttu-id="2d7d2-173">SSL/TLS-anslutningar stöds för DSC för Linux, New-CimSession måste användas med parametern – UseSSL värdet $true.</span><span class="sxs-lookup"><span data-stu-id="2d7d2-173">Only SSL/TLS connections are supported for DSC for Linux, the New-CimSession must be used with the –UseSSL parameter set to $true.</span></span>
* <span data-ttu-id="2d7d2-174">SSL-certifikatet som används av OMI (för DSC) har angetts i filen: `/opt/omi/etc/omiserver.conf` med egenskaper: pemfile och nyckelfil.</span><span class="sxs-lookup"><span data-stu-id="2d7d2-174">The SSL certificate used by OMI (for DSC) is specified in the file: `/opt/omi/etc/omiserver.conf` with the properties: pemfile and keyfile.</span></span>
<span data-ttu-id="2d7d2-175">Om det här certifikatet inte är betrott av Windows-dator som du kör den [New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) cmdlet på, kan du ignorera certifikatvalidering med CIMSession alternativ: `-SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true`</span><span class="sxs-lookup"><span data-stu-id="2d7d2-175">If this certificate is not trusted by the Windows computer that you are running the [New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) cmdlet on, you can choose to ignore certificate validation with the CIMSession Options: `-SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true`</span></span>

<span data-ttu-id="2d7d2-176">Kör följande kommando för att push-DSC-konfigurationen till Linux-nod.</span><span class="sxs-lookup"><span data-stu-id="2d7d2-176">Run the following command to push the DSC configuration to the Linux node.</span></span>

`Start-DscConfiguration -Path:"C:\temp" -CimSession:$Sess -Wait -Verbose`

### <a name="distribute-the-configuration-with-a-pull-server"></a><span data-ttu-id="2d7d2-177">Distribuera konfigurationen med en pull-server</span><span class="sxs-lookup"><span data-stu-id="2d7d2-177">Distribute the configuration with a pull server</span></span>

<span data-ttu-id="2d7d2-178">Konfigurationer som kan distribueras till en Linux-dator med en pull-server, precis som för Windows-datorer.</span><span class="sxs-lookup"><span data-stu-id="2d7d2-178">Configurations can be distributed to a Linux computer with a pull server, just like for Windows computers.</span></span> <span data-ttu-id="2d7d2-179">Anvisningar om hur du använder en pull-server finns [Windows PowerShell önskad tillstånd Pull Konfigurationsservrar](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="2d7d2-179">For guidance on using a pull server, see [Windows PowerShell Desired State Configuration Pull Servers](pullServer.md).</span></span> <span data-ttu-id="2d7d2-180">För ytterligare information och begränsningar som rör bruket av Linux-datorer med en pull-server finns i viktig information för Desired State Configuration för Linux.</span><span class="sxs-lookup"><span data-stu-id="2d7d2-180">For additional information and limitations related to using Linux computers with a pull server, see the Release Notes for Desired State Configuration for Linux.</span></span>

### <a name="working-with-configurations-locally"></a><span data-ttu-id="2d7d2-181">Arbeta med konfigurationer lokalt</span><span class="sxs-lookup"><span data-stu-id="2d7d2-181">Working with configurations locally</span></span>

<span data-ttu-id="2d7d2-182">DSC för Linux innehåller skript för att arbeta med konfigurationen från den lokala Linux-datorn.</span><span class="sxs-lookup"><span data-stu-id="2d7d2-182">DSC for Linux includes scripts to work with configuration from the local Linux computer.</span></span> <span data-ttu-id="2d7d2-183">Dessa skript hitta i `/opt/microsoft/dsc/Scripts` och inkluderar följande:</span><span class="sxs-lookup"><span data-stu-id="2d7d2-183">These scripts are locate in `/opt/microsoft/dsc/Scripts` and include the following:</span></span>
* <span data-ttu-id="2d7d2-184">GetDscConfiguration.py</span><span class="sxs-lookup"><span data-stu-id="2d7d2-184">GetDscConfiguration.py</span></span>

 <span data-ttu-id="2d7d2-185">Returnerar den aktuella konfigurationen som används på datorn.</span><span class="sxs-lookup"><span data-stu-id="2d7d2-185">Returns the current configuration applied to the computer.</span></span> <span data-ttu-id="2d7d2-186">Liknar Windows PowerShell-cmdleten Get-DscConfiguration cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2d7d2-186">Similar to the Windows PowerShell cmdlet Get-DscConfiguration cmdlet.</span></span>

`# sudo ./GetDscConfiguration.py`

* <span data-ttu-id="2d7d2-187">GetDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="2d7d2-187">GetDscLocalConfigurationManager.py</span></span>

 <span data-ttu-id="2d7d2-188">Returnerar den aktuella meta-konfigurationen används på datorn.</span><span class="sxs-lookup"><span data-stu-id="2d7d2-188">Returns the current meta-configuration applied to the computer.</span></span> <span data-ttu-id="2d7d2-189">Liknar cmdlet [Get-DSCLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2d7d2-189">Similar to the cmdlet [Get-DSCLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx) cmdlet.</span></span>

`# sudo ./GetDscLocalConfigurationManager.py`

* <span data-ttu-id="2d7d2-190">InstallModule.py</span><span class="sxs-lookup"><span data-stu-id="2d7d2-190">InstallModule.py</span></span>

 <span data-ttu-id="2d7d2-191">Installerar en anpassad modul för DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="2d7d2-191">Installs a custom DSC resource module.</span></span> <span data-ttu-id="2d7d2-192">Kräver sökvägen till en ZIP-fil som innehåller modulen delade objektbiblioteket och schemat MOF-filer.</span><span class="sxs-lookup"><span data-stu-id="2d7d2-192">Requires the path to a .zip file containing the module shared object library and schema MOF files.</span></span>

`# sudo ./InstallModule.py /tmp/cnx_Resource.zip`

* <span data-ttu-id="2d7d2-193">RemoveModule.py</span><span class="sxs-lookup"><span data-stu-id="2d7d2-193">RemoveModule.py</span></span>

 <span data-ttu-id="2d7d2-194">Tar bort en anpassad modul för DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="2d7d2-194">Removes a custom DSC resource module.</span></span> <span data-ttu-id="2d7d2-195">Du måste ange namn på modulen som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="2d7d2-195">Requires the name of the module to remove.</span></span>

`# sudo ./RemoveModule.py cnx_Resource`

* <span data-ttu-id="2d7d2-196">StartDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="2d7d2-196">StartDscLocalConfigurationManager.py</span></span>

 <span data-ttu-id="2d7d2-197">Gäller en konfiguration MOF-filen till datorn.</span><span class="sxs-lookup"><span data-stu-id="2d7d2-197">Applies a configuration MOF file to the computer.</span></span> <span data-ttu-id="2d7d2-198">Liknar den [Start DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2d7d2-198">Similar to the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet.</span></span> <span data-ttu-id="2d7d2-199">Kräver sökväg till MOF att tillämpa konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="2d7d2-199">Requires the path to the configuration MOF to apply.</span></span>

`# sudo ./StartDscLocalConfigurationManager.py –configurationmof /tmp/localhost.mof`

* <span data-ttu-id="2d7d2-200">SetDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="2d7d2-200">SetDscLocalConfigurationManager.py</span></span>

 <span data-ttu-id="2d7d2-201">Gäller en Meta Configuration MOF-filen till datorn.</span><span class="sxs-lookup"><span data-stu-id="2d7d2-201">Applies a Meta Configuration MOF file to the computer.</span></span> <span data-ttu-id="2d7d2-202">Liknar den [Set DSCLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2d7d2-202">Similar to the [Set-DSCLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx) cmdlet.</span></span> <span data-ttu-id="2d7d2-203">Kräver sökväg till MOF Meta konfigurationen ska tillämpas.</span><span class="sxs-lookup"><span data-stu-id="2d7d2-203">Requires the path to the Meta Configuration MOF to apply.</span></span>

`# sudo ./SetDscLocalConfigurationManager.py –configurationmof /tmp/localhost.meta.mof`

## <a name="powershell-desired-state-configuration-for-linux-log-files"></a><span data-ttu-id="2d7d2-204">PowerShell önskad Tillståndskonfiguration för Linux-loggfiler</span><span class="sxs-lookup"><span data-stu-id="2d7d2-204">PowerShell Desired State Configuration for Linux Log Files</span></span>

<span data-ttu-id="2d7d2-205">Följande loggfiler genereras för DSC för Linux-meddelanden.</span><span class="sxs-lookup"><span data-stu-id="2d7d2-205">The following log files are generated for DSC for Linux messages.</span></span>

|<span data-ttu-id="2d7d2-206">Loggfil</span><span class="sxs-lookup"><span data-stu-id="2d7d2-206">Log file</span></span>|<span data-ttu-id="2d7d2-207">Katalog</span><span class="sxs-lookup"><span data-stu-id="2d7d2-207">Directory</span></span>|<span data-ttu-id="2d7d2-208">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="2d7d2-208">Description</span></span>|
|---|---|---|
|<span data-ttu-id="2d7d2-209">omiserver.log</span><span class="sxs-lookup"><span data-stu-id="2d7d2-209">omiserver.log</span></span>|<span data-ttu-id="2d7d2-210">/var/OPT/omi/log</span><span class="sxs-lookup"><span data-stu-id="2d7d2-210">/var/opt/omi/log</span></span>|<span data-ttu-id="2d7d2-211">Meddelanden om driften av OMI CIM-servern.</span><span class="sxs-lookup"><span data-stu-id="2d7d2-211">Messages relating to the operation of the OMI CIM server.</span></span>|
|<span data-ttu-id="2d7d2-212">DSC.log</span><span class="sxs-lookup"><span data-stu-id="2d7d2-212">dsc.log</span></span>|<span data-ttu-id="2d7d2-213">/var/OPT/omi/log</span><span class="sxs-lookup"><span data-stu-id="2d7d2-213">/var/opt/omi/log</span></span>|<span data-ttu-id="2d7d2-214">Meddelanden om åtgärden med de lokala Configuration Manager (MGM) och DSC resurs.</span><span class="sxs-lookup"><span data-stu-id="2d7d2-214">Messages relating to the operation of the Local Configuration Manager (LCM) and DSC resource operations.</span></span>|