---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Förstå DSC-rollen i en CI/CD-pipeline
ms.openlocfilehash: 8d7244a6e5e2c215d9d3ada959b716df2cce0b83
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "80500814"
---
# <a name="understanding-dscs-role-in-a-cicd-pipeline"></a><span data-ttu-id="8fec1-103">Förstå DSC-rollen i en CI/CD-pipeline</span><span class="sxs-lookup"><span data-stu-id="8fec1-103">Understanding DSC's role in a CI/CD pipeline</span></span>

<span data-ttu-id="8fec1-104">I den här artikeln beskrivs vilka typer av metoder som är tillgängliga för att kombinera konfigurationer och resurser.</span><span class="sxs-lookup"><span data-stu-id="8fec1-104">This article describes the types of approaches available for combining configurations and resources.</span></span>
<span data-ttu-id="8fec1-105">Målet för varje scenario är detsamma, för att minska komplexiteten när flera konfigurationer föredras för att uppnå ett slut tillstånd för Server distribution.</span><span class="sxs-lookup"><span data-stu-id="8fec1-105">The goal for each scenario is the same, to reduce complexity when multiple configurations are preferred to reach a server deployment end state.</span></span> <span data-ttu-id="8fec1-106">Ett exempel på detta är flera team som bidrar till resultatet av en Server distribution, till exempel en program ägare som upprätthåller program tillstånd och ett centralt team som släpper ut ändringar i säkerhets bas linjerna.</span><span class="sxs-lookup"><span data-stu-id="8fec1-106">An example of this would be multiple teams contributing to the outcome of a server deployment, such as an application owner maintaining the application state and a central team releasing changes to security baselines.</span></span> <span data-ttu-id="8fec1-107">Olika delarna för varje metod inklusive de fördelar och risker som beskrivs här.</span><span class="sxs-lookup"><span data-stu-id="8fec1-107">The nuances of each approach including the benefits and risks are detailed here.</span></span>

![Pipeline](media/authoringAdvanced/Pipeline.jpg)

## <a name="types-of-collaborative-authoring-techniques"></a><span data-ttu-id="8fec1-109">Typer av tekniker för samarbets redigering</span><span class="sxs-lookup"><span data-stu-id="8fec1-109">Types of Collaborative Authoring Techniques</span></span>

<span data-ttu-id="8fec1-110">Det finns två lösningar som är inbyggda i lokala Configuration Manager för att aktivera det här konceptet:</span><span class="sxs-lookup"><span data-stu-id="8fec1-110">There are two solutions built in to Local Configuration Manager to enable this concept:</span></span>

|        <span data-ttu-id="8fec1-111">Begrepp</span><span class="sxs-lookup"><span data-stu-id="8fec1-111">Concept</span></span>         |                    <span data-ttu-id="8fec1-112">Detaljerad information</span><span class="sxs-lookup"><span data-stu-id="8fec1-112">Detailed Information</span></span>                     |
| ---------------------- | ----------------------------------------------------------- |
| <span data-ttu-id="8fec1-113">Partiella konfigurationer</span><span class="sxs-lookup"><span data-stu-id="8fec1-113">Partial Configurations</span></span> | [<span data-ttu-id="8fec1-114">Dokumentation</span><span class="sxs-lookup"><span data-stu-id="8fec1-114">Documentation</span></span>](../pull-server/partialConfigs.md)           |
| <span data-ttu-id="8fec1-115">Sammansatta resurser</span><span class="sxs-lookup"><span data-stu-id="8fec1-115">Composite Resources</span></span>    | [<span data-ttu-id="8fec1-116">Dokumentation</span><span class="sxs-lookup"><span data-stu-id="8fec1-116">Documentation</span></span>](../resources/authoringResourceComposite.md) |

## <a name="understanding-the-impact-of-each-approach"></a><span data-ttu-id="8fec1-117">Förstå påverkan av varje metod</span><span class="sxs-lookup"><span data-stu-id="8fec1-117">Understanding The Impact of Each Approach</span></span>

<span data-ttu-id="8fec1-118">Du kan använda någon av dessa lösningar för att hantera resultatet av en Server distribution.</span><span class="sxs-lookup"><span data-stu-id="8fec1-118">Either of these solutions can be used to manage the outcome of a server deployment.</span></span> <span data-ttu-id="8fec1-119">Det finns dock betydande skillnader i effekten av att använda varje metod.</span><span class="sxs-lookup"><span data-stu-id="8fec1-119">However, there is significant difference in the impact of using each approach.</span></span>

