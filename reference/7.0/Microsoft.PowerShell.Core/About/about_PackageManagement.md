---
description: PackageManagement är en aggregator för program pakets hanterare.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_packagemanagement?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PackageManagement
ms.openlocfilehash: 5b4b42dfce03831da5cc317276e78e0777ff73d6
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93272384"
---
# <a name="about-packagemanagement"></a><span data-ttu-id="e6617-104">Om PackageManagement</span><span class="sxs-lookup"><span data-stu-id="e6617-104">About PackageManagement</span></span>

## <a name="short-description"></a><span data-ttu-id="e6617-105">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="e6617-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="e6617-106">PackageManagement är en aggregator för program pakets hanterare.</span><span class="sxs-lookup"><span data-stu-id="e6617-106">PackageManagement is an aggregator for software package managers.</span></span>

## <a name="long-description"></a><span data-ttu-id="e6617-107">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="e6617-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="e6617-108">PackageManagement-funktionen introducerades i Windows PowerShell 5,0.</span><span class="sxs-lookup"><span data-stu-id="e6617-108">PackageManagement functionality was introduced in Windows PowerShell 5.0.</span></span>

<span data-ttu-id="e6617-109">PackageManagement är ett enhetligt gränssnitt för hanterings system för program varu paket. Du kan köra PackageManagement-cmdletar för att utföra program identifiering, installation och inventering (SDII)-uppgifter.</span><span class="sxs-lookup"><span data-stu-id="e6617-109">PackageManagement is a unified interface for software package management systems; you can run PackageManagement cmdlets to perform software discovery, installation, and inventory (SDII) tasks.</span></span> <span data-ttu-id="e6617-110">Oberoende av den underliggande installations tekniken kan du köra de vanliga cmdletarna i PackageManagement-modulen för att söka efter, installera eller avinstallera paket. Lägg till, ta bort och fråga paket databaser; och kör frågor på en dator för att avgöra vilka program varu paket som är installerade.</span><span class="sxs-lookup"><span data-stu-id="e6617-110">Regardless of the underlying installation technology, you can run the common cmdlets in the PackageManagement module to search for, install, or uninstall packages; add, remove, and query package repositories; and run queries on a computer to determine which software packages are installed.</span></span>

<span data-ttu-id="e6617-111">PackageManagement stöder en flexibel plugin-modell som möjliggör stöd för andra hanterings system för program varu paket.</span><span class="sxs-lookup"><span data-stu-id="e6617-111">PackageManagement supports a flexible plug-in model that enables support for other software package management systems.</span></span>

<span data-ttu-id="e6617-112">PackageManagement-modulen ingår i Windows PowerShell 5,0 och senare versioner av PowerShell och fungerar på tre nivåer av paket hanterings strukturen: paket leverantörer, paket källor och själva paketen.</span><span class="sxs-lookup"><span data-stu-id="e6617-112">The PackageManagement module is included with Windows PowerShell 5.0 and later releases of PowerShell, and works on three levels of package management structure: package providers, package sources, and the packages themselves.</span></span> <span data-ttu-id="e6617-113">Låt oss definiera några villkor:</span><span class="sxs-lookup"><span data-stu-id="e6617-113">Let us define some terms:</span></span>

- <span data-ttu-id="e6617-114">Paket hanterare: program vara pakethanteringssystem.</span><span class="sxs-lookup"><span data-stu-id="e6617-114">Package manager: Software package management system.</span></span> <span data-ttu-id="e6617-115">I PackageManagement villkor är detta en paket leverantör.</span><span class="sxs-lookup"><span data-stu-id="e6617-115">In PackageManagement terms, this is a package provider.</span></span>
- <span data-ttu-id="e6617-116">Package provider: PackageManagement term för en paket hanterare.</span><span class="sxs-lookup"><span data-stu-id="e6617-116">Package provider: PackageManagement term for a package manager.</span></span> <span data-ttu-id="e6617-117">Exempel kan vara Windows Installer, choklad och andra.</span><span class="sxs-lookup"><span data-stu-id="e6617-117">Examples can include Windows Installer, Chocolatey, and others.</span></span>
- <span data-ttu-id="e6617-118">Paket Källa: en URL, lokal mapp eller delad nätverksmapp som du konfigurerar paket leverantörer att använda som en lagrings plats.</span><span class="sxs-lookup"><span data-stu-id="e6617-118">Package source: A URL, local folder, or network shared folder that you configure package providers to use as a repository.</span></span>
- <span data-ttu-id="e6617-119">Paket: en program vara som en Package provider hanterar och som lagras i en viss paket källa.</span><span class="sxs-lookup"><span data-stu-id="e6617-119">Package: A piece of software that a package provider manages, and that is stored in a specific package source.</span></span>

