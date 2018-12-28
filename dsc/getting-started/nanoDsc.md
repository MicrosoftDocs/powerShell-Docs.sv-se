---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Använda DSC på Nano Server
ms.openlocfilehash: fd81fe56d16100f45d9ee2dfd8fdc303c2a6c17a
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404955"
---
# <a name="using-dsc-on-nano-server"></a><span data-ttu-id="eab2a-103">Använda DSC på Nano Server</span><span class="sxs-lookup"><span data-stu-id="eab2a-103">Using DSC on Nano Server</span></span>

> <span data-ttu-id="eab2a-104">Gäller för: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="eab2a-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="eab2a-105">**DSC på Nano Server** är ett valfritt paket i den `NanoServer\Packages` mappen för Windows Server 2016 media.</span><span class="sxs-lookup"><span data-stu-id="eab2a-105">**DSC on Nano Server** is an optional package in the `NanoServer\Packages` folder of the Windows Server 2016 media.</span></span> <span data-ttu-id="eab2a-106">Paketet kan installeras när du skapar en virtuell Hårddisk för Nano Server genom att ange **Microsoft-NanoServer-DSC-Package** som värde för den **paket** -parametern för den **New-NanoServerImage**  funktion.</span><span class="sxs-lookup"><span data-stu-id="eab2a-106">The package can be installed when you create a VHD for a Nano Server by specifying **Microsoft-NanoServer-DSC-Package** as the value of the **Packages** parameter of the **New-NanoServerImage** function.</span></span> <span data-ttu-id="eab2a-107">Om du skapar en virtuell Hårddisk för en virtuell dator, till exempel se kommandot ut så här:</span><span class="sxs-lookup"><span data-stu-id="eab2a-107">For example, if you are creating a VHD for a virtual machine, the command would look like the following:</span></span>

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

<span data-ttu-id="eab2a-108">Information om installation och användning av Nano Server, samt hur du hanterar Nano Server med PowerShell-fjärrkommunikation finns i [komma igång med Nano Server](/windows-server/get-started/getting-started-with-nano-server).</span><span class="sxs-lookup"><span data-stu-id="eab2a-108">For information about installing and using Nano Server, as well as how to manage Nano Server with PowerShell Remoting, see [Getting Started with Nano Server](/windows-server/get-started/getting-started-with-nano-server).</span></span>

## <a name="dsc-features-available-on-nano-server"></a><span data-ttu-id="eab2a-109">DSC-funktioner som är tillgängliga på Nano Server</span><span class="sxs-lookup"><span data-stu-id="eab2a-109">DSC features available on Nano Server</span></span>

<span data-ttu-id="eab2a-110">Eftersom Nano Server stöder endast en begränsad uppsättning API: er jämfört med en fullständig version av Windows Server, har DSC på Nano Server inte fullständiga funktioner i paritet med DSC som körs på fullständiga SKU: er för tillfället.</span><span class="sxs-lookup"><span data-stu-id="eab2a-110">Because Nano Server supports only a limited set of APIs compared to a full version of Windows Server, DSC on Nano Server does not have full functional parity with DSC running on full SKUs for the time being.</span></span> <span data-ttu-id="eab2a-111">DSC på Nano Server är i aktivt med utveckling och ännu inte är funktionen som är klar.</span><span class="sxs-lookup"><span data-stu-id="eab2a-111">DSC on Nano Server is in active development and is not yet feature complete.</span></span>

<span data-ttu-id="eab2a-112">Följande DSC-funktioner är tillgängliga på Nano Server:</span><span class="sxs-lookup"><span data-stu-id="eab2a-112">The following DSC features are currently available on Nano Server:</span></span>

<span data-ttu-id="eab2a-113">Både sändnings- och mottagningsläge</span><span class="sxs-lookup"><span data-stu-id="eab2a-113">Both push and pull modes</span></span>

