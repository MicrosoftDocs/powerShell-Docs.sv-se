---
Download Help Link: https://go.microsoft.com/fwlink/?LinkId=393271
Help Version: 5.2.0.0
keywords: powershell,cmdlet
Locale: en-US
Module Guid: 1d73a601-4a6c-43c5-ba3f-619b18bbb404
Module Name: PowerShellGet
ms.date: 06/09/2017
schema: 2.0.0
title: PowerShellGet
ms.openlocfilehash: 130582b1b9f18a8f6ada7c009c6d25a7dab75e46
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94890720"
---
# <span data-ttu-id="d3d98-103">PowerShellGet-modul</span><span class="sxs-lookup"><span data-stu-id="d3d98-103">PowerShellGet Module</span></span>

## <span data-ttu-id="d3d98-104">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d3d98-104">Description</span></span>

<span data-ttu-id="d3d98-105">PowerShellGet är en modul med kommandon för att upptäcka, installera, uppdatera och publicera PowerShell-artefakter som moduler, DSC-resurser, roll funktioner och skript.</span><span class="sxs-lookup"><span data-stu-id="d3d98-105">PowerShellGet is a module with commands for discovering, installing, updating and publishing PowerShell artifacts like Modules, DSC Resources, Role Capabilities, and Scripts.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d3d98-106">Från och med april 2020 stöder PowerShell-galleriet inte längre Transport Layer Security (TLS), version 1,0 och 1,1.</span><span class="sxs-lookup"><span data-stu-id="d3d98-106">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="d3d98-107">Om du inte använder TLS 1,2 eller senare visas ett fel meddelande när du försöker få åtkomst till PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="d3d98-107">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="d3d98-108">Använd följande kommando för att se till att du använder TLS 1,2:</span><span class="sxs-lookup"><span data-stu-id="d3d98-108">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="d3d98-109">Mer information finns i [meddelandet](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) i PowerShell-bloggen.</span><span class="sxs-lookup"><span data-stu-id="d3d98-109">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="d3d98-110">PowerShellGet-cmdletar</span><span class="sxs-lookup"><span data-stu-id="d3d98-110">PowerShellGet Cmdlets</span></span>

### [<span data-ttu-id="d3d98-111">Sök-kommando</span><span class="sxs-lookup"><span data-stu-id="d3d98-111">Find-Command</span></span>](Find-Command.md)
<span data-ttu-id="d3d98-112">Söker efter PowerShell-kommandon i moduler.</span><span class="sxs-lookup"><span data-stu-id="d3d98-112">Finds PowerShell commands in modules.</span></span>

### [<span data-ttu-id="d3d98-113">Find-Dscresource Keyword Supports</span><span class="sxs-lookup"><span data-stu-id="d3d98-113">Find-DscResource</span></span>](Find-DscResource.md)
<span data-ttu-id="d3d98-114">Söker efter en DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="d3d98-114">Finds a DSC resource.</span></span>

### [<span data-ttu-id="d3d98-115">Sök-modul</span><span class="sxs-lookup"><span data-stu-id="d3d98-115">Find-Module</span></span>](Find-Module.md)
<span data-ttu-id="d3d98-116">Söker efter moduler i en lagrings plats som matchar de angivna kriterierna.</span><span class="sxs-lookup"><span data-stu-id="d3d98-116">Finds modules in a repository that match specified criteria.</span></span>

### [<span data-ttu-id="d3d98-117">Find-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="d3d98-117">Find-RoleCapability</span></span>](Find-RoleCapability.md)
<span data-ttu-id="d3d98-118">Hittar roll funktioner i moduler.</span><span class="sxs-lookup"><span data-stu-id="d3d98-118">Finds role capabilities in modules.</span></span>

### [<span data-ttu-id="d3d98-119">Sök – skript</span><span class="sxs-lookup"><span data-stu-id="d3d98-119">Find-Script</span></span>](Find-Script.md)
<span data-ttu-id="d3d98-120">Söker efter ett skript.</span><span class="sxs-lookup"><span data-stu-id="d3d98-120">Finds a script.</span></span>

