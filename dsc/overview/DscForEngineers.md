---
ms.date: 10/13/2017
keywords: DSC, powershell, konfiguration, installation
title: Desired State Configuration-översikt för tekniker
ms.openlocfilehash: 0e599c2218cd2df29dbd0529006be5e1ef17ce5f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079990"
---
# <a name="desired-state-configuration-overview-for-engineers"></a><span data-ttu-id="d0de1-103">Desired State Configuration-översikt för tekniker</span><span class="sxs-lookup"><span data-stu-id="d0de1-103">Desired State Configuration Overview for Engineers</span></span>

<span data-ttu-id="d0de1-104">Det här dokumentet är avsett för utvecklare och åtgärder team att förstå fördelarna med PowerShell Desired State Configuration (DSC).</span><span class="sxs-lookup"><span data-stu-id="d0de1-104">This document is intended for developer and operations teams to understand the benefits of PowerShell Desired State Configuration (DSC).</span></span>
<span data-ttu-id="d0de1-105">För en högre nivå vy av DSC-värdet erbjuder finns [Desired State Configuration-översikt för beslutsfattare](decisionMaker.md)</span><span class="sxs-lookup"><span data-stu-id="d0de1-105">For a higher level view of the value DSC provides, please see [Desired State Configuration Overview for Decision Makers](decisionMaker.md)</span></span>

## <a name="benefits-of-desired-state-configuration"></a><span data-ttu-id="d0de1-106">Fördelarna med Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="d0de1-106">Benefits of Desired State Configuration</span></span>

<span data-ttu-id="d0de1-107">DSC finns för att:</span><span class="sxs-lookup"><span data-stu-id="d0de1-107">DSC exists to:</span></span>

- <span data-ttu-id="d0de1-108">Minska komplexiteten i skript i Windows</span><span class="sxs-lookup"><span data-stu-id="d0de1-108">Decrease the complexity of scripting in Windows</span></span>
- <span data-ttu-id="d0de1-109">Öka hastigheten på iteration</span><span class="sxs-lookup"><span data-stu-id="d0de1-109">Increase the speed of iteration</span></span>

<span data-ttu-id="d0de1-110">Begreppet ”kontinuerlig distribution” blir viktigare.</span><span class="sxs-lookup"><span data-stu-id="d0de1-110">The concept of "continuous deployment" is becoming more important.</span></span>
<span data-ttu-id="d0de1-111">Kontinuerlig distribution innebär möjlighet att distribuera oftare och potentiellt många gånger per dag.</span><span class="sxs-lookup"><span data-stu-id="d0de1-111">Continuous deployment means the ability to deploy frequently, potentially many times per day.</span></span>
<span data-ttu-id="d0de1-112">Syftet med dessa distributioner är inte att korrigera något, men att få något publicerade snabbt.</span><span class="sxs-lookup"><span data-stu-id="d0de1-112">The purpose of these deployments are not to fix something but to get something published quickly.</span></span>
<span data-ttu-id="d0de1-113">Genom att hämta nya funktioner via utveckling i drift som smidigt och på ett tillförlitligt sätt som möjligt, minska tiden till värde av nya affärslogik.</span><span class="sxs-lookup"><span data-stu-id="d0de1-113">By getting new features through development into operation as smoothly and reliably as possible, you reduce time-to-value of new business logic.</span></span>

<span data-ttu-id="d0de1-114">Övergången molnbaserad databehandling innebär en distributionslösning som använder en ”mall”-modell, där en end tillstånd miljö deklarerats som text och publiceras på en motor för distribution.</span><span class="sxs-lookup"><span data-stu-id="d0de1-114">The move towards cloud computing implies a deployment solution that utilizes a "declarative" template model, where an end state environment is declared as text and published to a deployment engine.</span></span>
<span data-ttu-id="d0de1-115">Den här distributionen tekniken kan snabba förändringar i skala, med flexibilitet mot risken för fel eftersom när som helst distributionen kan upprepas konsekvent för att garantera ett sluttillstånd.</span><span class="sxs-lookup"><span data-stu-id="d0de1-115">This deployment technique allows for rapid change, at scale, with resilience against threat of failure because at any time the deployment can be consistently repeated to guarantee an end state.</span></span>
<span data-ttu-id="d0de1-116">Skapandet av verktyg och tjänster som stöder den här typen av åtgärder via automation är ett svar på dessa ändringar.</span><span class="sxs-lookup"><span data-stu-id="d0de1-116">The creation of tools and services that support this style of operations through automation is a response to these changes.</span></span>

