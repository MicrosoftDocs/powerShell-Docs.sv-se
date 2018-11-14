---
ms.date: 11/06/2018
contributor: JKeithB
keywords: galleriet, powershell, cmdlet, psgallery, psget
title: Arbeta med lokala PSRepositories
ms.openlocfilehash: 94824ea584c097838b24c6f2cd02407b6147a781
ms.sourcegitcommit: 91786b03704fbd2d185f674df0bc67faddfb6288
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/14/2018
ms.locfileid: "51619267"
---
# <a name="working-with-local-powershellget-repositories"></a><span data-ttu-id="f11f0-103">Arbeta med lokala PowerShellGet-databaser</span><span class="sxs-lookup"><span data-stu-id="f11f0-103">Working with local PowerShellGet Repositories</span></span>

<span data-ttu-id="f11f0-104">PowerShellGet-modul support lagringsplatser än PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="f11f0-104">The PowerShellGet module support repositories other than the PowerShell Gallery.</span></span>
<span data-ttu-id="f11f0-105">Dessa cmdletar aktivera följande scenarier:</span><span class="sxs-lookup"><span data-stu-id="f11f0-105">These cmdlets enable the following scenarios:</span></span>

- <span data-ttu-id="f11f0-106">Stöd för en betrodd, före validerade uppsättning PowerShell-moduler för användning i din miljö</span><span class="sxs-lookup"><span data-stu-id="f11f0-106">Support a trusted, pre-validated set of PowerShell modules for use in your environment</span></span>
- <span data-ttu-id="f11f0-107">Testa en CI/CD-pipeline som bygger på PowerShell-moduler eller skript</span><span class="sxs-lookup"><span data-stu-id="f11f0-107">Testing a CI/CD pipeline that builds PowerShell modules or scripts</span></span>
- <span data-ttu-id="f11f0-108">Leverera PowerShell-skript och moduler för system där det går inte att få åtkomst till internet</span><span class="sxs-lookup"><span data-stu-id="f11f0-108">Deliver PowerShell scripts and modules to systems that can't access the internet</span></span>

<span data-ttu-id="f11f0-109">Den här artikeln beskriver hur du ställer in en lokal PowerShell-lagringsplats.</span><span class="sxs-lookup"><span data-stu-id="f11f0-109">This article describes how to set up a local PowerShell repository.</span></span> <span data-ttu-id="f11f0-110">Den här artikeln beskriver också den [OfflinePowerShellGetDeploy][] modul som är tillgängliga från PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="f11f0-110">The article also covers the [OfflinePowerShellGetDeploy][] module available from the PowerShell Gallery.</span></span> <span data-ttu-id="f11f0-111">Den här modulen innehåller cmdlets för att installera den senaste versionen av PowerShellGet i din lokala lagringsplats.</span><span class="sxs-lookup"><span data-stu-id="f11f0-111">This module contains cmdlets to install the latest version of PowerShellGet into your local repository.</span></span>

## <a name="local-repository-types"></a><span data-ttu-id="f11f0-112">Lagringsplats-typer</span><span class="sxs-lookup"><span data-stu-id="f11f0-112">Local repository types</span></span>

<span data-ttu-id="f11f0-113">Det finns två sätt att skapa en lokal PSRepository: NuGet server eller filresurs.</span><span class="sxs-lookup"><span data-stu-id="f11f0-113">There are two ways to create a local PSRepository: NuGet server or file share.</span></span> <span data-ttu-id="f11f0-114">Varje typ har fördelar och nackdelar:</span><span class="sxs-lookup"><span data-stu-id="f11f0-114">Each type has advantages and disadvantages:</span></span>

<span data-ttu-id="f11f0-115">NuGet-Server</span><span class="sxs-lookup"><span data-stu-id="f11f0-115">NuGet Server</span></span>

