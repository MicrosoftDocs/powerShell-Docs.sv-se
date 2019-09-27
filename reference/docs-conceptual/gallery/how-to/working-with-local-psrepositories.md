---
ms.date: 11/06/2018
contributor: JKeithB
keywords: Galleri, PowerShell, cmdlet, psgallery, psget
title: Arbeta med lokala PSRepositories
ms.openlocfilehash: 94824ea584c097838b24c6f2cd02407b6147a781
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71328835"
---
# <a name="working-with-local-powershellget-repositories"></a><span data-ttu-id="44cfc-103">Arbeta med lokala PowerShellGet-databaser</span><span class="sxs-lookup"><span data-stu-id="44cfc-103">Working with local PowerShellGet Repositories</span></span>

<span data-ttu-id="44cfc-104">PowerShellGet-modulen stöder andra databaser än PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="44cfc-104">The PowerShellGet module support repositories other than the PowerShell Gallery.</span></span>
<span data-ttu-id="44cfc-105">Dessa cmdletar möjliggör följande scenarier:</span><span class="sxs-lookup"><span data-stu-id="44cfc-105">These cmdlets enable the following scenarios:</span></span>

- <span data-ttu-id="44cfc-106">Stöd för en betrodd, fördefinierad uppsättning PowerShell-moduler för användning i din miljö</span><span class="sxs-lookup"><span data-stu-id="44cfc-106">Support a trusted, pre-validated set of PowerShell modules for use in your environment</span></span>
- <span data-ttu-id="44cfc-107">Testa en CI/CD-pipeline som bygger PowerShell-moduler eller-skript</span><span class="sxs-lookup"><span data-stu-id="44cfc-107">Testing a CI/CD pipeline that builds PowerShell modules or scripts</span></span>
- <span data-ttu-id="44cfc-108">Leverera PowerShell-skript och moduler till system som inte har åtkomst till Internet</span><span class="sxs-lookup"><span data-stu-id="44cfc-108">Deliver PowerShell scripts and modules to systems that can't access the internet</span></span>

<span data-ttu-id="44cfc-109">Den här artikeln beskriver hur du konfigurerar en lokal PowerShell-lagringsplats.</span><span class="sxs-lookup"><span data-stu-id="44cfc-109">This article describes how to set up a local PowerShell repository.</span></span> <span data-ttu-id="44cfc-110">Artikeln beskriver också [OfflinePowerShellGetDeploy][] -modulen som är tillgänglig från PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="44cfc-110">The article also covers the [OfflinePowerShellGetDeploy][] module available from the PowerShell Gallery.</span></span> <span data-ttu-id="44cfc-111">Den här modulen innehåller cmdlets för att installera den senaste versionen av PowerShellGet i din lokala lagrings plats.</span><span class="sxs-lookup"><span data-stu-id="44cfc-111">This module contains cmdlets to install the latest version of PowerShellGet into your local repository.</span></span>

## <a name="local-repository-types"></a><span data-ttu-id="44cfc-112">Typer av lokala databaser</span><span class="sxs-lookup"><span data-stu-id="44cfc-112">Local repository types</span></span>

<span data-ttu-id="44cfc-113">Det finns två sätt att skapa en lokal PSRepository: NuGet-Server eller fil resurs.</span><span class="sxs-lookup"><span data-stu-id="44cfc-113">There are two ways to create a local PSRepository: NuGet server or file share.</span></span> <span data-ttu-id="44cfc-114">Varje typ har fördelar och nack delar:</span><span class="sxs-lookup"><span data-stu-id="44cfc-114">Each type has advantages and disadvantages:</span></span>

<span data-ttu-id="44cfc-115">NuGet-Server</span><span class="sxs-lookup"><span data-stu-id="44cfc-115">NuGet Server</span></span>