### [<span data-ttu-id="d3d98-121">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="d3d98-121">Get-InstalledModule</span></span>](Get-InstalledModule.md)
<span data-ttu-id="d3d98-122">Hämtar en lista över moduler på den dator som har installerats av PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="d3d98-122">Gets a list of modules on the computer that were installed by PowerShellGet.</span></span>

### [<span data-ttu-id="d3d98-123">Get-InstalledScript</span><span class="sxs-lookup"><span data-stu-id="d3d98-123">Get-InstalledScript</span></span>](Get-InstalledScript.md)
<span data-ttu-id="d3d98-124">Hämtar ett installerat skript.</span><span class="sxs-lookup"><span data-stu-id="d3d98-124">Gets an installed script.</span></span>

### [<span data-ttu-id="d3d98-125">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="d3d98-125">Get-PSRepository</span></span>](Get-PSRepository.md)
<span data-ttu-id="d3d98-126">Hämtar PowerShell-databaser.</span><span class="sxs-lookup"><span data-stu-id="d3d98-126">Gets PowerShell repositories.</span></span>

### [<span data-ttu-id="d3d98-127">Installera-modul</span><span class="sxs-lookup"><span data-stu-id="d3d98-127">Install-Module</span></span>](Install-Module.md)
<span data-ttu-id="d3d98-128">Laddar ned en eller flera moduler från en lagrings plats och installerar dem på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="d3d98-128">Downloads one or more modules from a repository, and installs them on the local computer.</span></span>

### [<span data-ttu-id="d3d98-129">Installera – skript</span><span class="sxs-lookup"><span data-stu-id="d3d98-129">Install-Script</span></span>](Install-Script.md)
<span data-ttu-id="d3d98-130">Installerar ett skript.</span><span class="sxs-lookup"><span data-stu-id="d3d98-130">Installs a script.</span></span>

### [<span data-ttu-id="d3d98-131">New-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="d3d98-131">New-ScriptFileInfo</span></span>](New-ScriptFileInfo.md)
<span data-ttu-id="d3d98-132">Skapar en skript fil med metadata.</span><span class="sxs-lookup"><span data-stu-id="d3d98-132">Creates a script file with metadata.</span></span>

### [<span data-ttu-id="d3d98-133">Publicera-modul</span><span class="sxs-lookup"><span data-stu-id="d3d98-133">Publish-Module</span></span>](Publish-Module.md)
<span data-ttu-id="d3d98-134">Publicerar en angiven modul från den lokala datorn till ett onlinegalleri.</span><span class="sxs-lookup"><span data-stu-id="d3d98-134">Publishes a specified module from the local computer to an online gallery.</span></span>

### [<span data-ttu-id="d3d98-135">Publicera – skript</span><span class="sxs-lookup"><span data-stu-id="d3d98-135">Publish-Script</span></span>](Publish-Script.md)
<span data-ttu-id="d3d98-136">Publicerar ett skript.</span><span class="sxs-lookup"><span data-stu-id="d3d98-136">Publishes a script.</span></span>

### [<span data-ttu-id="d3d98-137">Registrera – PSRepository</span><span class="sxs-lookup"><span data-stu-id="d3d98-137">Register-PSRepository</span></span>](Register-PSRepository.md)
<span data-ttu-id="d3d98-138">Registrerar en PowerShell-lagringsplats.</span><span class="sxs-lookup"><span data-stu-id="d3d98-138">Registers a PowerShell repository.</span></span>

### [<span data-ttu-id="d3d98-139">Spara-modul</span><span class="sxs-lookup"><span data-stu-id="d3d98-139">Save-Module</span></span>](Save-Module.md)
<span data-ttu-id="d3d98-140">Sparar en modul och dess beroenden på den lokala datorn, men installerar inte modulen.</span><span class="sxs-lookup"><span data-stu-id="d3d98-140">Saves a module and its dependencies on the local computer but doesn't install the module.</span></span>

