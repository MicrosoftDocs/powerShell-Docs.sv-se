---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: "Hämta server bästa praxis"
ms.openlocfilehash: 3d0ab969b7a0de9d428becc4b9bdb124a7a44c2c
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/15/2018
---
# <a name="pull-server-best-practices"></a><span data-ttu-id="606b8-103">Hämta server bästa praxis</span><span class="sxs-lookup"><span data-stu-id="606b8-103">Pull server best practices</span></span>

><span data-ttu-id="606b8-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="606b8-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="606b8-105">Sammanfattning: Det här dokumentet är avsett att inkludera processen och utökningsbarhet att hjälpa tekniker som förbereder för lösningen.</span><span class="sxs-lookup"><span data-stu-id="606b8-105">Summary: This document is intended to include process and extensibility to assist engineers who are preparing for the solution.</span></span> <span data-ttu-id="606b8-106">Information bör ge bästa praxis som identifieras av kunder och sedan verifieras av Produktteamet för att säkerställa rekommendationer framtida riktade och anses vara stabil.</span><span class="sxs-lookup"><span data-stu-id="606b8-106">Details should provide best practices as identified by customers and then validated by the product team to ensure recommendations are future facing and considered stable.</span></span>

| |<span data-ttu-id="606b8-107">Doc-Info</span><span class="sxs-lookup"><span data-stu-id="606b8-107">Doc Info</span></span>|
|:---|:---|
<span data-ttu-id="606b8-108">författare</span><span class="sxs-lookup"><span data-stu-id="606b8-108">Author</span></span> | <span data-ttu-id="606b8-109">Michael Greene</span><span class="sxs-lookup"><span data-stu-id="606b8-109">Michael Greene</span></span>  
<span data-ttu-id="606b8-110">Granskare</span><span class="sxs-lookup"><span data-stu-id="606b8-110">Reviewers</span></span> | <span data-ttu-id="606b8-111">Ben Gelens, Ravikanth Chaganti Aleksandar Nikolic</span><span class="sxs-lookup"><span data-stu-id="606b8-111">Ben Gelens, Ravikanth Chaganti, Aleksandar Nikolic</span></span>  
<span data-ttu-id="606b8-112">Publicerade</span><span class="sxs-lookup"><span data-stu-id="606b8-112">Published</span></span> | <span data-ttu-id="606b8-113">April 2015</span><span class="sxs-lookup"><span data-stu-id="606b8-113">April, 2015</span></span>

## <a name="abstract"></a><span data-ttu-id="606b8-114">Abstrakt</span><span class="sxs-lookup"><span data-stu-id="606b8-114">Abstract</span></span>

