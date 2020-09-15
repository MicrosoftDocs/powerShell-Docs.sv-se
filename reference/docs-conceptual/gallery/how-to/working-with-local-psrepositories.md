---
ms.date: 11/06/2018
contributor: JKeithB
keywords: Galleri, PowerShell, cmdlet, psgallery, psget
title: Arbeta med lokala PSRepositories
ms.openlocfilehash: 421b73c141c7551224e2298f51464a19bc736d0e
ms.sourcegitcommit: 105c69ecedfe5180d8c12e8015d667c5f1a71579
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85837587"
---
# <a name="working-with-private-powershellget-repositories"></a><span data-ttu-id="b44e9-103">Arbeta med privata PowerShellGet-lagringsplatser</span><span class="sxs-lookup"><span data-stu-id="b44e9-103">Working with Private PowerShellGet Repositories</span></span>

<span data-ttu-id="b44e9-104">PowerShellGet-modulen stöder andra databaser än PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="b44e9-104">The PowerShellGet module support repositories other than the PowerShell Gallery.</span></span>
<span data-ttu-id="b44e9-105">Dessa cmdletar möjliggör följande scenarier:</span><span class="sxs-lookup"><span data-stu-id="b44e9-105">These cmdlets enable the following scenarios:</span></span>

- <span data-ttu-id="b44e9-106">Stöd för en betrodd, fördefinierad uppsättning PowerShell-moduler för användning i din miljö</span><span class="sxs-lookup"><span data-stu-id="b44e9-106">Support a trusted, pre-validated set of PowerShell modules for use in your environment</span></span>
- <span data-ttu-id="b44e9-107">Testa en CI/CD-pipeline som bygger PowerShell-moduler eller-skript</span><span class="sxs-lookup"><span data-stu-id="b44e9-107">Testing a CI/CD pipeline that builds PowerShell modules or scripts</span></span>
- <span data-ttu-id="b44e9-108">Leverera PowerShell-skript och moduler till system som inte har åtkomst till Internet</span><span class="sxs-lookup"><span data-stu-id="b44e9-108">Deliver PowerShell scripts and modules to systems that can't access the internet</span></span>
- <span data-ttu-id="b44e9-109">Leverera PowerShell-skript och moduler som endast är tillgängliga för din organisation</span><span class="sxs-lookup"><span data-stu-id="b44e9-109">Deliver PowerShell scripts and modules only available to your organization</span></span>

<span data-ttu-id="b44e9-110">Den här artikeln beskriver hur du konfigurerar en lokal PowerShell-lagringsplats.</span><span class="sxs-lookup"><span data-stu-id="b44e9-110">This article describes how to set up a local PowerShell repository.</span></span> <span data-ttu-id="b44e9-111">Artikeln beskriver också [OfflinePowerShellGetDeploy][] -modulen som är tillgänglig från PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="b44e9-111">The article also covers the [OfflinePowerShellGetDeploy][] module available from the PowerShell Gallery.</span></span> <span data-ttu-id="b44e9-112">Den här modulen innehåller cmdlets för att installera den senaste versionen av PowerShellGet i din lokala lagrings plats.</span><span class="sxs-lookup"><span data-stu-id="b44e9-112">This module contains cmdlets to install the latest version of PowerShellGet into your local repository.</span></span>

## <a name="local-repository-types"></a><span data-ttu-id="b44e9-113">Typer av lokala databaser</span><span class="sxs-lookup"><span data-stu-id="b44e9-113">Local repository types</span></span>

<span data-ttu-id="b44e9-114">Det finns två sätt att skapa en lokal PSRepository: NuGet-Server eller fil resurs.</span><span class="sxs-lookup"><span data-stu-id="b44e9-114">There are two ways to create a local PSRepository: NuGet server or file share.</span></span> <span data-ttu-id="b44e9-115">Varje typ har fördelar och nack delar:</span><span class="sxs-lookup"><span data-stu-id="b44e9-115">Each type has advantages and disadvantages:</span></span>

### <a name="nuget-server"></a><span data-ttu-id="b44e9-116">NuGet-Server</span><span class="sxs-lookup"><span data-stu-id="b44e9-116">NuGet Server</span></span>

