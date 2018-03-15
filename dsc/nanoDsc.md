---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: "Använder DSC på Nano Server"
ms.openlocfilehash: c8f3669ee9c2ed6107c14ba9f4460d82276e1932
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/15/2018
---
# <a name="using-dsc-on-nano-server"></a><span data-ttu-id="18a8c-103">Använder DSC på Nano Server</span><span class="sxs-lookup"><span data-stu-id="18a8c-103">Using DSC on Nano Server</span></span>

> <span data-ttu-id="18a8c-104">Gäller för: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="18a8c-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="18a8c-105">**DSC på Nano Server** är ett valfritt paket i den `NanoServer\Packages` mapp på Windows Server 2016-mediet.</span><span class="sxs-lookup"><span data-stu-id="18a8c-105">**DSC on Nano Server** is an optional package in the `NanoServer\Packages` folder of the Windows Server 2016 media.</span></span> <span data-ttu-id="18a8c-106">Paketet kan installeras när du skapar en virtuell Hårddisk för en Nano Server genom att ange **Microsoft-NanoServer-DSC-Package** som värde för den **paket** parameter för den **ny NanoServerImage**  funktion.</span><span class="sxs-lookup"><span data-stu-id="18a8c-106">The package can be installed when you create a VHD for a Nano Server by specifying **Microsoft-NanoServer-DSC-Package** as the value of the **Packages** parameter of the **New-NanoServerImage** function.</span></span> <span data-ttu-id="18a8c-107">Till exempel om du skapar en virtuell Hårddisk för en virtuell dator, skulle kommandot se ut så här:</span><span class="sxs-lookup"><span data-stu-id="18a8c-107">For example, if you are creating a VHD for a virtual machine, the command would look like the following:</span></span>

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

