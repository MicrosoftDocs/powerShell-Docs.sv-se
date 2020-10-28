---
ms.date: 10/13/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Desired State Configuration-översikt för tekniker
description: Det här dokumentet är avsett för utvecklare och drifts team för att förstå fördelarna med PowerShell-tjänsten för önskad tillstånds konfiguration (DSC).
ms.openlocfilehash: c98295d0e78f4dc89e5df429e3c1de9a0c024054
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92646940"
---
# <a name="desired-state-configuration-overview-for-engineers"></a><span data-ttu-id="10eaf-104">Desired State Configuration-översikt för tekniker</span><span class="sxs-lookup"><span data-stu-id="10eaf-104">Desired State Configuration Overview for Engineers</span></span>

<span data-ttu-id="10eaf-105">Det här dokumentet är avsett för utvecklare och drifts team för att förstå fördelarna med PowerShell-tjänsten för önskad tillstånds konfiguration (DSC).</span><span class="sxs-lookup"><span data-stu-id="10eaf-105">This document is intended for developer and operations teams to understand the benefits of PowerShell Desired State Configuration (DSC).</span></span> <span data-ttu-id="10eaf-106">Om du vill visa en högre nivå av värdet DSC kan du läsa [Översikt över önskad tillstånds konfiguration för besluts fattare](decisionMaker.md)</span><span class="sxs-lookup"><span data-stu-id="10eaf-106">For a higher level view of the value DSC provides, please see [Desired State Configuration Overview for Decision Makers](decisionMaker.md)</span></span>

## <a name="benefits-of-desired-state-configuration"></a><span data-ttu-id="10eaf-107">Fördelar med önskad tillstånds konfiguration</span><span class="sxs-lookup"><span data-stu-id="10eaf-107">Benefits of Desired State Configuration</span></span>

<span data-ttu-id="10eaf-108">DSC finns för att:</span><span class="sxs-lookup"><span data-stu-id="10eaf-108">DSC exists to:</span></span>

- <span data-ttu-id="10eaf-109">Minska komplexiteten i skript i Windows</span><span class="sxs-lookup"><span data-stu-id="10eaf-109">Decrease the complexity of scripting in Windows</span></span>
- <span data-ttu-id="10eaf-110">Öka upprepnings hastigheten</span><span class="sxs-lookup"><span data-stu-id="10eaf-110">Increase the speed of iteration</span></span>

<span data-ttu-id="10eaf-111">Begreppet "kontinuerlig distribution" blir viktigare.</span><span class="sxs-lookup"><span data-stu-id="10eaf-111">The concept of "continuous deployment" is becoming more important.</span></span> <span data-ttu-id="10eaf-112">Kontinuerlig distribution innebär att du kan distribuera oftare, potentiellt många gånger per dag.</span><span class="sxs-lookup"><span data-stu-id="10eaf-112">Continuous deployment means the ability to deploy frequently, potentially many times per day.</span></span> <span data-ttu-id="10eaf-113">Syftet med dessa distributioner är inte att åtgärda något men för att få något publicerat snabbt.</span><span class="sxs-lookup"><span data-stu-id="10eaf-113">The purpose of these deployments are not to fix something but to get something published quickly.</span></span> <span data-ttu-id="10eaf-114">Genom att få nya funktioner genom utveckling i drift så smidigt och tillförlitligt som möjligt minskar du tiden till värde för nya affärs logik.</span><span class="sxs-lookup"><span data-stu-id="10eaf-114">By getting new features through development into operation as smoothly and reliably as possible, you reduce time-to-value of new business logic.</span></span>

<span data-ttu-id="10eaf-115">Flytten till molnbaserad data behandling innebär en distributions lösning som använder en "deklarativ" mall modell, där en slut tillstånds miljö deklareras som text och publiceras till en distributions motor.</span><span class="sxs-lookup"><span data-stu-id="10eaf-115">The move towards cloud computing implies a deployment solution that utilizes a "declarative" template model, where an end state environment is declared as text and published to a deployment engine.</span></span> <span data-ttu-id="10eaf-116">Med den här distributions tekniken kan du snabbt ändra i skala, med återhämtning mot hot om felet, eftersom distributionen kan upprepas kontinuerligt för att garantera ett slut tillstånd.</span><span class="sxs-lookup"><span data-stu-id="10eaf-116">This deployment technique allows for rapid change, at scale, with resilience against threat of failure because at any time the deployment can be consistently repeated to guarantee an end state.</span></span> <span data-ttu-id="10eaf-117">Att skapa verktyg och tjänster som har stöd för den här typen av åtgärder via automatisering är ett svar på dessa ändringar.</span><span class="sxs-lookup"><span data-stu-id="10eaf-117">The creation of tools and services that support this style of operations through automation is a response to these changes.</span></span>