| <span data-ttu-id="b44e9-117">Fördelar</span><span class="sxs-lookup"><span data-stu-id="b44e9-117">Advantages</span></span>| <span data-ttu-id="b44e9-118">Nackdelar</span><span class="sxs-lookup"><span data-stu-id="b44e9-118">Disadvantages</span></span> |
| --- | --- |
| <span data-ttu-id="b44e9-119">Liknar PowerShellGallery-funktioner</span><span class="sxs-lookup"><span data-stu-id="b44e9-119">Closely mimics PowerShellGallery functionality</span></span> | <span data-ttu-id="b44e9-120">En app med flera nivåer kräver åtgärder som planerar &</span><span class="sxs-lookup"><span data-stu-id="b44e9-120">Multi-tier app requires operations planning & support</span></span> |
| <span data-ttu-id="b44e9-121">NuGet integreras med Visual Studio, andra verktyg</span><span class="sxs-lookup"><span data-stu-id="b44e9-121">NuGet integrates with Visual Studio, other tools</span></span> | <span data-ttu-id="b44e9-122">Autentiserings modell och NuGet Accounts Management krävs</span><span class="sxs-lookup"><span data-stu-id="b44e9-122">Authentication model and NuGet accounts management needed</span></span> |
| <span data-ttu-id="b44e9-123">NuGet stöder metadata i `.Nupkg` paket</span><span class="sxs-lookup"><span data-stu-id="b44e9-123">NuGet supports metadata in `.Nupkg` packages</span></span> | <span data-ttu-id="b44e9-124">Publicering kräver hantering av API-nyckel & underhåll</span><span class="sxs-lookup"><span data-stu-id="b44e9-124">Publishing requires API Key management & maintenance</span></span> |
| <span data-ttu-id="b44e9-125">Tillhandahåller sökning, paket administration osv.</span><span class="sxs-lookup"><span data-stu-id="b44e9-125">Provides search, package administration, etc.</span></span> | |

### <a name="file-share"></a><span data-ttu-id="b44e9-126">Filresurs</span><span class="sxs-lookup"><span data-stu-id="b44e9-126">File Share</span></span>

| <span data-ttu-id="b44e9-127">Fördelar</span><span class="sxs-lookup"><span data-stu-id="b44e9-127">Advantages</span></span>| <span data-ttu-id="b44e9-128">Nackdelar</span><span class="sxs-lookup"><span data-stu-id="b44e9-128">Disadvantages</span></span> |
| --- | --- |
| <span data-ttu-id="b44e9-129">Enkelt att konfigurera, säkerhetskopiera och underhålla</span><span class="sxs-lookup"><span data-stu-id="b44e9-129">Easy to set up, back up, and maintain</span></span> | <span data-ttu-id="b44e9-130">Metadata som används av PowerShellGet är inte tillgängliga</span><span class="sxs-lookup"><span data-stu-id="b44e9-130">Metadata used by PowerShellGet isn't available</span></span> |
| <span data-ttu-id="b44e9-131">Enkel säkerhets modell – användar behörigheter på resursen</span><span class="sxs-lookup"><span data-stu-id="b44e9-131">Simple security model - user permissions on the share</span></span> | <span data-ttu-id="b44e9-132">Inget användar gränssnitt utöver grundläggande fil resurs</span><span class="sxs-lookup"><span data-stu-id="b44e9-132">No UI beyond basic file share</span></span> |
| <span data-ttu-id="b44e9-133">Inga begränsningar, som att ersätta befintliga objekt</span><span class="sxs-lookup"><span data-stu-id="b44e9-133">No constraints such as replacing existing items</span></span> | <span data-ttu-id="b44e9-134">Begränsad säkerhet och ingen inspelning av vem som uppdaterar vad</span><span class="sxs-lookup"><span data-stu-id="b44e9-134">Limited security and no recording of who updates what</span></span> |

