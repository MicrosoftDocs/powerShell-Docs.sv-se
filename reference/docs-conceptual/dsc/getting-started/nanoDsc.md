---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Använda DSC på Nano Server
ms.openlocfilehash: fb826455c21833ae4c8dc2ecd731ffce6bf7eaba
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941882"
---
# <a name="using-dsc-on-nano-server"></a><span data-ttu-id="80e7b-103">Använda DSC på Nano Server</span><span class="sxs-lookup"><span data-stu-id="80e7b-103">Using DSC on Nano Server</span></span>

> <span data-ttu-id="80e7b-104">Gäller för: Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="80e7b-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="80e7b-105">**DSC på Nano Server** är ett valfritt paket i mappen `NanoServer\Packages` i Windows Server 2016-mediet.</span><span class="sxs-lookup"><span data-stu-id="80e7b-105">**DSC on Nano Server** is an optional package in the `NanoServer\Packages` folder of the Windows Server 2016 media.</span></span> <span data-ttu-id="80e7b-106">Paketet kan installeras när du skapar en virtuell hård disk för en Nano Server genom att ange **Microsoft-NanoServer-DSC-Package** som värdet för parametern **packages** för funktionen **New-NanoServerImage** .</span><span class="sxs-lookup"><span data-stu-id="80e7b-106">The package can be installed when you create a VHD for a Nano Server by specifying **Microsoft-NanoServer-DSC-Package** as the value of the **Packages** parameter of the **New-NanoServerImage** function.</span></span> <span data-ttu-id="80e7b-107">Om du till exempel skapar en virtuell hård disk för en virtuell dator ser kommandot ut så här:</span><span class="sxs-lookup"><span data-stu-id="80e7b-107">For example, if you are creating a VHD for a virtual machine, the command would look like the following:</span></span>

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

<span data-ttu-id="80e7b-108">Information om hur du installerar och använder Nano Server, samt hur du hanterar Nano Server med PowerShell-fjärrkommunikation, finns [komma igång med Nano Server](/windows-server/get-started/getting-started-with-nano-server).</span><span class="sxs-lookup"><span data-stu-id="80e7b-108">For information about installing and using Nano Server, as well as how to manage Nano Server with PowerShell Remoting, see [Getting Started with Nano Server](/windows-server/get-started/getting-started-with-nano-server).</span></span>

## <a name="dsc-features-available-on-nano-server"></a><span data-ttu-id="80e7b-109">DSC-funktioner som är tillgängliga på Nano Server</span><span class="sxs-lookup"><span data-stu-id="80e7b-109">DSC features available on Nano Server</span></span>

<span data-ttu-id="80e7b-110">Eftersom Nano Server bara stöder en begränsad uppsättning API: er jämfört med en fullständig version av Windows Server, har DSC på Nano Server inte fullt fungerande paritet med DSC som körs på fullständiga SKU: er under tiden.</span><span class="sxs-lookup"><span data-stu-id="80e7b-110">Because Nano Server supports only a limited set of APIs compared to a full version of Windows Server, DSC on Nano Server does not have full functional parity with DSC running on full SKUs for the time being.</span></span> <span data-ttu-id="80e7b-111">DSC på Nano Server är i aktiv utveckling och funktionen är inte slutförd ännu.</span><span class="sxs-lookup"><span data-stu-id="80e7b-111">DSC on Nano Server is in active development and is not yet feature complete.</span></span>

<span data-ttu-id="80e7b-112">Följande DSC-funktioner är för närvarande tillgängliga på Nano Server:</span><span class="sxs-lookup"><span data-stu-id="80e7b-112">The following DSC features are currently available on Nano Server:</span></span>

<span data-ttu-id="80e7b-113">Både push-och pull-lägen</span><span class="sxs-lookup"><span data-stu-id="80e7b-113">Both push and pull modes</span></span>