<span data-ttu-id="18a8c-108">Mer information om hur du installerar och använder Nano Server, samt hur du hanterar Nano Server med PowerShell-fjärrkommunikation finns [komma igång med Nano Server](https://technet.microsoft.com/library/mt126167.aspx).</span><span class="sxs-lookup"><span data-stu-id="18a8c-108">For information about installing and using Nano Server, as well as how to manage Nano Server with PowerShell Remoting, see [Getting Started with Nano Server](https://technet.microsoft.com/library/mt126167.aspx).</span></span>


## <a name="dsc-features-available-on-nano-server"></a><span data-ttu-id="18a8c-109">DSC-funktioner som är tillgängliga på Nano Server</span><span class="sxs-lookup"><span data-stu-id="18a8c-109">DSC features available on Nano Server</span></span>

 <span data-ttu-id="18a8c-110">Eftersom Nano Server stöder endast en begränsad uppsättning API: er jämfört med en fullständig version av Windows Server, har DSC på Nano Server inte fullständig jämlika med DSC som körs på fullständig SKU: er för närvarande.</span><span class="sxs-lookup"><span data-stu-id="18a8c-110">Because Nano Server supports only a limited set of APIs compared to a full version of Windows Server, DSC on Nano Server does not have full functional parity with DSC running on full SKUs for the time being.</span></span> <span data-ttu-id="18a8c-111">DSC på Nano Server är i aktiv utveckling och ännu inte är funktionen som är klar.</span><span class="sxs-lookup"><span data-stu-id="18a8c-111">DSC on Nano Server is in active development and is not yet feature complete.</span></span>
 
 <span data-ttu-id="18a8c-112">Följande DSC-funktioner är tillgängliga på Nano Server:</span><span class="sxs-lookup"><span data-stu-id="18a8c-112">The following DSC features are currently available on Nano Server:</span></span> 


* <span data-ttu-id="18a8c-113">Både sändning och mottagning lägen</span><span class="sxs-lookup"><span data-stu-id="18a8c-113">Both push and pull modes</span></span>

* <span data-ttu-id="18a8c-114">Alla DSC-cmdletar som finns på en fullständig version av Windows Server, inklusive följande:</span><span class="sxs-lookup"><span data-stu-id="18a8c-114">All DSC cmdlets that exist on a full version of Windows Server, including the following:</span></span> 
  * [<span data-ttu-id="18a8c-115">Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="18a8c-115">Get-DscLocalConfigurationManager</span></span>](https://technet.microsoft.com/library/dn407378.aspx)
  * [<span data-ttu-id="18a8c-116">Set-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="18a8c-116">Set-DscLocalConfigurationManager</span></span>](https://technet.microsoft.com/library/dn521621.aspx)     
  * [<span data-ttu-id="18a8c-117">Aktivera DscDebug</span><span class="sxs-lookup"><span data-stu-id="18a8c-117">Enable-DscDebug</span></span>](https://technet.microsoft.com/en-us/library/mt517870.aspx)
  * [<span data-ttu-id="18a8c-118">Inaktivera DscDebug</span><span class="sxs-lookup"><span data-stu-id="18a8c-118">Disable-DscDebug</span></span>](https://technet.microsoft.com/en-us/library/mt517872.aspx)       
  * [<span data-ttu-id="18a8c-119">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="18a8c-119">Start-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/dn521623.aspx)
  * [<span data-ttu-id="18a8c-120">Stoppa DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="18a8c-120">Stop-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/mt143542.aspx)
  * [<span data-ttu-id="18a8c-121">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="18a8c-121">Get-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/dn407379.aspx)
  * [<span data-ttu-id="18a8c-122">Testa DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="18a8c-122">Test-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/dn407382.aspx)      
  * [<span data-ttu-id="18a8c-123">Publish-DscConfiguraiton</span><span class="sxs-lookup"><span data-stu-id="18a8c-123">Publish-DscConfiguraiton</span></span>](https://technet.microsoft.com/en-us/library/mt517875.aspx) 
  * [<span data-ttu-id="18a8c-124">Uppdatera DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="18a8c-124">Update-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/mt143541.aspx)
  * [<span data-ttu-id="18a8c-125">Återställ DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="18a8c-125">Restore-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/dn407383.aspx)
  * [<span data-ttu-id="18a8c-126">Remove-DscConfigurationDocument</span><span class="sxs-lookup"><span data-stu-id="18a8c-126">Remove-DscConfigurationDocument</span></span>](https://technet.microsoft.com/en-us/library/mt143544.aspx)
  * [<span data-ttu-id="18a8c-127">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="18a8c-127">Get-DscConfigurationStatus</span></span>](https://technet.microsoft.com/en-us/library/mt517868.aspx)
  * [<span data-ttu-id="18a8c-128">Invoke-DscResource</span><span class="sxs-lookup"><span data-stu-id="18a8c-128">Invoke-DscResource</span></span>](https://technet.microsoft.com/en-us/library/mt517869.aspx)
  * [<span data-ttu-id="18a8c-129">Hitta DscResource</span><span class="sxs-lookup"><span data-stu-id="18a8c-129">Find-DscResource</span></span>](https://technet.microsoft.com/en-us/library/mt517874.aspx)
  * [<span data-ttu-id="18a8c-130">Get-DscResource</span><span class="sxs-lookup"><span data-stu-id="18a8c-130">Get-DscResource</span></span>](https://technet.microsoft.com/en-us/library/dn521625.aspx)
  * [<span data-ttu-id="18a8c-131">Ny DscChecksum</span><span class="sxs-lookup"><span data-stu-id="18a8c-131">New-DscChecksum</span></span>](https://technet.microsoft.com/en-us/library/dn521622.aspx)    

* <span data-ttu-id="18a8c-132">Kompilera konfigurationer (se [DSC-konfigurationer](configurations.md))</span><span class="sxs-lookup"><span data-stu-id="18a8c-132">Compiling configurations (see [DSC configurations](configurations.md))</span></span>

  <span data-ttu-id="18a8c-133">**Problem:** lösenordskryptering (se [skydda MOF-filen](securemof.md)) under konfigurationen kompilering fungerar inte.</span><span class="sxs-lookup"><span data-stu-id="18a8c-133">**Issue:** Password encryption (see [Securing the MOF File](securemof.md)) during configuration compilation doesn't work.</span></span>

* <span data-ttu-id="18a8c-134">Kompilera metaconfigurations (se [konfigurera den lokala Configuration Manager](metaConfig.md))</span><span class="sxs-lookup"><span data-stu-id="18a8c-134">Compiling metaconfigurations (see [Configuring the Local Configuration Manager](metaConfig.md))</span></span>

* <span data-ttu-id="18a8c-135">Kör en resurs under användarkontext (se [kör DSC med autentiseringsuppgifterna för användaren (RunAs)](runAsUser.md))</span><span class="sxs-lookup"><span data-stu-id="18a8c-135">Running a resource under user context (see [Running DSC with user credentials (RunAs)](runAsUser.md))</span></span>

* <span data-ttu-id="18a8c-136">Klass-baserade resurser (se [skriva en anpassad DSC-resurs med PowerShell klasser](authoringResourceClass.md))</span><span class="sxs-lookup"><span data-stu-id="18a8c-136">Class-based resources (see [Writing a custom DSC resource with PowerShell classes](authoringResourceClass.md))</span></span>

* <span data-ttu-id="18a8c-137">Felsökning av DSC-resurser (se [felsökning DSC resurser](debugresource.md))</span><span class="sxs-lookup"><span data-stu-id="18a8c-137">Debugging of DSC resources (see [Debugging DSC resources](debugresource.md))</span></span>
  
  <span data-ttu-id="18a8c-138">**Problem:** fungerar inte om en resurs använder PsDscRunAsCredential (se [kör DSC med autentiseringsuppgifterna för användaren](runAsUser.md))</span><span class="sxs-lookup"><span data-stu-id="18a8c-138">**Issue:** Doesn't work if a resource is using PsDscRunAsCredential (see [Running DSC with user credentials](runAsUser.md))</span></span>

* [<span data-ttu-id="18a8c-139">Ange beroenden mellan noder</span><span class="sxs-lookup"><span data-stu-id="18a8c-139">Specifying cross-node dependencies</span></span>](crossNodeDependencies.md) 

* [<span data-ttu-id="18a8c-140">Resursen versionshantering</span><span class="sxs-lookup"><span data-stu-id="18a8c-140">Resource versioning</span></span>](sxsResource.md)

* <span data-ttu-id="18a8c-141">Pull-klienten (konfigurationer och resurser) (se [ställa in en pull-klient som använder konfigurationsnamn](pullClientConfigNames.md))</span><span class="sxs-lookup"><span data-stu-id="18a8c-141">Pull client (configurations & resources) (see [Setting up a pull client using configuration names](pullClientConfigNames.md))</span></span>

* [<span data-ttu-id="18a8c-142">Partiell konfigurationer (pull och push)</span><span class="sxs-lookup"><span data-stu-id="18a8c-142">Partial configurations (pull & push)</span></span>](partialConfigs.md)

* [<span data-ttu-id="18a8c-143">Rapporterar till pull-server</span><span class="sxs-lookup"><span data-stu-id="18a8c-143">Reporting to pull server</span></span>](reportServer.md) 

* <span data-ttu-id="18a8c-144">MOF-kryptering</span><span class="sxs-lookup"><span data-stu-id="18a8c-144">MOF encryption</span></span>

* <span data-ttu-id="18a8c-145">Händelseloggning</span><span class="sxs-lookup"><span data-stu-id="18a8c-145">Event logging</span></span>

* <span data-ttu-id="18a8c-146">Azure Automation DSC-rapportering</span><span class="sxs-lookup"><span data-stu-id="18a8c-146">Azure Automation DSC reporting</span></span>

* <span data-ttu-id="18a8c-147">Resurser som är helt funktionella</span><span class="sxs-lookup"><span data-stu-id="18a8c-147">Resources that are fully functional</span></span>
  * [<span data-ttu-id="18a8c-148">Arkiv</span><span class="sxs-lookup"><span data-stu-id="18a8c-148">Archive</span></span>](archiveResource.md)
  * [<span data-ttu-id="18a8c-149">Miljö</span><span class="sxs-lookup"><span data-stu-id="18a8c-149">Environment</span></span>](environmentResource.md)
  * [<span data-ttu-id="18a8c-150">Filen</span><span class="sxs-lookup"><span data-stu-id="18a8c-150">File</span></span>](fileResource.md)
  * [<span data-ttu-id="18a8c-151">Logg</span><span class="sxs-lookup"><span data-stu-id="18a8c-151">Log</span></span>](logResource.md)
  * <span data-ttu-id="18a8c-152">ProcessSet</span><span class="sxs-lookup"><span data-stu-id="18a8c-152">ProcessSet</span></span>
  * [<span data-ttu-id="18a8c-153">Registret</span><span class="sxs-lookup"><span data-stu-id="18a8c-153">Registry</span></span>](registryResource.md)
  * [<span data-ttu-id="18a8c-154">Skriptet</span><span class="sxs-lookup"><span data-stu-id="18a8c-154">Script</span></span>](scriptResource.md)
  * <span data-ttu-id="18a8c-155">WindowsPackageCab</span><span class="sxs-lookup"><span data-stu-id="18a8c-155">WindowsPackageCab</span></span>
  * [<span data-ttu-id="18a8c-156">WindowsProcess</span><span class="sxs-lookup"><span data-stu-id="18a8c-156">WindowsProcess</span></span>](windowsProcessResource.md)
  * <span data-ttu-id="18a8c-157">WaitForAll (se [angett beroenden mellan noder](crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="18a8c-157">WaitForAll (see [Specifying cross-node dependencies](crossNodeDependencies.md))</span></span>
  * <span data-ttu-id="18a8c-158">WaitForAny (se [angett beroenden mellan noder](crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="18a8c-158">WaitForAny (see [Specifying cross-node dependencies](crossNodeDependencies.md))</span></span>
  * <span data-ttu-id="18a8c-159">WaitForSome (se [angett beroenden mellan noder](crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="18a8c-159">WaitForSome (see [Specifying cross-node dependencies](crossNodeDependencies.md))</span></span>

* <span data-ttu-id="18a8c-160">Resurser som delvis fungerar</span><span class="sxs-lookup"><span data-stu-id="18a8c-160">Resources that are partially functional</span></span>
  * [<span data-ttu-id="18a8c-161">Grupp</span><span class="sxs-lookup"><span data-stu-id="18a8c-161">Group</span></span>](groupResource.md)
  * <span data-ttu-id="18a8c-162">GroupSet</span><span class="sxs-lookup"><span data-stu-id="18a8c-162">GroupSet</span></span>
  
  <span data-ttu-id="18a8c-163">**Problem:** ovan resurser misslyckas om specifika instansen anropas två gånger (körs två gånger i samma konfiguration)</span><span class="sxs-lookup"><span data-stu-id="18a8c-163">**Issue:** Above resources fail if specific instance is called twice (running the same configuration twice)</span></span>
  
  * [<span data-ttu-id="18a8c-164">Tjänsten</span><span class="sxs-lookup"><span data-stu-id="18a8c-164">Service</span></span>](serviceResource.md)
  * <span data-ttu-id="18a8c-165">ServiceSet</span><span class="sxs-lookup"><span data-stu-id="18a8c-165">ServiceSet</span></span>
  
  <span data-ttu-id="18a8c-166">**Problem:** fungerar bara för Starta/Stoppa tjänst (status).</span><span class="sxs-lookup"><span data-stu-id="18a8c-166">**Issue:** Only works for starting/stopping (status) service.</span></span> <span data-ttu-id="18a8c-167">Misslyckas om någon försöker ändra andra attribut som startuptype, autentiseringsuppgifter, beskrivning etc...</span><span class="sxs-lookup"><span data-stu-id="18a8c-167">Fails, if one tries to change other service attributes like startuptype, credentials, description etc..</span></span> <span data-ttu-id="18a8c-168">Felet uppstod liknar:</span><span class="sxs-lookup"><span data-stu-id="18a8c-168">The error thrown is similar to:</span></span>
  
  <span data-ttu-id="18a8c-169">*Det går inte att hitta typen [management.managementobject]: Kontrollera att sammansättningen som innehåller den här typen är inläst.*</span><span class="sxs-lookup"><span data-stu-id="18a8c-169">*Cannot find type [management.managementobject]: verify that the assembly containing this type is loaded.*</span></span>
  
* <span data-ttu-id="18a8c-170">Resurser som inte fungerar</span><span class="sxs-lookup"><span data-stu-id="18a8c-170">Resources that are not functional</span></span>
  * [<span data-ttu-id="18a8c-171">Användaren</span><span class="sxs-lookup"><span data-stu-id="18a8c-171">User</span></span>](userResource.md)
  

## <a name="dsc-features-not-available-on-nano-server"></a><span data-ttu-id="18a8c-172">DSC-funktioner som inte finns på Nano Server</span><span class="sxs-lookup"><span data-stu-id="18a8c-172">DSC features not available on Nano Server</span></span>

<span data-ttu-id="18a8c-173">Följande DSC-funktioner är inte tillgängliga på Nano Server:</span><span class="sxs-lookup"><span data-stu-id="18a8c-173">The following DSC features are not currently available on Nano Server:</span></span>

* <span data-ttu-id="18a8c-174">Dekryptera MOF-dokument med krypterade password(s)</span><span class="sxs-lookup"><span data-stu-id="18a8c-174">Decrypting MOF document with encrypted password(s)</span></span> 
* <span data-ttu-id="18a8c-175">Pull-Server – du kan inte just nu konfigurera en pull-server på Nano Server</span><span class="sxs-lookup"><span data-stu-id="18a8c-175">Pull Server--you cannot currently set up a pull server on Nano Server</span></span>
* <span data-ttu-id="18a8c-176">Något som inte finns med i listan över funktionen fungerar</span><span class="sxs-lookup"><span data-stu-id="18a8c-176">Anything that is not in the list of feature works</span></span>

## <a name="using-custom-dsc-resources-on-nano-server"></a><span data-ttu-id="18a8c-177">Med hjälp av anpassade DSC-resurser på Nano Server</span><span class="sxs-lookup"><span data-stu-id="18a8c-177">Using custom DSC resources on Nano Server</span></span>
 
<span data-ttu-id="18a8c-178">På grund av en begränsade uppsättningar av Windows API: er och CLR-bibliotek som är tillgängliga på Nano Server fungerar DSC-resurser som kan användas i den fullständiga CLR-versionen av Windows inte nödvändigtvis på Nano Server.</span><span class="sxs-lookup"><span data-stu-id="18a8c-178">Due to a limited sets of Windows APIs and CLR libraries available on Nano Server, DSC resources that work on the full CLR version of Windows do not necessarily work on Nano Server.</span></span> <span data-ttu-id="18a8c-179">Slutföra slutpunkt till slutpunkt testning innan du distribuerar några anpassade DSC-resurser i en produktionsmiljö.</span><span class="sxs-lookup"><span data-stu-id="18a8c-179">Complete end-to-end testing before deploying any DSC custom resources to a production environment.</span></span>

## <a name="see-also"></a><span data-ttu-id="18a8c-180">Se även</span><span class="sxs-lookup"><span data-stu-id="18a8c-180">See Also</span></span>
- [<span data-ttu-id="18a8c-181">Komma igång med Nano Server</span><span class="sxs-lookup"><span data-stu-id="18a8c-181">Getting Started with Nano Server</span></span>](https://technet.microsoft.com/library/mt126167.aspx)