<span data-ttu-id="606b8-115">Det här dokumentet är utformad att ge officiella vägledning för alla planera för en Windows PowerShell Desired State Configuration pull-serverimplementering.</span><span class="sxs-lookup"><span data-stu-id="606b8-115">This document is designed to provide official guidance for anyone planning for a Windows PowerShell Desired State Configuration pull server implementation.</span></span> <span data-ttu-id="606b8-116">En pull-server är en enkel tjänst som tar endast minuter att distribuera.</span><span class="sxs-lookup"><span data-stu-id="606b8-116">A pull server is a simple service that should take only minutes to deploy.</span></span> <span data-ttu-id="606b8-117">Även om det här dokumentet kommer att erbjuda teknisk vägledning som kan användas i en distribution, är värdet för det här dokumentet som en referens för bästa praxis och vad du ska tänka på innan du distribuerar.</span><span class="sxs-lookup"><span data-stu-id="606b8-117">Although this document will offer technical how-to guidance that can be used in a deployment, the value of this document is as a reference for best practices and what to think about before deploying.</span></span>
<span data-ttu-id="606b8-118">Läsare bör ha grundläggande kunskaper med DSC och de termer som används för att beskriva komponenterna som ingår i en DSC-distribution.</span><span class="sxs-lookup"><span data-stu-id="606b8-118">Readers should have basic familiarity with DSC, and the terms used to describe the components that are included in a DSC deployment.</span></span> <span data-ttu-id="606b8-119">Mer information finns i [Windows PowerShell Desired Configuration översikt över](https://technet.microsoft.com/library/dn249912.aspx) avsnittet.</span><span class="sxs-lookup"><span data-stu-id="606b8-119">For more information, see the [Windows PowerShell Desired State Configuration Overview](https://technet.microsoft.com/library/dn249912.aspx)  topic.</span></span>
<span data-ttu-id="606b8-120">Som DSC är förväntat att utvecklas i molnet takt förväntas också den underliggande tekniken inklusive hämtningsservern att utvecklas och ger nya möjligheter.</span><span class="sxs-lookup"><span data-stu-id="606b8-120">As DSC is expected to evolve at cloud cadence, the underlying technology including pull server is also expected to evolve and to introduce new capabilities.</span></span> <span data-ttu-id="606b8-121">Det här dokumentet innehåller en versionstabell i tillägget som innehåller referenser till tidigare versioner och referenser till framtida söker lösningar för att uppmuntra framtida Designer.</span><span class="sxs-lookup"><span data-stu-id="606b8-121">This document includes a version table in the appendix that provides references to previous releases and references to future looking solutions to encourage forward-looking designs.</span></span>

<span data-ttu-id="606b8-122">Det här dokumentet två huvuddelar:</span><span class="sxs-lookup"><span data-stu-id="606b8-122">The two major sections of this document:</span></span>

 - <span data-ttu-id="606b8-123">Planera konfiguration</span><span class="sxs-lookup"><span data-stu-id="606b8-123">Configuration Planning</span></span>
 - <span data-ttu-id="606b8-124">Installationsguiden</span><span class="sxs-lookup"><span data-stu-id="606b8-124">Installation Guide</span></span>
 
### <a name="versions-of-the-windows-management-framework"></a><span data-ttu-id="606b8-125">Versioner av Windows Management Framework</span><span class="sxs-lookup"><span data-stu-id="606b8-125">Versions of the Windows Management Framework</span></span> 
<span data-ttu-id="606b8-126">Informationen i det här dokumentet är avsedd att tillämpa på Windows Management Framework 5.0.</span><span class="sxs-lookup"><span data-stu-id="606b8-126">The information in this document is intended to apply to Windows Management Framework 5.0.</span></span> <span data-ttu-id="606b8-127">WMF 5.0 inte krävs för distribution och drift av en pull-server, är version 5.0 fokus för det här dokumentet.</span><span class="sxs-lookup"><span data-stu-id="606b8-127">While WMF 5.0 is not required for deploying and operating a pull server, version 5.0 is the focus of this document.</span></span>

### <a name="windows-powershell-desired-state-configuration"></a><span data-ttu-id="606b8-128">Windows PowerShell önskad Tillståndskonfiguration</span><span class="sxs-lookup"><span data-stu-id="606b8-128">Windows PowerShell Desired State Configuration</span></span>
<span data-ttu-id="606b8-129">Önskat tillstånd Configuration (DSC) är en plattform som gör att distribuera och hantera konfigurationsdata med hjälp av en branschen syntax som heter Managed Object Format (MOF) för att beskriva Common Information Model (CIM).</span><span class="sxs-lookup"><span data-stu-id="606b8-129">Desired State Configuration (DSC) is a management platform that enables deploying and managing configuration data by using an industry syntax named the Managed Object Format (MOF) to describe the Common Information Model (CIM).</span></span> <span data-ttu-id="606b8-130">Det finns ett projekt med öppen källkod, Open Management Infrastructure (OMI), för att ytterligare utvecklingen av dessa normer över plattformar, inklusive Linux och -maskinvara, operativsystem.</span><span class="sxs-lookup"><span data-stu-id="606b8-130">An open source project, Open Management Infrastructure (OMI), exists to further development of these standards across platforms including Linux and network hardware operating systems.</span></span> <span data-ttu-id="606b8-131">Mer information finns i [DMTF sida länkar till MOF-specifikationer](http://dmtf.org/standards/cim), och [OMI dokument och källan](https://collaboration.opengroup.org/omi/documents.php).</span><span class="sxs-lookup"><span data-stu-id="606b8-131">For more information, see the [DMTF page linking to MOF specifications](http://dmtf.org/standards/cim), and [OMI Documents and Source](https://collaboration.opengroup.org/omi/documents.php).</span></span>

<span data-ttu-id="606b8-132">Windows PowerShell innehåller en uppsättning tillägg för Desired State Configuration som du kan använda för att skapa och hantera deklarativ konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="606b8-132">Windows PowerShell provides a set of language extensions for Desired State Configuration that you can use to create and manage declarative configurations.</span></span>

### <a name="pull-server-role"></a><span data-ttu-id="606b8-133">Pull-serverrollen</span><span class="sxs-lookup"><span data-stu-id="606b8-133">Pull server role</span></span>  
<span data-ttu-id="606b8-134">En pull-server är en centraliserad tjänst för att lagra konfigurationer som kommer att vara tillgänglig för målnoder.</span><span class="sxs-lookup"><span data-stu-id="606b8-134">A pull server provides a centralized service to store configurations that will be accessible to target nodes.</span></span>
 
<span data-ttu-id="606b8-135">Pull-serverrollen kan distribueras som en webbserver-instans eller en SMB filresurs.</span><span class="sxs-lookup"><span data-stu-id="606b8-135">The pull server role can be deployed as either a Web Server instance or an SMB file share.</span></span> <span data-ttu-id="606b8-136">Web server-kapacitet innehåller ett OData-gränssnitt och att inkludera välja funktioner för målnoder rapporterar bekräftelse av lyckats eller misslyckats eftersom konfigurationer tillämpas.</span><span class="sxs-lookup"><span data-stu-id="606b8-136">The web server capability includes an OData interface and can optionally include capabilities for target nodes to report back confirmation of success or failure as configurations are applied.</span></span> <span data-ttu-id="606b8-137">Den här funktionen är användbar i miljöer där det finns ett stort antal målnoder.</span><span class="sxs-lookup"><span data-stu-id="606b8-137">This functionality is useful in environments where there are a large number of target nodes.</span></span> <span data-ttu-id="606b8-138">När du har konfigurerat en målnod (kallas även en klient) för att peka på hämtningsservern i den senaste konfigurationen hämtas och aktiveras data och alla nödvändiga skript.</span><span class="sxs-lookup"><span data-stu-id="606b8-138">After configuring a target node (also referred to as a client) to point to the pull server the latest configuration data and any required scripts are downloaded and applied.</span></span> <span data-ttu-id="606b8-139">Detta kan inträffa som en enstaka distribution eller som ett nytt förekommer jobb som är dessutom hämtningsservern i en viktig tillgång för att hantera ändring i större skala.</span><span class="sxs-lookup"><span data-stu-id="606b8-139">This can happen as a one-time deployment or as a re-occurring job which also makes the pull server an important asset for managing change at scale.</span></span> <span data-ttu-id="606b8-140">Mer information finns i [Windows PowerShell önskad tillstånd hämtar Konfigurationsservrar](https://technet.microsoft.com/library/dn249913.aspx) och [Push och Pull-konfigurationslägen](https://technet.microsoft.com/library/dn249913.aspx).</span><span class="sxs-lookup"><span data-stu-id="606b8-140">For more information, see [Windows PowerShell Desired State Configuration Pull Servers](https://technet.microsoft.com/library/dn249913.aspx) and [Push and Pull Configuration Modes](https://technet.microsoft.com/library/dn249913.aspx).</span></span>

## <a name="configuration-planning"></a><span data-ttu-id="606b8-141">Planera konfiguration</span><span class="sxs-lookup"><span data-stu-id="606b8-141">Configuration planning</span></span>

<span data-ttu-id="606b8-142">För alla företag programdistribution finns information som samlas in i förväg för att planera för rätt arkitektur och förberedas för de steg som krävs för att slutföra distributionen.</span><span class="sxs-lookup"><span data-stu-id="606b8-142">For any enterprise software deployment there is information that can be collected in advance to help plan for the correct architecture and to be prepared for the steps required to complete the deployment.</span></span> <span data-ttu-id="606b8-143">Följande avsnitt innehåller information om hur du förbereder och de organisatoriska anslutningar som behöver förmodligen inträffa i förväg.</span><span class="sxs-lookup"><span data-stu-id="606b8-143">The following sections provide information regarding how to prepare and the organizational connections that will likely need to happen in advance.</span></span>

### <a name="software-requirements"></a><span data-ttu-id="606b8-144">Programvarukrav</span><span class="sxs-lookup"><span data-stu-id="606b8-144">Software requirements</span></span>

<span data-ttu-id="606b8-145">Distribution av en pull-server kräver funktionen DSC-tjänsten i Windows Server.</span><span class="sxs-lookup"><span data-stu-id="606b8-145">Deployment of a pull server requires the DSC Service feature of Windows Server.</span></span> <span data-ttu-id="606b8-146">Den här funktionen introducerades i Windows Server 2012 och har uppdaterats via pågående versioner av Windows Management Framework (WMF).</span><span class="sxs-lookup"><span data-stu-id="606b8-146">This feature was introduced in Windows Server 2012, and has been updated through ongoing releases of Windows Management Framework (WMF).</span></span>

### <a name="software-downloads"></a><span data-ttu-id="606b8-147">Nedladdning av programvara</span><span class="sxs-lookup"><span data-stu-id="606b8-147">Software downloads</span></span>

<span data-ttu-id="606b8-148">Förutom att installera det senaste innehållet från Windows Update finns två hämtningar anses vara bästa praxis för att distribuera en DSC pull-server: den senaste versionen av Windows Management Framework och en DSC-modul för att automatisera etablering av pull-servrar.</span><span class="sxs-lookup"><span data-stu-id="606b8-148">In addition to installing the latest content from Windows Update, there are two downloads considered best practice to deploy a DSC pull server: The latest version of Windows Management Framework, and a DSC module to automate pull server provisioning.</span></span>

### <a name="wmf"></a><span data-ttu-id="606b8-149">WMF</span><span class="sxs-lookup"><span data-stu-id="606b8-149">WMF</span></span>

<span data-ttu-id="606b8-150">Windows Server 2012 R2 innehåller en funktion som heter DSC-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="606b8-150">Windows Server 2012 R2 includes a feature named the DSC Service.</span></span> <span data-ttu-id="606b8-151">Funktionen DSC-tjänsten tillhandahåller pull serverfunktionalitet, inklusive de binära filerna som har stöd för OData-slutpunkten.</span><span class="sxs-lookup"><span data-stu-id="606b8-151">The DSC Service feature provides the pull server functionality, including the binaries that support the OData endpoint.</span></span> <span data-ttu-id="606b8-152">WMF ingår i Windows Server och uppdateras i en flexibel takt mellan versioner av Windows Server.</span><span class="sxs-lookup"><span data-stu-id="606b8-152">WMF is included in Windows Server and is updated on an agile cadence between Windows Server releases.</span></span> <span data-ttu-id="606b8-153">[Nya versioner av WMF 5.0](http://aka.ms/wmf5latest) kan innehålla uppdateringar till funktionen DSC-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="606b8-153">[New versions of WMF 5.0](http://aka.ms/wmf5latest)  can include updates to the DSC Service feature.</span></span> <span data-ttu-id="606b8-154">Därför är det bäst att hämta den senaste versionen av WMF och granska viktig information för att avgöra om versionen innehåller en uppdatering av funktionen DSC-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="606b8-154">For this reason, it is a best practice to download the latest release of WMF and to review the release notes to determine if the release includes an update to the DSC service feature.</span></span> <span data-ttu-id="606b8-155">Du bör också granska avsnittet i viktig information som anger om den design för en uppdatering eller scenario statusen stabilt och experiment.</span><span class="sxs-lookup"><span data-stu-id="606b8-155">You should also review the section of the release notes that indicates whether the design status for an update or scenario is listed as stable or experimental.</span></span> <span data-ttu-id="606b8-156">Om du vill tillåta en smidig övergång cykel enskilda funktioner kan deklareras stabil, är vilket anger att funktionen redo att användas i en produktionsmiljö, även när WMF släpps i förhandsgranskningen.</span><span class="sxs-lookup"><span data-stu-id="606b8-156">To allow for an agile release cycle, individual features can be declared stable, which indicates the feature is ready to be used in a production environment even while WMF is released in preview.</span></span>
<span data-ttu-id="606b8-157">Andra funktioner som tidigare har uppdaterats av WMF versioner (se WMF viktig information för detaljerat):</span><span class="sxs-lookup"><span data-stu-id="606b8-157">Other features that have historically been updated by WMF releases (see the WMF Release Notes for further detail):</span></span>

 - <span data-ttu-id="606b8-158">Windows PowerShell, Windows PowerShell Integrated Scripting</span><span class="sxs-lookup"><span data-stu-id="606b8-158">Windows PowerShell Windows PowerShell Integrated Scripting</span></span>
 - <span data-ttu-id="606b8-159">Environment (ISE) Windows PowerShell-webbtjänster (Management OData</span><span class="sxs-lookup"><span data-stu-id="606b8-159">Environment (ISE) Windows PowerShell Web Services (Management OData</span></span>
 - <span data-ttu-id="606b8-160">IIS-tillägg) Windows PowerShell önskad Tillståndskonfiguration DSC)</span><span class="sxs-lookup"><span data-stu-id="606b8-160">IIS Extension)  Windows PowerShell Desired State Configuration (DSC)</span></span>
 - <span data-ttu-id="606b8-161">Windows Remote Management (WinRM) Windows Management Instrumentation (WMI)</span><span class="sxs-lookup"><span data-stu-id="606b8-161">Windows Remote Management (WinRM) Windows Management Instrumentation (WMI)</span></span>

### <a name="dsc-resource"></a><span data-ttu-id="606b8-162">DSC-resurs</span><span class="sxs-lookup"><span data-stu-id="606b8-162">DSC resource</span></span>

<span data-ttu-id="606b8-163">En pull-serverdistribution kan förenklas genom att etablera tjänsten med hjälp av ett DSC-konfigurationsskript.</span><span class="sxs-lookup"><span data-stu-id="606b8-163">A pull server deployment can be simplified by provisioning the service using a DSC configuration script.</span></span> <span data-ttu-id="606b8-164">Det här dokumentet innehåller konfigurationsskript som kan användas för att distribuera en klar servernoden i produktion.</span><span class="sxs-lookup"><span data-stu-id="606b8-164">This document includes configuration scripts that can be used to deploy a production ready server node.</span></span> <span data-ttu-id="606b8-165">Om du vill använda konfigurationsskript en DSC-modul krävs som inte ingår i Windows Server.</span><span class="sxs-lookup"><span data-stu-id="606b8-165">To use the configuration scripts, a DSC module is required that is not included in Windows Server.</span></span> <span data-ttu-id="606b8-166">Nödvändiga Modulnamn **xPSDesiredStateConfiguration**, som innehåller resursen DSC **xDscWebService**.</span><span class="sxs-lookup"><span data-stu-id="606b8-166">The required module name is **xPSDesiredStateConfiguration**, which includes the DSC resource **xDscWebService**.</span></span> <span data-ttu-id="606b8-167">Modulen xPSDesiredStateConfiguration kan hämtas [här](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d).</span><span class="sxs-lookup"><span data-stu-id="606b8-167">The xPSDesiredStateConfiguration module can be downloaded [here](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d).</span></span>

<span data-ttu-id="606b8-168">Använd den **installera modulen** cmdlet från den **PowerShellGet** modul.</span><span class="sxs-lookup"><span data-stu-id="606b8-168">Use the **Install-Module** cmdlet from the **PowerShellGet** module.</span></span>

```powershell
Install-Module xPSDesiredStateConfiguration
```

<span data-ttu-id="606b8-169">Den **PowerShellGet** modulen hämtar modulen:</span><span class="sxs-lookup"><span data-stu-id="606b8-169">The **PowerShellGet** module will download the module to:</span></span> 

`C:\Program Files\Windows PowerShell\Modules`

<span data-ttu-id="606b8-170">Planera aktivitet</span><span class="sxs-lookup"><span data-stu-id="606b8-170">Planning task</span></span>|
---|
<span data-ttu-id="606b8-171">Du har tillgång till installationsfilerna för Windows Server 2012 R2?</span><span class="sxs-lookup"><span data-stu-id="606b8-171">Do you have access to the installation files for Windows Server 2012 R2?</span></span>|
<span data-ttu-id="606b8-172">Distributionsmiljö har Internetåtkomst för att hämta WMF och modulen från galleriet online?</span><span class="sxs-lookup"><span data-stu-id="606b8-172">Will the deployment environment have Internet access to download WMF and the module from the online gallery?</span></span>|
<span data-ttu-id="606b8-173">Hur ska du installera de senaste säkerhetsuppdateringarna när du har installerat operativsystemet?</span><span class="sxs-lookup"><span data-stu-id="606b8-173">How will you install the latest security updates after installing the operating system?</span></span>|
<span data-ttu-id="606b8-174">Miljön har Internetåtkomst för att hämta uppdateringar eller den har en lokal server i Windows Server Update Services (WSUS)?</span><span class="sxs-lookup"><span data-stu-id="606b8-174">Will the environment have Internet access to obtain updates, or will it have a local Windows Server Update Services (WSUS) server?</span></span>|
<span data-ttu-id="606b8-175">Har du tillgång till installationsfilerna för Windows Server som redan omfattar uppdateringar via offline injection?</span><span class="sxs-lookup"><span data-stu-id="606b8-175">Do you have access to Windows Server installation files that already include updates through offline injection?</span></span>|

### <a name="hardware-requirements"></a><span data-ttu-id="606b8-176">Maskinvarukrav</span><span class="sxs-lookup"><span data-stu-id="606b8-176">Hardware requirements</span></span>

<span data-ttu-id="606b8-177">Pull-serverdistribution stöds på både fysiska och virtuella servrar.</span><span class="sxs-lookup"><span data-stu-id="606b8-177">Pull server deployments are supported on both physical and virtual servers.</span></span> <span data-ttu-id="606b8-178">Storlek för kraven på hämtningsservern överensstämmer med kraven för Windows Server 2012 R2.</span><span class="sxs-lookup"><span data-stu-id="606b8-178">The sizing requirements for pull server align with the requirements for Windows Server 2012 R2.</span></span>

<span data-ttu-id="606b8-179">Processor: 1,4 GHz 64-bitars processor</span><span class="sxs-lookup"><span data-stu-id="606b8-179">CPU: 1.4 GHz 64-bit processor</span></span>  
<span data-ttu-id="606b8-180">Minne: 512 MB</span><span class="sxs-lookup"><span data-stu-id="606b8-180">Memory: 512 MB</span></span>  
<span data-ttu-id="606b8-181">Diskutrymme: 32 GB</span><span class="sxs-lookup"><span data-stu-id="606b8-181">Disk Space: 32 GB</span></span>  
<span data-ttu-id="606b8-182">: Gigabit Ethernet-nätverkskort</span><span class="sxs-lookup"><span data-stu-id="606b8-182">Network: Gigabit Ethernet Adapter</span></span>  

<span data-ttu-id="606b8-183">Planera aktivitet</span><span class="sxs-lookup"><span data-stu-id="606b8-183">Planning task</span></span>|
---|
<span data-ttu-id="606b8-184">Du distribuerar på fysisk maskinvara eller på en virtualiseringsplattform?</span><span class="sxs-lookup"><span data-stu-id="606b8-184">Will you deploy on physical hardware or on a virtualization platform?</span></span>|
<span data-ttu-id="606b8-185">Vad är processen för att begära en ny server för målmiljön?</span><span class="sxs-lookup"><span data-stu-id="606b8-185">What is the process to request a new server for your target environment?</span></span>|
<span data-ttu-id="606b8-186">Vad är den genomsnittliga tid för en server ska bli tillgänglig?</span><span class="sxs-lookup"><span data-stu-id="606b8-186">What is the average turnaround time for a server to become available?</span></span>|
<span data-ttu-id="606b8-187">Vilken storlek du begär servern?</span><span class="sxs-lookup"><span data-stu-id="606b8-187">What size server will you request?</span></span>|

### <a name="accounts"></a><span data-ttu-id="606b8-188">Konton</span><span class="sxs-lookup"><span data-stu-id="606b8-188">Accounts</span></span>

<span data-ttu-id="606b8-189">Det finns inga krav på tjänstkonto att distribuera en pull-serverinstans.</span><span class="sxs-lookup"><span data-stu-id="606b8-189">There are no service account requirements to deploy a pull server instance.</span></span> <span data-ttu-id="606b8-190">Det finns emellertid scenarier där webbplatsen kan köras i kontexten för ett lokalt användarkonto.</span><span class="sxs-lookup"><span data-stu-id="606b8-190">However, there are scenarios where the website could run in the context of a local user account.</span></span> <span data-ttu-id="606b8-191">Till exempel om det är nödvändigt att åtkomst en storage-resurs för webbplatsens innehåll och Windows Server eller enhet som är värd för storage-resurs är inte ansluten till en domän.</span><span class="sxs-lookup"><span data-stu-id="606b8-191">For example, if there is a need to access a storage share for website content and either the Windows Server or the device hosting the storage share are not domain joined.</span></span>

### <a name="dns-records"></a><span data-ttu-id="606b8-192">DNS-poster</span><span class="sxs-lookup"><span data-stu-id="606b8-192">DNS records</span></span>

<span data-ttu-id="606b8-193">Du behöver ett servernamn som du använder när du konfigurerar klienter för att arbeta med en pull-servermiljö.</span><span class="sxs-lookup"><span data-stu-id="606b8-193">You will need a server name to use when configuring clients to work with a pull server environment.</span></span> <span data-ttu-id="606b8-194">I testmiljöer, oftast serverns värdnamn eller IP-adressen för servern kan användas om DNS-namnmatchningen inte är tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="606b8-194">In test environments, typically the server hostname is used, or the IP address for the server can be used if DNS name resolution is not available.</span></span> <span data-ttu-id="606b8-195">Det bästa sättet är att skapa en DNS CNAME-post i produktionsmiljöer eller i en testmiljö som är avsedd att representera en Produktionsdistribution.</span><span class="sxs-lookup"><span data-stu-id="606b8-195">In production environments or in a lab environment that is intended to represent a production deployment, the best practice is to create a DNS CNAME record.</span></span>

<span data-ttu-id="606b8-196">Ett DNS CNAME kan du skapa ett alias du vill referera till din värd (A) post.</span><span class="sxs-lookup"><span data-stu-id="606b8-196">A DNS CNAME allows you to create an alias to refer to your host (A) record.</span></span> <span data-ttu-id="606b8-197">Syftet med den ytterligare namnposten är att öka flexibiliteten ändras inte behövs i framtiden.</span><span class="sxs-lookup"><span data-stu-id="606b8-197">The intent of the additional name record is to increase flexibility should a change be required in the future.</span></span> <span data-ttu-id="606b8-198">En CNAME-post kan hjälpa för att isolera klientkonfigurationen så att ändringar av server-miljö, t.ex ersätter en pull-server eller lägga till ytterligare pull-servrar, inte kräver en motsvarande ändring i klientkonfigurationen.</span><span class="sxs-lookup"><span data-stu-id="606b8-198">A CNAME can help to isolate the client configuration so that changes to the server environment, such as replacing a pull server or adding additional pull servers, will not require a corresponding change to the client configuration.</span></span>

<span data-ttu-id="606b8-199">Tänk lösningsarkitekturen när du väljer ett namn för DNS-posten.</span><span class="sxs-lookup"><span data-stu-id="606b8-199">When choosing a name for the DNS record, keep the solution architecture in mind.</span></span> <span data-ttu-id="606b8-200">Om med belastningsutjämning, måste certifikatet som används för att skydda trafik via HTTPS delar samma namn som DNS-posten.</span><span class="sxs-lookup"><span data-stu-id="606b8-200">If using load balancing, the certificate used to secure traffic over HTTPS will need to share the same name as the DNS record.</span></span> 

<span data-ttu-id="606b8-201">Scenario</span><span class="sxs-lookup"><span data-stu-id="606b8-201">Scenario</span></span> |<span data-ttu-id="606b8-202">Bästa praxis</span><span class="sxs-lookup"><span data-stu-id="606b8-202">Best Practice</span></span>
:---|:---
<span data-ttu-id="606b8-203">Testmiljö</span><span class="sxs-lookup"><span data-stu-id="606b8-203">Test Environment</span></span> |<span data-ttu-id="606b8-204">Återskapa planerad produktionsmiljön, om möjligt.</span><span class="sxs-lookup"><span data-stu-id="606b8-204">Reproduce the planned production environment, if possible.</span></span> <span data-ttu-id="606b8-205">Ett värdnamn för servern är lämpligt för enkel konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="606b8-205">A server hostname is suitable for simple configurations.</span></span> <span data-ttu-id="606b8-206">Om DNS inte är tillgänglig, kan en IP-adress användas i stället för ett värdnamn.</span><span class="sxs-lookup"><span data-stu-id="606b8-206">If DNS is not available, an IP address may be used in lieu of a hostname.</span></span>|
<span data-ttu-id="606b8-207">Distribution av enskild nod</span><span class="sxs-lookup"><span data-stu-id="606b8-207">Single Node Deployment</span></span> |<span data-ttu-id="606b8-208">Skapa en DNS CNAME-post som pekar på serverns värdnamn.</span><span class="sxs-lookup"><span data-stu-id="606b8-208">Create a DNS CNAME record that points to the server hostname.</span></span>|

<span data-ttu-id="606b8-209">Mer information finns i [konfigurera DNS för resursallokering i Windows Server](https://technet.microsoft.com/en-us/library/cc787484(v=ws.10).aspx).</span><span class="sxs-lookup"><span data-stu-id="606b8-209">For more information, see [Configuring DNS Round Robin in Windows Server](https://technet.microsoft.com/en-us/library/cc787484(v=ws.10).aspx).</span></span>

<span data-ttu-id="606b8-210">Planera aktivitet</span><span class="sxs-lookup"><span data-stu-id="606b8-210">Planning task</span></span>|
---|
<span data-ttu-id="606b8-211">Vet du att kontakta om du vill att DNS-poster skapas och ändras?</span><span class="sxs-lookup"><span data-stu-id="606b8-211">Do you know who to contact to have DNS records created and changed?</span></span>|
<span data-ttu-id="606b8-212">Vad är den genomsnittliga tid en begäran om en DNS-post?</span><span class="sxs-lookup"><span data-stu-id="606b8-212">What is the average turnaround for a request for a DNS record?</span></span>|
<span data-ttu-id="606b8-213">Behöver du begära statiska värdnamn (A)-poster för servrar?</span><span class="sxs-lookup"><span data-stu-id="606b8-213">Do you need to request static Hostname (A) records for servers?</span></span>|
<span data-ttu-id="606b8-214">Vad du begär som en CNAME-post?</span><span class="sxs-lookup"><span data-stu-id="606b8-214">What will you request as a CNAME?</span></span>|
<span data-ttu-id="606b8-215">Om det behövs, vilken typ av belastningsutjämning lösning ska du använda?</span><span class="sxs-lookup"><span data-stu-id="606b8-215">If needed, what type of Load Balancing solution will you utilize?</span></span> <span data-ttu-id="606b8-216">(se avsnittet belastningsutjämning för information)</span><span class="sxs-lookup"><span data-stu-id="606b8-216">(see section titled Load Balancing for details)</span></span>|

### <a name="public-key-infrastructure"></a><span data-ttu-id="606b8-217">Infrastruktur för offentliga nycklar</span><span class="sxs-lookup"><span data-stu-id="606b8-217">Public Key Infrastructure</span></span>

<span data-ttu-id="606b8-218">De flesta organisationer kräver idag att nätverkstrafik, särskilt trafik som innehåller dessa känsliga data om hur servrar har konfigurerats, måste verifieras och krypterad under överföringen.</span><span class="sxs-lookup"><span data-stu-id="606b8-218">Most organizations today require that network traffic, especially traffic that includes such sensitive data as how servers are configured, must be validated and/or encrypted during transit.</span></span> <span data-ttu-id="606b8-219">När det är möjligt att distribuera en pull-server med hjälp av HTTP som underlättar klientbegäranden i klartext, är det en bra idé att skydda trafik med hjälp av HTTPS.</span><span class="sxs-lookup"><span data-stu-id="606b8-219">While it is possible to deploy a pull server using HTTP which facilitates client requests in clear text, it is a best practice to secure traffic using HTTPS.</span></span> <span data-ttu-id="606b8-220">Tjänsten kan konfigureras för att använda HTTPS med en uppsättning parametrar i DSC-resursen **xPSDesiredStateConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="606b8-220">The service can be configured to use HTTPS using a set of parameters in the DSC resource **xPSDesiredStateConfiguration**.</span></span>

<span data-ttu-id="606b8-221">Certifikatkrav för säker HTTPS-trafik för pull-servern är inte annat än att skydda alla andra HTTPS-webbplats.</span><span class="sxs-lookup"><span data-stu-id="606b8-221">The certificate requirements to secure HTTPS traffic for pull server are not different than securing any other HTTPS web site.</span></span> <span data-ttu-id="606b8-222">Den **webbservern** mallen i Certifikattjänster i Windows Server uppfyller de nödvändiga funktionerna.</span><span class="sxs-lookup"><span data-stu-id="606b8-222">The **Web Server** template in a Windows Server Certificate Services satisfies the required capabilities.</span></span>

<span data-ttu-id="606b8-223">Planera aktivitet</span><span class="sxs-lookup"><span data-stu-id="606b8-223">Planning task</span></span>|
---|
<span data-ttu-id="606b8-224">Om certifikatbegäran inte sker automatiskt, som behöver du kontakta ett certifikat på begäran?</span><span class="sxs-lookup"><span data-stu-id="606b8-224">If certificate requests are not automated, who will you need to contact to requests a certificate?</span></span>|
<span data-ttu-id="606b8-225">Vad är den genomsnittliga tid för begäran?</span><span class="sxs-lookup"><span data-stu-id="606b8-225">What is the average turnaround for the request?</span></span>|
<span data-ttu-id="606b8-226">Hur certifikatfilen överförs till dig?</span><span class="sxs-lookup"><span data-stu-id="606b8-226">How will the certificate file be transferred to you?</span></span>|
<span data-ttu-id="606b8-227">Hur certifikatets privata nyckel överförs till dig?</span><span class="sxs-lookup"><span data-stu-id="606b8-227">How will the certificate private key be transferred to you?</span></span>|
<span data-ttu-id="606b8-228">Hur lång tid är förfallotiden som standard?</span><span class="sxs-lookup"><span data-stu-id="606b8-228">How long is the default expiration time?</span></span>|
<span data-ttu-id="606b8-229">Har du lösas på ett DNS-namn för pull-servermiljö, som du kan använda för certifikatets namn?</span><span class="sxs-lookup"><span data-stu-id="606b8-229">Have you settled on a DNS name for the pull server environment, that you can use for the certificate name?</span></span>|

### <a name="choosing-an-architecture"></a><span data-ttu-id="606b8-230">Om du väljer en arkitektur</span><span class="sxs-lookup"><span data-stu-id="606b8-230">Choosing an architecture</span></span>

<span data-ttu-id="606b8-231">En pull-server kan distribueras med hjälp av antingen en webbtjänst som IIS eller en SMB filresurs.</span><span class="sxs-lookup"><span data-stu-id="606b8-231">A pull server can be deployed using either a web service hosted on IIS, or an SMB file share.</span></span> <span data-ttu-id="606b8-232">I de flesta fall är ger web service alternativet större flexibilitet.</span><span class="sxs-lookup"><span data-stu-id="606b8-232">In most situations, the web service option will provide greater flexibility.</span></span> <span data-ttu-id="606b8-233">Det är inte ovanligt att HTTPS-trafik färdas över nätverksgränser, medan SMB-trafik är ofta filtrerade eller blockeras mellan nätverk.</span><span class="sxs-lookup"><span data-stu-id="606b8-233">It is not uncommon for HTTPS traffic to traverse network boundaries, whereas SMB traffic is often filtered or blocked between networks.</span></span> <span data-ttu-id="606b8-234">Webbtjänsten ger också möjlighet att inkludera en överensstämmelse Server eller Web Reporting Manager (både ämnen tas upp i en framtida version av det här dokumentet) som tillhandahåller en mekanism för klienter för att rapportera status tillbaka till en server för centraliserad synlighet.</span><span class="sxs-lookup"><span data-stu-id="606b8-234">The web service also offers the option to include a Conformance Server or Web Reporting Manager (both topics to be addressed in a future version of this document) that provide a mechanism for clients to report status back to a server for centralized visibility.</span></span> <span data-ttu-id="606b8-235">SMB ger ett alternativ för miljöer där principen anger att en server inte kan användas och för andra miljökrav som gör en rollen som webbserver oönskade.</span><span class="sxs-lookup"><span data-stu-id="606b8-235">SMB provides an option for environments where policy dictates that a web server should not be utilized, and for other environmental requirements that make a web server role undesirable.</span></span> <span data-ttu-id="606b8-236">Kom ihåg att utvärdera kraven för signering och kryptering av trafik i båda fallen.</span><span class="sxs-lookup"><span data-stu-id="606b8-236">In either case, remember to evaluate the requirements for signing and encrypting traffic.</span></span> <span data-ttu-id="606b8-237">Är alla alternativ vara värt att hänsyn tagits till HTTPS, SMB-signering och IPSEC-principer.</span><span class="sxs-lookup"><span data-stu-id="606b8-237">HTTPS, SMB signing, and IPSEC policies are all options worth considering.</span></span>

#### <a name="load-balancing"></a><span data-ttu-id="606b8-238">Belastningsutjämning</span><span class="sxs-lookup"><span data-stu-id="606b8-238">Load balancing</span></span>  
<span data-ttu-id="606b8-239">Klienter som interagerar med webbtjänsten gör en begäran om information som returneras i ett enda svar.</span><span class="sxs-lookup"><span data-stu-id="606b8-239">Clients interacting with the web service make a request for information that is returned in a single response.</span></span> <span data-ttu-id="606b8-240">Inga sekventiella förfrågningar krävs, så det inte är nödvändigt för belastningsutjämning plattform för att säkerställa sessioner underhålls på en enskild server när som helst i tid.</span><span class="sxs-lookup"><span data-stu-id="606b8-240">No sequential requests are required, so it is not necessary for the load balancing platform to ensure sessions are maintained on a single server at any point in time.</span></span>

<span data-ttu-id="606b8-241">Planera aktivitet</span><span class="sxs-lookup"><span data-stu-id="606b8-241">Planning task</span></span>|
---|
<span data-ttu-id="606b8-242">Vilken lösning ska användas för belastningsutjämning trafik mellan servrar?</span><span class="sxs-lookup"><span data-stu-id="606b8-242">What solution will be used for load balancing traffic across servers?</span></span>|
<span data-ttu-id="606b8-243">Om du använder en maskinvarubaserad belastningsutjämnare som tar en begäran om att lägga till en ny konfiguration för enheten?</span><span class="sxs-lookup"><span data-stu-id="606b8-243">If using a hardware load balancer, who will take a request to add a new configuration to the device?</span></span>|
<span data-ttu-id="606b8-244">Vad är den genomsnittliga tid för en begäran om att konfigurera en ny belastning belastningsutjämnade webbtjänsten?</span><span class="sxs-lookup"><span data-stu-id="606b8-244">What is the average turnaround for a request to configure a new load balanced web service?</span></span>|
<span data-ttu-id="606b8-245">Vilken information kommer att krävas för begäran?</span><span class="sxs-lookup"><span data-stu-id="606b8-245">What information will be required for the request?</span></span>|
<span data-ttu-id="606b8-246">Du måste begära en ytterligare IP-adress eller gruppen som ansvarar för belastningsutjämning hanterar som?</span><span class="sxs-lookup"><span data-stu-id="606b8-246">Will you need to request an additional IP or will the team responsible for load balancing handle that?</span></span>|
<span data-ttu-id="606b8-247">Har du DNS-poster som behövs och det krävs av gruppen som ansvarar för att konfigurera nätverkslösning för belastningsutjämning?</span><span class="sxs-lookup"><span data-stu-id="606b8-247">Do you have the DNS records needed, and will this be required by the team responsible for configuring the load balancing solution?</span></span>|
<span data-ttu-id="606b8-248">Läsa in belastningsutjämning lösningen kräver att PKI ska hanteras av enheten eller kan den belastningsutjämna HTTPS-trafik, så länge det finns inga sessionskrav?</span><span class="sxs-lookup"><span data-stu-id="606b8-248">Does the load balancing solution require that PKI be handled by the device or can it load balance HTTPS traffic as long as there are no session requirements?</span></span>|

### <a name="staging-configurations-and-modules-on-the-pull-server"></a><span data-ttu-id="606b8-249">Mellanlagring av konfigurationer och moduler på hämtningsservern</span><span class="sxs-lookup"><span data-stu-id="606b8-249">Staging configurations and modules on the pull server</span></span>

<span data-ttu-id="606b8-250">Som en del av konfigurationen planering, behöver du tycker om vilka DSC-moduler och konfigurationer som kommer att finnas av pull-servern.</span><span class="sxs-lookup"><span data-stu-id="606b8-250">As part of configuration planning, you will need to think about which DSC modules and configurations will be hosted by the pull server.</span></span> <span data-ttu-id="606b8-251">För att planera konfigurationen är det viktigt att ha en grundläggande förståelse för hur du förbereder och distribuerar innehåll till en pull-server.</span><span class="sxs-lookup"><span data-stu-id="606b8-251">For the purpose of configuration planning it is important to have a basic understanding of how to prepare and deploy content to a pull server.</span></span> 

<span data-ttu-id="606b8-252">Det här avsnittet kommer i framtiden, expanderas och ingår i en Funktionsguide för DSC Pull-Server.</span><span class="sxs-lookup"><span data-stu-id="606b8-252">In the future, this section will be expanded and included in an Operations Guide for DSC Pull Server.</span></span>  <span data-ttu-id="606b8-253">Guiden diskuterar dagliga processen för att hantera moduler och konfigurationer över tid med automatisering.</span><span class="sxs-lookup"><span data-stu-id="606b8-253">The guide will discuss the day to day process for managing modules and configurations over time with automation.</span></span> 

#### <a name="dsc-modules"></a><span data-ttu-id="606b8-254">DSC-moduler</span><span class="sxs-lookup"><span data-stu-id="606b8-254">DSC modules</span></span>  
<span data-ttu-id="606b8-255">Klienter som begär en konfiguration måste DSC-moduler som krävs.</span><span class="sxs-lookup"><span data-stu-id="606b8-255">Clients that request a configuration will need the required DSC modules.</span></span> <span data-ttu-id="606b8-256">En funktion av pull-server är att automatisera distribution på begäran av DSC-moduler till klienter.</span><span class="sxs-lookup"><span data-stu-id="606b8-256">A functionality of the pull server is to automate distribution on demand of DSC modules to clients.</span></span> <span data-ttu-id="606b8-257">Om du distribuerar en pull-server för första gången, kanske som ett labb eller konceptbevis, ska du troligen är beroende av DSC-moduler som är tillgängliga från offentliga databaser, till exempel PowerShell-galleriet eller PowerShell.org GitHub-lagringsplatser för DSC-moduler .</span><span class="sxs-lookup"><span data-stu-id="606b8-257">If you are deploying a pull server for the first time, perhaps as a lab or proof of concept, you are likely going to depend on DSC modules that are available from public repositories such as the PowerShell Gallery or the PowerShell.org GitHub repositories for DSC modules.</span></span>

<span data-ttu-id="606b8-258">Det är viktigt att komma ihåg att även för tillförlitliga online källor, till exempel PowerShell-galleriet alla moduler som har hämtats från en offentlig databas bör granskas av någon med PowerShell upplevelse och kunskap om miljön där modulerna som kommer att använda före som används i produktionen.</span><span class="sxs-lookup"><span data-stu-id="606b8-258">It is critical to remember that even for trusted online sources such as the PowerShell Gallery, any module that is downloaded from a public repository should be reviewed by someone with PowerShell experience and knowledge of the environment where the modules will be used prior to being used in production.</span></span> <span data-ttu-id="606b8-259">Det är dags att söka efter eventuella ytterligare nyttolast i modulen som kan tas bort, till exempel dokumentation och exempel skript för att slutföra den här uppgiften.</span><span class="sxs-lookup"><span data-stu-id="606b8-259">While completing this task it is a good time to check for any additional payload in the module that can be removed such as documentation and example scripts.</span></span> <span data-ttu-id="606b8-260">Detta minskar nätverkets bandbredd per klient i sin första begäran när moduler ska laddas ned över nätverket från servern till klienten.</span><span class="sxs-lookup"><span data-stu-id="606b8-260">This will reduce the network bandwidth per client in their first request, when modules will be downloaded over the network from server to client.</span></span>

<span data-ttu-id="606b8-261">Varje modul måste paketeras i ett specifikt format, en ZIP-fil med namnet ModuleName_Version.zip som innehåller modulen nyttolasten.</span><span class="sxs-lookup"><span data-stu-id="606b8-261">Each module must be packaged in a specific format, a ZIP file named ModuleName_Version.zip that contains the module payload.</span></span> <span data-ttu-id="606b8-262">När filen kopieras till servern måste du skapa en fil kontrollsummor.</span><span class="sxs-lookup"><span data-stu-id="606b8-262">After the file is copied to the server a checksum file must be created.</span></span> <span data-ttu-id="606b8-263">När klienter ansluter till servern, används kontrollsumman som för att kontrollera innehållet i DSC-modulen inte har ändrats sedan den publicerades.</span><span class="sxs-lookup"><span data-stu-id="606b8-263">When clients connect to the server, the checksum is used to verify the content of the DSC module has not changed since it was published.</span></span>

```powershell
New-DscCheckSum -ConfigurationPath .\ -OutPath .\
```

<span data-ttu-id="606b8-264">Planera aktivitet</span><span class="sxs-lookup"><span data-stu-id="606b8-264">Planning task</span></span>|
---|
<span data-ttu-id="606b8-265">Om du planerar en test- eller labb-miljö är vilka scenarier för att verifiera?</span><span class="sxs-lookup"><span data-stu-id="606b8-265">If you are planning a test or lab environment which scenarios are key to validate?</span></span>|
<span data-ttu-id="606b8-266">Finns det offentligt tillgängliga modulerna som innehåller resurser för att omfatta allt du behöver eller behöver du skapa dina egna resurser?</span><span class="sxs-lookup"><span data-stu-id="606b8-266">Are there publicly available modules that contain resources to cover everything you need or will you need to author your own resources?</span></span>|
<span data-ttu-id="606b8-267">Kommer din miljö ha Internetåtkomst för att hämta offentlig moduler?</span><span class="sxs-lookup"><span data-stu-id="606b8-267">Will your environment have Internet access to retrieve public modules?</span></span>|
<span data-ttu-id="606b8-268">Vem är ansvarig för att granska DSC-moduler?</span><span class="sxs-lookup"><span data-stu-id="606b8-268">Who will be responsible for reviewing DSC modules?</span></span>|
<span data-ttu-id="606b8-269">Om du planerar en produktionsmiljö vad ska du använda som en lokal databas för lagring av DSC-moduler?</span><span class="sxs-lookup"><span data-stu-id="606b8-269">If you are planning a production environment what will you use as a local repository for storing DSC modules?</span></span>|
<span data-ttu-id="606b8-270">En central team accepterar DSC-moduler från programteam?</span><span class="sxs-lookup"><span data-stu-id="606b8-270">Will a central team accept DSC modules from application teams?</span></span> <span data-ttu-id="606b8-271">Vad är processen?</span><span class="sxs-lookup"><span data-stu-id="606b8-271">What will the process be?</span></span>|
<span data-ttu-id="606b8-272">Kan du automatisera paketering, kopiera och skapa en kontrollsumma för produktionsklara DSC-moduler på servern från käll-lagringsplatsen?</span><span class="sxs-lookup"><span data-stu-id="606b8-272">Will you automate packaging, copying, and creating a checksum for production-ready DSC modules to the server, from your source repo?</span></span>|
<span data-ttu-id="606b8-273">Ditt team ansvarar för att hantera plattformen automation?</span><span class="sxs-lookup"><span data-stu-id="606b8-273">Will your team be responsible for managing the automation platform as well?</span></span>|

#### <a name="dsc-configurations"></a><span data-ttu-id="606b8-274">DSC-konfigurationer</span><span class="sxs-lookup"><span data-stu-id="606b8-274">DSC configurations</span></span>

<span data-ttu-id="606b8-275">Syftet med en pull-server är att tillhandahålla en centraliserad mekanism för att distribuera DSC-konfigurationer för klientnoder.</span><span class="sxs-lookup"><span data-stu-id="606b8-275">The purpose of a pull server is to provide a centralized mechanism for distributing DSC configurations to client nodes.</span></span> <span data-ttu-id="606b8-276">Konfigurationerna som lagras på servern som MOF-dokument.</span><span class="sxs-lookup"><span data-stu-id="606b8-276">The configurations are stored on the server as MOF documents.</span></span> <span data-ttu-id="606b8-277">Varje dokument kommer att namnges med ett unikt GUID.</span><span class="sxs-lookup"><span data-stu-id="606b8-277">Each document will be named with a unique GUID.</span></span> <span data-ttu-id="606b8-278">När klienterna är konfigurerade för att ansluta till en pull-server, ges de också GUID för konfigurationen hon måste begära.</span><span class="sxs-lookup"><span data-stu-id="606b8-278">When clients are configured to connect with a pull server, they are also given the GUID for the configuration they should request.</span></span> <span data-ttu-id="606b8-279">Systemet för att referera till konfigurationer av GUID garanterar globala unika och är flexibel så att du kan använda en konfiguration med granularitet per nod eller som en rollkonfiguration som sträcker sig över flera servrar som ska ha identiska konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="606b8-279">This system of referencing configurations by GUID guarantees global uniqueness and is flexible such that a configuration can be applied with granularity per node, or as a role configuration that spans many servers that should have identical configurations.</span></span>

#### <a name="guids"></a><span data-ttu-id="606b8-280">GUID</span><span class="sxs-lookup"><span data-stu-id="606b8-280">GUIDs</span></span>

<span data-ttu-id="606b8-281">Planera för konfiguration GUID är värt att ytterligare åtgärder när du funderar på en pull-serverdistribution.</span><span class="sxs-lookup"><span data-stu-id="606b8-281">Planning for configuration GUIDs is worth additional attention when thinking through a pull server deployment.</span></span> <span data-ttu-id="606b8-282">Det finns inga särskilda krav för hur du hanterar GUID och processen kan förväntas vara unikt för varje miljö.</span><span class="sxs-lookup"><span data-stu-id="606b8-282">There is no specific requirement for how to handle GUIDs and the process is likely to be unique for each environment.</span></span> <span data-ttu-id="606b8-283">Processen kan variera mellan enkla och komplexa: en centralt lagrade CSV-fil, en enkel SQLtabell, ett CMDB eller en komplex lösning kräver integrering med en annan lösning för verktyget eller programvara.</span><span class="sxs-lookup"><span data-stu-id="606b8-283">The process can range from simple to complex: a centrally stored CSV file, a simple SQL table, a CMDB, or a complex solution requiring integration with another tool or software solution.</span></span> <span data-ttu-id="606b8-284">Det finns två sätt:</span><span class="sxs-lookup"><span data-stu-id="606b8-284">There are two general approaches:</span></span>

 - <span data-ttu-id="606b8-285">**Tilldela GUID per server** – ger ett mått på försäkran om att varje konfiguration kontrolleras separat.</span><span class="sxs-lookup"><span data-stu-id="606b8-285">**Assigning GUIDs per server** — Provides a measure of assurance that every server configuration is controlled individually.</span></span> <span data-ttu-id="606b8-286">Detta ger en precision runt uppdateringar och kan fungera bra i miljöer med några servrar.</span><span class="sxs-lookup"><span data-stu-id="606b8-286">This provides a level of precision around updates and can work well in environments with few servers.</span></span>
 - <span data-ttu-id="606b8-287">**Tilldela GUID per serverrollen** – alla servrar som utför samma funktion, till exempel webbservrar, använda samma GUID för att referera till den nödvändiga konfigurationsdatan.</span><span class="sxs-lookup"><span data-stu-id="606b8-287">**Assigning GUIDs per server role** — All servers that perform the same function, such as web servers, use the same GUID to reference the required configuration data.</span></span>  <span data-ttu-id="606b8-288">Tänk på att om många servrar som delar samma GUID, alla skulle uppdateras samtidigt när konfigurationen ändras.</span><span class="sxs-lookup"><span data-stu-id="606b8-288">Be aware that if many servers share the same GUID, all of them would be updated simultaneously when the configuration changes.</span></span>

<span data-ttu-id="606b8-289">GUID är något som bör övervägas känsliga data eftersom den kan utnyttjas av en användare med skadliga åtgärder för att få intelligence om hur servrar distribuerats och konfigurerats i din miljö.</span><span class="sxs-lookup"><span data-stu-id="606b8-289">The GUID is something that should be considered sensitive data because it could be leveraged by someone with malicious intent to gain intelligence about how servers are deployed and configured in your environment.</span></span> <span data-ttu-id="606b8-290">Mer information finns i [på ett säkert sätt allokera GUID i PowerShell önskad tillstånd Pull-konfigurationsläge](http://blogs.msdn.com/b/powershell/archive/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode.aspx).</span><span class="sxs-lookup"><span data-stu-id="606b8-290">For more information, see [Securely allocating GUIDs in PowerShell Desired State Configuration Pull Mode](http://blogs.msdn.com/b/powershell/archive/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode.aspx).</span></span>

<span data-ttu-id="606b8-291">Planera aktivitet</span><span class="sxs-lookup"><span data-stu-id="606b8-291">Planning task</span></span>|
---|
<span data-ttu-id="606b8-292">Vem är ansvarig för att kopiera konfigurationer i till mappen pull server när de är klara?</span><span class="sxs-lookup"><span data-stu-id="606b8-292">Who will be responsible for copying configurations in to the pull server folder when they are ready?</span></span>|
<span data-ttu-id="606b8-293">Om konfigurationer som skapats av en grupp av program, vad processen är att lämnar dem?</span><span class="sxs-lookup"><span data-stu-id="606b8-293">If Configurations are authored by an application team, what will the process be to hand them off?</span></span>|
<span data-ttu-id="606b8-294">Använder du en lagringsplats för konfigurationer som de som skapats, mellan olika grupper?</span><span class="sxs-lookup"><span data-stu-id="606b8-294">Will you leverage a repository to store configurations as they are being authored, across teams?</span></span>|
<span data-ttu-id="606b8-295">Kan du automatisera processen för att kopiera konfigurationer till servern och skapa en kontrollsumma när de är klara?</span><span class="sxs-lookup"><span data-stu-id="606b8-295">Will you automate the process of copying configurations to the server and creating a checksum when they are ready?</span></span>|
<span data-ttu-id="606b8-296">Hur du mappar GUID till servrar eller roller och där det sparas?</span><span class="sxs-lookup"><span data-stu-id="606b8-296">How will you map GUIDs to servers or roles, and where will this be stored?</span></span>|
<span data-ttu-id="606b8-297">Vad ska du använda som en process för att konfigurera klientdatorer och hur kan den integreras med processen skapar och lagrar Configuration GUID?</span><span class="sxs-lookup"><span data-stu-id="606b8-297">What will you use as a process to configure client machines, and how will it integrate with your process for creating and storing Configuration GUIDs?</span></span>|

## <a name="installation-guide"></a><span data-ttu-id="606b8-298">Installationsguiden</span><span class="sxs-lookup"><span data-stu-id="606b8-298">Installation Guide</span></span>

<span data-ttu-id="606b8-299">*Skript som anges i det här dokumentet är stabil exempel. Alltid läsa igenom skript noggrant innan du kör dem i en produktionsmiljö.*</span><span class="sxs-lookup"><span data-stu-id="606b8-299">*Scripts given in this document are stable examples. Always review scripts carefully before executing them in a production environment.*</span></span>

### <a name="prerequisites"></a><span data-ttu-id="606b8-300">Förutsättningar</span><span class="sxs-lookup"><span data-stu-id="606b8-300">Prerequisites</span></span>

<span data-ttu-id="606b8-301">Använd följande kommando för att kontrollera version av PowerShell på servern.</span><span class="sxs-lookup"><span data-stu-id="606b8-301">To verify the version of PowerShell on your server use the following command.</span></span>

```powershell
$PSVersionTable.PSVersion
```

<span data-ttu-id="606b8-302">Om det är möjligt att uppgradera till den senaste versionen av Windows Management Framework.</span><span class="sxs-lookup"><span data-stu-id="606b8-302">If possible, upgrade to the latest version of Windows Management Framework.</span></span>
<span data-ttu-id="606b8-303">Sedan hämtar den `xPsDesiredStateConfiguration` modul med följande kommando.</span><span class="sxs-lookup"><span data-stu-id="606b8-303">Next, download the `xPsDesiredStateConfiguration` module using the following command.</span></span>


```powershell
Install-Module xPSDesiredStateConfiguration
```

<span data-ttu-id="606b8-304">Kommandot begär ditt godkännande innan du hämtar modulen.</span><span class="sxs-lookup"><span data-stu-id="606b8-304">The command will ask for your approval before downloading the module.</span></span>

### <a name="installation-and-configuration-scripts"></a><span data-ttu-id="606b8-305">Skript för installation och konfiguration</span><span class="sxs-lookup"><span data-stu-id="606b8-305">Installation and configuration scripts</span></span>
-

<span data-ttu-id="606b8-306">Det bästa sättet att distribuera en DSC pull-server är att använda ett DSC-konfigurationsskript.</span><span class="sxs-lookup"><span data-stu-id="606b8-306">The best method to deploy a DSC pull server is to use a DSC configuration script.</span></span> <span data-ttu-id="606b8-307">Det här dokumentet visas skript inklusive både grundläggande inställningar som konfigurerar bara DSC-webbtjänsten och avancerade inställningar som konfigurerar en Windows Server slutpunkt till slutpunkt inklusive DSC webbtjänst.</span><span class="sxs-lookup"><span data-stu-id="606b8-307">This document will present scripts including both basic settings that would configure only the DSC web service and advanced settings that would configure a Windows Server end-to-end including DSC web service.</span></span>

<span data-ttu-id="606b8-308">Obs: För närvarande den `xPSDesiredStateConfiguation` DSC-modulen kräver att servern ska vara EN-US lokalisering.</span><span class="sxs-lookup"><span data-stu-id="606b8-308">Note:  Currently the `xPSDesiredStateConfiguation` DSC module requires the server to be EN-US locale.</span></span>

### <a name="basic-configuration-for-windows-server-2012"></a><span data-ttu-id="606b8-309">Grundläggande konfiguration för Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="606b8-309">Basic configuration for Windows Server 2012</span></span>
-------------------------------------------
```powershell
# This is a very basic Configuration to deploy a pull server instance in a lab environment on Windows Server 2012.

Configuration PullServer {
Import-DscResource -ModuleName xPSDesiredStateConfiguration

        # Load the Windows Server DSC Service feature
        WindowsFeature DSCServiceFeature
        {
          Ensure = 'Present'
          Name = 'DSC-Service'
        }

        # Use the DSC Resource to simplify deployment of the web service
        xDSCWebService PSDSCPullServer
        {
          Ensure = 'Present'
          EndpointName = 'PSDSCPullServer'
          Port = 8080
          PhysicalPath = "$env:SYSTEMDRIVE\inetpub\wwwroot\PSDSCPullServer"
          CertificateThumbPrint = 'AllowUnencryptedTraffic'
          ModulePath = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
          ConfigurationPath = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
          State = 'Started'
          DependsOn = '[WindowsFeature]DSCServiceFeature'
        }
}
PullServer -OutputPath 'C:\PullServerConfig\'
Start-DscConfiguration -Wait -Force -Verbose -Path 'C:\PullServerConfig\'
```

### <a name="advanced-configuration-for-windows-server-2012-r2"></a><span data-ttu-id="606b8-310">Avancerad konfiguration för Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="606b8-310">Advanced configuration for Windows Server 2012 R2</span></span>

```powershell
# This is an advanced Configuration example for Pull Server production deployments on Windows Server 2012 R2.
# Many of the features demonstrated are optional and provided to demonstrate how to adapt the Configuration for multiple scenarios
# Select the needed resources based on the requirements for each environment.
# Optional scenarios include:
#      * Reduce footprint to Server Core
#      * Rename server and join domain
#      * Switch from SSL to TLS for HTTPS
#      * Automatically load certificate from Certificate Authority
#      * Locate Modules and Configuration data on remote SMB share
#      * Manage state of default websites in IIS
    
param (
        [Parameter(Mandatory=$true)] 
        [ValidateNotNullorEmpty()] 
        [System.String] $ServerName,
        [System.String] $DomainName,
        [System.String] $CARootName,
        [System.String] $CAServerFQDN,
        [System.String] $CertSubject,
        [System.String] $SMBShare,
        [Parameter(Mandatory=$true)] 
        [ValidateNotNullorEmpty()] 
        [PsCredential] $Credential
    )
    
Configuration PullServer {
    Import-DscResource -ModuleName xPSDesiredStateConfiguration, xWebAdministration, xCertificate, xComputerManagement
    Node localhost
    {
            
        # Configure the server to automatically corret configuration drift including reboots if needed.
        LocalConfigurationManager
        {
            ConfigurationMode = 'ApplyAndAutoCorrect'
            RebootNodeifNeeded = $node.RebootNodeifNeeded
            CertificateId = $node.Thumbprint
        }
    
        # Remove all GUI interfaces so the server has minimum running footprint.
        WindowsFeature ServerCore
        {
            Ensure = 'Absent'
            Name = 'User-Interfaces-Infra'
        }
    
        # Set the server name and if needed, join a domain. If not joining a domain, remove the DomainName parameter.
        xComputer DomainJoin
        {
            Name = $Node.ServerName
            DomainName = $Node.DomainName
            Credential = $Node.Credential
        }
    
        # The next series of settings disable SSL and enable TLS, for environments where that is required by policy.
        Registry TLS1_2ServerEnabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Server'
            ValueName = 'Enabled'
            ValueData = 1
            ValueType = 'Dword'
        }
        Registry TLS1_2ServerDisabledByDefault
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Server'
            ValueName = 'DisabledByDefault'
            ValueData = 0
            ValueType = 'Dword'
        }
        Registry TLS1_2ClientEnabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client'
            ValueName = 'Enabled'
            ValueData = 1
            ValueType = 'Dword'
        }
        Registry TLS1_2ClientDisabledByDefault
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client'
            ValueName = 'DisabledByDefault'
            ValueData = 0
            ValueType = 'Dword'
        }
        Registry SSL2ServerDisabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\SSL 2.0\Server'
            ValueName = 'Enabled'
            ValueData = 0
            ValueType = 'Dword'
        }
    
        # Install the Windows Server DSC Service feature
        WindowsFeature DSCServiceFeature
        {
            Ensure = 'Present'
            Name = 'DSC-Service'
        }
    
        # If using a certificate from a local Active Directory Enterprise Root Certificate Authority, complete a request and install the certificate
        xCertReq SSLCert
        {
            CARootName = $Node.CARootName
            CAServerFQDN = $Node.CAServerFQDN
            Subject = $Node.CertSubject
            AutoRenew = $Node.AutoRenew
            Credential = $Node.Credential
        }
    
        # Use the DSC resource to simplify deployment of the web service.  You might also consider modifying the default port, possibly leveraging port 443 in environments where that is enforced as a standard.
        xDSCWebService PSDSCPullServer
        {
            Ensure = 'Present'
            EndpointName = 'PSDSCPullServer'
            Port = 8080
            PhysicalPath = "$env:SYSTEMDRIVE\inetpub\wwwroot\PSDSCPullServer"
            CertificateThumbPrint = 'CertificateSubject'
            CertificateSubject = $Node.CertSubject
            ModulePath = "$($Node.SMBShare)\DscService\Modules"
            ConfigurationPath = "$($Node.SMBShare)\DscService\Configuration"
            State = 'Started'
            DependsOn = '[WindowsFeature]DSCServiceFeature'
        }
    
        # Validate web config file contains current DB settings
        xWebConfigKeyValue CorrectDBProvider
        { 
            ConfigSection = 'AppSettings'
            Key = 'dbprovider'
            Value = 'System.Data.OleDb'
            WebsitePath = 'IIS:\sites\PSDSCPullServer'
            DependsOn = '[xDSCWebService]PSDSCPullServer'
        }
        xWebConfigKeyValue CorrectDBConnectionStr
        { 
            ConfigSection = 'AppSettings'
            Key = 'dbconnectionstr'
            Value = 'Provider=Microsoft.Jet.OLEDB.4.0;Data Source=C:\Program Files\WindowsPowerShell\DscService\Devices.mdb;'
            WebsitePath = 'IIS:\sites\PSDSCPullServer'
            DependsOn = '[xDSCWebService]PSDSCPullServer'
        }
    
        # Stop the default website
        xWebsite StopDefaultSite  
        { 
            Ensure = 'Present'
            Name = 'Default Web Site'
            State = 'Stopped'
            PhysicalPath = 'C:\inetpub\wwwroot'
            DependsOn = '[WindowsFeature]DSCServiceFeature'
        }
    }
}
$configData = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            ServerName = $ServerName
            DomainName = $DomainName
            CARootName = $CARootName
            CAServerFQDN = $CAServerFQDN
            CertSubject = $CertSubject
            AutoRenew = $true
            SMBShare = $SMBShare
            Credential = $Credential
            RebootNodeifNeeded = $true
            CertificateFile = 'c:\PullServerConfig\Cert.cer'
            Thumbprint = 'B9A39921918B466EB1ADF2509E00F5DECB2EFDA9'
            }
        )
    }
PullServer -ConfigurationData $configData -OutputPath 'C:\PullServerConfig\'
Set-DscLocalConfigurationManager -ComputerName localhost -Path 'C:\PullServerConfig\'
Start-DscConfiguration -Wait -Force -Verbose -Path 'C:\PullServerConfig\'
    
# .\Script.ps1 -ServerName web1 -domainname 'test.pha' -carootname 'test-dc01-ca' -caserverfqdn 'dc01.test.pha' -certsubject 'CN=service.test.pha' -smbshare '\\sofs1.test.pha\share' 
```


### <a name="verify-pull-server-functionality"></a><span data-ttu-id="606b8-311">Kontrollera pull-serverfunktioner</span><span class="sxs-lookup"><span data-stu-id="606b8-311">Verify pull server functionality</span></span>

```powershell
# This function is meant to simplify a check against a DSC pull server. If you do not use the default service URL, you will need to adjust accordingly.
function Verify-DSCPullServer ($fqdn) {
    ([xml](invoke-webrequest "https://$($fqdn):8080/psdscpullserver.svc" | % Content)).service.workspace.collection.href
}
Verify-DSCPullServer 'INSERT SERVER FQDN' 

Expected Result:
Action
Module
StatusReport
Node
```

### <a name="configure-clients"></a><span data-ttu-id="606b8-312">Konfigurera klienter</span><span class="sxs-lookup"><span data-stu-id="606b8-312">Configure clients</span></span>

```powershell
Configuration PullClient {
    param(
    $ID,
    $Server
    )
        LocalConfigurationManager 
                { 
                    ConfigurationID = $ID;
                    RefreshMode = 'PULL';
                    DownloadManagerName = 'WebDownloadManager';
                    RebootNodeIfNeeded = $true;
                    RefreshFrequencyMins = 30;
                    ConfigurationModeFrequencyMins = 15; 
                    ConfigurationMode = 'ApplyAndAutoCorrect';
                    DownloadManagerCustomData = @{ServerUrl = "http://"+$Server+":8080/PSDSCPullServer.svc"; AllowUnsecureConnection = $true}
                }
}
PullClient -ID 'INSERTGUID' -Server 'INSERTSERVER' -Output 'C:\DSCConfig\'
Set-DscLocalConfigurationManager -ComputerName 'Localhost' -Path 'C:\DSCConfig\' -Verbose
```


## <a name="additional-references-snippets-and-examples"></a><span data-ttu-id="606b8-313">Ytterligare referenser, kodavsnitt och exempel</span><span class="sxs-lookup"><span data-stu-id="606b8-313">Additional references, snippets, and examples</span></span>

<span data-ttu-id="606b8-314">Det här exemplet visar hur du manuellt initiera en klientanslutning (kräver WMF5) för testning.</span><span class="sxs-lookup"><span data-stu-id="606b8-314">This example shows how to manually initiate a client connection (requires WMF5) for testing.</span></span> 

```powershell
Update-DSCConfiguration –Wait -Verbose
```

<span data-ttu-id="606b8-315">Den [Lägg till DnsServerResourceRecordName](http://bit.ly/1G1H31L) cmdlet som används för att lägga till en typ CNAME-post till en DNS-zon.</span><span class="sxs-lookup"><span data-stu-id="606b8-315">The [Add-DnsServerResourceRecordName](http://bit.ly/1G1H31L) cmdlet is used to add a type CNAME record to a DNS zone.</span></span> 

<span data-ttu-id="606b8-316">PowerShell-funktionen för att [skapa en kontrollsumma och publicera DSC MOF till SMB-Pull Server](http://bit.ly/1E46BhI) genererar automatiskt krävs kontrollsumma och kopierar sedan både MOF-konfigurationen och kontrollsumma filer till pull SMB-servern.</span><span class="sxs-lookup"><span data-stu-id="606b8-316">The PowerShell Function to [Create a Checksum and Publish DSC MOF to SMB Pull Server](http://bit.ly/1E46BhI) automatically generates the required checksum, and then copies both the MOF configuration and checksum files to the SMB pull server.</span></span>

## <a name="appendix---understanding-odata-service-data-file-types"></a><span data-ttu-id="606b8-317">Tillägg – förstå ODATA service data filtyper</span><span class="sxs-lookup"><span data-stu-id="606b8-317">Appendix - Understanding ODATA service data file types</span></span>

<span data-ttu-id="606b8-318">En fil lagras för att skapa information vid distribution av en pull-server som innehåller OData-webbtjänst.</span><span class="sxs-lookup"><span data-stu-id="606b8-318">A data file is stored to create information during deployment of a pull server that includes the OData web service.</span></span> <span data-ttu-id="606b8-319">Typ av fil beror på operativsystemet, enligt beskrivningen nedan.</span><span class="sxs-lookup"><span data-stu-id="606b8-319">The type of file depends on the operating system, as described below.</span></span>

 - <span data-ttu-id="606b8-320">**Windows Server 2012**</span><span class="sxs-lookup"><span data-stu-id="606b8-320">**Windows Server 2012**</span></span>  
<span data-ttu-id="606b8-321">Filtypen kommer alltid att .mdb</span><span class="sxs-lookup"><span data-stu-id="606b8-321">The file type will always be   .mdb</span></span>
 - <span data-ttu-id="606b8-322">**Windows Server 2012 R2**</span><span class="sxs-lookup"><span data-stu-id="606b8-322">**Windows Server 2012 R2**</span></span>  
<span data-ttu-id="606b8-323">Filtypen kommer som standard edb om en .mdb har angetts i konfigurationen</span><span class="sxs-lookup"><span data-stu-id="606b8-323">The file type will default to .edb unless a .mdb is specified in the configuration</span></span>

<span data-ttu-id="606b8-324">I den [avancerade exempelskriptet](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) för att installera en Pull-Server, det finns även ett exempel på hur du styr inställningarna för web.config-filen för att förhindra alla risken för fel som orsakats av filtyp automatiskt.</span><span class="sxs-lookup"><span data-stu-id="606b8-324">In the [Advanced example script](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) for installing a Pull Server, you will also find an example of how to automatically control the web.config file settings to prevent any chance of error caused by file type.</span></span>

