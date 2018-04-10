---
ms.date: 10/13/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: Desired State Configuration-översikt för beslutsfattare
ms.openlocfilehash: 3d2d4b7e09fb699751151d7af641410bae3b38a4
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="desired-state-configuration-overview-for-engineers"></a><span data-ttu-id="2cdb2-103">Desired State Configuration-översikt för tekniker</span><span class="sxs-lookup"><span data-stu-id="2cdb2-103">Desired State Configuration Overview for Engineers</span></span>

<span data-ttu-id="2cdb2-104">Det här dokumentet är avsett för utvecklare och åtgärder team att förstå fördelarna med PowerShell önskad tillstånd Configuration DSC ().</span><span class="sxs-lookup"><span data-stu-id="2cdb2-104">This document is intended for developer and operations teams to understand the benefits of PowerShell Desired State Configuration (DSC).</span></span>
<span data-ttu-id="2cdb2-105">För en högre nivå vy av DSC-värdet innehåller finns [Desired Configuration översikt över för beslutsfattare](decisionMaker.md)</span><span class="sxs-lookup"><span data-stu-id="2cdb2-105">For a higher level view of the value DSC provides, please see [Desired State Configuration Overview for Decision Makers](decisionMaker.md)</span></span>

## <a name="benefits-of-desired-state-configuration"></a><span data-ttu-id="2cdb2-106">Fördelarna med önskad Tillståndskonfiguration</span><span class="sxs-lookup"><span data-stu-id="2cdb2-106">Benefits of Desired State Configuration</span></span>

<span data-ttu-id="2cdb2-107">DSC finns på:</span><span class="sxs-lookup"><span data-stu-id="2cdb2-107">DSC exists to:</span></span>

- <span data-ttu-id="2cdb2-108">Minska komplexiteten över skript i Windows</span><span class="sxs-lookup"><span data-stu-id="2cdb2-108">Decrease the complexity of scripting in Windows</span></span>
- <span data-ttu-id="2cdb2-109">Öka hastigheten för upprepning</span><span class="sxs-lookup"><span data-stu-id="2cdb2-109">Increase the speed of iteration</span></span>

<span data-ttu-id="2cdb2-110">Begreppet ”kontinuerlig distribution” har blivit viktigare.</span><span class="sxs-lookup"><span data-stu-id="2cdb2-110">The concept of "continuous deployment" is becoming more important.</span></span>
<span data-ttu-id="2cdb2-111">Kontinuerlig distribution innebär möjlighet att distribuera ofta, kan vara för många gånger per dag.</span><span class="sxs-lookup"><span data-stu-id="2cdb2-111">Continuous deployment means the ability to deploy frequently, potentially many times per day.</span></span>
<span data-ttu-id="2cdb2-112">Syftet med dessa distributioner är inte att fastställa något utan att hämta något publicerade snabbt.</span><span class="sxs-lookup"><span data-stu-id="2cdb2-112">The purpose of these deployments are not to fix something but to get something published quickly.</span></span>
<span data-ttu-id="2cdb2-113">Genom att hämta nya funktioner via utveckling i drift så smidigt och på ett tillförlitligt sätt som möjligt, minska tid-värde för affärslogik på nytt.</span><span class="sxs-lookup"><span data-stu-id="2cdb2-113">By getting new features through development into operation as smoothly and reliably as possible, you reduce time-to-value of new business logic.</span></span>

<span data-ttu-id="2cdb2-114">Övergången cloud computing-lösningar innebär en distributionslösning för som använder en modell för ”deklarativ” mall, där en end tillstånd miljö har deklarerats som text och publiceras på en motor för distribution.</span><span class="sxs-lookup"><span data-stu-id="2cdb2-114">The move towards cloud computing implies a deployment solution that utilizes a "declarative" template model, where an end state environment is declared as text and published to a deployment engine.</span></span>
<span data-ttu-id="2cdb2-115">Den här distributionen tekniken ger snabb ändra, i skala, med återhämtning mot risken för fel eftersom när som helst distributionen kan konsekvent upprepas för att garantera en end-tillstånd.</span><span class="sxs-lookup"><span data-stu-id="2cdb2-115">This deployment technique allows for rapid change, at scale, with resilience against threat of failure because at any time the deployment can be consistently repeated to guarantee an end state.</span></span>
<span data-ttu-id="2cdb2-116">Verktyg och tjänster som stöder den här typen av åtgärder med hjälp av automation skapas ett svar på dessa ändringar.</span><span class="sxs-lookup"><span data-stu-id="2cdb2-116">The creation of tools and services that support this style of operations through automation is a response to these changes.</span></span>