- <span data-ttu-id="eab2a-114">Alla DSC-cmdletar som finns på en fullständig version av Windows Server, inklusive följande:</span><span class="sxs-lookup"><span data-stu-id="eab2a-114">All DSC cmdlets that exist on a full version of Windows Server, including the following:</span></span>
- [<span data-ttu-id="eab2a-115">Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="eab2a-115">Get-DscLocalConfigurationManager</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager)
- [<span data-ttu-id="eab2a-116">Set-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="eab2a-116">Set-DscLocalConfigurationManager</span></span>](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager)
- [<span data-ttu-id="eab2a-117">Aktivera DscDebug</span><span class="sxs-lookup"><span data-stu-id="eab2a-117">Enable-DscDebug</span></span>](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug)
- [<span data-ttu-id="eab2a-118">Inaktivera DscDebug</span><span class="sxs-lookup"><span data-stu-id="eab2a-118">Disable-DscDebug</span></span>](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug)
- [<span data-ttu-id="eab2a-119">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="eab2a-119">Start-DscConfiguration</span></span>](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration)
- [<span data-ttu-id="eab2a-120">Stop-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="eab2a-120">Stop-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration)
- [<span data-ttu-id="eab2a-121">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="eab2a-121">Get-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration)
- [<span data-ttu-id="eab2a-122">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="eab2a-122">Test-DscConfiguration</span></span>](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)
- [<span data-ttu-id="eab2a-123">Publicera DscConfiguraiton</span><span class="sxs-lookup"><span data-stu-id="eab2a-123">Publish-DscConfiguraiton</span></span>](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration)
- [<span data-ttu-id="eab2a-124">Update-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="eab2a-124">Update-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration)
- [<span data-ttu-id="eab2a-125">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="eab2a-125">Restore-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Restore-DscConfiguration)
- [<span data-ttu-id="eab2a-126">Ta bort DscConfigurationDocument</span><span class="sxs-lookup"><span data-stu-id="eab2a-126">Remove-DscConfigurationDocument</span></span>](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument)
- [<span data-ttu-id="eab2a-127">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="eab2a-127">Get-DscConfigurationStatus</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus)
- [<span data-ttu-id="eab2a-128">Anropa DscResource</span><span class="sxs-lookup"><span data-stu-id="eab2a-128">Invoke-DscResource</span></span>](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource)
- [<span data-ttu-id="eab2a-129">Sök-DscResource</span><span class="sxs-lookup"><span data-stu-id="eab2a-129">Find-DscResource</span></span>](https://technet.microsoft.com/en-us/library/mt517874.aspx)
- [<span data-ttu-id="eab2a-130">Get-DscResource</span><span class="sxs-lookup"><span data-stu-id="eab2a-130">Get-DscResource</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)
- [<span data-ttu-id="eab2a-131">Ny DscChecksum</span><span class="sxs-lookup"><span data-stu-id="eab2a-131">New-DscChecksum</span></span>](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum)

- <span data-ttu-id="eab2a-132">Kompilera konfigurationer (se [DSC-konfigurationer](../configurations/configurations.md))</span><span class="sxs-lookup"><span data-stu-id="eab2a-132">Compiling configurations (see [DSC configurations](../configurations/configurations.md))</span></span>

  <span data-ttu-id="eab2a-133">**Problem:** Lösenordskryptering (se [skydda MOF-filen](../pull-server/secureMOF.md)) under konfigurationen kompilering fungerar inte.</span><span class="sxs-lookup"><span data-stu-id="eab2a-133">**Issue:** Password encryption (see [Securing the MOF File](../pull-server/secureMOF.md)) during configuration compilation doesn't work.</span></span>

- <span data-ttu-id="eab2a-134">Kompilera metaconfigurations (se [konfigurerar den lokala Konfigurationshanteraren](../managing-nodes/metaConfig.md))</span><span class="sxs-lookup"><span data-stu-id="eab2a-134">Compiling metaconfigurations (see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md))</span></span>

- <span data-ttu-id="eab2a-135">Kör en resurs under användarkontext (se [kör DSC med autentiseringsuppgifterna för användaren (kör)](../configurations/runAsUser.md))</span><span class="sxs-lookup"><span data-stu-id="eab2a-135">Running a resource under user context (see [Running DSC with user credentials (RunAs)](../configurations/runAsUser.md))</span></span>

- <span data-ttu-id="eab2a-136">MOF-baserade resurser (se [skriva en anpassad DSC-resurs med PowerShell-klasser](../resources/authoringResourceClass.md))</span><span class="sxs-lookup"><span data-stu-id="eab2a-136">Class-based resources (see [Writing a custom DSC resource with PowerShell classes](../resources/authoringResourceClass.md))</span></span>

- <span data-ttu-id="eab2a-137">Felsökning av DSC-resurser (se [felsökning DSC-resurser](../troubleshooting/debugResource.md))</span><span class="sxs-lookup"><span data-stu-id="eab2a-137">Debugging of DSC resources (see [Debugging DSC resources](../troubleshooting/debugResource.md))</span></span>

  <span data-ttu-id="eab2a-138">**Problem:** Fungerar inte om en resurs använder PsDscRunAsCredential (se [kör DSC med autentiseringsuppgifterna för användaren](../configurations/runAsUser.md))</span><span class="sxs-lookup"><span data-stu-id="eab2a-138">**Issue:** Doesn't work if a resource is using PsDscRunAsCredential (see [Running DSC with user credentials](../configurations/runAsUser.md))</span></span>