<span data-ttu-id="d0de1-117">DSC är en plattform som ger deklarativ och idempotenta (upprepningsbara) distribution-, konfigurations- och efterlevnadsstatus.</span><span class="sxs-lookup"><span data-stu-id="d0de1-117">DSC is a platform that provides declarative and idempotent (repeatable) deployment, configuration and conformance.</span></span>
<span data-ttu-id="d0de1-118">DSC-plattformen gör det möjligt för dig att se till att komponenterna i ditt datacenter har rätt konfiguration, som undviker fel och förhindrar kostsamma distributionsfel.</span><span class="sxs-lookup"><span data-stu-id="d0de1-118">The DSC platform enables you to ensure that the components of your data center have the correct configuration, which avoids errors and prevents costly deployment failures.</span></span>
<span data-ttu-id="d0de1-119">DSC möjliggör kontinuerlig distribution genom att behandla DSC-konfigurationer som en del av programkoden.</span><span class="sxs-lookup"><span data-stu-id="d0de1-119">By treating DSC configurations as part of application code, DSC enables continuous deployment.</span></span>
<span data-ttu-id="d0de1-120">DSC-konfigurationen ska uppdateras som en del av programmet, se till att den kunskap som krävs för att distribuera programmet alltid är uppdaterade och redo att användas.</span><span class="sxs-lookup"><span data-stu-id="d0de1-120">The DSC configuration should be updated as a part of the application, ensuring that the knowledge needed to deploy the application is always up-to-date and ready to be used.</span></span>

## <a name="i-have-powershell-why-do-i-need-desired-state-configuration"></a><span data-ttu-id="d0de1-121">”Jag har PowerShell, varför behöver jag Desired State Configuration”?</span><span class="sxs-lookup"><span data-stu-id="d0de1-121">"I have PowerShell, why do I need Desired State Configuration?"</span></span>

<span data-ttu-id="d0de1-122">DSC-konfigurationer separat avsikter och ”vad jag vill göra”, från körning eller ”hur jag vill göra det”.</span><span class="sxs-lookup"><span data-stu-id="d0de1-122">DSC configurations separate intent, or "what I want to do", from execution, or "how I want to do it."</span></span>
<span data-ttu-id="d0de1-123">Det innebär att logik körs finns i resurserna.</span><span class="sxs-lookup"><span data-stu-id="d0de1-123">This means the logic of execution is contained within the resources.</span></span>
<span data-ttu-id="d0de1-124">Användarna behöver inte vet hur du implementerar eller distribuera en funktion när en DSC-resurs för den funktionen är tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="d0de1-124">Users do not have to know how to implement or deploy a feature when a DSC resource for that feature is available.</span></span>
<span data-ttu-id="d0de1-125">Detta gör att användaren kan fokusera på strukturen för deras distribution.</span><span class="sxs-lookup"><span data-stu-id="d0de1-125">This allows the user to focus on the structure of their deployment.</span></span>

<span data-ttu-id="d0de1-126">Till exempel PowerShell-skript ska se ut så här:</span><span class="sxs-lookup"><span data-stu-id="d0de1-126">As an example, PowerShell scripts should look like this:</span></span>
```powershell
# Create a share in Windows Server 8
New-SmbShare -Name MyShare -Path C:\Demo\Temp -FullAccess Alice -ReadAccess Bob
```
<span data-ttu-id="d0de1-127">Det här skriptet är enkel, begripligt och enkelt.</span><span class="sxs-lookup"><span data-stu-id="d0de1-127">This script is simple, comprehensible, and straightforward.</span></span>
<span data-ttu-id="d0de1-128">Men om du placera skriptet i produktion, kör flera problem.</span><span class="sxs-lookup"><span data-stu-id="d0de1-128">However, if you try putting that script into production, you will run into several issues.</span></span>
<span data-ttu-id="d0de1-129">Vad händer om som skriptet körs två gånger i rad?</span><span class="sxs-lookup"><span data-stu-id="d0de1-129">What happens if that script is run twice in a row?</span></span>
<span data-ttu-id="d0de1-130">Vad händer om Bob tidigare hade fullständig åtkomst till resursen?</span><span class="sxs-lookup"><span data-stu-id="d0de1-130">What happens if Bob previously had Full Access to the share?</span></span>

