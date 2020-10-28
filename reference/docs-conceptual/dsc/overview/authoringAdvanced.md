---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Förstå DSC-rollen i en CI/CD-pipeline
description: I den här artikeln beskrivs vilka typer av metoder som är tillgängliga för att kombinera konfigurationer och resurser i en CI/CD-pipeline.
ms.openlocfilehash: 8d06b86724eb25e657687e6518c01bb29d984264
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92647032"
---
# <a name="understanding-dscs-role-in-a-cicd-pipeline"></a><span data-ttu-id="4111b-104">Förstå DSC-rollen i en CI/CD-pipeline</span><span class="sxs-lookup"><span data-stu-id="4111b-104">Understanding DSC's role in a CI/CD pipeline</span></span>

<span data-ttu-id="4111b-105">I den här artikeln beskrivs vilka typer av metoder som är tillgängliga för att kombinera konfigurationer och resurser.</span><span class="sxs-lookup"><span data-stu-id="4111b-105">This article describes the types of approaches available for combining configurations and resources.</span></span>
<span data-ttu-id="4111b-106">Målet för varje scenario är detsamma, för att minska komplexiteten när flera konfigurationer föredras för att uppnå ett slut tillstånd för Server distribution.</span><span class="sxs-lookup"><span data-stu-id="4111b-106">The goal for each scenario is the same, to reduce complexity when multiple configurations are preferred to reach a server deployment end state.</span></span> <span data-ttu-id="4111b-107">Ett exempel på detta är flera team som bidrar till resultatet av en Server distribution, till exempel en program ägare som upprätthåller program tillstånd och ett centralt team som släpper ut ändringar i säkerhets bas linjerna.</span><span class="sxs-lookup"><span data-stu-id="4111b-107">An example of this would be multiple teams contributing to the outcome of a server deployment, such as an application owner maintaining the application state and a central team releasing changes to security baselines.</span></span> <span data-ttu-id="4111b-108">Olika delarna för varje metod inklusive de fördelar och risker som beskrivs här.</span><span class="sxs-lookup"><span data-stu-id="4111b-108">The nuances of each approach including the benefits and risks are detailed here.</span></span>

![Process flöde för en CI/CD-pipeline](media/authoringAdvanced/Pipeline.jpg)

## <a name="types-of-collaborative-authoring-techniques"></a><span data-ttu-id="4111b-110">Typer av tekniker för samarbets redigering</span><span class="sxs-lookup"><span data-stu-id="4111b-110">Types of Collaborative Authoring Techniques</span></span>

<span data-ttu-id="4111b-111">Det finns två lösningar som är inbyggda i lokala Configuration Manager för att aktivera det här konceptet:</span><span class="sxs-lookup"><span data-stu-id="4111b-111">There are two solutions built in to Local Configuration Manager to enable this concept:</span></span>

|        <span data-ttu-id="4111b-112">Koncept</span><span class="sxs-lookup"><span data-stu-id="4111b-112">Concept</span></span>         |                    <span data-ttu-id="4111b-113">Detaljerad information</span><span class="sxs-lookup"><span data-stu-id="4111b-113">Detailed Information</span></span>                     |
| ---------------------- | ----------------------------------------------------------- |
| <span data-ttu-id="4111b-114">Partiella konfigurationer</span><span class="sxs-lookup"><span data-stu-id="4111b-114">Partial Configurations</span></span> | [<span data-ttu-id="4111b-115">Dokumentation</span><span class="sxs-lookup"><span data-stu-id="4111b-115">Documentation</span></span>](../pull-server/partialConfigs.md)           |
| <span data-ttu-id="4111b-116">Sammansatta resurser</span><span class="sxs-lookup"><span data-stu-id="4111b-116">Composite Resources</span></span>    | [<span data-ttu-id="4111b-117">Dokumentation</span><span class="sxs-lookup"><span data-stu-id="4111b-117">Documentation</span></span>](../resources/authoringResourceComposite.md) |

## <a name="understanding-the-impact-of-each-approach"></a><span data-ttu-id="4111b-118">Förstå påverkan av varje metod</span><span class="sxs-lookup"><span data-stu-id="4111b-118">Understanding The Impact of Each Approach</span></span>