- [<span data-ttu-id="eab2a-139">Ange beroenden mellan noder</span><span class="sxs-lookup"><span data-stu-id="eab2a-139">Specifying cross-node dependencies</span></span>](../configurations/crossNodeDependencies.md)

- [<span data-ttu-id="eab2a-140">Resurs-versionshantering</span><span class="sxs-lookup"><span data-stu-id="eab2a-140">Resource versioning</span></span>](../configurations/sxsResource.md)

- <span data-ttu-id="eab2a-141">Pullklient (konfigurationer och resurser) (se [konfigurera en hämtningsklient med konfigurationsnamn](../pull-server/pullClientConfigNames.md))</span><span class="sxs-lookup"><span data-stu-id="eab2a-141">Pull client (configurations & resources) (see [Setting up a pull client using configuration names](../pull-server/pullClientConfigNames.md))</span></span>

- [<span data-ttu-id="eab2a-142">Partiella konfigurationer (pull och push)</span><span class="sxs-lookup"><span data-stu-id="eab2a-142">Partial configurations (pull & push)</span></span>](../pull-server/partialConfigs.md)

- [<span data-ttu-id="eab2a-143">Rapporterar till hämtningsserver</span><span class="sxs-lookup"><span data-stu-id="eab2a-143">Reporting to pull server</span></span>](../pull-server/reportServer.md)

- <span data-ttu-id="eab2a-144">MOF-kryptering</span><span class="sxs-lookup"><span data-stu-id="eab2a-144">MOF encryption</span></span>

- <span data-ttu-id="eab2a-145">Händelseloggning</span><span class="sxs-lookup"><span data-stu-id="eab2a-145">Event logging</span></span>

- <span data-ttu-id="eab2a-146">Azure Automation DSC-rapportering</span><span class="sxs-lookup"><span data-stu-id="eab2a-146">Azure Automation DSC reporting</span></span>

- <span data-ttu-id="eab2a-147">Resurser som är helt funktionella</span><span class="sxs-lookup"><span data-stu-id="eab2a-147">Resources that are fully functional</span></span>