- <span data-ttu-id="80e7b-114">Alla DSC-cmdletar som finns i en fullständig version av Windows Server, inklusive följande:</span><span class="sxs-lookup"><span data-stu-id="80e7b-114">All DSC cmdlets that exist on a full version of Windows Server, including the following:</span></span>
- [<span data-ttu-id="80e7b-115">Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="80e7b-115">Get-DscLocalConfigurationManager</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager)
- [<span data-ttu-id="80e7b-116">Set-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="80e7b-116">Set-DscLocalConfigurationManager</span></span>](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager)
- [<span data-ttu-id="80e7b-117">Aktivera – DscDebug</span><span class="sxs-lookup"><span data-stu-id="80e7b-117">Enable-DscDebug</span></span>](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug)
- [<span data-ttu-id="80e7b-118">Disable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="80e7b-118">Disable-DscDebug</span></span>](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug)
- [<span data-ttu-id="80e7b-119">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="80e7b-119">Start-DscConfiguration</span></span>](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration)
- [<span data-ttu-id="80e7b-120">Stop-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="80e7b-120">Stop-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration)
- [<span data-ttu-id="80e7b-121">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="80e7b-121">Get-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration)
- [<span data-ttu-id="80e7b-122">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="80e7b-122">Test-DscConfiguration</span></span>](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)
- [<span data-ttu-id="80e7b-123">Publicera – DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="80e7b-123">Publish-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration)
- [<span data-ttu-id="80e7b-124">Uppdatera – DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="80e7b-124">Update-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration)
- [<span data-ttu-id="80e7b-125">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="80e7b-125">Restore-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Restore-DscConfiguration)
- [<span data-ttu-id="80e7b-126">Remove-DscConfigurationDocument</span><span class="sxs-lookup"><span data-stu-id="80e7b-126">Remove-DscConfigurationDocument</span></span>](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument)
- [<span data-ttu-id="80e7b-127">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="80e7b-127">Get-DscConfigurationStatus</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus)
- [<span data-ttu-id="80e7b-128">Invoke-Dscresource Keyword Supports</span><span class="sxs-lookup"><span data-stu-id="80e7b-128">Invoke-DscResource</span></span>](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource)
- [<span data-ttu-id="80e7b-129">Find-Dscresource Keyword Supports</span><span class="sxs-lookup"><span data-stu-id="80e7b-129">Find-DscResource</span></span>](/powershell/module/powershellget/find-dscresource?view=powershell-6)
- [<span data-ttu-id="80e7b-130">Get-Dscresource Keyword Supports</span><span class="sxs-lookup"><span data-stu-id="80e7b-130">Get-DscResource</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)
- [<span data-ttu-id="80e7b-131">New-DscChecksum</span><span class="sxs-lookup"><span data-stu-id="80e7b-131">New-DscChecksum</span></span>](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum)

- <span data-ttu-id="80e7b-132">Kompilera konfigurationer (se [DSC-konfigurationer](../configurations/configurations.md))</span><span class="sxs-lookup"><span data-stu-id="80e7b-132">Compiling configurations (see [DSC configurations](../configurations/configurations.md))</span></span>

  <span data-ttu-id="80e7b-133">**Ge** Lösen ords kryptering (se [skydda MOF-filen](../pull-server/secureMOF.md)) under konfigurations kompileringen fungerar inte.</span><span class="sxs-lookup"><span data-stu-id="80e7b-133">**Issue:** Password encryption (see [Securing the MOF File](../pull-server/secureMOF.md)) during configuration compilation doesn't work.</span></span>

- <span data-ttu-id="80e7b-134">Kompilera metaconfigurations (se [Konfigurera den lokala Configuration Manager](../managing-nodes/metaConfig.md))</span><span class="sxs-lookup"><span data-stu-id="80e7b-134">Compiling metaconfigurations (see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md))</span></span>

- <span data-ttu-id="80e7b-135">Köra en resurs under användar kontext (se [köra DSC med användarautentiseringsuppgifter (runas)](../configurations/runAsUser.md))</span><span class="sxs-lookup"><span data-stu-id="80e7b-135">Running a resource under user context (see [Running DSC with user credentials (RunAs)](../configurations/runAsUser.md))</span></span>