## <a name="partial-configurations"></a><span data-ttu-id="8fec1-120">Partiella konfigurationer</span><span class="sxs-lookup"><span data-stu-id="8fec1-120">Partial Configurations</span></span>

<span data-ttu-id="8fec1-121">När du använder partiella konfigurationer konfigureras lokala Configuration Manager för att hantera flera konfigurationer oberoende av varandra.</span><span class="sxs-lookup"><span data-stu-id="8fec1-121">When using Partial Configurations, Local Configuration Manager is configured to manage multiple configurations independently.</span></span> <span data-ttu-id="8fec1-122">Konfigurationer kompileras oberoende och tilldelas sedan till noden.</span><span class="sxs-lookup"><span data-stu-id="8fec1-122">Configurations are compiled independently and then assigned to the node.</span></span> <span data-ttu-id="8fec1-123">Detta kräver att LCM konfigureras i förväg med namnet på varje konfiguration.</span><span class="sxs-lookup"><span data-stu-id="8fec1-123">This requires LCM to be configured in advance with the name of each configuration.</span></span>

![PartialConfiguration](media/authoringAdvanced/PartialConfiguration.jpg)

<span data-ttu-id="8fec1-125">Partiella konfigurationer ger två eller fler team fullständig kontroll över konfigurationen av en server, ofta utan fördelarna med kommunikation eller samarbete.</span><span class="sxs-lookup"><span data-stu-id="8fec1-125">Partial Configurations provide two, or more, teams complete control over configuration of a server, often without the benefit of communication or collaboration.</span></span>

<span data-ttu-id="8fec1-126">Kunderna har fått feedback om att detta kan leda till resurs konflikter, oavsiktliga åsidosättningar och i slut ändan av den verkliga konfigurations kontrollen för till gången.</span><span class="sxs-lookup"><span data-stu-id="8fec1-126">Customers have provided feedback that this can lead to resource conflicts, unintentional overrides, and ultimately loss of true configuration control of the asset.</span></span>

<span data-ttu-id="8fec1-127">Kunder har dessutom fått feedback om att när du använder den här modellen, är varje ändring av team konfigurations ändringar troligen inte helt testade genom en versions pipeline, vilket leder till oväntade resultat i produktionen.</span><span class="sxs-lookup"><span data-stu-id="8fec1-127">Additionally, customers have provided feedback that when using this model, each controlling teams configuration changes are unlikely to be fully tested through a release pipeline, leading to unexpected results in production.</span></span>

<span data-ttu-id="8fec1-128">**Det är viktigt att en enda pipeline används för att utvärdera alla ändringar som släpps till servrar.**</span><span class="sxs-lookup"><span data-stu-id="8fec1-128">**It is critical that a single pipeline be used to evaluate all changes released to servers.**</span></span>

<span data-ttu-id="8fec1-129">I bilden nedan släpper team B sin del konfiguration till Team A. Team A kör sedan sina tester mot en server med båda konfigurationerna applicerade.</span><span class="sxs-lookup"><span data-stu-id="8fec1-129">In the illustration below, Team B releases their partial configuration to Team A. Team A then runs their tests against a server with both configurations applied.</span></span> <span data-ttu-id="8fec1-130">I den här modellen har endast en myndighet behörighet att göra ändringar i produktionen.</span><span class="sxs-lookup"><span data-stu-id="8fec1-130">In this model, only one authority has permission to make changes in production.</span></span>

![PartialSinglePipeline](media/authoringAdvanced/PartialSinglePipeline.jpg)

<span data-ttu-id="8fec1-132">När ändringar krävs från Team B bör de skicka in en pull-begäran mot gruppens käll kontroll miljö.</span><span class="sxs-lookup"><span data-stu-id="8fec1-132">When changes are required from Team B, they should submit a Pull Request against Team A's source control environment.</span></span> <span data-ttu-id="8fec1-133">Team A granskar sedan ändringarna med test automatisering och släpp till produktion när det är säkert att ändringarna inte orsakar fel i de program eller tjänster som servern är värd för.</span><span class="sxs-lookup"><span data-stu-id="8fec1-133">Team A would then review the changes using test automation and release to production when there is confidence that the changes will not cause errors in the applications or services hosted by the server.</span></span>