<span data-ttu-id="10eaf-118">DSC är en plattform som tillhandahåller deklarativ och idempotenta (repeterbart) distribution, konfiguration och överensstämmelse.</span><span class="sxs-lookup"><span data-stu-id="10eaf-118">DSC is a platform that provides declarative and idempotent (repeatable) deployment, configuration and conformance.</span></span> <span data-ttu-id="10eaf-119">DSC-plattformen gör det möjligt för dig att se till att komponenterna i data centret har rätt konfiguration, vilket undviker fel och förhindrar kostsamma distributions fel.</span><span class="sxs-lookup"><span data-stu-id="10eaf-119">The DSC platform enables you to ensure that the components of your data center have the correct configuration, which avoids errors and prevents costly deployment failures.</span></span> <span data-ttu-id="10eaf-120">Genom att behandla DSC-konfigurationer som en del av program koden, aktiverar DSC kontinuerlig distribution.</span><span class="sxs-lookup"><span data-stu-id="10eaf-120">By treating DSC configurations as part of application code, DSC enables continuous deployment.</span></span> <span data-ttu-id="10eaf-121">DSC-konfigurationen bör uppdateras som en del av programmet, vilket säkerställer att den kunskap som krävs för att distribuera programmet alltid är uppdaterad och redo att användas.</span><span class="sxs-lookup"><span data-stu-id="10eaf-121">The DSC configuration should be updated as a part of the application, ensuring that the knowledge needed to deploy the application is always up-to-date and ready to be used.</span></span>

## <a name="i-have-powershell-why-do-i-need-desired-state-configuration"></a><span data-ttu-id="10eaf-122">"Jag har PowerShell, varför behöver jag önskad tillstånds konfiguration?"</span><span class="sxs-lookup"><span data-stu-id="10eaf-122">"I have PowerShell, why do I need Desired State Configuration?"</span></span>

<span data-ttu-id="10eaf-123">DSC-konfigurationer, separata avsikter, eller "vad jag vill göra", från körning eller "hur jag vill göra det".</span><span class="sxs-lookup"><span data-stu-id="10eaf-123">DSC configurations separate intent, or "what I want to do", from execution, or "how I want to do it."</span></span> <span data-ttu-id="10eaf-124">Det innebär att logiken för körningen ingår i resurserna.</span><span class="sxs-lookup"><span data-stu-id="10eaf-124">This means the logic of execution is contained within the resources.</span></span> <span data-ttu-id="10eaf-125">Användarna behöver inte veta hur de ska implementera eller distribuera en funktion när en DSC-resurs för den funktionen är tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="10eaf-125">Users do not have to know how to implement or deploy a feature when a DSC resource for that feature is available.</span></span> <span data-ttu-id="10eaf-126">Detta gör att användaren kan fokusera på strukturen i distributionen.</span><span class="sxs-lookup"><span data-stu-id="10eaf-126">This allows the user to focus on the structure of their deployment.</span></span>

<span data-ttu-id="10eaf-127">Som exempel bör PowerShell-skript se ut så här:</span><span class="sxs-lookup"><span data-stu-id="10eaf-127">As an example, PowerShell scripts should look like this:</span></span>

```powershell
# Create a share in Windows Server 8
New-SmbShare -Name MyShare -Path C:\Demo\Temp -FullAccess Alice -ReadAccess Bob
```

<span data-ttu-id="10eaf-128">Det här skriptet är enkelt, begripligt och enkelt.</span><span class="sxs-lookup"><span data-stu-id="10eaf-128">This script is simple, comprehensible, and straightforward.</span></span> <span data-ttu-id="10eaf-129">Men om du försöker sätta skriptet i produktion, kan du köra på flera problem.</span><span class="sxs-lookup"><span data-stu-id="10eaf-129">However, if you try putting that script into production, you will run into several issues.</span></span> <span data-ttu-id="10eaf-130">Vad händer om skriptet körs två gånger i rad?</span><span class="sxs-lookup"><span data-stu-id="10eaf-130">What happens if that script is run twice in a row?</span></span> <span data-ttu-id="10eaf-131">Vad händer om Bob tidigare hade fullständig åtkomst till resursen?</span><span class="sxs-lookup"><span data-stu-id="10eaf-131">What happens if Bob previously had Full Access to the share?</span></span>

