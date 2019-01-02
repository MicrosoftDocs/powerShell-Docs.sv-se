---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Avancerad DSC-redigering för sammansättning och samarbete
ms.openlocfilehash: 3e40ba94de0a53c1c9663553c4ec443b5e0df3fd
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405320"
---
# <a name="advanced-dsc-authoring-for-composition-and-collaboration"></a><span data-ttu-id="801c3-103">Avancerad DSC-redigering för sammansättning och samarbete</span><span class="sxs-lookup"><span data-stu-id="801c3-103">Advanced DSC Authoring for Composition and Collaboration</span></span>

<span data-ttu-id="801c3-104">Den här artikeln beskrivs olika metoder som är tillgängliga för att kombinera konfigurationer och resurser.</span><span class="sxs-lookup"><span data-stu-id="801c3-104">This article describes the types of approaches available for combining configurations and resources.</span></span>
<span data-ttu-id="801c3-105">Målet för varje scenario är samma, minska komplexiteten när flera konfigurationer är lämpligt att nå slutet distributionstillstånd för en server.</span><span class="sxs-lookup"><span data-stu-id="801c3-105">The goal for each scenario is the same, to reduce complexity when multiple configurations are preferred to reach a server deployment end state.</span></span>
<span data-ttu-id="801c3-106">Ett exempel på detta är flera team som bidrar till resultatet av en serverdistribution, till exempel en programägaren programtillståndet och ett centralt team lanserar ändringar i säkerheten.</span><span class="sxs-lookup"><span data-stu-id="801c3-106">An example of this would be multiple teams contributing to the outcome of a server deployment, such as an application owner maintaining the application state and a central team releasing changes to security baselines.</span></span>
<span data-ttu-id="801c3-107">Här beskrivs de olika delarna i varje metod, inklusive fördelar och risker.</span><span class="sxs-lookup"><span data-stu-id="801c3-107">The nuances of each approach including the benefits and risks are detailed here.</span></span>

![Pipeline](../images/Pipeline.jpg)

## <a name="types-of-collaborative-authoring-techniques"></a><span data-ttu-id="801c3-109">Typer av samarbetsfunktioner redigering tekniker</span><span class="sxs-lookup"><span data-stu-id="801c3-109">Types of Collaborative Authoring Techniques</span></span>

<span data-ttu-id="801c3-110">Det finns två lösningar som skapats till lokala Configuration Manager för att aktivera detta begrepp:</span><span class="sxs-lookup"><span data-stu-id="801c3-110">There are two solutions built in to Local Configuration Manager to enable this concept:</span></span>

| <span data-ttu-id="801c3-111">Begrepp</span><span class="sxs-lookup"><span data-stu-id="801c3-111">Concept</span></span> | <span data-ttu-id="801c3-112">Detaljerad Information</span><span class="sxs-lookup"><span data-stu-id="801c3-112">Detailed Information</span></span>
|-|-
| <span data-ttu-id="801c3-113">Partiella konfigurationer</span><span class="sxs-lookup"><span data-stu-id="801c3-113">Partial Configurations</span></span> | [<span data-ttu-id="801c3-114">Dokumentation</span><span class="sxs-lookup"><span data-stu-id="801c3-114">Documentation</span></span>](../pull-server/partialConfigs.md)
| <span data-ttu-id="801c3-115">Sammansatta resurser</span><span class="sxs-lookup"><span data-stu-id="801c3-115">Composite Resources</span></span> | [<span data-ttu-id="801c3-116">Dokumentation</span><span class="sxs-lookup"><span data-stu-id="801c3-116">Documentation</span></span>](../resources/authoringResourceComposite.md)

## <a name="understanding-the-impact-of-each-approach"></a><span data-ttu-id="801c3-117">Förstå effekten av varje metod</span><span class="sxs-lookup"><span data-stu-id="801c3-117">Understanding The Impact of Each Approach</span></span>

<span data-ttu-id="801c3-118">Någon av dessa lösningar kan användas för att hantera resultatet av en server-distribution.</span><span class="sxs-lookup"><span data-stu-id="801c3-118">Either of these solutions can be used to manage the outcome of a server deployment.</span></span>
<span data-ttu-id="801c3-119">Det finns betydande skillnader i effekten av att använda varje metod.</span><span class="sxs-lookup"><span data-stu-id="801c3-119">However, there is significant difference in the impact of using each approach.</span></span>