| <span data-ttu-id="f11f0-116">Fördelar</span><span class="sxs-lookup"><span data-stu-id="f11f0-116">Advantages</span></span>| <span data-ttu-id="f11f0-117">Nackdelar</span><span class="sxs-lookup"><span data-stu-id="f11f0-117">Disadvantages</span></span> |
| --- | --- |
| <span data-ttu-id="f11f0-118">Nära efterliknar PowerShellGallery-funktioner</span><span class="sxs-lookup"><span data-stu-id="f11f0-118">Closely mimics PowerShellGallery functionality</span></span> | <span data-ttu-id="f11f0-119">Flerskiktat program kräver åtgärder planering och support</span><span class="sxs-lookup"><span data-stu-id="f11f0-119">Multi-tier app requires operations planning & support</span></span> |
| <span data-ttu-id="f11f0-120">NuGet kan integreras med andra verktyg för Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f11f0-120">NuGet integrates with Visual Studio, other tools</span></span> | <span data-ttu-id="f11f0-121">Autentisering och hantering av NuGet-konton som behövs</span><span class="sxs-lookup"><span data-stu-id="f11f0-121">Authentication model and NuGet accounts management needed</span></span> |
| <span data-ttu-id="f11f0-122">NuGet har stöd för metadata i `.Nupkg` paket</span><span class="sxs-lookup"><span data-stu-id="f11f0-122">NuGet supports metadata in `.Nupkg` packages</span></span> | <span data-ttu-id="f11f0-123">Publicering kräver att API-nyckel för hantering och underhåll</span><span class="sxs-lookup"><span data-stu-id="f11f0-123">Publishing requires API Key management & maintenance</span></span> |
| <span data-ttu-id="f11f0-124">Innehåller Sök, Paketadministration osv.</span><span class="sxs-lookup"><span data-stu-id="f11f0-124">Provides search, package administration, etc.</span></span> | |

<span data-ttu-id="f11f0-125">Filresurs</span><span class="sxs-lookup"><span data-stu-id="f11f0-125">File Share</span></span>

| <span data-ttu-id="f11f0-126">Fördelar</span><span class="sxs-lookup"><span data-stu-id="f11f0-126">Advantages</span></span>| <span data-ttu-id="f11f0-127">Nackdelar</span><span class="sxs-lookup"><span data-stu-id="f11f0-127">Disadvantages</span></span> |
| --- | --- |
| <span data-ttu-id="f11f0-128">Enkelt att ställa in, säkerhetskopiera och underhålla</span><span class="sxs-lookup"><span data-stu-id="f11f0-128">Easy to set up, back up, and maintain</span></span> | <span data-ttu-id="f11f0-129">Metadata som används av PowerShellGet är inte tillgänglig</span><span class="sxs-lookup"><span data-stu-id="f11f0-129">Metadata used by PowerShellGet isn't available</span></span> |
| <span data-ttu-id="f11f0-130">Enkel säkerhetsmodell - användarbehörigheter för resursen</span><span class="sxs-lookup"><span data-stu-id="f11f0-130">Simple security model - user permissions on the share</span></span> | <span data-ttu-id="f11f0-131">Något användargränssnitt bortom grundläggande filresurs</span><span class="sxs-lookup"><span data-stu-id="f11f0-131">No UI beyond basic file share</span></span> |
| <span data-ttu-id="f11f0-132">Utan begränsningar, till exempel ersätta befintliga objekt</span><span class="sxs-lookup"><span data-stu-id="f11f0-132">No constraints such as replacing existing items</span></span> | <span data-ttu-id="f11f0-133">Begränsad säkerhet och ingen registrering av som uppdaterar vad</span><span class="sxs-lookup"><span data-stu-id="f11f0-133">Limited security and no recording of who updates what</span></span> |

<span data-ttu-id="f11f0-134">PowerShellGet fungerar med typen och har stöd för att hitta versioner och installationen av beroenden.</span><span class="sxs-lookup"><span data-stu-id="f11f0-134">PowerShellGet works with either type and supports locating versions and dependency installation.</span></span>
<span data-ttu-id="f11f0-135">Vissa funktioner som fungerar för PowerShell-galleriet är dock inte tillgängliga för grundläggande NuGet-servrar eller filresurser.</span><span class="sxs-lookup"><span data-stu-id="f11f0-135">However, some features that work for the PowerShell Gallery aren't available for base NuGet servers or file shares.</span></span>

- <span data-ttu-id="f11f0-136">Allt är ett paket - ingen skillnad i skript, moduler, DSC-resurser eller rollfunktioner.</span><span class="sxs-lookup"><span data-stu-id="f11f0-136">Everything is a package - no differentiation of scripts, modules, DSC resources, or role capabilities.</span></span>
- <span data-ttu-id="f11f0-137">Dela filservrar kan inte se paketmetadata, inklusive taggar.</span><span class="sxs-lookup"><span data-stu-id="f11f0-137">File share servers can't see package metadata, including tags.</span></span>

