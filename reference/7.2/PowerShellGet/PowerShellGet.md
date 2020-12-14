---
Download Help Link: https://aka.ms/powershell72-help
Help Version: 7.2.0.0
Locale: en-US
Module Guid: 1d73a601-4a6c-43c5-ba3f-619b18bbb404
Module Name: PowerShellGet
ms.date: 06/09/2017
schema: 2.0.0
title: PowerShellGet
ms.openlocfilehash: 0d4e5e26184558055a17f99bd5321aaf3f3789f7
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94889211"
---
# <span data-ttu-id="8e608-102">PowerShellGet-modul</span><span class="sxs-lookup"><span data-stu-id="8e608-102">PowerShellGet Module</span></span>

## <span data-ttu-id="8e608-103">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8e608-103">Description</span></span>

<span data-ttu-id="8e608-104">PowerShellGet är en modul med kommandon för att upptäcka, installera, uppdatera och publicera PowerShell-artefakter som moduler, DSC-resurser, roll funktioner och skript.</span><span class="sxs-lookup"><span data-stu-id="8e608-104">PowerShellGet is a module with commands for discovering, installing, updating and publishing PowerShell artifacts like Modules, DSC Resources, Role Capabilities, and Scripts.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8e608-105">Från och med april 2020 stöder PowerShell-galleriet inte längre Transport Layer Security (TLS), version 1,0 och 1,1.</span><span class="sxs-lookup"><span data-stu-id="8e608-105">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="8e608-106">Om du inte använder TLS 1,2 eller senare visas ett fel meddelande när du försöker få åtkomst till PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="8e608-106">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="8e608-107">Använd följande kommando för att se till att du använder TLS 1,2:</span><span class="sxs-lookup"><span data-stu-id="8e608-107">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="8e608-108">Mer information finns i [meddelandet](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) i PowerShell-bloggen.</span><span class="sxs-lookup"><span data-stu-id="8e608-108">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="8e608-109">PowerShellGet-cmdletar</span><span class="sxs-lookup"><span data-stu-id="8e608-109">PowerShellGet Cmdlets</span></span>

### [<span data-ttu-id="8e608-110">Sök-kommando</span><span class="sxs-lookup"><span data-stu-id="8e608-110">Find-Command</span></span>](Find-Command.md)
<span data-ttu-id="8e608-111">Söker efter PowerShell-kommandon i moduler.</span><span class="sxs-lookup"><span data-stu-id="8e608-111">Finds PowerShell commands in modules.</span></span>

### [<span data-ttu-id="8e608-112">Find-Dscresource Keyword Supports</span><span class="sxs-lookup"><span data-stu-id="8e608-112">Find-DscResource</span></span>](Find-DscResource.md)
<span data-ttu-id="8e608-113">Söker efter Desired State Configuration (DSC)-resurser.</span><span class="sxs-lookup"><span data-stu-id="8e608-113">Finds Desired State Configuration (DSC) resources.</span></span>

### [<span data-ttu-id="8e608-114">Sök-modul</span><span class="sxs-lookup"><span data-stu-id="8e608-114">Find-Module</span></span>](Find-Module.md)
<span data-ttu-id="8e608-115">Söker efter moduler i en lagrings plats som matchar de angivna kriterierna.</span><span class="sxs-lookup"><span data-stu-id="8e608-115">Finds modules in a repository that match specified criteria.</span></span>

### [<span data-ttu-id="8e608-116">Find-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="8e608-116">Find-RoleCapability</span></span>](Find-RoleCapability.md)
<span data-ttu-id="8e608-117">Hittar roll funktioner i moduler.</span><span class="sxs-lookup"><span data-stu-id="8e608-117">Finds role capabilities in modules.</span></span>

### [<span data-ttu-id="8e608-118">Sök – skript</span><span class="sxs-lookup"><span data-stu-id="8e608-118">Find-Script</span></span>](Find-Script.md)
<span data-ttu-id="8e608-119">Söker efter ett skript.</span><span class="sxs-lookup"><span data-stu-id="8e608-119">Finds a script.</span></span>

### [<span data-ttu-id="8e608-120">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="8e608-120">Get-InstalledModule</span></span>](Get-InstalledModule.md)
<span data-ttu-id="8e608-121">Hämtar en lista över moduler på den dator som har installerats av PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="8e608-121">Gets a list of modules on the computer that were installed by PowerShellGet.</span></span>

### [<span data-ttu-id="8e608-122">Get-InstalledScript</span><span class="sxs-lookup"><span data-stu-id="8e608-122">Get-InstalledScript</span></span>](Get-InstalledScript.md)
<span data-ttu-id="8e608-123">Hämtar ett installerat skript.</span><span class="sxs-lookup"><span data-stu-id="8e608-123">Gets an installed script.</span></span>

### [<span data-ttu-id="8e608-124">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="8e608-124">Get-PSRepository</span></span>](Get-PSRepository.md)
<span data-ttu-id="8e608-125">Hämtar PowerShell-databaser.</span><span class="sxs-lookup"><span data-stu-id="8e608-125">Gets PowerShell repositories.</span></span>

### [<span data-ttu-id="8e608-126">Installera-modul</span><span class="sxs-lookup"><span data-stu-id="8e608-126">Install-Module</span></span>](Install-Module.md)
<span data-ttu-id="8e608-127">Laddar ned en eller flera moduler från en lagrings plats och installerar dem på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="8e608-127">Downloads one or more modules from a repository, and installs them on the local computer.</span></span>

### [<span data-ttu-id="8e608-128">Installera – skript</span><span class="sxs-lookup"><span data-stu-id="8e608-128">Install-Script</span></span>](Install-Script.md)
<span data-ttu-id="8e608-129">Installerar ett skript.</span><span class="sxs-lookup"><span data-stu-id="8e608-129">Installs a script.</span></span>

