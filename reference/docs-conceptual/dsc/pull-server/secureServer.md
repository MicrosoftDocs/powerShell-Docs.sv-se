---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Metodtips för hämtningsservern
ms.openlocfilehash: 5cb47598b11f7884dddf1440cec21afeab49bebb
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417724"
---
# <a name="pull-server-best-practices"></a><span data-ttu-id="dce8d-103">Metodtips för hämtningsservern</span><span class="sxs-lookup"><span data-stu-id="dce8d-103">Pull server best practices</span></span>

<span data-ttu-id="dce8d-104">Gäller för: Windows PowerShell 4,0, Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="dce8d-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dce8d-105">Hämtnings servern (Windows Feature *DSC-tjänst*) är en komponent som stöds av Windows Server men det finns inga planer på att erbjuda nya funktioner eller funktioner.</span><span class="sxs-lookup"><span data-stu-id="dce8d-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="dce8d-106">Vi rekommenderar att du börjar överföra hanterade klienter till [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inklusive funktioner utöver hämtnings servern på Windows Server) eller någon av de community-lösningar som anges [här](/powershell/scripting/dsc/pull-server/pullserver#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="dce8d-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](/powershell/scripting/dsc/pull-server/pullserver#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="dce8d-107">Sammanfattning: det här dokumentet är avsett att omfatta process och utöknings barhet för att hjälpa tekniker som förbereder lösningen.</span><span class="sxs-lookup"><span data-stu-id="dce8d-107">Summary: This document is intended to include process and extensibility to assist engineers who are preparing for the solution.</span></span> <span data-ttu-id="dce8d-108">Informationen bör ge bästa praxis som identifieras av kunder och sedan verifieras av produkt teamet för att säkerställa att rekommendationerna är stabila och anses stabila.</span><span class="sxs-lookup"><span data-stu-id="dce8d-108">Details should provide best practices as identified by customers and then validated by the product team to ensure recommendations are future facing and considered stable.</span></span>

| |<span data-ttu-id="dce8d-109">Dokument information</span><span class="sxs-lookup"><span data-stu-id="dce8d-109">Doc Info</span></span>|
|:---|:---|
<span data-ttu-id="dce8d-110">Författare</span><span class="sxs-lookup"><span data-stu-id="dce8d-110">Author</span></span> | <span data-ttu-id="dce8d-111">Michael Greene</span><span class="sxs-lookup"><span data-stu-id="dce8d-111">Michael Greene</span></span>
<span data-ttu-id="dce8d-112">Granskare</span><span class="sxs-lookup"><span data-stu-id="dce8d-112">Reviewers</span></span> | <span data-ttu-id="dce8d-113">Ben Gelens, Ravikanth Chaganti, Aleksandar Nikolic</span><span class="sxs-lookup"><span data-stu-id="dce8d-113">Ben Gelens, Ravikanth Chaganti, Aleksandar Nikolic</span></span>
<span data-ttu-id="dce8d-114">Publicerad</span><span class="sxs-lookup"><span data-stu-id="dce8d-114">Published</span></span> | <span data-ttu-id="dce8d-115">April, 2015</span><span class="sxs-lookup"><span data-stu-id="dce8d-115">April, 2015</span></span>

## <a name="abstract"></a><span data-ttu-id="dce8d-116">Abstrakt</span><span class="sxs-lookup"><span data-stu-id="dce8d-116">Abstract</span></span>

<span data-ttu-id="dce8d-117">Det här dokumentet är utformat för att ge den officiella vägledningen för alla som planerar för en Windows PowerShell Desired State Configuration-hämtning av hämtnings servrar.</span><span class="sxs-lookup"><span data-stu-id="dce8d-117">This document is designed to provide official guidance for anyone planning for a Windows PowerShell Desired State Configuration pull server implementation.</span></span> <span data-ttu-id="dce8d-118">En pull-server är en enkel tjänst som bara tar några minuter att distribuera.</span><span class="sxs-lookup"><span data-stu-id="dce8d-118">A pull server is a simple service that should take only minutes to deploy.</span></span> <span data-ttu-id="dce8d-119">Även om det här dokumentet kommer att erbjuda teknisk instruktions vägledning som kan användas i en distribution, är värdet för det här dokumentet som en referens för bästa praxis och vad du behöver tänka på innan du distribuerar.</span><span class="sxs-lookup"><span data-stu-id="dce8d-119">Although this document will offer technical how-to guidance that can be used in a deployment, the value of this document is as a reference for best practices and what to think about before deploying.</span></span>
<span data-ttu-id="dce8d-120">Läsarna bör ha grundläggande kunskaper om DSC och de termer som används för att beskriva de komponenter som ingår i en DSC-distribution.</span><span class="sxs-lookup"><span data-stu-id="dce8d-120">Readers should have basic familiarity with DSC, and the terms used to describe the components that are included in a DSC deployment.</span></span> <span data-ttu-id="dce8d-121">Mer information finns i avsnittet [Översikt över Desired State Configuration i Windows PowerShell](/powershell/scripting/dsc/overview) .</span><span class="sxs-lookup"><span data-stu-id="dce8d-121">For more information, see the [Windows PowerShell Desired State Configuration Overview](/powershell/scripting/dsc/overview)  topic.</span></span>
<span data-ttu-id="dce8d-122">Eftersom DSC förväntas utvecklas på Cloud takt förväntas den underliggande tekniken, inklusive hämtnings servern, att utvecklas och introducera nya funktioner.</span><span class="sxs-lookup"><span data-stu-id="dce8d-122">As DSC is expected to evolve at cloud cadence, the underlying technology including pull server is also expected to evolve and to introduce new capabilities.</span></span> <span data-ttu-id="dce8d-123">Det här dokumentet innehåller en versions tabell i bilagan som innehåller referenser till tidigare versioner och referenser till kommande lösningar för att uppmuntra de vanliga designerna.</span><span class="sxs-lookup"><span data-stu-id="dce8d-123">This document includes a version table in the appendix that provides references to previous releases and references to future looking solutions to encourage forward-looking designs.</span></span>

<span data-ttu-id="dce8d-124">De två huvud avsnitten i det här dokumentet:</span><span class="sxs-lookup"><span data-stu-id="dce8d-124">The two major sections of this document:</span></span>

- <span data-ttu-id="dce8d-125">Konfigurations planering</span><span class="sxs-lookup"><span data-stu-id="dce8d-125">Configuration Planning</span></span>
- <span data-ttu-id="dce8d-126">Installations guide</span><span class="sxs-lookup"><span data-stu-id="dce8d-126">Installation Guide</span></span>

### <a name="versions-of-the-windows-management-framework"></a><span data-ttu-id="dce8d-127">Versioner av Windows Management Framework</span><span class="sxs-lookup"><span data-stu-id="dce8d-127">Versions of the Windows Management Framework</span></span>

<span data-ttu-id="dce8d-128">Informationen i det här dokumentet är avsedd att användas för Windows Management Framework 5,0.</span><span class="sxs-lookup"><span data-stu-id="dce8d-128">The information in this document is intended to apply to Windows Management Framework 5.0.</span></span> <span data-ttu-id="dce8d-129">Även om WMF 5,0 inte krävs för att distribuera och använda en hämtnings Server är version 5,0 fokus i det här dokumentet.</span><span class="sxs-lookup"><span data-stu-id="dce8d-129">While WMF 5.0 is not required for deploying and operating a pull server, version 5.0 is the focus of this document.</span></span>

### <a name="windows-powershell-desired-state-configuration"></a><span data-ttu-id="dce8d-130">Windows PowerShell Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="dce8d-130">Windows PowerShell Desired State Configuration</span></span>

<span data-ttu-id="dce8d-131">Önskad tillstånds konfiguration (DSC) är en hanterings plattform som gör det möjligt att distribuera och hantera konfigurations data med hjälp av en bransch-syntax med namnet Managed Object Format (MOF) som beskriver Common Information Model (CIM).</span><span class="sxs-lookup"><span data-stu-id="dce8d-131">Desired State Configuration (DSC) is a management platform that enables deploying and managing configuration data by using an industry syntax named the Managed Object Format (MOF) to describe the Common Information Model (CIM).</span></span> <span data-ttu-id="dce8d-132">Ett projekt med öppen källkod, öppen hanterings infrastruktur (OMI), finns för att utveckla dessa standarder på olika plattformar, inklusive Linux-och nätverks maskin varu operativ system.</span><span class="sxs-lookup"><span data-stu-id="dce8d-132">An open source project, Open Management Infrastructure (OMI), exists to further development of these standards across platforms including Linux and network hardware operating systems.</span></span> <span data-ttu-id="dce8d-133">Mer information finns i DMTF- [sidan länka till MOF-specifikationer](https://www.dmtf.org/standards/cim)och [OMI-dokument och-källa](https://collaboration.opengroup.org/omi/documents.php).</span><span class="sxs-lookup"><span data-stu-id="dce8d-133">For more information, see the [DMTF page linking to MOF specifications](https://www.dmtf.org/standards/cim), and [OMI Documents and Source](https://collaboration.opengroup.org/omi/documents.php).</span></span>

<span data-ttu-id="dce8d-134">Windows PowerShell innehåller en uppsättning språk tillägg för önskad tillstånds konfiguration som du kan använda för att skapa och hantera deklarativ konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="dce8d-134">Windows PowerShell provides a set of language extensions for Desired State Configuration that you can use to create and manage declarative configurations.</span></span>

### <a name="pull-server-role"></a><span data-ttu-id="dce8d-135">Hämta server roll</span><span class="sxs-lookup"><span data-stu-id="dce8d-135">Pull server role</span></span>

<span data-ttu-id="dce8d-136">En pull-server tillhandahåller en centraliserad tjänst för att lagra konfigurationer som kommer att vara tillgängliga för mål noder.</span><span class="sxs-lookup"><span data-stu-id="dce8d-136">A pull server provides a centralized service to store configurations that will be accessible to target nodes.</span></span>

<span data-ttu-id="dce8d-137">Hämtnings Server rollen kan distribueras antingen som en webb Server instans eller en SMB-filresurs.</span><span class="sxs-lookup"><span data-stu-id="dce8d-137">The pull server role can be deployed as either a Web Server instance or an SMB file share.</span></span> <span data-ttu-id="dce8d-138">Webb server funktionen innehåller ett OData-gränssnitt och kan även inkludera funktioner för målnoden för att rapportera om en bekräftelse eller ett haveri som har tillämpats.</span><span class="sxs-lookup"><span data-stu-id="dce8d-138">The web server capability includes an OData interface and can optionally include capabilities for target nodes to report back confirmation of success or failure as configurations are applied.</span></span> <span data-ttu-id="dce8d-139">Den här funktionen är användbar i miljöer där det finns ett stort antal mål noder.</span><span class="sxs-lookup"><span data-stu-id="dce8d-139">This functionality is useful in environments where there are a large number of target nodes.</span></span>
<span data-ttu-id="dce8d-140">När du har konfigurerat en målnod (kallas även en klient) för att peka på hämtnings servern, laddas de senaste konfigurations data och eventuella skript som krävs ned och tillämpas.</span><span class="sxs-lookup"><span data-stu-id="dce8d-140">After configuring a target node (also referred to as a client) to point to the pull server the latest configuration data and any required scripts are downloaded and applied.</span></span> <span data-ttu-id="dce8d-141">Detta kan ske vid en enstaka distribution eller som ett jobb som körs på nytt, vilket även gör hämtnings servern till en viktig till gång för att hantera förändringar i skala.</span><span class="sxs-lookup"><span data-stu-id="dce8d-141">This can happen as a one-time deployment or as a re-occurring job which also makes the pull server an important asset for managing change at scale.</span></span> <span data-ttu-id="dce8d-142">Mer information finns i [Windows PowerShell Desired State Configuration pull-servrar](/powershell/scripting/dsc/pullServer/pullserver) och</span><span class="sxs-lookup"><span data-stu-id="dce8d-142">For more information, see [Windows PowerShell Desired State Configuration Pull Servers](/powershell/scripting/dsc/pullServer/pullserver) and</span></span>

<span data-ttu-id="dce8d-143">[Konfigurations lägen för push och hämtning](/powershell/scripting/dsc/pullServer/pullserver).</span><span class="sxs-lookup"><span data-stu-id="dce8d-143">[Push and Pull Configuration Modes](/powershell/scripting/dsc/pullServer/pullserver).</span></span>

## <a name="configuration-planning"></a><span data-ttu-id="dce8d-144">Konfigurations planering</span><span class="sxs-lookup"><span data-stu-id="dce8d-144">Configuration planning</span></span>

<span data-ttu-id="dce8d-145">För distribution av företags program vara finns det information som kan samlas in i förväg för att planera för rätt arkitektur och förberedas för de steg som krävs för att slutföra distributionen.</span><span class="sxs-lookup"><span data-stu-id="dce8d-145">For any enterprise software deployment there is information that can be collected in advance to help plan for the correct architecture and to be prepared for the steps required to complete the deployment.</span></span> <span data-ttu-id="dce8d-146">I följande avsnitt finns information om hur du förbereder och de organisatoriska anslutningar som sannolikt kommer att behöva inträffa i förväg.</span><span class="sxs-lookup"><span data-stu-id="dce8d-146">The following sections provide information regarding how to prepare and the organizational connections that will likely need to happen in advance.</span></span>

### <a name="software-requirements"></a><span data-ttu-id="dce8d-147">Programvarukrav</span><span class="sxs-lookup"><span data-stu-id="dce8d-147">Software requirements</span></span>

<span data-ttu-id="dce8d-148">För att kunna distribuera en pull-server krävs DSC-funktionen i Windows Server.</span><span class="sxs-lookup"><span data-stu-id="dce8d-148">Deployment of a pull server requires the DSC Service feature of Windows Server.</span></span> <span data-ttu-id="dce8d-149">Den här funktionen introducerades i Windows Server 2012 och har uppdaterats genom pågående versioner av Windows Management Framework (WMF).</span><span class="sxs-lookup"><span data-stu-id="dce8d-149">This feature was introduced in Windows Server 2012, and has been updated through ongoing releases of Windows Management Framework (WMF).</span></span>

### <a name="software-downloads"></a><span data-ttu-id="dce8d-150">Hämtning av program vara</span><span class="sxs-lookup"><span data-stu-id="dce8d-150">Software downloads</span></span>

<span data-ttu-id="dce8d-151">Förutom att installera det senaste innehållet från Windows Update, finns det två hämtnings bara filer som anses vara bästa praxis för att distribuera en DSC-pull-server: den senaste versionen av Windows Management Framework och en DSC-modul för att automatisera hämtning av Server etablering.</span><span class="sxs-lookup"><span data-stu-id="dce8d-151">In addition to installing the latest content from Windows Update, there are two downloads considered best practice to deploy a DSC pull server: The latest version of Windows Management Framework, and a DSC module to automate pull server provisioning.</span></span>

### <a name="wmf"></a><span data-ttu-id="dce8d-152">WMF</span><span class="sxs-lookup"><span data-stu-id="dce8d-152">WMF</span></span>

<span data-ttu-id="dce8d-153">Windows Server 2012 R2 innehåller en funktion som kallas DSC-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="dce8d-153">Windows Server 2012 R2 includes a feature named the DSC Service.</span></span> <span data-ttu-id="dce8d-154">Funktionen DSC-tjänst tillhandahåller hämtnings Server funktioner, inklusive binärfiler som stöder OData-slutpunkten.</span><span class="sxs-lookup"><span data-stu-id="dce8d-154">The DSC Service feature provides the pull server functionality, including the binaries that support the OData endpoint.</span></span>
<span data-ttu-id="dce8d-155">WMF ingår i Windows Server och uppdateras på en smidig takt mellan Windows Server-versioner.</span><span class="sxs-lookup"><span data-stu-id="dce8d-155">WMF is included in Windows Server and is updated on an agile cadence between Windows Server releases.</span></span> <span data-ttu-id="dce8d-156">[Nya versioner av WMF 5,0](https://www.microsoft.com/en-us/download/details.aspx?id=54616) kan innehålla uppdateringar av DSC-tjänstens funktion.</span><span class="sxs-lookup"><span data-stu-id="dce8d-156">[New versions of WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=54616)  can include updates to the DSC Service feature.</span></span> <span data-ttu-id="dce8d-157">Av den anledningen är det bäst att ladda ned den senaste versionen av WMF och granska viktig information för att ta reda på om versionen innehåller en uppdatering av DSC-tjänstens funktion.</span><span class="sxs-lookup"><span data-stu-id="dce8d-157">For this reason, it is a best practice to download the latest release of WMF and to review the release notes to determine if the release includes an update to the DSC service feature.</span></span> <span data-ttu-id="dce8d-158">Du bör också läsa avsnittet i viktig information som anger om design status för en uppdatering eller ett scenario visas som stabil eller experimentell.</span><span class="sxs-lookup"><span data-stu-id="dce8d-158">You should also review the section of the release notes that indicates whether the design status for an update or scenario is listed as stable or experimental.</span></span>
<span data-ttu-id="dce8d-159">För att möjliggöra en smidig lanserings cykel kan enskilda funktioner deklareras som stabila, vilket innebär att funktionen är redo att användas i en produktions miljö även om WMF lanseras i för hands versionen.</span><span class="sxs-lookup"><span data-stu-id="dce8d-159">To allow for an agile release cycle, individual features can be declared stable, which indicates the feature is ready to be used in a production environment even while WMF is released in preview.</span></span>
<span data-ttu-id="dce8d-160">Andra funktioner som tidigare har uppdaterats av WMF-versioner (mer information finns i versions kommentarerna för WMF):</span><span class="sxs-lookup"><span data-stu-id="dce8d-160">Other features that have historically been updated by WMF releases (see the WMF Release Notes for further detail):</span></span>

- <span data-ttu-id="dce8d-161">Windows PowerShell Windows PowerShell-integrerat skript</span><span class="sxs-lookup"><span data-stu-id="dce8d-161">Windows PowerShell Windows PowerShell Integrated Scripting</span></span>
- <span data-ttu-id="dce8d-162">Environment (ISE) Windows PowerShell-webbtjänster (hantering OData</span><span class="sxs-lookup"><span data-stu-id="dce8d-162">Environment (ISE) Windows PowerShell Web Services (Management OData</span></span>
- <span data-ttu-id="dce8d-163">IIS-tillägg) Windows PowerShell Desired State Configuration (DSC)</span><span class="sxs-lookup"><span data-stu-id="dce8d-163">IIS Extension)  Windows PowerShell Desired State Configuration (DSC)</span></span>
- <span data-ttu-id="dce8d-164">Windows Remote Management (WinRM) Windows Management Instrumentation (WMI)</span><span class="sxs-lookup"><span data-stu-id="dce8d-164">Windows Remote Management (WinRM) Windows Management Instrumentation (WMI)</span></span>

### <a name="dsc-resource"></a><span data-ttu-id="dce8d-165">DSC-resurs</span><span class="sxs-lookup"><span data-stu-id="dce8d-165">DSC resource</span></span>

<span data-ttu-id="dce8d-166">En pull-Server-distribution kan för enklas genom att tillhandahålla tjänsten med hjälp av ett DSC-konfigurations skript.</span><span class="sxs-lookup"><span data-stu-id="dce8d-166">A pull server deployment can be simplified by provisioning the service using a DSC configuration script.</span></span> <span data-ttu-id="dce8d-167">Det här dokumentet innehåller konfigurations skript som kan användas för att distribuera en produktions klar Server-nod.</span><span class="sxs-lookup"><span data-stu-id="dce8d-167">This document includes configuration scripts that can be used to deploy a production ready server node.</span></span> <span data-ttu-id="dce8d-168">Om du vill använda konfigurations skripten krävs en DSC-modul som inte ingår i Windows Server.</span><span class="sxs-lookup"><span data-stu-id="dce8d-168">To use the configuration scripts, a DSC module is required that is not included in Windows Server.</span></span> <span data-ttu-id="dce8d-169">Namnet på den obligatoriska modulen är **xPSDesiredStateConfiguration**, som innehåller DSC- **xDscWebService**.</span><span class="sxs-lookup"><span data-stu-id="dce8d-169">The required module name is **xPSDesiredStateConfiguration**, which includes the DSC resource **xDscWebService**.</span></span> <span data-ttu-id="dce8d-170">XPSDesiredStateConfiguration-modulen kan hämtas [här](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d).</span><span class="sxs-lookup"><span data-stu-id="dce8d-170">The xPSDesiredStateConfiguration module can be downloaded [here](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d).</span></span>

<span data-ttu-id="dce8d-171">Använd `Install-Module`-cmdleten från **PowerShellGet** -modulen.</span><span class="sxs-lookup"><span data-stu-id="dce8d-171">Use the `Install-Module` cmdlet from the **PowerShellGet** module.</span></span>

```powershell
Install-Module xPSDesiredStateConfiguration
```

<span data-ttu-id="dce8d-172">Modulen **PowerShellGet** hämtar modulen till:</span><span class="sxs-lookup"><span data-stu-id="dce8d-172">The **PowerShellGet** module will download the module to:</span></span>

`C:\Program Files\Windows PowerShell\Modules`

<span data-ttu-id="dce8d-173">Planerings uppgift</span><span class="sxs-lookup"><span data-stu-id="dce8d-173">Planning task</span></span>|
---|
<span data-ttu-id="dce8d-174">Har du åtkomst till installationsfilerna för Windows Server 2012 R2?</span><span class="sxs-lookup"><span data-stu-id="dce8d-174">Do you have access to the installation files for Windows Server 2012 R2?</span></span>|
<span data-ttu-id="dce8d-175">Kommer distributions miljön att ha Internet åtkomst för att hämta WMF och modulen från Onlinegalleri?</span><span class="sxs-lookup"><span data-stu-id="dce8d-175">Will the deployment environment have Internet access to download WMF and the module from the online gallery?</span></span>|
<span data-ttu-id="dce8d-176">Hur installerar du de senaste säkerhets uppdateringarna efter att du har installerat operativ systemet?</span><span class="sxs-lookup"><span data-stu-id="dce8d-176">How will you install the latest security updates after installing the operating system?</span></span>|
<span data-ttu-id="dce8d-177">Kommer miljön att ha Internet åtkomst för att hämta uppdateringar eller kommer att ha en lokal Windows Server Update Services (WSUS)-Server?</span><span class="sxs-lookup"><span data-stu-id="dce8d-177">Will the environment have Internet access to obtain updates, or will it have a local Windows Server Update Services (WSUS) server?</span></span>|
<span data-ttu-id="dce8d-178">Har du åtkomst till Windows Server-installationsfiler som redan innehåller uppdateringar via offline-inmatning?</span><span class="sxs-lookup"><span data-stu-id="dce8d-178">Do you have access to Windows Server installation files that already include updates through offline injection?</span></span>|

### <a name="hardware-requirements"></a><span data-ttu-id="dce8d-179">Maskinvarukrav</span><span class="sxs-lookup"><span data-stu-id="dce8d-179">Hardware requirements</span></span>

<span data-ttu-id="dce8d-180">Hämtnings Server distributioner stöds på både fysiska och virtuella servrar.</span><span class="sxs-lookup"><span data-stu-id="dce8d-180">Pull server deployments are supported on both physical and virtual servers.</span></span> <span data-ttu-id="dce8d-181">Storleks kraven för hämtnings servern överensstämmer med kraven för Windows Server 2012 R2.</span><span class="sxs-lookup"><span data-stu-id="dce8d-181">The sizing requirements for pull server align with the requirements for Windows Server 2012 R2.</span></span>

<span data-ttu-id="dce8d-182">CPU: 1,4 GHz 64-bitars processor minne: 512 MB disk utrymme: 32 GB nätverk: Gigabit Ethernet-kort</span><span class="sxs-lookup"><span data-stu-id="dce8d-182">CPU: 1.4 GHz 64-bit processor Memory: 512 MB Disk Space: 32 GB Network: Gigabit Ethernet Adapter</span></span>

<span data-ttu-id="dce8d-183">Planerings uppgift</span><span class="sxs-lookup"><span data-stu-id="dce8d-183">Planning task</span></span>|
---|
<span data-ttu-id="dce8d-184">Kommer du att distribuera på en fysisk maskin vara eller en Virtualization-plattform?</span><span class="sxs-lookup"><span data-stu-id="dce8d-184">Will you deploy on physical hardware or on a virtualization platform?</span></span>|
<span data-ttu-id="dce8d-185">Vad är processen för att begära en ny server för mål miljön?</span><span class="sxs-lookup"><span data-stu-id="dce8d-185">What is the process to request a new server for your target environment?</span></span>|
<span data-ttu-id="dce8d-186">Vilken är den genomsnittliga leverans tiden för en server att bli tillgänglig?</span><span class="sxs-lookup"><span data-stu-id="dce8d-186">What is the average turnaround time for a server to become available?</span></span>|
<span data-ttu-id="dce8d-187">Vilken storleks server kommer du att begära?</span><span class="sxs-lookup"><span data-stu-id="dce8d-187">What size server will you request?</span></span>|

### <a name="accounts"></a><span data-ttu-id="dce8d-188">Konton</span><span class="sxs-lookup"><span data-stu-id="dce8d-188">Accounts</span></span>

<span data-ttu-id="dce8d-189">Det finns inga tjänst konto krav för att distribuera en pull-serverinstans.</span><span class="sxs-lookup"><span data-stu-id="dce8d-189">There are no service account requirements to deploy a pull server instance.</span></span>
<span data-ttu-id="dce8d-190">Det finns dock scenarier där webbplatsen kan köras i kontexten för ett lokalt användar konto.</span><span class="sxs-lookup"><span data-stu-id="dce8d-190">However, there are scenarios where the website could run in the context of a local user account.</span></span>
<span data-ttu-id="dce8d-191">Om det till exempel finns behov av att komma åt en lagrings resurs för webbplats innehåll och antingen Windows-servern eller enheten som är värd för lagrings resursen inte är domänansluten.</span><span class="sxs-lookup"><span data-stu-id="dce8d-191">For example, if there is a need to access a storage share for website content and either the Windows Server or the device hosting the storage share are not domain joined.</span></span>

### <a name="dns-records"></a><span data-ttu-id="dce8d-192">DNS-poster</span><span class="sxs-lookup"><span data-stu-id="dce8d-192">DNS records</span></span>

<span data-ttu-id="dce8d-193">Du behöver ett server namn som du kan använda när du konfigurerar klienter för att arbeta med en pull-server-miljö.</span><span class="sxs-lookup"><span data-stu-id="dce8d-193">You will need a server name to use when configuring clients to work with a pull server environment.</span></span>
<span data-ttu-id="dce8d-194">I test miljöer används vanligt vis serverns värdnamn, eller så kan IP-adressen för servern användas om DNS-namnmatchning inte är tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="dce8d-194">In test environments, typically the server hostname is used, or the IP address for the server can be used if DNS name resolution is not available.</span></span>
<span data-ttu-id="dce8d-195">I produktions miljöer eller i en labb miljö som är avsedd att representera en produktions distribution är det bästa sättet att skapa en DNS CNAME-post.</span><span class="sxs-lookup"><span data-stu-id="dce8d-195">In production environments or in a lab environment that is intended to represent a production deployment, the best practice is to create a DNS CNAME record.</span></span>

<span data-ttu-id="dce8d-196">Med en DNS CNAME kan du skapa ett alias för att referera till värd posten (A).</span><span class="sxs-lookup"><span data-stu-id="dce8d-196">A DNS CNAME allows you to create an alias to refer to your host (A) record.</span></span>
<span data-ttu-id="dce8d-197">Avsikten med den extra namn posten är att öka flexibiliteten om en ändring krävs i framtiden.</span><span class="sxs-lookup"><span data-stu-id="dce8d-197">The intent of the additional name record is to increase flexibility should a change be required in the future.</span></span>
<span data-ttu-id="dce8d-198">En CNAME kan hjälpa till att isolera klient konfigurationen så att ändringar i Server miljön, till exempel att ersätta en hämtnings Server eller lägga till ytterligare pull-servrar, kräver ingen motsvarande ändring i klient konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="dce8d-198">A CNAME can help to isolate the client configuration so that changes to the server environment, such as replacing a pull server or adding additional pull servers, will not require a corresponding change to the client configuration.</span></span>

<span data-ttu-id="dce8d-199">Behåll lösnings arkitekturen i åtanke när du väljer ett namn för DNS-posten.</span><span class="sxs-lookup"><span data-stu-id="dce8d-199">When choosing a name for the DNS record, keep the solution architecture in mind.</span></span>
<span data-ttu-id="dce8d-200">Om du använder belastnings utjämning måste certifikatet som används för att skydda trafik över HTTPS dela samma namn som DNS-posten.</span><span class="sxs-lookup"><span data-stu-id="dce8d-200">If using load balancing, the certificate used to secure traffic over HTTPS will need to share the same name as the DNS record.</span></span>

<span data-ttu-id="dce8d-201">Scenario</span><span class="sxs-lookup"><span data-stu-id="dce8d-201">Scenario</span></span> |<span data-ttu-id="dce8d-202">Bästa praxis</span><span class="sxs-lookup"><span data-stu-id="dce8d-202">Best Practice</span></span>
:---|:---
<span data-ttu-id="dce8d-203">Testmiljö</span><span class="sxs-lookup"><span data-stu-id="dce8d-203">Test Environment</span></span> |<span data-ttu-id="dce8d-204">Återskapa den planerade produktions miljön, om möjligt.</span><span class="sxs-lookup"><span data-stu-id="dce8d-204">Reproduce the planned production environment, if possible.</span></span> <span data-ttu-id="dce8d-205">Ett server namn är lämpligt för enkla konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="dce8d-205">A server hostname is suitable for simple configurations.</span></span> <span data-ttu-id="dce8d-206">Om DNS inte är tillgängligt kan en IP-adress användas i stället för ett värdnamn.</span><span class="sxs-lookup"><span data-stu-id="dce8d-206">If DNS is not available, an IP address may be used in lieu of a hostname.</span></span>|
<span data-ttu-id="dce8d-207">Distribution av en nod</span><span class="sxs-lookup"><span data-stu-id="dce8d-207">Single Node Deployment</span></span> |<span data-ttu-id="dce8d-208">Skapa en DNS CNAME-post som pekar på serverns värdnamn.</span><span class="sxs-lookup"><span data-stu-id="dce8d-208">Create a DNS CNAME record that points to the server hostname.</span></span>|

<span data-ttu-id="dce8d-209">Mer information finns i [Konfigurera DNS Round Robin i Windows Server](/previous-versions/windows/it-pro/windows-server-2003/cc787484(v=ws.10)).</span><span class="sxs-lookup"><span data-stu-id="dce8d-209">For more information, see [Configuring DNS Round Robin in Windows Server](/previous-versions/windows/it-pro/windows-server-2003/cc787484(v=ws.10)).</span></span>

<span data-ttu-id="dce8d-210">Planerings uppgift</span><span class="sxs-lookup"><span data-stu-id="dce8d-210">Planning task</span></span>|
---|
<span data-ttu-id="dce8d-211">Vet du vem du ska kontakta så att DNS-poster skapas och ändras?</span><span class="sxs-lookup"><span data-stu-id="dce8d-211">Do you know who to contact to have DNS records created and changed?</span></span>|
<span data-ttu-id="dce8d-212">Vad är genomsnittet för en begäran om en DNS-post?</span><span class="sxs-lookup"><span data-stu-id="dce8d-212">What is the average turnaround for a request for a DNS record?</span></span>|
<span data-ttu-id="dce8d-213">Behöver du begära statiska värdnamn (A) för servrar?</span><span class="sxs-lookup"><span data-stu-id="dce8d-213">Do you need to request static Hostname (A) records for servers?</span></span>|
<span data-ttu-id="dce8d-214">Vad kommer du att begära som CNAME?</span><span class="sxs-lookup"><span data-stu-id="dce8d-214">What will you request as a CNAME?</span></span>|
<span data-ttu-id="dce8d-215">Om det behövs, vilken typ av belastnings Utjämnings lösning kommer du att använda?</span><span class="sxs-lookup"><span data-stu-id="dce8d-215">If needed, what type of Load Balancing solution will you utilize?</span></span> <span data-ttu-id="dce8d-216">(se avsnittet med rubriken belastnings utjämning för mer information)</span><span class="sxs-lookup"><span data-stu-id="dce8d-216">(see section titled Load Balancing for details)</span></span>|

### <a name="public-key-infrastructure"></a><span data-ttu-id="dce8d-217">Infrastruktur för offentliga nycklar</span><span class="sxs-lookup"><span data-stu-id="dce8d-217">Public Key Infrastructure</span></span>

<span data-ttu-id="dce8d-218">De flesta organisationer i dag kräver att nätverks trafik, särskilt trafik som inkluderar sådana känsliga data som servrar konfigureras, måste verifieras och/eller krypteras under överföringen.</span><span class="sxs-lookup"><span data-stu-id="dce8d-218">Most organizations today require that network traffic, especially traffic that includes such sensitive data as how servers are configured, must be validated and/or encrypted during transit.</span></span>
<span data-ttu-id="dce8d-219">Även om det är möjligt att distribuera en pull-server med HTTP som underlättar klient begär anden i klartext, är det en bra idé att skydda trafiken med HTTPS.</span><span class="sxs-lookup"><span data-stu-id="dce8d-219">While it is possible to deploy a pull server using HTTP which facilitates client requests in clear text, it is a best practice to secure traffic using HTTPS.</span></span> <span data-ttu-id="dce8d-220">Tjänsten kan konfigureras att använda HTTPS med en uppsättning parametrar i DSC- **xPSDesiredStateConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="dce8d-220">The service can be configured to use HTTPS using a set of parameters in the DSC resource **xPSDesiredStateConfiguration**.</span></span>

<span data-ttu-id="dce8d-221">Certifikat kraven för säker HTTPS-trafik för hämtnings servern skiljer sig inte från att skydda andra HTTPS-webbplatser.</span><span class="sxs-lookup"><span data-stu-id="dce8d-221">The certificate requirements to secure HTTPS traffic for pull server are not different than securing any other HTTPS web site.</span></span> <span data-ttu-id="dce8d-222">**Webb server** mal len i en Windows Server Certificate Services uppfyller de funktioner som krävs.</span><span class="sxs-lookup"><span data-stu-id="dce8d-222">The **Web Server** template in a Windows Server Certificate Services satisfies the required capabilities.</span></span>

<span data-ttu-id="dce8d-223">Planerings uppgift</span><span class="sxs-lookup"><span data-stu-id="dce8d-223">Planning task</span></span>|
---|
<span data-ttu-id="dce8d-224">Om du inte automatiserar certifikat begär Anden måste du kontakta för att begära ett certifikat?</span><span class="sxs-lookup"><span data-stu-id="dce8d-224">If certificate requests are not automated, who will you need to contact to requests a certificate?</span></span>|
<span data-ttu-id="dce8d-225">Vilken är den genomsnittliga leveransen för begäran?</span><span class="sxs-lookup"><span data-stu-id="dce8d-225">What is the average turnaround for the request?</span></span>|
<span data-ttu-id="dce8d-226">Hur överförs certifikat filen till dig?</span><span class="sxs-lookup"><span data-stu-id="dce8d-226">How will the certificate file be transferred to you?</span></span>|
<span data-ttu-id="dce8d-227">Hur överförs certifikatets privata nyckel till dig?</span><span class="sxs-lookup"><span data-stu-id="dce8d-227">How will the certificate private key be transferred to you?</span></span>|
<span data-ttu-id="dce8d-228">Hur länge är standard förfallo tiden?</span><span class="sxs-lookup"><span data-stu-id="dce8d-228">How long is the default expiration time?</span></span>|
<span data-ttu-id="dce8d-229">Har du kvittat dig på ett DNS-namn för pull Server-miljön, som du kan använda för certifikat namnet?</span><span class="sxs-lookup"><span data-stu-id="dce8d-229">Have you settled on a DNS name for the pull server environment, that you can use for the certificate name?</span></span>|

### <a name="choosing-an-architecture"></a><span data-ttu-id="dce8d-230">Välja en arkitektur</span><span class="sxs-lookup"><span data-stu-id="dce8d-230">Choosing an architecture</span></span>

<span data-ttu-id="dce8d-231">En hämtnings Server kan distribueras med antingen en webb tjänst som finns på IIS eller en SMB-filresurs.</span><span class="sxs-lookup"><span data-stu-id="dce8d-231">A pull server can be deployed using either a web service hosted on IIS, or an SMB file share.</span></span> <span data-ttu-id="dce8d-232">I de flesta fall ger alternativet för webb tjänsten större flexibilitet.</span><span class="sxs-lookup"><span data-stu-id="dce8d-232">In most situations, the web service option will provide greater flexibility.</span></span> <span data-ttu-id="dce8d-233">Det är inte ovanligt att HTTPS-trafik passerar nätverks gränserna, medan SMB-trafik ofta filtreras eller blockeras mellan nätverk.</span><span class="sxs-lookup"><span data-stu-id="dce8d-233">It is not uncommon for HTTPS traffic to traverse network boundaries, whereas SMB traffic is often filtered or blocked between networks.</span></span> <span data-ttu-id="dce8d-234">Webb tjänsten erbjuder också alternativet att inkludera en inställnings Server eller Web repor ting Manager (båda ämnen som ska åtgärdas i en framtida version av det här dokumentet) som ger en mekanism för klienter att rapportera status tillbaka till en server för centraliserad synlighet.</span><span class="sxs-lookup"><span data-stu-id="dce8d-234">The web service also offers the option to include a Conformance Server or Web Reporting Manager (both topics to be addressed in a future version of this document) that provide a mechanism for clients to report status back to a server for centralized visibility.</span></span>
<span data-ttu-id="dce8d-235">SMB innehåller ett alternativ för miljöer där en princip anger att en webb server inte ska användas och andra miljö krav som gör en webb server roll olämplig.</span><span class="sxs-lookup"><span data-stu-id="dce8d-235">SMB provides an option for environments where policy dictates that a web server should not be utilized, and for other environmental requirements that make a web server role undesirable.</span></span>
<span data-ttu-id="dce8d-236">I båda fallen måste du komma ihåg att utvärdera kraven för signering och kryptering av trafik.</span><span class="sxs-lookup"><span data-stu-id="dce8d-236">In either case, remember to evaluate the requirements for signing and encrypting traffic.</span></span> <span data-ttu-id="dce8d-237">HTTPS-, SMB-signering och IPSEC-principer är alla alternativ som är värda att beakta.</span><span class="sxs-lookup"><span data-stu-id="dce8d-237">HTTPS, SMB signing, and IPSEC policies are all options worth considering.</span></span>

#### <a name="load-balancing"></a><span data-ttu-id="dce8d-238">Belastningsutjämning</span><span class="sxs-lookup"><span data-stu-id="dce8d-238">Load balancing</span></span>

<span data-ttu-id="dce8d-239">Klienter som interagerar med webb tjänsten gör en begäran om information som returneras i ett enda svar.</span><span class="sxs-lookup"><span data-stu-id="dce8d-239">Clients interacting with the web service make a request for information that is returned in a single response.</span></span> <span data-ttu-id="dce8d-240">Inga sekventiella begär Anden krävs, så det är inte nödvändigt för belastnings Utjämnings plattformen att säkerställa att sessioner upprätthålls på en enskild server vid varje tidpunkt.</span><span class="sxs-lookup"><span data-stu-id="dce8d-240">No sequential requests are required, so it is not necessary for the load balancing platform to ensure sessions are maintained on a single server at any point in time.</span></span>

<span data-ttu-id="dce8d-241">Planerings uppgift</span><span class="sxs-lookup"><span data-stu-id="dce8d-241">Planning task</span></span>|
---|
<span data-ttu-id="dce8d-242">Vilken lösning ska användas för belastnings Utjämnings trafik mellan servrar?</span><span class="sxs-lookup"><span data-stu-id="dce8d-242">What solution will be used for load balancing traffic across servers?</span></span>|
<span data-ttu-id="dce8d-243">Om du använder en maskinvarubaserad belastningsutjämnare, som tar en förfrågan om att lägga till en ny konfiguration till enheten?</span><span class="sxs-lookup"><span data-stu-id="dce8d-243">If using a hardware load balancer, who will take a request to add a new configuration to the device?</span></span>|
<span data-ttu-id="dce8d-244">Vad är genomsnittet för en begäran om att konfigurera en ny belastningsutjämnad webb tjänst?</span><span class="sxs-lookup"><span data-stu-id="dce8d-244">What is the average turnaround for a request to configure a new load balanced web service?</span></span>|
<span data-ttu-id="dce8d-245">Vilken information kommer att krävas för begäran?</span><span class="sxs-lookup"><span data-stu-id="dce8d-245">What information will be required for the request?</span></span>|
<span data-ttu-id="dce8d-246">Behöver du begära ytterligare en IP-adress eller teamet som ansvarar för belastnings Utjämnings referensen?</span><span class="sxs-lookup"><span data-stu-id="dce8d-246">Will you need to request an additional IP or will the team responsible for load balancing handle that?</span></span>|
<span data-ttu-id="dce8d-247">Har du de DNS-poster som behövs och kommer att krävas av teamet som ansvarar för att konfigurera belastnings Utjämnings lösningen?</span><span class="sxs-lookup"><span data-stu-id="dce8d-247">Do you have the DNS records needed, and will this be required by the team responsible for configuring the load balancing solution?</span></span>|
<span data-ttu-id="dce8d-248">Kräver belastnings Utjämnings lösningen att PKI hanteras av enheten eller kan den belastningsutjämna HTTPS-trafik så länge det inte finns några krav för sessionen?</span><span class="sxs-lookup"><span data-stu-id="dce8d-248">Does the load balancing solution require that PKI be handled by the device or can it load balance HTTPS traffic as long as there are no session requirements?</span></span>|

### <a name="staging-configurations-and-modules-on-the-pull-server"></a><span data-ttu-id="dce8d-249">Mellanlagring av konfigurationer och moduler på hämtnings servern</span><span class="sxs-lookup"><span data-stu-id="dce8d-249">Staging configurations and modules on the pull server</span></span>

<span data-ttu-id="dce8d-250">Som en del av konfigurations planeringen måste du tänka på vilka DSC-moduler och konfigurationer som ska hanteras av hämtnings servern.</span><span class="sxs-lookup"><span data-stu-id="dce8d-250">As part of configuration planning, you will need to think about which DSC modules and configurations will be hosted by the pull server.</span></span> <span data-ttu-id="dce8d-251">För konfigurations planering är det viktigt att du har en grundläggande förståelse för hur du förbereder och distribuerar innehåll till en pull-server.</span><span class="sxs-lookup"><span data-stu-id="dce8d-251">For the purpose of configuration planning it is important to have a basic understanding of how to prepare and deploy content to a pull server.</span></span>

<span data-ttu-id="dce8d-252">I framtiden kommer det här avsnittet att expanderas och ingå i en funktions guide för DSC-pull-server.</span><span class="sxs-lookup"><span data-stu-id="dce8d-252">In the future, this section will be expanded and included in an Operations Guide for DSC Pull Server.</span></span>  <span data-ttu-id="dce8d-253">Guiden diskuterar dag till dags process för att hantera moduler och konfigurationer över tid med automatisering.</span><span class="sxs-lookup"><span data-stu-id="dce8d-253">The guide will discuss the day to day process for managing modules and configurations over time with automation.</span></span>

#### <a name="dsc-modules"></a><span data-ttu-id="dce8d-254">DSC-moduler</span><span class="sxs-lookup"><span data-stu-id="dce8d-254">DSC modules</span></span>

<span data-ttu-id="dce8d-255">Klienter som begär en konfiguration kommer att behöva de DSC-moduler som krävs.</span><span class="sxs-lookup"><span data-stu-id="dce8d-255">Clients that request a configuration will need the required DSC modules.</span></span> <span data-ttu-id="dce8d-256">En funktion i pull-servern är att automatisera distributionen på begäran av DSC-moduler till klienter.</span><span class="sxs-lookup"><span data-stu-id="dce8d-256">A functionality of the pull server is to automate distribution on demand of DSC modules to clients.</span></span> <span data-ttu-id="dce8d-257">Om du distribuerar en hämtnings Server för första gången, kanske som labb eller koncept bevis, kommer du troligen att vara beroende av DSC-moduler som är tillgängliga från offentliga databaser, till exempel PowerShell-galleriet eller PowerShell.org GitHub-lagringsplatsen för DSC-moduler .</span><span class="sxs-lookup"><span data-stu-id="dce8d-257">If you are deploying a pull server for the first time, perhaps as a lab or proof of concept, you are likely going to depend on DSC modules that are available from public repositories such as the PowerShell Gallery or the PowerShell.org GitHub repositories for DSC modules.</span></span>

<span data-ttu-id="dce8d-258">Det är viktigt att komma ihåg att även för betrodda onlinekällor som PowerShell-galleriet, alla moduler som hämtas från ett offentligt lager bör granskas av någon med PowerShell-upplevelse och kunskap om miljön där modulerna kommer att används innan de används i produktionen.</span><span class="sxs-lookup"><span data-stu-id="dce8d-258">It is critical to remember that even for trusted online sources such as the PowerShell Gallery, any module that is downloaded from a public repository should be reviewed by someone with PowerShell experience and knowledge of the environment where the modules will be used prior to being used in production.</span></span> <span data-ttu-id="dce8d-259">När du slutför den här uppgiften är det en lämplig tid att söka efter ytterligare en nytto Last i modulen som kan tas bort, till exempel dokumentation och exempel skript.</span><span class="sxs-lookup"><span data-stu-id="dce8d-259">While completing this task it is a good time to check for any additional payload in the module that can be removed such as documentation and example scripts.</span></span> <span data-ttu-id="dce8d-260">Detta minskar nätverks bandbredden per klient i den första begäran, när moduler ska laddas ned över nätverket från server till klient.</span><span class="sxs-lookup"><span data-stu-id="dce8d-260">This will reduce the network bandwidth per client in their first request, when modules will be downloaded over the network from server to client.</span></span>

<span data-ttu-id="dce8d-261">Varje modul måste paketeras i ett särskilt format, en ZIP-fil med namnet ModuleName_Version. zip som innehåller modulens nytto Last.</span><span class="sxs-lookup"><span data-stu-id="dce8d-261">Each module must be packaged in a specific format, a ZIP file named ModuleName_Version.zip that contains the module payload.</span></span> <span data-ttu-id="dce8d-262">När filen har kopierats till servern måste en kontroll Summa fil skapas.</span><span class="sxs-lookup"><span data-stu-id="dce8d-262">After the file is copied to the server a checksum file must be created.</span></span> <span data-ttu-id="dce8d-263">När klienter ansluter till servern används kontroll summan för att kontrol lera att innehållet i DSC-modulen inte har ändrats sedan den publicerades.</span><span class="sxs-lookup"><span data-stu-id="dce8d-263">When clients connect to the server, the checksum is used to verify the content of the DSC module has not changed since it was published.</span></span>

```powershell
New-DscChecksum -ConfigurationPath .\ -OutPath .\
```

<span data-ttu-id="dce8d-264">Planerings uppgift</span><span class="sxs-lookup"><span data-stu-id="dce8d-264">Planning task</span></span>|
---|
<span data-ttu-id="dce8d-265">Om du planerar en test-eller labb miljö vars scenarier är nyckel att verifiera?</span><span class="sxs-lookup"><span data-stu-id="dce8d-265">If you are planning a test or lab environment which scenarios are key to validate?</span></span>|
<span data-ttu-id="dce8d-266">Finns det offentligt tillgängliga moduler som innehåller resurser för att omfatta allt du behöver eller behöver du redigera dina egna resurser?</span><span class="sxs-lookup"><span data-stu-id="dce8d-266">Are there publicly available modules that contain resources to cover everything you need or will you need to author your own resources?</span></span>|
<span data-ttu-id="dce8d-267">Kommer din miljö att ha Internet åtkomst för att hämta offentliga moduler?</span><span class="sxs-lookup"><span data-stu-id="dce8d-267">Will your environment have Internet access to retrieve public modules?</span></span>|
<span data-ttu-id="dce8d-268">Vem kommer att ansvara för att granska DSC-moduler?</span><span class="sxs-lookup"><span data-stu-id="dce8d-268">Who will be responsible for reviewing DSC modules?</span></span>|
<span data-ttu-id="dce8d-269">Om du planerar en produktions miljö vad kommer du att använda som lokal lagrings plats för att lagra DSC-moduler?</span><span class="sxs-lookup"><span data-stu-id="dce8d-269">If you are planning a production environment what will you use as a local repository for storing DSC modules?</span></span>|
<span data-ttu-id="dce8d-270">Accepterar Central team DSC-moduler från program team?</span><span class="sxs-lookup"><span data-stu-id="dce8d-270">Will a central team accept DSC modules from application teams?</span></span> <span data-ttu-id="dce8d-271">Vad kommer processen att vara?</span><span class="sxs-lookup"><span data-stu-id="dce8d-271">What will the process be?</span></span>|
<span data-ttu-id="dce8d-272">Kommer du att automatisera paketering, kopiering och skapande av en kontroll summa för produktions klara DSC-moduler till servern från din lagrings platsen?</span><span class="sxs-lookup"><span data-stu-id="dce8d-272">Will you automate packaging, copying, and creating a checksum for production-ready DSC modules to the server, from your source repo?</span></span>|
<span data-ttu-id="dce8d-273">Är ditt team ansvarigt för att hantera Automation-plattformen också?</span><span class="sxs-lookup"><span data-stu-id="dce8d-273">Will your team be responsible for managing the automation platform as well?</span></span>|

#### <a name="dsc-configurations"></a><span data-ttu-id="dce8d-274">DSC-konfigurationer</span><span class="sxs-lookup"><span data-stu-id="dce8d-274">DSC configurations</span></span>

<span data-ttu-id="dce8d-275">Syftet med en pull-server är att tillhandahålla en central mekanism för att distribuera DSC-konfigurationer till klient-noder.</span><span class="sxs-lookup"><span data-stu-id="dce8d-275">The purpose of a pull server is to provide a centralized mechanism for distributing DSC configurations to client nodes.</span></span> <span data-ttu-id="dce8d-276">Konfigurationerna lagras på servern som MOF-dokument.</span><span class="sxs-lookup"><span data-stu-id="dce8d-276">The configurations are stored on the server as MOF documents.</span></span>
<span data-ttu-id="dce8d-277">Varje dokument får ett unikt **GUID**-namn.</span><span class="sxs-lookup"><span data-stu-id="dce8d-277">Each document will be named with a unique **Guid**.</span></span> <span data-ttu-id="dce8d-278">När klienterna är konfigurerade för att ansluta till en pull-server får de också **GUID** för den konfiguration de bör begära.</span><span class="sxs-lookup"><span data-stu-id="dce8d-278">When clients are configured to connect with a pull server, they are also given the **Guid** for the configuration they should request.</span></span> <span data-ttu-id="dce8d-279">Det här systemet med referenser till konfigurationer efter **GUID** garanterar global unikhet och är flexibelt så att en konfiguration kan tillämpas med granularitet per nod, eller som en roll konfiguration som omfattar många servrar som ska ha identiska konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="dce8d-279">This system of referencing configurations by **Guid** guarantees global uniqueness and is flexible such that a configuration can be applied with granularity per node, or as a role configuration that spans many servers that should have identical configurations.</span></span>

#### <a name="guids"></a><span data-ttu-id="dce8d-280">GUID</span><span class="sxs-lookup"><span data-stu-id="dce8d-280">Guids</span></span>

<span data-ttu-id="dce8d-281">Planering av konfigurations- **GUID** är värda ytterligare uppmärksamhet vid användning av en pull-Server-distribution.</span><span class="sxs-lookup"><span data-stu-id="dce8d-281">Planning for configuration **Guids** is worth additional attention when thinking through a pull server deployment.</span></span> <span data-ttu-id="dce8d-282">Det finns inget särskilt krav för att hantera **GUID** och processen är förmodligen unik för varje miljö.</span><span class="sxs-lookup"><span data-stu-id="dce8d-282">There is no specific requirement for how to handle **Guids** and the process is likely to be unique for each environment.</span></span> <span data-ttu-id="dce8d-283">Processen kan vara mellan enkla och komplexa: en centralt lagrad CSV-fil, en enkel SQL-tabell, en CMDB eller en komplex lösning som kräver integrering med ett annat verktyg eller en program varu lösning.</span><span class="sxs-lookup"><span data-stu-id="dce8d-283">The process can range from simple to complex: a centrally stored CSV file, a simple SQL table, a CMDB, or a complex solution requiring integration with another tool or software solution.</span></span> <span data-ttu-id="dce8d-284">Det finns två allmänna metoder:</span><span class="sxs-lookup"><span data-stu-id="dce8d-284">There are two general approaches:</span></span>

- <span data-ttu-id="dce8d-285">**Tilldelning av GUID per server** – ger ett mått på att varje server konfiguration kontrol leras individuellt.</span><span class="sxs-lookup"><span data-stu-id="dce8d-285">**Assigning Guids per server** — Provides a measure of assurance that every server configuration is controlled individually.</span></span> <span data-ttu-id="dce8d-286">Detta ger en nivå av precision kring uppdateringar och kan fungera bra i miljöer med några få servrar.</span><span class="sxs-lookup"><span data-stu-id="dce8d-286">This provides a level of precision around updates and can work well in environments with few servers.</span></span>
- <span data-ttu-id="dce8d-287">**Tilldela GUID per server roll** – alla servrar som utför samma funktion, till exempel webb servrar, använder samma GUID för att referera till nödvändiga konfigurations data.</span><span class="sxs-lookup"><span data-stu-id="dce8d-287">**Assigning Guids per server role** — All servers that perform the same function, such as web servers, use the same GUID to reference the required configuration data.</span></span>  <span data-ttu-id="dce8d-288">Tänk på att om många servrar delar samma GUID, så uppdateras alla samtidigt när konfigurationen ändras.</span><span class="sxs-lookup"><span data-stu-id="dce8d-288">Be aware that if many servers share the same GUID, all of them would be updated simultaneously when the configuration changes.</span></span>

  <span data-ttu-id="dce8d-289">GUID är något som ska betraktas som känsliga data eftersom det kan utnyttjas av någon med skadlig avsikt för att få information om hur servrar distribueras och konfigureras i din miljö.</span><span class="sxs-lookup"><span data-stu-id="dce8d-289">The GUID is something that should be considered sensitive data because it could be leveraged by someone with malicious intent to gain intelligence about how servers are deployed and configured in your environment.</span></span> <span data-ttu-id="dce8d-290">Mer information finns i avsnittet om att [allokera GUID i PowerShell Desired State Configuration pull-läge](https://blogs.msdn.microsoft.com/powershell/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode/).</span><span class="sxs-lookup"><span data-stu-id="dce8d-290">For more information, see [Securely allocating Guids in PowerShell Desired State Configuration Pull Mode](https://blogs.msdn.microsoft.com/powershell/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode/).</span></span>

<span data-ttu-id="dce8d-291">Planerings uppgift</span><span class="sxs-lookup"><span data-stu-id="dce8d-291">Planning task</span></span>|
---|
<span data-ttu-id="dce8d-292">Vem kommer att ansvara för att kopiera konfigurationer till pull-servermappen när de är klara?</span><span class="sxs-lookup"><span data-stu-id="dce8d-292">Who will be responsible for copying configurations in to the pull server folder when they are ready?</span></span>|
<span data-ttu-id="dce8d-293">Vad kommer processen att bli av om konfigurationer har skapats av ett program team?</span><span class="sxs-lookup"><span data-stu-id="dce8d-293">If Configurations are authored by an application team, what will the process be to hand them off?</span></span>|
<span data-ttu-id="dce8d-294">Kommer du att använda en lagrings plats för att lagra konfigurationer när de skapas, i flera team?</span><span class="sxs-lookup"><span data-stu-id="dce8d-294">Will you leverage a repository to store configurations as they are being authored, across teams?</span></span>|
<span data-ttu-id="dce8d-295">Automatiseras processen med att kopiera konfigurationer till servern och skapa en kontroll Summa när de är klara?</span><span class="sxs-lookup"><span data-stu-id="dce8d-295">Will you automate the process of copying configurations to the server and creating a checksum when they are ready?</span></span>|
<span data-ttu-id="dce8d-296">Hur mappar du GUID till servrar eller roller och var kommer det att lagras?</span><span class="sxs-lookup"><span data-stu-id="dce8d-296">How will you map Guids to servers or roles, and where will this be stored?</span></span>|
<span data-ttu-id="dce8d-297">Vad ska du använda som en process för att konfigurera klient datorer och hur kommer det att integreras med processen för att skapa och lagra konfigurations-GUID?</span><span class="sxs-lookup"><span data-stu-id="dce8d-297">What will you use as a process to configure client machines, and how will it integrate with your process for creating and storing Configuration Guids?</span></span>|

## <a name="installation-guide"></a><span data-ttu-id="dce8d-298">Installations guide</span><span class="sxs-lookup"><span data-stu-id="dce8d-298">Installation Guide</span></span>

<span data-ttu-id="dce8d-299">*Skript som anges i det här dokumentet är stabila exempel. Granska alltid skript noggrant innan du kör dem i en produktions miljö.*</span><span class="sxs-lookup"><span data-stu-id="dce8d-299">*Scripts given in this document are stable examples. Always review scripts carefully before executing them in a production environment.*</span></span>

### <a name="prerequisites"></a><span data-ttu-id="dce8d-300">Förutsättningar</span><span class="sxs-lookup"><span data-stu-id="dce8d-300">Prerequisites</span></span>

<span data-ttu-id="dce8d-301">Använd följande kommando för att kontrol lera versionen av PowerShell på servern.</span><span class="sxs-lookup"><span data-stu-id="dce8d-301">To verify the version of PowerShell on your server use the following command.</span></span>

```powershell
$PSVersionTable.PSVersion
```

<span data-ttu-id="dce8d-302">Uppgradera om möjligt till den senaste versionen av Windows Management Framework.</span><span class="sxs-lookup"><span data-stu-id="dce8d-302">If possible, upgrade to the latest version of Windows Management Framework.</span></span>
<span data-ttu-id="dce8d-303">Hämta sedan `xPsDesiredStateConfiguration`-modulen med hjälp av följande kommando.</span><span class="sxs-lookup"><span data-stu-id="dce8d-303">Next, download the `xPsDesiredStateConfiguration` module using the following command.</span></span>

```powershell
Install-Module xPSDesiredStateConfiguration
```

<span data-ttu-id="dce8d-304">Kommandot ber om ditt godkännande innan du laddar ned modulen.</span><span class="sxs-lookup"><span data-stu-id="dce8d-304">The command will ask for your approval before downloading the module.</span></span>

### <a name="installation-and-configuration-scripts"></a><span data-ttu-id="dce8d-305">Installations-och konfigurations skript</span><span class="sxs-lookup"><span data-stu-id="dce8d-305">Installation and configuration scripts</span></span>

<span data-ttu-id="dce8d-306">Den bästa metoden för att distribuera en DSC-pull-server är att använda ett DSC-konfigurations skript.</span><span class="sxs-lookup"><span data-stu-id="dce8d-306">The best method to deploy a DSC pull server is to use a DSC configuration script.</span></span> <span data-ttu-id="dce8d-307">Det här dokumentet visar skript, inklusive både grundläggande inställningar som endast konfigurerar DSC-webbtjänsten och avancerade inställningar som konfigurerar en Windows Server från slut punkt till slut punkt inklusive DSC-webbtjänst.</span><span class="sxs-lookup"><span data-stu-id="dce8d-307">This document will present scripts including both basic settings that would configure only the DSC web service and advanced settings that would configure a Windows Server end-to-end including DSC web service.</span></span>

<span data-ttu-id="dce8d-308">OBS! den `xPSDesiredStateConfiguration` DSC-modulen kräver att servern är EN-US-språkvariant.</span><span class="sxs-lookup"><span data-stu-id="dce8d-308">Note:  Currently the `xPSDesiredStateConfiguration` DSC module requires the server to be EN-US locale.</span></span>

### <a name="basic-configuration-for-windows-server-2012"></a><span data-ttu-id="dce8d-309">Grundläggande konfiguration för Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="dce8d-309">Basic configuration for Windows Server 2012</span></span>

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

### <a name="advanced-configuration-for-windows-server-2012-r2"></a><span data-ttu-id="dce8d-310">Avancerad konfiguration för Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="dce8d-310">Advanced configuration for Windows Server 2012 R2</span></span>

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

### <a name="verify-pull-server-functionality"></a><span data-ttu-id="dce8d-311">Verifiera hämtning av Server funktioner</span><span class="sxs-lookup"><span data-stu-id="dce8d-311">Verify pull server functionality</span></span>

```powershell
# This function is meant to simplify a check against a DSC pull server. If you do not use the default service URL, you will need to adjust accordingly.
function Verify-DSCPullServer ($fqdn) {
    ([xml](Invoke-WebRequest "https://$($fqdn):8080/psdscpullserver.svc" | % Content)).service.workspace.collection.href
}

Verify-DSCPullServer 'INSERT SERVER FQDN'
```

```output
Expected Result:
Action
Module
StatusReport
Node
```

### <a name="configure-clients"></a><span data-ttu-id="dce8d-312">Konfigurera klienter</span><span class="sxs-lookup"><span data-stu-id="dce8d-312">Configure clients</span></span>

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

## <a name="additional-references-snippets-and-examples"></a><span data-ttu-id="dce8d-313">Ytterligare referenser, kodfragment och exempel</span><span class="sxs-lookup"><span data-stu-id="dce8d-313">Additional references, snippets, and examples</span></span>

<span data-ttu-id="dce8d-314">Det här exemplet visar hur du manuellt initierar en klient anslutning (kräver WMF5) för testning.</span><span class="sxs-lookup"><span data-stu-id="dce8d-314">This example shows how to manually initiate a client connection (requires WMF5) for testing.</span></span>

```powershell
Update-DscConfiguration –Wait -Verbose
```

<span data-ttu-id="dce8d-315">Cmdlet: en [Add-DnsServerResourceRecordName](http://bit.ly/1G1H31L) används för att lägga till en typ CNAME-post i en DNS-zon.</span><span class="sxs-lookup"><span data-stu-id="dce8d-315">The [Add-DnsServerResourceRecordName](http://bit.ly/1G1H31L) cmdlet is used to add a type CNAME record to a DNS zone.</span></span>

<span data-ttu-id="dce8d-316">PowerShell-funktionen för att [skapa en kontroll summa och publicera DSC MOF till SMB pull server](https://gallery.technet.microsoft.com/scriptcenter/PowerShell-Function-to-3bc4b7f0) genererar automatiskt den nödvändiga kontroll summan och kopierar sedan både MOF-konfigurationen och kontroll summornas filer till SMB-pull-servern.</span><span class="sxs-lookup"><span data-stu-id="dce8d-316">The PowerShell Function to [Create a Checksum and Publish DSC MOF to SMB Pull Server](https://gallery.technet.microsoft.com/scriptcenter/PowerShell-Function-to-3bc4b7f0) automatically generates the required checksum, and then copies both the MOF configuration and checksum files to the SMB pull server.</span></span>

## <a name="appendix---understanding-odata-service-data-file-types"></a><span data-ttu-id="dce8d-317">Tillägg – förstå ODATA-tjänstens data fil typer</span><span class="sxs-lookup"><span data-stu-id="dce8d-317">Appendix - Understanding ODATA service data file types</span></span>

<span data-ttu-id="dce8d-318">En datafil lagras för att skapa information under distributionen av en pull-server som inkluderar OData-webbtjänsten.</span><span class="sxs-lookup"><span data-stu-id="dce8d-318">A data file is stored to create information during deployment of a pull server that includes the OData web service.</span></span> <span data-ttu-id="dce8d-319">Vilken typ av fil som används beror på operativ systemet, enligt beskrivningen nedan.</span><span class="sxs-lookup"><span data-stu-id="dce8d-319">The type of file depends on the operating system, as described below.</span></span>

- <span data-ttu-id="dce8d-320">**Windows Server 2012** Filtypen är alltid. mdb</span><span class="sxs-lookup"><span data-stu-id="dce8d-320">**Windows Server 2012** The file type will always be   .mdb</span></span>
- <span data-ttu-id="dce8d-321">**Windows Server 2012 R2** Filtypen används som standard till. edb om inte en. mdb anges i konfigurationen</span><span class="sxs-lookup"><span data-stu-id="dce8d-321">**Windows Server 2012 R2** The file type will default to .edb unless a .mdb is specified in the configuration</span></span>

<span data-ttu-id="dce8d-322">I det [avancerade exempel skriptet](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) för att installera en hämtnings server hittar du också ett exempel på hur du automatiskt kontrollerar inställningarna för Web. config-filen för att förhindra eventuella fel som orsakas av filtypen.</span><span class="sxs-lookup"><span data-stu-id="dce8d-322">In the [Advanced example script](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) for installing a Pull Server, you will also find an example of how to automatically control the web.config file settings to prevent any chance of error caused by file type.</span></span>
