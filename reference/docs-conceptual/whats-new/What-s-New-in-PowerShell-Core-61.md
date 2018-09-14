---
title: Nyheter i PowerShell Core 6.1
description: Nya funktioner och ändringar som introducerades i PowerShell Core 6.1
ms.date: 09/13/2018
ms.openlocfilehash: 27e7e846e9ba6ab34d83a084c2589b67a9d5cba9
ms.sourcegitcommit: b235c58b34d23317076540631f5cf83f1f309c0d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/13/2018
ms.locfileid: "45557316"
---
# <a name="whats-new-in-powershell-core-61"></a><span data-ttu-id="8c8de-103">Nyheter i PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="8c8de-103">What's New in PowerShell Core 6.1</span></span>

<span data-ttu-id="8c8de-104">Nedan visas ett urval av några av de nya funktioner och ändringar som har införts i PowerShell Core 6.1.</span><span class="sxs-lookup"><span data-stu-id="8c8de-104">Below is a selection of some of the major new features and changes that have been introduced in PowerShell Core 6.1.</span></span>

<span data-ttu-id="8c8de-105">Det finns också **ton** av ”tråkiga” som gör att PowerShell snabbare och mer tillförlitliga (plus utbudet felkorrigeringar)!</span><span class="sxs-lookup"><span data-stu-id="8c8de-105">There's also **tons** of "boring stuff" that make PowerShell faster and more stable (plus lots and lots of bug fixes)!</span></span>
<span data-ttu-id="8c8de-106">En fullständig lista över ändringar, Kolla in vår [ändringsloggen på GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).</span><span class="sxs-lookup"><span data-stu-id="8c8de-106">For a full list of changes, check out our [changelog on GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).</span></span>