<span data-ttu-id="b44e9-135">PowerShellGet fungerar med antingen typ och har stöd för att hitta versioner och beroende installationer.</span><span class="sxs-lookup"><span data-stu-id="b44e9-135">PowerShellGet works with either type and supports locating versions and dependency installation.</span></span>
<span data-ttu-id="b44e9-136">Men vissa funktioner som fungerar för PowerShell-galleriet är inte tillgängliga för bas-NuGet-servrar eller fil resurser.</span><span class="sxs-lookup"><span data-stu-id="b44e9-136">However, some features that work for the PowerShell Gallery aren't available for base NuGet servers or file shares.</span></span>

- <span data-ttu-id="b44e9-137">Allt är ett paket – ingen differentiering av skript, moduler, DSC-resurser eller roll funktioner.</span><span class="sxs-lookup"><span data-stu-id="b44e9-137">Everything is a package - no differentiation of scripts, modules, DSC resources, or role capabilities.</span></span>
- <span data-ttu-id="b44e9-138">Fil resurs servrar kan inte se paketets metadata, inklusive taggar.</span><span class="sxs-lookup"><span data-stu-id="b44e9-138">File share servers can't see package metadata, including tags.</span></span>

## <a name="creating-a-local-repository"></a><span data-ttu-id="b44e9-139">Skapa en lokal lagrings plats</span><span class="sxs-lookup"><span data-stu-id="b44e9-139">Creating a local repository</span></span>

<span data-ttu-id="b44e9-140">I följande artikel visas stegen för att skapa en egen NuGet-Server.</span><span class="sxs-lookup"><span data-stu-id="b44e9-140">The following article lists the steps for setting up your own NuGet Server.</span></span>

- <span data-ttu-id="b44e9-141">[NuGet. Server][]</span><span class="sxs-lookup"><span data-stu-id="b44e9-141">[NuGet.Server][]</span></span>