- <span data-ttu-id="80e7b-136">Klassbaserade resurser (se [skriva en anpassad DSC-resurs med PowerShell-klasser](/previous-versions//dn948461(v=technet.10)))</span><span class="sxs-lookup"><span data-stu-id="80e7b-136">Class-based resources (see [Writing a custom DSC resource with PowerShell classes](/previous-versions//dn948461(v=technet.10)))</span></span>

- <span data-ttu-id="80e7b-137">Fel sökning av DSC-resurser (se [fel sökning av DSC-resurser](../troubleshooting/debugResource.md))</span><span class="sxs-lookup"><span data-stu-id="80e7b-137">Debugging of DSC resources (see [Debugging DSC resources](../troubleshooting/debugResource.md))</span></span>

  <span data-ttu-id="80e7b-138">**Ge** Fungerar inte om en resurs använder PsDscRunAsCredential (se [köra DSC med](../configurations/runAsUser.md)användarautentiseringsuppgifter)</span><span class="sxs-lookup"><span data-stu-id="80e7b-138">**Issue:** Doesn't work if a resource is using PsDscRunAsCredential (see [Running DSC with user credentials](../configurations/runAsUser.md))</span></span>

- [<span data-ttu-id="80e7b-139">Ange beroenden mellan noder</span><span class="sxs-lookup"><span data-stu-id="80e7b-139">Specifying cross-node dependencies</span></span>](../configurations/crossNodeDependencies.md)

- [<span data-ttu-id="80e7b-140">Resurs version</span><span class="sxs-lookup"><span data-stu-id="80e7b-140">Resource versioning</span></span>](../configurations/sxsResource.md)

- <span data-ttu-id="80e7b-141">Hämta klient (konfigurationer & resurser) (se [Konfigurera en pull-klient med hjälp av konfigurations namn](../pull-server/pullClientConfigNames.md))</span><span class="sxs-lookup"><span data-stu-id="80e7b-141">Pull client (configurations & resources) (see [Setting up a pull client using configuration names](../pull-server/pullClientConfigNames.md))</span></span>

- [<span data-ttu-id="80e7b-142">Partiella konfigurationer (pull-& push)</span><span class="sxs-lookup"><span data-stu-id="80e7b-142">Partial configurations (pull & push)</span></span>](../pull-server/partialConfigs.md)

- [<span data-ttu-id="80e7b-143">Rapportering till hämtnings Server</span><span class="sxs-lookup"><span data-stu-id="80e7b-143">Reporting to pull server</span></span>](../pull-server/reportServer.md)

- <span data-ttu-id="80e7b-144">MOF-kryptering</span><span class="sxs-lookup"><span data-stu-id="80e7b-144">MOF encryption</span></span>

- <span data-ttu-id="80e7b-145">Händelse loggning</span><span class="sxs-lookup"><span data-stu-id="80e7b-145">Event logging</span></span>

- <span data-ttu-id="80e7b-146">Azure Automation DSC-rapportering</span><span class="sxs-lookup"><span data-stu-id="80e7b-146">Azure Automation DSC reporting</span></span>

- <span data-ttu-id="80e7b-147">Resurser som är helt funktionella</span><span class="sxs-lookup"><span data-stu-id="80e7b-147">Resources that are fully functional</span></span>

- <span data-ttu-id="80e7b-148">**Arkiv**</span><span class="sxs-lookup"><span data-stu-id="80e7b-148">**Archive**</span></span>
- <span data-ttu-id="80e7b-149">**Miljö**</span><span class="sxs-lookup"><span data-stu-id="80e7b-149">**Environment**</span></span>
- <span data-ttu-id="80e7b-150">**Fil**</span><span class="sxs-lookup"><span data-stu-id="80e7b-150">**File**</span></span>
- <span data-ttu-id="80e7b-151">**log**</span><span class="sxs-lookup"><span data-stu-id="80e7b-151">**Log**</span></span>
- <span data-ttu-id="80e7b-152">**ProcessSet**</span><span class="sxs-lookup"><span data-stu-id="80e7b-152">**ProcessSet**</span></span>
- <span data-ttu-id="80e7b-153">**Registernyckeln**</span><span class="sxs-lookup"><span data-stu-id="80e7b-153">**Registry**</span></span>
- <span data-ttu-id="80e7b-154">**Över**</span><span class="sxs-lookup"><span data-stu-id="80e7b-154">**Script**</span></span>
- <span data-ttu-id="80e7b-155">**WindowsPackageCab**</span><span class="sxs-lookup"><span data-stu-id="80e7b-155">**WindowsPackageCab**</span></span>
- <span data-ttu-id="80e7b-156">**WindowsProcess**</span><span class="sxs-lookup"><span data-stu-id="80e7b-156">**WindowsProcess**</span></span>
- <span data-ttu-id="80e7b-157">**WaitForAll** (se [ange beroenden mellan noder](../configurations/crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="80e7b-157">**WaitForAll** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>
- <span data-ttu-id="80e7b-158">**WaitForAny** (se [ange beroenden mellan noder](../configurations/crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="80e7b-158">**WaitForAny** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>
- <span data-ttu-id="80e7b-159">**WaitForSome** (se [ange beroenden mellan noder](../configurations/crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="80e7b-159">**WaitForSome** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>

- <span data-ttu-id="80e7b-160">Resurser som är delvis funktionella</span><span class="sxs-lookup"><span data-stu-id="80e7b-160">Resources that are partially functional</span></span>
- <span data-ttu-id="80e7b-161">**Grupp**</span><span class="sxs-lookup"><span data-stu-id="80e7b-161">**Group**</span></span>
- <span data-ttu-id="80e7b-162">**GroupSet**</span><span class="sxs-lookup"><span data-stu-id="80e7b-162">**GroupSet**</span></span>

  <span data-ttu-id="80e7b-163">**Ge** Över resurser fungerar inte om en speciell instans anropas två gånger (kör samma konfiguration två gånger)</span><span class="sxs-lookup"><span data-stu-id="80e7b-163">**Issue:** Above resources fail if specific instance is called twice (running the same configuration twice)</span></span>

- <span data-ttu-id="80e7b-164">**Tjänst**</span><span class="sxs-lookup"><span data-stu-id="80e7b-164">**Service**</span></span>
- <span data-ttu-id="80e7b-165">**ServiceSet**</span><span class="sxs-lookup"><span data-stu-id="80e7b-165">**ServiceSet**</span></span>

  <span data-ttu-id="80e7b-166">**Ge** Fungerar bara för att starta/stoppa tjänsten (status).</span><span class="sxs-lookup"><span data-stu-id="80e7b-166">**Issue:** Only works for starting/stopping (status) service.</span></span> <span data-ttu-id="80e7b-167">Miss lyckas, om ett försök att ändra andra tjänsteattribut som startuptype tjänst, autentiseringsuppgifter, beskrivning osv.</span><span class="sxs-lookup"><span data-stu-id="80e7b-167">Fails, if one tries to change other service attributes like startuptype, credentials, description etc..</span></span> <span data-ttu-id="80e7b-168">Det fel som har utlösts liknar:</span><span class="sxs-lookup"><span data-stu-id="80e7b-168">The error thrown is similar to:</span></span>

  <span data-ttu-id="80e7b-169">*Det går inte att hitta typen [Management. managementobject]: kontrol lera att sammansättningen som innehåller den här typen har lästs in.*</span><span class="sxs-lookup"><span data-stu-id="80e7b-169">*Cannot find type [management.managementobject]: verify that the assembly containing this type is loaded.*</span></span>

- <span data-ttu-id="80e7b-170">Resurser som inte fungerar</span><span class="sxs-lookup"><span data-stu-id="80e7b-170">Resources that are not functional</span></span>
- <span data-ttu-id="80e7b-171">**Användarvänlig**</span><span class="sxs-lookup"><span data-stu-id="80e7b-171">**User**</span></span>

## <a name="dsc-features-not-available-on-nano-server"></a><span data-ttu-id="80e7b-172">DSC-funktioner är inte tillgängliga på Nano Server</span><span class="sxs-lookup"><span data-stu-id="80e7b-172">DSC features not available on Nano Server</span></span>

<span data-ttu-id="80e7b-173">Följande DSC-funktioner är för närvarande inte tillgängliga på Nano Server:</span><span class="sxs-lookup"><span data-stu-id="80e7b-173">The following DSC features are not currently available on Nano Server:</span></span>

- <span data-ttu-id="80e7b-174">Dekryptera MOF-dokument med krypterade lösen ord</span><span class="sxs-lookup"><span data-stu-id="80e7b-174">Decrypting MOF document with encrypted password(s)</span></span>
- <span data-ttu-id="80e7b-175">Pull-server – du kan för närvarande inte konfigurera en pull-server på Nano Server</span><span class="sxs-lookup"><span data-stu-id="80e7b-175">Pull Server--you cannot currently set up a pull server on Nano Server</span></span>
- <span data-ttu-id="80e7b-176">Allt som inte finns med i listan över funktioner fungerar</span><span class="sxs-lookup"><span data-stu-id="80e7b-176">Anything that is not in the list of feature works</span></span>

## <a name="using-custom-dsc-resources-on-nano-server"></a><span data-ttu-id="80e7b-177">Använda anpassade DSC-resurser på Nano Server</span><span class="sxs-lookup"><span data-stu-id="80e7b-177">Using custom DSC resources on Nano Server</span></span>

<span data-ttu-id="80e7b-178">På grund av en begränsad uppsättning Windows-API: er och CLR-bibliotek som är tillgängliga på Nano Server, fungerar DSC-resurser som fungerar på den fullständiga CLR-versionen av Windows inte nödvändigt vis på Nano Server.</span><span class="sxs-lookup"><span data-stu-id="80e7b-178">Due to a limited sets of Windows APIs and CLR libraries available on Nano Server, DSC resources that work on the full CLR version of Windows do not necessarily work on Nano Server.</span></span>
<span data-ttu-id="80e7b-179">Slutför testet från slut punkt till slut punkt innan du distribuerar några anpassade DSC-resurser till en produktions miljö.</span><span class="sxs-lookup"><span data-stu-id="80e7b-179">Complete end-to-end testing before deploying any DSC custom resources to a production environment.</span></span>

## <a name="see-also"></a><span data-ttu-id="80e7b-180">Se även</span><span class="sxs-lookup"><span data-stu-id="80e7b-180">See Also</span></span>

- [<span data-ttu-id="80e7b-181">Komma igång med Nano Server</span><span class="sxs-lookup"><span data-stu-id="80e7b-181">Getting Started with Nano Server</span></span>](/windows-server/get-started/getting-started-with-nano-server)