## <a name="creating-a-local-repository"></a><span data-ttu-id="f11f0-138">Skapa en lokal databas</span><span class="sxs-lookup"><span data-stu-id="f11f0-138">Creating a local repository</span></span>

<span data-ttu-id="f11f0-139">I följande artikel innehåller stegen för att konfigurera din egen NuGet-Server.</span><span class="sxs-lookup"><span data-stu-id="f11f0-139">The following article lists the steps for setting up your own NuGet Server.</span></span>

- <span data-ttu-id="f11f0-140">[NuGet.Server][]</span><span class="sxs-lookup"><span data-stu-id="f11f0-140">[NuGet.Server][]</span></span>

<span data-ttu-id="f11f0-141">Följ stegen i det läget för att lägga till paket.</span><span class="sxs-lookup"><span data-stu-id="f11f0-141">Follow the steps up to the point of adding packages.</span></span> <span data-ttu-id="f11f0-142">Stegen för att [publicerar ett paket](#publishing-to-a-local-repository) beskrivs senare i den här artikeln.</span><span class="sxs-lookup"><span data-stu-id="f11f0-142">The steps for [publishing a package](#publishing-to-a-local-repository) are covered later in this article.</span></span>

<span data-ttu-id="f11f0-143">För en fil filresursbaserade lagringsplats, se till att dina användare har behörighet att komma åt filresursen.</span><span class="sxs-lookup"><span data-stu-id="f11f0-143">For a file share-based repository, make sure that your users have permissions to access the file share.</span></span>

## <a name="registering-a-local-repository"></a><span data-ttu-id="f11f0-144">Registrera en lokal databas</span><span class="sxs-lookup"><span data-stu-id="f11f0-144">Registering a local repository</span></span>

<span data-ttu-id="f11f0-145">Innan en databas kan användas, måste den vara registrerad med hjälp av den `Register-PSRepository` kommando.</span><span class="sxs-lookup"><span data-stu-id="f11f0-145">Before a repository can be used, it must be registered using the `Register-PSRepository` command.</span></span>
<span data-ttu-id="f11f0-146">I exemplen nedan, den **InstallationPolicy** är inställd på *betrodda*, på antagandet att du har förtroende för en egen databas.</span><span class="sxs-lookup"><span data-stu-id="f11f0-146">In the examples below, the **InstallationPolicy** is set to *Trusted*, on the assumption that you trust your own repository.</span></span>

```powershell
# Register a NuGet-based server
Register-PSRepository -Name LocalPSRepo -SourceLocation http://MyLocalNuget/Api/V2/ -ScriptSourceLocation http://MyLocalNuget/Api/V2 -InstallationPolicy Trusted

# Register a file share on my local machine
Register-PSRepository -Name LocalPSRepo -SourceLocation '\\localhost\PSRepoLocal\' -ScriptSourceLocation '\\localhost\PSRepoLocal\' -InstallationPolicy Trusted
```

<span data-ttu-id="f11f0-147">Anteckna skillnaden mellan hur de två kommandona hanterar **ScriptSourceLocation**.</span><span class="sxs-lookup"><span data-stu-id="f11f0-147">Take note of the difference between how the two commands handle **ScriptSourceLocation**.</span></span> <span data-ttu-id="f11f0-148">För en fil filresursbaserade lagringsplatser, den **SourceLocation** och **ScriptSourceLocation** måste matcha.</span><span class="sxs-lookup"><span data-stu-id="f11f0-148">For a file share-based repositories, the **SourceLocation** and **ScriptSourceLocation** must match.</span></span> <span data-ttu-id="f11f0-149">För en webbaserad lagringsplats, och de måste vara olika, så i det här exemplet som en avslutande ”/” har lagts till i den **SourceLocation**.</span><span class="sxs-lookup"><span data-stu-id="f11f0-149">For a web-based repository, they must be different, so in this example a trailing "/" is added to the **SourceLocation**.</span></span>

<span data-ttu-id="f11f0-150">Om du vill att den nyligen skapade PSRepository vara standard-databasen måste du avregistrera alla andra PSRepositories.</span><span class="sxs-lookup"><span data-stu-id="f11f0-150">If you want the newly created PSRepository to be the default repository, you must unregister all other PSRepositories.</span></span> <span data-ttu-id="f11f0-151">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="f11f0-151">For example:</span></span>

```powershell
Unregister-PSRepository -Name PSGallery
```

> [!NOTE]
> <span data-ttu-id="f11f0-152">Namnet på lagringsplatsen ”PSGallery” är reserverade för användning av PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="f11f0-152">The repository name 'PSGallery' is reserved for use by the PowerShell Gallery.</span></span> <span data-ttu-id="f11f0-153">Du kan avregistrera PSGallery, men du kan inte återanvända namnet PSGallery för en annan lagringsplats.</span><span class="sxs-lookup"><span data-stu-id="f11f0-153">You can unregister PSGallery, but you cannot reuse the name PSGallery for any other repository.</span></span>

<span data-ttu-id="f11f0-154">Om du vill återställa PSGallery kör du följande kommando:</span><span class="sxs-lookup"><span data-stu-id="f11f0-154">If you need to restore the PSGallery, run the following command:</span></span>

```powershell
Register-PSRepository -Default
```

## <a name="publishing-to-a-local-repository"></a><span data-ttu-id="f11f0-155">Publicering till en lokal databas</span><span class="sxs-lookup"><span data-stu-id="f11f0-155">Publishing to a local repository</span></span>

<span data-ttu-id="f11f0-156">När du har registrerat den lokala PSRepository, kan du publicera dina lokala PSRepository.</span><span class="sxs-lookup"><span data-stu-id="f11f0-156">Once you've registered the local PSRepository, you can publish to your local PSRepository.</span></span> <span data-ttu-id="f11f0-157">Det finns två huvudscenarier för publicering: publicera en egen modul och publicera en modul från PSGallery.</span><span class="sxs-lookup"><span data-stu-id="f11f0-157">There are two main publishing scenarios: publishing your own module and publishing a module from the PSGallery.</span></span>

### <a name="publishing-a-module-you-authored"></a><span data-ttu-id="f11f0-158">Publicera en modul som du skapat</span><span class="sxs-lookup"><span data-stu-id="f11f0-158">Publishing a module you authored</span></span>

<span data-ttu-id="f11f0-159">Använd `Publish-Module` och `Publish-Script` att publicera din modul till din lokala PSRepository på samma sätt som du gör med PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="f11f0-159">Use `Publish-Module` and `Publish-Script` to publish your module to your local PSRepository the same way you do for the PowerShell Gallery.</span></span>

- <span data-ttu-id="f11f0-160">Ange platsen för din kod</span><span class="sxs-lookup"><span data-stu-id="f11f0-160">Specify the location for your code</span></span>
- <span data-ttu-id="f11f0-161">Ange en API-nyckel</span><span class="sxs-lookup"><span data-stu-id="f11f0-161">Supply an API key</span></span>
- <span data-ttu-id="f11f0-162">Ange namnet på lagringsplatsen.</span><span class="sxs-lookup"><span data-stu-id="f11f0-162">Specify the repository name.</span></span> <span data-ttu-id="f11f0-163">Till exempel `-PSRepository LocalPSRepo`</span><span class="sxs-lookup"><span data-stu-id="f11f0-163">For example, `-PSRepository LocalPSRepo`</span></span>

> [!NOTE]
> <span data-ttu-id="f11f0-164">Du måste skapa ett konto på NuGet-servern och sedan logga in att generera och spara API-nyckeln.</span><span class="sxs-lookup"><span data-stu-id="f11f0-164">You must create an account in the NuGet server, then sign in to generate and save the API key.</span></span>
> <span data-ttu-id="f11f0-165">Använd alla icke-tomma strängar för NuGetApiKey värdet för en filresurs.</span><span class="sxs-lookup"><span data-stu-id="f11f0-165">For a file share, use any non-blank string for the NuGetApiKey value.</span></span>

<span data-ttu-id="f11f0-166">Exempel:</span><span class="sxs-lookup"><span data-stu-id="f11f0-166">Examples:</span></span>

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> <span data-ttu-id="f11f0-167">För att garantera säkerheten, får API-nycklar inte vara hårdkodade i skript.</span><span class="sxs-lookup"><span data-stu-id="f11f0-167">To ensure security, API keys should not be hard-coded in scripts.</span></span> <span data-ttu-id="f11f0-168">Använd en säker nyckelhanteringssystem.</span><span class="sxs-lookup"><span data-stu-id="f11f0-168">Use a secure key management system.</span></span>

### <a name="publishing-a-module-from-the-psgallery"></a><span data-ttu-id="f11f0-169">Publicera en modul från PSGallery</span><span class="sxs-lookup"><span data-stu-id="f11f0-169">Publishing a module from the PSGallery</span></span>

<span data-ttu-id="f11f0-170">Om du vill publicera en modul från PSGallery till din lokala PSRepository, kan du använda cmdleten Save-Package.</span><span class="sxs-lookup"><span data-stu-id="f11f0-170">To publish a module from the PSGallery to your local PSRepository, you can use the 'Save-Package' cmdlet.</span></span>

- <span data-ttu-id="f11f0-171">Ange namnet på paketet</span><span class="sxs-lookup"><span data-stu-id="f11f0-171">Specify the Name of the Package</span></span>
- <span data-ttu-id="f11f0-172">Ange ”NuGet-providern</span><span class="sxs-lookup"><span data-stu-id="f11f0-172">Specify 'NuGet' as the Provider</span></span>
- <span data-ttu-id="f11f0-173">Ange PSGallery platsen som källa (https://www.powershellgallery.com/api/v2)</span><span class="sxs-lookup"><span data-stu-id="f11f0-173">Specify the PSGallery location as the source (https://www.powershellgallery.com/api/v2)</span></span>
- <span data-ttu-id="f11f0-174">Ange sökvägen till din lokala lagringsplats</span><span class="sxs-lookup"><span data-stu-id="f11f0-174">Specify the path to your local Repository</span></span>

<span data-ttu-id="f11f0-175">Exempel:</span><span class="sxs-lookup"><span data-stu-id="f11f0-175">Example:</span></span>

```powershell
# Publish from the PSGallery to your local Repository
Save-Package -Name 'PackageName' -Provider Nuget -Source https://www.powershellgallery.com/api/v2 -Path '\\localhost\PSRepoLocal\'
```

<span data-ttu-id="f11f0-176">Om din lokala PSRepository är webbaserade, krävs ytterligare ett steg där nuget.exe används för att publicera.</span><span class="sxs-lookup"><span data-stu-id="f11f0-176">If your local PSRepository is web-based, it requires an additional step that uses nuget.exe to publish.</span></span>

<span data-ttu-id="f11f0-177">Finns i dokumentationen för att använda [nuget.exe][].</span><span class="sxs-lookup"><span data-stu-id="f11f0-177">See the documentation for using [nuget.exe][].</span></span>

## <a name="installing-powershellget-on-a-disconnected-system"></a><span data-ttu-id="f11f0-178">Installera PowerShellGet på en frånkopplad system</span><span class="sxs-lookup"><span data-stu-id="f11f0-178">Installing PowerShellGet on a disconnected system</span></span>

<span data-ttu-id="f11f0-179">Distribuera PowerShellGet är svårt i miljöer som kräver att vara ansluten till internet.</span><span class="sxs-lookup"><span data-stu-id="f11f0-179">Deploying PowerShellGet is difficult in environments that require systems to be disconnected from the internet.</span></span> <span data-ttu-id="f11f0-180">PowerShellGet har en bootstrap process som installerar den senaste versionen första gången den används.</span><span class="sxs-lookup"><span data-stu-id="f11f0-180">PowerShellGet has a bootstrap process that installs the latest version the first time it's used.</span></span> <span data-ttu-id="f11f0-181">Modulen OfflinePowerShellGetDeploy i PowerShell-galleriet innehåller cmdletar som stöder bootstrap processen.</span><span class="sxs-lookup"><span data-stu-id="f11f0-181">The OfflinePowerShellGetDeploy module in the PowerShell Gallery provides cmdlets that support this bootstrap process.</span></span>

<span data-ttu-id="f11f0-182">För att kunna starta en offline-distribution, måste du:</span><span class="sxs-lookup"><span data-stu-id="f11f0-182">To bootstrap an offline deployment, you need to:</span></span>

- <span data-ttu-id="f11f0-183">Hämta och installera OfflinePowerShellGetDeploy din internet-anslutna system och dina frånkopplade system</span><span class="sxs-lookup"><span data-stu-id="f11f0-183">Download and install the OfflinePowerShellGetDeploy your internet-connected system and your disconnected systems</span></span>
- <span data-ttu-id="f11f0-184">Hämta PowerShellGet och dess beroenden på internet-anslutna system med den `Save-PowerShellGetForOffline` cmdlet</span><span class="sxs-lookup"><span data-stu-id="f11f0-184">Download PowerShellGet and its dependencies on the internet-connected system using the `Save-PowerShellGetForOffline` cmdlet</span></span>
- <span data-ttu-id="f11f0-185">Kopiera PowerShellGet och dess beroenden från internet-anslutna systemet till det frånkopplade systemet</span><span class="sxs-lookup"><span data-stu-id="f11f0-185">Copy PowerShellGet and its dependencies from the internet-connected system to the disconnected system</span></span>
- <span data-ttu-id="f11f0-186">Använd den `Install-PowerShellGetOffline` på det frånkopplade systemet placera PowerShellGet och dess beroenden i rätt mappar</span><span class="sxs-lookup"><span data-stu-id="f11f0-186">Use the `Install-PowerShellGetOffline` on the disconnected system to place PowerShellGet and its dependencies into the proper folders</span></span>

<span data-ttu-id="f11f0-187">Följande kommandon används `Save-PowerShellGetForOffline` att placera alla komponenter i en mapp `f:\OfflinePowerShellGet`</span><span class="sxs-lookup"><span data-stu-id="f11f0-187">The following commands use `Save-PowerShellGetForOffline` to put all the components into a folder `f:\OfflinePowerShellGet`</span></span>

```powershell
# Requires -RunAsAdministrator
#Download the OfflinePowerShellGetDeploy to a location that can be accessed
# by both the connected and disconnected systems.
Save-Module -Name OfflinePowerShellGetDeploy -Path 'F:\' -Repository PSGallery
Import-Module F:\OfflinePowerShellGetDeploy

# Put PowerShellGet somewhere locally
Save-PowerShellGetForOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

<span data-ttu-id="f11f0-188">Nu måste du se innehållet i `F:\OfflinePowerShellGet` tillgänglig för dina frånkopplade system.</span><span class="sxs-lookup"><span data-stu-id="f11f0-188">At this point, you must make the contents of `F:\OfflinePowerShellGet` available to your disconnected systems.</span></span> <span data-ttu-id="f11f0-189">Kör den `Install-PowerShellGetOffline` cmdlet för att installera PowerShellGet på det frånkopplade systemet.</span><span class="sxs-lookup"><span data-stu-id="f11f0-189">Run the `Install-PowerShellGetOffline` cmdlet to install PowerShellGet on the disconnected system.</span></span>

> [!NOTE]
> <span data-ttu-id="f11f0-190">Det är viktigt att du inte kör PowerShellGet i PowerShell-sessionen innan du kör dessa kommandon.</span><span class="sxs-lookup"><span data-stu-id="f11f0-190">It is important that you do not run PowerShellGet in the PowerShell session before running these commands.</span></span> <span data-ttu-id="f11f0-191">När PowerShellGet har lästs in i sessionen, kan inte komponenterna uppdateras.</span><span class="sxs-lookup"><span data-stu-id="f11f0-191">Once PowerShellGet is loaded into the session, the components cannot be updated.</span></span> <span data-ttu-id="f11f0-192">Om du ska börja PowerShellGet av misstag, avsluta och starta om PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f11f0-192">If you do start PowerShellGet by mistake, exit and restart PowerShell.</span></span>

```powershell
Import-Module F:\OfflinePowerShellGetDeploy

Install-PowerShellGetOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

<span data-ttu-id="f11f0-193">När du har kört dessa kommandon är du redo att publicera PowerShellGet till din lokala lagringsplats.</span><span class="sxs-lookup"><span data-stu-id="f11f0-193">After running these commands, you are ready to publish PowerShellGet to your local repository.</span></span>

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'F:\OfflinePowershellGet' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'F:\OfflinePowerShellGet' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> <span data-ttu-id="f11f0-194">För att garantera säkerheten, får API-nycklar inte vara hårdkodade i skript.</span><span class="sxs-lookup"><span data-stu-id="f11f0-194">To ensure security, API keys should not be hard-coded in scripts.</span></span> <span data-ttu-id="f11f0-195">Använd en säker nyckelhanteringssystem.</span><span class="sxs-lookup"><span data-stu-id="f11f0-195">Use a secure key management system.</span></span>

<!-- external links -->
[OfflinePowerShellGetDeploy]: https://www.powershellgallery.com/packages/OfflinePowerShellGetDeploy/0.1.1
[Nuget.Server]: /nuget/hosting-packages/nuget-server
[nuget.exe]: /nuget/tools/nuget-exe-cli-reference