| <span data-ttu-id="44cfc-116">Fördelar</span><span class="sxs-lookup"><span data-stu-id="44cfc-116">Advantages</span></span>| <span data-ttu-id="44cfc-117">Nackdelar</span><span class="sxs-lookup"><span data-stu-id="44cfc-117">Disadvantages</span></span> |
| --- | --- |
| <span data-ttu-id="44cfc-118">Liknar PowerShellGallery-funktioner</span><span class="sxs-lookup"><span data-stu-id="44cfc-118">Closely mimics PowerShellGallery functionality</span></span> | <span data-ttu-id="44cfc-119">En app med flera nivåer kräver åtgärder som planerar &</span><span class="sxs-lookup"><span data-stu-id="44cfc-119">Multi-tier app requires operations planning & support</span></span> |
| <span data-ttu-id="44cfc-120">NuGet integreras med Visual Studio, andra verktyg</span><span class="sxs-lookup"><span data-stu-id="44cfc-120">NuGet integrates with Visual Studio, other tools</span></span> | <span data-ttu-id="44cfc-121">Autentiserings modell och NuGet Accounts Management krävs</span><span class="sxs-lookup"><span data-stu-id="44cfc-121">Authentication model and NuGet accounts management needed</span></span> |
| <span data-ttu-id="44cfc-122">NuGet stöder metadata i `.Nupkg` paket</span><span class="sxs-lookup"><span data-stu-id="44cfc-122">NuGet supports metadata in `.Nupkg` packages</span></span> | <span data-ttu-id="44cfc-123">Publicering kräver hantering av API-nyckel & underhåll</span><span class="sxs-lookup"><span data-stu-id="44cfc-123">Publishing requires API Key management & maintenance</span></span> |
| <span data-ttu-id="44cfc-124">Tillhandahåller sökning, paket administration osv.</span><span class="sxs-lookup"><span data-stu-id="44cfc-124">Provides search, package administration, etc.</span></span> | |

<span data-ttu-id="44cfc-125">Fil resurs</span><span class="sxs-lookup"><span data-stu-id="44cfc-125">File Share</span></span>

| <span data-ttu-id="44cfc-126">Fördelar</span><span class="sxs-lookup"><span data-stu-id="44cfc-126">Advantages</span></span>| <span data-ttu-id="44cfc-127">Nackdelar</span><span class="sxs-lookup"><span data-stu-id="44cfc-127">Disadvantages</span></span> |
| --- | --- |
| <span data-ttu-id="44cfc-128">Enkelt att konfigurera, säkerhetskopiera och underhålla</span><span class="sxs-lookup"><span data-stu-id="44cfc-128">Easy to set up, back up, and maintain</span></span> | <span data-ttu-id="44cfc-129">Metadata som används av PowerShellGet är inte tillgängliga</span><span class="sxs-lookup"><span data-stu-id="44cfc-129">Metadata used by PowerShellGet isn't available</span></span> |
| <span data-ttu-id="44cfc-130">Enkel säkerhets modell – användar behörigheter på resursen</span><span class="sxs-lookup"><span data-stu-id="44cfc-130">Simple security model - user permissions on the share</span></span> | <span data-ttu-id="44cfc-131">Inget användar gränssnitt utöver grundläggande fil resurs</span><span class="sxs-lookup"><span data-stu-id="44cfc-131">No UI beyond basic file share</span></span> |
| <span data-ttu-id="44cfc-132">Inga begränsningar, som att ersätta befintliga objekt</span><span class="sxs-lookup"><span data-stu-id="44cfc-132">No constraints such as replacing existing items</span></span> | <span data-ttu-id="44cfc-133">Begränsad säkerhet och ingen inspelning av vem som uppdaterar vad</span><span class="sxs-lookup"><span data-stu-id="44cfc-133">Limited security and no recording of who updates what</span></span> |

<span data-ttu-id="44cfc-134">PowerShellGet fungerar med antingen typ och har stöd för att hitta versioner och beroende installationer.</span><span class="sxs-lookup"><span data-stu-id="44cfc-134">PowerShellGet works with either type and supports locating versions and dependency installation.</span></span>
<span data-ttu-id="44cfc-135">Men vissa funktioner som fungerar för PowerShell-galleriet är inte tillgängliga för bas-NuGet-servrar eller fil resurser.</span><span class="sxs-lookup"><span data-stu-id="44cfc-135">However, some features that work for the PowerShell Gallery aren't available for base NuGet servers or file shares.</span></span>

- <span data-ttu-id="44cfc-136">Allt är ett paket – ingen differentiering av skript, moduler, DSC-resurser eller roll funktioner.</span><span class="sxs-lookup"><span data-stu-id="44cfc-136">Everything is a package - no differentiation of scripts, modules, DSC resources, or role capabilities.</span></span>
- <span data-ttu-id="44cfc-137">Fil resurs servrar kan inte se paketets metadata, inklusive taggar.</span><span class="sxs-lookup"><span data-stu-id="44cfc-137">File share servers can't see package metadata, including tags.</span></span>