<span data-ttu-id="e6617-120">PackageManagement-modulen innehåller följande cmdletar.</span><span class="sxs-lookup"><span data-stu-id="e6617-120">The PackageManagement module includes the following cmdlets.</span></span> <span data-ttu-id="e6617-121">Mer information finns i [PackageManagement](/powershell/module/packagemanagement) -hjälpen.</span><span class="sxs-lookup"><span data-stu-id="e6617-121">For more information, see the [PackageManagement](/powershell/module/packagemanagement) help.</span></span>

- <span data-ttu-id="e6617-122">`Get-PackageProvider`: Returnerar en lista med paket leverantörer som är anslutna till PackageManagement.</span><span class="sxs-lookup"><span data-stu-id="e6617-122">`Get-PackageProvider`: Returns a list of package providers that are  connected to PackageManagement.</span></span>
- <span data-ttu-id="e6617-123">`Get-PackageSource`: Hämtar en lista över paket källor som har registrerats för en paket leverantör.</span><span class="sxs-lookup"><span data-stu-id="e6617-123">`Get-PackageSource`: Gets a list of package sources that are registered for a package provider.</span></span>
- <span data-ttu-id="e6617-124">`Register-PackageSource`: Lägger till en paket källa för en angiven paket leverantör.</span><span class="sxs-lookup"><span data-stu-id="e6617-124">`Register-PackageSource`: Adds a package source for a specified package provider.</span></span>
- <span data-ttu-id="e6617-125">`Set-PackageSource`: Anger egenskaper för en befintlig paket källa.</span><span class="sxs-lookup"><span data-stu-id="e6617-125">`Set-PackageSource`: Sets properties on an existing package source.</span></span>
- <span data-ttu-id="e6617-126">`Unregister-PackageSource`: Tar bort en registrerad paket källa.</span><span class="sxs-lookup"><span data-stu-id="e6617-126">`Unregister-PackageSource`: Removes a registered package source.</span></span>
- <span data-ttu-id="e6617-127">`Get-Package`: Returnerar en lista över installerade program varu paket.</span><span class="sxs-lookup"><span data-stu-id="e6617-127">`Get-Package`: Returns a list of installed software packages.</span></span>
- <span data-ttu-id="e6617-128">`Find-Package`: Söker efter program varu paket i tillgängliga paket källor.</span><span class="sxs-lookup"><span data-stu-id="e6617-128">`Find-Package`: Finds software packages in available package sources.</span></span>
- <span data-ttu-id="e6617-129">`Install-Package`: Installerar ett eller flera program varu paket.</span><span class="sxs-lookup"><span data-stu-id="e6617-129">`Install-Package`: Installs one or more software packages.</span></span>
- <span data-ttu-id="e6617-130">`Save-Package`: Sparar paket på den lokala datorn utan att installera dem.</span><span class="sxs-lookup"><span data-stu-id="e6617-130">`Save-Package`: Saves packages to the local computer without installing them.</span></span>
- <span data-ttu-id="e6617-131">`Uninstall-Package`: Avinstallerar ett eller flera program varu paket.</span><span class="sxs-lookup"><span data-stu-id="e6617-131">`Uninstall-Package`: Uninstalls one or more software packages.</span></span>

### <a name="package-provider-bootstrapping-and-dynamic-cmdlet-parameters"></a><span data-ttu-id="e6617-132">Parametrar för start och dynamisk cmdlet för paketera Provider</span><span class="sxs-lookup"><span data-stu-id="e6617-132">Package Provider Bootstrapping and Dynamic Cmdlet Parameters</span></span>

<span data-ttu-id="e6617-133">Som standard levereras PackageManagement med en Core bootstrap-Provider.</span><span class="sxs-lookup"><span data-stu-id="e6617-133">By default, PackageManagement ships with a core bootstrap provider.</span></span> <span data-ttu-id="e6617-134">Du kan installera ytterligare paket leverantörer när du behöver dem genom att starta providern. det vill säga att du svarar på en uppfråga för att installera providern automatiskt från en webb tjänst.</span><span class="sxs-lookup"><span data-stu-id="e6617-134">You can install additional package providers as you need them by bootstrapping the providers; that is, responding to a prompt to install the provider automatically, from a web service.</span></span> <span data-ttu-id="e6617-135">Du kan ange en paket leverantör med valfri PackageManagement-cmdlet; om den angivna providern inte är tillgänglig, kommer PackageManagement att bli ombedd att starta (eller installera automatiskt) providern.</span><span class="sxs-lookup"><span data-stu-id="e6617-135">You can specify a package provider with any PackageManagement cmdlet; if the specified provider is not available, PackageManagement prompts you to bootstrap (or automatically install) the provider.</span></span> <span data-ttu-id="e6617-136">I följande exempel, om den choklad leverantören inte redan är installerad, installerar PackageManagement-providern.</span><span class="sxs-lookup"><span data-stu-id="e6617-136">In the following examples, if the Chocolatey provider is not already installed, PackageManagement bootstrapping installs the provider.</span></span>

```powershell
Find-Package -Provider Chocolatey <PackageName>
```

