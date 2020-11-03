---
description: Visar en lista över de cmdletar som har utformats för användning med PowerShell-leverantörer.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_core_commands?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Core_Commands
ms.openlocfilehash: 5c784518ae30108813d32497f654198e7d10b379
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270074"
---
# <a name="about-core-commands"></a><span data-ttu-id="9e8d3-104">Om Core-kommandon</span><span class="sxs-lookup"><span data-stu-id="9e8d3-104">About Core Commands</span></span>

## <a name="short-description"></a><span data-ttu-id="9e8d3-105">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="9e8d3-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="9e8d3-106">Visar en lista över de cmdletar som har utformats för användning med PowerShell-leverantörer.</span><span class="sxs-lookup"><span data-stu-id="9e8d3-106">Lists the cmdlets that are designed for use with PowerShell providers.</span></span>

## <a name="long-description"></a><span data-ttu-id="9e8d3-107">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="9e8d3-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="9e8d3-108">PowerShell innehåller en uppsättning cmdletar som är särskilt utformade för att hantera objekt i data lager som exponeras av PowerShell-leverantörer.</span><span class="sxs-lookup"><span data-stu-id="9e8d3-108">PowerShell includes a set of cmdlets that are specifically designed to manage the items in the data stores that are exposed by PowerShell providers.</span></span>
<span data-ttu-id="9e8d3-109">Du kan använda dessa cmdlets på samma sätt för att hantera alla olika typer av data som providern gör tillgängliga för dig.</span><span class="sxs-lookup"><span data-stu-id="9e8d3-109">You can use these cmdlets in the same ways to manage all the different types of data that the providers make available to you.</span></span> <span data-ttu-id="9e8d3-110">Om du vill ha mer information om leverantörer skriver du "Get-Help about_providers".</span><span class="sxs-lookup"><span data-stu-id="9e8d3-110">For more information about providers, type "get-help about_providers".</span></span>

<span data-ttu-id="9e8d3-111">Du kan till exempel använda cmdleten Get-ChildItem för att lista filerna i en fil system katalog, nycklar under en register nyckel eller de objekt som exponeras av en provider som du skriver eller hämtar.</span><span class="sxs-lookup"><span data-stu-id="9e8d3-111">For example, you can use the Get-ChildItem cmdlet to list the files in a file system directory, the keys under a registry key, or the items that are exposed by a provider that you write or download.</span></span>

<span data-ttu-id="9e8d3-112">Följande är en lista över PowerShell-cmdletar som har utformats för användning med providers:</span><span class="sxs-lookup"><span data-stu-id="9e8d3-112">The following is a list of the PowerShell cmdlets that are designed for use with providers:</span></span>

<span data-ttu-id="9e8d3-113">ChildItem-cmdletar</span><span class="sxs-lookup"><span data-stu-id="9e8d3-113">ChildItem cmdlets</span></span>

- <span data-ttu-id="9e8d3-114">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="9e8d3-114">Get-ChildItem</span></span>

<span data-ttu-id="9e8d3-115">Innehålls-cmdletar</span><span class="sxs-lookup"><span data-stu-id="9e8d3-115">Content cmdlets</span></span>

- <span data-ttu-id="9e8d3-116">Add-Content</span><span class="sxs-lookup"><span data-stu-id="9e8d3-116">Add-Content</span></span>
- <span data-ttu-id="9e8d3-117">Clear-Content</span><span class="sxs-lookup"><span data-stu-id="9e8d3-117">Clear-Content</span></span>
- <span data-ttu-id="9e8d3-118">Get-Content</span><span class="sxs-lookup"><span data-stu-id="9e8d3-118">Get-Content</span></span>
- <span data-ttu-id="9e8d3-119">Set-Content</span><span class="sxs-lookup"><span data-stu-id="9e8d3-119">Set-Content</span></span>

<span data-ttu-id="9e8d3-120">Objekt-cmdletar</span><span class="sxs-lookup"><span data-stu-id="9e8d3-120">Item cmdlets</span></span>

- <span data-ttu-id="9e8d3-121">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="9e8d3-121">Clear-Item</span></span>
- <span data-ttu-id="9e8d3-122">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="9e8d3-122">Copy-Item</span></span>
- <span data-ttu-id="9e8d3-123">Get-Item</span><span class="sxs-lookup"><span data-stu-id="9e8d3-123">Get-Item</span></span>
- <span data-ttu-id="9e8d3-124">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="9e8d3-124">Invoke-Item</span></span>
- <span data-ttu-id="9e8d3-125">Move-Item</span><span class="sxs-lookup"><span data-stu-id="9e8d3-125">Move-Item</span></span>
- <span data-ttu-id="9e8d3-126">New-Item</span><span class="sxs-lookup"><span data-stu-id="9e8d3-126">New-Item</span></span>
- <span data-ttu-id="9e8d3-127">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="9e8d3-127">Remove-Item</span></span>
- <span data-ttu-id="9e8d3-128">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="9e8d3-128">Rename-Item</span></span>
- <span data-ttu-id="9e8d3-129">Set-Item</span><span class="sxs-lookup"><span data-stu-id="9e8d3-129">Set-Item</span></span>