## <a name="partial-configurations"></a><span data-ttu-id="801c3-120">Partiella konfigurationer</span><span class="sxs-lookup"><span data-stu-id="801c3-120">Partial Configurations</span></span>

<span data-ttu-id="801c3-121">När du använder partiella konfigurationer, har Local Configuration Manager konfigurerats för att hantera konfigurationer med flera oberoende av varandra.</span><span class="sxs-lookup"><span data-stu-id="801c3-121">When using Partial Configurations, Local Configuration Manager is configured to manage multiple configurations independently.</span></span>
<span data-ttu-id="801c3-122">Konfigurationer kompileras oberoende av varandra och sedan tilldelad till noden.</span><span class="sxs-lookup"><span data-stu-id="801c3-122">Configurations are compiled independently and then assigned to the node.</span></span>
<span data-ttu-id="801c3-123">Detta kräver LCM konfigureras i förväg med namnet på varje konfiguration.</span><span class="sxs-lookup"><span data-stu-id="801c3-123">This requires LCM to be configured in advance with the name of each configuration.</span></span>

![PartialConfiguration](../images/PartialConfiguration.jpg)

<span data-ttu-id="801c3-125">Partiella konfigurationer ange två eller fler, teams fullständig kontroll över konfigurationen för en server, ofta utan kommunikations- eller samarbetstjänster.</span><span class="sxs-lookup"><span data-stu-id="801c3-125">Partial Configurations provide two, or more, teams complete control over configuration of a server, often without the benefit of communication or collaboration.</span></span>

<span data-ttu-id="801c3-126">Kunder har angett feedback som detta kan leda till konflikter, oavsiktlig åsidosättningar och i slutänden förlust av SANT Konfigurationskontroll av tillgången.</span><span class="sxs-lookup"><span data-stu-id="801c3-126">Customers have provided feedback that this can lead to resource conflicts, unintentional overrides, and ultimately loss of true configuration control of the asset.</span></span>

<span data-ttu-id="801c3-127">Kunder har dessutom som feedback att varje styra team konfigurationsändringar är sannolikt inte kommer att testas helt via en releasepipeline när du använder den här modellen, vilket leder till oväntade resultat i produktion.</span><span class="sxs-lookup"><span data-stu-id="801c3-127">Additionally, customers have provided feedback that when using this model, each controlling teams configuration changes are unlikely to be fully tested through a release pipeline, leading to unexpected results in production.</span></span>

<span data-ttu-id="801c3-128">**Det är viktigt att en enda pipeline kan användas för att utvärdera alla ändringar versionen till servrar.**</span><span class="sxs-lookup"><span data-stu-id="801c3-128">**It is critical that a single pipeline be used to evaluate all changes release to servers.**</span></span>

<span data-ttu-id="801c3-129">På bilden nedan Team B släpper sina partiell konfiguration till teamet A. Team A och kör sina tester mot en server med båda konfigurationer som används.</span><span class="sxs-lookup"><span data-stu-id="801c3-129">In the illustration below, Team B releases their partial configuration to Team A. Team A then runs their tests against a server with both configurations applied.</span></span>
<span data-ttu-id="801c3-130">I den här modellen har endast en utfärdaren behörighet att göra ändringar i produktion.</span><span class="sxs-lookup"><span data-stu-id="801c3-130">In this model, only one authority has permission to make changes in production.</span></span>

![PartialSinglePipeline](../images/PartialSinglePipeline.jpg)

<span data-ttu-id="801c3-132">När det krävs ändringar från teamet B, bör de skicka en Pull-begäran mot Team A: s källmiljö för kontrollen.</span><span class="sxs-lookup"><span data-stu-id="801c3-132">When changes are required from Team B, they should submit a Pull Request against Team A's source control environment.</span></span>
<span data-ttu-id="801c3-133">Grupp A skulle sedan granska ändringarna med automatiserad testning och släpp till produktion när det inte är säker på att ändringarna inte orsakar fel i program eller tjänster som hanteras av servern.</span><span class="sxs-lookup"><span data-stu-id="801c3-133">Team A would then review the changes using test automation and release to production when there is confidence that the changes will not cause errors in the applications or services hosted by the server.</span></span>

## <a name="composite-resources"></a><span data-ttu-id="801c3-134">Sammansatta resurser</span><span class="sxs-lookup"><span data-stu-id="801c3-134">Composite Resources</span></span>

