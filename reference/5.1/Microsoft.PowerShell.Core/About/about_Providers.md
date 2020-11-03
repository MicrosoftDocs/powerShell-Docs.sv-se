---
description: Beskriver hur PowerShell-leverantörer ger åtkomst till data och komponenter som annars inte är lättillgängliga på kommando raden. Data presenteras i ett konsekvent format som liknar en fil system enhet.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_providers?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Providers
ms.openlocfilehash: 952ab618f1e47f0f912209ba56c37a667c596aaf
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271485"
---
# <a name="about-providers"></a><span data-ttu-id="87fd6-105">Om leverantörer</span><span class="sxs-lookup"><span data-stu-id="87fd6-105">About Providers</span></span>

## <a name="short-description"></a><span data-ttu-id="87fd6-106">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="87fd6-106">Short description</span></span>
<span data-ttu-id="87fd6-107">Beskriver hur PowerShell-leverantörer ger åtkomst till data och komponenter som annars inte är lättillgängliga på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="87fd6-107">Describes how PowerShell providers provide access to data and components that wouldn't otherwise be easily accessible at the command line.</span></span>
<span data-ttu-id="87fd6-108">Data presenteras i ett konsekvent format som liknar en fil system enhet.</span><span class="sxs-lookup"><span data-stu-id="87fd6-108">The data is presented in a consistent format that resembles a file system drive.</span></span>

## <a name="long-description"></a><span data-ttu-id="87fd6-109">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="87fd6-109">Long description</span></span>

<span data-ttu-id="87fd6-110">PowerShell-leverantörer är .NET-program som ger åtkomst till specialiserade data lager för enklare visning och hantering.</span><span class="sxs-lookup"><span data-stu-id="87fd6-110">PowerShell providers are .NET programs that provide access to specialized data stores for easier viewing and management.</span></span> <span data-ttu-id="87fd6-111">Data visas i en enhet och du får åtkomst till data i en sökväg som du skulle göra på en hård disk.</span><span class="sxs-lookup"><span data-stu-id="87fd6-111">The data appears in a drive, and you access the data in a path like you would on a hard disk drive.</span></span> <span data-ttu-id="87fd6-112">Du kan använda någon av de inbyggda cmdletarna som providern stöder för att hantera data i leverantörs enheten.</span><span class="sxs-lookup"><span data-stu-id="87fd6-112">You can use any of the built-in cmdlets that the provider supports to manage the data in the provider drive.</span></span> <span data-ttu-id="87fd6-113">Du kan också använda anpassade cmdlets som är utformade särskilt för data.</span><span class="sxs-lookup"><span data-stu-id="87fd6-113">And, you can use custom cmdlets that are designed especially for the data.</span></span>

<span data-ttu-id="87fd6-114">Providers kan också lägga till dynamiska parametrar till de inbyggda cmdletarna.</span><span class="sxs-lookup"><span data-stu-id="87fd6-114">The providers can also add dynamic parameters to the built-in cmdlets.</span></span> <span data-ttu-id="87fd6-115">Dessa parametrar är bara tillgängliga när du använder-cmdlet: en med providerns data.</span><span class="sxs-lookup"><span data-stu-id="87fd6-115">These parameters are only available when you use the cmdlet with the provider data.</span></span>

## <a name="built-in-providers"></a><span data-ttu-id="87fd6-116">Inbyggda leverantörer</span><span class="sxs-lookup"><span data-stu-id="87fd6-116">Built-in providers</span></span>

<span data-ttu-id="87fd6-117">PowerShell innehåller en uppsättning inbyggda providers som du kan använda för att få åtkomst till olika typer av data lager.</span><span class="sxs-lookup"><span data-stu-id="87fd6-117">PowerShell includes a set of built-in providers that you can use to access the different types of data stores.</span></span>