<span data-ttu-id="8c8de-107">Och medan vi anropa vissa namn nedan tack till [alla community-deltagare](https://github.com/PowerShell/PowerShell/graphs/contributors) som möjligt den här versionen.</span><span class="sxs-lookup"><span data-stu-id="8c8de-107">And while we call out some names below, thank you to [all of the community contributors](https://github.com/PowerShell/PowerShell/graphs/contributors) that made this release possible.</span></span>

## <a name="net-core-21"></a><span data-ttu-id="8c8de-108">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="8c8de-108">.NET Core 2.1</span></span>

<span data-ttu-id="8c8de-109">PowerShell Core 6.1 flyttas till .NET Core 2.1 när den var [introducerades i maj](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/), vilket resulterar i ett antal förbättringar i PowerShell, inklusive:</span><span class="sxs-lookup"><span data-stu-id="8c8de-109">PowerShell Core 6.1 moved to .NET Core 2.1 after it was [released in May](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/), resulting in a number of improvements to PowerShell, including:</span></span>

- <span data-ttu-id="8c8de-110">prestandaförbättringar (se [nedan](#performance-improvements))</span><span class="sxs-lookup"><span data-stu-id="8c8de-110">performance improvements (see [below](#performance-improvements))</span></span>
- <span data-ttu-id="8c8de-111">Alpine Linux-support (förhandsversion)</span><span class="sxs-lookup"><span data-stu-id="8c8de-111">Alpine Linux support (preview)</span></span>
- <span data-ttu-id="8c8de-112">[Stöd för .NET-globala verktyg](/dotnet/core/tools/global-tools) – kommer snart att PowerShell</span><span class="sxs-lookup"><span data-stu-id="8c8de-112">[.NET global tool support](/dotnet/core/tools/global-tools) - coming soon to PowerShell</span></span>
- [`Span<T>`](/dotnet/api/system.span-1?view=netcore-2.1)

## <a name="windows-compatibility-pack-for-net-core"></a><span data-ttu-id="8c8de-113">Windows Compatibility Pack för .NET Core</span><span class="sxs-lookup"><span data-stu-id="8c8de-113">Windows Compatibility Pack for .NET Core</span></span>

<span data-ttu-id="8c8de-114">På Windows, .NET-teamet levereras de [Windows Compatibility Pack för .NET Core](https://blogs.msdn.microsoft.com/dotnet/2017/11/16/announcing-the-windows-compatibility-pack-for-net-core/), en uppsättning sammansättningar som lägger till ett antal bort API: er till .NET Core för Windows.</span><span class="sxs-lookup"><span data-stu-id="8c8de-114">On Windows, the .NET team shipped the [Windows Compatibility Pack for .NET Core](https://blogs.msdn.microsoft.com/dotnet/2017/11/16/announcing-the-windows-compatibility-pack-for-net-core/), a set of assemblies that add a number of removed APIs back to .NET Core on Windows.</span></span>

<span data-ttu-id="8c8de-115">Vi har lagt till Compatibility-Pack för Windows PowerShell Core 6.1 versionen så att alla moduler eller skript som använder dessa API: er kan använda dem som det är tillgängligt.</span><span class="sxs-lookup"><span data-stu-id="8c8de-115">We've added the Windows Compatibility Pack to PowerShell Core 6.1 release so that any modules or scripts that use these APIs can rely on them being available.</span></span>

<span data-ttu-id="8c8de-116">Windows Compatibility Pack gör det möjligt för PowerShell Core att använda **mer än 1900 cmdletar som levereras med Windows 10 oktober 2018 Update och Windows Server 2019**.</span><span class="sxs-lookup"><span data-stu-id="8c8de-116">The Windows Compatibility Pack enables PowerShell Core to use **more than 1900 cmdlets that ship with Windows 10 October 2018 Update and Windows Server 2019**.</span></span>

## <a name="performance-improvements"></a><span data-ttu-id="8c8de-117">Prestandaförbättringar</span><span class="sxs-lookup"><span data-stu-id="8c8de-117">Performance improvements</span></span>

<span data-ttu-id="8c8de-118">PowerShell Core 6.0 gjort några betydande förbättringar.</span><span class="sxs-lookup"><span data-stu-id="8c8de-118">PowerShell Core 6.0 made some significant performance improvements.</span></span>
<span data-ttu-id="8c8de-119">PowerShell Core 6.1 fortsätter att förbättra hastigheten på vissa åtgärder.</span><span class="sxs-lookup"><span data-stu-id="8c8de-119">PowerShell Core 6.1 continues to improve the speed of certain operations.</span></span>

<span data-ttu-id="8c8de-120">Till exempel `Group-Object` har sped med 66%:</span><span class="sxs-lookup"><span data-stu-id="8c8de-120">For example, `Group-Object` has been sped up by 66%:</span></span>

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Group-Object }
```

|              | <span data-ttu-id="8c8de-121">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="8c8de-121">Windows PowerShell 5.1</span></span> | <span data-ttu-id="8c8de-122">PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="8c8de-122">PowerShell Core 6.0</span></span> | <span data-ttu-id="8c8de-123">PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="8c8de-123">PowerShell Core 6.1</span></span> |
|--------------|------------------------|---------------------|---------------------|
| <span data-ttu-id="8c8de-124">Tid (sek)</span><span class="sxs-lookup"><span data-stu-id="8c8de-124">Time (sec)</span></span>   | <span data-ttu-id="8c8de-125">25.178</span><span class="sxs-lookup"><span data-stu-id="8c8de-125">25.178</span></span>                 | <span data-ttu-id="8c8de-126">19.653</span><span class="sxs-lookup"><span data-stu-id="8c8de-126">19.653</span></span>              | <span data-ttu-id="8c8de-127">6.641</span><span class="sxs-lookup"><span data-stu-id="8c8de-127">6.641</span></span>               |
| <span data-ttu-id="8c8de-128">Hastigheter (%)</span><span class="sxs-lookup"><span data-stu-id="8c8de-128">Speed-up (%)</span></span> | <span data-ttu-id="8c8de-129">Saknas</span><span class="sxs-lookup"><span data-stu-id="8c8de-129">N/A</span></span>                    | <span data-ttu-id="8c8de-130">21.9%</span><span class="sxs-lookup"><span data-stu-id="8c8de-130">21.9%</span></span>               | <span data-ttu-id="8c8de-131">66.2%</span><span class="sxs-lookup"><span data-stu-id="8c8de-131">66.2%</span></span>               |

<span data-ttu-id="8c8de-132">På samma sätt har sortering scenarier som den här förbättrats med mer än 15%:</span><span class="sxs-lookup"><span data-stu-id="8c8de-132">Similarly, sorting scenarios like this one have improved by more than 15%:</span></span>

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Sort-Object }
```

|              | <span data-ttu-id="8c8de-133">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="8c8de-133">Windows PowerShell 5.1</span></span> | <span data-ttu-id="8c8de-134">PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="8c8de-134">PowerShell Core 6.0</span></span> | <span data-ttu-id="8c8de-135">PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="8c8de-135">PowerShell Core 6.1</span></span> |
|--------------|------------------------|---------------------|---------------------|
| <span data-ttu-id="8c8de-136">Tid (sek)</span><span class="sxs-lookup"><span data-stu-id="8c8de-136">Time (sec)</span></span>   | <span data-ttu-id="8c8de-137">12.170</span><span class="sxs-lookup"><span data-stu-id="8c8de-137">12.170</span></span>                 | <span data-ttu-id="8c8de-138">8.493</span><span class="sxs-lookup"><span data-stu-id="8c8de-138">8.493</span></span>               | <span data-ttu-id="8c8de-139">7.08</span><span class="sxs-lookup"><span data-stu-id="8c8de-139">7.08</span></span>                |
| <span data-ttu-id="8c8de-140">Hastigheter (%)</span><span class="sxs-lookup"><span data-stu-id="8c8de-140">Speed-up (%)</span></span> | <span data-ttu-id="8c8de-141">Saknas</span><span class="sxs-lookup"><span data-stu-id="8c8de-141">N/A</span></span>                    | <span data-ttu-id="8c8de-142">30,2%</span><span class="sxs-lookup"><span data-stu-id="8c8de-142">30.2%</span></span>               | <span data-ttu-id="8c8de-143">16.6%</span><span class="sxs-lookup"><span data-stu-id="8c8de-143">16.6%</span></span>               |

<span data-ttu-id="8c8de-144">`Import-Csv` har också tagits sped avsevärt efter en regression från Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8c8de-144">`Import-Csv` has also been sped up significantly after a regression from Windows PowerShell.</span></span>
<span data-ttu-id="8c8de-145">I följande exempel används ett test CSV med 26,616 sex kolumner:</span><span class="sxs-lookup"><span data-stu-id="8c8de-145">The following example uses a test CSV with 26,616 rows and six columns:</span></span>

```powershell
Measure-Command {$a = Import-Csv foo.csv}
```

|              | <span data-ttu-id="8c8de-146">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="8c8de-146">Windows PowerShell 5.1</span></span> | <span data-ttu-id="8c8de-147">PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="8c8de-147">PowerShell Core 6.0</span></span> | <span data-ttu-id="8c8de-148">PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="8c8de-148">PowerShell Core 6.1</span></span>    |
|--------------|------------------------|---------------------|------------------------|
| <span data-ttu-id="8c8de-149">Tid (sek)</span><span class="sxs-lookup"><span data-stu-id="8c8de-149">Time (sec)</span></span>   | <span data-ttu-id="8c8de-150">0.441</span><span class="sxs-lookup"><span data-stu-id="8c8de-150">0.441</span></span>                  | <span data-ttu-id="8c8de-151">1.069</span><span class="sxs-lookup"><span data-stu-id="8c8de-151">1.069</span></span>               | <span data-ttu-id="8c8de-152">0.268</span><span class="sxs-lookup"><span data-stu-id="8c8de-152">0.268</span></span>                  |
| <span data-ttu-id="8c8de-153">Hastigheter (%)</span><span class="sxs-lookup"><span data-stu-id="8c8de-153">Speed-up (%)</span></span> | <span data-ttu-id="8c8de-154">Saknas</span><span class="sxs-lookup"><span data-stu-id="8c8de-154">N/A</span></span>                    | <span data-ttu-id="8c8de-155">-142.4%</span><span class="sxs-lookup"><span data-stu-id="8c8de-155">-142.4%</span></span>             | <span data-ttu-id="8c8de-156">74.9% (39.2. % från WPS)</span><span class="sxs-lookup"><span data-stu-id="8c8de-156">74.9% (39.2% from WPS)</span></span> |

<span data-ttu-id="8c8de-157">Till sist konvertering från JSON till `PSObject` har varit sped med mer än 50% sedan Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8c8de-157">Lastly, conversion from JSON into `PSObject` has been sped up by more than 50% since Windows PowerShell.</span></span>
<span data-ttu-id="8c8de-158">I följande exempel används en ~ 2MB test JSON-fil:</span><span class="sxs-lookup"><span data-stu-id="8c8de-158">The following example uses a ~2MB test JSON file:</span></span>

```powershell
Measure-Command {Get-Content .\foo.json | ConvertFrom-Json}
```

|              | <span data-ttu-id="8c8de-159">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="8c8de-159">Windows PowerShell 5.1</span></span> | <span data-ttu-id="8c8de-160">PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="8c8de-160">PowerShell Core 6.0</span></span> | <span data-ttu-id="8c8de-161">PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="8c8de-161">PowerShell Core 6.1</span></span>    |
|--------------|------------------------|---------------------|------------------------|
| <span data-ttu-id="8c8de-162">Tid (sek)</span><span class="sxs-lookup"><span data-stu-id="8c8de-162">Time (sec)</span></span>   | <span data-ttu-id="8c8de-163">0.259</span><span class="sxs-lookup"><span data-stu-id="8c8de-163">0.259</span></span>                  | <span data-ttu-id="8c8de-164">0.577</span><span class="sxs-lookup"><span data-stu-id="8c8de-164">0.577</span></span>               | <span data-ttu-id="8c8de-165">0,125</span><span class="sxs-lookup"><span data-stu-id="8c8de-165">0.125</span></span>                  |
| <span data-ttu-id="8c8de-166">Hastigheter (%)</span><span class="sxs-lookup"><span data-stu-id="8c8de-166">Speed-up (%)</span></span> | <span data-ttu-id="8c8de-167">Saknas</span><span class="sxs-lookup"><span data-stu-id="8c8de-167">N/A</span></span>                    | <span data-ttu-id="8c8de-168">-122.8%</span><span class="sxs-lookup"><span data-stu-id="8c8de-168">-122.8%</span></span>             | <span data-ttu-id="8c8de-169">78.3% (51.7% från WPS)</span><span class="sxs-lookup"><span data-stu-id="8c8de-169">78.3% (51.7% from WPS)</span></span> |

## <a name="check-system32-for-compatible-inbox-modules-on-windows"></a><span data-ttu-id="8c8de-170">Kontrollera `system32` för kompatibla inkorg moduler på Windows</span><span class="sxs-lookup"><span data-stu-id="8c8de-170">Check `system32` for compatible inbox modules on Windows</span></span>

<span data-ttu-id="8c8de-171">Vi har uppdaterat ett antal inkorg PowerShell-moduler för att markera dem som kompatibel med PowerShell Core i Windows 10 1809 update och Windows Server 2019.</span><span class="sxs-lookup"><span data-stu-id="8c8de-171">In the Windows 10 1809 update and Windows Server 2019, we updated a number of inbox PowerShell modules to mark them as compatible with PowerShell Core.</span></span>

<span data-ttu-id="8c8de-172">När PowerShell Core 6.1 startas automatiskt inkluderar `$windir\System32` som en del av den `PSModulePath` miljövariabeln.</span><span class="sxs-lookup"><span data-stu-id="8c8de-172">When PowerShell Core 6.1 starts up, it will automatically include `$windir\System32` as part of the `PSModulePath` environment variable.</span></span>
<span data-ttu-id="8c8de-173">Men det endast visar moduler att `Get-Module` och `Import-Module` om dess `CompatiblePSEdition` är markerad som kompatibel med `Core`.</span><span class="sxs-lookup"><span data-stu-id="8c8de-173">However, it only exposes modules to `Get-Module` and `Import-Module` if its `CompatiblePSEdition` is marked as compatible with `Core`.</span></span>


```powershell
Get-Module -ListAvailable
```

> [!NOTE]
> <span data-ttu-id="8c8de-174">Du kan se olika tillgängliga moduler beroende på vilka roller och funktioner installeras.</span><span class="sxs-lookup"><span data-stu-id="8c8de-174">You may see different available modules depending on what roles and features are installed.</span></span>

```Output
...
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Manifest   2.0.1.0    Appx                                Core,Desk {Add-AppxPackage, Get-AppxPackage, Get-AppxPacka...
Manifest   1.0.0.0    BitLocker                           Core,Desk {Unlock-BitLocker, Suspend-BitLocker, Resume-Bit...
Manifest   1.0.0.0    DnsClient                           Core,Desk {Resolve-DnsName, Clear-DnsClientCache, Get-DnsC...
Manifest   1.0.0.0    HgsDiagnostics                      Core,Desk {New-HgsTraceTarget, Get-HgsTrace, Get-HgsTraceF...
Binary     2.0.0.0    Hyper-V                             Core,Desk {Add-VMAssignableDevice, Add-VMDvdDrive, Add-VMF...
Binary     1.1        Hyper-V                             Core,Desk {Add-VMDvdDrive, Add-VMFibreChannelHba, Add-VMHa...
Manifest   2.0.0.0    NetAdapter                          Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetEventPacketCapture               Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                             Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                              Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                              Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                         Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam                       Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetWNV                              Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   2.0.0.0    TrustedPlatformModule               Core,Desk {Get-Tpm, Initialize-Tpm, Clear-Tpm, Unblock-Tpm...
...
```

<span data-ttu-id="8c8de-175">Du kan åsidosätta detta beteende om du vill visa alla moduler med den `-SkipEditionCheck` växla parametern.</span><span class="sxs-lookup"><span data-stu-id="8c8de-175">You can override this behavior to show all modules using the `-SkipEditionCheck` switch parameter.</span></span>
<span data-ttu-id="8c8de-176">Vi har även lagt till en `PSEdition` egenskap till tabellutdata.</span><span class="sxs-lookup"><span data-stu-id="8c8de-176">We've also added a `PSEdition` property to the table output.</span></span>

```powershell
Get-Module Net* -ListAvailable -SkipEditionCheck
```

```Output
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                        PSEdition ExportedCommands
---------- -------    ----                        --------- ----------------
Manifest   2.0.0.0    NetAdapter                  Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetConnection               Desk      {Get-NetConnectionProfile, Set-NetConnectionProf...
Manifest   1.0.0.0    NetDiagnostics              Desk      Get-NetView
Manifest   1.0.0.0    NetEventPacketCapture       Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                     Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                      Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                      Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                 Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam               Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetTCPIP                    Desk      {Get-NetIPAddress, Get-NetIPInterface, Get-NetIP...
Manifest   1.0.0.0    NetWNV                      Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   1.0.0.0    NetworkConnectivityStatus   Desk      {Get-DAConnectionStatus, Get-NCSIPolicyConfigura...
Manifest   1.0.0.0    NetworkSwitchManager        Desk      {Disable-NetworkSwitchEthernetPort, Enable-Netwo...
Manifest   1.0.0.0    NetworkTransition           Desk      {Add-NetIPHttpsCertBinding, Disable-NetDnsTransi...
```

<span data-ttu-id="8c8de-177">Mer information om det här beteendet Kolla in [PowerShell RFC0025](https://github.com/PowerShell/PowerShell-RFC/blob/master/2-Draft-Accepted/RFC0025-PSCore6-and-Windows-Modules.md).</span><span class="sxs-lookup"><span data-stu-id="8c8de-177">For more information about this behavior, check out [PowerShell RFC0025](https://github.com/PowerShell/PowerShell-RFC/blob/master/2-Draft-Accepted/RFC0025-PSCore6-and-Windows-Modules.md).</span></span>

## <a name="markdown-cmdlets-and-rendering"></a><span data-ttu-id="8c8de-178">Markdown-cmdletar och rendering</span><span class="sxs-lookup"><span data-stu-id="8c8de-178">Markdown cmdlets and rendering</span></span>

<span data-ttu-id="8c8de-179">Markdown är en standard för att skapa läsbara klartext dokument med enkla format som kan återges i HTML-format.</span><span class="sxs-lookup"><span data-stu-id="8c8de-179">Markdown is a standard for creating readable plaintext documents with basic formatting that can be rendered into HTML.</span></span>

<span data-ttu-id="8c8de-180">Vi har lagt till vissa cmdlets i 6.1 så att du kan konvertera och rendera Markdown-dokument i konsolen, inklusive:</span><span class="sxs-lookup"><span data-stu-id="8c8de-180">We've added some cmdlets in 6.1 that allow you to convert and render Markdown documents in the console, including:</span></span>

- `ConvertFrom-Markdown`
- `Get-MarkdownOption`
- `Set-MarkdownOption`
- `Show-Markdown`

<span data-ttu-id="8c8de-181">Till exempel `Show-Markdown` visas med en Markdown-fil i konsolen:</span><span class="sxs-lookup"><span data-stu-id="8c8de-181">For example, `Show-Markdown` renders a Markdown file in the console:</span></span>

![Visa Markdown-exempel](./images/markdown_example.png)

<span data-ttu-id="8c8de-183">Mer information om hur dessa cmdlets fungerar finns i [denna RFC](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-Native-Markdown-Rendering.md).</span><span class="sxs-lookup"><span data-stu-id="8c8de-183">For more information about how these cmdlets work, check out [this RFC](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-Native-Markdown-Rendering.md).</span></span>

## <a name="experimental-feature-flags"></a><span data-ttu-id="8c8de-184">Experimentell funktion flaggor</span><span class="sxs-lookup"><span data-stu-id="8c8de-184">Experimental feature flags</span></span>

<span data-ttu-id="8c8de-185">Experimentell funktion flaggor kan du aktivera funktioner som inte har avslutats.</span><span class="sxs-lookup"><span data-stu-id="8c8de-185">Experimental feature flags enable users to turn on features that haven't been finalized.</span></span>
<span data-ttu-id="8c8de-186">Dessa experimentella funktioner stöds inte och kan ha buggar.</span><span class="sxs-lookup"><span data-stu-id="8c8de-186">These experimental features aren't supported and may have bugs.</span></span>

<span data-ttu-id="8c8de-187">Du kan läsa mer om den här funktionen i [PowerShell RFC0029](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md).</span><span class="sxs-lookup"><span data-stu-id="8c8de-187">You can learn more about this feature in [PowerShell RFC0029](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md).</span></span>

## <a name="web-cmdlet-improvements"></a><span data-ttu-id="8c8de-188">Förbättringar för Web-cmdlet</span><span class="sxs-lookup"><span data-stu-id="8c8de-188">Web cmdlet improvements</span></span>

<span data-ttu-id="8c8de-189">Tack vare @markekraus, en hela slew förbättringar har gjorts i vår webb-cmdletar: [`Invoke-WebRequest`](/powershell/module/microsoft.powershell.utility/invoke-webrequest)</span><span class="sxs-lookup"><span data-stu-id="8c8de-189">Thanks to @markekraus, a whole slew of improvements have been made to our web cmdlets: [`Invoke-WebRequest`](/powershell/module/microsoft.powershell.utility/invoke-webrequest)</span></span>
<span data-ttu-id="8c8de-190">och [ `Invoke-RestMethod` ](/powershell/module/microsoft.powershell.utility/invoke-restmethod).</span><span class="sxs-lookup"><span data-stu-id="8c8de-190">and [`Invoke-RestMethod`](/powershell/module/microsoft.powershell.utility/invoke-restmethod).</span></span>

- <span data-ttu-id="8c8de-191">[PR #6109](https://github.com/PowerShell/PowerShell/pull/6109) -standard kodning inställt UTF-8 för `application-json` svar</span><span class="sxs-lookup"><span data-stu-id="8c8de-191">[PR #6109](https://github.com/PowerShell/PowerShell/pull/6109) - default encoding set to UTF-8 for `application-json` responses</span></span>
- <span data-ttu-id="8c8de-192">[PR #6018](https://github.com/PowerShell/PowerShell/pull/6018)  -  `-SkipHeaderValidation` parametern så att `Content-Type` rubriker som inte är standardkompatibel</span><span class="sxs-lookup"><span data-stu-id="8c8de-192">[PR #6018](https://github.com/PowerShell/PowerShell/pull/6018) - `-SkipHeaderValidation` parameter to allow `Content-Type` headers that aren't standards-compliant</span></span>
- <span data-ttu-id="8c8de-193">[PR #5972](https://github.com/PowerShell/PowerShell/pull/5972)  -  `Form` parametern för förenklad `multipart/form-data` stöd</span><span class="sxs-lookup"><span data-stu-id="8c8de-193">[PR #5972](https://github.com/PowerShell/PowerShell/pull/5972) - `Form` parameter to support simplified `multipart/form-data` support</span></span>
- <span data-ttu-id="8c8de-194">[PR #6338](https://github.com/PowerShell/PowerShell/pull/6338) - kompatibla, skiftlägesokänslig hantering av nycklar för relationen</span><span class="sxs-lookup"><span data-stu-id="8c8de-194">[PR #6338](https://github.com/PowerShell/PowerShell/pull/6338) - Compliant, case-insensitive handling of relation keys</span></span>
- <span data-ttu-id="8c8de-195">[PR #6447](https://github.com/PowerShell/PowerShell/pull/6447) – Lägg till `-Resume` parametern för web-cmdletar</span><span class="sxs-lookup"><span data-stu-id="8c8de-195">[PR #6447](https://github.com/PowerShell/PowerShell/pull/6447) - Add `-Resume` parameter for web cmdlets</span></span>

## <a name="remoting-improvements"></a><span data-ttu-id="8c8de-196">Förbättringar för fjärrkommunikation</span><span class="sxs-lookup"><span data-stu-id="8c8de-196">Remoting improvements</span></span>

### <a name="powershell-direct-tries-to-use-powershell-core-first"></a><span data-ttu-id="8c8de-197">PowerShell Direct försöker först använda PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="8c8de-197">PowerShell Direct tries to use PowerShell Core first</span></span>

<span data-ttu-id="8c8de-198">[PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct) är en funktion i PowerShell och Hyper-V som gör det möjligt att ansluta till en Hyper-V virtuell dator utan nätverksanslutning eller andra tjänster för fjärrhantering.</span><span class="sxs-lookup"><span data-stu-id="8c8de-198">[PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct) is a feature of PowerShell and Hyper-V that allows you to connect to a Hyper-V VM without network connectivity or other remote management services.</span></span>

<span data-ttu-id="8c8de-199">Tidigare var ansluten PowerShell Direct med hjälp av Windows PowerShell-instansen inkorg på den virtuella datorn.</span><span class="sxs-lookup"><span data-stu-id="8c8de-199">In the past, PowerShell Direct connected using the inbox Windows PowerShell instance on the VM.</span></span>
<span data-ttu-id="8c8de-200">Nu, PowerShell Direct först försöker ansluta med hjälp av alla tillgängliga `pwsh.exe` på den `PATH` miljövariabeln.</span><span class="sxs-lookup"><span data-stu-id="8c8de-200">Now, PowerShell Direct first attempts to connect using any available `pwsh.exe` on the `PATH` environment variable.</span></span>
<span data-ttu-id="8c8de-201">Om `pwsh.exe` är inte tillgänglig, PowerShell Direct faller tillbaka om du vill använda `powershell.exe`.</span><span class="sxs-lookup"><span data-stu-id="8c8de-201">If `pwsh.exe` isn't available, PowerShell Direct falls back to use `powershell.exe`.</span></span>

### <a name="enable-psremoting-now-creates-separate-remoting-endpoints-for-preview-versions"></a><span data-ttu-id="8c8de-202">`Enable-PSRemoting` skapar nu separata fjärrkommunikation slutpunkter för förhandsversioner</span><span class="sxs-lookup"><span data-stu-id="8c8de-202">`Enable-PSRemoting` now creates separate remoting endpoints for preview versions</span></span>

<span data-ttu-id="8c8de-203">`Enable-PSRemoting` Nu skapar två fjärrkommunikation sessionskonfigurationer:</span><span class="sxs-lookup"><span data-stu-id="8c8de-203">`Enable-PSRemoting` now creates two remoting session configurations:</span></span>

- <span data-ttu-id="8c8de-204">En för den huvudsakliga versionen av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8c8de-204">One for the major version of PowerShell.</span></span> <span data-ttu-id="8c8de-205">Till exempel`PowerShell.6`.</span><span class="sxs-lookup"><span data-stu-id="8c8de-205">For example,`PowerShell.6`.</span></span> <span data-ttu-id="8c8de-206">Den här slutpunkten kan förlita sig på mellan mindre versionsuppdateringar som sessionskonfigurationen ”systemomfattande” PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="8c8de-206">This endpoint that can be relied upon across minor version updates as the "system-wide" PowerShell 6 session configuration</span></span>
- <span data-ttu-id="8c8de-207">En versionsspecifika sessionskonfiguration, till exempel: `PowerShell.6.1.0`</span><span class="sxs-lookup"><span data-stu-id="8c8de-207">One version-specific session configuration, for example: `PowerShell.6.1.0`</span></span>

<span data-ttu-id="8c8de-208">Detta är användbart om du vill ha flera PowerShell 6 versioner installerade och kan nås på samma dator.</span><span class="sxs-lookup"><span data-stu-id="8c8de-208">This behavior is useful if you want to have multiple PowerShell 6 versions installed and accessible on the same machine.</span></span>

<span data-ttu-id="8c8de-209">Dessutom förhandsversioner av PowerShell nu få sina egna fjärrkommunikation sessionskonfigurationer efter körning i `Enable-PSRemoting` cmdlet:</span><span class="sxs-lookup"><span data-stu-id="8c8de-209">Additionally, preview versions of PowerShell now get their own remoting session configurations after running the `Enable-PSRemoting` cmdlet:</span></span>

```powershell
C:\WINDOWS\system32> Enable-PSRemoting
```

<span data-ttu-id="8c8de-210">Dina utdata kan skilja sig om du inte har konfigurerat WinRM innan.</span><span class="sxs-lookup"><span data-stu-id="8c8de-210">Your output may be different if you haven't set up WinRM before.</span></span>

```Output
WinRM is already set up to receive requests on this computer.
WinRM is already set up for remote management on this computer.
```

<span data-ttu-id="8c8de-211">Sedan kan du se separata PowerShell-sessionskonfigurationer för förhandsversionen och stabil bygger på PowerShell 6 och för varje specifik version.</span><span class="sxs-lookup"><span data-stu-id="8c8de-211">Then you can see separate PowerShell session configurations for the preview and stable builds of PowerShell 6, and for each specific version.</span></span>

```powershell
Get-PSSessionConfiguration
```

```Output
Name          : PowerShell.6.2-preview.1
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6-preview
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : powershell.6
PSVersion     : 6.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : powershell.6.1.0
PSVersion     : 6.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
```

### <a name="userhostport-syntax-supported-for-ssh"></a><span data-ttu-id="8c8de-212">`user@host:port` syntax som stöds för SSH</span><span class="sxs-lookup"><span data-stu-id="8c8de-212">`user@host:port` syntax supported for SSH</span></span>

<span data-ttu-id="8c8de-213">SSH-klienter normalt stöder en anslutningssträng i formatet `user@host:port`.</span><span class="sxs-lookup"><span data-stu-id="8c8de-213">SSH clients typically support a connection string in the format `user@host:port`.</span></span>
<span data-ttu-id="8c8de-214">Med hjälp av SSH som ett protokoll för PowerShell-fjärrkommunikation, har vi lagt till stöd för det här formatet för anslutningssträngen:</span><span class="sxs-lookup"><span data-stu-id="8c8de-214">With the addition of SSH as a protocol for PowerShell Remoting, we've added support for this format of connection string:</span></span>

`Enter-PSSession -HostName fooUser@ssh.contoso.com:2222`

## <a name="msi-option-to-add-explorer-shell-context-menu-on-windows"></a><span data-ttu-id="8c8de-215">MSI-alternativet att lägga till snabbmenyn i explorer-gränssnittet på Windows</span><span class="sxs-lookup"><span data-stu-id="8c8de-215">MSI option to add explorer shell context menu on Windows</span></span>

<span data-ttu-id="8c8de-216">Tack vare @bergmeister, nu kan du aktivera en snabbmeny på Windows.</span><span class="sxs-lookup"><span data-stu-id="8c8de-216">Thanks to @bergmeister, now you can enable a context menu on Windows.</span></span> <span data-ttu-id="8c8de-217">Nu kan du öppna din systemomfattande installation av PowerShell 6.1 från valfri mapp i Windows Explorer:</span><span class="sxs-lookup"><span data-stu-id="8c8de-217">Now you can open your system-wide installation of PowerShell 6.1 from any folder in the Windows Explorer:</span></span>

![Shell-snabbmenyn för PowerShell 6](./images/shell_context_menu.png)

## <a name="goodies"></a><span data-ttu-id="8c8de-219">Godbitar</span><span class="sxs-lookup"><span data-stu-id="8c8de-219">Goodies</span></span>

### <a name="run-as-administrator-in-the-windows-shortcut-jump-list"></a><span data-ttu-id="8c8de-220">”Kör som administratör” i listan över Windows genväg hopp</span><span class="sxs-lookup"><span data-stu-id="8c8de-220">"Run as Administrator" in the Windows shortcut jump list</span></span>

<span data-ttu-id="8c8de-221">Tack vare @bergmeister, genvägen PowerShell Core jump-listan innehåller nu ”kör som administratör”:</span><span class="sxs-lookup"><span data-stu-id="8c8de-221">Thanks to @bergmeister, the PowerShell Core shortcut's jump list now includes "Run as Administrator":</span></span>

![Kör som administratör i PowerShell 6 jump-listan](./images/jumplist.png)

### <a name="cd---returns-to-previous-directory"></a><span data-ttu-id="8c8de-223">`cd -` Returnerar föregående katalog</span><span class="sxs-lookup"><span data-stu-id="8c8de-223">`cd -` returns to previous directory</span></span>

```powershell
C:\Windows\System32> cd C:\
C:\> cd -
C:\Windows\System32>
```

<span data-ttu-id="8c8de-224">Eller på Linux:</span><span class="sxs-lookup"><span data-stu-id="8c8de-224">Or on Linux:</span></span>

```ShellSession
PS /etc> cd /usr/bin
PS /usr/bin> cd -
PS /etc>
```

<span data-ttu-id="8c8de-225">Dessutom `cd --` ändras till `$HOME`.</span><span class="sxs-lookup"><span data-stu-id="8c8de-225">Also, `cd --` changes to `$HOME`.</span></span>

### `Test-Connection`

<span data-ttu-id="8c8de-226">Tack vare @iSazonov, [ `Test-Connection` ](/powershell/module/microsoft.powershell.management/test-connection) cmdlet har varit portas till PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="8c8de-226">Thanks to @iSazonov, the [`Test-Connection`](/powershell/module/microsoft.powershell.management/test-connection) cmdlet has been ported to PowerShell Core.</span></span>

### <a name="update-help-as-non-admin"></a><span data-ttu-id="8c8de-227">`Update-Help` som icke-administratörer</span><span class="sxs-lookup"><span data-stu-id="8c8de-227">`Update-Help` as non-admin</span></span>

<span data-ttu-id="8c8de-228">På allmän begäran `Update-Help` inte längre behöver köras som administratör.</span><span class="sxs-lookup"><span data-stu-id="8c8de-228">By popular demand, `Update-Help` no longer needs to be run as an administrator.</span></span>
<span data-ttu-id="8c8de-229">`Update-Help` som standard nu sparar hjälper till att en användarspecifika mapp.</span><span class="sxs-lookup"><span data-stu-id="8c8de-229">`Update-Help` now defaults to saving help to a user-scoped folder.</span></span>

### <a name="new-methodsproperties-on-pscustomobject"></a><span data-ttu-id="8c8de-230">Nya metoder/egenskaper på `PSCustomObject`</span><span class="sxs-lookup"><span data-stu-id="8c8de-230">New methods/properties on `PSCustomObject`</span></span>

<span data-ttu-id="8c8de-231">Tack vare @iSazonov, vi har lagt till nya metoder och egenskaper som `PSCustomObject`.</span><span class="sxs-lookup"><span data-stu-id="8c8de-231">Thanks to @iSazonov, we've added new methods and properties to `PSCustomObject`.</span></span>
<span data-ttu-id="8c8de-232">`PSCustomObject` innehåller nu en `Count` / `Length` egenskap som ger antalet objekt.</span><span class="sxs-lookup"><span data-stu-id="8c8de-232">`PSCustomObject` now includes a `Count`/`Length` property that gives the number of items.</span></span>

<span data-ttu-id="8c8de-233">Båda exemplen returnera `2` som antalet `PSCustomObjects` i samlingen.</span><span class="sxs-lookup"><span data-stu-id="8c8de-233">Both of these examples return `2` as the number of `PSCustomObjects` in the collection.</span></span>

```powershell
@(
[pscustomobject]@{foo = '1'},
[pscustomobject]@{bar = '2' }).Length
```

```powershell
@(
[pscustomobject]@{foo = '1'},
[pscustomobject]@{bar = '2' }).Count
```

<span data-ttu-id="8c8de-234">Det här att fungera även `ForEach` och `Where` metoder som gör det möjligt att driva och filtrera på `PSCustomObject` objekt:</span><span class="sxs-lookup"><span data-stu-id="8c8de-234">This work also includes `ForEach` and `Where` methods that allow you to operate and filter on `PSCustomObject` items:</span></span>

```powershell
@(
>> [pscustomobject]@{foo = 1},
>> [pscustomobject]@{foo = 2 }).ForEach({$_.foo+1})
```

```Output
2
3
```

```powershell
@(
>> [pscustomobject]@{foo = 1},
>> [pscustomobject]@{foo = 2 }).Where({$_.foo -gt 1})
```

```Output
foo
---
  2
```

### `Where-Object -Not`

<span data-ttu-id="8c8de-235">Tack vare @SimonWahlin, vi har lagt till den `-Not` parameter `Where-Object`.</span><span class="sxs-lookup"><span data-stu-id="8c8de-235">Thanks to @SimonWahlin, we've added the `-Not` parameter to `Where-Object`.</span></span>
<span data-ttu-id="8c8de-236">Du kan nu filtrera ett objekt på pipelinen för icke-förekomsten av en egenskap eller ett egenskapsvärde för null/tomt.</span><span class="sxs-lookup"><span data-stu-id="8c8de-236">Now you can filter an object at the pipeline for the non-existence of a property, or a null/empty property value.</span></span>

<span data-ttu-id="8c8de-237">Det här kommandot returnerar till exempel alla tjänster som inte har några definierade beroende tjänster:</span><span class="sxs-lookup"><span data-stu-id="8c8de-237">For example, this command returns all services that don't have any dependent services defined:</span></span>

```powershell
Get-Service | Where-Object -Not DependentServices
```

### <a name="new-modulemanifest-creates-a-bom-less-utf-8-document"></a><span data-ttu-id="8c8de-238">`New-ModuleManifest` skapar ett BOM utan UTF-8-dokument</span><span class="sxs-lookup"><span data-stu-id="8c8de-238">`New-ModuleManifest` creates a BOM-less UTF-8 document</span></span>

<span data-ttu-id="8c8de-239">Med vår övergång till BOM utan UTF-8 i PowerShell 6.0 kan vi har uppdaterat den `New-ModuleManifest` cmdlet för att skapa ett BOM utan UTF-8-dokument i stället för en UTF-16 något.</span><span class="sxs-lookup"><span data-stu-id="8c8de-239">Given our move to BOM-less UTF-8 in PowerShell 6.0, we've updated the `New-ModuleManifest` cmdlet to create a BOM-less UTF-8 document instead of a UTF-16 one.</span></span>

### <a name="conversions-from-psmethod-to-delegate"></a><span data-ttu-id="8c8de-240">Konverteringar från PSMethod till ombud</span><span class="sxs-lookup"><span data-stu-id="8c8de-240">Conversions from PSMethod to Delegate</span></span>

<span data-ttu-id="8c8de-241">Tack vare @powercode, vi nu stöd för konvertering av en `PSMethod` till ett ombud.</span><span class="sxs-lookup"><span data-stu-id="8c8de-241">Thanks to @powercode, we now support the conversion of a `PSMethod` into a delegate.</span></span>
<span data-ttu-id="8c8de-242">Du kan till exempel skicka `PSMethod` `[M]::DoubleStrLen` som ett ombud värde i `[M]::AggregateString`:</span><span class="sxs-lookup"><span data-stu-id="8c8de-242">This allows you to do things like passing `PSMethod` `[M]::DoubleStrLen` as a delegate value into `[M]::AggregateString`:</span></span>

```powershell
class M {
    static [int] DoubleStrLen([string] $value) { return 2 * $value.Length }

    static [long] AggregateString([string[]] $values, [func[string, int]] $selector) {
        [long] $res = 0
        foreach($s in $values){
            $res += $selector.Invoke($s)
        }
        return $res
    }
}

[M]::AggregateString((gci).Name, [M]::DoubleStrLen)
```

<span data-ttu-id="8c8de-243">Mer information om den här ändringen finns [PR #5287](https://github.com/PowerShell/PowerShell/pull/5287).</span><span class="sxs-lookup"><span data-stu-id="8c8de-243">For more info on this change, check out [PR #5287](https://github.com/PowerShell/PowerShell/pull/5287).</span></span>

### <a name="standard-deviation-in-measure-object"></a><span data-ttu-id="8c8de-244">Standardavvikelsen i `Measure-Object`</span><span class="sxs-lookup"><span data-stu-id="8c8de-244">Standard deviation in `Measure-Object`</span></span>

<span data-ttu-id="8c8de-245">Tack vare @CloudyDino, vi har lagt till en `StandardDeviation` egenskap `Measure-Object`:</span><span class="sxs-lookup"><span data-stu-id="8c8de-245">Thanks to @CloudyDino, we've added a `StandardDeviation` property to `Measure-Object`:</span></span>

```powershell
Get-Process | Measure-Object -Property CPU -AllStats
```

```Output
Count             : 308
Average           : 31.3720576298701
Sum               : 9662.59375
Maximum           : 4416.046875
Minimum           :
StandardDeviation : 264.389544720926
Property          : CPU
```

### `GetPfxCertificate -Password`

<span data-ttu-id="8c8de-246">Tack vare @maybe-hello-world, `Get-PfxCertificate` har nu den `Password` parametern, som tar en `SecureString`.</span><span class="sxs-lookup"><span data-stu-id="8c8de-246">Thanks to @maybe-hello-world, `Get-PfxCertificate` now has the `Password` parameter, which takes a `SecureString`.</span></span> <span data-ttu-id="8c8de-247">På så sätt kan du använda den icke-interaktivt:</span><span class="sxs-lookup"><span data-stu-id="8c8de-247">This allows you to use it non-interactively:</span></span>

```powershell
$certFile = '\\server\share\pwd-protected.pfx'
$certPass = Read-Host -AsSecureString -Prompt 'Enter the password for certificate: '

$certThumbPrint = (Get-PfxCertificate -FilePath $certFile -Password $certPass ).ThumbPrint
```

### <a name="removal-of-the-more-function"></a><span data-ttu-id="8c8de-248">Borttagning av den `more` funktion</span><span class="sxs-lookup"><span data-stu-id="8c8de-248">Removal of the `more` function</span></span>

<span data-ttu-id="8c8de-249">Tidigare levererat PowerShell en funktion i Windows som kallas `more` som omslutna `more.com`.</span><span class="sxs-lookup"><span data-stu-id="8c8de-249">In the past, PowerShell shipped a function on Windows called `more` that wrapped `more.com`.</span></span>
<span data-ttu-id="8c8de-250">Funktionen har nu tagits bort.</span><span class="sxs-lookup"><span data-stu-id="8c8de-250">That function has now been removed.</span></span>

<span data-ttu-id="8c8de-251">Även den `help` funktionen ändrats till att använda `more.com` på Windows eller systemets standard personsökare anges av `$env:PAGER` på icke-Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="8c8de-251">Also the `help` function changed to use `more.com` on Windows, or the system's default pager specified by `$env:PAGER` on non-Windows platforms.</span></span>

### <a name="cd-drivename-now-returns-users-to-the-current-working-directory-in-that-drive"></a><span data-ttu-id="8c8de-252">`cd DriveName:` Nu returnerar användare till den aktuella arbetskatalogen i den här enheten</span><span class="sxs-lookup"><span data-stu-id="8c8de-252">`cd DriveName:` now returns users to the current working directory in that drive</span></span>

<span data-ttu-id="8c8de-253">Tidigare med hjälp av `Set-Location` eller `cd` att återgå till en PSDrive skickas användarna till standardplatsen för den här enheten.</span><span class="sxs-lookup"><span data-stu-id="8c8de-253">Previously, using `Set-Location` or `cd` to return to a PSDrive sent users to the default location for that drive.</span></span>

<span data-ttu-id="8c8de-254">Tack vare @mcbobke, användarna skickas nu till den senaste kända aktuella arbetskatalogen för den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="8c8de-254">Thanks to @mcbobke, users are now sent to the last known current working directory for that session.</span></span>

### <a name="windows-powershell-type-accelerators"></a><span data-ttu-id="8c8de-255">Acceleratorer för Windows PowerShell-typ</span><span class="sxs-lookup"><span data-stu-id="8c8de-255">Windows PowerShell type accelerators</span></span>

<span data-ttu-id="8c8de-256">Vi inkluderat följande typ-acceleratorer för att göra det lättare att arbeta med sina respektive typer i Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="8c8de-256">In Windows PowerShell, we included the following type accelerators to make it easier to work with their respective types:</span></span>

- <span data-ttu-id="8c8de-257">`[adsi]`: `System.DirectoryServices.DirectoryEntry`</span><span class="sxs-lookup"><span data-stu-id="8c8de-257">`[adsi]`: `System.DirectoryServices.DirectoryEntry`</span></span>
- <span data-ttu-id="8c8de-258">`[adsisearcher]`: `System.DirectoryServices.DirectorySearcher`</span><span class="sxs-lookup"><span data-stu-id="8c8de-258">`[adsisearcher]`: `System.DirectoryServices.DirectorySearcher`</span></span>
- <span data-ttu-id="8c8de-259">`[wmi]`: `System.Management.ManagementObject`</span><span class="sxs-lookup"><span data-stu-id="8c8de-259">`[wmi]`: `System.Management.ManagementObject`</span></span>
- <span data-ttu-id="8c8de-260">`[wmiclass]`: `System.Management.ManagementClass`</span><span class="sxs-lookup"><span data-stu-id="8c8de-260">`[wmiclass]`: `System.Management.ManagementClass`</span></span>
- <span data-ttu-id="8c8de-261">`[wmisearcher]`: `System.Management.ManagementObjectSearcher`</span><span class="sxs-lookup"><span data-stu-id="8c8de-261">`[wmisearcher]`: `System.Management.ManagementObjectSearcher`</span></span>

<span data-ttu-id="8c8de-262">Dessa typ acceleratorer inkluderades inte i PowerShell 6, men har lagts till PowerShell 6.1 som körs på Windows.</span><span class="sxs-lookup"><span data-stu-id="8c8de-262">These type accelerators were not included in PowerShell 6, but have been added to PowerShell 6.1 running on Windows.</span></span>

<span data-ttu-id="8c8de-263">Dessa typer är användbara enkelt konstruera AD och WMI-objekt.</span><span class="sxs-lookup"><span data-stu-id="8c8de-263">These types are useful in easily constructing AD and WMI objects.</span></span>

<span data-ttu-id="8c8de-264">Du kan till exempel fråga genom att använda LDAP:</span><span class="sxs-lookup"><span data-stu-id="8c8de-264">For example, you can query using LDAP:</span></span>

```powershell
[adsi]'LDAP://CN=FooUse,OU=People,DC=contoso,DC=com'
```

<span data-ttu-id="8c8de-265">Båda exemplen skapar du en Win32_OperatingSystem CIM-objekt:</span><span class="sxs-lookup"><span data-stu-id="8c8de-265">Both of these examples create a Win32_OperatingSystem CIM object:</span></span>

```powershell
[wmi]"win32_operatingsystem=@"
[wmiclass]"win32_operatingsystem"
```

```Output
SystemDirectory : C:\WINDOWS\system32
Organization    : Contoso IT
BuildNumber     : 18234
RegisteredUser  : Contoso Corp.
SerialNumber    : 12345-67890-ABCDE-F0123
Version         : 10.0.18234
```

### <a name="-lp-alias-for-all--literalpath-parameters"></a><span data-ttu-id="8c8de-266">`-lp` alias för alla `-LiteralPath` parametrar</span><span class="sxs-lookup"><span data-stu-id="8c8de-266">`-lp` alias for all `-LiteralPath` parameters</span></span>

<span data-ttu-id="8c8de-267">Tack vare @kvprasoon, nu har vi ett parameteralias `-lp` för alla inbyggda PowerShell-cmdletar som har en `-LiteralPath` parametern.</span><span class="sxs-lookup"><span data-stu-id="8c8de-267">Thanks to @kvprasoon, we now have a parameter alias `-lp` for all the built-in PowerShell cmdlets that have a `-LiteralPath` parameter.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="8c8de-268">Större ändringar</span><span class="sxs-lookup"><span data-stu-id="8c8de-268">Breaking Changes</span></span>

### <a name="msi-based-installation-paths-on-windows"></a><span data-ttu-id="8c8de-269">MSI-baserad installation sökvägar på Windows</span><span class="sxs-lookup"><span data-stu-id="8c8de-269">MSI-based installation paths on Windows</span></span>

<span data-ttu-id="8c8de-270">På Windows installerar MSI-paketet nu till följande sökväg:</span><span class="sxs-lookup"><span data-stu-id="8c8de-270">On Windows, the MSI package now installs to the following path:</span></span>

- <span data-ttu-id="8c8de-271">`$env:ProgramFiles\PowerShell\6\` för att säkra installera 6.x</span><span class="sxs-lookup"><span data-stu-id="8c8de-271">`$env:ProgramFiles\PowerShell\6\` for the stable installation of 6.x</span></span>
- <span data-ttu-id="8c8de-272">`$env:ProgramFiles\PowerShell\6-preview\` för att installera förhandsversion 6.x</span><span class="sxs-lookup"><span data-stu-id="8c8de-272">`$env:ProgramFiles\PowerShell\6-preview\` for the preview installation of 6.x</span></span>

<span data-ttu-id="8c8de-273">Den här ändringen gör att PowerShell Core kan vara uppdaterad/underhålls av Microsoft Update.</span><span class="sxs-lookup"><span data-stu-id="8c8de-273">This change ensures that PowerShell Core can be updated/serviced by Microsoft Update.</span></span>

<span data-ttu-id="8c8de-274">Mer information finns i [PowerShell RFC0026](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0026-MSI-Installation-Path.md).</span><span class="sxs-lookup"><span data-stu-id="8c8de-274">For more information, check out [PowerShell RFC0026](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0026-MSI-Installation-Path.md).</span></span>

### <a name="telemetry-can-only-be-disabled-with-an-environment-variable"></a><span data-ttu-id="8c8de-275">Telemetri kan endast inaktiveras med en miljövariabel</span><span class="sxs-lookup"><span data-stu-id="8c8de-275">Telemetry can only be disabled with an environment variable</span></span>

<span data-ttu-id="8c8de-276">PowerShell Core skickar grundläggande telemetridata till Microsoft när den startas.</span><span class="sxs-lookup"><span data-stu-id="8c8de-276">PowerShell Core sends basic telemetry data to Microsoft when it is launched.</span></span> <span data-ttu-id="8c8de-277">Data innehåller namn på operativsystem, operativsystemversion och PowerShell-version.</span><span class="sxs-lookup"><span data-stu-id="8c8de-277">The data includes the OS name, OS version, and PowerShell version.</span></span> <span data-ttu-id="8c8de-278">Den här informationen gör det möjligt för oss att bättre förstå de miljöer där PowerShell används och gör det möjligt för oss att prioritera nya funktioner och korrigeringar.</span><span class="sxs-lookup"><span data-stu-id="8c8de-278">This data allows us to better understand the environments where PowerShell is used and enables us to prioritize new features and fixes.</span></span>

<span data-ttu-id="8c8de-279">Om du vill välja bort den här telemetrin, ange miljövariabeln `POWERSHELL_TELEMETRY_OPTOUT` till `true`, `yes`, eller `1`.</span><span class="sxs-lookup"><span data-stu-id="8c8de-279">To opt-out of this telemetry, set the environment variable `POWERSHELL_TELEMETRY_OPTOUT` to `true`, `yes`, or `1`.</span></span> <span data-ttu-id="8c8de-280">Vi har inte längre stöd för borttagning av filen `DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` att inaktivera telemetri.</span><span class="sxs-lookup"><span data-stu-id="8c8de-280">We no longer support deletion of the file `DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` to disable telemetry.</span></span>

### <a name="disallowed-basic-auth-over-http-in-powershell-remoting-on-unix-platforms"></a><span data-ttu-id="8c8de-281">Tillåts inte grundläggande autentisering över HTTP i PowerShell-fjärrkommunikation för Unix-plattformar</span><span class="sxs-lookup"><span data-stu-id="8c8de-281">Disallowed Basic Auth over HTTP in PowerShell Remoting on Unix platforms</span></span>

<span data-ttu-id="8c8de-282">Om du vill förhindra användning av okrypterade trafik kräver PowerShell-fjärrkommunikation på Unix-plattformar nu användningen av NTLM/förhandla eller HTTPS.</span><span class="sxs-lookup"><span data-stu-id="8c8de-282">To prevent the use of unencrypted traffic, PowerShell Remoting on Unix platforms now requires usage of NTLM/Negotiate or HTTPS.</span></span>

<span data-ttu-id="8c8de-283">Mer information om dessa ändringar finns [PR #6799](https://github.com/PowerShell/PowerShell/pull/6799).</span><span class="sxs-lookup"><span data-stu-id="8c8de-283">For more information on these changes, check out [PR #6799](https://github.com/PowerShell/PowerShell/pull/6799).</span></span>

### <a name="removed-visualbasic-as-a-supported-language-in-add-type"></a><span data-ttu-id="8c8de-284">Ta bort `VisualBasic` som ett språk som stöds i Add-Type</span><span class="sxs-lookup"><span data-stu-id="8c8de-284">Removed `VisualBasic` as a supported language in Add-Type</span></span>

<span data-ttu-id="8c8de-285">Tidigare kunde du kompilera Visual Basic kod med den `Add-Type` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8c8de-285">In the past, you could compile Visual Basic code using the `Add-Type` cmdlet.</span></span>
<span data-ttu-id="8c8de-286">Visual Basic används sällan med `Add-Type`.</span><span class="sxs-lookup"><span data-stu-id="8c8de-286">Visual Basic was rarely used with `Add-Type`.</span></span> <span data-ttu-id="8c8de-287">Vi har tagit bort den här funktionen för att minska storleken på PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8c8de-287">We removed this feature to reduce the size of PowerShell.</span></span>

### <a name="cleaned-up-uses-of-commandtypesworkflow-and-workflowinfocleaned"></a><span data-ttu-id="8c8de-288">Rensa användningsområden för `CommandTypes.Workflow` och `WorkflowInfoCleaned`</span><span class="sxs-lookup"><span data-stu-id="8c8de-288">Cleaned up uses of `CommandTypes.Workflow` and `WorkflowInfoCleaned`</span></span>

<span data-ttu-id="8c8de-289">Mer information om dessa ändringar finns [PR #6708](https://github.com/PowerShell/PowerShell/pull/6708).</span><span class="sxs-lookup"><span data-stu-id="8c8de-289">For more information on these changes, check out [PR #6708](https://github.com/PowerShell/PowerShell/pull/6708).</span></span>