<span data-ttu-id="801c3-135">En sammansatt resurs är helt enkelt en DSC-konfiguration som paketerad som en resurs.</span><span class="sxs-lookup"><span data-stu-id="801c3-135">A composite resource is simply a DSC Configuration packaged as a resource.</span></span>
<span data-ttu-id="801c3-136">Det finns inga särskilda krav för att konfigurera LCM att acceptera sammansatta resurser.</span><span class="sxs-lookup"><span data-stu-id="801c3-136">There are no special requirements for configuring LCM to accept composite resources.</span></span>
<span data-ttu-id="801c3-137">Resurserna som används i en ny konfiguration och en enda sammanställning resulterar i en MOF-filen.</span><span class="sxs-lookup"><span data-stu-id="801c3-137">The resources are used within a new configuration and a single compilation results in one MOF file.</span></span>

![CompositeResource](../images/CompositeResource.jpg)

<span data-ttu-id="801c3-139">Det finns två vanliga scenarier för sammansatta resurser.</span><span class="sxs-lookup"><span data-stu-id="801c3-139">There are two common scenarios for composite resources.</span></span>
<span data-ttu-id="801c3-140">Först är att minska komplexiteten och abstrakt unika begrepp.</span><span class="sxs-lookup"><span data-stu-id="801c3-140">The first is to reduce complexity and abstract unique concepts.</span></span>
<span data-ttu-id="801c3-141">Andra är att tillåta baslinjer som ska paketeras för ett program-teamet på ett säkert sätt distribuerar via sina releasepipeline till produktion när du har klarat alla tester.</span><span class="sxs-lookup"><span data-stu-id="801c3-141">The second is to allow baselines to be packaged for an application team to safely deploy through their release pipeline to production after all tests have passed.</span></span>

```PowerShell
Configuration Name
{
  File 1
  {
    Ensure = “Present”
    Path = “c:\inetpub\file1.zip”
    Source = “http://uri/file1.zip”
  }
  Service A
  {
    Ensure = “Present”
    Name = “ServiceA”
    Status = “Running”
  }
  SecurityBaseline Settings
  {
    Ensure = “Present”
    Datacenter = “NorthAmerica”
  }
}
```

<span data-ttu-id="801c3-142">Sammansatta resurser för enklare både sammansättning och samarbete med hjälp av en pipeline när du skapar operativa mognad</span><span class="sxs-lookup"><span data-stu-id="801c3-142">Composite resources promote both composition and collaboration using a pipeline while building operational maturity</span></span>

<span data-ttu-id="801c3-143">Du kanske redan använder sammansatta resurser utan att märker det.</span><span class="sxs-lookup"><span data-stu-id="801c3-143">You might be already using composite resources without realizing it.</span></span>
<span data-ttu-id="801c3-144">Ett exempel är **ServiceSet**.</span><span class="sxs-lookup"><span data-stu-id="801c3-144">An example is **ServiceSet**.</span></span>
<span data-ttu-id="801c3-145">Den här resursen hanterar tillståndet för flera Windows-tjänster utan att skriva dem individuellt.</span><span class="sxs-lookup"><span data-stu-id="801c3-145">This resource manages the state of multiple Windows Services without listing them individually.</span></span>
<span data-ttu-id="801c3-146">Namnegenskapen accepterar en matris med strängar att ange namnet på varje tjänst.</span><span class="sxs-lookup"><span data-stu-id="801c3-146">The Name property accepts an array of strings to provide the name of each service.</span></span>
<span data-ttu-id="801c3-147">När konfigurationen kompileras innehåller MOF en unik Service-avsnittet för var och en av de namn som skickats till ServiceSet.</span><span class="sxs-lookup"><span data-stu-id="801c3-147">When the configuration is compiled, the MOF will contain a unique Service section for each of the Names passed to ServiceSet.</span></span>

<span data-ttu-id="801c3-148">Organisationer kan ha ”agenter” eller ”mellanprogram” som ska installeras på varje server.</span><span class="sxs-lookup"><span data-stu-id="801c3-148">Organizations might have "agents" or "middleware" that should be installed on every server.</span></span>
<span data-ttu-id="801c3-149">En sammansatt resurs är det bästa svaret för att hantera beroenden, installationen och konfigurationen av verktyg och hjälpmedel.</span><span class="sxs-lookup"><span data-stu-id="801c3-149">A composite resource is the best answer to managing the dependencies, setup, and configuration of any such tools and utilities.</span></span>