<span data-ttu-id="d0de1-131">För att kompensera för de här problemen, ut en ”verklig” version av skriptet närmare till något som liknar:</span><span class="sxs-lookup"><span data-stu-id="d0de1-131">To compensate for these issues, a "real" version of the script will look closer to something like:</span></span>
```powershell
# But actually creating a share in an idempotent way would be

$shareExists = $false
$smbShare = Get-SmbShare -Name $Name -ErrorAction SilentlyContinue
if($smbShare -ne $null)
{
    Write-Verbose -Message "Share with name $Name exists"
    $shareExists = $true
}

if ($shareExists -eq $false)
{
    Write-Verbose "Creating share $Name to ensure it is Present"
    New-SmbShare @psboundparameters
}
else
{
    # Need to call either Set-SmbShare or *ShareAccess cmdlets
    if ($psboundparameters.ContainsKey("ChangeAccess"))
    {
       #...etc, etc, etc
    }
}
```

<span data-ttu-id="d0de1-132">Det här skriptet är mer komplex, med mycket logik och felhantering.</span><span class="sxs-lookup"><span data-stu-id="d0de1-132">This script is more complex, with plenty of logic and error handling.</span></span>
<span data-ttu-id="d0de1-133">Skriptet är mer komplexa eftersom du inte längre om vad som du vill ha klar, men *gör så*.</span><span class="sxs-lookup"><span data-stu-id="d0de1-133">The script is more complex because you are no longer stating what you want done, but *how to do it*.</span></span>

<span data-ttu-id="d0de1-134">DSC kan du till önskad text klar och den underliggande logiken har abstraherats direkt.</span><span class="sxs-lookup"><span data-stu-id="d0de1-134">DSC allows you to say what you want done, and the underlying logic is abstracted away.</span></span>

```powershell
# A configuration is a special kind of PowerShell function
Configuration Sample_Share
{
   Import-DscResource -Module xSmbShare
   # Nodes are the endpoint we wish to configure
   # A Configuration block can have zero or more Node blocks
   Node $NodeName
   {
      # Next, specify one or more resource blocks
      # Resources are simply PowerShell modules that
      # implement the logic of "how" to execute a task
      xSmbShare MySMBShare
      {
          Ensure      = "Present"
          Name        = "MyShare"
          Path        = "C:\Demo\Temp"
          ReadAccess  = "Bob"
          FullAccess  = "Alice"
          Description = "This is an updated description for this share"
      }
   }
}
#Run the function to compile the configuration
Sample_Share
#Pass the configuration to the nodes we defined and configure them
Start-DscConfiguration Sample_Share
```

<span data-ttu-id="d0de1-135">Det här skriptet är korrekt formaterad och enkelt att läsa.</span><span class="sxs-lookup"><span data-stu-id="d0de1-135">This script is cleanly formatted and straightforward to read.</span></span>
<span data-ttu-id="d0de1-136">Logik sökvägar och felhantering finns kvar i den [resource](../resources/resources.md) implementering, men osynlig till skriptförfattaren.</span><span class="sxs-lookup"><span data-stu-id="d0de1-136">The logic paths and error handling are still present in the [resource](../resources/resources.md) implementation, but invisible to the script author.</span></span>

## <a name="separating-environment-from-structure"></a><span data-ttu-id="d0de1-137">Separera miljö från struktur</span><span class="sxs-lookup"><span data-stu-id="d0de1-137">Separating Environment from Structure</span></span>

