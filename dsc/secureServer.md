---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Metodtips för hämtningsservern
ms.openlocfilehash: 1efc016df6882fa962f59dfd3e53eaa6d6b0c121
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
ms.locfileid: "34190306"
---
# <a name="pull-server-best-practices"></a><span data-ttu-id="5ec81-103">Metodtips för hämtningsservern</span><span class="sxs-lookup"><span data-stu-id="5ec81-103">Pull server best practices</span></span>

><span data-ttu-id="5ec81-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="5ec81-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5ec81-105">Pull-Server (Windows-funktionen *DSC-Service*) är en stöds komponent i Windows Server men det finns inga planer på att erbjuda nya funktioner eller funktioner.</span><span class="sxs-lookup"><span data-stu-id="5ec81-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="5ec81-106">Vi rekommenderar att börja övergång hanteras klienter [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (omfattar funktioner utöver Pull-Server på Windows Server) eller någon av community-lösningar som anges [här](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="5ec81-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="5ec81-107">Sammanfattning: Det här dokumentet är avsett att inkludera processen och utökningsbarhet att hjälpa tekniker som förbereder för lösningen.</span><span class="sxs-lookup"><span data-stu-id="5ec81-107">Summary: This document is intended to include process and extensibility to assist engineers who are preparing for the solution.</span></span> <span data-ttu-id="5ec81-108">Information bör ge bästa praxis som identifieras av kunder och sedan verifieras av Produktteamet för att säkerställa rekommendationer framtida riktade och anses vara stabil.</span><span class="sxs-lookup"><span data-stu-id="5ec81-108">Details should provide best practices as identified by customers and then validated by the product team to ensure recommendations are future facing and considered stable.</span></span>

| |<span data-ttu-id="5ec81-109">Doc-Info</span><span class="sxs-lookup"><span data-stu-id="5ec81-109">Doc Info</span></span>|
|:---|:---|
<span data-ttu-id="5ec81-110">författare</span><span class="sxs-lookup"><span data-stu-id="5ec81-110">Author</span></span> | <span data-ttu-id="5ec81-111">Michael Greene</span><span class="sxs-lookup"><span data-stu-id="5ec81-111">Michael Greene</span></span>
<span data-ttu-id="5ec81-112">Granskare</span><span class="sxs-lookup"><span data-stu-id="5ec81-112">Reviewers</span></span> | <span data-ttu-id="5ec81-113">Ben Gelens, Ravikanth Chaganti Aleksandar Nikolic</span><span class="sxs-lookup"><span data-stu-id="5ec81-113">Ben Gelens, Ravikanth Chaganti, Aleksandar Nikolic</span></span>
<span data-ttu-id="5ec81-114">Publicerade</span><span class="sxs-lookup"><span data-stu-id="5ec81-114">Published</span></span> | <span data-ttu-id="5ec81-115">April 2015</span><span class="sxs-lookup"><span data-stu-id="5ec81-115">April, 2015</span></span>

## <a name="abstract"></a><span data-ttu-id="5ec81-116">Abstrakt</span><span class="sxs-lookup"><span data-stu-id="5ec81-116">Abstract</span></span>

<span data-ttu-id="5ec81-117">Det här dokumentet är utformad att ge officiella vägledning för alla planera för en Windows PowerShell Desired State Configuration pull-serverimplementering.</span><span class="sxs-lookup"><span data-stu-id="5ec81-117">This document is designed to provide official guidance for anyone planning for a Windows PowerShell Desired State Configuration pull server implementation.</span></span> <span data-ttu-id="5ec81-118">En pull-server är en enkel tjänst som tar endast minuter att distribuera.</span><span class="sxs-lookup"><span data-stu-id="5ec81-118">A pull server is a simple service that should take only minutes to deploy.</span></span> <span data-ttu-id="5ec81-119">Även om det här dokumentet kommer att erbjuda teknisk vägledning som kan användas i en distribution, är värdet för det här dokumentet som en referens för bästa praxis och vad du ska tänka på innan du distribuerar.</span><span class="sxs-lookup"><span data-stu-id="5ec81-119">Although this document will offer technical how-to guidance that can be used in a deployment, the value of this document is as a reference for best practices and what to think about before deploying.</span></span>
<span data-ttu-id="5ec81-120">Läsare bör ha grundläggande kunskaper med DSC och de termer som används för att beskriva komponenterna som ingår i en DSC-distribution.</span><span class="sxs-lookup"><span data-stu-id="5ec81-120">Readers should have basic familiarity with DSC, and the terms used to describe the components that are included in a DSC deployment.</span></span> <span data-ttu-id="5ec81-121">Mer information finns i [Windows PowerShell Desired Configuration översikt över](https://technet.microsoft.com/library/dn249912.aspx) avsnittet.</span><span class="sxs-lookup"><span data-stu-id="5ec81-121">For more information, see the [Windows PowerShell Desired State Configuration Overview](https://technet.microsoft.com/library/dn249912.aspx)  topic.</span></span>
<span data-ttu-id="5ec81-122">Som DSC är förväntat att utvecklas i molnet takt förväntas också den underliggande tekniken inklusive hämtningsservern att utvecklas och ger nya möjligheter.</span><span class="sxs-lookup"><span data-stu-id="5ec81-122">As DSC is expected to evolve at cloud cadence, the underlying technology including pull server is also expected to evolve and to introduce new capabilities.</span></span> <span data-ttu-id="5ec81-123">Det här dokumentet innehåller en versionstabell i tillägget som innehåller referenser till tidigare versioner och referenser till framtida söker lösningar för att uppmuntra framtida Designer.</span><span class="sxs-lookup"><span data-stu-id="5ec81-123">This document includes a version table in the appendix that provides references to previous releases and references to future looking solutions to encourage forward-looking designs.</span></span>

<span data-ttu-id="5ec81-124">Det här dokumentet två huvuddelar:</span><span class="sxs-lookup"><span data-stu-id="5ec81-124">The two major sections of this document:</span></span>

 - <span data-ttu-id="5ec81-125">Planera konfiguration</span><span class="sxs-lookup"><span data-stu-id="5ec81-125">Configuration Planning</span></span>
 - <span data-ttu-id="5ec81-126">Installationsguiden</span><span class="sxs-lookup"><span data-stu-id="5ec81-126">Installation Guide</span></span>

### <a name="versions-of-the-windows-management-framework"></a><span data-ttu-id="5ec81-127">Versioner av Windows Management Framework</span><span class="sxs-lookup"><span data-stu-id="5ec81-127">Versions of the Windows Management Framework</span></span>
<span data-ttu-id="5ec81-128">Informationen i det här dokumentet är avsedd att tillämpa på Windows Management Framework 5.0.</span><span class="sxs-lookup"><span data-stu-id="5ec81-128">The information in this document is intended to apply to Windows Management Framework 5.0.</span></span> <span data-ttu-id="5ec81-129">WMF 5.0 inte krävs för distribution och drift av en pull-server, är version 5.0 fokus för det här dokumentet.</span><span class="sxs-lookup"><span data-stu-id="5ec81-129">While WMF 5.0 is not required for deploying and operating a pull server, version 5.0 is the focus of this document.</span></span>

### <a name="windows-powershell-desired-state-configuration"></a><span data-ttu-id="5ec81-130">Windows PowerShell önskad Tillståndskonfiguration</span><span class="sxs-lookup"><span data-stu-id="5ec81-130">Windows PowerShell Desired State Configuration</span></span>
<span data-ttu-id="5ec81-131">Önskat tillstånd Configuration (DSC) är en plattform som gör att distribuera och hantera konfigurationsdata med hjälp av en branschen syntax som heter Managed Object Format (MOF) för att beskriva Common Information Model (CIM).</span><span class="sxs-lookup"><span data-stu-id="5ec81-131">Desired State Configuration (DSC) is a management platform that enables deploying and managing configuration data by using an industry syntax named the Managed Object Format (MOF) to describe the Common Information Model (CIM).</span></span> <span data-ttu-id="5ec81-132">Det finns ett projekt med öppen källkod, Open Management Infrastructure (OMI), för att ytterligare utvecklingen av dessa normer över plattformar, inklusive Linux och -maskinvara, operativsystem.</span><span class="sxs-lookup"><span data-stu-id="5ec81-132">An open source project, Open Management Infrastructure (OMI), exists to further development of these standards across platforms including Linux and network hardware operating systems.</span></span> <span data-ttu-id="5ec81-133">Mer information finns i [DMTF sida länkar till MOF-specifikationer](http://dmtf.org/standards/cim), och [OMI dokument och källan](https://collaboration.opengroup.org/omi/documents.php).</span><span class="sxs-lookup"><span data-stu-id="5ec81-133">For more information, see the [DMTF page linking to MOF specifications](http://dmtf.org/standards/cim), and [OMI Documents and Source](https://collaboration.opengroup.org/omi/documents.php).</span></span>

<span data-ttu-id="5ec81-134">Windows PowerShell innehåller en uppsättning tillägg för Desired State Configuration som du kan använda för att skapa och hantera deklarativ konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="5ec81-134">Windows PowerShell provides a set of language extensions for Desired State Configuration that you can use to create and manage declarative configurations.</span></span>

### <a name="pull-server-role"></a><span data-ttu-id="5ec81-135">Pull-serverrollen</span><span class="sxs-lookup"><span data-stu-id="5ec81-135">Pull server role</span></span>
<span data-ttu-id="5ec81-136">En pull-server är en centraliserad tjänst för att lagra konfigurationer som kommer att vara tillgänglig för målnoder.</span><span class="sxs-lookup"><span data-stu-id="5ec81-136">A pull server provides a centralized service to store configurations that will be accessible to target nodes.</span></span>

<span data-ttu-id="5ec81-137">Pull-serverrollen kan distribueras som en webbserver-instans eller en SMB filresurs.</span><span class="sxs-lookup"><span data-stu-id="5ec81-137">The pull server role can be deployed as either a Web Server instance or an SMB file share.</span></span> <span data-ttu-id="5ec81-138">Web server-kapacitet innehåller ett OData-gränssnitt och att inkludera välja funktioner för målnoder rapporterar bekräftelse av lyckats eller misslyckats eftersom konfigurationer tillämpas.</span><span class="sxs-lookup"><span data-stu-id="5ec81-138">The web server capability includes an OData interface and can optionally include capabilities for target nodes to report back confirmation of success or failure as configurations are applied.</span></span> <span data-ttu-id="5ec81-139">Den här funktionen är användbar i miljöer där det finns ett stort antal målnoder.</span><span class="sxs-lookup"><span data-stu-id="5ec81-139">This functionality is useful in environments where there are a large number of target nodes.</span></span>
<span data-ttu-id="5ec81-140">När du har konfigurerat en målnod (kallas även en klient) för att peka på hämtningsservern i den senaste konfigurationen hämtas och aktiveras data och alla nödvändiga skript.</span><span class="sxs-lookup"><span data-stu-id="5ec81-140">After configuring a target node (also referred to as a client) to point to the pull server the latest configuration data and any required scripts are downloaded and applied.</span></span> <span data-ttu-id="5ec81-141">Detta kan inträffa som en enstaka distribution eller som ett nytt förekommer jobb som är dessutom hämtningsservern i en viktig tillgång för att hantera ändring i större skala.</span><span class="sxs-lookup"><span data-stu-id="5ec81-141">This can happen as a one-time deployment or as a re-occurring job which also makes the pull server an important asset for managing change at scale.</span></span> <span data-ttu-id="5ec81-142">Mer information finns i [Windows PowerShell önskad tillstånd hämtar Konfigurationsservrar](https://technet.microsoft.com/library/dn249913.aspx) och [Push och Pull-konfigurationslägen](https://technet.microsoft.com/library/dn249913.aspx).</span><span class="sxs-lookup"><span data-stu-id="5ec81-142">For more information, see [Windows PowerShell Desired State Configuration Pull Servers](https://technet.microsoft.com/library/dn249913.aspx) and [Push and Pull Configuration Modes](https://technet.microsoft.com/library/dn249913.aspx).</span></span>

## <a name="configuration-planning"></a><span data-ttu-id="5ec81-143">Planera konfiguration</span><span class="sxs-lookup"><span data-stu-id="5ec81-143">Configuration planning</span></span>

<span data-ttu-id="5ec81-144">För alla företag programdistribution finns information som samlas in i förväg för att planera för rätt arkitektur och förberedas för de steg som krävs för att slutföra distributionen.</span><span class="sxs-lookup"><span data-stu-id="5ec81-144">For any enterprise software deployment there is information that can be collected in advance to help plan for the correct architecture and to be prepared for the steps required to complete the deployment.</span></span> <span data-ttu-id="5ec81-145">Följande avsnitt innehåller information om hur du förbereder och de organisatoriska anslutningar som behöver förmodligen inträffa i förväg.</span><span class="sxs-lookup"><span data-stu-id="5ec81-145">The following sections provide information regarding how to prepare and the organizational connections that will likely need to happen in advance.</span></span>

### <a name="software-requirements"></a><span data-ttu-id="5ec81-146">Programvarukrav</span><span class="sxs-lookup"><span data-stu-id="5ec81-146">Software requirements</span></span>

<span data-ttu-id="5ec81-147">Distribution av en pull-server kräver funktionen DSC-tjänsten i Windows Server.</span><span class="sxs-lookup"><span data-stu-id="5ec81-147">Deployment of a pull server requires the DSC Service feature of Windows Server.</span></span> <span data-ttu-id="5ec81-148">Den här funktionen introducerades i Windows Server 2012 och har uppdaterats via pågående versioner av Windows Management Framework (WMF).</span><span class="sxs-lookup"><span data-stu-id="5ec81-148">This feature was introduced in Windows Server 2012, and has been updated through ongoing releases of Windows Management Framework (WMF).</span></span>

### <a name="software-downloads"></a><span data-ttu-id="5ec81-149">Nedladdning av programvara</span><span class="sxs-lookup"><span data-stu-id="5ec81-149">Software downloads</span></span>

<span data-ttu-id="5ec81-150">Förutom att installera det senaste innehållet från Windows Update finns två hämtningar anses vara bästa praxis för att distribuera en DSC pull-server: den senaste versionen av Windows Management Framework och en DSC-modul för att automatisera etablering av pull-servrar.</span><span class="sxs-lookup"><span data-stu-id="5ec81-150">In addition to installing the latest content from Windows Update, there are two downloads considered best practice to deploy a DSC pull server: The latest version of Windows Management Framework, and a DSC module to automate pull server provisioning.</span></span>

### <a name="wmf"></a><span data-ttu-id="5ec81-151">WMF</span><span class="sxs-lookup"><span data-stu-id="5ec81-151">WMF</span></span>

<span data-ttu-id="5ec81-152">Windows Server 2012 R2 innehåller en funktion som heter DSC-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="5ec81-152">Windows Server 2012 R2 includes a feature named the DSC Service.</span></span> <span data-ttu-id="5ec81-153">Funktionen DSC-tjänsten tillhandahåller pull serverfunktionalitet, inklusive de binära filerna som har stöd för OData-slutpunkten.</span><span class="sxs-lookup"><span data-stu-id="5ec81-153">The DSC Service feature provides the pull server functionality, including the binaries that support the OData endpoint.</span></span>
<span data-ttu-id="5ec81-154">WMF ingår i Windows Server och uppdateras i en flexibel takt mellan versioner av Windows Server.</span><span class="sxs-lookup"><span data-stu-id="5ec81-154">WMF is included in Windows Server and is updated on an agile cadence between Windows Server releases.</span></span> <span data-ttu-id="5ec81-155">[Nya versioner av WMF 5.0](http://aka.ms/wmf5latest) kan innehålla uppdateringar till funktionen DSC-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="5ec81-155">[New versions of WMF 5.0](http://aka.ms/wmf5latest)  can include updates to the DSC Service feature.</span></span> <span data-ttu-id="5ec81-156">Därför är det bäst att hämta den senaste versionen av WMF och granska viktig information för att avgöra om versionen innehåller en uppdatering av funktionen DSC-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="5ec81-156">For this reason, it is a best practice to download the latest release of WMF and to review the release notes to determine if the release includes an update to the DSC service feature.</span></span> <span data-ttu-id="5ec81-157">Du bör också granska avsnittet i viktig information som anger om den design för en uppdatering eller scenario statusen stabilt och experiment.</span><span class="sxs-lookup"><span data-stu-id="5ec81-157">You should also review the section of the release notes that indicates whether the design status for an update or scenario is listed as stable or experimental.</span></span>
<span data-ttu-id="5ec81-158">Om du vill tillåta en smidig övergång cykel enskilda funktioner kan deklareras stabil, är vilket anger att funktionen redo att användas i en produktionsmiljö, även när WMF släpps i förhandsgranskningen.</span><span class="sxs-lookup"><span data-stu-id="5ec81-158">To allow for an agile release cycle, individual features can be declared stable, which indicates the feature is ready to be used in a production environment even while WMF is released in preview.</span></span>
<span data-ttu-id="5ec81-159">Andra funktioner som tidigare har uppdaterats av WMF versioner (se WMF viktig information för detaljerat):</span><span class="sxs-lookup"><span data-stu-id="5ec81-159">Other features that have historically been updated by WMF releases (see the WMF Release Notes for further detail):</span></span>

 - <span data-ttu-id="5ec81-160">Windows PowerShell, Windows PowerShell Integrated Scripting</span><span class="sxs-lookup"><span data-stu-id="5ec81-160">Windows PowerShell Windows PowerShell Integrated Scripting</span></span>
 - <span data-ttu-id="5ec81-161">Environment (ISE) Windows PowerShell-webbtjänster (Management OData</span><span class="sxs-lookup"><span data-stu-id="5ec81-161">Environment (ISE) Windows PowerShell Web Services (Management OData</span></span>
 - <span data-ttu-id="5ec81-162">IIS-tillägg) Windows PowerShell önskad Tillståndskonfiguration DSC)</span><span class="sxs-lookup"><span data-stu-id="5ec81-162">IIS Extension)  Windows PowerShell Desired State Configuration (DSC)</span></span>
 - <span data-ttu-id="5ec81-163">Windows Remote Management (WinRM) Windows Management Instrumentation (WMI)</span><span class="sxs-lookup"><span data-stu-id="5ec81-163">Windows Remote Management (WinRM) Windows Management Instrumentation (WMI)</span></span>

### <a name="dsc-resource"></a><span data-ttu-id="5ec81-164">DSC-resurs</span><span class="sxs-lookup"><span data-stu-id="5ec81-164">DSC resource</span></span>

<span data-ttu-id="5ec81-165">En pull-serverdistribution kan förenklas genom att etablera tjänsten med hjälp av ett DSC-konfigurationsskript.</span><span class="sxs-lookup"><span data-stu-id="5ec81-165">A pull server deployment can be simplified by provisioning the service using a DSC configuration script.</span></span> <span data-ttu-id="5ec81-166">Det här dokumentet innehåller konfigurationsskript som kan användas för att distribuera en klar servernoden i produktion.</span><span class="sxs-lookup"><span data-stu-id="5ec81-166">This document includes configuration scripts that can be used to deploy a production ready server node.</span></span> <span data-ttu-id="5ec81-167">Om du vill använda konfigurationsskript en DSC-modul krävs som inte ingår i Windows Server.</span><span class="sxs-lookup"><span data-stu-id="5ec81-167">To use the configuration scripts, a DSC module is required that is not included in Windows Server.</span></span> <span data-ttu-id="5ec81-168">Nödvändiga Modulnamn **xPSDesiredStateConfiguration**, som innehåller resursen DSC **xDscWebService**.</span><span class="sxs-lookup"><span data-stu-id="5ec81-168">The required module name is **xPSDesiredStateConfiguration**, which includes the DSC resource **xDscWebService**.</span></span> <span data-ttu-id="5ec81-169">Modulen xPSDesiredStateConfiguration kan hämtas [här](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d).</span><span class="sxs-lookup"><span data-stu-id="5ec81-169">The xPSDesiredStateConfiguration module can be downloaded [here](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d).</span></span>

<span data-ttu-id="5ec81-170">Använd den **installera modulen** cmdlet från den **PowerShellGet** modul.</span><span class="sxs-lookup"><span data-stu-id="5ec81-170">Use the **Install-Module** cmdlet from the **PowerShellGet** module.</span></span>

```powershell
Install-Module xPSDesiredStateConfiguration
```

<span data-ttu-id="5ec81-171">Den **PowerShellGet** modulen hämtar modulen:</span><span class="sxs-lookup"><span data-stu-id="5ec81-171">The **PowerShellGet** module will download the module to:</span></span>

`C:\Program Files\Windows PowerShell\Modules`

<span data-ttu-id="5ec81-172">Planera aktivitet</span><span class="sxs-lookup"><span data-stu-id="5ec81-172">Planning task</span></span>|
---|
<span data-ttu-id="5ec81-173">Du har tillgång till installationsfilerna för Windows Server 2012 R2?</span><span class="sxs-lookup"><span data-stu-id="5ec81-173">Do you have access to the installation files for Windows Server 2012 R2?</span></span>|
<span data-ttu-id="5ec81-174">Distributionsmiljö har Internetåtkomst för att hämta WMF och modulen från galleriet online?</span><span class="sxs-lookup"><span data-stu-id="5ec81-174">Will the deployment environment have Internet access to download WMF and the module from the online gallery?</span></span>|
<span data-ttu-id="5ec81-175">Hur ska du installera de senaste säkerhetsuppdateringarna när du har installerat operativsystemet?</span><span class="sxs-lookup"><span data-stu-id="5ec81-175">How will you install the latest security updates after installing the operating system?</span></span>|
<span data-ttu-id="5ec81-176">Miljön har Internetåtkomst för att hämta uppdateringar eller den har en lokal server i Windows Server Update Services (WSUS)?</span><span class="sxs-lookup"><span data-stu-id="5ec81-176">Will the environment have Internet access to obtain updates, or will it have a local Windows Server Update Services (WSUS) server?</span></span>|
<span data-ttu-id="5ec81-177">Har du tillgång till installationsfilerna för Windows Server som redan omfattar uppdateringar via offline injection?</span><span class="sxs-lookup"><span data-stu-id="5ec81-177">Do you have access to Windows Server installation files that already include updates through offline injection?</span></span>|

### <a name="hardware-requirements"></a><span data-ttu-id="5ec81-178">Maskinvarukrav</span><span class="sxs-lookup"><span data-stu-id="5ec81-178">Hardware requirements</span></span>

<span data-ttu-id="5ec81-179">Pull-serverdistribution stöds på både fysiska och virtuella servrar.</span><span class="sxs-lookup"><span data-stu-id="5ec81-179">Pull server deployments are supported on both physical and virtual servers.</span></span> <span data-ttu-id="5ec81-180">Storlek för kraven på hämtningsservern överensstämmer med kraven för Windows Server 2012 R2.</span><span class="sxs-lookup"><span data-stu-id="5ec81-180">The sizing requirements for pull server align with the requirements for Windows Server 2012 R2.</span></span>

<span data-ttu-id="5ec81-181">Processor: 1,4 GHz 64-bitars processor minne: 512 MB ledigt diskutrymme: 32 GB nätverk: Gigabit Ethernet-nätverkskort</span><span class="sxs-lookup"><span data-stu-id="5ec81-181">CPU: 1.4 GHz 64-bit processor Memory: 512 MB Disk Space: 32 GB Network: Gigabit Ethernet Adapter</span></span>

<span data-ttu-id="5ec81-182">Planera aktivitet</span><span class="sxs-lookup"><span data-stu-id="5ec81-182">Planning task</span></span>|
---|
<span data-ttu-id="5ec81-183">Du distribuerar på fysisk maskinvara eller på en virtualiseringsplattform?</span><span class="sxs-lookup"><span data-stu-id="5ec81-183">Will you deploy on physical hardware or on a virtualization platform?</span></span>|
<span data-ttu-id="5ec81-184">Vad är processen för att begära en ny server för målmiljön?</span><span class="sxs-lookup"><span data-stu-id="5ec81-184">What is the process to request a new server for your target environment?</span></span>|
<span data-ttu-id="5ec81-185">Vad är den genomsnittliga tid för en server ska bli tillgänglig?</span><span class="sxs-lookup"><span data-stu-id="5ec81-185">What is the average turnaround time for a server to become available?</span></span>|
<span data-ttu-id="5ec81-186">Vilken storlek du begär servern?</span><span class="sxs-lookup"><span data-stu-id="5ec81-186">What size server will you request?</span></span>|

### <a name="accounts"></a><span data-ttu-id="5ec81-187">Konton</span><span class="sxs-lookup"><span data-stu-id="5ec81-187">Accounts</span></span>

<span data-ttu-id="5ec81-188">Det finns inga krav på tjänstkonto att distribuera en pull-serverinstans.</span><span class="sxs-lookup"><span data-stu-id="5ec81-188">There are no service account requirements to deploy a pull server instance.</span></span>
<span data-ttu-id="5ec81-189">Det finns emellertid scenarier där webbplatsen kan köras i kontexten för ett lokalt användarkonto.</span><span class="sxs-lookup"><span data-stu-id="5ec81-189">However, there are scenarios where the website could run in the context of a local user account.</span></span>
<span data-ttu-id="5ec81-190">Till exempel om det är nödvändigt att åtkomst en storage-resurs för webbplatsens innehåll och Windows Server eller enhet som är värd för storage-resurs är inte ansluten till en domän.</span><span class="sxs-lookup"><span data-stu-id="5ec81-190">For example, if there is a need to access a storage share for website content and either the Windows Server or the device hosting the storage share are not domain joined.</span></span>

### <a name="dns-records"></a><span data-ttu-id="5ec81-191">DNS-poster</span><span class="sxs-lookup"><span data-stu-id="5ec81-191">DNS records</span></span>

<span data-ttu-id="5ec81-192">Du behöver ett servernamn som du använder när du konfigurerar klienter för att arbeta med en pull-servermiljö.</span><span class="sxs-lookup"><span data-stu-id="5ec81-192">You will need a server name to use when configuring clients to work with a pull server environment.</span></span>
<span data-ttu-id="5ec81-193">I testmiljöer, oftast serverns värdnamn eller IP-adressen för servern kan användas om DNS-namnmatchningen inte är tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="5ec81-193">In test environments, typically the server hostname is used, or the IP address for the server can be used if DNS name resolution is not available.</span></span>
<span data-ttu-id="5ec81-194">Det bästa sättet är att skapa en DNS CNAME-post i produktionsmiljöer eller i en testmiljö som är avsedd att representera en Produktionsdistribution.</span><span class="sxs-lookup"><span data-stu-id="5ec81-194">In production environments or in a lab environment that is intended to represent a production deployment, the best practice is to create a DNS CNAME record.</span></span>

<span data-ttu-id="5ec81-195">Ett DNS CNAME kan du skapa ett alias du vill referera till din värd (A) post.</span><span class="sxs-lookup"><span data-stu-id="5ec81-195">A DNS CNAME allows you to create an alias to refer to your host (A) record.</span></span>
<span data-ttu-id="5ec81-196">Syftet med den ytterligare namnposten är att öka flexibiliteten ändras inte behövs i framtiden.</span><span class="sxs-lookup"><span data-stu-id="5ec81-196">The intent of the additional name record is to increase flexibility should a change be required in the future.</span></span>
<span data-ttu-id="5ec81-197">En CNAME-post kan hjälpa för att isolera klientkonfigurationen så att ändringar av server-miljö, t.ex ersätter en pull-server eller lägga till ytterligare pull-servrar, inte kräver en motsvarande ändring i klientkonfigurationen.</span><span class="sxs-lookup"><span data-stu-id="5ec81-197">A CNAME can help to isolate the client configuration so that changes to the server environment, such as replacing a pull server or adding additional pull servers, will not require a corresponding change to the client configuration.</span></span>

<span data-ttu-id="5ec81-198">Tänk lösningsarkitekturen när du väljer ett namn för DNS-posten.</span><span class="sxs-lookup"><span data-stu-id="5ec81-198">When choosing a name for the DNS record, keep the solution architecture in mind.</span></span>
<span data-ttu-id="5ec81-199">Om med belastningsutjämning, måste certifikatet som används för att skydda trafik via HTTPS delar samma namn som DNS-posten.</span><span class="sxs-lookup"><span data-stu-id="5ec81-199">If using load balancing, the certificate used to secure traffic over HTTPS will need to share the same name as the DNS record.</span></span>

<span data-ttu-id="5ec81-200">Scenario</span><span class="sxs-lookup"><span data-stu-id="5ec81-200">Scenario</span></span> |<span data-ttu-id="5ec81-201">Bästa praxis</span><span class="sxs-lookup"><span data-stu-id="5ec81-201">Best Practice</span></span>
:---|:---
<span data-ttu-id="5ec81-202">Testmiljö</span><span class="sxs-lookup"><span data-stu-id="5ec81-202">Test Environment</span></span> |<span data-ttu-id="5ec81-203">Återskapa planerad produktionsmiljön, om möjligt.</span><span class="sxs-lookup"><span data-stu-id="5ec81-203">Reproduce the planned production environment, if possible.</span></span> <span data-ttu-id="5ec81-204">Ett värdnamn för servern är lämpligt för enkel konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="5ec81-204">A server hostname is suitable for simple configurations.</span></span> <span data-ttu-id="5ec81-205">Om DNS inte är tillgänglig, kan en IP-adress användas i stället för ett värdnamn.</span><span class="sxs-lookup"><span data-stu-id="5ec81-205">If DNS is not available, an IP address may be used in lieu of a hostname.</span></span>|
<span data-ttu-id="5ec81-206">Distribution av enskild nod</span><span class="sxs-lookup"><span data-stu-id="5ec81-206">Single Node Deployment</span></span> |<span data-ttu-id="5ec81-207">Skapa en DNS CNAME-post som pekar på serverns värdnamn.</span><span class="sxs-lookup"><span data-stu-id="5ec81-207">Create a DNS CNAME record that points to the server hostname.</span></span>|

<span data-ttu-id="5ec81-208">Mer information finns i [konfigurera DNS för resursallokering i Windows Server](https://technet.microsoft.com/en-us/library/cc787484(v=ws.10).aspx).</span><span class="sxs-lookup"><span data-stu-id="5ec81-208">For more information, see [Configuring DNS Round Robin in Windows Server](https://technet.microsoft.com/en-us/library/cc787484(v=ws.10).aspx).</span></span>

<span data-ttu-id="5ec81-209">Planera aktivitet</span><span class="sxs-lookup"><span data-stu-id="5ec81-209">Planning task</span></span>|
---|
<span data-ttu-id="5ec81-210">Vet du att kontakta om du vill att DNS-poster skapas och ändras?</span><span class="sxs-lookup"><span data-stu-id="5ec81-210">Do you know who to contact to have DNS records created and changed?</span></span>|
<span data-ttu-id="5ec81-211">Vad är den genomsnittliga tid en begäran om en DNS-post?</span><span class="sxs-lookup"><span data-stu-id="5ec81-211">What is the average turnaround for a request for a DNS record?</span></span>|
<span data-ttu-id="5ec81-212">Behöver du begära statiska värdnamn (A)-poster för servrar?</span><span class="sxs-lookup"><span data-stu-id="5ec81-212">Do you need to request static Hostname (A) records for servers?</span></span>|
<span data-ttu-id="5ec81-213">Vad du begär som en CNAME-post?</span><span class="sxs-lookup"><span data-stu-id="5ec81-213">What will you request as a CNAME?</span></span>|
<span data-ttu-id="5ec81-214">Om det behövs, vilken typ av belastningsutjämning lösning ska du använda?</span><span class="sxs-lookup"><span data-stu-id="5ec81-214">If needed, what type of Load Balancing solution will you utilize?</span></span> <span data-ttu-id="5ec81-215">(se avsnittet belastningsutjämning för information)</span><span class="sxs-lookup"><span data-stu-id="5ec81-215">(see section titled Load Balancing for details)</span></span>|

### <a name="public-key-infrastructure"></a><span data-ttu-id="5ec81-216">Infrastruktur för offentliga nycklar</span><span class="sxs-lookup"><span data-stu-id="5ec81-216">Public Key Infrastructure</span></span>

<span data-ttu-id="5ec81-217">De flesta organisationer kräver idag att nätverkstrafik, särskilt trafik som innehåller dessa känsliga data om hur servrar har konfigurerats, måste verifieras och krypterad under överföringen.</span><span class="sxs-lookup"><span data-stu-id="5ec81-217">Most organizations today require that network traffic, especially traffic that includes such sensitive data as how servers are configured, must be validated and/or encrypted during transit.</span></span>
<span data-ttu-id="5ec81-218">När det är möjligt att distribuera en pull-server med hjälp av HTTP som underlättar klientbegäranden i klartext, är det en bra idé att skydda trafik med hjälp av HTTPS.</span><span class="sxs-lookup"><span data-stu-id="5ec81-218">While it is possible to deploy a pull server using HTTP which facilitates client requests in clear text, it is a best practice to secure traffic using HTTPS.</span></span> <span data-ttu-id="5ec81-219">Tjänsten kan konfigureras för att använda HTTPS med en uppsättning parametrar i DSC-resursen **xPSDesiredStateConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="5ec81-219">The service can be configured to use HTTPS using a set of parameters in the DSC resource **xPSDesiredStateConfiguration**.</span></span>

<span data-ttu-id="5ec81-220">Certifikatkrav för säker HTTPS-trafik för pull-servern är inte annat än att skydda alla andra HTTPS-webbplats.</span><span class="sxs-lookup"><span data-stu-id="5ec81-220">The certificate requirements to secure HTTPS traffic for pull server are not different than securing any other HTTPS web site.</span></span> <span data-ttu-id="5ec81-221">Den **webbservern** mallen i Certifikattjänster i Windows Server uppfyller de nödvändiga funktionerna.</span><span class="sxs-lookup"><span data-stu-id="5ec81-221">The **Web Server** template in a Windows Server Certificate Services satisfies the required capabilities.</span></span>

<span data-ttu-id="5ec81-222">Planera aktivitet</span><span class="sxs-lookup"><span data-stu-id="5ec81-222">Planning task</span></span>|
---|
<span data-ttu-id="5ec81-223">Om certifikatbegäran inte sker automatiskt, som behöver du kontakta ett certifikat på begäran?</span><span class="sxs-lookup"><span data-stu-id="5ec81-223">If certificate requests are not automated, who will you need to contact to requests a certificate?</span></span>|
<span data-ttu-id="5ec81-224">Vad är den genomsnittliga tid för begäran?</span><span class="sxs-lookup"><span data-stu-id="5ec81-224">What is the average turnaround for the request?</span></span>|
<span data-ttu-id="5ec81-225">Hur certifikatfilen överförs till dig?</span><span class="sxs-lookup"><span data-stu-id="5ec81-225">How will the certificate file be transferred to you?</span></span>|
<span data-ttu-id="5ec81-226">Hur certifikatets privata nyckel överförs till dig?</span><span class="sxs-lookup"><span data-stu-id="5ec81-226">How will the certificate private key be transferred to you?</span></span>|
<span data-ttu-id="5ec81-227">Hur lång tid är förfallotiden som standard?</span><span class="sxs-lookup"><span data-stu-id="5ec81-227">How long is the default expiration time?</span></span>|
<span data-ttu-id="5ec81-228">Har du lösas på ett DNS-namn för pull-servermiljö, som du kan använda för certifikatets namn?</span><span class="sxs-lookup"><span data-stu-id="5ec81-228">Have you settled on a DNS name for the pull server environment, that you can use for the certificate name?</span></span>|

### <a name="choosing-an-architecture"></a><span data-ttu-id="5ec81-229">Om du väljer en arkitektur</span><span class="sxs-lookup"><span data-stu-id="5ec81-229">Choosing an architecture</span></span>

<span data-ttu-id="5ec81-230">En pull-server kan distribueras med hjälp av antingen en webbtjänst som IIS eller en SMB filresurs.</span><span class="sxs-lookup"><span data-stu-id="5ec81-230">A pull server can be deployed using either a web service hosted on IIS, or an SMB file share.</span></span> <span data-ttu-id="5ec81-231">I de flesta fall är ger web service alternativet större flexibilitet.</span><span class="sxs-lookup"><span data-stu-id="5ec81-231">In most situations, the web service option will provide greater flexibility.</span></span> <span data-ttu-id="5ec81-232">Det är inte ovanligt att HTTPS-trafik färdas över nätverksgränser, medan SMB-trafik är ofta filtrerade eller blockeras mellan nätverk.</span><span class="sxs-lookup"><span data-stu-id="5ec81-232">It is not uncommon for HTTPS traffic to traverse network boundaries, whereas SMB traffic is often filtered or blocked between networks.</span></span> <span data-ttu-id="5ec81-233">Webbtjänsten ger också möjlighet att inkludera en överensstämmelse Server eller Web Reporting Manager (både ämnen tas upp i en framtida version av det här dokumentet) som tillhandahåller en mekanism för klienter för att rapportera status tillbaka till en server för centraliserad synlighet.</span><span class="sxs-lookup"><span data-stu-id="5ec81-233">The web service also offers the option to include a Conformance Server or Web Reporting Manager (both topics to be addressed in a future version of this document) that provide a mechanism for clients to report status back to a server for centralized visibility.</span></span>
<span data-ttu-id="5ec81-234">SMB ger ett alternativ för miljöer där principen anger att en server inte kan användas och för andra miljökrav som gör en rollen som webbserver oönskade.</span><span class="sxs-lookup"><span data-stu-id="5ec81-234">SMB provides an option for environments where policy dictates that a web server should not be utilized, and for other environmental requirements that make a web server role undesirable.</span></span>
<span data-ttu-id="5ec81-235">Kom ihåg att utvärdera kraven för signering och kryptering av trafik i båda fallen.</span><span class="sxs-lookup"><span data-stu-id="5ec81-235">In either case, remember to evaluate the requirements for signing and encrypting traffic.</span></span> <span data-ttu-id="5ec81-236">Är alla alternativ vara värt att hänsyn tagits till HTTPS, SMB-signering och IPSEC-principer.</span><span class="sxs-lookup"><span data-stu-id="5ec81-236">HTTPS, SMB signing, and IPSEC policies are all options worth considering.</span></span>

#### <a name="load-balancing"></a><span data-ttu-id="5ec81-237">Belastningsutjämning</span><span class="sxs-lookup"><span data-stu-id="5ec81-237">Load balancing</span></span>
<span data-ttu-id="5ec81-238">Klienter som interagerar med webbtjänsten gör en begäran om information som returneras i ett enda svar.</span><span class="sxs-lookup"><span data-stu-id="5ec81-238">Clients interacting with the web service make a request for information that is returned in a single response.</span></span> <span data-ttu-id="5ec81-239">Inga sekventiella förfrågningar krävs, så det inte är nödvändigt för belastningsutjämning plattform för att säkerställa sessioner underhålls på en enskild server när som helst i tid.</span><span class="sxs-lookup"><span data-stu-id="5ec81-239">No sequential requests are required, so it is not necessary for the load balancing platform to ensure sessions are maintained on a single server at any point in time.</span></span>

<span data-ttu-id="5ec81-240">Planera aktivitet</span><span class="sxs-lookup"><span data-stu-id="5ec81-240">Planning task</span></span>|
---|
<span data-ttu-id="5ec81-241">Vilken lösning ska användas för belastningsutjämning trafik mellan servrar?</span><span class="sxs-lookup"><span data-stu-id="5ec81-241">What solution will be used for load balancing traffic across servers?</span></span>|
<span data-ttu-id="5ec81-242">Om du använder en maskinvarubaserad belastningsutjämnare som tar en begäran om att lägga till en ny konfiguration för enheten?</span><span class="sxs-lookup"><span data-stu-id="5ec81-242">If using a hardware load balancer, who will take a request to add a new configuration to the device?</span></span>|
<span data-ttu-id="5ec81-243">Vad är den genomsnittliga tid för en begäran om att konfigurera en ny belastning belastningsutjämnade webbtjänsten?</span><span class="sxs-lookup"><span data-stu-id="5ec81-243">What is the average turnaround for a request to configure a new load balanced web service?</span></span>|
<span data-ttu-id="5ec81-244">Vilken information kommer att krävas för begäran?</span><span class="sxs-lookup"><span data-stu-id="5ec81-244">What information will be required for the request?</span></span>|
<span data-ttu-id="5ec81-245">Du måste begära en ytterligare IP-adress eller gruppen som ansvarar för belastningsutjämning hanterar som?</span><span class="sxs-lookup"><span data-stu-id="5ec81-245">Will you need to request an additional IP or will the team responsible for load balancing handle that?</span></span>|
<span data-ttu-id="5ec81-246">Har du DNS-poster som behövs och det krävs av gruppen som ansvarar för att konfigurera nätverkslösning för belastningsutjämning?</span><span class="sxs-lookup"><span data-stu-id="5ec81-246">Do you have the DNS records needed, and will this be required by the team responsible for configuring the load balancing solution?</span></span>|
<span data-ttu-id="5ec81-247">Läsa in belastningsutjämning lösningen kräver att PKI ska hanteras av enheten eller kan den belastningsutjämna HTTPS-trafik, så länge det finns inga sessionskrav?</span><span class="sxs-lookup"><span data-stu-id="5ec81-247">Does the load balancing solution require that PKI be handled by the device or can it load balance HTTPS traffic as long as there are no session requirements?</span></span>|

### <a name="staging-configurations-and-modules-on-the-pull-server"></a><span data-ttu-id="5ec81-248">Mellanlagring av konfigurationer och moduler på hämtningsservern</span><span class="sxs-lookup"><span data-stu-id="5ec81-248">Staging configurations and modules on the pull server</span></span>

<span data-ttu-id="5ec81-249">Som en del av konfigurationen planering, behöver du tycker om vilka DSC-moduler och konfigurationer som kommer att finnas av pull-servern.</span><span class="sxs-lookup"><span data-stu-id="5ec81-249">As part of configuration planning, you will need to think about which DSC modules and configurations will be hosted by the pull server.</span></span> <span data-ttu-id="5ec81-250">För att planera konfigurationen är det viktigt att ha en grundläggande förståelse för hur du förbereder och distribuerar innehåll till en pull-server.</span><span class="sxs-lookup"><span data-stu-id="5ec81-250">For the purpose of configuration planning it is important to have a basic understanding of how to prepare and deploy content to a pull server.</span></span>

<span data-ttu-id="5ec81-251">Det här avsnittet kommer i framtiden, expanderas och ingår i en Funktionsguide för DSC Pull-Server.</span><span class="sxs-lookup"><span data-stu-id="5ec81-251">In the future, this section will be expanded and included in an Operations Guide for DSC Pull Server.</span></span>  <span data-ttu-id="5ec81-252">Guiden diskuterar dagliga processen för att hantera moduler och konfigurationer över tid med automatisering.</span><span class="sxs-lookup"><span data-stu-id="5ec81-252">The guide will discuss the day to day process for managing modules and configurations over time with automation.</span></span>

#### <a name="dsc-modules"></a><span data-ttu-id="5ec81-253">DSC-moduler</span><span class="sxs-lookup"><span data-stu-id="5ec81-253">DSC modules</span></span>
<span data-ttu-id="5ec81-254">Klienter som begär en konfiguration måste DSC-moduler som krävs.</span><span class="sxs-lookup"><span data-stu-id="5ec81-254">Clients that request a configuration will need the required DSC modules.</span></span> <span data-ttu-id="5ec81-255">En funktion av pull-server är att automatisera distribution på begäran av DSC-moduler till klienter.</span><span class="sxs-lookup"><span data-stu-id="5ec81-255">A functionality of the pull server is to automate distribution on demand of DSC modules to clients.</span></span> <span data-ttu-id="5ec81-256">Om du distribuerar en pull-server för första gången, kanske som ett labb eller konceptbevis, ska du troligen är beroende av DSC-moduler som är tillgängliga från offentliga databaser, till exempel PowerShell-galleriet eller PowerShell.org GitHub-lagringsplatser för DSC-moduler .</span><span class="sxs-lookup"><span data-stu-id="5ec81-256">If you are deploying a pull server for the first time, perhaps as a lab or proof of concept, you are likely going to depend on DSC modules that are available from public repositories such as the PowerShell Gallery or the PowerShell.org GitHub repositories for DSC modules.</span></span>

<span data-ttu-id="5ec81-257">Det är viktigt att komma ihåg att även för tillförlitliga online källor, till exempel PowerShell-galleriet alla moduler som har hämtats från en offentlig databas bör granskas av någon med PowerShell upplevelse och kunskap om miljön där modulerna som kommer att använda före som används i produktionen.</span><span class="sxs-lookup"><span data-stu-id="5ec81-257">It is critical to remember that even for trusted online sources such as the PowerShell Gallery, any module that is downloaded from a public repository should be reviewed by someone with PowerShell experience and knowledge of the environment where the modules will be used prior to being used in production.</span></span> <span data-ttu-id="5ec81-258">Det är dags att söka efter eventuella ytterligare nyttolast i modulen som kan tas bort, till exempel dokumentation och exempel skript för att slutföra den här uppgiften.</span><span class="sxs-lookup"><span data-stu-id="5ec81-258">While completing this task it is a good time to check for any additional payload in the module that can be removed such as documentation and example scripts.</span></span> <span data-ttu-id="5ec81-259">Detta minskar nätverkets bandbredd per klient i sin första begäran när moduler ska laddas ned över nätverket från servern till klienten.</span><span class="sxs-lookup"><span data-stu-id="5ec81-259">This will reduce the network bandwidth per client in their first request, when modules will be downloaded over the network from server to client.</span></span>

<span data-ttu-id="5ec81-260">Varje modul måste paketeras i ett specifikt format, en ZIP-fil med namnet ModuleName_Version.zip som innehåller modulen nyttolasten.</span><span class="sxs-lookup"><span data-stu-id="5ec81-260">Each module must be packaged in a specific format, a ZIP file named ModuleName_Version.zip that contains the module payload.</span></span> <span data-ttu-id="5ec81-261">När filen kopieras till servern måste du skapa en fil kontrollsummor.</span><span class="sxs-lookup"><span data-stu-id="5ec81-261">After the file is copied to the server a checksum file must be created.</span></span> <span data-ttu-id="5ec81-262">När klienter ansluter till servern, används kontrollsumman som för att kontrollera innehållet i DSC-modulen inte har ändrats sedan den publicerades.</span><span class="sxs-lookup"><span data-stu-id="5ec81-262">When clients connect to the server, the checksum is used to verify the content of the DSC module has not changed since it was published.</span></span>

```powershell
New-DscCheckSum -ConfigurationPath .\ -OutPath .\
```

<span data-ttu-id="5ec81-263">Planera aktivitet</span><span class="sxs-lookup"><span data-stu-id="5ec81-263">Planning task</span></span>|
---|
<span data-ttu-id="5ec81-264">Om du planerar en test- eller labb-miljö är vilka scenarier för att verifiera?</span><span class="sxs-lookup"><span data-stu-id="5ec81-264">If you are planning a test or lab environment which scenarios are key to validate?</span></span>|
<span data-ttu-id="5ec81-265">Finns det offentligt tillgängliga modulerna som innehåller resurser för att omfatta allt du behöver eller behöver du skapa dina egna resurser?</span><span class="sxs-lookup"><span data-stu-id="5ec81-265">Are there publicly available modules that contain resources to cover everything you need or will you need to author your own resources?</span></span>|
<span data-ttu-id="5ec81-266">Kommer din miljö ha Internetåtkomst för att hämta offentlig moduler?</span><span class="sxs-lookup"><span data-stu-id="5ec81-266">Will your environment have Internet access to retrieve public modules?</span></span>|
<span data-ttu-id="5ec81-267">Vem är ansvarig för att granska DSC-moduler?</span><span class="sxs-lookup"><span data-stu-id="5ec81-267">Who will be responsible for reviewing DSC modules?</span></span>|
<span data-ttu-id="5ec81-268">Om du planerar en produktionsmiljö vad ska du använda som en lokal databas för lagring av DSC-moduler?</span><span class="sxs-lookup"><span data-stu-id="5ec81-268">If you are planning a production environment what will you use as a local repository for storing DSC modules?</span></span>|
<span data-ttu-id="5ec81-269">En central team accepterar DSC-moduler från programteam?</span><span class="sxs-lookup"><span data-stu-id="5ec81-269">Will a central team accept DSC modules from application teams?</span></span> <span data-ttu-id="5ec81-270">Vad är processen?</span><span class="sxs-lookup"><span data-stu-id="5ec81-270">What will the process be?</span></span>|
<span data-ttu-id="5ec81-271">Kan du automatisera paketering, kopiera och skapa en kontrollsumma för produktionsklara DSC-moduler på servern från käll-lagringsplatsen?</span><span class="sxs-lookup"><span data-stu-id="5ec81-271">Will you automate packaging, copying, and creating a checksum for production-ready DSC modules to the server, from your source repo?</span></span>|
<span data-ttu-id="5ec81-272">Ditt team ansvarar för att hantera plattformen automation?</span><span class="sxs-lookup"><span data-stu-id="5ec81-272">Will your team be responsible for managing the automation platform as well?</span></span>|

#### <a name="dsc-configurations"></a><span data-ttu-id="5ec81-273">DSC-konfigurationer</span><span class="sxs-lookup"><span data-stu-id="5ec81-273">DSC configurations</span></span>

<span data-ttu-id="5ec81-274">Syftet med en pull-server är att tillhandahålla en centraliserad mekanism för att distribuera DSC-konfigurationer för klientnoder.</span><span class="sxs-lookup"><span data-stu-id="5ec81-274">The purpose of a pull server is to provide a centralized mechanism for distributing DSC configurations to client nodes.</span></span> <span data-ttu-id="5ec81-275">Konfigurationerna som lagras på servern som MOF-dokument.</span><span class="sxs-lookup"><span data-stu-id="5ec81-275">The configurations are stored on the server as MOF documents.</span></span>
<span data-ttu-id="5ec81-276">Varje dokument kommer att namnges med ett unikt GUID.</span><span class="sxs-lookup"><span data-stu-id="5ec81-276">Each document will be named with a unique GUID.</span></span> <span data-ttu-id="5ec81-277">När klienterna är konfigurerade för att ansluta till en pull-server, ges de också GUID för konfigurationen hon måste begära.</span><span class="sxs-lookup"><span data-stu-id="5ec81-277">When clients are configured to connect with a pull server, they are also given the GUID for the configuration they should request.</span></span> <span data-ttu-id="5ec81-278">Systemet för att referera till konfigurationer av GUID garanterar globala unika och är flexibel så att du kan använda en konfiguration med granularitet per nod eller som en rollkonfiguration som sträcker sig över flera servrar som ska ha identiska konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="5ec81-278">This system of referencing configurations by GUID guarantees global uniqueness and is flexible such that a configuration can be applied with granularity per node, or as a role configuration that spans many servers that should have identical configurations.</span></span>

#### <a name="guids"></a><span data-ttu-id="5ec81-279">GUID</span><span class="sxs-lookup"><span data-stu-id="5ec81-279">GUIDs</span></span>

<span data-ttu-id="5ec81-280">Planera för konfiguration GUID är värt att ytterligare åtgärder när du funderar på en pull-serverdistribution.</span><span class="sxs-lookup"><span data-stu-id="5ec81-280">Planning for configuration GUIDs is worth additional attention when thinking through a pull server deployment.</span></span> <span data-ttu-id="5ec81-281">Det finns inga särskilda krav för hur du hanterar GUID och processen kan förväntas vara unikt för varje miljö.</span><span class="sxs-lookup"><span data-stu-id="5ec81-281">There is no specific requirement for how to handle GUIDs and the process is likely to be unique for each environment.</span></span> <span data-ttu-id="5ec81-282">Processen kan variera mellan enkla och komplexa: en centralt lagrade CSV-fil, en enkel SQLtabell, ett CMDB eller en komplex lösning kräver integrering med en annan lösning för verktyget eller programvara.</span><span class="sxs-lookup"><span data-stu-id="5ec81-282">The process can range from simple to complex: a centrally stored CSV file, a simple SQL table, a CMDB, or a complex solution requiring integration with another tool or software solution.</span></span> <span data-ttu-id="5ec81-283">Det finns två sätt:</span><span class="sxs-lookup"><span data-stu-id="5ec81-283">There are two general approaches:</span></span>

 - <span data-ttu-id="5ec81-284">**Tilldela GUID per server** – ger ett mått på försäkran om att varje konfiguration kontrolleras separat.</span><span class="sxs-lookup"><span data-stu-id="5ec81-284">**Assigning GUIDs per server** — Provides a measure of assurance that every server configuration is controlled individually.</span></span> <span data-ttu-id="5ec81-285">Detta ger en precision runt uppdateringar och kan fungera bra i miljöer med några servrar.</span><span class="sxs-lookup"><span data-stu-id="5ec81-285">This provides a level of precision around updates and can work well in environments with few servers.</span></span>
 - <span data-ttu-id="5ec81-286">**Tilldela GUID per serverrollen** – alla servrar som utför samma funktion, till exempel webbservrar, använda samma GUID för att referera till den nödvändiga konfigurationsdatan.</span><span class="sxs-lookup"><span data-stu-id="5ec81-286">**Assigning GUIDs per server role** — All servers that perform the same function, such as web servers, use the same GUID to reference the required configuration data.</span></span>  <span data-ttu-id="5ec81-287">Tänk på att om många servrar som delar samma GUID, alla skulle uppdateras samtidigt när konfigurationen ändras.</span><span class="sxs-lookup"><span data-stu-id="5ec81-287">Be aware that if many servers share the same GUID, all of them would be updated simultaneously when the configuration changes.</span></span>

<span data-ttu-id="5ec81-288">GUID är något som bör övervägas känsliga data eftersom den kan utnyttjas av en användare med skadliga åtgärder för att få intelligence om hur servrar distribuerats och konfigurerats i din miljö.</span><span class="sxs-lookup"><span data-stu-id="5ec81-288">The GUID is something that should be considered sensitive data because it could be leveraged by someone with malicious intent to gain intelligence about how servers are deployed and configured in your environment.</span></span> <span data-ttu-id="5ec81-289">Mer information finns i [på ett säkert sätt allokera GUID i PowerShell önskad tillstånd Pull-konfigurationsläge](http://blogs.msdn.com/b/powershell/archive/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode.aspx).</span><span class="sxs-lookup"><span data-stu-id="5ec81-289">For more information, see [Securely allocating GUIDs in PowerShell Desired State Configuration Pull Mode](http://blogs.msdn.com/b/powershell/archive/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode.aspx).</span></span>

<span data-ttu-id="5ec81-290">Planera aktivitet</span><span class="sxs-lookup"><span data-stu-id="5ec81-290">Planning task</span></span>|
---|
<span data-ttu-id="5ec81-291">Vem är ansvarig för att kopiera konfigurationer i till mappen pull server när de är klara?</span><span class="sxs-lookup"><span data-stu-id="5ec81-291">Who will be responsible for copying configurations in to the pull server folder when they are ready?</span></span>|
<span data-ttu-id="5ec81-292">Om konfigurationer som skapats av en grupp av program, vad processen är att lämnar dem?</span><span class="sxs-lookup"><span data-stu-id="5ec81-292">If Configurations are authored by an application team, what will the process be to hand them off?</span></span>|
<span data-ttu-id="5ec81-293">Använder du en lagringsplats för konfigurationer som de som skapats, mellan olika grupper?</span><span class="sxs-lookup"><span data-stu-id="5ec81-293">Will you leverage a repository to store configurations as they are being authored, across teams?</span></span>|
<span data-ttu-id="5ec81-294">Kan du automatisera processen för att kopiera konfigurationer till servern och skapa en kontrollsumma när de är klara?</span><span class="sxs-lookup"><span data-stu-id="5ec81-294">Will you automate the process of copying configurations to the server and creating a checksum when they are ready?</span></span>|
<span data-ttu-id="5ec81-295">Hur du mappar GUID till servrar eller roller och där det sparas?</span><span class="sxs-lookup"><span data-stu-id="5ec81-295">How will you map GUIDs to servers or roles, and where will this be stored?</span></span>|
<span data-ttu-id="5ec81-296">Vad ska du använda som en process för att konfigurera klientdatorer och hur kan den integreras med processen skapar och lagrar Configuration GUID?</span><span class="sxs-lookup"><span data-stu-id="5ec81-296">What will you use as a process to configure client machines, and how will it integrate with your process for creating and storing Configuration GUIDs?</span></span>|

## <a name="installation-guide"></a><span data-ttu-id="5ec81-297">Installationsguiden</span><span class="sxs-lookup"><span data-stu-id="5ec81-297">Installation Guide</span></span>

<span data-ttu-id="5ec81-298">*Skript som anges i det här dokumentet är stabil exempel. Alltid läsa igenom skript noggrant innan du kör dem i en produktionsmiljö.*</span><span class="sxs-lookup"><span data-stu-id="5ec81-298">*Scripts given in this document are stable examples. Always review scripts carefully before executing them in a production environment.*</span></span>

### <a name="prerequisites"></a><span data-ttu-id="5ec81-299">Förutsättningar</span><span class="sxs-lookup"><span data-stu-id="5ec81-299">Prerequisites</span></span>

<span data-ttu-id="5ec81-300">Använd följande kommando för att kontrollera version av PowerShell på servern.</span><span class="sxs-lookup"><span data-stu-id="5ec81-300">To verify the version of PowerShell on your server use the following command.</span></span>

```powershell
$PSVersionTable.PSVersion
```

<span data-ttu-id="5ec81-301">Om det är möjligt att uppgradera till den senaste versionen av Windows Management Framework.</span><span class="sxs-lookup"><span data-stu-id="5ec81-301">If possible, upgrade to the latest version of Windows Management Framework.</span></span>
<span data-ttu-id="5ec81-302">Sedan hämtar den `xPsDesiredStateConfiguration` modul med följande kommando.</span><span class="sxs-lookup"><span data-stu-id="5ec81-302">Next, download the `xPsDesiredStateConfiguration` module using the following command.</span></span>


```powershell
Install-Module xPSDesiredStateConfiguration
```

<span data-ttu-id="5ec81-303">Kommandot begär ditt godkännande innan du hämtar modulen.</span><span class="sxs-lookup"><span data-stu-id="5ec81-303">The command will ask for your approval before downloading the module.</span></span>

### <a name="installation-and-configuration-scripts"></a><span data-ttu-id="5ec81-304">Skript för installation och konfiguration</span><span class="sxs-lookup"><span data-stu-id="5ec81-304">Installation and configuration scripts</span></span>
-

<span data-ttu-id="5ec81-305">Det bästa sättet att distribuera en DSC pull-server är att använda ett DSC-konfigurationsskript.</span><span class="sxs-lookup"><span data-stu-id="5ec81-305">The best method to deploy a DSC pull server is to use a DSC configuration script.</span></span> <span data-ttu-id="5ec81-306">Det här dokumentet visas skript inklusive både grundläggande inställningar som konfigurerar bara DSC-webbtjänsten och avancerade inställningar som konfigurerar en Windows Server slutpunkt till slutpunkt inklusive DSC webbtjänst.</span><span class="sxs-lookup"><span data-stu-id="5ec81-306">This document will present scripts including both basic settings that would configure only the DSC web service and advanced settings that would configure a Windows Server end-to-end including DSC web service.</span></span>

<span data-ttu-id="5ec81-307">Obs: För närvarande den `xPSDesiredStateConfiguation` DSC-modulen kräver att servern ska vara EN-US lokalisering.</span><span class="sxs-lookup"><span data-stu-id="5ec81-307">Note:  Currently the `xPSDesiredStateConfiguation` DSC module requires the server to be EN-US locale.</span></span>

### <a name="basic-configuration-for-windows-server-2012"></a><span data-ttu-id="5ec81-308">Grundläggande konfiguration för Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="5ec81-308">Basic configuration for Windows Server 2012</span></span>
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

### <a name="advanced-configuration-for-windows-server-2012-r2"></a><span data-ttu-id="5ec81-309">Avancerad konfiguration för Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="5ec81-309">Advanced configuration for Windows Server 2012 R2</span></span>

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


### <a name="verify-pull-server-functionality"></a><span data-ttu-id="5ec81-310">Kontrollera pull-serverfunktioner</span><span class="sxs-lookup"><span data-stu-id="5ec81-310">Verify pull server functionality</span></span>

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

### <a name="configure-clients"></a><span data-ttu-id="5ec81-311">Konfigurera klienter</span><span class="sxs-lookup"><span data-stu-id="5ec81-311">Configure clients</span></span>

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


## <a name="additional-references-snippets-and-examples"></a><span data-ttu-id="5ec81-312">Ytterligare referenser, kodavsnitt och exempel</span><span class="sxs-lookup"><span data-stu-id="5ec81-312">Additional references, snippets, and examples</span></span>

<span data-ttu-id="5ec81-313">Det här exemplet visar hur du manuellt initiera en klientanslutning (kräver WMF5) för testning.</span><span class="sxs-lookup"><span data-stu-id="5ec81-313">This example shows how to manually initiate a client connection (requires WMF5) for testing.</span></span>

```powershell
Update-DSCConfiguration –Wait -Verbose
```

<span data-ttu-id="5ec81-314">Den [Lägg till DnsServerResourceRecordName](http://bit.ly/1G1H31L) cmdlet som används för att lägga till en typ CNAME-post till en DNS-zon.</span><span class="sxs-lookup"><span data-stu-id="5ec81-314">The [Add-DnsServerResourceRecordName](http://bit.ly/1G1H31L) cmdlet is used to add a type CNAME record to a DNS zone.</span></span>

<span data-ttu-id="5ec81-315">PowerShell-funktionen för att [skapa en kontrollsumma och publicera DSC MOF till SMB-Pull Server](http://bit.ly/1E46BhI) genererar automatiskt krävs kontrollsumma och kopierar sedan både MOF-konfigurationen och kontrollsumma filer till pull SMB-servern.</span><span class="sxs-lookup"><span data-stu-id="5ec81-315">The PowerShell Function to [Create a Checksum and Publish DSC MOF to SMB Pull Server](http://bit.ly/1E46BhI) automatically generates the required checksum, and then copies both the MOF configuration and checksum files to the SMB pull server.</span></span>

## <a name="appendix---understanding-odata-service-data-file-types"></a><span data-ttu-id="5ec81-316">Tillägg – förstå ODATA service data filtyper</span><span class="sxs-lookup"><span data-stu-id="5ec81-316">Appendix - Understanding ODATA service data file types</span></span>

<span data-ttu-id="5ec81-317">En fil lagras för att skapa information vid distribution av en pull-server som innehåller OData-webbtjänst.</span><span class="sxs-lookup"><span data-stu-id="5ec81-317">A data file is stored to create information during deployment of a pull server that includes the OData web service.</span></span> <span data-ttu-id="5ec81-318">Typ av fil beror på operativsystemet, enligt beskrivningen nedan.</span><span class="sxs-lookup"><span data-stu-id="5ec81-318">The type of file depends on the operating system, as described below.</span></span>

 - <span data-ttu-id="5ec81-319">**Windows Server 2012** filtypen kommer alltid att .mdb</span><span class="sxs-lookup"><span data-stu-id="5ec81-319">**Windows Server 2012** The file type will always be   .mdb</span></span>
 - <span data-ttu-id="5ec81-320">**Windows Server 2012 R2** filtypen kommer som standard edb om en .mdb har angetts i konfigurationen</span><span class="sxs-lookup"><span data-stu-id="5ec81-320">**Windows Server 2012 R2** The file type will default to .edb unless a .mdb is specified in the configuration</span></span>

<span data-ttu-id="5ec81-321">I den [avancerade exempelskriptet](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) för att installera en Pull-Server, det finns även ett exempel på hur du styr inställningarna för web.config-filen för att förhindra alla risken för fel som orsakats av filtyp automatiskt.</span><span class="sxs-lookup"><span data-stu-id="5ec81-321">In the [Advanced example script](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) for installing a Pull Server, you will also find an example of how to automatically control the web.config file settings to prevent any chance of error caused by file type.</span></span>