| <span data-ttu-id="87fd6-118">Leverantör</span><span class="sxs-lookup"><span data-stu-id="87fd6-118">Provider</span></span>   |   <span data-ttu-id="87fd6-119">Enhet (er)</span><span class="sxs-lookup"><span data-stu-id="87fd6-119">Drive(s)</span></span>  |<span data-ttu-id="87fd6-120">OutputType</span><span class="sxs-lookup"><span data-stu-id="87fd6-120">OutputType</span></span>                                                    |
|----------- |------------ |--------------------------------------------------------------|
|<span data-ttu-id="87fd6-121">Alias</span><span class="sxs-lookup"><span data-stu-id="87fd6-121">Alias</span></span>       |<span data-ttu-id="87fd6-122">Aliasuppsättning</span><span class="sxs-lookup"><span data-stu-id="87fd6-122">Alias:</span></span>       |<span data-ttu-id="87fd6-123">System. Management. Automation. AliasInfo</span><span class="sxs-lookup"><span data-stu-id="87fd6-123">System.Management.Automation.AliasInfo</span></span>                        |
|<span data-ttu-id="87fd6-124">Certifikat</span><span class="sxs-lookup"><span data-stu-id="87fd6-124">Certificate</span></span> |<span data-ttu-id="87fd6-125">Certifikatet</span><span class="sxs-lookup"><span data-stu-id="87fd6-125">Cert:</span></span>        |<span data-ttu-id="87fd6-126">Microsoft. PowerShell. commands. X509StoreLocation</span><span class="sxs-lookup"><span data-stu-id="87fd6-126">Microsoft.PowerShell.Commands.X509StoreLocation</span></span>               |
|            |             |<span data-ttu-id="87fd6-127">System. Security. Cryptography. X509Certificates. X509Certificate2</span><span class="sxs-lookup"><span data-stu-id="87fd6-127">System.Security.Cryptography.X509Certificates.X509Certificate2</span></span>|
|<span data-ttu-id="87fd6-128">Miljö</span><span class="sxs-lookup"><span data-stu-id="87fd6-128">Environment</span></span> |<span data-ttu-id="87fd6-129">Kuvert</span><span class="sxs-lookup"><span data-stu-id="87fd6-129">Env:</span></span>         |<span data-ttu-id="87fd6-130">System. Collections. typen DictionaryEntry</span><span class="sxs-lookup"><span data-stu-id="87fd6-130">System.Collections.DictionaryEntry</span></span>                            |
|<span data-ttu-id="87fd6-131">Filsystem</span><span class="sxs-lookup"><span data-stu-id="87fd6-131">FileSystem</span></span>  |<span data-ttu-id="87fd6-132">C: (\*)</span><span class="sxs-lookup"><span data-stu-id="87fd6-132">C: (\*)</span></span>       |<span data-ttu-id="87fd6-133">System. IO. FileInfo</span><span class="sxs-lookup"><span data-stu-id="87fd6-133">System.IO.FileInfo</span></span>                                            |
|            |             |<span data-ttu-id="87fd6-134">System. IO. DirectoryInfo</span><span class="sxs-lookup"><span data-stu-id="87fd6-134">System.IO.DirectoryInfo</span></span>                                       |
|<span data-ttu-id="87fd6-135">Funktion</span><span class="sxs-lookup"><span data-stu-id="87fd6-135">Function</span></span>    |<span data-ttu-id="87fd6-136">Funktioner</span><span class="sxs-lookup"><span data-stu-id="87fd6-136">Function:</span></span>    |<span data-ttu-id="87fd6-137">System. Management. Automation. FunctionInfo</span><span class="sxs-lookup"><span data-stu-id="87fd6-137">System.Management.Automation.FunctionInfo</span></span>                     |
|<span data-ttu-id="87fd6-138">Register</span><span class="sxs-lookup"><span data-stu-id="87fd6-138">Registry</span></span>    |<span data-ttu-id="87fd6-139">HKLM: HKCU:</span><span class="sxs-lookup"><span data-stu-id="87fd6-139">HKLM: HKCU:</span></span>  |<span data-ttu-id="87fd6-140">Microsoft. Win32. RegistryKey</span><span class="sxs-lookup"><span data-stu-id="87fd6-140">Microsoft.Win32.RegistryKey</span></span>                                   |
|<span data-ttu-id="87fd6-141">Variabel</span><span class="sxs-lookup"><span data-stu-id="87fd6-141">Variable</span></span>    |<span data-ttu-id="87fd6-142">Variabel</span><span class="sxs-lookup"><span data-stu-id="87fd6-142">Variable:</span></span>    |<span data-ttu-id="87fd6-143">System. Management. Automation. PSVariable</span><span class="sxs-lookup"><span data-stu-id="87fd6-143">System.Management.Automation.PSVariable</span></span>                       |
|<span data-ttu-id="87fd6-144">WSMan</span><span class="sxs-lookup"><span data-stu-id="87fd6-144">WSMan</span></span>       |<span data-ttu-id="87fd6-145">WSMan</span><span class="sxs-lookup"><span data-stu-id="87fd6-145">WSMan:</span></span>       |<span data-ttu-id="87fd6-146">Microsoft. WSMan. Management. WSManConfigContainerElement</span><span class="sxs-lookup"><span data-stu-id="87fd6-146">Microsoft.WSMan.Management.WSManConfigContainerElement</span></span>        |

<span data-ttu-id="87fd6-147">(\*) Fil Systems enheterna varierar beroende på varje system.</span><span class="sxs-lookup"><span data-stu-id="87fd6-147">(\*) The FileSystem drives vary on each system.</span></span>

<span data-ttu-id="87fd6-148">Du kan också skapa egna PowerShell-leverantörer och du kan installera leverantörer som andra utvecklar.</span><span class="sxs-lookup"><span data-stu-id="87fd6-148">You can also create your own PowerShell providers, and you can install providers that others develop.</span></span> <span data-ttu-id="87fd6-149">Om du vill visa en lista över tillgängliga providers i sessionen skriver du:</span><span class="sxs-lookup"><span data-stu-id="87fd6-149">To list the providers that are available in your session, type:</span></span>