### [<span data-ttu-id="8e608-130">New-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="8e608-130">New-ScriptFileInfo</span></span>](New-ScriptFileInfo.md)
<span data-ttu-id="8e608-131">Skapar en skript fil med metadata.</span><span class="sxs-lookup"><span data-stu-id="8e608-131">Creates a script file with metadata.</span></span>

### [<span data-ttu-id="8e608-132">Publicera-modul</span><span class="sxs-lookup"><span data-stu-id="8e608-132">Publish-Module</span></span>](Publish-Module.md)
<span data-ttu-id="8e608-133">Publicerar en angiven modul från den lokala datorn till ett onlinegalleri.</span><span class="sxs-lookup"><span data-stu-id="8e608-133">Publishes a specified module from the local computer to an online gallery.</span></span>

### [<span data-ttu-id="8e608-134">Publicera – skript</span><span class="sxs-lookup"><span data-stu-id="8e608-134">Publish-Script</span></span>](Publish-Script.md)
<span data-ttu-id="8e608-135">Publicerar ett skript.</span><span class="sxs-lookup"><span data-stu-id="8e608-135">Publishes a script.</span></span>

### [<span data-ttu-id="8e608-136">Registrera – PSRepository</span><span class="sxs-lookup"><span data-stu-id="8e608-136">Register-PSRepository</span></span>](Register-PSRepository.md)
<span data-ttu-id="8e608-137">Registrerar en PowerShell-lagringsplats.</span><span class="sxs-lookup"><span data-stu-id="8e608-137">Registers a PowerShell repository.</span></span>

### [<span data-ttu-id="8e608-138">Spara-modul</span><span class="sxs-lookup"><span data-stu-id="8e608-138">Save-Module</span></span>](Save-Module.md)
<span data-ttu-id="8e608-139">Sparar en modul och dess beroenden på den lokala datorn, men installerar inte modulen.</span><span class="sxs-lookup"><span data-stu-id="8e608-139">Saves a module and its dependencies on the local computer but doesn't install the module.</span></span>

### [<span data-ttu-id="8e608-140">Spara – skript</span><span class="sxs-lookup"><span data-stu-id="8e608-140">Save-Script</span></span>](Save-Script.md)
<span data-ttu-id="8e608-141">Sparar ett skript.</span><span class="sxs-lookup"><span data-stu-id="8e608-141">Saves a script.</span></span>

### [<span data-ttu-id="8e608-142">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="8e608-142">Set-PSRepository</span></span>](Set-PSRepository.md)
<span data-ttu-id="8e608-143">Anger värden för en registrerad lagrings plats.</span><span class="sxs-lookup"><span data-stu-id="8e608-143">Sets values for a registered repository.</span></span>

### [<span data-ttu-id="8e608-144">Test-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="8e608-144">Test-ScriptFileInfo</span></span>](Test-ScriptFileInfo.md)
<span data-ttu-id="8e608-145">Verifierar ett kommentar block för ett skript.</span><span class="sxs-lookup"><span data-stu-id="8e608-145">Validates a comment block for a script.</span></span>

### [<span data-ttu-id="8e608-146">Avinstallera-modul</span><span class="sxs-lookup"><span data-stu-id="8e608-146">Uninstall-Module</span></span>](Uninstall-Module.md)
<span data-ttu-id="8e608-147">Avinstallerar en modul.</span><span class="sxs-lookup"><span data-stu-id="8e608-147">Uninstalls a module.</span></span>

### [<span data-ttu-id="8e608-148">Avinstallera – skript</span><span class="sxs-lookup"><span data-stu-id="8e608-148">Uninstall-Script</span></span>](Uninstall-Script.md)
<span data-ttu-id="8e608-149">Avinstallerar ett skript.</span><span class="sxs-lookup"><span data-stu-id="8e608-149">Uninstalls a script.</span></span>

### [<span data-ttu-id="8e608-150">Avregistrera-PSRepository</span><span class="sxs-lookup"><span data-stu-id="8e608-150">Unregister-PSRepository</span></span>](Unregister-PSRepository.md)
<span data-ttu-id="8e608-151">Avregistrerar en lagrings plats.</span><span class="sxs-lookup"><span data-stu-id="8e608-151">Unregisters a repository.</span></span>

### [<span data-ttu-id="8e608-152">Update-modul</span><span class="sxs-lookup"><span data-stu-id="8e608-152">Update-Module</span></span>](Update-Module.md)
<span data-ttu-id="8e608-153">Hämtar och installerar den senaste versionen av angivna moduler från ett onlinegalleri till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="8e608-153">Downloads and installs the newest version of specified modules from an online gallery to the local computer.</span></span>

### [<span data-ttu-id="8e608-154">Uppdatera – ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="8e608-154">Update-ModuleManifest</span></span>](Update-ModuleManifest.md)
<span data-ttu-id="8e608-155">Uppdaterar en modul manifest fil.</span><span class="sxs-lookup"><span data-stu-id="8e608-155">Updates a module manifest file.</span></span>

### [<span data-ttu-id="8e608-156">Uppdatera skript</span><span class="sxs-lookup"><span data-stu-id="8e608-156">Update-Script</span></span>](Update-Script.md)
<span data-ttu-id="8e608-157">Uppdaterar ett skript.</span><span class="sxs-lookup"><span data-stu-id="8e608-157">Updates a script.</span></span>

### [<span data-ttu-id="8e608-158">Update-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="8e608-158">Update-ScriptFileInfo</span></span>](Update-ScriptFileInfo.md)
<span data-ttu-id="8e608-159">Uppdaterings information för ett skript.</span><span class="sxs-lookup"><span data-stu-id="8e608-159">Updates information for a script.</span></span>