## <a name="composite-resources"></a><span data-ttu-id="8fec1-134">Sammansatta resurser</span><span class="sxs-lookup"><span data-stu-id="8fec1-134">Composite Resources</span></span>

<span data-ttu-id="8fec1-135">En sammansatt resurs är helt enkelt en DSC-konfiguration som paketeras som en resurs.</span><span class="sxs-lookup"><span data-stu-id="8fec1-135">A composite resource is simply a DSC Configuration packaged as a resource.</span></span> <span data-ttu-id="8fec1-136">Det finns inga särskilda krav för att konfigurera LCM för att godkänna sammansatta resurser.</span><span class="sxs-lookup"><span data-stu-id="8fec1-136">There are no special requirements for configuring LCM to accept composite resources.</span></span> <span data-ttu-id="8fec1-137">Resurserna används i en ny konfiguration och ett enda kompilerings resultat i en MOF-fil.</span><span class="sxs-lookup"><span data-stu-id="8fec1-137">The resources are used within a new configuration and a single compilation results in one MOF file.</span></span>

![CompositeResource](media/authoringAdvanced/CompositeResource.jpg)

<span data-ttu-id="8fec1-139">Det finns två vanliga scenarier för sammansatta resurser.</span><span class="sxs-lookup"><span data-stu-id="8fec1-139">There are two common scenarios for composite resources.</span></span> <span data-ttu-id="8fec1-140">Det första är att minska komplexiteten och abstrakta unika begrepp.</span><span class="sxs-lookup"><span data-stu-id="8fec1-140">The first is to reduce complexity and abstract unique concepts.</span></span> <span data-ttu-id="8fec1-141">Det andra är att tillåta att bas linjer paketeras för att en program grupp ska kunna distribueras genom sin versions pipeline till produktion när alla tester har slutförts.</span><span class="sxs-lookup"><span data-stu-id="8fec1-141">The second is to allow baselines to be packaged for an application team to safely deploy through their release pipeline to production after all tests have passed.</span></span>

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

<span data-ttu-id="8fec1-142">Sammansatta resurser befordrar både komposition och samarbete med en pipeline medan man skapar drifts löp tid.</span><span class="sxs-lookup"><span data-stu-id="8fec1-142">Composite resources promote both composition and collaboration using a pipeline while building operational maturity.</span></span>

<span data-ttu-id="8fec1-143">Du kanske redan använder sammansatta resurser utan att realisera den.</span><span class="sxs-lookup"><span data-stu-id="8fec1-143">You might be already using composite resources without realizing it.</span></span> <span data-ttu-id="8fec1-144">Ett exempel är **ServiceSet**.</span><span class="sxs-lookup"><span data-stu-id="8fec1-144">An example is **ServiceSet**.</span></span>
<span data-ttu-id="8fec1-145">Den här resursen hanterar statusen för flera Windows-tjänster utan att lista dem separat.</span><span class="sxs-lookup"><span data-stu-id="8fec1-145">This resource manages the state of multiple Windows Services without listing them individually.</span></span> <span data-ttu-id="8fec1-146">Egenskapen Name accepterar en sträng mat ris som anger namnet på varje tjänst.</span><span class="sxs-lookup"><span data-stu-id="8fec1-146">The Name property accepts an array of strings to provide the name of each service.</span></span> <span data-ttu-id="8fec1-147">När konfigurationen kompileras innehåller MOF ett unikt tjänst avsnitt för varje namn som skickas till ServiceSet.</span><span class="sxs-lookup"><span data-stu-id="8fec1-147">When the configuration is compiled, the MOF will contain a unique Service section for each of the Names passed to ServiceSet.</span></span>

<span data-ttu-id="8fec1-148">Organisationer kan ha "agenter" eller "mellanprogram" som ska installeras på alla servrar.</span><span class="sxs-lookup"><span data-stu-id="8fec1-148">Organizations might have "agents" or "middleware" that should be installed on every server.</span></span> <span data-ttu-id="8fec1-149">En sammansatt resurs är det bästa svaret på att hantera beroenden, installation och konfiguration av sådana verktyg och verktyg.</span><span class="sxs-lookup"><span data-stu-id="8fec1-149">A composite resource is the best answer to managing the dependencies, setup, and configuration of any such tools and utilities.</span></span>