<span data-ttu-id="4111b-119">Du kan använda någon av dessa lösningar för att hantera resultatet av en Server distribution.</span><span class="sxs-lookup"><span data-stu-id="4111b-119">Either of these solutions can be used to manage the outcome of a server deployment.</span></span> <span data-ttu-id="4111b-120">Det finns dock betydande skillnader i effekten av att använda varje metod.</span><span class="sxs-lookup"><span data-stu-id="4111b-120">However, there is significant difference in the impact of using each approach.</span></span>

## <a name="partial-configurations"></a><span data-ttu-id="4111b-121">Partiella konfigurationer</span><span class="sxs-lookup"><span data-stu-id="4111b-121">Partial Configurations</span></span>

<span data-ttu-id="4111b-122">När du använder partiella konfigurationer konfigureras lokala Configuration Manager för att hantera flera konfigurationer oberoende av varandra.</span><span class="sxs-lookup"><span data-stu-id="4111b-122">When using Partial Configurations, Local Configuration Manager is configured to manage multiple configurations independently.</span></span> <span data-ttu-id="4111b-123">Konfigurationer kompileras oberoende och tilldelas sedan till noden.</span><span class="sxs-lookup"><span data-stu-id="4111b-123">Configurations are compiled independently and then assigned to the node.</span></span> <span data-ttu-id="4111b-124">Detta kräver att LCM konfigureras i förväg med namnet på varje konfiguration.</span><span class="sxs-lookup"><span data-stu-id="4111b-124">This requires LCM to be configured in advance with the name of each configuration.</span></span>

![Diagram över partiella konfigurationer](media/authoringAdvanced/PartialConfiguration.jpg)

<span data-ttu-id="4111b-126">Partiella konfigurationer ger två eller fler team fullständig kontroll över konfigurationen av en server, ofta utan fördelarna med kommunikation eller samarbete.</span><span class="sxs-lookup"><span data-stu-id="4111b-126">Partial Configurations provide two, or more, teams complete control over configuration of a server, often without the benefit of communication or collaboration.</span></span>

<span data-ttu-id="4111b-127">Kunderna har fått feedback om att detta kan leda till resurs konflikter, oavsiktliga åsidosättningar och i slut ändan av den verkliga konfigurations kontrollen för till gången.</span><span class="sxs-lookup"><span data-stu-id="4111b-127">Customers have provided feedback that this can lead to resource conflicts, unintentional overrides, and ultimately loss of true configuration control of the asset.</span></span>

<span data-ttu-id="4111b-128">Kunder har dessutom fått feedback om att när du använder den här modellen, är varje ändring av team konfigurations ändringar troligen inte helt testade genom en versions pipeline, vilket leder till oväntade resultat i produktionen.</span><span class="sxs-lookup"><span data-stu-id="4111b-128">Additionally, customers have provided feedback that when using this model, each controlling teams configuration changes are unlikely to be fully tested through a release pipeline, leading to unexpected results in production.</span></span>

<span data-ttu-id="4111b-129">**Det är viktigt att en enda pipeline används för att utvärdera alla ändringar som släpps till servrar.**</span><span class="sxs-lookup"><span data-stu-id="4111b-129">**It is critical that a single pipeline be used to evaluate all changes released to servers.**</span></span>

<span data-ttu-id="4111b-130">I bilden nedan släpper team B sin del konfiguration till Team A. Team A kör sedan sina tester mot en server med båda konfigurationerna applicerade.</span><span class="sxs-lookup"><span data-stu-id="4111b-130">In the illustration below, Team B releases their partial configuration to Team A. Team A then runs their tests against a server with both configurations applied.</span></span> <span data-ttu-id="4111b-131">I den här modellen har endast en myndighet behörighet att göra ändringar i produktionen.</span><span class="sxs-lookup"><span data-stu-id="4111b-131">In this model, only one authority has permission to make changes in production.</span></span>

![Diagram över en delvis enskild pipeline](media/authoringAdvanced/PartialSinglePipeline.jpg)

<span data-ttu-id="4111b-133">När ändringar krävs från Team B bör de skicka in en pull-begäran mot gruppens käll kontroll miljö.</span><span class="sxs-lookup"><span data-stu-id="4111b-133">When changes are required from Team B, they should submit a Pull Request against Team A's source control environment.</span></span> <span data-ttu-id="4111b-134">Team A granskar sedan ändringarna med test automatisering och släpp till produktion när det är säkert att ändringarna inte orsakar fel i de program eller tjänster som servern är värd för.</span><span class="sxs-lookup"><span data-stu-id="4111b-134">Team A would then review the changes using test automation and release to production when there is confidence that the changes will not cause errors in the applications or services hosted by the server.</span></span>

