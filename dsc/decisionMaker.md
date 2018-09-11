---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Desired State Configuration-översikt för beslutsfattare
ms.openlocfilehash: 7c36aa5fadeab8bcb381f316288d102b5ce402e2
ms.sourcegitcommit: ac20e0faaa37142e9c6e4507a21df2f4a3fdbece
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/10/2018
ms.locfileid: "44339845"
---
# <a name="desired-state-configuration-overview-for-decision-makers"></a><span data-ttu-id="99770-103">Desired State Configuration-översikt för beslutsfattare</span><span class="sxs-lookup"><span data-stu-id="99770-103">Desired State Configuration Overview for Decision Makers</span></span>

<span data-ttu-id="99770-104">Det här dokumentet beskriver fördelarna med hjälp av Windows PowerShell Desired State Configuration (DSC).</span><span class="sxs-lookup"><span data-stu-id="99770-104">This document describes the business benefits of using Windows PowerShell Desired State Configuration (DSC).</span></span> <span data-ttu-id="99770-105">Det är inte en teknisk vägledning.</span><span class="sxs-lookup"><span data-stu-id="99770-105">It is not a technical guide.</span></span>

## <a name="what-is-desired-state-configuration"></a><span data-ttu-id="99770-106">Vad är Desired State Configuration?</span><span class="sxs-lookup"><span data-stu-id="99770-106">What Is Desired State Configuration?</span></span>

<span data-ttu-id="99770-107">PowerShell Desired State Configuration är en plattform för hantering av konfiguration som är inbyggda i Windows som baseras på öppna standarder.</span><span class="sxs-lookup"><span data-stu-id="99770-107">PowerShell Desired State Configuration is a configuration management platform built into Windows that is based on open standards.</span></span> <span data-ttu-id="99770-108">DSC är tillräckligt flexibelt för att fungera på ett tillförlitligt och konsekvent i varje steg i livscykeln för distribution (utveckling, testning, före produktion, produktion), samt vid skala ut.</span><span class="sxs-lookup"><span data-stu-id="99770-108">DSC is flexible enough to function reliably and consistently in each stage of the deployment lifecycle (development, test, pre-production, production), as well as during scale-out.</span></span>