<span data-ttu-id="e6617-137">Om den choklad leverantören inte redan är installerad, uppmanas du att installera det när du kör föregående kommando.</span><span class="sxs-lookup"><span data-stu-id="e6617-137">If the Chocolatey provider is not already installed, when you run the preceding command, you are prompted to install it.</span></span>

```powershell
Install-Package <Chocolatey package Name> -ForceBootstrap
```

<span data-ttu-id="e6617-138">Om den choklad leverantören inte redan är installerad när du kör föregående kommando, installeras providern. men eftersom parametern ForceBootstrap har lagts till i kommandot, uppmanas du inte att installera den. både providern och paketet installeras automatiskt.</span><span class="sxs-lookup"><span data-stu-id="e6617-138">If the Chocolatey provider is not already installed, when you run the preceding command, the provider is installed; but because the ForceBootstrap parameter has been added to the command, you are not prompted to install it; both the provider and the package are installed automatically.</span></span>

<span data-ttu-id="e6617-139">Om du försöker installera ett paket, om du inte redan har den stödda providern installerad, och du inte lägger till parametern ForceBootstrap i ditt kommando, kommer PackageManagement att be dig att installera providern.</span><span class="sxs-lookup"><span data-stu-id="e6617-139">When you try to install a package, if you do not already have the supporting provider installed, and you do not add the ForceBootstrap parameter to your command, PackageManagement prompts you to install the provider.</span></span>

<span data-ttu-id="e6617-140">Om du anger en paket leverantör i ditt PackageManagement-kommando kan du göra dynamiska parametrar som är tillgängliga för den paket leverantören.</span><span class="sxs-lookup"><span data-stu-id="e6617-140">Specifying a package provider in your PackageManagement command can make dynamic parameters available that are specific to that package provider.</span></span> <span data-ttu-id="e6617-141">När du kör Get-Help för en särskild PackageManagement-cmdlet returneras en lista med parameter uppsättningar, grupper dynamiska parametrar för tillgängliga paket leverantörer i separata parameter uppsättningar.</span><span class="sxs-lookup"><span data-stu-id="e6617-141">When you run Get-Help for a specific PackageManagement cmdlet, a list of parameter sets are returned, grouping dynamic parameters for available package providers in separate parameter sets.</span></span>

<span data-ttu-id="e6617-142">Mer information om PackageManagement-projektet</span><span class="sxs-lookup"><span data-stu-id="e6617-142">More Information About the PackageManagement Project</span></span>

<span data-ttu-id="e6617-143">Mer information om PackageManagement Open Development Project, inklusive hur du skapar en PackageManagement-paket leverantör finns i PackageManagement-projektet på GitHub på https://oneget.org .</span><span class="sxs-lookup"><span data-stu-id="e6617-143">For more information about the PackageManagement open development project, including how to create a PackageManagement package provider, see the PackageManagement project on GitHub at https://oneget.org.</span></span>

## <a name="see-also"></a><span data-ttu-id="e6617-144">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="e6617-144">SEE ALSO</span></span>

[<span data-ttu-id="e6617-145">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="e6617-145">Get-PackageProvider</span></span>](xref:PackageManagement.Get-PackageProvider)

[<span data-ttu-id="e6617-146">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="e6617-146">Get-PackageSource</span></span>](xref:PackageManagement.Get-PackageSource)

[<span data-ttu-id="e6617-147">Registrera – PackageSource</span><span class="sxs-lookup"><span data-stu-id="e6617-147">Register-PackageSource</span></span>](xref:PackageManagement.Register-PackageSource)

[<span data-ttu-id="e6617-148">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="e6617-148">Set-PackageSource</span></span>](xref:PackageManagement.Set-PackageSource)

[<span data-ttu-id="e6617-149">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="e6617-149">Unregister-PackageSource</span></span>](xref:PackageManagement.Unregister-PackageSource)

[<span data-ttu-id="e6617-150">Get-Package</span><span class="sxs-lookup"><span data-stu-id="e6617-150">Get-Package</span></span>](xref:PackageManagement.Get-Package)

[<span data-ttu-id="e6617-151">Sök-paket</span><span class="sxs-lookup"><span data-stu-id="e6617-151">Find-Package</span></span>](xref:PackageManagement.Find-Package)

[<span data-ttu-id="e6617-152">Installationspaket</span><span class="sxs-lookup"><span data-stu-id="e6617-152">Install-Package</span></span>](xref:PackageManagement.Install-Package)

[<span data-ttu-id="e6617-153">Spara paket</span><span class="sxs-lookup"><span data-stu-id="e6617-153">Save-Package</span></span>](xref:PackageManagement.Save-Package)

[<span data-ttu-id="e6617-154">Avinstallera paket</span><span class="sxs-lookup"><span data-stu-id="e6617-154">Uninstall-Package</span></span>](xref:PackageManagement.Uninstall-Package)
