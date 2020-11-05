---
title: Nyheter i PowerShell Core 6,1
description: Nya funktioner och ändringar som lanseras i PowerShell Core 6,1
ms.date: 09/13/2018
ms.openlocfilehash: 4ff70be239197c7a4f64019d2aab42433f82f36c
ms.sourcegitcommit: 39c2a697228276d5dae39e540995fa479c2b5f39
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/05/2020
ms.locfileid: "93354668"
---
# <a name="whats-new-in-powershell-core-61"></a><span data-ttu-id="4cbb1-103">Nyheter i PowerShell Core 6,1</span><span class="sxs-lookup"><span data-stu-id="4cbb1-103">What's New in PowerShell Core 6.1</span></span>

<span data-ttu-id="4cbb1-104">Nedan visas några av de viktigaste nya funktionerna och ändringarna som har introducerats i PowerShell Core 6,1.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-104">Below is a selection of some of the major new features and changes that have been introduced in PowerShell Core 6.1.</span></span>

<span data-ttu-id="4cbb1-105">Det finns också **massor** av "tråkigae-saker" som gör PowerShell snabbare och mer stabilt (plus massor och massor av fel korrigeringar)!</span><span class="sxs-lookup"><span data-stu-id="4cbb1-105">There's also **tons** of "boring stuff" that make PowerShell faster and more stable (plus lots and lots of bug fixes)!</span></span> <span data-ttu-id="4cbb1-106">En fullständig lista över ändringar finns [i vår ändringsloggen på GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).</span><span class="sxs-lookup"><span data-stu-id="4cbb1-106">For a full list of changes, check out our [changelog on GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).</span></span>