- <span data-ttu-id="eab2a-148">**Arkiv**</span><span class="sxs-lookup"><span data-stu-id="eab2a-148">**Archive**</span></span>
- <span data-ttu-id="eab2a-149">**Miljö**</span><span class="sxs-lookup"><span data-stu-id="eab2a-149">**Environment**</span></span>
- <span data-ttu-id="eab2a-150">**Filen**</span><span class="sxs-lookup"><span data-stu-id="eab2a-150">**File**</span></span>
- <span data-ttu-id="eab2a-151">**Log**</span><span class="sxs-lookup"><span data-stu-id="eab2a-151">**Log**</span></span>
- <span data-ttu-id="eab2a-152">**ProcessSet**</span><span class="sxs-lookup"><span data-stu-id="eab2a-152">**ProcessSet**</span></span>
- <span data-ttu-id="eab2a-153">**registret**</span><span class="sxs-lookup"><span data-stu-id="eab2a-153">**Registry**</span></span>
- <span data-ttu-id="eab2a-154">**Skriptet**</span><span class="sxs-lookup"><span data-stu-id="eab2a-154">**Script**</span></span>
- <span data-ttu-id="eab2a-155">**WindowsPackageCab**</span><span class="sxs-lookup"><span data-stu-id="eab2a-155">**WindowsPackageCab**</span></span>
- <span data-ttu-id="eab2a-156">**WindowsProcess**</span><span class="sxs-lookup"><span data-stu-id="eab2a-156">**WindowsProcess**</span></span>
- <span data-ttu-id="eab2a-157">**WaitForAll** (se [att ange beroenden mellan noder](../configurations/crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="eab2a-157">**WaitForAll** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>
- <span data-ttu-id="eab2a-158">**WaitForAny** (se [att ange beroenden mellan noder](../configurations/crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="eab2a-158">**WaitForAny** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>
- <span data-ttu-id="eab2a-159">**WaitForSome** (se [att ange beroenden mellan noder](../configurations/crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="eab2a-159">**WaitForSome** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>

- <span data-ttu-id="eab2a-160">Resurser som delvis fungerar</span><span class="sxs-lookup"><span data-stu-id="eab2a-160">Resources that are partially functional</span></span>
- <span data-ttu-id="eab2a-161">**Grupp**</span><span class="sxs-lookup"><span data-stu-id="eab2a-161">**Group**</span></span>
- <span data-ttu-id="eab2a-162">**GroupSet**</span><span class="sxs-lookup"><span data-stu-id="eab2a-162">**GroupSet**</span></span>

  <span data-ttu-id="eab2a-163">**Problem:** Ovan resurser misslyckas om specifika instans kallas två gånger (som kör samma konfiguration för två gånger)</span><span class="sxs-lookup"><span data-stu-id="eab2a-163">**Issue:** Above resources fail if specific instance is called twice (running the same configuration twice)</span></span>

- <span data-ttu-id="eab2a-164">**Tjänsten**</span><span class="sxs-lookup"><span data-stu-id="eab2a-164">**Service**</span></span>
- <span data-ttu-id="eab2a-165">**ServiceSet**</span><span class="sxs-lookup"><span data-stu-id="eab2a-165">**ServiceSet**</span></span>

  <span data-ttu-id="eab2a-166">**Problem:** Fungerar bara för Starta/Stoppa tjänst (status).</span><span class="sxs-lookup"><span data-stu-id="eab2a-166">**Issue:** Only works for starting/stopping (status) service.</span></span> <span data-ttu-id="eab2a-167">Misslyckas om någon försöker ändra andra attribut som startuptype för, autentiseringsuppgifter, beskrivning osv...</span><span class="sxs-lookup"><span data-stu-id="eab2a-167">Fails, if one tries to change other service attributes like startuptype, credentials, description etc..</span></span> <span data-ttu-id="eab2a-168">Felet uppstod är ungefär:</span><span class="sxs-lookup"><span data-stu-id="eab2a-168">The error thrown is similar to:</span></span>

  <span data-ttu-id="eab2a-169">*Det går inte att hitta typen [management.managementobject]: Kontrollera att sammansättningen som innehåller den här typen har lästs in.*</span><span class="sxs-lookup"><span data-stu-id="eab2a-169">*Cannot find type [management.managementobject]: verify that the assembly containing this type is loaded.*</span></span>

- <span data-ttu-id="eab2a-170">Resurser som inte fungerar</span><span class="sxs-lookup"><span data-stu-id="eab2a-170">Resources that are not functional</span></span>
- <span data-ttu-id="eab2a-171">**Användaren**</span><span class="sxs-lookup"><span data-stu-id="eab2a-171">**User**</span></span>

## <a name="dsc-features-not-available-on-nano-server"></a><span data-ttu-id="eab2a-172">DSC-funktioner som inte är tillgängliga på Nano Server</span><span class="sxs-lookup"><span data-stu-id="eab2a-172">DSC features not available on Nano Server</span></span>

<span data-ttu-id="eab2a-173">Följande DSC-funktioner är inte tillgängliga på Nano Server:</span><span class="sxs-lookup"><span data-stu-id="eab2a-173">The following DSC features are not currently available on Nano Server:</span></span>

- <span data-ttu-id="eab2a-174">Dekryptera MOF-dokument med krypterade password(s)</span><span class="sxs-lookup"><span data-stu-id="eab2a-174">Decrypting MOF document with encrypted password(s)</span></span>
- <span data-ttu-id="eab2a-175">Hämtningsservern – du kan inte för närvarande konfigurera en pull-server på Nano Server</span><span class="sxs-lookup"><span data-stu-id="eab2a-175">Pull Server--you cannot currently set up a pull server on Nano Server</span></span>
- <span data-ttu-id="eab2a-176">Något som inte är i listan över funktionen fungerar</span><span class="sxs-lookup"><span data-stu-id="eab2a-176">Anything that is not in the list of feature works</span></span>

## <a name="using-custom-dsc-resources-on-nano-server"></a><span data-ttu-id="eab2a-177">Använda anpassade DSC-resurser på Nano Server</span><span class="sxs-lookup"><span data-stu-id="eab2a-177">Using custom DSC resources on Nano Server</span></span>

<span data-ttu-id="eab2a-178">På grund av en begränsad uppsättning Windows API: er och CLR-bibliotek som är tillgängliga på Nano Server fungerar DSC-resurser som arbetar med den fullständiga CLR-versionen av Windows inte nödvändigtvis på Nano Server.</span><span class="sxs-lookup"><span data-stu-id="eab2a-178">Due to a limited sets of Windows APIs and CLR libraries available on Nano Server, DSC resources that work on the full CLR version of Windows do not necessarily work on Nano Server.</span></span>
<span data-ttu-id="eab2a-179">Slutför slutpunkt till slutpunkt testning innan du distribuerar eventuella anpassade DSC-resurser till en produktionsmiljö.</span><span class="sxs-lookup"><span data-stu-id="eab2a-179">Complete end-to-end testing before deploying any DSC custom resources to a production environment.</span></span>

## <a name="see-also"></a><span data-ttu-id="eab2a-180">Se även</span><span class="sxs-lookup"><span data-stu-id="eab2a-180">See Also</span></span>

- [<span data-ttu-id="eab2a-181">Komma igång med Nano Server</span><span class="sxs-lookup"><span data-stu-id="eab2a-181">Getting Started with Nano Server</span></span>](/windows-server/get-started/getting-started-with-nano-server)
