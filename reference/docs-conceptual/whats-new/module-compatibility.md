---
title: PowerShell 7-modulens kompatibilitet
ms.date: 02/03/2020
ms.openlocfilehash: 1f7a2f4fa04e07b8f56635d0a39e580924ae0134
ms.sourcegitcommit: d34841a44742af1123da007fefbdc24a2f1762dd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/07/2020
ms.locfileid: "78926201"
---
# <a name="powershell-7-module-compatibility"></a><span data-ttu-id="c9f3e-102">PowerShell 7-modulens kompatibilitet</span><span class="sxs-lookup"><span data-stu-id="c9f3e-102">PowerShell 7 module compatibility</span></span>

<span data-ttu-id="c9f3e-103">Den här artikeln innehåller en lista med PowerShell-moduler som publicerats av Microsoft och som ger hantering och stöd för olika Microsoft-produkter och-tjänster.</span><span class="sxs-lookup"><span data-stu-id="c9f3e-103">This article contains a list of PowerShell modules published by Microsoft that provide management and support for various Microsoft products and services.</span></span> <span data-ttu-id="c9f3e-104">Dessa moduler har uppdaterats för att fungera internt med PowerShell 7 eller testas för kompatibilitet med PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="c9f3e-104">These modules have been updated to work natively with PowerShell 7 or tested for compatibility with PowerShell 7.</span></span>