<span data-ttu-id="4cbb1-107">Och vi kallar några namn nedan och tackar dig till [alla deltagare i communityn](https://github.com/PowerShell/PowerShell/graphs/contributors) som gjorde den här versionen möjlig.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-107">And while we call out some names below, thank you to [all of the community contributors](https://github.com/PowerShell/PowerShell/graphs/contributors) that made this release possible.</span></span>

## <a name="net-core-21"></a><span data-ttu-id="4cbb1-108">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="4cbb1-108">.NET Core 2.1</span></span>

<span data-ttu-id="4cbb1-109">PowerShell Core 6,1 flyttades till .NET Core 2,1 efter att den [släpptes i kan](https://devblogs.microsoft.com/dotnet/announcing-net-core-2-1/), vilket resulterar i ett antal förbättringar av PowerShell, inklusive:</span><span class="sxs-lookup"><span data-stu-id="4cbb1-109">PowerShell Core 6.1 moved to .NET Core 2.1 after it was [released in May](https://devblogs.microsoft.com/dotnet/announcing-net-core-2-1/), resulting in a number of improvements to PowerShell, including:</span></span>

- <span data-ttu-id="4cbb1-110">prestanda förbättringar (se [nedan](#performance-improvements))</span><span class="sxs-lookup"><span data-stu-id="4cbb1-110">performance improvements (see [below](#performance-improvements))</span></span>
- <span data-ttu-id="4cbb1-111">Stöd för Alpine Linux (för hands version)</span><span class="sxs-lookup"><span data-stu-id="4cbb1-111">Alpine Linux support (preview)</span></span>
- <span data-ttu-id="4cbb1-112">[Stöd för globalt .net-verktyg](/dotnet/core/tools/global-tools) – kommer snart till PowerShell</span><span class="sxs-lookup"><span data-stu-id="4cbb1-112">[.NET global tool support](/dotnet/core/tools/global-tools) - coming soon to PowerShell</span></span>
- [`Span<T>`](/dotnet/api/system.span-1)

## <a name="windows-compatibility-pack-for-net-core"></a><span data-ttu-id="4cbb1-113">Windows Compatibility Pack för .NET Core</span><span class="sxs-lookup"><span data-stu-id="4cbb1-113">Windows Compatibility Pack for .NET Core</span></span>

<span data-ttu-id="4cbb1-114">I Windows levererade .NET-teamet [Windows Compatibility Pack för .net Core](https://devblogs.microsoft.com/dotnet/announcing-the-windows-compatibility-pack-for-net-core/), en uppsättning sammansättningar som lägger till ett antal borttagna API: er tillbaka till .net core i Windows.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-114">On Windows, the .NET team shipped the [Windows Compatibility Pack for .NET Core](https://devblogs.microsoft.com/dotnet/announcing-the-windows-compatibility-pack-for-net-core/), a set of assemblies that add a number of removed APIs back to .NET Core on Windows.</span></span>

<span data-ttu-id="4cbb1-115">Vi har lagt till Windows-kompatibilitetspaketet till PowerShell Core 6,1-versionen så att moduler eller skript som använder dessa API: er kan vara beroende av att de är tillgängliga.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-115">We've added the Windows Compatibility Pack to PowerShell Core 6.1 release so that any modules or scripts that use these APIs can rely on them being available.</span></span>

<span data-ttu-id="4cbb1-116">Windows-kompatibilitetspaketet gör det möjligt för PowerShell Core att använda **mer än 1900 cmdlets som levereras med Windows 10 oktober 2018 Update och Windows Server 2019**.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-116">The Windows Compatibility Pack enables PowerShell Core to use **more than 1900 cmdlets that ship with Windows 10 October 2018 Update and Windows Server 2019**.</span></span>

## <a name="support-for-application-allow-lists"></a><span data-ttu-id="4cbb1-117">Stöd för listor över tillåtna program</span><span class="sxs-lookup"><span data-stu-id="4cbb1-117">Support for Application allow lists</span></span>

<span data-ttu-id="4cbb1-118">PowerShell Core 6,1 har paritet med Windows PowerShell 5,1 som stöder [AppLocker](/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview) -och [Device Guard](/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control) -program för att tillåta listor.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-118">PowerShell Core 6.1 has parity with Windows PowerShell 5.1 supporting [AppLocker](/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview) and [Device Guard](/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control) application allow lists.</span></span> <span data-ttu-id="4cbb1-119">Med listan över tillåtna program kan du få detaljerad kontroll över vilka binärfiler som kan användas för att köra dem med PowerShell- [begränsat språk läge](https://devblogs.microsoft.com/powershell/powershell-constrained-language-mode/).</span><span class="sxs-lookup"><span data-stu-id="4cbb1-119">Application allow lists allow granular control of what binaries are allowed to be executed used with PowerShell [Constrained Language mode](https://devblogs.microsoft.com/powershell/powershell-constrained-language-mode/).</span></span>

## <a name="performance-improvements"></a><span data-ttu-id="4cbb1-120">Prestandaförbättringar</span><span class="sxs-lookup"><span data-stu-id="4cbb1-120">Performance improvements</span></span>

<span data-ttu-id="4cbb1-121">PowerShell Core 6,0 gjorde några betydande prestanda förbättringar.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-121">PowerShell Core 6.0 made some significant performance improvements.</span></span> <span data-ttu-id="4cbb1-122">PowerShell Core 6,1 fortsätter att förbättra hastigheten på vissa åtgärder.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-122">PowerShell Core 6.1 continues to improve the speed of certain operations.</span></span>

<span data-ttu-id="4cbb1-123">Till exempel `Group-Object` har sped upp med 66%:</span><span class="sxs-lookup"><span data-stu-id="4cbb1-123">For example, `Group-Object` has been sped up by 66%:</span></span>

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Group-Object }
```

|    <span data-ttu-id="4cbb1-124">Mått</span><span class="sxs-lookup"><span data-stu-id="4cbb1-124">Metric</span></span>    | <span data-ttu-id="4cbb1-125">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="4cbb1-125">Windows PowerShell 5.1</span></span> | <span data-ttu-id="4cbb1-126">PowerShell Core 6,0</span><span class="sxs-lookup"><span data-stu-id="4cbb1-126">PowerShell Core 6.0</span></span> | <span data-ttu-id="4cbb1-127">PowerShell Core 6,1</span><span class="sxs-lookup"><span data-stu-id="4cbb1-127">PowerShell Core 6.1</span></span> |
| ------------ | ---------------------- | ------------------- | ------------------- |
| <span data-ttu-id="4cbb1-128">Tid (SEK)</span><span class="sxs-lookup"><span data-stu-id="4cbb1-128">Time (sec)</span></span>   | <span data-ttu-id="4cbb1-129">25,178</span><span class="sxs-lookup"><span data-stu-id="4cbb1-129">25.178</span></span>                 | <span data-ttu-id="4cbb1-130">19,653</span><span class="sxs-lookup"><span data-stu-id="4cbb1-130">19.653</span></span>              | <span data-ttu-id="4cbb1-131">6,641</span><span class="sxs-lookup"><span data-stu-id="4cbb1-131">6.641</span></span>               |
| <span data-ttu-id="4cbb1-132">Hastighets anslutning (%)</span><span class="sxs-lookup"><span data-stu-id="4cbb1-132">Speed-up (%)</span></span> | <span data-ttu-id="4cbb1-133">E.t.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-133">N/A</span></span>                    | <span data-ttu-id="4cbb1-134">21,9%</span><span class="sxs-lookup"><span data-stu-id="4cbb1-134">21.9%</span></span>               | <span data-ttu-id="4cbb1-135">66,2%</span><span class="sxs-lookup"><span data-stu-id="4cbb1-135">66.2%</span></span>               |

<span data-ttu-id="4cbb1-136">På samma sätt har sorterings scenarier som det här förbättrats med mer än 15%:</span><span class="sxs-lookup"><span data-stu-id="4cbb1-136">Similarly, sorting scenarios like this one have improved by more than 15%:</span></span>

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Sort-Object }
```

|    <span data-ttu-id="4cbb1-137">Mått</span><span class="sxs-lookup"><span data-stu-id="4cbb1-137">Metric</span></span>    | <span data-ttu-id="4cbb1-138">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="4cbb1-138">Windows PowerShell 5.1</span></span> | <span data-ttu-id="4cbb1-139">PowerShell Core 6,0</span><span class="sxs-lookup"><span data-stu-id="4cbb1-139">PowerShell Core 6.0</span></span> | <span data-ttu-id="4cbb1-140">PowerShell Core 6,1</span><span class="sxs-lookup"><span data-stu-id="4cbb1-140">PowerShell Core 6.1</span></span> |
| ------------ | ---------------------- | ------------------- | ------------------- |
| <span data-ttu-id="4cbb1-141">Tid (SEK)</span><span class="sxs-lookup"><span data-stu-id="4cbb1-141">Time (sec)</span></span>   | <span data-ttu-id="4cbb1-142">12,170</span><span class="sxs-lookup"><span data-stu-id="4cbb1-142">12.170</span></span>                 | <span data-ttu-id="4cbb1-143">8,493</span><span class="sxs-lookup"><span data-stu-id="4cbb1-143">8.493</span></span>               | <span data-ttu-id="4cbb1-144">7,08</span><span class="sxs-lookup"><span data-stu-id="4cbb1-144">7.08</span></span>                |
| <span data-ttu-id="4cbb1-145">Hastighets anslutning (%)</span><span class="sxs-lookup"><span data-stu-id="4cbb1-145">Speed-up (%)</span></span> | <span data-ttu-id="4cbb1-146">E.t.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-146">N/A</span></span>                    | <span data-ttu-id="4cbb1-147">30,2%</span><span class="sxs-lookup"><span data-stu-id="4cbb1-147">30.2%</span></span>               | <span data-ttu-id="4cbb1-148">16,6%</span><span class="sxs-lookup"><span data-stu-id="4cbb1-148">16.6%</span></span>               |

<span data-ttu-id="4cbb1-149">`Import-Csv` har också sped varit märkbart efter en regression från Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-149">`Import-Csv` has also been sped up significantly after a regression from Windows PowerShell.</span></span>
<span data-ttu-id="4cbb1-150">I följande exempel används en test-CSV med 26 616 rader och sex kolumner:</span><span class="sxs-lookup"><span data-stu-id="4cbb1-150">The following example uses a test CSV with 26,616 rows and six columns:</span></span>

```powershell
Measure-Command {$a = Import-Csv foo.csv}
```

|    <span data-ttu-id="4cbb1-151">Mått</span><span class="sxs-lookup"><span data-stu-id="4cbb1-151">Metric</span></span>    | <span data-ttu-id="4cbb1-152">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="4cbb1-152">Windows PowerShell 5.1</span></span> | <span data-ttu-id="4cbb1-153">PowerShell Core 6,0</span><span class="sxs-lookup"><span data-stu-id="4cbb1-153">PowerShell Core 6.0</span></span> |  <span data-ttu-id="4cbb1-154">PowerShell Core 6,1</span><span class="sxs-lookup"><span data-stu-id="4cbb1-154">PowerShell Core 6.1</span></span>   |
| ------------ | ---------------------- | ------------------- | ---------------------- |
| <span data-ttu-id="4cbb1-155">Tid (SEK)</span><span class="sxs-lookup"><span data-stu-id="4cbb1-155">Time (sec)</span></span>   | <span data-ttu-id="4cbb1-156">0,441</span><span class="sxs-lookup"><span data-stu-id="4cbb1-156">0.441</span></span>                  | <span data-ttu-id="4cbb1-157">1,069</span><span class="sxs-lookup"><span data-stu-id="4cbb1-157">1.069</span></span>               | <span data-ttu-id="4cbb1-158">0,268</span><span class="sxs-lookup"><span data-stu-id="4cbb1-158">0.268</span></span>                  |
| <span data-ttu-id="4cbb1-159">Hastighets anslutning (%)</span><span class="sxs-lookup"><span data-stu-id="4cbb1-159">Speed-up (%)</span></span> | <span data-ttu-id="4cbb1-160">E.t.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-160">N/A</span></span>                    | <span data-ttu-id="4cbb1-161">– 142,4%</span><span class="sxs-lookup"><span data-stu-id="4cbb1-161">-142.4%</span></span>             | <span data-ttu-id="4cbb1-162">74,9% (39,2% från WPS)</span><span class="sxs-lookup"><span data-stu-id="4cbb1-162">74.9% (39.2% from WPS)</span></span> |

<span data-ttu-id="4cbb1-163">Till sist har konverteringen från JSON till `PSObject` sped upp med mer än 50% sedan Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-163">Lastly, conversion from JSON into `PSObject` has been sped up by more than 50% since Windows PowerShell.</span></span>
<span data-ttu-id="4cbb1-164">I följande exempel används ~ 2 MB test-JSON-fil:</span><span class="sxs-lookup"><span data-stu-id="4cbb1-164">The following example uses a ~2MB test JSON file:</span></span>

```powershell
Measure-Command {Get-Content .\foo.json | ConvertFrom-Json}
```

|    <span data-ttu-id="4cbb1-165">Mått</span><span class="sxs-lookup"><span data-stu-id="4cbb1-165">Metric</span></span>    | <span data-ttu-id="4cbb1-166">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="4cbb1-166">Windows PowerShell 5.1</span></span> | <span data-ttu-id="4cbb1-167">PowerShell Core 6,0</span><span class="sxs-lookup"><span data-stu-id="4cbb1-167">PowerShell Core 6.0</span></span> |  <span data-ttu-id="4cbb1-168">PowerShell Core 6,1</span><span class="sxs-lookup"><span data-stu-id="4cbb1-168">PowerShell Core 6.1</span></span>   |
| ------------ | ---------------------- | ------------------- | ---------------------- |
| <span data-ttu-id="4cbb1-169">Tid (SEK)</span><span class="sxs-lookup"><span data-stu-id="4cbb1-169">Time (sec)</span></span>   | <span data-ttu-id="4cbb1-170">0,259</span><span class="sxs-lookup"><span data-stu-id="4cbb1-170">0.259</span></span>                  | <span data-ttu-id="4cbb1-171">0,577</span><span class="sxs-lookup"><span data-stu-id="4cbb1-171">0.577</span></span>               | <span data-ttu-id="4cbb1-172">0.125</span><span class="sxs-lookup"><span data-stu-id="4cbb1-172">0.125</span></span>                  |
| <span data-ttu-id="4cbb1-173">Hastighets anslutning (%)</span><span class="sxs-lookup"><span data-stu-id="4cbb1-173">Speed-up (%)</span></span> | <span data-ttu-id="4cbb1-174">E.t.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-174">N/A</span></span>                    | <span data-ttu-id="4cbb1-175">– 122,8%</span><span class="sxs-lookup"><span data-stu-id="4cbb1-175">-122.8%</span></span>             | <span data-ttu-id="4cbb1-176">78,3% (51,7% från WPS)</span><span class="sxs-lookup"><span data-stu-id="4cbb1-176">78.3% (51.7% from WPS)</span></span> |

## <a name="check-system32-for-compatible-built-in-modules-on-windows"></a><span data-ttu-id="4cbb1-177">Sök `system32` efter kompatibla inbyggda moduler i Windows</span><span class="sxs-lookup"><span data-stu-id="4cbb1-177">Check `system32` for compatible built-in modules on Windows</span></span>

<span data-ttu-id="4cbb1-178">I Windows 10 1809-uppdateringen och Windows Server 2019 har vi uppdaterat ett antal inbyggda PowerShell-moduler för att markera dem som kompatibla med PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-178">In the Windows 10 1809 update and Windows Server 2019, we updated a number of built-in PowerShell modules to mark them as compatible with PowerShell Core.</span></span>

<span data-ttu-id="4cbb1-179">När PowerShell Core 6,1 startas tas den automatiskt med `$windir\System32` som en del av `PSModulePath` miljövariabeln.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-179">When PowerShell Core 6.1 starts up, it will automatically include `$windir\System32` as part of the `PSModulePath` environment variable.</span></span> <span data-ttu-id="4cbb1-180">Det exponerar dock bara moduler för `Get-Module` och `Import-Module` om det `CompatiblePSEdition` är markerat som kompatibelt med `Core` .</span><span class="sxs-lookup"><span data-stu-id="4cbb1-180">However, it only exposes modules to `Get-Module` and `Import-Module` if its `CompatiblePSEdition` is marked as compatible with `Core`.</span></span>

```powershell
Get-Module -ListAvailable
```

> [!NOTE]
> <span data-ttu-id="4cbb1-181">Du kan se olika tillgängliga moduler beroende på vilka roller och funktioner som är installerade.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-181">You may see different available modules depending on what roles and features are installed.</span></span>

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

<span data-ttu-id="4cbb1-182">Du kan åsidosätta det här beteendet för att visa alla moduler med hjälp av `-SkipEditionCheck` switch-parametern.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-182">You can override this behavior to show all modules using the `-SkipEditionCheck` switch parameter.</span></span>
<span data-ttu-id="4cbb1-183">Vi har också lagt till en `PSEdition` egenskap i tabellens utdata.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-183">We've also added a `PSEdition` property to the table output.</span></span>

```powershell
Get-Module Net* -ListAvailable -SkipEditionCheck
```

```Output
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                        PSEdition ExportedCommands
---------- -------    ----                        --------- ----------------
Manifest   2.0.0.0    NetAdapter                  Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetConnection               Core,Desk {Get-NetConnectionProfile, Set-NetConnectionProf...
Manifest   1.0.0.0    NetDiagnostics              Desk      Get-NetView
Manifest   1.0.0.0    NetEventPacketCapture       Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                     Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                      Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                      Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                 Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam               Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetTCPIP                    Core,Desk {Get-NetIPAddress, Get-NetIPInterface, Get-NetIP...
Manifest   1.0.0.0    NetWNV                      Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   1.0.0.0    NetworkConnectivityStatus   Core,Desk {Get-DAConnectionStatus, Get-NCSIPolicyConfigura...
Manifest   1.0.0.0    NetworkSwitchManager        Core,Desk {Disable-NetworkSwitchEthernetPort, Enable-Netwo...
Manifest   1.0.0.0    NetworkTransition           Core,Desk {Add-NetIPHttpsCertBinding, Disable-NetDnsTransi...
```

<span data-ttu-id="4cbb1-184">Mer information om det här problemet finns i [PowerShell-RFC0025](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-PSCore6-and-Windows-Modules.md).</span><span class="sxs-lookup"><span data-stu-id="4cbb1-184">For more information about this behavior, check out [PowerShell RFC0025](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-PSCore6-and-Windows-Modules.md).</span></span>

## <a name="markdown-cmdlets-and-rendering"></a><span data-ttu-id="4cbb1-185">Markdown-cmdletar och rendering</span><span class="sxs-lookup"><span data-stu-id="4cbb1-185">Markdown cmdlets and rendering</span></span>

<span data-ttu-id="4cbb1-186">Markdown är en standard för att skapa läsbara klartext-dokument med grundläggande formatering som kan återges i HTML.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-186">Markdown is a standard for creating readable plaintext documents with basic formatting that can be rendered into HTML.</span></span>

<span data-ttu-id="4cbb1-187">Vi har lagt till några cmdletar i 6,1 som gör det möjligt att konvertera och återge markdown-dokument i-konsolen, inklusive:</span><span class="sxs-lookup"><span data-stu-id="4cbb1-187">We've added some cmdlets in 6.1 that allow you to convert and render Markdown documents in the console, including:</span></span>

- `ConvertFrom-Markdown`
- `Get-MarkdownOption`
- `Set-MarkdownOption`
- `Show-Markdown`

<span data-ttu-id="4cbb1-188">Återge till exempel `Show-Markdown` en MARKDOWN-fil i-konsolen:</span><span class="sxs-lookup"><span data-stu-id="4cbb1-188">For example, `Show-Markdown` renders a Markdown file in the console:</span></span>

![Show-Markdown exempel](media/What-s-New-in-PowerShell-Core-61/markdown_example.png)

<span data-ttu-id="4cbb1-190">Mer information om hur dessa cmdlets fungerar finns i [denna RFC](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-Native-Markdown-Rendering.md).</span><span class="sxs-lookup"><span data-stu-id="4cbb1-190">For more information about how these cmdlets work, check out [this RFC](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-Native-Markdown-Rendering.md).</span></span>

## <a name="experimental-feature-flags"></a><span data-ttu-id="4cbb1-191">Experimentella funktions flaggor</span><span class="sxs-lookup"><span data-stu-id="4cbb1-191">Experimental feature flags</span></span>

<span data-ttu-id="4cbb1-192">Vi har aktiverat stöd för [experimentella funktioner][].</span><span class="sxs-lookup"><span data-stu-id="4cbb1-192">We enabled support for [Experimental Features][].</span></span> <span data-ttu-id="4cbb1-193">Detta gör att PowerShell-utvecklare kan leverera nya funktioner och få feedback innan designen är klar.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-193">This allows PowerShell developers to deliver new features and get feedback before the design is complete.</span></span> <span data-ttu-id="4cbb1-194">På så sätt undviker vi att göra ändringar när designen utvecklas.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-194">This way we avoid making breaking changes as the design evolves.</span></span>

<span data-ttu-id="4cbb1-195">Använd `Get-ExperimentalFeature` för att hämta en lista över tillgängliga experimentella funktioner.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-195">Use `Get-ExperimentalFeature` to get a list of available experimental features.</span></span> <span data-ttu-id="4cbb1-196">Du kan aktivera eller inaktivera dessa funktioner med `Enable-ExperimentalFeature` och `Disable-ExperimentalFeature` .</span><span class="sxs-lookup"><span data-stu-id="4cbb1-196">You can enable or disable these features with `Enable-ExperimentalFeature` and `Disable-ExperimentalFeature`.</span></span>

<span data-ttu-id="4cbb1-197">Du kan lära dig mer om den här funktionen i [PowerShell-RFC0029](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md).</span><span class="sxs-lookup"><span data-stu-id="4cbb1-197">You can learn more about this feature in [PowerShell RFC0029](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md).</span></span>

## <a name="web-cmdlet-improvements"></a><span data-ttu-id="4cbb1-198">Förbättringar av webb-cmdlet</span><span class="sxs-lookup"><span data-stu-id="4cbb1-198">Web cmdlet improvements</span></span>

<span data-ttu-id="4cbb1-199">Till [@markekraus](https://github.com/markekraus) och med en hel sväng av förbättringar har gjorts i våra webb-cmdlets: [`Invoke-WebRequest`](/powershell/module/microsoft.powershell.utility/invoke-webrequest)</span><span class="sxs-lookup"><span data-stu-id="4cbb1-199">Thanks to [@markekraus](https://github.com/markekraus), a whole slew of improvements have been made to our web cmdlets: [`Invoke-WebRequest`](/powershell/module/microsoft.powershell.utility/invoke-webrequest)</span></span>
<span data-ttu-id="4cbb1-200">och [`Invoke-RestMethod`](/powershell/module/microsoft.powershell.utility/invoke-restmethod) .</span><span class="sxs-lookup"><span data-stu-id="4cbb1-200">and [`Invoke-RestMethod`](/powershell/module/microsoft.powershell.utility/invoke-restmethod).</span></span>

- <span data-ttu-id="4cbb1-201">[PR #6109](https://github.com/PowerShell/PowerShell/pull/6109) – standard kodningen anges till UTF-8 för `application-json` svar</span><span class="sxs-lookup"><span data-stu-id="4cbb1-201">[PR #6109](https://github.com/PowerShell/PowerShell/pull/6109) - default encoding set to UTF-8 for `application-json` responses</span></span>
- <span data-ttu-id="4cbb1-202">[PR-#6018](https://github.com/PowerShell/PowerShell/pull/6018) - `-SkipHeaderValidation` parameter för att tillåta `Content-Type` huvuden som inte är standarder-kompatibla</span><span class="sxs-lookup"><span data-stu-id="4cbb1-202">[PR #6018](https://github.com/PowerShell/PowerShell/pull/6018) - `-SkipHeaderValidation` parameter to allow `Content-Type` headers that aren't standards-compliant</span></span>
- <span data-ttu-id="4cbb1-203">[PR-#5972](https://github.com/PowerShell/PowerShell/pull/5972) - `Form` parameter för stöd för förenklad `multipart/form-data` Support</span><span class="sxs-lookup"><span data-stu-id="4cbb1-203">[PR #5972](https://github.com/PowerShell/PowerShell/pull/5972) - `Form` parameter to support simplified `multipart/form-data` support</span></span>
- <span data-ttu-id="4cbb1-204">[PR #6338](https://github.com/PowerShell/PowerShell/pull/6338) -kompatibel, SKIFT läges okänslig hantering av Relations nycklar</span><span class="sxs-lookup"><span data-stu-id="4cbb1-204">[PR #6338](https://github.com/PowerShell/PowerShell/pull/6338) - Compliant, case-insensitive handling of relation keys</span></span>
- <span data-ttu-id="4cbb1-205">[PR #6447](https://github.com/PowerShell/PowerShell/pull/6447) – Lägg till `-Resume` parameter för webb-cmdletar</span><span class="sxs-lookup"><span data-stu-id="4cbb1-205">[PR #6447](https://github.com/PowerShell/PowerShell/pull/6447) - Add `-Resume` parameter for web cmdlets</span></span>

## <a name="remoting-improvements"></a><span data-ttu-id="4cbb1-206">Förbättringar av fjärrkommunikation</span><span class="sxs-lookup"><span data-stu-id="4cbb1-206">Remoting improvements</span></span>

### <a name="powershell-direct-for-containers-tries-to-use-powershell-core-first"></a><span data-ttu-id="4cbb1-207">PowerShell Direct för behållare försöker använda PowerShell Core först</span><span class="sxs-lookup"><span data-stu-id="4cbb1-207">PowerShell Direct for Containers tries to use PowerShell Core first</span></span>

<span data-ttu-id="4cbb1-208">[PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct) är en funktion i PowerShell och Hyper-v som gör att du kan ansluta till en virtuell Hyper-V-dator eller-behållare utan nätverks anslutning eller andra tjänster för fjärrhantering.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-208">[PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct) is a feature of PowerShell and Hyper-V that allows you to connect to a Hyper-V VM or Container without network connectivity or other remote management services.</span></span>

<span data-ttu-id="4cbb1-209">Tidigare anslöt PowerShell Direct till med den inbyggda Windows PowerShell-instansen på behållaren.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-209">In the past, PowerShell Direct connected using the built-in Windows PowerShell instance on the Container.</span></span> <span data-ttu-id="4cbb1-210">Nu försöker PowerShell Direct först ansluta med alla tillgängliga `pwsh.exe` på `PATH` miljö variabeln.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-210">Now, PowerShell Direct first attempts to connect using any available `pwsh.exe` on the `PATH` environment variable.</span></span> <span data-ttu-id="4cbb1-211">Om `pwsh.exe` inte är tillgängligt går PowerShell Direct tillbaka till att använda `powershell.exe` .</span><span class="sxs-lookup"><span data-stu-id="4cbb1-211">If `pwsh.exe` isn't available, PowerShell Direct falls back to use `powershell.exe`.</span></span>

### <a name="enable-psremoting-now-creates-separate-remoting-endpoints-for-preview-versions"></a><span data-ttu-id="4cbb1-212">`Enable-PSRemoting` skapar nu separata Fjärrslutpunkter för för hands versioner</span><span class="sxs-lookup"><span data-stu-id="4cbb1-212">`Enable-PSRemoting` now creates separate remoting endpoints for preview versions</span></span>

<span data-ttu-id="4cbb1-213">`Enable-PSRemoting` nu skapas två konfigurationer för fjärrsessioner:</span><span class="sxs-lookup"><span data-stu-id="4cbb1-213">`Enable-PSRemoting` now creates two remoting session configurations:</span></span>

- <span data-ttu-id="4cbb1-214">En för den högre versionen av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-214">One for the major version of PowerShell.</span></span> <span data-ttu-id="4cbb1-215">Exempelvis `PowerShell.6`.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-215">For example, `PowerShell.6`.</span></span> <span data-ttu-id="4cbb1-216">Den här slut punkten som kan förlita sig på en del versions uppdateringar som "system-bred" PowerShell 6-session konfiguration</span><span class="sxs-lookup"><span data-stu-id="4cbb1-216">This endpoint that can be relied upon across minor version updates as the "system-wide" PowerShell 6 session configuration</span></span>
- <span data-ttu-id="4cbb1-217">En version – en konfiguration av en speciell session, till exempel: `PowerShell.6.1.0`</span><span class="sxs-lookup"><span data-stu-id="4cbb1-217">One version-specific session configuration, for example: `PowerShell.6.1.0`</span></span>

<span data-ttu-id="4cbb1-218">Det här beteendet är användbart om du vill ha flera PowerShell 6-versioner installerade och tillgängliga på samma dator.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-218">This behavior is useful if you want to have multiple PowerShell 6 versions installed and accessible on the same machine.</span></span>

<span data-ttu-id="4cbb1-219">Dessutom hämtar för hands versioner av PowerShell sina egna konfigurationer för fjärrsessioner efter att du kört `Enable-PSRemoting` cmdleten:</span><span class="sxs-lookup"><span data-stu-id="4cbb1-219">Additionally, preview versions of PowerShell now get their own remoting session configurations after running the `Enable-PSRemoting` cmdlet:</span></span>

```powershell
C:\WINDOWS\system32> Enable-PSRemoting
```

<span data-ttu-id="4cbb1-220">Dina utdata kan vara olika om du inte har konfigurerat WinRM tidigare.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-220">Your output may be different if you haven't set up WinRM before.</span></span>

```Output
WinRM is already set up to receive requests on this computer.
WinRM is already set up for remote management on this computer.
```

<span data-ttu-id="4cbb1-221">Sedan kan du se separata PowerShell-sessionsbaserade för för hands versionen och stabila versioner av PowerShell 6, och för varje enskild version.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-221">Then you can see separate PowerShell session configurations for the preview and stable builds of PowerShell 6, and for each specific version.</span></span>

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

### <a name="userhostport-syntax-supported-for-ssh"></a><span data-ttu-id="4cbb1-222">`user@host:port` syntax som stöds för SSH</span><span class="sxs-lookup"><span data-stu-id="4cbb1-222">`user@host:port` syntax supported for SSH</span></span>

<span data-ttu-id="4cbb1-223">SSH-klienter stöder vanligt vis en anslutnings sträng i formatet `user@host:port` .</span><span class="sxs-lookup"><span data-stu-id="4cbb1-223">SSH clients typically support a connection string in the format `user@host:port`.</span></span> <span data-ttu-id="4cbb1-224">Med tillägget av SSH som ett protokoll för PowerShell-fjärrkommunikation har vi lagt till stöd för det här formatet för anslutnings strängen:</span><span class="sxs-lookup"><span data-stu-id="4cbb1-224">With the addition of SSH as a protocol for PowerShell Remoting, we've added support for this format of connection string:</span></span>

`Enter-PSSession -HostName fooUser@ssh.contoso.com:2222`

## <a name="msi-option-to-add-explorer-shell-context-menu-on-windows"></a><span data-ttu-id="4cbb1-225">MSI-alternativ för att lägga till Explorer Shell snabb menyn i Windows</span><span class="sxs-lookup"><span data-stu-id="4cbb1-225">MSI option to add explorer shell context menu on Windows</span></span>

<span data-ttu-id="4cbb1-226">Tack för [@bergmeister](https://github.com/bergmeister) kan du nu aktivera en snabb meny i Windows.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-226">Thanks to [@bergmeister](https://github.com/bergmeister), now you can enable a context menu on Windows.</span></span> <span data-ttu-id="4cbb1-227">Nu kan du öppna din systemomfattande installation av PowerShell 6,1 från valfri mapp i Utforskaren i Windows:</span><span class="sxs-lookup"><span data-stu-id="4cbb1-227">Now you can open your system-wide installation of PowerShell 6.1 from any folder in the Windows Explorer:</span></span>

![Snabb menyn i Shell för PowerShell 6](media/What-s-New-in-PowerShell-Core-61/shell_context_menu.png)

## <a name="goodies"></a><span data-ttu-id="4cbb1-229">Godbitar</span><span class="sxs-lookup"><span data-stu-id="4cbb1-229">Goodies</span></span>

### <a name="run-as-administrator-in-the-windows-shortcut-jump-list"></a><span data-ttu-id="4cbb1-230">"Kör som administratör" i Windows Shortcuts snabb lista</span><span class="sxs-lookup"><span data-stu-id="4cbb1-230">"Run as Administrator" in the Windows shortcut jump list</span></span>

<span data-ttu-id="4cbb1-231">Tack vare [@bergmeister](https://github.com/bergmeister) , innehåller PowerShell Core-genvägens snabb lista nu "kör som administratör":</span><span class="sxs-lookup"><span data-stu-id="4cbb1-231">Thanks to [@bergmeister](https://github.com/bergmeister), the PowerShell Core shortcut's jump list now includes "Run as Administrator":</span></span>

![Kör som administratör i snabb listan för PowerShell 6](media/What-s-New-in-PowerShell-Core-61/jumplist.png)

### <a name="cd---returns-to-previous-directory"></a><span data-ttu-id="4cbb1-233">`cd -` återgår till föregående katalog</span><span class="sxs-lookup"><span data-stu-id="4cbb1-233">`cd -` returns to previous directory</span></span>

```powershell
C:\Windows\System32> cd C:\
C:\> cd -
C:\Windows\System32>
```

<span data-ttu-id="4cbb1-234">Eller på Linux:</span><span class="sxs-lookup"><span data-stu-id="4cbb1-234">Or on Linux:</span></span>

```ShellSession
PS /etc> cd /usr/bin
PS /usr/bin> cd -
PS /etc>
```

<span data-ttu-id="4cbb1-235">Även `cd` och `cd --` ändra till `$HOME` .</span><span class="sxs-lookup"><span data-stu-id="4cbb1-235">Also, `cd` and `cd --` change to `$HOME`.</span></span>

### `Test-Connection`

<span data-ttu-id="4cbb1-236">Till [@iSazonov](https://github.com/iSazonov) och [`Test-Connection`](/powershell/module/microsoft.powershell.management/test-connection) med har cmdleten hamnat till PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-236">Thanks to [@iSazonov](https://github.com/iSazonov), the [`Test-Connection`](/powershell/module/microsoft.powershell.management/test-connection) cmdlet has been ported to PowerShell Core.</span></span>

### <a name="update-help-as-non-admin"></a><span data-ttu-id="4cbb1-237">`Update-Help` som icke-administratör</span><span class="sxs-lookup"><span data-stu-id="4cbb1-237">`Update-Help` as non-admin</span></span>

<span data-ttu-id="4cbb1-238">Efter populära behov `Update-Help` behöver inte längre köras som administratör.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-238">By popular demand, `Update-Help` no longer needs to be run as an administrator.</span></span> <span data-ttu-id="4cbb1-239">`Update-Help` nu ska vi använda standardinställningarna för att spara hjälp till en mapp med användar omfång.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-239">`Update-Help` now defaults to saving help to a user-scoped folder.</span></span>

### <a name="new-methodsproperties-on-pscustomobject"></a><span data-ttu-id="4cbb1-240">Nya metoder/egenskaper på `PSCustomObject`</span><span class="sxs-lookup"><span data-stu-id="4cbb1-240">New methods/properties on `PSCustomObject`</span></span>

<span data-ttu-id="4cbb1-241">Tack för [@iSazonov](https://github.com/iSazonov) , har vi lagt till nya metoder och egenskaper för `PSCustomObject` .</span><span class="sxs-lookup"><span data-stu-id="4cbb1-241">Thanks to [@iSazonov](https://github.com/iSazonov), we've added new methods and properties to `PSCustomObject`.</span></span> <span data-ttu-id="4cbb1-242">`PSCustomObject`innehåller nu en `Count` / `Length` egenskap som andra objekt.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-242">`PSCustomObject` now includes a `Count`/`Length` property like other objects.</span></span>

```powershell
$PSCustomObject = [pscustomobject]@{foo = 1}

$PSCustomObject.Length
```

```Output
1
```

```powershell
$PSCustomObject.Count
```

```Output
1
```

<span data-ttu-id="4cbb1-243">Det här arbetet innehåller också `ForEach` och `Where` metoder som gör att du kan använda och filtrera efter `PSCustomObject` objekt:</span><span class="sxs-lookup"><span data-stu-id="4cbb1-243">This work also includes `ForEach` and `Where` methods that allow you to operate and filter on `PSCustomObject` items:</span></span>

```powershell
$PSCustomObject.ForEach({$_.foo + 1})
```

```Output
2
```

```powershell
$PSCustomObject.Where({$_.foo -gt 0})
```

```Output
foo
---
  1
```

### `Where-Object -Not`

<span data-ttu-id="4cbb1-244">Tack för @SimonWahlin , har vi lagt till- `-Not` parametern i `Where-Object` .</span><span class="sxs-lookup"><span data-stu-id="4cbb1-244">Thanks to @SimonWahlin, we've added the `-Not` parameter to `Where-Object`.</span></span> <span data-ttu-id="4cbb1-245">Nu kan du filtrera ett objekt i pipelinen för att det inte finns någon egenskap, eller ett egenskaps värde som är null/tomt.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-245">Now you can filter an object at the pipeline for the non-existence of a property, or a null/empty property value.</span></span>

<span data-ttu-id="4cbb1-246">Det här kommandot returnerar till exempel alla tjänster som inte har några beroende tjänster definierade:</span><span class="sxs-lookup"><span data-stu-id="4cbb1-246">For example, this command returns all services that don't have any dependent services defined:</span></span>

```powershell
Get-Service | Where-Object -Not DependentServices
```

### <a name="new-modulemanifest-creates-a-bom-less-utf-8-document"></a><span data-ttu-id="4cbb1-247">`New-ModuleManifest` skapar ett struktur löst UTF-8-dokument</span><span class="sxs-lookup"><span data-stu-id="4cbb1-247">`New-ModuleManifest` creates a BOM-less UTF-8 document</span></span>

<span data-ttu-id="4cbb1-248">Med tanke på vår flytt till BOM-mindre UTF-8 i PowerShell 6,0 har vi uppdaterat `New-ModuleManifest` cmdleten för att skapa ett BOM-mindre UTF-8-dokument i stället för ett UTF-16 1.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-248">Given our move to BOM-less UTF-8 in PowerShell 6.0, we've updated the `New-ModuleManifest` cmdlet to create a BOM-less UTF-8 document instead of a UTF-16 one.</span></span>

### <a name="conversions-from-psmethod-to-delegate"></a><span data-ttu-id="4cbb1-249">Konverteringar från PSMethod till delegate</span><span class="sxs-lookup"><span data-stu-id="4cbb1-249">Conversions from PSMethod to Delegate</span></span>

<span data-ttu-id="4cbb1-250">Tack för [@powercode](https://github.com/powercode) har vi nu stöd för konverteringen av a `PSMethod` till ett ombud.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-250">Thanks to [@powercode](https://github.com/powercode), we now support the conversion of a `PSMethod` into a delegate.</span></span> <span data-ttu-id="4cbb1-251">På så sätt kan du göra saker som att skicka `PSMethod` `[M]::DoubleStrLen` som ett ombuds värde till `[M]::AggregateString` :</span><span class="sxs-lookup"><span data-stu-id="4cbb1-251">This allows you to do things like passing `PSMethod` `[M]::DoubleStrLen` as a delegate value into `[M]::AggregateString`:</span></span>

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

<span data-ttu-id="4cbb1-252">Om du vill ha mer information om den här ändringen kan du kolla in [PR #5287](https://github.com/PowerShell/PowerShell/pull/5287).</span><span class="sxs-lookup"><span data-stu-id="4cbb1-252">For more info on this change, check out [PR #5287](https://github.com/PowerShell/PowerShell/pull/5287).</span></span>

### <a name="standard-deviation-in-measure-object"></a><span data-ttu-id="4cbb1-253">Standard avvikelse i `Measure-Object`</span><span class="sxs-lookup"><span data-stu-id="4cbb1-253">Standard deviation in `Measure-Object`</span></span>

<span data-ttu-id="4cbb1-254">Tack för [@CloudyDino](https://github.com/CloudyDino) , har vi lagt till en `StandardDeviation` egenskap för `Measure-Object` :</span><span class="sxs-lookup"><span data-stu-id="4cbb1-254">Thanks to [@CloudyDino](https://github.com/CloudyDino), we've added a `StandardDeviation` property to `Measure-Object`:</span></span>

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

<span data-ttu-id="4cbb1-255">Tack än [@maybe-hello-world](https://github.com/maybe-hello-world) , `Get-PfxCertificate` har nu `Password` parametern, som tar en `SecureString` .</span><span class="sxs-lookup"><span data-stu-id="4cbb1-255">Thanks to [@maybe-hello-world](https://github.com/maybe-hello-world), `Get-PfxCertificate` now has the `Password` parameter, which takes a `SecureString`.</span></span> <span data-ttu-id="4cbb1-256">På så sätt kan du använda den icke-interaktivt:</span><span class="sxs-lookup"><span data-stu-id="4cbb1-256">This allows you to use it non-interactively:</span></span>

```powershell
$certFile = '\\server\share\pwd-protected.pfx'
$certPass = Read-Host -AsSecureString -Prompt 'Enter the password for certificate: '

$certThumbPrint = (Get-PfxCertificate -FilePath $certFile -Password $certPass ).ThumbPrint
```

### <a name="removal-of-the-more-function"></a><span data-ttu-id="4cbb1-257">Borttagning av `more` funktionen</span><span class="sxs-lookup"><span data-stu-id="4cbb1-257">Removal of the `more` function</span></span>

<span data-ttu-id="4cbb1-258">Tidigare levererade PowerShell en funktion i Windows `more` som har omslutits `more.com` .</span><span class="sxs-lookup"><span data-stu-id="4cbb1-258">In the past, PowerShell shipped a function on Windows called `more` that wrapped `more.com`.</span></span> <span data-ttu-id="4cbb1-259">Funktionen har nu tagits bort.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-259">That function has now been removed.</span></span>

<span data-ttu-id="4cbb1-260">`help`Funktionen ändrades också till att användas `more.com` i Windows eller systemets standard-pager som anges av `$env:PAGER` på andra plattformar än Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-260">Also, the `help` function changed to use `more.com` on Windows, or the system's default pager specified by `$env:PAGER` on non-Windows platforms.</span></span>

### <a name="cd-drivename-now-returns-users-to-the-current-working-directory-in-that-drive"></a><span data-ttu-id="4cbb1-261">`cd DriveName:` returnerar nu användare till den aktuella arbets katalogen i den enheten</span><span class="sxs-lookup"><span data-stu-id="4cbb1-261">`cd DriveName:` now returns users to the current working directory in that drive</span></span>

<span data-ttu-id="4cbb1-262">Tidigare har du använt `Set-Location` eller `cd` för att återgå till en PSDrive som har skickat användare till standard platsen för den enheten.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-262">Previously, using `Set-Location` or `cd` to return to a PSDrive sent users to the default location for that drive.</span></span>

<span data-ttu-id="4cbb1-263">Till [@mcbobke](https://github.com/mcbobke) och med skickas nu användare till den senast kända aktuella arbets katalogen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-263">Thanks to [@mcbobke](https://github.com/mcbobke), users are now sent to the last known current working directory for that session.</span></span>

### <a name="windows-powershell-type-accelerators"></a><span data-ttu-id="4cbb1-264">Windows PowerShell-typ acceleratorer</span><span class="sxs-lookup"><span data-stu-id="4cbb1-264">Windows PowerShell type accelerators</span></span>

<span data-ttu-id="4cbb1-265">I Windows PowerShell inkluderade vi följande typ acceleratorer för att göra det enklare att arbeta med sina respektive typer:</span><span class="sxs-lookup"><span data-stu-id="4cbb1-265">In Windows PowerShell, we included the following type accelerators to make it easier to work with their respective types:</span></span>

- <span data-ttu-id="4cbb1-266">`[adsi]`: `System.DirectoryServices.DirectoryEntry`</span><span class="sxs-lookup"><span data-stu-id="4cbb1-266">`[adsi]`: `System.DirectoryServices.DirectoryEntry`</span></span>
- <span data-ttu-id="4cbb1-267">`[adsisearcher]`: `System.DirectoryServices.DirectorySearcher`</span><span class="sxs-lookup"><span data-stu-id="4cbb1-267">`[adsisearcher]`: `System.DirectoryServices.DirectorySearcher`</span></span>
- <span data-ttu-id="4cbb1-268">`[wmi]`: `System.Management.ManagementObject`</span><span class="sxs-lookup"><span data-stu-id="4cbb1-268">`[wmi]`: `System.Management.ManagementObject`</span></span>
- <span data-ttu-id="4cbb1-269">`[wmiclass]`: `System.Management.ManagementClass`</span><span class="sxs-lookup"><span data-stu-id="4cbb1-269">`[wmiclass]`: `System.Management.ManagementClass`</span></span>
- <span data-ttu-id="4cbb1-270">`[wmisearcher]`: `System.Management.ManagementObjectSearcher`</span><span class="sxs-lookup"><span data-stu-id="4cbb1-270">`[wmisearcher]`: `System.Management.ManagementObjectSearcher`</span></span>

<span data-ttu-id="4cbb1-271">Dessa typ acceleratorer inkluderades inte i PowerShell 6, men har lagts till i PowerShell 6,1 som körs i Windows.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-271">These type accelerators were not included in PowerShell 6, but have been added to PowerShell 6.1 running on Windows.</span></span>

<span data-ttu-id="4cbb1-272">De här typerna är användbara för att enkelt konstruera AD-och WMI-objekt.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-272">These types are useful in easily constructing AD and WMI objects.</span></span>

<span data-ttu-id="4cbb1-273">Du kan till exempel fråga med LDAP:</span><span class="sxs-lookup"><span data-stu-id="4cbb1-273">For example, you can query using LDAP:</span></span>

```powershell
[adsi]'LDAP://CN=FooUse,OU=People,DC=contoso,DC=com'
```

<span data-ttu-id="4cbb1-274">I följande exempel skapas ett Win32_OperatingSystem CIM-objekt:</span><span class="sxs-lookup"><span data-stu-id="4cbb1-274">Following example creates a Win32_OperatingSystem CIM object:</span></span>

```powershell
[wmi]"Win32_OperatingSystem=@"
```

```Output
SystemDirectory : C:\WINDOWS\system32
Organization    : Contoso IT
BuildNumber     : 18234
RegisteredUser  : Contoso Corp.
SerialNumber    : 12345-67890-ABCDE-F0123
Version         : 10.0.18234
```

<span data-ttu-id="4cbb1-275">Det här exemplet returnerar ett ManagementClass-objekt för Win32_OperatingSystem-klassen.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-275">This example returns a ManagementClass object for Win32_OperatingSystem class.</span></span>

```powershell
[wmiclass]"Win32_OperatingSystem"
```

```Output
   NameSpace: ROOT\cimv2

Name                                Methods              Properties
----                                -------              ----------
Win32_OperatingSystem               {Reboot, Shutdown... {BootDevice, BuildNumber, BuildType, Caption...}
```

### <a name="-lp-alias-for-all--literalpath-parameters"></a><span data-ttu-id="4cbb1-276">`-lp` alias för alla `-LiteralPath` parametrar</span><span class="sxs-lookup"><span data-stu-id="4cbb1-276">`-lp` alias for all `-LiteralPath` parameters</span></span>

<span data-ttu-id="4cbb1-277">[@kvprasoon](https://github.com/kvprasoon)Vi har nu ett parameter Ali Aset `-lp` för alla inbyggda PowerShell-cmdletar som har en `-LiteralPath` parameter.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-277">Thanks to [@kvprasoon](https://github.com/kvprasoon), we now have a parameter alias `-lp` for all the built-in PowerShell cmdlets that have a `-LiteralPath` parameter.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="4cbb1-278">Icke-bakåtkompatibla ändringar</span><span class="sxs-lookup"><span data-stu-id="4cbb1-278">Breaking Changes</span></span>

### <a name="msi-based-installation-paths-on-windows"></a><span data-ttu-id="4cbb1-279">MSI-baserade installations Sök vägar i Windows</span><span class="sxs-lookup"><span data-stu-id="4cbb1-279">MSI-based installation paths on Windows</span></span>

<span data-ttu-id="4cbb1-280">I Windows installeras nu MSI-paketet på följande sökväg:</span><span class="sxs-lookup"><span data-stu-id="4cbb1-280">On Windows, the MSI package now installs to the following path:</span></span>

- <span data-ttu-id="4cbb1-281">`$env:ProgramFiles\PowerShell\6\` för en stabil installation av 6. x</span><span class="sxs-lookup"><span data-stu-id="4cbb1-281">`$env:ProgramFiles\PowerShell\6\` for the stable installation of 6.x</span></span>
- <span data-ttu-id="4cbb1-282">`$env:ProgramFiles\PowerShell\6-preview\` för för hands version av 6. x</span><span class="sxs-lookup"><span data-stu-id="4cbb1-282">`$env:ProgramFiles\PowerShell\6-preview\` for the preview installation of 6.x</span></span>

<span data-ttu-id="4cbb1-283">Den här ändringen ser till att PowerShell-kärnan kan uppdateras/servas av Microsoft Update.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-283">This change ensures that PowerShell Core can be updated/serviced by Microsoft Update.</span></span>

<span data-ttu-id="4cbb1-284">Mer information finns i PowerShell- [RFC0026](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0026-MSI-Installation-Path.md).</span><span class="sxs-lookup"><span data-stu-id="4cbb1-284">For more information, check out [PowerShell RFC0026](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0026-MSI-Installation-Path.md).</span></span>

### <a name="telemetry-can-only-be-disabled-with-an-environment-variable"></a><span data-ttu-id="4cbb1-285">Telemetri kan bara inaktive ras med en miljö variabel</span><span class="sxs-lookup"><span data-stu-id="4cbb1-285">Telemetry can only be disabled with an environment variable</span></span>

<span data-ttu-id="4cbb1-286">PowerShell-kärnan skickar grundläggande telemetridata till Microsoft när den startas.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-286">PowerShell Core sends basic telemetry data to Microsoft when it is launched.</span></span> <span data-ttu-id="4cbb1-287">Datan innehåller operativ systemets namn, OS-version och PowerShell-version.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-287">The data includes the OS name, OS version, and PowerShell version.</span></span> <span data-ttu-id="4cbb1-288">Med den här informationen kan vi bättre förstå de miljöer där PowerShell används och göra det möjligt för oss att prioritera nya funktioner och korrigeringar.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-288">This data allows us to better understand the environments where PowerShell is used and enables us to prioritize new features and fixes.</span></span>

<span data-ttu-id="4cbb1-289">Om du vill inaktivera den här Telemetrin ställer du in miljövariabeln `POWERSHELL_TELEMETRY_OPTOUT` på `true` , `yes` eller `1` .</span><span class="sxs-lookup"><span data-stu-id="4cbb1-289">To opt-out of this telemetry, set the environment variable `POWERSHELL_TELEMETRY_OPTOUT` to `true`, `yes`, or `1`.</span></span> <span data-ttu-id="4cbb1-290">Vi stöder inte längre borttagning av filen `DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` för att inaktivera telemetri.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-290">We no longer support deletion of the file `DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` to disable telemetry.</span></span>

### <a name="disallowed-basic-auth-over-http-in-powershell-remoting-on-unix-platforms"></a><span data-ttu-id="4cbb1-291">Otillåten grundläggande autentisering över HTTP i PowerShell-fjärrkommunikation på UNIX-plattformar</span><span class="sxs-lookup"><span data-stu-id="4cbb1-291">Disallowed Basic Auth over HTTP in PowerShell Remoting on Unix platforms</span></span>

<span data-ttu-id="4cbb1-292">För att förhindra användning av okrypterad trafik, kräver PowerShell-fjärrkommunikation på UNIX-plattformar att NTLM/Negotiate eller HTTPS används nu.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-292">To prevent the use of unencrypted traffic, PowerShell Remoting on Unix platforms now requires usage of NTLM/Negotiate or HTTPS.</span></span>

<span data-ttu-id="4cbb1-293">Mer information om dessa ändringar finns i [problem #6779](https://github.com/PowerShell/PowerShell/issues/6779).</span><span class="sxs-lookup"><span data-stu-id="4cbb1-293">For more information on these changes, check out [Issue #6779](https://github.com/PowerShell/PowerShell/issues/6779).</span></span>

### <a name="removed-visualbasic-as-a-supported-language-in-add-type"></a><span data-ttu-id="4cbb1-294">Borttaget `VisualBasic` som ett språk som stöds i Add-Type</span><span class="sxs-lookup"><span data-stu-id="4cbb1-294">Removed `VisualBasic` as a supported language in Add-Type</span></span>

<span data-ttu-id="4cbb1-295">Tidigare kunde du kompilera Visual Basic kod med hjälp av `Add-Type` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-295">In the past, you could compile Visual Basic code using the `Add-Type` cmdlet.</span></span> <span data-ttu-id="4cbb1-296">Visual Basic användes sällan med `Add-Type` .</span><span class="sxs-lookup"><span data-stu-id="4cbb1-296">Visual Basic was rarely used with `Add-Type`.</span></span> <span data-ttu-id="4cbb1-297">Vi har tagit bort den här funktionen för att minska storleken på PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-297">We removed this feature to reduce the size of PowerShell.</span></span>

### <a name="cleaned-up-uses-of-commandtypesworkflow-and-workflowinfocleaned"></a><span data-ttu-id="4cbb1-298">Rensade användning av `CommandTypes.Workflow` och `WorkflowInfoCleaned`</span><span class="sxs-lookup"><span data-stu-id="4cbb1-298">Cleaned up uses of `CommandTypes.Workflow` and `WorkflowInfoCleaned`</span></span>

<span data-ttu-id="4cbb1-299">Mer information om dessa ändringar finns i [PR #6708](https://github.com/PowerShell/PowerShell/pull/6708).</span><span class="sxs-lookup"><span data-stu-id="4cbb1-299">For more information on these changes, check out [PR #6708](https://github.com/PowerShell/PowerShell/pull/6708).</span></span>

### <a name="group-object-now-sorts-the-groups"></a><span data-ttu-id="4cbb1-300">Nu sorterar Group-Object grupperna</span><span class="sxs-lookup"><span data-stu-id="4cbb1-300">Group-Object now sorts the groups</span></span>

<span data-ttu-id="4cbb1-301">Som en del av prestanda förbättringen `Group-Object` returnerar nu en sorterad lista över grupperna.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-301">As part of the performance improvement, `Group-Object` now returns a sorted listing of the groups.</span></span>
<span data-ttu-id="4cbb1-302">Även om du inte bör förlita dig på ordern, kan du bryta den här ändringen om du ville ha den första gruppen.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-302">Although you should not rely on the order, you could be broken by this change if you wanted the first group.</span></span> <span data-ttu-id="4cbb1-303">Vi beslutade att den här prestanda förbättringen var värt förändringen eftersom effekten av att vara beroende av tidigare beteende är låg.</span><span class="sxs-lookup"><span data-stu-id="4cbb1-303">We decided that this performance improvement was worth the change since the impact of being dependent on previous behavior is low.</span></span>

<span data-ttu-id="4cbb1-304">Mer information om den här ändringen finns i [problem #7409](https://github.com/PowerShell/PowerShell/issues/7409).</span><span class="sxs-lookup"><span data-stu-id="4cbb1-304">For more information on this change, see [Issue #7409](https://github.com/PowerShell/PowerShell/issues/7409).</span></span>

<!-- URL references -->
[Experimentella funktioner]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
[Experimental Features]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