<span data-ttu-id="9e8d3-130">ItemProperty-cmdletar</span><span class="sxs-lookup"><span data-stu-id="9e8d3-130">ItemProperty cmdlets</span></span>

- <span data-ttu-id="9e8d3-131">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="9e8d3-131">Clear-ItemProperty</span></span>
- <span data-ttu-id="9e8d3-132">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="9e8d3-132">Copy-ItemProperty</span></span>
- <span data-ttu-id="9e8d3-133">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="9e8d3-133">Get-ItemProperty</span></span>
- <span data-ttu-id="9e8d3-134">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="9e8d3-134">Move-ItemProperty</span></span>
- <span data-ttu-id="9e8d3-135">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="9e8d3-135">New-ItemProperty</span></span>
- <span data-ttu-id="9e8d3-136">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="9e8d3-136">Remove-ItemProperty</span></span>
- <span data-ttu-id="9e8d3-137">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="9e8d3-137">Rename-ItemProperty</span></span>
- <span data-ttu-id="9e8d3-138">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="9e8d3-138">Set-ItemProperty</span></span>

<span data-ttu-id="9e8d3-139">Plats-cmdletar</span><span class="sxs-lookup"><span data-stu-id="9e8d3-139">Location cmdlets</span></span>

- <span data-ttu-id="9e8d3-140">Get-Location</span><span class="sxs-lookup"><span data-stu-id="9e8d3-140">Get-Location</span></span>
- <span data-ttu-id="9e8d3-141">Pop-Location</span><span class="sxs-lookup"><span data-stu-id="9e8d3-141">Pop-Location</span></span>
- <span data-ttu-id="9e8d3-142">Push-Location</span><span class="sxs-lookup"><span data-stu-id="9e8d3-142">Push-Location</span></span>
- <span data-ttu-id="9e8d3-143">Set-Location</span><span class="sxs-lookup"><span data-stu-id="9e8d3-143">Set-Location</span></span>

<span data-ttu-id="9e8d3-144">Sök vägs-cmdletar</span><span class="sxs-lookup"><span data-stu-id="9e8d3-144">Path cmdlets</span></span>

- <span data-ttu-id="9e8d3-145">Join-Path</span><span class="sxs-lookup"><span data-stu-id="9e8d3-145">Join-Path</span></span>
- <span data-ttu-id="9e8d3-146">Convert-Path</span><span class="sxs-lookup"><span data-stu-id="9e8d3-146">Convert-Path</span></span>
- <span data-ttu-id="9e8d3-147">Split-Path</span><span class="sxs-lookup"><span data-stu-id="9e8d3-147">Split-Path</span></span>
- <span data-ttu-id="9e8d3-148">Resolve-Path</span><span class="sxs-lookup"><span data-stu-id="9e8d3-148">Resolve-Path</span></span>
- <span data-ttu-id="9e8d3-149">Test-Path</span><span class="sxs-lookup"><span data-stu-id="9e8d3-149">Test-Path</span></span>

<span data-ttu-id="9e8d3-150">PSDrive-cmdletar</span><span class="sxs-lookup"><span data-stu-id="9e8d3-150">PSDrive cmdlets</span></span>

- <span data-ttu-id="9e8d3-151">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="9e8d3-151">Get-PSDrive</span></span>
- <span data-ttu-id="9e8d3-152">New-PSDrive</span><span class="sxs-lookup"><span data-stu-id="9e8d3-152">New-PSDrive</span></span>
- <span data-ttu-id="9e8d3-153">Remove-PSDrive</span><span class="sxs-lookup"><span data-stu-id="9e8d3-153">Remove-PSDrive</span></span>

<span data-ttu-id="9e8d3-154">PSProvider-cmdletar</span><span class="sxs-lookup"><span data-stu-id="9e8d3-154">PSProvider cmdlets</span></span>

- <span data-ttu-id="9e8d3-155">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="9e8d3-155">Get-PSProvider</span></span>

<span data-ttu-id="9e8d3-156">Om du vill ha mer information om en cmdlet skriver du `get-help <cmdlet-name>` .</span><span class="sxs-lookup"><span data-stu-id="9e8d3-156">For more information about a cmdlet, type `get-help <cmdlet-name>`.</span></span>

## <a name="see-also"></a><span data-ttu-id="9e8d3-157">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="9e8d3-157">SEE ALSO</span></span>

[<span data-ttu-id="9e8d3-158">about_Providers</span><span class="sxs-lookup"><span data-stu-id="9e8d3-158">about_Providers</span></span>](about_Providers.md)