<span data-ttu-id="c9f3e-105">Den här listan kommer att uppdateras med ny information när fler moduler identifieras och testas.</span><span class="sxs-lookup"><span data-stu-id="c9f3e-105">This list will be updated with new information as more modules are identified and tested.</span></span> <span data-ttu-id="c9f3e-106">Om du har information om att dela eller problem med specifika moduler, så kan du skicka ett problem i [WindowsCompatibility](https://github.com/PowerShell/WindowsCompatibility) -lagringsplatsen.</span><span class="sxs-lookup"><span data-stu-id="c9f3e-106">If you have information to share or issues with specific modules, please file an issue in the [WindowsCompatibility](https://github.com/PowerShell/WindowsCompatibility) repository.</span></span>

## <a name="windows-management-modules"></a><span data-ttu-id="c9f3e-107">Windows Management-moduler</span><span class="sxs-lookup"><span data-stu-id="c9f3e-107">Windows management modules</span></span>

<span data-ttu-id="c9f3e-108">Windows Management-modulerna installeras på olika sätt beroende på vilken typ av Windows och hur modulen paketerades.</span><span class="sxs-lookup"><span data-stu-id="c9f3e-108">The Windows management modules are installed in different ways depending on the type of Windows and how the module was packaged.</span></span> <span data-ttu-id="c9f3e-109">Dessa moduler måste installeras från en utökad PowerShell-session med alternativet **Kör som administratör** .</span><span class="sxs-lookup"><span data-stu-id="c9f3e-109">These modules must be installed from an elevate PowerShell session using the **Run as administrator** option.</span></span>

<span data-ttu-id="c9f3e-110">På Windows Server använder du funktions namnet med [Install-WindowsFeature](/powershell/module/servermanager/install-windowsfeature) för att installera modulen.</span><span class="sxs-lookup"><span data-stu-id="c9f3e-110">On Windows Server, use the feature name with the [Install-WindowsFeature](/powershell/module/servermanager/install-windowsfeature) to install the module.</span></span> <span data-ttu-id="c9f3e-111">Exempel:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-111">For example:</span></span>

```powershell
Install-WindowsFeature -Name ActiveDirectory
```

<span data-ttu-id="c9f3e-112">I Windows 10 måste du använda en av dessa cmdlets, beroende på paket typen:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-112">On Windows 10, you have to use one of these cmdlets depending the package type:</span></span>
- [<span data-ttu-id="c9f3e-113">Aktivera – WindowsOptionalFeature</span><span class="sxs-lookup"><span data-stu-id="c9f3e-113">Enable-WindowsOptionalFeature</span></span>](/powershell/module/dism/enable-windowsoptionalfeature)
- [<span data-ttu-id="c9f3e-114">Add-WindowsCapability</span><span class="sxs-lookup"><span data-stu-id="c9f3e-114">Add-WindowsCapability</span></span>](/powershell/module/dism/add-windowscapability)

<span data-ttu-id="c9f3e-115">För moduler som installeras som Windows-funktioner:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-115">For modules that install as Windows Features:</span></span>

```powershell
Enable-WindowsOptionalFeature -Online -FeatureName FooFeatureName
```

<span data-ttu-id="c9f3e-116">För moduler som installeras som Windows-funktioner måste du lägga till `~~~~0.0.1.0` i slutet av paket namnet.</span><span class="sxs-lookup"><span data-stu-id="c9f3e-116">For modules that install as Windows Capabilities, you have to append `~~~~0.0.1.0` to the end of the package name.</span></span> <span data-ttu-id="c9f3e-117">Exempel:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-117">For example:</span></span>

```powershell
Add-WindowsCapability -Online -Name Rsat.ServerManager.Tools~~~~0.0.1.0
```

### <a name="activedirectory"></a><span data-ttu-id="c9f3e-118">ActiveDirectory</span><span class="sxs-lookup"><span data-stu-id="c9f3e-118">ActiveDirectory</span></span>

<span data-ttu-id="c9f3e-119">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-119">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-120">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-120">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-121">Server version: 1809 + med RSAT-AD-PowerShell</span><span class="sxs-lookup"><span data-stu-id="c9f3e-121">Server version: 1809+ with RSAT-AD-PowerShell</span></span>
- <span data-ttu-id="c9f3e-122">Windows 10-version: 1809 + med RSAT. ActiveDirectory. DS-LDS. tools</span><span class="sxs-lookup"><span data-stu-id="c9f3e-122">Windows 10 version: 1809+ with Rsat.ActiveDirectory.DS-LDS.Tools</span></span>

### <a name="adfs"></a><span data-ttu-id="c9f3e-123">ADFS</span><span class="sxs-lookup"><span data-stu-id="c9f3e-123">ADFS</span></span>

<span data-ttu-id="c9f3e-124">Status: avtestat med kompatibilitetsläge</span><span class="sxs-lookup"><span data-stu-id="c9f3e-124">Status: Untested with Compatibility Layer</span></span>

### <a name="appbackgroundtask"></a><span data-ttu-id="c9f3e-125">AppBackgroundTask</span><span class="sxs-lookup"><span data-stu-id="c9f3e-125">AppBackgroundTask</span></span>

<span data-ttu-id="c9f3e-126">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-126">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-127">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-127">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-128">Windows 10-version: 1903 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-128">Windows 10 version: 1903+</span></span>

### <a name="applocker"></a><span data-ttu-id="c9f3e-129">AppLocker</span><span class="sxs-lookup"><span data-stu-id="c9f3e-129">AppLocker</span></span>

<span data-ttu-id="c9f3e-130">Status: avtestat med kompatibilitetsläge</span><span class="sxs-lookup"><span data-stu-id="c9f3e-130">Status: Untested with Compatibility Layer</span></span>

### <a name="appvclient"></a><span data-ttu-id="c9f3e-131">AppvClient</span><span class="sxs-lookup"><span data-stu-id="c9f3e-131">AppvClient</span></span>

<span data-ttu-id="c9f3e-132">Status: avtestat med kompatibilitetsläge</span><span class="sxs-lookup"><span data-stu-id="c9f3e-132">Status: Untested with Compatibility Layer</span></span>

### <a name="appx"></a><span data-ttu-id="c9f3e-133">Appx</span><span class="sxs-lookup"><span data-stu-id="c9f3e-133">Appx</span></span>

<span data-ttu-id="c9f3e-134">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-134">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-135">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-135">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-136">Server version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-136">Server version: 1809+</span></span>
- <span data-ttu-id="c9f3e-137">Windows 10-version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-137">Windows 10 version: 1809+</span></span>

### <a name="assignedaccess"></a><span data-ttu-id="c9f3e-138">AssignedAccess</span><span class="sxs-lookup"><span data-stu-id="c9f3e-138">AssignedAccess</span></span>

<span data-ttu-id="c9f3e-139">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-139">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-140">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-140">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-141">Windows 10-version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-141">Windows 10 version: 1809+</span></span>

### <a name="bestpractices"></a><span data-ttu-id="c9f3e-142">BestPractices</span><span class="sxs-lookup"><span data-stu-id="c9f3e-142">BestPractices</span></span>

<span data-ttu-id="c9f3e-143">Status: avtestat med kompatibilitetsläge</span><span class="sxs-lookup"><span data-stu-id="c9f3e-143">Status: Untested with Compatibility Layer</span></span>

### <a name="bitlocker"></a><span data-ttu-id="c9f3e-144">BitLocker</span><span class="sxs-lookup"><span data-stu-id="c9f3e-144">BitLocker</span></span>

<span data-ttu-id="c9f3e-145">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-145">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-146">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-146">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-147">Server version: 1809 + med BitLocker</span><span class="sxs-lookup"><span data-stu-id="c9f3e-147">Server version: 1809+ with BitLocker</span></span>
- <span data-ttu-id="c9f3e-148">Windows 10-version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-148">Windows 10 version: 1809+</span></span>

### <a name="bitstransfer"></a><span data-ttu-id="c9f3e-149">BitsTransfer</span><span class="sxs-lookup"><span data-stu-id="c9f3e-149">BitsTransfer</span></span>

<span data-ttu-id="c9f3e-150">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-150">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-151">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-151">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-152">Server version: 20H1</span><span class="sxs-lookup"><span data-stu-id="c9f3e-152">Server version: 20H1</span></span>
- <span data-ttu-id="c9f3e-153">Windows 10-version: 20H1</span><span class="sxs-lookup"><span data-stu-id="c9f3e-153">Windows 10 version: 20H1</span></span>

### <a name="booteventcollector"></a><span data-ttu-id="c9f3e-154">BootEventCollector</span><span class="sxs-lookup"><span data-stu-id="c9f3e-154">BootEventCollector</span></span>

<span data-ttu-id="c9f3e-155">Status: avtestat med kompatibilitetsläge</span><span class="sxs-lookup"><span data-stu-id="c9f3e-155">Status: Untested with Compatibility Layer</span></span>

### <a name="branchcache"></a><span data-ttu-id="c9f3e-156">BranchCache</span><span class="sxs-lookup"><span data-stu-id="c9f3e-156">BranchCache</span></span>

<span data-ttu-id="c9f3e-157">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-157">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-158">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-158">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-159">Server version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-159">Server version: 1809+</span></span>
- <span data-ttu-id="c9f3e-160">Windows 10-version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-160">Windows 10 version: 1809+</span></span>

### <a name="cimcmdlets"></a><span data-ttu-id="c9f3e-161">CimCmdlets</span><span class="sxs-lookup"><span data-stu-id="c9f3e-161">CimCmdlets</span></span>

<span data-ttu-id="c9f3e-162">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-162">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-163">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-163">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-164">Inbyggd i PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="c9f3e-164">Built into PowerShell 7</span></span>

### <a name="clusterawareupdating"></a><span data-ttu-id="c9f3e-165">ClusterAwareUpdating</span><span class="sxs-lookup"><span data-stu-id="c9f3e-165">ClusterAwareUpdating</span></span>

<span data-ttu-id="c9f3e-166">Status: avtestat med kompatibilitetsläge</span><span class="sxs-lookup"><span data-stu-id="c9f3e-166">Status: Untested with Compatibility Layer</span></span>

### <a name="configci"></a><span data-ttu-id="c9f3e-167">ConfigCI</span><span class="sxs-lookup"><span data-stu-id="c9f3e-167">ConfigCI</span></span>

<span data-ttu-id="c9f3e-168">Status: avtestat med kompatibilitetsläge</span><span class="sxs-lookup"><span data-stu-id="c9f3e-168">Status: Untested with Compatibility Layer</span></span>

### <a name="defender"></a><span data-ttu-id="c9f3e-169">Defender</span><span class="sxs-lookup"><span data-stu-id="c9f3e-169">Defender</span></span>

<span data-ttu-id="c9f3e-170">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-170">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-171">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-171">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-172">Server version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-172">Server version: 1809+</span></span>
- <span data-ttu-id="c9f3e-173">Windows 10-version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-173">Windows 10 version: 1809+</span></span>

### <a name="deliveryoptimization"></a><span data-ttu-id="c9f3e-174">DeliveryOptimization</span><span class="sxs-lookup"><span data-stu-id="c9f3e-174">DeliveryOptimization</span></span>

<span data-ttu-id="c9f3e-175">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-175">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-176">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-176">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-177">Server version: 1903 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-177">Server version: 1903+</span></span>
- <span data-ttu-id="c9f3e-178">Windows 10-version: 1903 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-178">Windows 10 version: 1903+</span></span>

### <a name="dfsn"></a><span data-ttu-id="c9f3e-179">DFSN</span><span class="sxs-lookup"><span data-stu-id="c9f3e-179">DFSN</span></span>

<span data-ttu-id="c9f3e-180">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-180">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-181">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-181">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-182">Server version: 1809 + med FS-DFS-namnrymd</span><span class="sxs-lookup"><span data-stu-id="c9f3e-182">Server version: 1809+ with FS-DFS-Namespace</span></span>
- <span data-ttu-id="c9f3e-183">Windows 10-version: 1809 + med RSAT. FailoverCluster. Management. tools</span><span class="sxs-lookup"><span data-stu-id="c9f3e-183">Windows 10 version: 1809+ with Rsat.FailoverCluster.Management.Tools</span></span>

### <a name="dfsr"></a><span data-ttu-id="c9f3e-184">DFSR</span><span class="sxs-lookup"><span data-stu-id="c9f3e-184">DFSR</span></span>

<span data-ttu-id="c9f3e-185">Status: avtestat med kompatibilitetsläge</span><span class="sxs-lookup"><span data-stu-id="c9f3e-185">Status: Untested with Compatibility Layer</span></span>

### <a name="dhcpserver"></a><span data-ttu-id="c9f3e-186">Server</span><span class="sxs-lookup"><span data-stu-id="c9f3e-186">DhcpServer</span></span>

<span data-ttu-id="c9f3e-187">Status: avtestat med kompatibilitetsläge</span><span class="sxs-lookup"><span data-stu-id="c9f3e-187">Status: Untested with Compatibility Layer</span></span>

### <a name="directaccessclientcomponents"></a><span data-ttu-id="c9f3e-188">DirectAccessClientComponents</span><span class="sxs-lookup"><span data-stu-id="c9f3e-188">DirectAccessClientComponents</span></span>

<span data-ttu-id="c9f3e-189">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-189">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-190">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-190">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-191">Server version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-191">Server version: 1809+</span></span>
- <span data-ttu-id="c9f3e-192">Windows 10-version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-192">Windows 10 version: 1809+</span></span>

### <a name="dism"></a><span data-ttu-id="c9f3e-193">Kommandoradssyntax</span><span class="sxs-lookup"><span data-stu-id="c9f3e-193">Dism</span></span>

<span data-ttu-id="c9f3e-194">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-194">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-195">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-195">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-196">Server version: 1903 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-196">Server version: 1903+</span></span>
- <span data-ttu-id="c9f3e-197">Windows 10-version: 1903 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-197">Windows 10 version: 1903+</span></span>

### <a name="dnsclient"></a><span data-ttu-id="c9f3e-198">DnsClient</span><span class="sxs-lookup"><span data-stu-id="c9f3e-198">DnsClient</span></span>

<span data-ttu-id="c9f3e-199">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-199">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-200">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-200">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-201">Server version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-201">Server version: 1809+</span></span>
- <span data-ttu-id="c9f3e-202">Windows 10-version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-202">Windows 10 version: 1809+</span></span>

### <a name="dnsserver"></a><span data-ttu-id="c9f3e-203">DnsServer</span><span class="sxs-lookup"><span data-stu-id="c9f3e-203">DnsServer</span></span>

<span data-ttu-id="c9f3e-204">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-204">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-205">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-205">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-206">Server version: 1809 + med DNS eller RSAT-DNS-Server</span><span class="sxs-lookup"><span data-stu-id="c9f3e-206">Server version: 1809+ with DNS or RSAT-DNS-Server</span></span>
- <span data-ttu-id="c9f3e-207">Windows 10-version: 1809 + med RSAT. DNS. tools</span><span class="sxs-lookup"><span data-stu-id="c9f3e-207">Windows 10 version: 1809+ with Rsat.Dns.Tools</span></span>

### <a name="eventtracingmanagement"></a><span data-ttu-id="c9f3e-208">EventTracingManagement</span><span class="sxs-lookup"><span data-stu-id="c9f3e-208">EventTracingManagement</span></span>

<span data-ttu-id="c9f3e-209">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-209">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-210">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-210">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-211">Server version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-211">Server version: 1809+</span></span>
- <span data-ttu-id="c9f3e-212">Windows 10-version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-212">Windows 10 version: 1809+</span></span>

### <a name="failoverclusters"></a><span data-ttu-id="c9f3e-213">FailoverClusters</span><span class="sxs-lookup"><span data-stu-id="c9f3e-213">FailoverClusters</span></span>

<span data-ttu-id="c9f3e-214">Status: avtestat med kompatibilitetsläge</span><span class="sxs-lookup"><span data-stu-id="c9f3e-214">Status: Untested with Compatibility Layer</span></span>

### <a name="failoverclusterset"></a><span data-ttu-id="c9f3e-215">FailoverClusterSet</span><span class="sxs-lookup"><span data-stu-id="c9f3e-215">FailoverClusterSet</span></span>

<span data-ttu-id="c9f3e-216">Status: avtestat med kompatibilitetsläge</span><span class="sxs-lookup"><span data-stu-id="c9f3e-216">Status: Untested with Compatibility Layer</span></span>

### <a name="fileserverresourcemanager"></a><span data-ttu-id="c9f3e-217">FileServerResourceManager</span><span class="sxs-lookup"><span data-stu-id="c9f3e-217">FileServerResourceManager</span></span>

<span data-ttu-id="c9f3e-218">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-218">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-219">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-219">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-220">Server version: 1809 + med FS – Resource Manager</span><span class="sxs-lookup"><span data-stu-id="c9f3e-220">Server version: 1809+ with FS-Resource-Manager</span></span>

### <a name="grouppolicy"></a><span data-ttu-id="c9f3e-221">GroupPolicy</span><span class="sxs-lookup"><span data-stu-id="c9f3e-221">GroupPolicy</span></span>

<span data-ttu-id="c9f3e-222">Status: avtestat med kompatibilitetsläge</span><span class="sxs-lookup"><span data-stu-id="c9f3e-222">Status: Untested with Compatibility Layer</span></span>

### <a name="hgsclient"></a><span data-ttu-id="c9f3e-223">HgsClient</span><span class="sxs-lookup"><span data-stu-id="c9f3e-223">HgsClient</span></span>

<span data-ttu-id="c9f3e-224">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-224">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-225">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-225">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-226">Server version: 1903 + med Hyper-V eller RSAT-skärmad-VM-tools</span><span class="sxs-lookup"><span data-stu-id="c9f3e-226">Server version: 1903+ with Hyper-V or RSAT-Shielded-VM-Tools</span></span>
- <span data-ttu-id="c9f3e-227">Windows 10-version: 1903 + med RSAT. skärmad. VM. tools</span><span class="sxs-lookup"><span data-stu-id="c9f3e-227">Windows 10 version: 1903+ with Rsat.Shielded.VM.Tools</span></span>

### <a name="hgsdiagnostics"></a><span data-ttu-id="c9f3e-228">HgsDiagnostics</span><span class="sxs-lookup"><span data-stu-id="c9f3e-228">HgsDiagnostics</span></span>

<span data-ttu-id="c9f3e-229">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-229">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-230">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-230">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-231">Server version: 1809 + med Hyper-V eller RSAT-skärmad-VM-tools</span><span class="sxs-lookup"><span data-stu-id="c9f3e-231">Server version: 1809+ with Hyper-V or RSAT-Shielded-VM-Tools</span></span>
- <span data-ttu-id="c9f3e-232">Windows 10-version: 1809 + med RSAT. skärmad. VM. tools</span><span class="sxs-lookup"><span data-stu-id="c9f3e-232">Windows 10 version: 1809+ with Rsat.Shielded.VM.Tools</span></span>

### <a name="hyper-v"></a><span data-ttu-id="c9f3e-233">Hyper-V</span><span class="sxs-lookup"><span data-stu-id="c9f3e-233">Hyper-V</span></span>

<span data-ttu-id="c9f3e-234">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-234">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-235">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-235">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-236">Server version: 1809 + med Hyper-V – PowerShell</span><span class="sxs-lookup"><span data-stu-id="c9f3e-236">Server version: 1809+ with Hyper-V-PowerShell</span></span>
- <span data-ttu-id="c9f3e-237">Windows 10-version: 1809 + med Microsoft-Hyper-V-Management – PowerShell</span><span class="sxs-lookup"><span data-stu-id="c9f3e-237">Windows 10 version: 1809+ with Microsoft-Hyper-V-Management-PowerShell</span></span>

### <a name="iisadministration"></a><span data-ttu-id="c9f3e-238">Administrationsmodul</span><span class="sxs-lookup"><span data-stu-id="c9f3e-238">IISAdministration</span></span>

<span data-ttu-id="c9f3e-239">Status: avtestat med kompatibilitetsläge</span><span class="sxs-lookup"><span data-stu-id="c9f3e-239">Status: Untested with Compatibility Layer</span></span>

### <a name="international"></a><span data-ttu-id="c9f3e-240">Standarder</span><span class="sxs-lookup"><span data-stu-id="c9f3e-240">International</span></span>

<span data-ttu-id="c9f3e-241">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-241">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-242">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-242">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-243">Server version: 1903 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-243">Server version: 1903+</span></span>
- <span data-ttu-id="c9f3e-244">Windows 10-version: 1903 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-244">Windows 10 version: 1903+</span></span>

### <a name="ipamserver"></a><span data-ttu-id="c9f3e-245">IpamServer</span><span class="sxs-lookup"><span data-stu-id="c9f3e-245">IpamServer</span></span>

<span data-ttu-id="c9f3e-246">Status: avtestat med kompatibilitetsläge</span><span class="sxs-lookup"><span data-stu-id="c9f3e-246">Status: Untested with Compatibility Layer</span></span>

### <a name="iscsi"></a><span data-ttu-id="c9f3e-247">iSCSI</span><span class="sxs-lookup"><span data-stu-id="c9f3e-247">iSCSI</span></span>

<span data-ttu-id="c9f3e-248">Status: avtestat med kompatibilitetsläge</span><span class="sxs-lookup"><span data-stu-id="c9f3e-248">Status: Untested with Compatibility Layer</span></span>

### <a name="iscsitarget"></a><span data-ttu-id="c9f3e-249">IscsiTarget</span><span class="sxs-lookup"><span data-stu-id="c9f3e-249">IscsiTarget</span></span>

<span data-ttu-id="c9f3e-250">Status: avtestat med kompatibilitetsläge</span><span class="sxs-lookup"><span data-stu-id="c9f3e-250">Status: Untested with Compatibility Layer</span></span>

### <a name="ise"></a><span data-ttu-id="c9f3e-251">ISE</span><span class="sxs-lookup"><span data-stu-id="c9f3e-251">ISE</span></span>

<span data-ttu-id="c9f3e-252">Status: avtestat med kompatibilitetsläge</span><span class="sxs-lookup"><span data-stu-id="c9f3e-252">Status: Untested with Compatibility Layer</span></span>

### <a name="kds"></a><span data-ttu-id="c9f3e-253">KDs</span><span class="sxs-lookup"><span data-stu-id="c9f3e-253">Kds</span></span>

<span data-ttu-id="c9f3e-254">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-254">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-255">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-255">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-256">Server version: 20H1</span><span class="sxs-lookup"><span data-stu-id="c9f3e-256">Server version: 20H1</span></span>
- <span data-ttu-id="c9f3e-257">Windows 10-version: 20H1</span><span class="sxs-lookup"><span data-stu-id="c9f3e-257">Windows 10 version: 20H1</span></span>

### <a name="microsoftpowershellarchive"></a><span data-ttu-id="c9f3e-258">Microsoft. PowerShell. Archive</span><span class="sxs-lookup"><span data-stu-id="c9f3e-258">Microsoft.PowerShell.Archive</span></span>

<span data-ttu-id="c9f3e-259">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-259">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-260">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-260">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-261">Inbyggd i PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="c9f3e-261">Built into PowerShell 7</span></span>

### <a name="microsoftpowershelldiagnostics"></a><span data-ttu-id="c9f3e-262">Microsoft.PowerShell.Diagnostics</span><span class="sxs-lookup"><span data-stu-id="c9f3e-262">Microsoft.PowerShell.Diagnostics</span></span>

<span data-ttu-id="c9f3e-263">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-263">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-264">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-264">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-265">Inbyggd i PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="c9f3e-265">Built into PowerShell 7</span></span>

### <a name="microsoftpowershellhost"></a><span data-ttu-id="c9f3e-266">Microsoft.PowerShell.Host</span><span class="sxs-lookup"><span data-stu-id="c9f3e-266">Microsoft.PowerShell.Host</span></span>

<span data-ttu-id="c9f3e-267">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-267">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-268">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-268">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-269">Inbyggd i PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="c9f3e-269">Built into PowerShell 7</span></span>

### <a name="microsoftpowershelllocalaccounts"></a><span data-ttu-id="c9f3e-270">Microsoft. PowerShell. LocalAccounts</span><span class="sxs-lookup"><span data-stu-id="c9f3e-270">Microsoft.PowerShell.LocalAccounts</span></span>

<span data-ttu-id="c9f3e-271">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-271">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-272">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-272">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-273">Server version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-273">Server version: 1809+</span></span>
- <span data-ttu-id="c9f3e-274">Windows 10-version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-274">Windows 10 version: 1809+</span></span>

### <a name="microsoftpowershellmanagement"></a><span data-ttu-id="c9f3e-275">Microsoft.PowerShell.Management</span><span class="sxs-lookup"><span data-stu-id="c9f3e-275">Microsoft.PowerShell.Management</span></span>

<span data-ttu-id="c9f3e-276">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-276">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-277">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-277">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-278">Inbyggd i PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="c9f3e-278">Built into PowerShell 7</span></span>

### <a name="microsoftpowershellodatautils"></a><span data-ttu-id="c9f3e-279">Microsoft. PowerShell. ODataUtils</span><span class="sxs-lookup"><span data-stu-id="c9f3e-279">Microsoft.PowerShell.ODataUtils</span></span>

<span data-ttu-id="c9f3e-280">Status: avtestat med kompatibilitetsläge</span><span class="sxs-lookup"><span data-stu-id="c9f3e-280">Status: Untested with Compatibility Layer</span></span>

### <a name="microsoftpowershellsecurity"></a><span data-ttu-id="c9f3e-281">Microsoft.PowerShell.Security</span><span class="sxs-lookup"><span data-stu-id="c9f3e-281">Microsoft.PowerShell.Security</span></span>

<span data-ttu-id="c9f3e-282">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-282">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-283">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-283">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-284">Inbyggd i PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="c9f3e-284">Built into PowerShell 7</span></span>

### <a name="microsoftpowershellutility"></a><span data-ttu-id="c9f3e-285">Microsoft.PowerShell.Utility</span><span class="sxs-lookup"><span data-stu-id="c9f3e-285">Microsoft.PowerShell.Utility</span></span>

<span data-ttu-id="c9f3e-286">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-286">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-287">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-287">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-288">Inbyggd i PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="c9f3e-288">Built into PowerShell 7</span></span>

### <a name="microsoftwsmanmanagement"></a><span data-ttu-id="c9f3e-289">Microsoft.WSMan.Management</span><span class="sxs-lookup"><span data-stu-id="c9f3e-289">Microsoft.WSMan.Management</span></span>

<span data-ttu-id="c9f3e-290">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-290">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-291">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-291">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-292">Inbyggd i PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="c9f3e-292">Built into PowerShell 7</span></span>

### <a name="mmagent"></a><span data-ttu-id="c9f3e-293">MMAgent</span><span class="sxs-lookup"><span data-stu-id="c9f3e-293">MMAgent</span></span>

<span data-ttu-id="c9f3e-294">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-294">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-295">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-295">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-296">Server version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-296">Server version: 1809+</span></span>
- <span data-ttu-id="c9f3e-297">Windows 10-version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-297">Windows 10 version: 1809+</span></span>

### <a name="mpio"></a><span data-ttu-id="c9f3e-298">MPIO</span><span class="sxs-lookup"><span data-stu-id="c9f3e-298">MPIO</span></span>

<span data-ttu-id="c9f3e-299">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-299">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-300">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-300">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-301">Server version: 1809 + med multipath-IO</span><span class="sxs-lookup"><span data-stu-id="c9f3e-301">Server version: 1809+ with Multipath-IO</span></span>

### <a name="msdtc"></a><span data-ttu-id="c9f3e-302">MsDtc</span><span class="sxs-lookup"><span data-stu-id="c9f3e-302">MsDtc</span></span>

<span data-ttu-id="c9f3e-303">Status: avtestat med kompatibilitetsläge</span><span class="sxs-lookup"><span data-stu-id="c9f3e-303">Status: Untested with Compatibility Layer</span></span>

### <a name="netadapter"></a><span data-ttu-id="c9f3e-304">NetAdapter</span><span class="sxs-lookup"><span data-stu-id="c9f3e-304">NetAdapter</span></span>

<span data-ttu-id="c9f3e-305">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-305">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-306">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-306">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-307">Server version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-307">Server version: 1809+</span></span>
- <span data-ttu-id="c9f3e-308">Windows 10-version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-308">Windows 10 version: 1809+</span></span>

### <a name="netconnection"></a><span data-ttu-id="c9f3e-309">NetConnection</span><span class="sxs-lookup"><span data-stu-id="c9f3e-309">NetConnection</span></span>

<span data-ttu-id="c9f3e-310">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-310">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-311">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-311">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-312">Server version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-312">Server version: 1809+</span></span>
- <span data-ttu-id="c9f3e-313">Windows 10-version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-313">Windows 10 version: 1809+</span></span>

### <a name="neteventpacketcapture"></a><span data-ttu-id="c9f3e-314">NetEventPacketCapture</span><span class="sxs-lookup"><span data-stu-id="c9f3e-314">NetEventPacketCapture</span></span>

<span data-ttu-id="c9f3e-315">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-315">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-316">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-316">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-317">Server version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-317">Server version: 1809+</span></span>
- <span data-ttu-id="c9f3e-318">Windows 10-version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-318">Windows 10 version: 1809+</span></span>

### <a name="netlbfo"></a><span data-ttu-id="c9f3e-319">NetLbfo</span><span class="sxs-lookup"><span data-stu-id="c9f3e-319">NetLbfo</span></span>

<span data-ttu-id="c9f3e-320">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-320">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-321">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-321">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-322">Server version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-322">Server version: 1809+</span></span>
- <span data-ttu-id="c9f3e-323">Windows 10-version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-323">Windows 10 version: 1809+</span></span>

### <a name="netlldpagent"></a><span data-ttu-id="c9f3e-324">NetLldpAgent</span><span class="sxs-lookup"><span data-stu-id="c9f3e-324">NetLldpAgent</span></span>

<span data-ttu-id="c9f3e-325">Status: avtestat med kompatibilitetsläge</span><span class="sxs-lookup"><span data-stu-id="c9f3e-325">Status: Untested with Compatibility Layer</span></span>

### <a name="netnat"></a><span data-ttu-id="c9f3e-326">NetNat</span><span class="sxs-lookup"><span data-stu-id="c9f3e-326">NetNat</span></span>

<span data-ttu-id="c9f3e-327">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-327">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-328">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-328">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-329">Server version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-329">Server version: 1809+</span></span>
- <span data-ttu-id="c9f3e-330">Windows 10-version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-330">Windows 10 version: 1809+</span></span>

### <a name="netqos"></a><span data-ttu-id="c9f3e-331">NetQos</span><span class="sxs-lookup"><span data-stu-id="c9f3e-331">NetQos</span></span>

<span data-ttu-id="c9f3e-332">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-332">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-333">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-333">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-334">Server version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-334">Server version: 1809+</span></span>
- <span data-ttu-id="c9f3e-335">Windows 10-version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-335">Windows 10 version: 1809+</span></span>

### <a name="netsecurity"></a><span data-ttu-id="c9f3e-336">Netsäkerhet</span><span class="sxs-lookup"><span data-stu-id="c9f3e-336">NetSecurity</span></span>

<span data-ttu-id="c9f3e-337">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-337">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-338">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-338">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-339">Server version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-339">Server version: 1809+</span></span>
- <span data-ttu-id="c9f3e-340">Windows 10-version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-340">Windows 10 version: 1809+</span></span>

### <a name="netswitchteam"></a><span data-ttu-id="c9f3e-341">NetSwitchTeam</span><span class="sxs-lookup"><span data-stu-id="c9f3e-341">NetSwitchTeam</span></span>

<span data-ttu-id="c9f3e-342">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-342">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-343">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-343">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-344">Server version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-344">Server version: 1809+</span></span>
- <span data-ttu-id="c9f3e-345">Windows 10-version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-345">Windows 10 version: 1809+</span></span>

### <a name="nettcpip"></a><span data-ttu-id="c9f3e-346">Nettcpip</span><span class="sxs-lookup"><span data-stu-id="c9f3e-346">NetTCPIP</span></span>

<span data-ttu-id="c9f3e-347">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-347">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-348">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-348">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-349">Server version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-349">Server version: 1809+</span></span>
- <span data-ttu-id="c9f3e-350">Windows 10-version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-350">Windows 10 version: 1809+</span></span>

### <a name="netwnv"></a><span data-ttu-id="c9f3e-351">NetWNV</span><span class="sxs-lookup"><span data-stu-id="c9f3e-351">NetWNV</span></span>

<span data-ttu-id="c9f3e-352">Status: avtestat med kompatibilitetsläge</span><span class="sxs-lookup"><span data-stu-id="c9f3e-352">Status: Untested with Compatibility Layer</span></span>

### <a name="networkconnectivitystatus"></a><span data-ttu-id="c9f3e-353">NetworkConnectivityStatus</span><span class="sxs-lookup"><span data-stu-id="c9f3e-353">NetworkConnectivityStatus</span></span>

<span data-ttu-id="c9f3e-354">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-354">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-355">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-355">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-356">Server version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-356">Server version: 1809+</span></span>
- <span data-ttu-id="c9f3e-357">Windows 10-version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-357">Windows 10 version: 1809+</span></span>

### <a name="networkcontroller"></a><span data-ttu-id="c9f3e-358">NetworkController</span><span class="sxs-lookup"><span data-stu-id="c9f3e-358">NetworkController</span></span>

<span data-ttu-id="c9f3e-359">Status: avtestat med kompatibilitetsläge</span><span class="sxs-lookup"><span data-stu-id="c9f3e-359">Status: Untested with Compatibility Layer</span></span>

### <a name="networkcontrollerdiagnostics"></a><span data-ttu-id="c9f3e-360">NetworkControllerDiagnostics</span><span class="sxs-lookup"><span data-stu-id="c9f3e-360">NetworkControllerDiagnostics</span></span>

<span data-ttu-id="c9f3e-361">Status: avtestat med kompatibilitetsläge</span><span class="sxs-lookup"><span data-stu-id="c9f3e-361">Status: Untested with Compatibility Layer</span></span>

### <a name="networkloadbalancingclusters"></a><span data-ttu-id="c9f3e-362">NetworkLoadBalancingClusters</span><span class="sxs-lookup"><span data-stu-id="c9f3e-362">NetworkLoadBalancingClusters</span></span>

<span data-ttu-id="c9f3e-363">Status: avtestat med kompatibilitetsläge</span><span class="sxs-lookup"><span data-stu-id="c9f3e-363">Status: Untested with Compatibility Layer</span></span>

### <a name="networkswitchmanager"></a><span data-ttu-id="c9f3e-364">NetworkSwitchManager</span><span class="sxs-lookup"><span data-stu-id="c9f3e-364">NetworkSwitchManager</span></span>

<span data-ttu-id="c9f3e-365">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-365">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-366">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-366">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-367">Server version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-367">Server version: 1809+</span></span>
- <span data-ttu-id="c9f3e-368">Windows 10-version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-368">Windows 10 version: 1809+</span></span>

### <a name="networktransition"></a><span data-ttu-id="c9f3e-369">NetworkTransition</span><span class="sxs-lookup"><span data-stu-id="c9f3e-369">NetworkTransition</span></span>

<span data-ttu-id="c9f3e-370">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-370">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-371">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-371">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-372">Server version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-372">Server version: 1809+</span></span>
- <span data-ttu-id="c9f3e-373">Windows 10-version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-373">Windows 10 version: 1809+</span></span>

### <a name="nfs"></a><span data-ttu-id="c9f3e-374">NFS</span><span class="sxs-lookup"><span data-stu-id="c9f3e-374">NFS</span></span>

<span data-ttu-id="c9f3e-375">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-375">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-376">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-376">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-377">Server version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-377">Server version: 1809+</span></span>
- <span data-ttu-id="c9f3e-378">Windows 10-version: 1809 + med RSAT. ServerManager. tools</span><span class="sxs-lookup"><span data-stu-id="c9f3e-378">Windows 10 version: 1809+ with Rsat.ServerManager.Tools</span></span>

### <a name="packagemanagement"></a><span data-ttu-id="c9f3e-379">PackageManagement</span><span class="sxs-lookup"><span data-stu-id="c9f3e-379">PackageManagement</span></span>

<span data-ttu-id="c9f3e-380">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-380">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-381">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-381">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-382">Inbyggd i PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="c9f3e-382">Built into PowerShell 7</span></span>

### <a name="pcsvdevice"></a><span data-ttu-id="c9f3e-383">PcsvDevice</span><span class="sxs-lookup"><span data-stu-id="c9f3e-383">PcsvDevice</span></span>

<span data-ttu-id="c9f3e-384">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-384">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-385">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-385">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-386">Server version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-386">Server version: 1809+</span></span>
- <span data-ttu-id="c9f3e-387">Windows 10-version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-387">Windows 10 version: 1809+</span></span>

### <a name="persistentmemory"></a><span data-ttu-id="c9f3e-388">PersistentMemory</span><span class="sxs-lookup"><span data-stu-id="c9f3e-388">PersistentMemory</span></span>

<span data-ttu-id="c9f3e-389">Status: avtestat med kompatibilitetsläge</span><span class="sxs-lookup"><span data-stu-id="c9f3e-389">Status: Untested with Compatibility Layer</span></span>

### <a name="pki"></a><span data-ttu-id="c9f3e-390">PKI</span><span class="sxs-lookup"><span data-stu-id="c9f3e-390">PKI</span></span>

<span data-ttu-id="c9f3e-391">Status: avtestat med kompatibilitetsläge</span><span class="sxs-lookup"><span data-stu-id="c9f3e-391">Status: Untested with Compatibility Layer</span></span>

### <a name="pnpdevice"></a><span data-ttu-id="c9f3e-392">PnpDevice</span><span class="sxs-lookup"><span data-stu-id="c9f3e-392">PnpDevice</span></span>

<span data-ttu-id="c9f3e-393">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-393">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-394">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-394">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-395">Server version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-395">Server version: 1809+</span></span>
- <span data-ttu-id="c9f3e-396">Windows 10-version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-396">Windows 10 version: 1809+</span></span>

### <a name="powershellget"></a><span data-ttu-id="c9f3e-397">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="c9f3e-397">PowerShellGet</span></span>

<span data-ttu-id="c9f3e-398">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-398">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-399">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-399">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-400">Inbyggd i PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="c9f3e-400">Built into PowerShell 7</span></span>

### <a name="printmanagement"></a><span data-ttu-id="c9f3e-401">PrintManagement</span><span class="sxs-lookup"><span data-stu-id="c9f3e-401">PrintManagement</span></span>

<span data-ttu-id="c9f3e-402">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-402">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-403">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-403">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-404">Server version: 1903 + med utskrifts tjänster</span><span class="sxs-lookup"><span data-stu-id="c9f3e-404">Server version: 1903+ with Print-Services</span></span>
- <span data-ttu-id="c9f3e-405">Windows 10-version: 1903 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-405">Windows 10 version: 1903+</span></span>

### <a name="processmitigations"></a><span data-ttu-id="c9f3e-406">ProcessMitigations</span><span class="sxs-lookup"><span data-stu-id="c9f3e-406">ProcessMitigations</span></span>

<span data-ttu-id="c9f3e-407">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-407">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-408">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-408">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-409">Server version: 1903 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-409">Server version: 1903+</span></span>
- <span data-ttu-id="c9f3e-410">Windows 10-version: 1903 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-410">Windows 10 version: 1903+</span></span>

### <a name="provisioning"></a><span data-ttu-id="c9f3e-411">Etablering</span><span class="sxs-lookup"><span data-stu-id="c9f3e-411">Provisioning</span></span>

<span data-ttu-id="c9f3e-412">Status: avtestat med kompatibilitetsläge</span><span class="sxs-lookup"><span data-stu-id="c9f3e-412">Status: Untested with Compatibility Layer</span></span>

### <a name="psdesiredstateconfiguration"></a><span data-ttu-id="c9f3e-413">PSDesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="c9f3e-413">PSDesiredStateConfiguration</span></span>

<span data-ttu-id="c9f3e-414">Status: delvis</span><span class="sxs-lookup"><span data-stu-id="c9f3e-414">Status: Partially</span></span>

<span data-ttu-id="c9f3e-415">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-415">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-416">Inbyggd i PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="c9f3e-416">Built into PowerShell 7</span></span>

### <a name="psdiagnostics"></a><span data-ttu-id="c9f3e-417">PSDiagnostics</span><span class="sxs-lookup"><span data-stu-id="c9f3e-417">PSDiagnostics</span></span>

<span data-ttu-id="c9f3e-418">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-418">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-419">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-419">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-420">Inbyggd i PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="c9f3e-420">Built into PowerShell 7</span></span>

### <a name="psscheduledjob"></a><span data-ttu-id="c9f3e-421">PSScheduledJob</span><span class="sxs-lookup"><span data-stu-id="c9f3e-421">PSScheduledJob</span></span>

<span data-ttu-id="c9f3e-422">Status: fungerar inte med kompatibilitetsläge</span><span class="sxs-lookup"><span data-stu-id="c9f3e-422">Status: Not working with Compatibility Layer</span></span>

<span data-ttu-id="c9f3e-423">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-423">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-424">Inbyggt i PowerShell 5,1</span><span class="sxs-lookup"><span data-stu-id="c9f3e-424">Built into PowerShell 5.1</span></span>

### <a name="psworkflow"></a><span data-ttu-id="c9f3e-425">PSWorkflow</span><span class="sxs-lookup"><span data-stu-id="c9f3e-425">PSWorkflow</span></span>

<span data-ttu-id="c9f3e-426">Status: avtestat med kompatibilitetsläge</span><span class="sxs-lookup"><span data-stu-id="c9f3e-426">Status: Untested with Compatibility Layer</span></span>

### <a name="psworkflowutility"></a><span data-ttu-id="c9f3e-427">PSWorkflowUtility</span><span class="sxs-lookup"><span data-stu-id="c9f3e-427">PSWorkflowUtility</span></span>

<span data-ttu-id="c9f3e-428">Status: avtestat med kompatibilitetsläge</span><span class="sxs-lookup"><span data-stu-id="c9f3e-428">Status: Untested with Compatibility Layer</span></span>

### <a name="remoteaccess"></a><span data-ttu-id="c9f3e-429">RemoteAccess</span><span class="sxs-lookup"><span data-stu-id="c9f3e-429">RemoteAccess</span></span>

<span data-ttu-id="c9f3e-430">Status: avtestat med kompatibilitetsläge</span><span class="sxs-lookup"><span data-stu-id="c9f3e-430">Status: Untested with Compatibility Layer</span></span>

### <a name="remotedesktop"></a><span data-ttu-id="c9f3e-431">RemoteDesktop</span><span class="sxs-lookup"><span data-stu-id="c9f3e-431">RemoteDesktop</span></span>

<span data-ttu-id="c9f3e-432">Status: avtestat med kompatibilitetsläge</span><span class="sxs-lookup"><span data-stu-id="c9f3e-432">Status: Untested with Compatibility Layer</span></span>

### <a name="scheduledtasks"></a><span data-ttu-id="c9f3e-433">ScheduledTasks</span><span class="sxs-lookup"><span data-stu-id="c9f3e-433">ScheduledTasks</span></span>

<span data-ttu-id="c9f3e-434">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-434">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-435">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-435">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-436">Server version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-436">Server version: 1809+</span></span>
- <span data-ttu-id="c9f3e-437">Windows 10-version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-437">Windows 10 version: 1809+</span></span>

### <a name="secureboot"></a><span data-ttu-id="c9f3e-438">SecureBoot</span><span class="sxs-lookup"><span data-stu-id="c9f3e-438">SecureBoot</span></span>

<span data-ttu-id="c9f3e-439">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-439">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-440">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-440">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-441">Server version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-441">Server version: 1809+</span></span>
- <span data-ttu-id="c9f3e-442">Windows 10-version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-442">Windows 10 version: 1809+</span></span>

### <a name="servercore"></a><span data-ttu-id="c9f3e-443">ServerCore</span><span class="sxs-lookup"><span data-stu-id="c9f3e-443">ServerCore</span></span>

<span data-ttu-id="c9f3e-444">Status: avtestat med kompatibilitetsläge</span><span class="sxs-lookup"><span data-stu-id="c9f3e-444">Status: Untested with Compatibility Layer</span></span>

### <a name="servermanager"></a><span data-ttu-id="c9f3e-445">ServerManager</span><span class="sxs-lookup"><span data-stu-id="c9f3e-445">ServerManager</span></span>

<span data-ttu-id="c9f3e-446">Status: avtestat med kompatibilitetsläge</span><span class="sxs-lookup"><span data-stu-id="c9f3e-446">Status: Untested with Compatibility Layer</span></span>

### <a name="servermanagertasks"></a><span data-ttu-id="c9f3e-447">ServerManagerTasks</span><span class="sxs-lookup"><span data-stu-id="c9f3e-447">ServerManagerTasks</span></span>

<span data-ttu-id="c9f3e-448">Status: avtestat med kompatibilitetsläge</span><span class="sxs-lookup"><span data-stu-id="c9f3e-448">Status: Untested with Compatibility Layer</span></span>

### <a name="shieldedvmdatafile"></a><span data-ttu-id="c9f3e-449">ShieldedVMDataFile</span><span class="sxs-lookup"><span data-stu-id="c9f3e-449">ShieldedVMDataFile</span></span>

<span data-ttu-id="c9f3e-450">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-450">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-451">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-451">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-452">Server version: 1903 + med RSAT-skärmad-VM-tools</span><span class="sxs-lookup"><span data-stu-id="c9f3e-452">Server version: 1903+ with RSAT-Shielded-VM-Tools</span></span>
- <span data-ttu-id="c9f3e-453">Windows 10-version: 1903 + med RSAT. skärmad. VM. tools</span><span class="sxs-lookup"><span data-stu-id="c9f3e-453">Windows 10 version: 1903+ with Rsat.Shielded.VM.Tools</span></span>

### <a name="shieldedvmprovisioning"></a><span data-ttu-id="c9f3e-454">ShieldedVMProvisioning</span><span class="sxs-lookup"><span data-stu-id="c9f3e-454">ShieldedVMProvisioning</span></span>

<span data-ttu-id="c9f3e-455">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-455">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-456">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-456">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-457">Server version: 1809 + med HostGuardian</span><span class="sxs-lookup"><span data-stu-id="c9f3e-457">Server version: 1809+ with HostGuardian</span></span>
- <span data-ttu-id="c9f3e-458">Windows 10-version: 1809 + med HostGuardian</span><span class="sxs-lookup"><span data-stu-id="c9f3e-458">Windows 10 version: 1809+ with HostGuardian</span></span>

### <a name="shieldedvmtemplate"></a><span data-ttu-id="c9f3e-459">ShieldedVMTemplate</span><span class="sxs-lookup"><span data-stu-id="c9f3e-459">ShieldedVMTemplate</span></span>

<span data-ttu-id="c9f3e-460">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-460">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-461">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-461">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-462">Server version: 1809 + med RSAT-skärmad-VM-tools</span><span class="sxs-lookup"><span data-stu-id="c9f3e-462">Server version: 1809+ with RSAT-Shielded-VM-Tools</span></span>
- <span data-ttu-id="c9f3e-463">Windows 10-version: 1809 + med RSAT. skärmad. VM. tools</span><span class="sxs-lookup"><span data-stu-id="c9f3e-463">Windows 10 version: 1809+ with Rsat.Shielded.VM.Tools</span></span>

### <a name="smbshare"></a><span data-ttu-id="c9f3e-464">SmbShare</span><span class="sxs-lookup"><span data-stu-id="c9f3e-464">SmbShare</span></span>

<span data-ttu-id="c9f3e-465">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-465">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-466">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-466">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-467">Server version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-467">Server version: 1809+</span></span>
- <span data-ttu-id="c9f3e-468">Windows 10-version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-468">Windows 10 version: 1809+</span></span>

### <a name="smbwitness"></a><span data-ttu-id="c9f3e-469">SmbWitness</span><span class="sxs-lookup"><span data-stu-id="c9f3e-469">SmbWitness</span></span>

<span data-ttu-id="c9f3e-470">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-470">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-471">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-471">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-472">Server version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-472">Server version: 1809+</span></span>
- <span data-ttu-id="c9f3e-473">Windows 10-version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-473">Windows 10 version: 1809+</span></span>

### <a name="smisconfig"></a><span data-ttu-id="c9f3e-474">SMISConfig</span><span class="sxs-lookup"><span data-stu-id="c9f3e-474">SMISConfig</span></span>

<span data-ttu-id="c9f3e-475">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-475">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-476">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-476">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-477">Server version: 1903 + med WindowsStorageManagementService</span><span class="sxs-lookup"><span data-stu-id="c9f3e-477">Server version: 1903+ with WindowsStorageManagementService</span></span>

### <a name="sms"></a><span data-ttu-id="c9f3e-478">SMS</span><span class="sxs-lookup"><span data-stu-id="c9f3e-478">SMS</span></span>

<span data-ttu-id="c9f3e-479">Status: avtestat med kompatibilitetsläge</span><span class="sxs-lookup"><span data-stu-id="c9f3e-479">Status: Untested with Compatibility Layer</span></span>

### <a name="softwareinventorylogging"></a><span data-ttu-id="c9f3e-480">SoftwareInventoryLogging</span><span class="sxs-lookup"><span data-stu-id="c9f3e-480">SoftwareInventoryLogging</span></span>

<span data-ttu-id="c9f3e-481">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-481">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-482">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-482">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-483">Server version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-483">Server version: 1809+</span></span>

### <a name="startlayout"></a><span data-ttu-id="c9f3e-484">StartLayout</span><span class="sxs-lookup"><span data-stu-id="c9f3e-484">StartLayout</span></span>

<span data-ttu-id="c9f3e-485">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-485">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-486">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-486">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-487">Server version: 1809 + med Skriv bords miljö</span><span class="sxs-lookup"><span data-stu-id="c9f3e-487">Server version: 1809+ with Desktop Experience</span></span>
- <span data-ttu-id="c9f3e-488">Windows 10-version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-488">Windows 10 version: 1809+</span></span>

### <a name="storage"></a><span data-ttu-id="c9f3e-489">Storage</span><span class="sxs-lookup"><span data-stu-id="c9f3e-489">Storage</span></span>

<span data-ttu-id="c9f3e-490">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-490">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-491">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-491">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-492">Server version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-492">Server version: 1809+</span></span>
- <span data-ttu-id="c9f3e-493">Windows 10-version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-493">Windows 10 version: 1809+</span></span>

### <a name="storagebuscache"></a><span data-ttu-id="c9f3e-494">StorageBusCache</span><span class="sxs-lookup"><span data-stu-id="c9f3e-494">StorageBusCache</span></span>

<span data-ttu-id="c9f3e-495">Status: avtestat med kompatibilitetsläge</span><span class="sxs-lookup"><span data-stu-id="c9f3e-495">Status: Untested with Compatibility Layer</span></span>

### <a name="storagemigrationservice"></a><span data-ttu-id="c9f3e-496">StorageMigrationService</span><span class="sxs-lookup"><span data-stu-id="c9f3e-496">StorageMigrationService</span></span>

<span data-ttu-id="c9f3e-497">Status: avtestat med kompatibilitetsläge</span><span class="sxs-lookup"><span data-stu-id="c9f3e-497">Status: Untested with Compatibility Layer</span></span>

### <a name="storageqos"></a><span data-ttu-id="c9f3e-498">StorageQOS</span><span class="sxs-lookup"><span data-stu-id="c9f3e-498">StorageQOS</span></span>

<span data-ttu-id="c9f3e-499">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-499">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-500">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-500">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-501">Server version: 1809 + med RSAT-Clustering – PowerShell</span><span class="sxs-lookup"><span data-stu-id="c9f3e-501">Server version: 1809+ with RSAT-Clustering-PowerShell</span></span>
- <span data-ttu-id="c9f3e-502">Windows 10-version: 1809 + med RSAT. FailoverCluster. Management. tools</span><span class="sxs-lookup"><span data-stu-id="c9f3e-502">Windows 10 version: 1809+ with Rsat.FailoverCluster.Management.Tools</span></span>

### <a name="storagereplica"></a><span data-ttu-id="c9f3e-503">StorageReplica</span><span class="sxs-lookup"><span data-stu-id="c9f3e-503">StorageReplica</span></span>

<span data-ttu-id="c9f3e-504">Status: avtestat med kompatibilitetsläge</span><span class="sxs-lookup"><span data-stu-id="c9f3e-504">Status: Untested with Compatibility Layer</span></span>

### <a name="syncshare"></a><span data-ttu-id="c9f3e-505">SyncShare</span><span class="sxs-lookup"><span data-stu-id="c9f3e-505">SyncShare</span></span>

<span data-ttu-id="c9f3e-506">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-506">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-507">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-507">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-508">Server version: 1809 + med FS-SyncShareService</span><span class="sxs-lookup"><span data-stu-id="c9f3e-508">Server version: 1809+ with FS-SyncShareService</span></span>

### <a name="systeminsights"></a><span data-ttu-id="c9f3e-509">SystemInsights</span><span class="sxs-lookup"><span data-stu-id="c9f3e-509">SystemInsights</span></span>

<span data-ttu-id="c9f3e-510">Status: avtestat med kompatibilitetsläge</span><span class="sxs-lookup"><span data-stu-id="c9f3e-510">Status: Untested with Compatibility Layer</span></span>

### <a name="tls"></a><span data-ttu-id="c9f3e-511">TLS</span><span class="sxs-lookup"><span data-stu-id="c9f3e-511">TLS</span></span>

<span data-ttu-id="c9f3e-512">Status: avtestat med kompatibilitetsläge</span><span class="sxs-lookup"><span data-stu-id="c9f3e-512">Status: Untested with Compatibility Layer</span></span>

### <a name="troubleshootingpack"></a><span data-ttu-id="c9f3e-513">TroubleshootingPack</span><span class="sxs-lookup"><span data-stu-id="c9f3e-513">TroubleshootingPack</span></span>

<span data-ttu-id="c9f3e-514">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-514">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-515">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-515">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-516">Windows 10-version: 1903 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-516">Windows 10 version: 1903+</span></span>

### <a name="trustedplatformmodule"></a><span data-ttu-id="c9f3e-517">TrustedPlatformModule</span><span class="sxs-lookup"><span data-stu-id="c9f3e-517">TrustedPlatformModule</span></span>

<span data-ttu-id="c9f3e-518">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-518">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-519">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-519">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-520">Server version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-520">Server version: 1809+</span></span>
- <span data-ttu-id="c9f3e-521">Windows 10-version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-521">Windows 10 version: 1809+</span></span>

### <a name="uev"></a><span data-ttu-id="c9f3e-522">UEV</span><span class="sxs-lookup"><span data-stu-id="c9f3e-522">UEV</span></span>

<span data-ttu-id="c9f3e-523">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-523">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-524">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-524">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-525">Server version:?? En framtida version av server med Skriv bords miljö?</span><span class="sxs-lookup"><span data-stu-id="c9f3e-525">Server version: ??Future version of Server with Desktop Experience??</span></span>
- <span data-ttu-id="c9f3e-526">Windows 10-version: 1903 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-526">Windows 10 version: 1903+</span></span>

### <a name="updateservices"></a><span data-ttu-id="c9f3e-527">UpdateServices</span><span class="sxs-lookup"><span data-stu-id="c9f3e-527">UpdateServices</span></span>

<span data-ttu-id="c9f3e-528">Status: fungerar inte med kompatibilitetsläge</span><span class="sxs-lookup"><span data-stu-id="c9f3e-528">Status: Not working with Compatibility Layer</span></span>

### <a name="vpnclient"></a><span data-ttu-id="c9f3e-529">VpnClient</span><span class="sxs-lookup"><span data-stu-id="c9f3e-529">VpnClient</span></span>

<span data-ttu-id="c9f3e-530">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-530">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-531">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-531">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-532">Server version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-532">Server version: 1809+</span></span>
- <span data-ttu-id="c9f3e-533">Windows 10-version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-533">Windows 10 version: 1809+</span></span>

### <a name="wdac"></a><span data-ttu-id="c9f3e-534">Wdac</span><span class="sxs-lookup"><span data-stu-id="c9f3e-534">Wdac</span></span>

<span data-ttu-id="c9f3e-535">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-535">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-536">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-536">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-537">Server version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-537">Server version: 1809+</span></span>
- <span data-ttu-id="c9f3e-538">Windows 10-version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-538">Windows 10 version: 1809+</span></span>

### <a name="webadministration"></a><span data-ttu-id="c9f3e-539">Webadministration</span><span class="sxs-lookup"><span data-stu-id="c9f3e-539">WebAdministration</span></span>

<span data-ttu-id="c9f3e-540">Status: avtestat med kompatibilitetsläge</span><span class="sxs-lookup"><span data-stu-id="c9f3e-540">Status: Untested with Compatibility Layer</span></span>

### <a name="whea"></a><span data-ttu-id="c9f3e-541">WHEA</span><span class="sxs-lookup"><span data-stu-id="c9f3e-541">WHEA</span></span>

<span data-ttu-id="c9f3e-542">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-542">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-543">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-543">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-544">Server version: 1903 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-544">Server version: 1903+</span></span>
- <span data-ttu-id="c9f3e-545">Windows 10-version: 1903 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-545">Windows 10 version: 1903+</span></span>

### <a name="windowsdeveloperlicense"></a><span data-ttu-id="c9f3e-546">WindowsDeveloperLicense</span><span class="sxs-lookup"><span data-stu-id="c9f3e-546">WindowsDeveloperLicense</span></span>

<span data-ttu-id="c9f3e-547">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-547">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-548">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-548">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-549">Server version: 1809 + med Skriv bords miljö</span><span class="sxs-lookup"><span data-stu-id="c9f3e-549">Server version: 1809+ with Desktop Experience</span></span>
- <span data-ttu-id="c9f3e-550">Windows 10-version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-550">Windows 10 version: 1809+</span></span>

### <a name="windowserrorreporting"></a><span data-ttu-id="c9f3e-551">WindowsErrorReporting</span><span class="sxs-lookup"><span data-stu-id="c9f3e-551">WindowsErrorReporting</span></span>

<span data-ttu-id="c9f3e-552">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-552">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-553">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-553">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-554">Server version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-554">Server version: 1809+</span></span>
- <span data-ttu-id="c9f3e-555">Windows 10-version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-555">Windows 10 version: 1809+</span></span>

### <a name="windowssearch"></a><span data-ttu-id="c9f3e-556">WindowsSearch</span><span class="sxs-lookup"><span data-stu-id="c9f3e-556">WindowsSearch</span></span>

<span data-ttu-id="c9f3e-557">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-557">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-558">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-558">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-559">Windows 10-version: 1903 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-559">Windows 10 version: 1903+</span></span>

### <a name="windowsserverbackup"></a><span data-ttu-id="c9f3e-560">WindowsServerBackup</span><span class="sxs-lookup"><span data-stu-id="c9f3e-560">WindowsServerBackup</span></span>

<span data-ttu-id="c9f3e-561">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-561">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-562">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-562">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-563">Server version: 19H2 med Windows-Server – säkerhets kopiering</span><span class="sxs-lookup"><span data-stu-id="c9f3e-563">Server version: 19H2 with Windows-Server-Backup</span></span>

### <a name="windowsupdate"></a><span data-ttu-id="c9f3e-564">WindowsUpdate</span><span class="sxs-lookup"><span data-stu-id="c9f3e-564">WindowsUpdate</span></span>

<span data-ttu-id="c9f3e-565">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-565">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-566">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-566">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-567">Server version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-567">Server version: 1809+</span></span>
- <span data-ttu-id="c9f3e-568">Windows 10-version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-568">Windows 10 version: 1809+</span></span>

### <a name="windowsupdateprovider"></a><span data-ttu-id="c9f3e-569">WindowsUpdateProvider</span><span class="sxs-lookup"><span data-stu-id="c9f3e-569">WindowsUpdateProvider</span></span>

<span data-ttu-id="c9f3e-570">Status: internt kompatibel</span><span class="sxs-lookup"><span data-stu-id="c9f3e-570">Status: Natively Compatible</span></span>

<span data-ttu-id="c9f3e-571">Kompatibel med:</span><span class="sxs-lookup"><span data-stu-id="c9f3e-571">Compatible with:</span></span>

- <span data-ttu-id="c9f3e-572">Server version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-572">Server version: 1809+</span></span>
- <span data-ttu-id="c9f3e-573">Windows 10-version: 1809 +</span><span class="sxs-lookup"><span data-stu-id="c9f3e-573">Windows 10 version: 1809+</span></span>