## <a name="composite-resources"></a><span data-ttu-id="4111b-135">Sammansatta resurser</span><span class="sxs-lookup"><span data-stu-id="4111b-135">Composite Resources</span></span>

<span data-ttu-id="4111b-136">En sammansatt resurs är helt enkelt en DSC-konfiguration som paketeras som en resurs.</span><span class="sxs-lookup"><span data-stu-id="4111b-136">A composite resource is simply a DSC Configuration packaged as a resource.</span></span> <span data-ttu-id="4111b-137">Det finns inga särskilda krav för att konfigurera LCM för att godkänna sammansatta resurser.</span><span class="sxs-lookup"><span data-stu-id="4111b-137">There are no special requirements for configuring LCM to accept composite resources.</span></span> <span data-ttu-id="4111b-138">Resurserna används i en ny konfiguration och ett enda kompilerings resultat i en MOF-fil.</span><span class="sxs-lookup"><span data-stu-id="4111b-138">The resources are used within a new configuration and a single compilation results in one MOF file.</span></span>

![Diagram över en sammansatt resurs](media/authoringAdvanced/CompositeResource.jpg)

<span data-ttu-id="4111b-140">Det finns två vanliga scenarier för sammansatta resurser.</span><span class="sxs-lookup"><span data-stu-id="4111b-140">There are two common scenarios for composite resources.</span></span> <span data-ttu-id="4111b-141">Det första är att minska komplexiteten och abstrakta unika begrepp.</span><span class="sxs-lookup"><span data-stu-id="4111b-141">The first is to reduce complexity and abstract unique concepts.</span></span> <span data-ttu-id="4111b-142">Det andra är att tillåta att bas linjer paketeras för att en program grupp ska kunna distribueras genom sin versions pipeline till produktion när alla tester har slutförts.</span><span class="sxs-lookup"><span data-stu-id="4111b-142">The second is to allow baselines to be packaged for an application team to safely deploy through their release pipeline to production after all tests have passed.</span></span>

```PowerShell
Configuration Name
{
  File 1
  {
    Ensure = "Present"
    Path = "c:\inetpub\file1.zip"
    Source = "http://uri/file1.zip"
  }
  Service A
  {
    Ensure = "Present"
    Name = "ServiceA"
    Status = "Running"
  }
  SecurityBaseline Settings
  {
    Ensure = "Present"
    Datacenter = "NorthAmerica"
  }
}
```

<span data-ttu-id="4111b-143">Sammansatta resurser befordrar både komposition och samarbete med en pipeline medan man skapar drifts löp tid.</span><span class="sxs-lookup"><span data-stu-id="4111b-143">Composite resources promote both composition and collaboration using a pipeline while building operational maturity.</span></span>

<span data-ttu-id="4111b-144">Du kanske redan använder sammansatta resurser utan att realisera den.</span><span class="sxs-lookup"><span data-stu-id="4111b-144">You might be already using composite resources without realizing it.</span></span> <span data-ttu-id="4111b-145">Ett exempel är **ServiceSet** .</span><span class="sxs-lookup"><span data-stu-id="4111b-145">An example is **ServiceSet** .</span></span>
<span data-ttu-id="4111b-146">Den här resursen hanterar statusen för flera Windows-tjänster utan att lista dem separat.</span><span class="sxs-lookup"><span data-stu-id="4111b-146">This resource manages the state of multiple Windows Services without listing them individually.</span></span> <span data-ttu-id="4111b-147">Egenskapen Name accepterar en sträng mat ris som anger namnet på varje tjänst.</span><span class="sxs-lookup"><span data-stu-id="4111b-147">The Name property accepts an array of strings to provide the name of each service.</span></span> <span data-ttu-id="4111b-148">När konfigurationen kompileras innehåller MOF ett unikt tjänst avsnitt för varje namn som skickas till ServiceSet.</span><span class="sxs-lookup"><span data-stu-id="4111b-148">When the configuration is compiled, the MOF will contain a unique Service section for each of the Names passed to ServiceSet.</span></span>

<span data-ttu-id="4111b-149">Organisationer kan ha "agenter" eller "mellanprogram" som ska installeras på alla servrar.</span><span class="sxs-lookup"><span data-stu-id="4111b-149">Organizations might have "agents" or "middleware" that should be installed on every server.</span></span> <span data-ttu-id="4111b-150">En sammansatt resurs är det bästa svaret på att hantera beroenden, installation och konfiguration av sådana verktyg och verktyg.</span><span class="sxs-lookup"><span data-stu-id="4111b-150">A composite resource is the best answer to managing the dependencies, setup, and configuration of any such tools and utilities.</span></span>