```powershell
Get-PSProvider
```

## <a name="installing-and-removing-providers"></a><span data-ttu-id="87fd6-150">Installera och ta bort providrar</span><span class="sxs-lookup"><span data-stu-id="87fd6-150">Installing and removing providers</span></span>

<span data-ttu-id="87fd6-151">Leverantörer installeras vanligt vis via PowerShell-moduler.</span><span class="sxs-lookup"><span data-stu-id="87fd6-151">Providers are typically installed via PowerShell modules.</span></span> <span data-ttu-id="87fd6-152">Importera modulen läser in providern i sessionen.</span><span class="sxs-lookup"><span data-stu-id="87fd6-152">Importing the module loads the provider into your session.</span></span> <span data-ttu-id="87fd6-153">Du kan inte avinstallera inbyggda providers.</span><span class="sxs-lookup"><span data-stu-id="87fd6-153">You can't uninstall the built-in providers.</span></span> <span data-ttu-id="87fd6-154">Du kan avinstallera providrar som har lästs in av andra moduler.</span><span class="sxs-lookup"><span data-stu-id="87fd6-154">You can uninstall providers loaded by other modules.</span></span>

<span data-ttu-id="87fd6-155">Du kan ta bort en provider från den aktuella sessionen med hjälp av `Remove-Module` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="87fd6-155">You can unload a provider from the current session using the `Remove-Module` cmdlet.</span></span> <span data-ttu-id="87fd6-156">Denna cmdlet avinstallerar inte providern, men den gör att providern inte är tillgänglig i sessionen.</span><span class="sxs-lookup"><span data-stu-id="87fd6-156">This cmdlet doesn't uninstall the provider, but it makes the provider unavailable in the session.</span></span>

<span data-ttu-id="87fd6-157">Du kan också använda `Remove-PSDrive` cmdleten för att ta bort alla enheter från den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="87fd6-157">You can also use the `Remove-PSDrive` cmdlet to remove any drive from the current session.</span></span> <span data-ttu-id="87fd6-158">Dessa data på enheten påverkas inte, men enheten är inte längre tillgänglig i den sessionen.</span><span class="sxs-lookup"><span data-stu-id="87fd6-158">This data on the drive isn't affected, but the drive is no longer available in that session.</span></span>

## <a name="viewing-providers"></a><span data-ttu-id="87fd6-159">Visa leverantörer</span><span class="sxs-lookup"><span data-stu-id="87fd6-159">Viewing providers</span></span>

<span data-ttu-id="87fd6-160">Om du vill visa PowerShell-providern på datorn skriver du:</span><span class="sxs-lookup"><span data-stu-id="87fd6-160">To view the PowerShell providers on your computer, type:</span></span>

```powershell
Get-PSProvider
```

<span data-ttu-id="87fd6-161">I utdata visas de inbyggda providers och providers som du har lagt till i sessionen.</span><span class="sxs-lookup"><span data-stu-id="87fd6-161">The output lists the built-in providers and the providers that you added to the session.</span></span>

## <a name="the-provider-cmdlets"></a><span data-ttu-id="87fd6-162">Provider-cmdletar</span><span class="sxs-lookup"><span data-stu-id="87fd6-162">The provider cmdlets</span></span>

<span data-ttu-id="87fd6-163">Följande cmdletar är utformade för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="87fd6-163">The following cmdlets are designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="87fd6-164">Du kan använda samma cmdlets på samma sätt för att hantera de olika typer av data som providern visar.</span><span class="sxs-lookup"><span data-stu-id="87fd6-164">You can use the same cmdlets in the same way to manage the different types of data that providers expose.</span></span> <span data-ttu-id="87fd6-165">När du har lärt dig att hantera data från en leverantör kan du använda samma procedurer med data från valfri Provider.</span><span class="sxs-lookup"><span data-stu-id="87fd6-165">After you learn to manage the data of one provider, you can use the same procedures with the data from any provider.</span></span>

<span data-ttu-id="87fd6-166">Till exempel `New-Item` skapar cmdleten ett nytt objekt.</span><span class="sxs-lookup"><span data-stu-id="87fd6-166">For example, the `New-Item` cmdlet creates a new item.</span></span> <span data-ttu-id="87fd6-167">I den `C:` enhet som stöds av **fil** tjänst leverantören kan du använda `New-Item` för att skapa en ny fil eller mapp.</span><span class="sxs-lookup"><span data-stu-id="87fd6-167">In the `C:` drive that is supported by the **FileSystem** provider, you can use `New-Item` to create a new file or folder.</span></span> <span data-ttu-id="87fd6-168">I de enheter som stöds av **Registry** -providern kan du använda `New-Item` för att skapa en ny register nyckel.</span><span class="sxs-lookup"><span data-stu-id="87fd6-168">In the drives that are supported by the **Registry** provider, you can use `New-Item` to create a new registry key.</span></span> <span data-ttu-id="87fd6-169">I `Alias:` enheten kan du använda `New-Item` för att skapa ett nytt alias.</span><span class="sxs-lookup"><span data-stu-id="87fd6-169">In the `Alias:` drive, you can use `New-Item` to create a new alias.</span></span>