## <a name="creating-a-local-repository"></a><span data-ttu-id="44cfc-138">Skapa en lokal lagrings plats</span><span class="sxs-lookup"><span data-stu-id="44cfc-138">Creating a local repository</span></span>

<span data-ttu-id="44cfc-139">I följande artikel visas stegen för att skapa en egen NuGet-Server.</span><span class="sxs-lookup"><span data-stu-id="44cfc-139">The following article lists the steps for setting up your own NuGet Server.</span></span>

- <span data-ttu-id="44cfc-140">[NuGet. Server][]</span><span class="sxs-lookup"><span data-stu-id="44cfc-140">[NuGet.Server][]</span></span>

<span data-ttu-id="44cfc-141">Följ stegen upp till punkten för att lägga till paket.</span><span class="sxs-lookup"><span data-stu-id="44cfc-141">Follow the steps up to the point of adding packages.</span></span> <span data-ttu-id="44cfc-142">Stegen för att [publicera ett paket](#publishing-to-a-local-repository) beskrivs längre fram i den här artikeln.</span><span class="sxs-lookup"><span data-stu-id="44cfc-142">The steps for [publishing a package](#publishing-to-a-local-repository) are covered later in this article.</span></span>

<span data-ttu-id="44cfc-143">Se till att användarna har behörighet att komma åt fil resursen för en fil resursbaserade lagrings plats.</span><span class="sxs-lookup"><span data-stu-id="44cfc-143">For a file share-based repository, make sure that your users have permissions to access the file share.</span></span>

## <a name="registering-a-local-repository"></a><span data-ttu-id="44cfc-144">Registrera en lokal lagrings plats</span><span class="sxs-lookup"><span data-stu-id="44cfc-144">Registering a local repository</span></span>

<span data-ttu-id="44cfc-145">Innan du kan använda en lagrings plats måste du registrera den med `Register-PSRepository` hjälp av kommandot.</span><span class="sxs-lookup"><span data-stu-id="44cfc-145">Before a repository can be used, it must be registered using the `Register-PSRepository` command.</span></span>
<span data-ttu-id="44cfc-146">I exemplen nedan är **InstallationPolicy** inställt på *betrott*, enligt det antagande att du litar på din egen lagrings plats.</span><span class="sxs-lookup"><span data-stu-id="44cfc-146">In the examples below, the **InstallationPolicy** is set to *Trusted*, on the assumption that you trust your own repository.</span></span>

```powershell
# Register a NuGet-based server
Register-PSRepository -Name LocalPSRepo -SourceLocation http://MyLocalNuget/Api/V2/ -ScriptSourceLocation http://MyLocalNuget/Api/V2 -InstallationPolicy Trusted

# Register a file share on my local machine
Register-PSRepository -Name LocalPSRepo -SourceLocation '\\localhost\PSRepoLocal\' -ScriptSourceLocation '\\localhost\PSRepoLocal\' -InstallationPolicy Trusted
```

<span data-ttu-id="44cfc-147">Anteckna skillnaden mellan de två kommandona som hanterar **ScriptSourceLocation**.</span><span class="sxs-lookup"><span data-stu-id="44cfc-147">Take note of the difference between how the two commands handle **ScriptSourceLocation**.</span></span> <span data-ttu-id="44cfc-148">För en fil resursbaserade databaser måste **SourceLocation** och **ScriptSourceLocation** matcha.</span><span class="sxs-lookup"><span data-stu-id="44cfc-148">For a file share-based repositories, the **SourceLocation** and **ScriptSourceLocation** must match.</span></span> <span data-ttu-id="44cfc-149">För en webbaserad lagrings plats måste de vara olika, så i det här exemplet läggs ett efterföljande "/" till i **SourceLocation**.</span><span class="sxs-lookup"><span data-stu-id="44cfc-149">For a web-based repository, they must be different, so in this example a trailing "/" is added to the **SourceLocation**.</span></span>

<span data-ttu-id="44cfc-150">Om du vill att det nyligen skapade PSRepository ska vara standard lagrings platsen måste du avregistrera alla andra PSRepositories.</span><span class="sxs-lookup"><span data-stu-id="44cfc-150">If you want the newly created PSRepository to be the default repository, you must unregister all other PSRepositories.</span></span> <span data-ttu-id="44cfc-151">Exempel:</span><span class="sxs-lookup"><span data-stu-id="44cfc-151">For example:</span></span>

```powershell
Unregister-PSRepository -Name PSGallery
```

> [!NOTE]
> <span data-ttu-id="44cfc-152">Databas namnet "PSGallery" är reserverat för användning av PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="44cfc-152">The repository name 'PSGallery' is reserved for use by the PowerShell Gallery.</span></span> <span data-ttu-id="44cfc-153">Du kan avregistrera PSGallery, men du kan inte återanvända namnet PSGallery för andra lagrings platser.</span><span class="sxs-lookup"><span data-stu-id="44cfc-153">You can unregister PSGallery, but you cannot reuse the name PSGallery for any other repository.</span></span>

<span data-ttu-id="44cfc-154">Om du behöver återställa PSGallery kör du följande kommando:</span><span class="sxs-lookup"><span data-stu-id="44cfc-154">If you need to restore the PSGallery, run the following command:</span></span>

```powershell
Register-PSRepository -Default
```

## <a name="publishing-to-a-local-repository"></a><span data-ttu-id="44cfc-155">Publicera till en lokal lagrings plats</span><span class="sxs-lookup"><span data-stu-id="44cfc-155">Publishing to a local repository</span></span>

<span data-ttu-id="44cfc-156">När du har registrerat den lokala PSRepository kan du publicera den på din lokala PSRepository.</span><span class="sxs-lookup"><span data-stu-id="44cfc-156">Once you've registered the local PSRepository, you can publish to your local PSRepository.</span></span> <span data-ttu-id="44cfc-157">Det finns två huvudsakliga publicerings scenarier: publicera en egen modul och publicera en modul från PSGallery.</span><span class="sxs-lookup"><span data-stu-id="44cfc-157">There are two main publishing scenarios: publishing your own module and publishing a module from the PSGallery.</span></span>

### <a name="publishing-a-module-you-authored"></a><span data-ttu-id="44cfc-158">Publicera en modul som du har skapat</span><span class="sxs-lookup"><span data-stu-id="44cfc-158">Publishing a module you authored</span></span>

<span data-ttu-id="44cfc-159">Använd `Publish-Module` och`Publish-Script` för att publicera modulen i din lokala PSRepository på samma sätt som du gör för PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="44cfc-159">Use `Publish-Module` and `Publish-Script` to publish your module to your local PSRepository the same way you do for the PowerShell Gallery.</span></span>

- <span data-ttu-id="44cfc-160">Ange plats för koden</span><span class="sxs-lookup"><span data-stu-id="44cfc-160">Specify the location for your code</span></span>
- <span data-ttu-id="44cfc-161">Ange en API-nyckel</span><span class="sxs-lookup"><span data-stu-id="44cfc-161">Supply an API key</span></span>
- <span data-ttu-id="44cfc-162">Ange namnet på databasen.</span><span class="sxs-lookup"><span data-stu-id="44cfc-162">Specify the repository name.</span></span> <span data-ttu-id="44cfc-163">Till exempel, `-PSRepository LocalPSRepo`</span><span class="sxs-lookup"><span data-stu-id="44cfc-163">For example, `-PSRepository LocalPSRepo`</span></span>

> [!NOTE]
> <span data-ttu-id="44cfc-164">Du måste skapa ett konto på NuGet-servern och sedan logga in för att generera och spara API-nyckeln.</span><span class="sxs-lookup"><span data-stu-id="44cfc-164">You must create an account in the NuGet server, then sign in to generate and save the API key.</span></span>
> <span data-ttu-id="44cfc-165">För en fil resurs använder du en icke-tom sträng för NuGetApiKey-värdet.</span><span class="sxs-lookup"><span data-stu-id="44cfc-165">For a file share, use any non-blank string for the NuGetApiKey value.</span></span>

<span data-ttu-id="44cfc-166">Exempel:</span><span class="sxs-lookup"><span data-stu-id="44cfc-166">Examples:</span></span>

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> <span data-ttu-id="44cfc-167">För att säkerställa säkerheten bör API-nycklar inte hårdkodas i skript.</span><span class="sxs-lookup"><span data-stu-id="44cfc-167">To ensure security, API keys should not be hard-coded in scripts.</span></span> <span data-ttu-id="44cfc-168">Använd ett säkert nyckel hanterings system.</span><span class="sxs-lookup"><span data-stu-id="44cfc-168">Use a secure key management system.</span></span>

### <a name="publishing-a-module-from-the-psgallery"></a><span data-ttu-id="44cfc-169">Publicera en modul från PSGallery</span><span class="sxs-lookup"><span data-stu-id="44cfc-169">Publishing a module from the PSGallery</span></span>

<span data-ttu-id="44cfc-170">Om du vill publicera en modul från PSGallery till din lokala PSRepository kan du använda cmdleten "Save-Package".</span><span class="sxs-lookup"><span data-stu-id="44cfc-170">To publish a module from the PSGallery to your local PSRepository, you can use the 'Save-Package' cmdlet.</span></span>

- <span data-ttu-id="44cfc-171">Ange paketets namn</span><span class="sxs-lookup"><span data-stu-id="44cfc-171">Specify the Name of the Package</span></span>
- <span data-ttu-id="44cfc-172">Ange "NuGet" som Provider</span><span class="sxs-lookup"><span data-stu-id="44cfc-172">Specify 'NuGet' as the Provider</span></span>
- <span data-ttu-id="44cfc-173">Ange PSGallery-platsen som källa (https://www.powershellgallery.com/api/v2)</span><span class="sxs-lookup"><span data-stu-id="44cfc-173">Specify the PSGallery location as the source (https://www.powershellgallery.com/api/v2)</span></span>
- <span data-ttu-id="44cfc-174">Ange sökvägen till din lokala lagrings plats</span><span class="sxs-lookup"><span data-stu-id="44cfc-174">Specify the path to your local Repository</span></span>

<span data-ttu-id="44cfc-175">Exempel:</span><span class="sxs-lookup"><span data-stu-id="44cfc-175">Example:</span></span>

```powershell
# Publish from the PSGallery to your local Repository
Save-Package -Name 'PackageName' -Provider Nuget -Source https://www.powershellgallery.com/api/v2 -Path '\\localhost\PSRepoLocal\'
```

<span data-ttu-id="44cfc-176">Om din lokala PSRepository är webbaserad kräver det ytterligare ett steg som använder NuGet. exe för att publicera.</span><span class="sxs-lookup"><span data-stu-id="44cfc-176">If your local PSRepository is web-based, it requires an additional step that uses nuget.exe to publish.</span></span>

<span data-ttu-id="44cfc-177">Se dokumentationen för att använda [NuGet. exe][].</span><span class="sxs-lookup"><span data-stu-id="44cfc-177">See the documentation for using [nuget.exe][].</span></span>

## <a name="installing-powershellget-on-a-disconnected-system"></a><span data-ttu-id="44cfc-178">Installera PowerShellGet på ett frånkopplat system</span><span class="sxs-lookup"><span data-stu-id="44cfc-178">Installing PowerShellGet on a disconnected system</span></span>

<span data-ttu-id="44cfc-179">Det är svårt att distribuera PowerShellGet i miljöer som kräver att system kopplas från Internet.</span><span class="sxs-lookup"><span data-stu-id="44cfc-179">Deploying PowerShellGet is difficult in environments that require systems to be disconnected from the internet.</span></span> <span data-ttu-id="44cfc-180">PowerShellGet har en start process som installerar den senaste versionen första gången den används.</span><span class="sxs-lookup"><span data-stu-id="44cfc-180">PowerShellGet has a bootstrap process that installs the latest version the first time it's used.</span></span> <span data-ttu-id="44cfc-181">OfflinePowerShellGetDeploy-modulen i PowerShell-galleriet tillhandahåller cmdlets som stöder den här start processen.</span><span class="sxs-lookup"><span data-stu-id="44cfc-181">The OfflinePowerShellGetDeploy module in the PowerShell Gallery provides cmdlets that support this bootstrap process.</span></span>

<span data-ttu-id="44cfc-182">Om du vill starta en offline-distribution måste du:</span><span class="sxs-lookup"><span data-stu-id="44cfc-182">To bootstrap an offline deployment, you need to:</span></span>

- <span data-ttu-id="44cfc-183">Hämta och installera OfflinePowerShellGetDeploy-datorn och dina frånkopplade system</span><span class="sxs-lookup"><span data-stu-id="44cfc-183">Download and install the OfflinePowerShellGetDeploy your internet-connected system and your disconnected systems</span></span>
- <span data-ttu-id="44cfc-184">Ladda ned PowerShellGet och dess beroenden på det Internet-anslutna systemet `Save-PowerShellGetForOffline` med cmdleten</span><span class="sxs-lookup"><span data-stu-id="44cfc-184">Download PowerShellGet and its dependencies on the internet-connected system using the `Save-PowerShellGetForOffline` cmdlet</span></span>
- <span data-ttu-id="44cfc-185">Kopiera PowerShellGet och dess beroenden från det Internet-anslutna systemet till det frånkopplade systemet</span><span class="sxs-lookup"><span data-stu-id="44cfc-185">Copy PowerShellGet and its dependencies from the internet-connected system to the disconnected system</span></span>
- <span data-ttu-id="44cfc-186">`Install-PowerShellGetOffline` Använd på det frånkopplade systemet för att placera PowerShellGet och dess beroenden i rätt mappar</span><span class="sxs-lookup"><span data-stu-id="44cfc-186">Use the `Install-PowerShellGetOffline` on the disconnected system to place PowerShellGet and its dependencies into the proper folders</span></span>

<span data-ttu-id="44cfc-187">Följande kommandon används `Save-PowerShellGetForOffline` för att skicka alla komponenter till en mapp`f:\OfflinePowerShellGet`</span><span class="sxs-lookup"><span data-stu-id="44cfc-187">The following commands use `Save-PowerShellGetForOffline` to put all the components into a folder `f:\OfflinePowerShellGet`</span></span>

```powershell
# Requires -RunAsAdministrator
#Download the OfflinePowerShellGetDeploy to a location that can be accessed
# by both the connected and disconnected systems.
Save-Module -Name OfflinePowerShellGetDeploy -Path 'F:\' -Repository PSGallery
Import-Module F:\OfflinePowerShellGetDeploy

# Put PowerShellGet somewhere locally
Save-PowerShellGetForOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

<span data-ttu-id="44cfc-188">I det här läget måste du göra innehållet `F:\OfflinePowerShellGet` tillgängligt för de frånkopplade systemen.</span><span class="sxs-lookup"><span data-stu-id="44cfc-188">At this point, you must make the contents of `F:\OfflinePowerShellGet` available to your disconnected systems.</span></span> <span data-ttu-id="44cfc-189">`Install-PowerShellGetOffline` Kör cmdleten för att installera PowerShellGet på det frånkopplade systemet.</span><span class="sxs-lookup"><span data-stu-id="44cfc-189">Run the `Install-PowerShellGetOffline` cmdlet to install PowerShellGet on the disconnected system.</span></span>

> [!NOTE]
> <span data-ttu-id="44cfc-190">Det är viktigt att du inte kör PowerShellGet i PowerShell-sessionen innan du kör de här kommandona.</span><span class="sxs-lookup"><span data-stu-id="44cfc-190">It is important that you do not run PowerShellGet in the PowerShell session before running these commands.</span></span> <span data-ttu-id="44cfc-191">När PowerShellGet har lästs in i sessionen går det inte att uppdatera komponenterna.</span><span class="sxs-lookup"><span data-stu-id="44cfc-191">Once PowerShellGet is loaded into the session, the components cannot be updated.</span></span> <span data-ttu-id="44cfc-192">Om du startar PowerShellGet av misstag, avslutar du och startar om PowerShell.</span><span class="sxs-lookup"><span data-stu-id="44cfc-192">If you do start PowerShellGet by mistake, exit and restart PowerShell.</span></span>

```powershell
Import-Module F:\OfflinePowerShellGetDeploy

Install-PowerShellGetOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

<span data-ttu-id="44cfc-193">När du har kört dessa kommandon är du redo att publicera PowerShellGet till din lokala lagrings plats.</span><span class="sxs-lookup"><span data-stu-id="44cfc-193">After running these commands, you are ready to publish PowerShellGet to your local repository.</span></span>

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'F:\OfflinePowershellGet' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'F:\OfflinePowerShellGet' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> <span data-ttu-id="44cfc-194">För att säkerställa säkerheten bör API-nycklar inte hårdkodas i skript.</span><span class="sxs-lookup"><span data-stu-id="44cfc-194">To ensure security, API keys should not be hard-coded in scripts.</span></span> <span data-ttu-id="44cfc-195">Använd ett säkert nyckel hanterings system.</span><span class="sxs-lookup"><span data-stu-id="44cfc-195">Use a secure key management system.</span></span>

<!-- external links -->
[OfflinePowerShellGetDeploy]: https://www.powershellgallery.com/packages/OfflinePowerShellGetDeploy/0.1.1
[NuGet. Server]: /nuget/hosting-packages/nuget-server
[Nuget.Server]: /nuget/hosting-packages/nuget-server
[NuGet. exe]: /nuget/tools/nuget-exe-cli-reference
[nuget.exe]: /nuget/tools/nuget-exe-cli-reference
