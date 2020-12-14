---
description: Visar en lista över de cmdletar som har utformats för användning med PowerShell-leverantörer.
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_core_commands?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Core_Commands
ms.openlocfilehash: 1f023c5a66265f561ef6644afdc45cd0149f35b7
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710663"
---
# <a name="about-core-commands"></a><span data-ttu-id="70a1c-103">Om Core-kommandon</span><span class="sxs-lookup"><span data-stu-id="70a1c-103">About Core Commands</span></span>

## <a name="short-description"></a><span data-ttu-id="70a1c-104">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="70a1c-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="70a1c-105">Visar en lista över de cmdletar som har utformats för användning med PowerShell-leverantörer.</span><span class="sxs-lookup"><span data-stu-id="70a1c-105">Lists the cmdlets that are designed for use with PowerShell providers.</span></span>

## <a name="long-description"></a><span data-ttu-id="70a1c-106">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="70a1c-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="70a1c-107">PowerShell innehåller en uppsättning cmdletar som är särskilt utformade för att hantera objekt i data lager som exponeras av PowerShell-leverantörer.</span><span class="sxs-lookup"><span data-stu-id="70a1c-107">PowerShell includes a set of cmdlets that are specifically designed to manage the items in the data stores that are exposed by PowerShell providers.</span></span>
<span data-ttu-id="70a1c-108">Du kan använda dessa cmdlets på samma sätt för att hantera alla olika typer av data som providern gör tillgängliga för dig.</span><span class="sxs-lookup"><span data-stu-id="70a1c-108">You can use these cmdlets in the same ways to manage all the different types of data that the providers make available to you.</span></span> <span data-ttu-id="70a1c-109">Om du vill ha mer information om leverantörer skriver du "Get-Help about_providers".</span><span class="sxs-lookup"><span data-stu-id="70a1c-109">For more information about providers, type "get-help about_providers".</span></span>

<span data-ttu-id="70a1c-110">Du kan till exempel använda cmdleten Get-ChildItem för att lista filerna i en fil system katalog, nycklar under en register nyckel eller de objekt som exponeras av en provider som du skriver eller hämtar.</span><span class="sxs-lookup"><span data-stu-id="70a1c-110">For example, you can use the Get-ChildItem cmdlet to list the files in a file system directory, the keys under a registry key, or the items that are exposed by a provider that you write or download.</span></span>

<span data-ttu-id="70a1c-111">Följande är en lista över PowerShell-cmdletar som har utformats för användning med providers:</span><span class="sxs-lookup"><span data-stu-id="70a1c-111">The following is a list of the PowerShell cmdlets that are designed for use with providers:</span></span>

<span data-ttu-id="70a1c-112">ChildItem-cmdletar</span><span class="sxs-lookup"><span data-stu-id="70a1c-112">ChildItem cmdlets</span></span>

- <span data-ttu-id="70a1c-113">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="70a1c-113">Get-ChildItem</span></span>

<span data-ttu-id="70a1c-114">Innehålls-cmdletar</span><span class="sxs-lookup"><span data-stu-id="70a1c-114">Content cmdlets</span></span>

- <span data-ttu-id="70a1c-115">Add-Content</span><span class="sxs-lookup"><span data-stu-id="70a1c-115">Add-Content</span></span>
- <span data-ttu-id="70a1c-116">Clear-Content</span><span class="sxs-lookup"><span data-stu-id="70a1c-116">Clear-Content</span></span>
- <span data-ttu-id="70a1c-117">Get-Content</span><span class="sxs-lookup"><span data-stu-id="70a1c-117">Get-Content</span></span>
- <span data-ttu-id="70a1c-118">Set-Content</span><span class="sxs-lookup"><span data-stu-id="70a1c-118">Set-Content</span></span>

<span data-ttu-id="70a1c-119">Objekt-cmdletar</span><span class="sxs-lookup"><span data-stu-id="70a1c-119">Item cmdlets</span></span>

- <span data-ttu-id="70a1c-120">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="70a1c-120">Clear-Item</span></span>
- <span data-ttu-id="70a1c-121">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="70a1c-121">Copy-Item</span></span>
- <span data-ttu-id="70a1c-122">Get-Item</span><span class="sxs-lookup"><span data-stu-id="70a1c-122">Get-Item</span></span>
- <span data-ttu-id="70a1c-123">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="70a1c-123">Invoke-Item</span></span>
- <span data-ttu-id="70a1c-124">Move-Item</span><span class="sxs-lookup"><span data-stu-id="70a1c-124">Move-Item</span></span>
- <span data-ttu-id="70a1c-125">New-Item</span><span class="sxs-lookup"><span data-stu-id="70a1c-125">New-Item</span></span>
- <span data-ttu-id="70a1c-126">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="70a1c-126">Remove-Item</span></span>
- <span data-ttu-id="70a1c-127">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="70a1c-127">Rename-Item</span></span>
- <span data-ttu-id="70a1c-128">Set-Item</span><span class="sxs-lookup"><span data-stu-id="70a1c-128">Set-Item</span></span>