<span data-ttu-id="801c3-150">Den person eller grupp som ansvarar för lösningar som sträcker sig över flera servrar skapar du en konfiguration som innehåller deras krav.</span><span class="sxs-lookup"><span data-stu-id="801c3-150">The person or team responsible for solutions that span multiple servers authors a configuration containing their requirements.</span></span>
<span data-ttu-id="801c3-151">Sedan skulle konfigurationen vara paketerad som sammansatta resurser genom att använda instruktionerna i dokumentationen till sammansatta resource.</span><span class="sxs-lookup"><span data-stu-id="801c3-151">Next, the configuration would be packaged as a composite resource using instructions provided in the composite resource documentation.</span></span>
<span data-ttu-id="801c3-152">Slutligen den nya sammansatta resursen ska publiceras till en plats, till exempel en filresurs eller NuGet flöde där applikationsteam kan använda den i sina konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="801c3-152">Finally, the new composite resource should be published to a location such as a file share or NuGet feed where application teams can consume it in their configurations.</span></span>

<span data-ttu-id="801c3-153">Varje gång som teamet släpper en ny version, skulle de öka versionsnumret i modulmanifestet för sina sammansatta resursen.</span><span class="sxs-lookup"><span data-stu-id="801c3-153">Each time the team releases a new version, they would increment the version number in the module manifest for their composite resource.</span></span>
<span data-ttu-id="801c3-154">Programteam innehåller sammansatta resurs i konfigurationen som de skapar för att hantera beroenden.</span><span class="sxs-lookup"><span data-stu-id="801c3-154">The application teams include the composite resource in the configuration they author for managing application dependencies.</span></span>
<span data-ttu-id="801c3-155">När Operations/Security Team släpper en ny version av resursen, meddela de programteam av en ny ändring.</span><span class="sxs-lookup"><span data-stu-id="801c3-155">When the Operations/Security teams release a new version of their resource, they notify the application teams of a new change.</span></span>

<span data-ttu-id="801c3-156">Programteam kan utlöser en släppning till produktion där den enda förändringen är att baslinjer.</span><span class="sxs-lookup"><span data-stu-id="801c3-156">The application teams might trigger a release to production where the only change is to baselines.</span></span>
<span data-ttu-id="801c3-157">Det ger dock en möjlighet att utvärdera påverkan på program innan du risken för avbrott i tjänsten.</span><span class="sxs-lookup"><span data-stu-id="801c3-157">However, this provides an opportunity to evaluate impact to applications before risk of a service outage.</span></span>

<span data-ttu-id="801c3-158">Obs! – Feedback om användningen av sammansatta resurser har inkluderat kritik för att ändringarna kräver när koden kompileras och lanserar en ny MOF.</span><span class="sxs-lookup"><span data-stu-id="801c3-158">Note - Feedback regarding the use of composite resources has included criticism that making changes requires compiling and releasing a new MOF.</span></span>
<span data-ttu-id="801c3-159">Det här är avsiktligt.</span><span class="sxs-lookup"><span data-stu-id="801c3-159">This is by design.</span></span>
<span data-ttu-id="801c3-160">Varje ny version av configuration bör innehålla en statisk referens till en specifik version av varje resurs och bör verifieras genom tester innan de når produktionen servernoder.</span><span class="sxs-lookup"><span data-stu-id="801c3-160">Each new configuration release should include a static reference to a specific version of each resource, and should be validated by tests before reaching production server nodes.</span></span>
<span data-ttu-id="801c3-161">Hur du testar och publicerar ändringar från källkontroll skapar en säker miljö för att frisläppa ändring i små och ofta batchar.</span><span class="sxs-lookup"><span data-stu-id="801c3-161">The process of testing and releasing changes from source control creates a safe environment for releasing change in small but frequent batches.</span></span>

<span data-ttu-id="801c3-162">Mer information om hur du använder distributions-pipelines för att hantera grundläggande infrastruktur finns i faktabladet: [Pipeline-modellen versionen](../further-reading/whitepapers.md).</span><span class="sxs-lookup"><span data-stu-id="801c3-162">For more information about using release pipelines to manage core infrastructure, see the whitepaper: [The Release Pipeline Model](../further-reading/whitepapers.md).</span></span>