<span data-ttu-id="2cdb2-117">DSC är en plattform som tillhandahåller deklarativ och idempotent (repeterbara) distribution, konfiguration och överensstämmelse.</span><span class="sxs-lookup"><span data-stu-id="2cdb2-117">DSC is a platform that provides declarative and idempotent (repeatable) deployment, configuration and conformance.</span></span>
<span data-ttu-id="2cdb2-118">DSC-plattformen gör det möjligt för dig att se till att komponenterna i ditt datacenter har rätt konfiguration, vilket förhindrar fel och förhindrar att kostsamma distributionsfel.</span><span class="sxs-lookup"><span data-stu-id="2cdb2-118">The DSC platform enables you to ensure that the components of your data center have the correct configuration, which avoids errors and prevents costly deployment failures.</span></span>
<span data-ttu-id="2cdb2-119">Genom att behandla DSC-konfigurationer som en del av programkoden kan DSC kontinuerlig distribution.</span><span class="sxs-lookup"><span data-stu-id="2cdb2-119">By treating DSC configurations as part of application code, DSC enables continuous deployment.</span></span>
<span data-ttu-id="2cdb2-120">DSC-konfigurationen ska uppdateras som en del av programmet, se till att informationen som krävs för att distribuera programmet alltid är uppdaterade och redo att användas.</span><span class="sxs-lookup"><span data-stu-id="2cdb2-120">The DSC configuration should be updated as a part of the application, ensuring that the knowledge needed to deploy the application is always up-to-date and ready to be used.</span></span>

## <a name="i-have-powershell-why-do-i-need-desired-state-configuration"></a><span data-ttu-id="2cdb2-121">”Jag har PowerShell, varför behöver Desired State Configuration”?</span><span class="sxs-lookup"><span data-stu-id="2cdb2-121">"I have PowerShell, why do I need Desired State Configuration?"</span></span>

<span data-ttu-id="2cdb2-122">DSC-konfigurationer separat avsikter och ”vad jag vill”, från körning eller ”hur jag vill göra det”.</span><span class="sxs-lookup"><span data-stu-id="2cdb2-122">DSC configurations separate intent, or "what I want to do", from execution, or "how I want to do it."</span></span>
<span data-ttu-id="2cdb2-123">Det innebär att logiken för körning av finns i resurserna.</span><span class="sxs-lookup"><span data-stu-id="2cdb2-123">This means the logic of execution is contained within the resources.</span></span>
<span data-ttu-id="2cdb2-124">Användare behöver inte känna till hur du implementerar eller distribuera en funktion när en DSC-resurs för funktionen är tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="2cdb2-124">Users do not have to know how to implement or deploy a feature when a DSC resource for that feature is available.</span></span>
<span data-ttu-id="2cdb2-125">Detta används att fokusera på strukturen för deras distribution.</span><span class="sxs-lookup"><span data-stu-id="2cdb2-125">This allows the user to focus on the structure of their deployment.</span></span>

<span data-ttu-id="2cdb2-126">Exempelvis PowerShell-skript ska se ut så här:</span><span class="sxs-lookup"><span data-stu-id="2cdb2-126">As an example, PowerShell scripts should look like this:</span></span>
```powershell
# Create a share in Windows Server 8
New-SmbShare -Name MyShare -Path C:\Demo\Temp -FullAccess Alice -ReadAccess Bob
```
<span data-ttu-id="2cdb2-127">Det här skriptet är enkla lättförståeliga och enkelt.</span><span class="sxs-lookup"><span data-stu-id="2cdb2-127">This script is simple, comprehensible, and straightforward.</span></span>
<span data-ttu-id="2cdb2-128">Men om du försöker att skriptet till produktion, stöter på problem med flera.</span><span class="sxs-lookup"><span data-stu-id="2cdb2-128">However, if you try putting that script into production, you will run into several issues.</span></span>
<span data-ttu-id="2cdb2-129">Vad händer om skriptet körs två gånger i rad?</span><span class="sxs-lookup"><span data-stu-id="2cdb2-129">What happens if that script is run twice in a row?</span></span>
<span data-ttu-id="2cdb2-130">Vad händer om Bob tidigare hade fullständig åtkomst till resursen?</span><span class="sxs-lookup"><span data-stu-id="2cdb2-130">What happens if Bob previously had Full Access to the share?</span></span>

<span data-ttu-id="2cdb2-131">För att kompensera för de här problemen, ser en ”verkliga” version av skriptet närmare något som liknar:</span><span class="sxs-lookup"><span data-stu-id="2cdb2-131">To compensate for these issues, a "real" version of the script will look closer to something like:</span></span>
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

<span data-ttu-id="2cdb2-132">Det här skriptet är mer komplexa, med mycket logik och felhantering.</span><span class="sxs-lookup"><span data-stu-id="2cdb2-132">This script is more complex, with plenty of logic and error handling.</span></span>
<span data-ttu-id="2cdb2-133">Skriptet är mer komplex eftersom du inte längre om vad du vill klart, men *gör du*.</span><span class="sxs-lookup"><span data-stu-id="2cdb2-133">The script is more complex because you are no longer stating what you want done, but *how to do it*.</span></span>