<span data-ttu-id="70a1c-129">ItemProperty-cmdletar</span><span class="sxs-lookup"><span data-stu-id="70a1c-129">ItemProperty cmdlets</span></span>

- <span data-ttu-id="70a1c-130">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="70a1c-130">Clear-ItemProperty</span></span>
- <span data-ttu-id="70a1c-131">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="70a1c-131">Copy-ItemProperty</span></span>
- <span data-ttu-id="70a1c-132">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="70a1c-132">Get-ItemProperty</span></span>
- <span data-ttu-id="70a1c-133">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="70a1c-133">Move-ItemProperty</span></span>
- <span data-ttu-id="70a1c-134">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="70a1c-134">New-ItemProperty</span></span>
- <span data-ttu-id="70a1c-135">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="70a1c-135">Remove-ItemProperty</span></span>
- <span data-ttu-id="70a1c-136">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="70a1c-136">Rename-ItemProperty</span></span>
- <span data-ttu-id="70a1c-137">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="70a1c-137">Set-ItemProperty</span></span>

<span data-ttu-id="70a1c-138">Plats-cmdletar</span><span class="sxs-lookup"><span data-stu-id="70a1c-138">Location cmdlets</span></span>

- <span data-ttu-id="70a1c-139">Get-Location</span><span class="sxs-lookup"><span data-stu-id="70a1c-139">Get-Location</span></span>
- <span data-ttu-id="70a1c-140">Pop-Location</span><span class="sxs-lookup"><span data-stu-id="70a1c-140">Pop-Location</span></span>
- <span data-ttu-id="70a1c-141">Push-Location</span><span class="sxs-lookup"><span data-stu-id="70a1c-141">Push-Location</span></span>
- <span data-ttu-id="70a1c-142">Set-Location</span><span class="sxs-lookup"><span data-stu-id="70a1c-142">Set-Location</span></span>

<span data-ttu-id="70a1c-143">Sök vägs-cmdletar</span><span class="sxs-lookup"><span data-stu-id="70a1c-143">Path cmdlets</span></span>

- <span data-ttu-id="70a1c-144">Join-Path</span><span class="sxs-lookup"><span data-stu-id="70a1c-144">Join-Path</span></span>
- <span data-ttu-id="70a1c-145">Convert-Path</span><span class="sxs-lookup"><span data-stu-id="70a1c-145">Convert-Path</span></span>
- <span data-ttu-id="70a1c-146">Split-Path</span><span class="sxs-lookup"><span data-stu-id="70a1c-146">Split-Path</span></span>
- <span data-ttu-id="70a1c-147">Resolve-Path</span><span class="sxs-lookup"><span data-stu-id="70a1c-147">Resolve-Path</span></span>
- <span data-ttu-id="70a1c-148">Test-Path</span><span class="sxs-lookup"><span data-stu-id="70a1c-148">Test-Path</span></span>

<span data-ttu-id="70a1c-149">PSDrive-cmdletar</span><span class="sxs-lookup"><span data-stu-id="70a1c-149">PSDrive cmdlets</span></span>

- <span data-ttu-id="70a1c-150">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="70a1c-150">Get-PSDrive</span></span>
- <span data-ttu-id="70a1c-151">New-PSDrive</span><span class="sxs-lookup"><span data-stu-id="70a1c-151">New-PSDrive</span></span>
- <span data-ttu-id="70a1c-152">Remove-PSDrive</span><span class="sxs-lookup"><span data-stu-id="70a1c-152">Remove-PSDrive</span></span>

<span data-ttu-id="70a1c-153">PSProvider-cmdletar</span><span class="sxs-lookup"><span data-stu-id="70a1c-153">PSProvider cmdlets</span></span>

- <span data-ttu-id="70a1c-154">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="70a1c-154">Get-PSProvider</span></span>

<span data-ttu-id="70a1c-155">Om du vill ha mer information om en cmdlet skriver du `get-help <cmdlet-name>` .</span><span class="sxs-lookup"><span data-stu-id="70a1c-155">For more information about a cmdlet, type `get-help <cmdlet-name>`.</span></span>

## <a name="see-also"></a><span data-ttu-id="70a1c-156">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="70a1c-156">SEE ALSO</span></span>

[<span data-ttu-id="70a1c-157">about_Providers</span><span class="sxs-lookup"><span data-stu-id="70a1c-157">about_Providers</span></span>](about_Providers.md)