<span data-ttu-id="b44e9-142">Följ stegen upp till punkten för att lägga till paket.</span><span class="sxs-lookup"><span data-stu-id="b44e9-142">Follow the steps up to the point of adding packages.</span></span> <span data-ttu-id="b44e9-143">Stegen för att [publicera ett paket](#publishing-to-a-local-repository) beskrivs längre fram i den här artikeln.</span><span class="sxs-lookup"><span data-stu-id="b44e9-143">The steps for [publishing a package](#publishing-to-a-local-repository) are covered later in this article.</span></span>

<span data-ttu-id="b44e9-144">Se till att användarna har behörighet att komma åt fil resursen för en fil resursbaserade lagrings plats.</span><span class="sxs-lookup"><span data-stu-id="b44e9-144">For a file share-based repository, make sure that your users have permissions to access the file share.</span></span>

## <a name="registering-a-local-repository"></a><span data-ttu-id="b44e9-145">Registrera en lokal lagrings plats</span><span class="sxs-lookup"><span data-stu-id="b44e9-145">Registering a local repository</span></span>

<span data-ttu-id="b44e9-146">Innan du kan använda en lagrings plats måste du registrera den med hjälp av `Register-PSRepository` kommandot.</span><span class="sxs-lookup"><span data-stu-id="b44e9-146">Before a repository can be used, it must be registered using the `Register-PSRepository` command.</span></span>
<span data-ttu-id="b44e9-147">I exemplen nedan är **InstallationPolicy** inställt på *betrott*, enligt det antagande att du litar på din egen lagrings plats.</span><span class="sxs-lookup"><span data-stu-id="b44e9-147">In the examples below, the **InstallationPolicy** is set to *Trusted*, on the assumption that you trust your own repository.</span></span>

```powershell
# Register a NuGet-based server
Register-PSRepository -Name LocalPSRepo -SourceLocation http://MyLocalNuget/Api/V2/ -ScriptSourceLocation http://MyLocalNuget/Api/V2 -InstallationPolicy Trusted

# Register a file share on my local machine
Register-PSRepository -Name LocalPSRepo -SourceLocation '\\localhost\PSRepoLocal\' -ScriptSourceLocation '\\localhost\PSRepoLocal\' -InstallationPolicy Trusted
```

<span data-ttu-id="b44e9-148">Anteckna skillnaden mellan de två kommandona som hanterar **ScriptSourceLocation**.</span><span class="sxs-lookup"><span data-stu-id="b44e9-148">Take note of the difference between how the two commands handle **ScriptSourceLocation**.</span></span> <span data-ttu-id="b44e9-149">För en fil resursbaserade databaser måste **SourceLocation** och **ScriptSourceLocation** matcha.</span><span class="sxs-lookup"><span data-stu-id="b44e9-149">For a file share-based repositories, the **SourceLocation** and **ScriptSourceLocation** must match.</span></span> <span data-ttu-id="b44e9-150">För en webbaserad lagrings plats måste de vara olika, så i det här exemplet läggs ett efterföljande "/" till i **SourceLocation**.</span><span class="sxs-lookup"><span data-stu-id="b44e9-150">For a web-based repository, they must be different, so in this example a trailing "/" is added to the **SourceLocation**.</span></span>

<span data-ttu-id="b44e9-151">Om du vill att det nyligen skapade PSRepository ska vara standard lagrings platsen måste du avregistrera alla andra PSRepositories.</span><span class="sxs-lookup"><span data-stu-id="b44e9-151">If you want the newly created PSRepository to be the default repository, you must unregister all other PSRepositories.</span></span> <span data-ttu-id="b44e9-152">Exempel:</span><span class="sxs-lookup"><span data-stu-id="b44e9-152">For example:</span></span>

```powershell
Unregister-PSRepository -Name PSGallery
```

> [!NOTE]
> <span data-ttu-id="b44e9-153">Databas namnet "PSGallery" är reserverat för användning av PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="b44e9-153">The repository name 'PSGallery' is reserved for use by the PowerShell Gallery.</span></span> <span data-ttu-id="b44e9-154">Du kan avregistrera PSGallery, men du kan inte återanvända namnet PSGallery för andra lagrings platser.</span><span class="sxs-lookup"><span data-stu-id="b44e9-154">You can unregister PSGallery, but you cannot reuse the name PSGallery for any other repository.</span></span>

<span data-ttu-id="b44e9-155">Om du behöver återställa PSGallery kör du följande kommando:</span><span class="sxs-lookup"><span data-stu-id="b44e9-155">If you need to restore the PSGallery, run the following command:</span></span>

```powershell
Register-PSRepository -Default
```

## <a name="publishing-to-a-local-repository"></a><span data-ttu-id="b44e9-156">Publicera till en lokal lagrings plats</span><span class="sxs-lookup"><span data-stu-id="b44e9-156">Publishing to a local repository</span></span>

<span data-ttu-id="b44e9-157">När du har registrerat den lokala PSRepository kan du publicera den på din lokala PSRepository.</span><span class="sxs-lookup"><span data-stu-id="b44e9-157">Once you've registered the local PSRepository, you can publish to your local PSRepository.</span></span> <span data-ttu-id="b44e9-158">Det finns två huvudsakliga publicerings scenarier: publicera en egen modul och publicera en modul från PSGallery.</span><span class="sxs-lookup"><span data-stu-id="b44e9-158">There are two main publishing scenarios: publishing your own module and publishing a module from the PSGallery.</span></span>

### <a name="publishing-a-module-you-authored"></a><span data-ttu-id="b44e9-159">Publicera en modul som du har skapat</span><span class="sxs-lookup"><span data-stu-id="b44e9-159">Publishing a module you authored</span></span>

<span data-ttu-id="b44e9-160">Använd `Publish-Module` och `Publish-Script` för att publicera modulen i din lokala PSRepository på samma sätt som du gör för PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="b44e9-160">Use `Publish-Module` and `Publish-Script` to publish your module to your local PSRepository the same way you do for the PowerShell Gallery.</span></span>

- <span data-ttu-id="b44e9-161">Ange plats för koden</span><span class="sxs-lookup"><span data-stu-id="b44e9-161">Specify the location for your code</span></span>
- <span data-ttu-id="b44e9-162">Ange en API-nyckel</span><span class="sxs-lookup"><span data-stu-id="b44e9-162">Supply an API key</span></span>
- <span data-ttu-id="b44e9-163">Ange namnet på databasen.</span><span class="sxs-lookup"><span data-stu-id="b44e9-163">Specify the repository name.</span></span> <span data-ttu-id="b44e9-164">Till exempel `-PSRepository LocalPSRepo`</span><span class="sxs-lookup"><span data-stu-id="b44e9-164">For example, `-PSRepository LocalPSRepo`</span></span>

> [!NOTE]
> <span data-ttu-id="b44e9-165">Du måste skapa ett konto på NuGet-servern och sedan logga in för att generera och spara API-nyckeln.</span><span class="sxs-lookup"><span data-stu-id="b44e9-165">You must create an account in the NuGet server, then sign in to generate and save the API key.</span></span>
> <span data-ttu-id="b44e9-166">För en fil resurs använder du en icke-tom sträng för NuGetApiKey-värdet.</span><span class="sxs-lookup"><span data-stu-id="b44e9-166">For a file share, use any non-blank string for the NuGetApiKey value.</span></span>

<span data-ttu-id="b44e9-167">Exempel:</span><span class="sxs-lookup"><span data-stu-id="b44e9-167">Examples:</span></span>

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey $nuGetApiKey
```

> [!IMPORTANT]
> <span data-ttu-id="b44e9-168">För att säkerställa säkerheten bör API-nycklar inte hårdkodas i skript.</span><span class="sxs-lookup"><span data-stu-id="b44e9-168">To ensure security, API keys should not be hard-coded in scripts.</span></span> <span data-ttu-id="b44e9-169">Använd ett säkert nyckel hanterings system.</span><span class="sxs-lookup"><span data-stu-id="b44e9-169">Use a secure key management system.</span></span> <span data-ttu-id="b44e9-170">När du kör ett kommando manuellt ska API-nycklar inte skickas som vanlig text för att undvika att den loggas. `Read-Host` cmdleten kan användas för att på ett säkert sätt skicka värdet för API-nyckeln.</span><span class="sxs-lookup"><span data-stu-id="b44e9-170">When executing a command manually, API keys should not be passed as plain-text to avoid it being logged, the `Read-Host` cmdlet can be used to safely pass the value of the API key.</span></span>

```powershell
# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

### <a name="publishing-a-module-from-the-psgallery"></a><span data-ttu-id="b44e9-171">Publicera en modul från PSGallery</span><span class="sxs-lookup"><span data-stu-id="b44e9-171">Publishing a module from the PSGallery</span></span>

<span data-ttu-id="b44e9-172">Om du vill publicera en modul från PSGallery till din lokala PSRepository kan du använda cmdleten "Save-Package".</span><span class="sxs-lookup"><span data-stu-id="b44e9-172">To publish a module from the PSGallery to your local PSRepository, you can use the 'Save-Package' cmdlet.</span></span>

- <span data-ttu-id="b44e9-173">Ange paketets namn</span><span class="sxs-lookup"><span data-stu-id="b44e9-173">Specify the Name of the Package</span></span>
- <span data-ttu-id="b44e9-174">Ange "NuGet" som Provider</span><span class="sxs-lookup"><span data-stu-id="b44e9-174">Specify 'NuGet' as the Provider</span></span>
- <span data-ttu-id="b44e9-175">Ange PSGallery-platsen som källa (https://www.powershellgallery.com/api/v2)</span><span class="sxs-lookup"><span data-stu-id="b44e9-175">Specify the PSGallery location as the source (https://www.powershellgallery.com/api/v2)</span></span>
- <span data-ttu-id="b44e9-176">Ange sökvägen till din lokala lagrings plats</span><span class="sxs-lookup"><span data-stu-id="b44e9-176">Specify the path to your local Repository</span></span>

<span data-ttu-id="b44e9-177">Exempel:</span><span class="sxs-lookup"><span data-stu-id="b44e9-177">Example:</span></span>

```powershell
# Publish from the PSGallery to your local Repository
Save-Package -Name 'PackageName' -Provider NuGet -Source https://www.powershellgallery.com/api/v2 -Path '\\localhost\PSRepoLocal\'
```

<span data-ttu-id="b44e9-178">Om din lokala PSRepository är webbaserad kräver det ytterligare ett steg som använder nuget.exe för att publicera.</span><span class="sxs-lookup"><span data-stu-id="b44e9-178">If your local PSRepository is web-based, it requires an additional step that uses nuget.exe to publish.</span></span>

<span data-ttu-id="b44e9-179">Se dokumentationen för att använda [nuget.exe][].</span><span class="sxs-lookup"><span data-stu-id="b44e9-179">See the documentation for using [nuget.exe][].</span></span>

## <a name="installing-powershellget-on-a-disconnected-system"></a><span data-ttu-id="b44e9-180">Installera PowerShellGet på ett frånkopplat system</span><span class="sxs-lookup"><span data-stu-id="b44e9-180">Installing PowerShellGet on a disconnected system</span></span>

<span data-ttu-id="b44e9-181">Det är svårt att distribuera PowerShellGet i miljöer som kräver att system kopplas från Internet.</span><span class="sxs-lookup"><span data-stu-id="b44e9-181">Deploying PowerShellGet is difficult in environments that require systems to be disconnected from the internet.</span></span> <span data-ttu-id="b44e9-182">PowerShellGet har en start process som installerar den senaste versionen första gången den används.</span><span class="sxs-lookup"><span data-stu-id="b44e9-182">PowerShellGet has a bootstrap process that installs the latest version the first time it's used.</span></span> <span data-ttu-id="b44e9-183">OfflinePowerShellGetDeploy-modulen i PowerShell-galleriet tillhandahåller cmdlets som stöder den här start processen.</span><span class="sxs-lookup"><span data-stu-id="b44e9-183">The OfflinePowerShellGetDeploy module in the PowerShell Gallery provides cmdlets that support this bootstrap process.</span></span>

<span data-ttu-id="b44e9-184">Om du vill starta en offline-distribution måste du:</span><span class="sxs-lookup"><span data-stu-id="b44e9-184">To bootstrap an offline deployment, you need to:</span></span>

- <span data-ttu-id="b44e9-185">Hämta och installera OfflinePowerShellGetDeploy-datorn och dina frånkopplade system</span><span class="sxs-lookup"><span data-stu-id="b44e9-185">Download and install the OfflinePowerShellGetDeploy your internet-connected system and your disconnected systems</span></span>
- <span data-ttu-id="b44e9-186">Ladda ned PowerShellGet och dess beroenden på det Internet-anslutna systemet med `Save-PowerShellGetForOffline` cmdleten</span><span class="sxs-lookup"><span data-stu-id="b44e9-186">Download PowerShellGet and its dependencies on the internet-connected system using the `Save-PowerShellGetForOffline` cmdlet</span></span>
- <span data-ttu-id="b44e9-187">Kopiera PowerShellGet och dess beroenden från det Internet-anslutna systemet till det frånkopplade systemet</span><span class="sxs-lookup"><span data-stu-id="b44e9-187">Copy PowerShellGet and its dependencies from the internet-connected system to the disconnected system</span></span>
- <span data-ttu-id="b44e9-188">Använd `Install-PowerShellGetOffline` på det frånkopplade systemet för att placera PowerShellGet och dess beroenden i rätt mappar</span><span class="sxs-lookup"><span data-stu-id="b44e9-188">Use the `Install-PowerShellGetOffline` on the disconnected system to place PowerShellGet and its dependencies into the proper folders</span></span>

<span data-ttu-id="b44e9-189">Följande kommandon används `Save-PowerShellGetForOffline` för att skicka alla komponenter till en mapp `f:\OfflinePowerShellGet`</span><span class="sxs-lookup"><span data-stu-id="b44e9-189">The following commands use `Save-PowerShellGetForOffline` to put all the components into a folder `f:\OfflinePowerShellGet`</span></span>

```powershell
# Requires -RunAsAdministrator
#Download the OfflinePowerShellGetDeploy to a location that can be accessed
# by both the connected and disconnected systems.
Save-Module -Name OfflinePowerShellGetDeploy -Path 'F:\' -Repository PSGallery
Import-Module F:\OfflinePowerShellGetDeploy

# Put PowerShellGet somewhere locally
Save-PowerShellGetForOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

<span data-ttu-id="b44e9-190">I det här läget måste du göra innehållet `F:\OfflinePowerShellGet` tillgängligt för de frånkopplade systemen.</span><span class="sxs-lookup"><span data-stu-id="b44e9-190">At this point, you must make the contents of `F:\OfflinePowerShellGet` available to your disconnected systems.</span></span> <span data-ttu-id="b44e9-191">Kör `Install-PowerShellGetOffline` cmdleten för att installera PowerShellGet på det frånkopplade systemet.</span><span class="sxs-lookup"><span data-stu-id="b44e9-191">Run the `Install-PowerShellGetOffline` cmdlet to install PowerShellGet on the disconnected system.</span></span>

> [!NOTE]
> <span data-ttu-id="b44e9-192">Det är viktigt att du inte kör PowerShellGet i PowerShell-sessionen innan du kör de här kommandona.</span><span class="sxs-lookup"><span data-stu-id="b44e9-192">It is important that you do not run PowerShellGet in the PowerShell session before running these commands.</span></span> <span data-ttu-id="b44e9-193">När PowerShellGet har lästs in i sessionen går det inte att uppdatera komponenterna.</span><span class="sxs-lookup"><span data-stu-id="b44e9-193">Once PowerShellGet is loaded into the session, the components cannot be updated.</span></span> <span data-ttu-id="b44e9-194">Om du startar PowerShellGet av misstag, avslutar du och startar om PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b44e9-194">If you do start PowerShellGet by mistake, exit and restart PowerShell.</span></span>

```powershell
Import-Module F:\OfflinePowerShellGetDeploy

Install-PowerShellGetOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

<span data-ttu-id="b44e9-195">När du har kört dessa kommandon är du redo att publicera PowerShellGet till din lokala lagrings plats.</span><span class="sxs-lookup"><span data-stu-id="b44e9-195">After running these commands, you are ready to publish PowerShellGet to your local repository.</span></span>

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'F:\OfflinePowershellGet' -Repository LocalPsRepo -NuGetApiKey $nuGetApiKey
```

> [!IMPORTANT]
> <span data-ttu-id="b44e9-196">För att säkerställa säkerheten bör API-nycklar inte hårdkodas i skript.</span><span class="sxs-lookup"><span data-stu-id="b44e9-196">To ensure security, API keys should not be hard-coded in scripts.</span></span> <span data-ttu-id="b44e9-197">Använd ett säkert nyckel hanterings system.</span><span class="sxs-lookup"><span data-stu-id="b44e9-197">Use a secure key management system.</span></span> <span data-ttu-id="b44e9-198">När du kör ett kommando manuellt ska API-nycklar inte skickas som vanlig text för att undvika att den loggas. `Read-Host` cmdleten kan användas för att på ett säkert sätt skicka värdet för API-nyckeln.</span><span class="sxs-lookup"><span data-stu-id="b44e9-198">When executing a command manually, API keys should not be passed as plain-text to avoid it being logged, the `Read-Host` cmdlet can be used to safely pass the value of the API key.</span></span>

```powershell
# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'F:\OfflinePowerShellGet' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

## <a name="use-packaging-solutions-to-host-powershellget-repositories"></a><span data-ttu-id="b44e9-199">Använda förpacknings lösningar för att vara värdar för PowerShellGet-databaser</span><span class="sxs-lookup"><span data-stu-id="b44e9-199">Use Packaging solutions to host PowerShellGet repositories</span></span>

<span data-ttu-id="b44e9-200">Du kan också använda paket lösningar som Azure-artefakter som värdar för en privat eller offentlig PowerShellGet-lagringsplats.</span><span class="sxs-lookup"><span data-stu-id="b44e9-200">You can also use packaging solutions like Azure Artifacts to host a private or public PowerShellGet repository.</span></span> <span data-ttu-id="b44e9-201">Mer information och instruktioner finns i dokumentationen för [Azure-artefakter](/azure/devops/artifacts/tutorials/private-powershell-library).</span><span class="sxs-lookup"><span data-stu-id="b44e9-201">For more information and instructions, see the [Azure Artifacts documentation](/azure/devops/artifacts/tutorials/private-powershell-library).</span></span>

<!-- external links -->
[OfflinePowerShellGetDeploy]: https://www.powershellgallery.com/packages/OfflinePowerShellGetDeploy/0.1.1
[NuGet. Server]: /nuget/hosting-packages/nuget-server
[Nuget.Server]: /nuget/hosting-packages/nuget-server
[nuget.exe]: /nuget/tools/nuget-exe-cli-reference