<span data-ttu-id="87fd6-170">Om du vill ha detaljerad information om någon av följande cmdletar skriver du:</span><span class="sxs-lookup"><span data-stu-id="87fd6-170">For detailed information about any of the following cmdlets, type:</span></span>

```
Get-Help <cmdlet-name> -Detailed
```

### <a name="childitem-cmdlets"></a><span data-ttu-id="87fd6-171">ChildItem-cmdletar</span><span class="sxs-lookup"><span data-stu-id="87fd6-171">ChildItem cmdlets</span></span>

- [<span data-ttu-id="87fd6-172">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="87fd6-172">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="content-cmdlets"></a><span data-ttu-id="87fd6-173">Innehålls-cmdletar</span><span class="sxs-lookup"><span data-stu-id="87fd6-173">Content Cmdlets</span></span>

- [<span data-ttu-id="87fd6-174">Lägg till innehåll</span><span class="sxs-lookup"><span data-stu-id="87fd6-174">Add-Content</span></span>](xref:Microsoft.PowerShell.Management.Add-Content)
- [<span data-ttu-id="87fd6-175">Rensa innehåll</span><span class="sxs-lookup"><span data-stu-id="87fd6-175">Clear-Content</span></span>](xref:Microsoft.PowerShell.Management.Clear-Content)
- [<span data-ttu-id="87fd6-176">Hämta innehåll</span><span class="sxs-lookup"><span data-stu-id="87fd6-176">Get-Content</span></span>](xref:Microsoft.PowerShell.Management.Get-Content)
- [<span data-ttu-id="87fd6-177">Ange innehåll</span><span class="sxs-lookup"><span data-stu-id="87fd6-177">Set-Content</span></span>](xref:Microsoft.PowerShell.Management.Set-Content)

### <a name="item-cmdlets"></a><span data-ttu-id="87fd6-178">Objekt-cmdletar</span><span class="sxs-lookup"><span data-stu-id="87fd6-178">Item Cmdlets</span></span>

- [<span data-ttu-id="87fd6-179">Rensa objekt</span><span class="sxs-lookup"><span data-stu-id="87fd6-179">Clear-Item</span></span>](xref:Microsoft.PowerShell.Management.Clear-Item)
- [<span data-ttu-id="87fd6-180">Kopiera objekt</span><span class="sxs-lookup"><span data-stu-id="87fd6-180">Copy-Item</span></span>](xref:Microsoft.PowerShell.Management.Copy-Item)
- [<span data-ttu-id="87fd6-181">Hämta objekt</span><span class="sxs-lookup"><span data-stu-id="87fd6-181">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="87fd6-182">Anropa-objekt</span><span class="sxs-lookup"><span data-stu-id="87fd6-182">Invoke-Item</span></span>](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [<span data-ttu-id="87fd6-183">Flytta objekt</span><span class="sxs-lookup"><span data-stu-id="87fd6-183">Move-Item</span></span>](xref:Microsoft.PowerShell.Management.Move-Item)
- [<span data-ttu-id="87fd6-184">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="87fd6-184">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="87fd6-185">Ta bort objekt</span><span class="sxs-lookup"><span data-stu-id="87fd6-185">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="87fd6-186">Byt namn – objekt</span><span class="sxs-lookup"><span data-stu-id="87fd6-186">Rename-Item</span></span>](xref:Microsoft.PowerShell.Management.Rename-Item)
- [<span data-ttu-id="87fd6-187">Ange objekt</span><span class="sxs-lookup"><span data-stu-id="87fd6-187">Set-Item</span></span>](xref:Microsoft.PowerShell.Management.Set-Item)

### <a name="itemproperty-cmdlets"></a><span data-ttu-id="87fd6-188">ItemProperty-cmdletar</span><span class="sxs-lookup"><span data-stu-id="87fd6-188">ItemProperty cmdlets</span></span>

- [<span data-ttu-id="87fd6-189">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="87fd6-189">Clear-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [<span data-ttu-id="87fd6-190">Kopiera – ItemProperty</span><span class="sxs-lookup"><span data-stu-id="87fd6-190">Copy-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Copy-ItemProperty)
- [<span data-ttu-id="87fd6-191">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="87fd6-191">Get-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [<span data-ttu-id="87fd6-192">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="87fd6-192">Move-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Move-ItemProperty)
- [<span data-ttu-id="87fd6-193">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="87fd6-193">New-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.New-ItemProperty)
- [<span data-ttu-id="87fd6-194">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="87fd6-194">Remove-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)
- [<span data-ttu-id="87fd6-195">Byt namn – ItemProperty</span><span class="sxs-lookup"><span data-stu-id="87fd6-195">Rename-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Rename-ItemProperty)
- [<span data-ttu-id="87fd6-196">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="87fd6-196">Set-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)

### <a name="location-cmdlets"></a><span data-ttu-id="87fd6-197">Plats-cmdletar</span><span class="sxs-lookup"><span data-stu-id="87fd6-197">Location cmdlets</span></span>

- [<span data-ttu-id="87fd6-198">Get-location</span><span class="sxs-lookup"><span data-stu-id="87fd6-198">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="87fd6-199">Pop-location</span><span class="sxs-lookup"><span data-stu-id="87fd6-199">Pop-Location</span></span>](xref:Microsoft.PowerShell.Management.Pop-Location)
- [<span data-ttu-id="87fd6-200">Push-plats</span><span class="sxs-lookup"><span data-stu-id="87fd6-200">Push-Location</span></span>](xref:Microsoft.PowerShell.Management.Push-Location)
- [<span data-ttu-id="87fd6-201">Ange plats</span><span class="sxs-lookup"><span data-stu-id="87fd6-201">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)

### <a name="path-cmdlets"></a><span data-ttu-id="87fd6-202">Sök vägs-cmdletar</span><span class="sxs-lookup"><span data-stu-id="87fd6-202">Path cmdlets</span></span>

- [<span data-ttu-id="87fd6-203">Anslut till sökväg</span><span class="sxs-lookup"><span data-stu-id="87fd6-203">Join-Path</span></span>](xref:Microsoft.PowerShell.Management.Join-Path)
- [<span data-ttu-id="87fd6-204">Konvertera-sökväg</span><span class="sxs-lookup"><span data-stu-id="87fd6-204">Convert-Path</span></span>](xref:Microsoft.PowerShell.Management.Convert-Path)
- [<span data-ttu-id="87fd6-205">Dela-sökväg</span><span class="sxs-lookup"><span data-stu-id="87fd6-205">Split-Path</span></span>](xref:Microsoft.PowerShell.Management.Split-Path)
- [<span data-ttu-id="87fd6-206">Lös-sökväg</span><span class="sxs-lookup"><span data-stu-id="87fd6-206">Resolve-Path</span></span>](xref:Microsoft.PowerShell.Management.Resolve-Path)
- [<span data-ttu-id="87fd6-207">Test-sökväg</span><span class="sxs-lookup"><span data-stu-id="87fd6-207">Test-Path</span></span>](xref:Microsoft.PowerShell.Management.Test-Path)

### <a name="psdrive-cmdlets"></a><span data-ttu-id="87fd6-208">PSDrive-cmdletar</span><span class="sxs-lookup"><span data-stu-id="87fd6-208">PSDrive cmdlets</span></span>

- [<span data-ttu-id="87fd6-209">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="87fd6-209">Get-PSDrive</span></span>](xref:Microsoft.PowerShell.Management.Get-PSDrive)
- [<span data-ttu-id="87fd6-210">New-PSDrive</span><span class="sxs-lookup"><span data-stu-id="87fd6-210">New-PSDrive</span></span>](xref:Microsoft.PowerShell.Management.New-PSDrive)
- [<span data-ttu-id="87fd6-211">Remove-PSDrive</span><span class="sxs-lookup"><span data-stu-id="87fd6-211">Remove-PSDrive</span></span>](xref:Microsoft.PowerShell.Management.Remove-PSDrive)

### <a name="psprovider-cmdlets"></a><span data-ttu-id="87fd6-212">PSProvider-cmdletar</span><span class="sxs-lookup"><span data-stu-id="87fd6-212">PSProvider Cmdlets</span></span>

- [<span data-ttu-id="87fd6-213">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="87fd6-213">Get-PSProvider</span></span>](xref:Microsoft.PowerShell.Management.Get-PSProvider)

## <a name="viewing-provider-data"></a><span data-ttu-id="87fd6-214">Visa leverantörs data</span><span class="sxs-lookup"><span data-stu-id="87fd6-214">Viewing provider data</span></span>

<span data-ttu-id="87fd6-215">Den främsta fördelen med en provider är att den exponerar data på ett välbekant och konsekvent sätt.</span><span class="sxs-lookup"><span data-stu-id="87fd6-215">The primary benefit of a provider is that it exposes its data in a familiar and consistent way.</span></span> <span data-ttu-id="87fd6-216">Modellen för data presentation är en fil systemen het.</span><span class="sxs-lookup"><span data-stu-id="87fd6-216">The model for data presentation is a file system drive.</span></span>

<span data-ttu-id="87fd6-217">Med providern kan du Visa, navigera och ändra objekt i data lagret som om de var data i ett fil system.</span><span class="sxs-lookup"><span data-stu-id="87fd6-217">The provider allows you to view, navigate, and change items in the data store as though they were data in a file system.</span></span> <span data-ttu-id="87fd6-218">Data lagret används av namnet på den enhet som stöds.</span><span class="sxs-lookup"><span data-stu-id="87fd6-218">The data store is accessed by the name of the drive that it supports.</span></span>

<span data-ttu-id="87fd6-219">Enheten visas i standard visningen av `Get-PSProvider` cmdleten, men du kan hämta information om providerns enhet med hjälp av `Get-PSDrive` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="87fd6-219">The drive is listed in the default display of the `Get-PSProvider` cmdlet, but you can get information about the provider drive using the `Get-PSDrive` cmdlet.</span></span> <span data-ttu-id="87fd6-220">Om du till exempel vill hämta alla egenskaper för funktionen: enhet skriver du:</span><span class="sxs-lookup"><span data-stu-id="87fd6-220">For example, to get all the properties of the Function: drive, type:</span></span>

```powershell
Get-PSDrive Function | Format-List *
```

<span data-ttu-id="87fd6-221">Du kan visa och flytta igenom data i en leverantörs enhet precis som på en fil systemen het.</span><span class="sxs-lookup"><span data-stu-id="87fd6-221">You can view and move through the data in a provider drive just as you would on a file system drive.</span></span>

<span data-ttu-id="87fd6-222">Om du vill visa innehållet i en provider använder du Get-Item-eller Get-ChildItem-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="87fd6-222">To view the contents of a provider drive, use the Get-Item or Get-ChildItem cmdlets.</span></span> <span data-ttu-id="87fd6-223">Skriv enhets namnet följt av ett kolon (:).</span><span class="sxs-lookup"><span data-stu-id="87fd6-223">Type the drive name followed by a colon (:).</span></span> <span data-ttu-id="87fd6-224">Om du till exempel vill visa innehållet i aliaset: enhet skriver du:</span><span class="sxs-lookup"><span data-stu-id="87fd6-224">For example, to view the contents of the Alias: drive, type:</span></span>

```powershell
Get-Item alias:
```

<span data-ttu-id="87fd6-225">Du kan visa och hantera data i alla enheter från en annan enhet genom att inkludera enhets namnet i sökvägen.</span><span class="sxs-lookup"><span data-stu-id="87fd6-225">You can view and manage the data in any drive from another drive by including the drive name in the path.</span></span> <span data-ttu-id="87fd6-226">Om du till exempel vill visa register nyckeln HKLM\Software i HKLM: Drive från en annan enhet, skriver du:</span><span class="sxs-lookup"><span data-stu-id="87fd6-226">For example, to view the HKLM\Software registry key in the HKLM: drive from another drive, type:</span></span>

```powershell
Get-ChildItem HKLM:\SOFTWARE\
```

<span data-ttu-id="87fd6-227">Använd Set-Location-cmdleten för att öppna enheten.</span><span class="sxs-lookup"><span data-stu-id="87fd6-227">To open the drive, use the Set-Location cmdlet.</span></span> <span data-ttu-id="87fd6-228">Kom ihåg kolonet när du anger enhetens sökväg.</span><span class="sxs-lookup"><span data-stu-id="87fd6-228">Remember the colon when you specify the drive path.</span></span> <span data-ttu-id="87fd6-229">Om du till exempel vill ändra platsen till rot katalogen för certifikatet: enhet skriver du:</span><span class="sxs-lookup"><span data-stu-id="87fd6-229">For example, to change your location to the root directory of the Cert: drive, type:</span></span>

```powershell
Set-Location cert:
```

<span data-ttu-id="87fd6-230">Om du sedan vill visa innehållet i certifikatet: enhet skriver du:</span><span class="sxs-lookup"><span data-stu-id="87fd6-230">Then, to view the contents of the Cert: drive, type:</span></span>

```powershell
Get-ChildItem
```

## <a name="moving-through-hierarchical-data"></a><span data-ttu-id="87fd6-231">Flytta genom hierarkiska data</span><span class="sxs-lookup"><span data-stu-id="87fd6-231">Moving through hierarchical data</span></span>

<span data-ttu-id="87fd6-232">Du kan flytta genom en leverantörs enhet på samma sätt som en hård disk.</span><span class="sxs-lookup"><span data-stu-id="87fd6-232">You can move through a provider drive just as you would a hard disk drive.</span></span>
<span data-ttu-id="87fd6-233">Om data är ordnade i en hierarki med objekt i objekt, använder du ett omvänt snedstreck ( `\` ) för att ange ett underordnat objekt.</span><span class="sxs-lookup"><span data-stu-id="87fd6-233">If the data is arranged in a hierarchy of items within items, use a backslash (`\`) to indicate a child item.</span></span> <span data-ttu-id="87fd6-234">Använd följande format:</span><span class="sxs-lookup"><span data-stu-id="87fd6-234">Use the following format:</span></span>

```
drive:\location\child-location\...
```

<span data-ttu-id="87fd6-235">Om du till exempel vill ändra din plats till register nyckeln HKLM\Software skriver du ett Set-Location kommando, till exempel:</span><span class="sxs-lookup"><span data-stu-id="87fd6-235">For example, to change your location to the HKLM\Software registry key, type a Set-Location command, such as:</span></span>

```powershell
Set-Location HKLM:\SOFTWARE\
```

<span data-ttu-id="87fd6-236">Om något element i det fullständigt kvalificerade namnet innehåller blank steg måste du skriva namnet inom dubbla citat tecken ( `"` ).</span><span class="sxs-lookup"><span data-stu-id="87fd6-236">If any element in the fully qualified name includes spaces, you must enclose the name in double-quotation marks (`"`).</span></span> <span data-ttu-id="87fd6-237">I följande exempel visas en fullkvalificerad sökväg som innehåller blank steg.</span><span class="sxs-lookup"><span data-stu-id="87fd6-237">The following example shows a fully qualified path that includes spaces.</span></span>

```
"C:\Program Files\Internet Explorer\iexplore.exe"
```

<span data-ttu-id="87fd6-238">Du kan också använda relativa referenser till platser.</span><span class="sxs-lookup"><span data-stu-id="87fd6-238">You can also use relative references to locations.</span></span> <span data-ttu-id="87fd6-239">En punkt ( `.` ) representerar den aktuella platsen.</span><span class="sxs-lookup"><span data-stu-id="87fd6-239">A dot (`.`) represents the current location.</span></span> <span data-ttu-id="87fd6-240">Om du till exempel är i `HKLM:\Software\Microsoft` register nyckeln och vill visa register under nycklarna i `HKLM:\Software\Microsoft\PowerShell` nyckeln, skriver du följande kommando:</span><span class="sxs-lookup"><span data-stu-id="87fd6-240">For example, if you are in the `HKLM:\Software\Microsoft` registry key, and you want to list the registry subkeys in the `HKLM:\Software\Microsoft\PowerShell` key, type the following command:</span></span>

```powershell
Get-ChildItem .\PowerShell
```

<span data-ttu-id="87fd6-241">Dessutom refererar dubbla punkter ( `..` ) till katalogen eller behållaren direkt ovanför din aktuella plats.</span><span class="sxs-lookup"><span data-stu-id="87fd6-241">Also, double-dots (`..`) refers to the directory or container directly above your current location.</span></span> <span data-ttu-id="87fd6-242">Du kan använda dubbla punkter ( `..` ) för att navigera i en dimensionshierarki.</span><span class="sxs-lookup"><span data-stu-id="87fd6-242">You can use double-dots (`..`) to navigate through a provider hierarchy.</span></span>

```
PS HKLM:\SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters\> cd ..\..\LanmanWorkstation\Parameters
PS HKLM:\SYSTEM\CurrentControlSet\Services\LanmanWorkstation\Parameters>
```

## <a name="provider-home"></a><span data-ttu-id="87fd6-243">Start för Provider</span><span class="sxs-lookup"><span data-stu-id="87fd6-243">Provider Home</span></span>

<span data-ttu-id="87fd6-244">Leverantörer har också en **Start** plats.</span><span class="sxs-lookup"><span data-stu-id="87fd6-244">Providers also have a **Home** location.</span></span>  <span data-ttu-id="87fd6-245">Den här platsen delas av alla `PSDrives` som har säkerhetskopierats av providern.</span><span class="sxs-lookup"><span data-stu-id="87fd6-245">This location is shared by all `PSDrives` backed by the provider.</span></span> <span data-ttu-id="87fd6-246">Den kan hämtas genom att se providerns **Start** egenskap.</span><span class="sxs-lookup"><span data-stu-id="87fd6-246">It can be retrieved by viewing the **Home** property of the provider.</span></span>

```powershell
Get-PSProvider | Format-Table Name, Home
```

```Output
Name        Home
----        ----
Registry
Alias
Environment
FileSystem  C:\Users\username
Function
Variable
Certificate
```

<span data-ttu-id="87fd6-247">**Fil Systems** leverantören är den enda providern som har ett standardvärde för **Start**.</span><span class="sxs-lookup"><span data-stu-id="87fd6-247">The **FileSystem** provider is the only provider that has a default value for **Home**.</span></span> <span data-ttu-id="87fd6-248">Det är samma värde som `$Home` .</span><span class="sxs-lookup"><span data-stu-id="87fd6-248">It's the same value as `$Home`.</span></span> <span data-ttu-id="87fd6-249">Mer information finns i [about_Automatic_Variables](about_Automatic_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="87fd6-249">For more information, see [about_Automatic_Variables](about_Automatic_Variables.md).</span></span>

<span data-ttu-id="87fd6-250">Du kan ställa in **arbets** katalogen för en provider för den aktuella sessionen med hjälp av egenskapen.</span><span class="sxs-lookup"><span data-stu-id="87fd6-250">You can set the **Home** directory for a provider, for the current session, using its property.</span></span>

```powershell
(Get-PSProvider FileSystem).Home = "C:\"
```

<span data-ttu-id="87fd6-251">Du `~` kan använda det här alternativet för att representera providerns Hem Katalog.</span><span class="sxs-lookup"><span data-stu-id="87fd6-251">The `~` character can be used to represent the provider's home directory.</span></span>
<span data-ttu-id="87fd6-252">Om providern inte har en **Start** plats som har angetts visas ett fel meddelande.</span><span class="sxs-lookup"><span data-stu-id="87fd6-252">If the provider doesn't have a **Home** location set, you see an error.</span></span>

```powershell
Cert:\> Set-Location ~
```

```Output
Set-Location : Home location for this provider isn't set. To set the home
location, call "(get-psprovider 'Certificate').Home = 'path'".
At line:1 char:1
+ Set-Location ~
+ ~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Set-Location],
                              PSInvalidOperationException
...
```

## <a name="finding-dynamic-parameters"></a><span data-ttu-id="87fd6-253">Hitta dynamiska parametrar</span><span class="sxs-lookup"><span data-stu-id="87fd6-253">Finding dynamic parameters</span></span>

<span data-ttu-id="87fd6-254">Dynamiska parametrar är cmdlet-parametrar som läggs till i en cmdlet av en provider.</span><span class="sxs-lookup"><span data-stu-id="87fd6-254">Dynamic parameters are cmdlet parameters that are added to a cmdlet by a provider.</span></span> <span data-ttu-id="87fd6-255">Dessa parametrar är bara tillgängliga när cmdleten används med providern som lade till dem.</span><span class="sxs-lookup"><span data-stu-id="87fd6-255">These parameters are available only when the cmdlet is used with the provider that added them.</span></span>

<span data-ttu-id="87fd6-256">Enheten lägger till exempel till `Cert:` parametern **CodeSigningCert** i `Get-Item` `Get-ChildItem` cmdletarna och.</span><span class="sxs-lookup"><span data-stu-id="87fd6-256">For example, the `Cert:` drive adds the **CodeSigningCert** parameter to the `Get-Item` and `Get-ChildItem` cmdlets.</span></span> <span data-ttu-id="87fd6-257">Du kan bara använda den här parametern när du använder `Get-Item` eller `Get-ChildItem` i `Cert:` enheten.</span><span class="sxs-lookup"><span data-stu-id="87fd6-257">You can use this parameter only when you use `Get-Item` or `Get-ChildItem` in the `Cert:` drive.</span></span>

<span data-ttu-id="87fd6-258">En lista över de dynamiska parametrar som en provider stöder finns i Hjälp filen för providern.</span><span class="sxs-lookup"><span data-stu-id="87fd6-258">For a list of the dynamic parameters that a provider supports, see the Help file for the provider.</span></span> <span data-ttu-id="87fd6-259">Ange:</span><span class="sxs-lookup"><span data-stu-id="87fd6-259">Type:</span></span>

```
Get-Help <provider-name>
```

<span data-ttu-id="87fd6-260">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="87fd6-260">For example:</span></span>

```powershell
Get-Help certificate
```

## <a name="learning-about-providers"></a><span data-ttu-id="87fd6-261">Lär dig om leverantörer</span><span class="sxs-lookup"><span data-stu-id="87fd6-261">Learning about providers</span></span>

<span data-ttu-id="87fd6-262">Även om alla leverantörs data visas i enheter och du använder samma metoder för att gå igenom dem, stannar likheten där.</span><span class="sxs-lookup"><span data-stu-id="87fd6-262">Although all provider data appears in drives and you use the same methods to move through them, the similarity stops there.</span></span> <span data-ttu-id="87fd6-263">De data lager som providern visar kan vara lika varierande som Active Directory platser och Microsoft Exchange Server-postlådor.</span><span class="sxs-lookup"><span data-stu-id="87fd6-263">The data stores that the provider exposes can be as varied as Active Directory locations and Microsoft Exchange Server mailboxes.</span></span>

<span data-ttu-id="87fd6-264">Om du vill ha mer information om enskilda PowerShell-leverantörer skriver du:</span><span class="sxs-lookup"><span data-stu-id="87fd6-264">For information about individual PowerShell providers, type:</span></span>

```
Get-Help <ProviderName>
```

<span data-ttu-id="87fd6-265">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="87fd6-265">For example:</span></span>

```powershell
Get-Help registry
```

<span data-ttu-id="87fd6-266">Om du vill ha en lista över hjälp avsnitt om providern skriver du:</span><span class="sxs-lookup"><span data-stu-id="87fd6-266">For a list of Help topics about the providers, type:</span></span>

```powershell
Get-Help * -Category Provider
```

## <a name="see-also"></a><span data-ttu-id="87fd6-267">Se även</span><span class="sxs-lookup"><span data-stu-id="87fd6-267">See also</span></span>

[<span data-ttu-id="87fd6-268">about_Locations</span><span class="sxs-lookup"><span data-stu-id="87fd6-268">about_Locations</span></span>](about_Locations.md)

[<span data-ttu-id="87fd6-269">about_Path_Syntax</span><span class="sxs-lookup"><span data-stu-id="87fd6-269">about_Path_Syntax</span></span>](about_Path_Syntax.md)