<span data-ttu-id="8fec1-150">Den person eller det team som ansvarar för lösningar som sträcker sig över flera servrar redigerar en konfiguration som innehåller deras krav.</span><span class="sxs-lookup"><span data-stu-id="8fec1-150">The person or team responsible for solutions that span multiple servers authors a configuration containing their requirements.</span></span> <span data-ttu-id="8fec1-151">Därefter paketeras konfigurationen som en sammansatt resurs med hjälp av anvisningarna i den sammansatta resurs dokumentationen.</span><span class="sxs-lookup"><span data-stu-id="8fec1-151">Next, the configuration would be packaged as a composite resource using instructions provided in the composite resource documentation.</span></span> <span data-ttu-id="8fec1-152">Slutligen bör den nya sammansatta resursen publiceras på en plats, till exempel en fil resurs eller ett NuGet-flöde där program team kan använda den i sina konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="8fec1-152">Finally, the new composite resource should be published to a location such as a file share or NuGet feed where application teams can consume it in their configurations.</span></span>

<span data-ttu-id="8fec1-153">Varje gången gruppen frigör en ny version, ökar versions numret i modulens manifest för sin sammansatta resurs.</span><span class="sxs-lookup"><span data-stu-id="8fec1-153">Each time the team releases a new version, they would increment the version number in the module manifest for their composite resource.</span></span> <span data-ttu-id="8fec1-154">Program teamen innehåller den sammansatta resursen i konfigurationen som de skapar för att hantera program beroenden.</span><span class="sxs-lookup"><span data-stu-id="8fec1-154">The application teams include the composite resource in the configuration they author for managing application dependencies.</span></span> <span data-ttu-id="8fec1-155">När drift-/säkerhets teamen släpper en ny version av sin resurs, meddelar de program teamen om en ny ändring.</span><span class="sxs-lookup"><span data-stu-id="8fec1-155">When the Operations/Security teams release a new version of their resource, they notify the application teams of a new change.</span></span>

<span data-ttu-id="8fec1-156">Program teamen kan utlösa en version till produktion där den enda ändringen är till bas linjer.</span><span class="sxs-lookup"><span data-stu-id="8fec1-156">The application teams might trigger a release to production where the only change is to baselines.</span></span>
<span data-ttu-id="8fec1-157">Detta ger dock en möjlighet att utvärdera program som påverkar risken för avbrott i tjänsten.</span><span class="sxs-lookup"><span data-stu-id="8fec1-157">However, this provides an opportunity to evaluate impact to applications before risk of a service outage.</span></span>

> [!NOTE]
> <span data-ttu-id="8fec1-158">Feedback om användningen av sammansatta resurser har inkluderat Criticism som gör att ändringar kräver kompilering och frisläppning av en ny MOF.</span><span class="sxs-lookup"><span data-stu-id="8fec1-158">Feedback regarding the use of composite resources has included criticism that making changes requires compiling and releasing a new MOF.</span></span> <span data-ttu-id="8fec1-159">Det här är avsiktligt.</span><span class="sxs-lookup"><span data-stu-id="8fec1-159">This is by design.</span></span> <span data-ttu-id="8fec1-160">Varje ny konfigurations utgåva bör innehålla en statisk referens till en speciell version av varje resurs och bör verifieras av tester innan de når till produktions serverns noder.</span><span class="sxs-lookup"><span data-stu-id="8fec1-160">Each new configuration release should include a static reference to a specific version of each resource, and should be validated by tests before reaching production server nodes.</span></span> <span data-ttu-id="8fec1-161">Processen för att testa och släppa ändringar från käll kontrollen skapar en säker miljö för att släppa ändringar i små och ofta förekommande batchar.</span><span class="sxs-lookup"><span data-stu-id="8fec1-161">The process of testing and releasing changes from source control creates a safe environment for releasing change in small but frequent batches.</span></span>

<span data-ttu-id="8fec1-162">Mer information om hur du använder versions pipelines för att hantera kärn infrastrukturen finns i fakta bladet [version: versions pipeline](../further-reading/whitepapers.md).</span><span class="sxs-lookup"><span data-stu-id="8fec1-162">For more information about using release pipelines to manage core infrastructure, see the whitepaper: [The Release Pipeline Model](../further-reading/whitepapers.md).</span></span>