<span data-ttu-id="4111b-151">Den person eller det team som ansvarar för lösningar som sträcker sig över flera servrar redigerar en konfiguration som innehåller deras krav.</span><span class="sxs-lookup"><span data-stu-id="4111b-151">The person or team responsible for solutions that span multiple servers authors a configuration containing their requirements.</span></span> <span data-ttu-id="4111b-152">Därefter paketeras konfigurationen som en sammansatt resurs med hjälp av anvisningarna i den sammansatta resurs dokumentationen.</span><span class="sxs-lookup"><span data-stu-id="4111b-152">Next, the configuration would be packaged as a composite resource using instructions provided in the composite resource documentation.</span></span> <span data-ttu-id="4111b-153">Slutligen bör den nya sammansatta resursen publiceras på en plats, till exempel en fil resurs eller ett NuGet-flöde där program team kan använda den i sina konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="4111b-153">Finally, the new composite resource should be published to a location such as a file share or NuGet feed where application teams can consume it in their configurations.</span></span>

<span data-ttu-id="4111b-154">Varje gången gruppen frigör en ny version, ökar versions numret i modulens manifest för sin sammansatta resurs.</span><span class="sxs-lookup"><span data-stu-id="4111b-154">Each time the team releases a new version, they would increment the version number in the module manifest for their composite resource.</span></span> <span data-ttu-id="4111b-155">Program teamen innehåller den sammansatta resursen i konfigurationen som de skapar för att hantera program beroenden.</span><span class="sxs-lookup"><span data-stu-id="4111b-155">The application teams include the composite resource in the configuration they author for managing application dependencies.</span></span> <span data-ttu-id="4111b-156">När drift-/säkerhets teamen släpper en ny version av sin resurs, meddelar de program teamen om en ny ändring.</span><span class="sxs-lookup"><span data-stu-id="4111b-156">When the Operations/Security teams release a new version of their resource, they notify the application teams of a new change.</span></span>

<span data-ttu-id="4111b-157">Program teamen kan utlösa en version till produktion där den enda ändringen är till bas linjer.</span><span class="sxs-lookup"><span data-stu-id="4111b-157">The application teams might trigger a release to production where the only change is to baselines.</span></span>
<span data-ttu-id="4111b-158">Detta ger dock en möjlighet att utvärdera program som påverkar risken för avbrott i tjänsten.</span><span class="sxs-lookup"><span data-stu-id="4111b-158">However, this provides an opportunity to evaluate impact to applications before risk of a service outage.</span></span>

> [!NOTE]
> <span data-ttu-id="4111b-159">Feedback om användningen av sammansatta resurser har inkluderat Criticism som gör att ändringar kräver kompilering och frisläppning av en ny MOF.</span><span class="sxs-lookup"><span data-stu-id="4111b-159">Feedback regarding the use of composite resources has included criticism that making changes requires compiling and releasing a new MOF.</span></span> <span data-ttu-id="4111b-160">Det här är avsiktligt.</span><span class="sxs-lookup"><span data-stu-id="4111b-160">This is by design.</span></span> <span data-ttu-id="4111b-161">Varje ny konfigurations utgåva bör innehålla en statisk referens till en speciell version av varje resurs och bör verifieras av tester innan de når till produktions serverns noder.</span><span class="sxs-lookup"><span data-stu-id="4111b-161">Each new configuration release should include a static reference to a specific version of each resource, and should be validated by tests before reaching production server nodes.</span></span> <span data-ttu-id="4111b-162">Processen för att testa och släppa ändringar från käll kontrollen skapar en säker miljö för att släppa ändringar i små och ofta förekommande batchar.</span><span class="sxs-lookup"><span data-stu-id="4111b-162">The process of testing and releasing changes from source control creates a safe environment for releasing change in small but frequent batches.</span></span>

<span data-ttu-id="4111b-163">Mer information om hur du använder versions pipelines för att hantera kärn infrastrukturen finns i fakta bladet [version: versions pipeline](../further-reading/whitepapers.md).</span><span class="sxs-lookup"><span data-stu-id="4111b-163">For more information about using release pipelines to manage core infrastructure, see the whitepaper: [The Release Pipeline Model](../further-reading/whitepapers.md).</span></span>