<span data-ttu-id="d0de1-138">Ett vanligt mönster i DevOps är att ha flera miljöer för distribution.</span><span class="sxs-lookup"><span data-stu-id="d0de1-138">A common pattern in DevOps is to have multiple environments for deployment.</span></span>
<span data-ttu-id="d0de1-139">Det kan till exempel finnas en ”” utvecklingsmiljö som används för att snabbt skapa prototyper ny kod.</span><span class="sxs-lookup"><span data-stu-id="d0de1-139">For example, there might be a "dev" environment used to quickly prototype new code.</span></span>
<span data-ttu-id="d0de1-140">Koden från ”utvecklingsmiljö” hamnar i en miljö med ”test”, där andra verifiera de nya funktionerna.</span><span class="sxs-lookup"><span data-stu-id="d0de1-140">The code from the "dev" environment goes into a "test" environment, where other people verify the new functionality.</span></span>
<span data-ttu-id="d0de1-141">Slutligen hamnar koden i ”prod”- eller produktionsmiljön live-webbplatsen.</span><span class="sxs-lookup"><span data-stu-id="d0de1-141">Finally, the code goes into "prod", or the live site production environment.</span></span>

<span data-ttu-id="d0de1-142">DSC-konfigurationer hantera denna dev-test-prod pipeline med [konfigurationsdata](../configurations/configData.md).</span><span class="sxs-lookup"><span data-stu-id="d0de1-142">DSC configurations accommodate this dev-test-prod pipeline through the use of [configuration data](../configurations/configData.md).</span></span>
<span data-ttu-id="d0de1-143">Detta ytterligare avlägsnar skillnaden mellan struktur för konfigurationen från de noder som ska hanteras.</span><span class="sxs-lookup"><span data-stu-id="d0de1-143">This further abstracts the difference between the structure of the configuration from the nodes that are managed.</span></span>
<span data-ttu-id="d0de1-144">Du kan till exempel definiera en konfiguration som kräver en SQLServer, en IIS-server och en mellannivå-server.</span><span class="sxs-lookup"><span data-stu-id="d0de1-144">For example, you can define a configuration that requires a SQL server, an IIS server, and a middle-tier server.</span></span>
<span data-ttu-id="d0de1-145">Oavsett vilka noder får de olika delarna av den här konfigurationen kan kommer dessa tre element alltid att finnas.</span><span class="sxs-lookup"><span data-stu-id="d0de1-145">Regardless of what nodes receive the different pieces of this configuration, those three elements will always be present.</span></span>
<span data-ttu-id="d0de1-146">Du kan använda konfigurationsdata för alla tre element för samma dator för en utvecklingsmiljö, separat tre element på tre olika datorer för en testmiljö och slutligen på alla produktionsservrar prod-miljön.</span><span class="sxs-lookup"><span data-stu-id="d0de1-146">You can use configuration data to point all three elements towards the same machine for a dev environment, separate out the three elements to three different machines for a test environment, and finally towards all your production servers for the prod environment.</span></span>
<span data-ttu-id="d0de1-147">Om du vill distribuera till olika miljöer, kan du anropa **Start-DscConfiguration** med rätt konfigurationsdata för den miljö som du vill använda.</span><span class="sxs-lookup"><span data-stu-id="d0de1-147">To deploy to the different environments, you can invoke **Start-DscConfiguration** with the correct configuration data for the environment you want to target.</span></span>

## <a name="see-also"></a><span data-ttu-id="d0de1-148">Se även</span><span class="sxs-lookup"><span data-stu-id="d0de1-148">See Also</span></span>

[<span data-ttu-id="d0de1-149">Konfigurationer</span><span class="sxs-lookup"><span data-stu-id="d0de1-149">Configurations</span></span>](../configurations/configurations.md)

[<span data-ttu-id="d0de1-150">Konfigurationsdata</span><span class="sxs-lookup"><span data-stu-id="d0de1-150">Configuration Data</span></span>](../configurations/configData.md)

[<span data-ttu-id="d0de1-151">Resurser</span><span class="sxs-lookup"><span data-stu-id="d0de1-151">Resources</span></span>](../resources/resources.md)