<span data-ttu-id="2cdb2-134">DSC kan du önskad text klart och den underliggande logiken representeras direkt.</span><span class="sxs-lookup"><span data-stu-id="2cdb2-134">DSC allows you to say what you want done, and the underlying logic is abstracted away.</span></span>

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
          ReadAccess  = "Alice"
          FullAccess  = "Bob"
          Description = "This is an updated description for this share"
      }
   }
}
#Run the function to compile the configuration
Sample_Share
#Pass the configuration to the nodes we defined and configure them
Start-DscConfiguration Sample_Share
```

<span data-ttu-id="2cdb2-135">Det här skriptet är korrekt formaterad och enkla att läsa.</span><span class="sxs-lookup"><span data-stu-id="2cdb2-135">This script is cleanly formatted and straightforward to read.</span></span>
<span data-ttu-id="2cdb2-136">Logik sökvägar och felhantering finns kvar i den [resurs](resources.md) implementeringen, men osynlig till skriptet författare.</span><span class="sxs-lookup"><span data-stu-id="2cdb2-136">The logic paths and error handling are still present in the [resource](resources.md) implementation, but invisible to the script author.</span></span>

## <a name="separating-environment-from-structure"></a><span data-ttu-id="2cdb2-137">Avgränsa miljön från struktur</span><span class="sxs-lookup"><span data-stu-id="2cdb2-137">Separating Environment from Structure</span></span>

<span data-ttu-id="2cdb2-138">Ett vanligt mönster i DevOps är att ha flera miljöer för distribution.</span><span class="sxs-lookup"><span data-stu-id="2cdb2-138">A common pattern in DevOps is to have multiple environments for deployment.</span></span>
<span data-ttu-id="2cdb2-139">Det kan till exempel finnas en ”utvecklingsmiljö”, används för att snabbt prototyp ny kod.</span><span class="sxs-lookup"><span data-stu-id="2cdb2-139">For example, there might be a "dev" environment used to quickly prototype new code.</span></span>
<span data-ttu-id="2cdb2-140">Koden från ”utvecklingsmiljö” försätts i ett ”test”-miljö där andra verifiera de nya funktionerna.</span><span class="sxs-lookup"><span data-stu-id="2cdb2-140">The code from the "dev" environment goes into a "test" environment, where other people verify the new functionality.</span></span>
<span data-ttu-id="2cdb2-141">Slutligen blir koden ”prod” eller liveplatsen produktionsmiljön.</span><span class="sxs-lookup"><span data-stu-id="2cdb2-141">Finally, the code goes into "prod", or the live site production environment.</span></span>

<span data-ttu-id="2cdb2-142">DSC-konfigurationer hantera denna dev-test-produktprenumeration pipeline med [konfigurationsdata](configData.md).</span><span class="sxs-lookup"><span data-stu-id="2cdb2-142">DSC configurations accommodate this dev-test-prod pipeline through the use of [configuration data](configData.md).</span></span>
<span data-ttu-id="2cdb2-143">Detta ytterligare avlägsnar skillnaden mellan strukturen för konfiguration av de noder som ska hanteras.</span><span class="sxs-lookup"><span data-stu-id="2cdb2-143">This further abstracts the difference between the structure of the configuration from the nodes that are managed.</span></span>
<span data-ttu-id="2cdb2-144">Du kan till exempel definiera en konfiguration som kräver en SQLServer, en IIS-server och en mellannivå-server.</span><span class="sxs-lookup"><span data-stu-id="2cdb2-144">For example, you can define a configuration that requires a SQL server, an IIS server, and a middle-tier server.</span></span>
<span data-ttu-id="2cdb2-145">Oavsett vilka noder får olika delar av den här konfigurationen, är dessa tre element alltid tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="2cdb2-145">Regardless of what nodes receive the different pieces of this configuration, those three elements will always be present.</span></span>
<span data-ttu-id="2cdb2-146">Du kan använda konfigurationsdata för alla tre element för samma dator för en utvecklingsmiljö separat av tre element till tre olika datorer för en testmiljö och slutligen mot alla produktionsservrar för prod-miljö.</span><span class="sxs-lookup"><span data-stu-id="2cdb2-146">You can use configuration data to point all three elements towards the same machine for a dev environment, separate out the three elements to three different machines for a test environment, and finally towards all your production servers for the prod environment.</span></span>
<span data-ttu-id="2cdb2-147">Om du vill distribuera till olika miljöer, kan du anropa **Start DscConfiguration** med rätt konfigurationsdata för den miljö du vill använda som mål.</span><span class="sxs-lookup"><span data-stu-id="2cdb2-147">To deploy to the different environments, you can invoke **Start-DscConfiguration** with the correct configuration data for the environment you want to target.</span></span>

## <a name="see-also"></a><span data-ttu-id="2cdb2-148">Se även</span><span class="sxs-lookup"><span data-stu-id="2cdb2-148">See Also</span></span>

[<span data-ttu-id="2cdb2-149">Konfigurationer</span><span class="sxs-lookup"><span data-stu-id="2cdb2-149">Configurations</span></span>](configurations.md)

[<span data-ttu-id="2cdb2-150">Konfigurationsdata</span><span class="sxs-lookup"><span data-stu-id="2cdb2-150">Configuration Data</span></span>](configData.md)

[<span data-ttu-id="2cdb2-151">Resurser</span><span class="sxs-lookup"><span data-stu-id="2cdb2-151">Resources</span></span>](resources.md)