### [<span data-ttu-id="d3d98-141">Spara – skript</span><span class="sxs-lookup"><span data-stu-id="d3d98-141">Save-Script</span></span>](Save-Script.md)
<span data-ttu-id="d3d98-142">Sparar ett skript.</span><span class="sxs-lookup"><span data-stu-id="d3d98-142">Saves a script.</span></span>

### [<span data-ttu-id="d3d98-143">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="d3d98-143">Set-PSRepository</span></span>](Set-PSRepository.md)
<span data-ttu-id="d3d98-144">Anger värden för en registrerad lagrings plats.</span><span class="sxs-lookup"><span data-stu-id="d3d98-144">Sets values for a registered repository.</span></span>

### [<span data-ttu-id="d3d98-145">Test-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="d3d98-145">Test-ScriptFileInfo</span></span>](Test-ScriptFileInfo.md)
<span data-ttu-id="d3d98-146">Verifierar ett kommentar block för ett skript.</span><span class="sxs-lookup"><span data-stu-id="d3d98-146">Validates a comment block for a script.</span></span>

### [<span data-ttu-id="d3d98-147">Avinstallera-modul</span><span class="sxs-lookup"><span data-stu-id="d3d98-147">Uninstall-Module</span></span>](Uninstall-Module.md)
<span data-ttu-id="d3d98-148">Avinstallerar en modul.</span><span class="sxs-lookup"><span data-stu-id="d3d98-148">Uninstalls a module.</span></span>

### [<span data-ttu-id="d3d98-149">Avinstallera – skript</span><span class="sxs-lookup"><span data-stu-id="d3d98-149">Uninstall-Script</span></span>](Uninstall-Script.md)
<span data-ttu-id="d3d98-150">Avinstallerar ett skript.</span><span class="sxs-lookup"><span data-stu-id="d3d98-150">Uninstalls a script.</span></span>

### [<span data-ttu-id="d3d98-151">Avregistrera-PSRepository</span><span class="sxs-lookup"><span data-stu-id="d3d98-151">Unregister-PSRepository</span></span>](Unregister-PSRepository.md)
<span data-ttu-id="d3d98-152">Avregistrerar en lagrings plats.</span><span class="sxs-lookup"><span data-stu-id="d3d98-152">Unregisters a repository.</span></span>

### [<span data-ttu-id="d3d98-153">Update-modul</span><span class="sxs-lookup"><span data-stu-id="d3d98-153">Update-Module</span></span>](Update-Module.md)
<span data-ttu-id="d3d98-154">Hämtar och installerar den senaste versionen av angivna moduler från ett onlinegalleri till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="d3d98-154">Downloads and installs the newest version of specified modules from an online gallery to the local computer.</span></span>

### [<span data-ttu-id="d3d98-155">Uppdatera – ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="d3d98-155">Update-ModuleManifest</span></span>](Update-ModuleManifest.md)
<span data-ttu-id="d3d98-156">Uppdaterar en modul manifest fil.</span><span class="sxs-lookup"><span data-stu-id="d3d98-156">Updates a module manifest file.</span></span>

### [<span data-ttu-id="d3d98-157">Uppdatera skript</span><span class="sxs-lookup"><span data-stu-id="d3d98-157">Update-Script</span></span>](Update-Script.md)
<span data-ttu-id="d3d98-158">Uppdaterar ett skript.</span><span class="sxs-lookup"><span data-stu-id="d3d98-158">Updates a script.</span></span>

### [<span data-ttu-id="d3d98-159">Update-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="d3d98-159">Update-ScriptFileInfo</span></span>](Update-ScriptFileInfo.md)
<span data-ttu-id="d3d98-160">Uppdaterings information för ett skript.</span><span class="sxs-lookup"><span data-stu-id="d3d98-160">Updates information for a script.</span></span>