<span data-ttu-id="99770-109">DSC fokuserad på [konfigurationer](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="99770-109">DSC centers around [configurations](configurations.md).</span></span>
<span data-ttu-id="99770-110">En konfiguration är ett enkelt att läsa dokument som beskriver en miljö som består av datorer (”noder”) med specifika egenskaper.</span><span class="sxs-lookup"><span data-stu-id="99770-110">A configuration is an easy-to-read document that describes an environment made up of computers ("nodes") with specific characteristics.</span></span>
<span data-ttu-id="99770-111">Följande egenskaper kan vara lika enkelt som att se till att en specifik Windows-funktion är aktiverat eller så komplext som distribution av SharePoint.</span><span class="sxs-lookup"><span data-stu-id="99770-111">These characteristics can be as simple as ensuring a specific Windows feature is enabled or as complex as deploying SharePoint.</span></span>

<span data-ttu-id="99770-112">DSC har också övervakning och rapportering inbyggda.</span><span class="sxs-lookup"><span data-stu-id="99770-112">DSC also has monitoring and reporting built in.</span></span>
<span data-ttu-id="99770-113">Om ett system inte längre kompatibel, DSC utlösa en avisering och vidta åtgärder för att korrigera systemet.</span><span class="sxs-lookup"><span data-stu-id="99770-113">If a system is no longer compliant, DSC can raise an alert and act to correct the system.</span></span>

## <a name="benefits-of-using-desired-state-configuration"></a><span data-ttu-id="99770-114">Fördelarna med att använda Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="99770-114">Benefits of Using Desired State Configuration</span></span>

<span data-ttu-id="99770-115">Konfigurationer som är utformade för att vara enkelt läsa, lagras och uppdaterade.</span><span class="sxs-lookup"><span data-stu-id="99770-115">Configurations are designed to be easily read, stored, and updated.</span></span>
<span data-ttu-id="99770-116">Konfigurationer deklarera målenheter tillstånd ska vara i, istället för att skriva instruktioner för hur du placerar dem i det aktuella tillståndet.</span><span class="sxs-lookup"><span data-stu-id="99770-116">Configurations declare the state target devices should be in, instead of writing instructions for how to put them in that state.</span></span>
<span data-ttu-id="99770-117">På så sätt blir det mycket billigare att lära dig, använda, implementera och underhålla konfiguration via DSC.</span><span class="sxs-lookup"><span data-stu-id="99770-117">This makes it much less costly to learn, adopt, implement, and maintain configuration through DSC.</span></span>

<span data-ttu-id="99770-118">Skapar konfigurationer innebär att komplexa distributionsstegen avbildas som en ”enda sanningskällan” på en enda plats.</span><span class="sxs-lookup"><span data-stu-id="99770-118">Creating configurations means that complex deployment steps are captured as a "single source of truth" in a single location.</span></span>
<span data-ttu-id="99770-119">Upprepade distributioner av en specifik uppsättning datorer blir mycket mindre felbenägna.</span><span class="sxs-lookup"><span data-stu-id="99770-119">This makes repeated deployments of a specific set of machines much less error-prone.</span></span>
<span data-ttu-id="99770-120">I sin tur gör distributioner snabbare och mer tillförlitlig som gör det möjligt för kort tid på komplexa distributioner.</span><span class="sxs-lookup"><span data-stu-id="99770-120">In turn, making deployments faster and more reliable which enables a quick turnaround on complex deployments.</span></span>

<span data-ttu-id="99770-121">Det går också att dela via konfigurationer i [PowerShell-galleriet](https://powershellgallery.com) vilket innebär att vanliga scenarier och bästa praxis kanske redan finns för det arbete som behöver göras.</span><span class="sxs-lookup"><span data-stu-id="99770-121">Configurations are also shareable via the [PowerShell Gallery](https://powershellgallery.com) meaning common scenarios and best practices might already exist for the work that needs to be done.</span></span>


## <a name="desired-state-configuration-and-devops"></a><span data-ttu-id="99770-122">Desired State Configuration och DevOps</span><span class="sxs-lookup"><span data-stu-id="99770-122">Desired State Configuration and DevOps</span></span>

<span data-ttu-id="99770-123">DSC utformades med [DevOps](http://blogs.technet.com/b/ashleymcglone/archive/2015/11/20/devops-for-n00bs-ie-windows-people.aspx) i åtanke, en kombination av personer, processer och verktyg som gör det lätt att implementera och iteration fokuserar på att leverera värde till slutanvändare om interna eller externa.</span><span class="sxs-lookup"><span data-stu-id="99770-123">DSC was designed with [DevOps](http://blogs.technet.com/b/ashleymcglone/archive/2015/11/20/devops-for-n00bs-ie-windows-people.aspx) in mind, a combination of people, processes, and tools that allow for rapid deployment and iteration focused on delivering value to end users whether internal or external.</span></span>
<span data-ttu-id="99770-124">Med en enda konfiguration definiera en miljö innebär att utvecklare kan koda sina krav till en konfiguration, kontrollera att konfigurationen till källkontroll och åtgärden utvecklingsteam kan enkelt distribuera kod utan att behöva gå igenom felbenägna manuella processer.</span><span class="sxs-lookup"><span data-stu-id="99770-124">Having a single configuration define an environment means that developers can encode their requirements into a configuration, check that configuration into source control, and operation teams can easily deploy code without having to go through error-prone manual processes.</span></span>

<span data-ttu-id="99770-125">Konfigurationer är också [datadrivna](configData.md), vilket gör det lättare för ops att identifiera och ändra miljöer utan inblandning av utvecklare.</span><span class="sxs-lookup"><span data-stu-id="99770-125">Configurations are also [data-driven](configData.md), which makes it easier for ops to identify and change environments without developer intervention.</span></span>

## <a name="desired-state-configuration-on--and-off-premises"></a><span data-ttu-id="99770-126">Desired State Configuration på - och annan plats</span><span class="sxs-lookup"><span data-stu-id="99770-126">Desired State Configuration On- and Off-Premises</span></span>

<span data-ttu-id="99770-127">DSC kan användas för att hantera både lokala och av lokala distributioner.</span><span class="sxs-lookup"><span data-stu-id="99770-127">DSC can be used to manage both on-premise and off-premise deployments.</span></span>
<span data-ttu-id="99770-128">Lokala lösningar, DSC har en [hämtningsservern](pullServer.md) som kan användas för att centralisera hanteringen av datorer och rapportera om deras status.</span><span class="sxs-lookup"><span data-stu-id="99770-128">For on-premise solutions, DSC has a [pull server](pullServer.md) that can be used to centralize management of machines and report on their status.</span></span>
<span data-ttu-id="99770-129">Molnlösningar kan DSC användas var Windows kommer att kunna användas.</span><span class="sxs-lookup"><span data-stu-id="99770-129">For cloud solutions, DSC is usable wherever Windows is usable.</span></span>
<span data-ttu-id="99770-130">Det finns även specifika erbjudanden från Azure bygger på Desired State Configuration, till exempel [Azure Automation](https://azure.microsoft.com/en-us/documentation/services/automation/), vilket centraliserar rapportering av DSC.</span><span class="sxs-lookup"><span data-stu-id="99770-130">There are also specific offerings from Azure built on Desired State Configuration, such as [Azure Automation](https://azure.microsoft.com/en-us/documentation/services/automation/), which centralizes reporting of DSC.</span></span>

## <a name="dsc-and-compatibility"></a><span data-ttu-id="99770-131">DSC och kompatibilitet</span><span class="sxs-lookup"><span data-stu-id="99770-131">DSC and Compatibility</span></span>

<span data-ttu-id="99770-132">Även om DSC introducerades i Windows Server 2012 R2, är den tillgänglig för äldre operativsystem via paketet Windows Management Framework (WMF).</span><span class="sxs-lookup"><span data-stu-id="99770-132">Although DSC was introduced in Windows Server 2012 R2, it is available for down-level operating systems via the Windows Management Framework (WMF) package.</span></span>
<span data-ttu-id="99770-133">Mer information om WMF kan hittas på den [PowerShell startsidan](/powershell/).</span><span class="sxs-lookup"><span data-stu-id="99770-133">More information about the WMF can be found on the [PowerShell homepage](/powershell/).</span></span>

<span data-ttu-id="99770-134">DSC kan också användas för att hantera Linux.</span><span class="sxs-lookup"><span data-stu-id="99770-134">DSC can also be used to manage Linux.</span></span> <span data-ttu-id="99770-135">Mer information finns i [komma igång med DSC för Linux](lnxGettingStarted.md).</span><span class="sxs-lookup"><span data-stu-id="99770-135">For more information, see [Getting Started with DSC for Linux](lnxGettingStarted.md).</span></span>