<span data-ttu-id="10eaf-132">För att kompensera för de här problemen ser en "verklig" version av skriptet att se ut ungefär så här:</span><span class="sxs-lookup"><span data-stu-id="10eaf-132">To compensate for these issues, a "real" version of the script will look closer to something like:</span></span>

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
    New-SmbShare @PSBoundParameters
}
else
{
    # Need to call either Set-SmbShare or *ShareAccess cmdlets
    if ($PSBoundParameters.ContainsKey("ChangeAccess"))
    {
       #...etc, etc, etc
    }
}
```

<span data-ttu-id="10eaf-133">Det här skriptet är mer komplicerat, med massor av logik-och fel hantering.</span><span class="sxs-lookup"><span data-stu-id="10eaf-133">This script is more complex, with plenty of logic and error handling.</span></span> <span data-ttu-id="10eaf-134">Skriptet är mer komplicerat eftersom du inte längre anger vad du vill göra, men _hur du gör det_ .</span><span class="sxs-lookup"><span data-stu-id="10eaf-134">The script is more complex because you are no longer stating what you want done, but _how to do it_ .</span></span>

<span data-ttu-id="10eaf-135">DSC låter dig säga vad du vill göra och den underliggande logiken är indelad.</span><span class="sxs-lookup"><span data-stu-id="10eaf-135">DSC allows you to say what you want done, and the underlying logic is abstracted away.</span></span>

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

<span data-ttu-id="10eaf-136">Det här skriptet är rent formaterat och enkelt att läsa.</span><span class="sxs-lookup"><span data-stu-id="10eaf-136">This script is cleanly formatted and straightforward to read.</span></span>
<span data-ttu-id="10eaf-137">Logik Sök vägar och fel hantering finns kvar i [resurs](../resources/resources.md) implementeringen, men är osynliga för skript författaren.</span><span class="sxs-lookup"><span data-stu-id="10eaf-137">The logic paths and error handling are still present in the [resource](../resources/resources.md) implementation, but invisible to the script author.</span></span>

## <a name="separating-environment-from-structure"></a><span data-ttu-id="10eaf-138">Separera miljö från struktur</span><span class="sxs-lookup"><span data-stu-id="10eaf-138">Separating Environment from Structure</span></span>

<span data-ttu-id="10eaf-139">Ett vanligt mönster i DevOps är att ha flera miljöer för distribution.</span><span class="sxs-lookup"><span data-stu-id="10eaf-139">A common pattern in DevOps is to have multiple environments for deployment.</span></span> <span data-ttu-id="10eaf-140">Det kan till exempel finnas en "dev"-miljö som används för att snabbt kunna prototypa ny kod.</span><span class="sxs-lookup"><span data-stu-id="10eaf-140">For example, there might be a "dev" environment used to quickly prototype new code.</span></span> <span data-ttu-id="10eaf-141">Koden från "dev"-miljön hamnar i en test miljö där andra personer verifierar de nya funktionerna.</span><span class="sxs-lookup"><span data-stu-id="10eaf-141">The code from the "dev" environment goes into a "test" environment, where other people verify the new functionality.</span></span> <span data-ttu-id="10eaf-142">Slutligen hamnar koden i "Prod" eller The Live site Production Environment.</span><span class="sxs-lookup"><span data-stu-id="10eaf-142">Finally, the code goes into "prod", or the live site production environment.</span></span>

<span data-ttu-id="10eaf-143">DSC-konfigurationer hanterar den här dev-test-Prod-pipeline genom att använda [konfigurations data](../configurations/configData.md).</span><span class="sxs-lookup"><span data-stu-id="10eaf-143">DSC configurations accommodate this dev-test-prod pipeline through the use of [configuration data](../configurations/configData.md).</span></span>
<span data-ttu-id="10eaf-144">Detta sammanfattar skillnaden mellan konfigurationens struktur och de noder som hanteras.</span><span class="sxs-lookup"><span data-stu-id="10eaf-144">This further abstracts the difference between the structure of the configuration from the nodes that are managed.</span></span> <span data-ttu-id="10eaf-145">Du kan till exempel definiera en konfiguration som kräver en SQL-Server, en IIS-server och en server på mellan nivå.</span><span class="sxs-lookup"><span data-stu-id="10eaf-145">For example, you can define a configuration that requires a SQL server, an IIS server, and a middle-tier server.</span></span> <span data-ttu-id="10eaf-146">Oavsett vilka noder som tar emot olika delar av den här konfigurationen, kommer dessa tre element alltid att finnas.</span><span class="sxs-lookup"><span data-stu-id="10eaf-146">Regardless of what nodes receive the different pieces of this configuration, those three elements will always be present.</span></span> <span data-ttu-id="10eaf-147">Du kan använda konfigurations data för att peka alla tre element mot samma dator för en utvecklings miljö, separera de tre elementen till tre olika datorer för en test miljö och slutligen till alla produktions servrar för produktions miljön.</span><span class="sxs-lookup"><span data-stu-id="10eaf-147">You can use configuration data to point all three elements towards the same machine for a dev environment, separate out the three elements to three different machines for a test environment, and finally towards all your production servers for the prod environment.</span></span> <span data-ttu-id="10eaf-148">Om du vill distribuera till olika miljöer kan du anropa `Start-DscConfiguration` med rätt konfigurations data för den miljö som du vill använda som mål.</span><span class="sxs-lookup"><span data-stu-id="10eaf-148">To deploy to the different environments, you can invoke `Start-DscConfiguration` with the correct configuration data for the environment you want to target.</span></span>

## <a name="see-also"></a><span data-ttu-id="10eaf-149">Se även</span><span class="sxs-lookup"><span data-stu-id="10eaf-149">See Also</span></span>

[<span data-ttu-id="10eaf-150">Konfigurationer</span><span class="sxs-lookup"><span data-stu-id="10eaf-150">Configurations</span></span>](../configurations/configurations.md)

[<span data-ttu-id="10eaf-151">Konfigurationsdata</span><span class="sxs-lookup"><span data-stu-id="10eaf-151">Configuration Data</span></span>](../configurations/configData.md)

[<span data-ttu-id="10eaf-152">Resurser</span><span class="sxs-lookup"><span data-stu-id="10eaf-152">Resources</span></span>](../resources/resources.md)
