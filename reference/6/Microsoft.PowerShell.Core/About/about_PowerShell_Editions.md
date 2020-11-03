---
description: Olika versioner av PowerShell körs på olika underliggande körningar.
Locale: en-US
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_powershell_editions?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PowerShell_Editions
ms.openlocfilehash: 4649c1b47a69423eb2f11a119583f441191882dd
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270555"
---
# <a name="about-powershell-editions"></a><span data-ttu-id="7ae83-103">Om PowerShell-versioner</span><span class="sxs-lookup"><span data-stu-id="7ae83-103">About PowerShell Editions</span></span>

## <a name="short-description"></a><span data-ttu-id="7ae83-104">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="7ae83-104">Short Description</span></span>
<span data-ttu-id="7ae83-105">Olika versioner av PowerShell körs på olika underliggande körningar.</span><span class="sxs-lookup"><span data-stu-id="7ae83-105">Different editions of PowerShell run on different underlying runtimes.</span></span>

## <a name="long-description"></a><span data-ttu-id="7ae83-106">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="7ae83-106">Long Description</span></span>

<span data-ttu-id="7ae83-107">Från PowerShell 5,1 finns det flera _utgåvor_ av PowerShell som körs på en annan .net-körning.</span><span class="sxs-lookup"><span data-stu-id="7ae83-107">From PowerShell 5.1, there are multiple _editions_ of PowerShell that each run on a different .NET runtime.</span></span> <span data-ttu-id="7ae83-108">Från och med PowerShell 6,2 finns två versioner av PowerShell:</span><span class="sxs-lookup"><span data-stu-id="7ae83-108">As of PowerShell 6.2 there are two editions of PowerShell:</span></span>

- <span data-ttu-id="7ae83-109">**Desktop** , som körs på .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7ae83-109">**Desktop** , which runs on .NET Framework.</span></span> <span data-ttu-id="7ae83-110">PowerShell 4 och lägre, samt PowerShell 5,1 på Windows-versioner med full funktionalitet som Windows Desktop, Windows Server, Windows Server Core och de flesta andra Windows-operativsystem är Desktop Edition.</span><span class="sxs-lookup"><span data-stu-id="7ae83-110">PowerShell 4 and below, as well as PowerShell 5.1 on full-featured Windows editions like Windows Desktop, Windows Server, Windows Server Core and most other Windows operating systems are Desktop edition.</span></span> <span data-ttu-id="7ae83-111">Det här är den ursprungliga PowerShell-versionen.</span><span class="sxs-lookup"><span data-stu-id="7ae83-111">This is the original PowerShell edition.</span></span>
- <span data-ttu-id="7ae83-112">**Core** , som körs på .net Core.</span><span class="sxs-lookup"><span data-stu-id="7ae83-112">**Core** , which runs on .NET Core.</span></span> <span data-ttu-id="7ae83-113">PowerShell 6,0 och senare, samt PowerShell 5,1 på vissa Windows-versioner med lägre storlek, till exempel Windows Nano Server och Windows IoT där .NET Framework inte är tillgängligt.</span><span class="sxs-lookup"><span data-stu-id="7ae83-113">PowerShell 6.0 and above, as well as PowerShell 5.1 on some reduced-footprint Windows editions such as Windows Nano Server and Windows IoT where .NET Framework is unavailable.</span></span>

<span data-ttu-id="7ae83-114">Eftersom versionen av PowerShell motsvarar .NET-körningen är det den primära indikatorn för kompatibilitet med .NET API och PowerShell-modul. vissa .NET-API: er, typer eller metoder är inte tillgängliga i både .NET-körningar och detta påverkar PowerShell-skript och moduler som är beroende av dem.</span><span class="sxs-lookup"><span data-stu-id="7ae83-114">Because the edition of PowerShell corresponds to its .NET runtime, it is the primary indicator of .NET API and PowerShell module compatibility; some .NET APIs, types or methods are not available in both .NET runtimes and this affects PowerShell scripts and modules that depend on them.</span></span>

## <a name="the-psedition-automatic-variable"></a><span data-ttu-id="7ae83-115">Den `$PSEdition` automatiska variabeln</span><span class="sxs-lookup"><span data-stu-id="7ae83-115">The `$PSEdition` automatic variable</span></span>

<span data-ttu-id="7ae83-116">I PowerShell 5,1 och senare kan du ta reda på vilken version som körs med den `$PSEdition` automatiska variabeln:</span><span class="sxs-lookup"><span data-stu-id="7ae83-116">In PowerShell 5.1 and above, you can find out what edition you are running with the `$PSEdition` automatic variable:</span></span>

```powershell
$PSEdition
```

```Output
Core
```

<span data-ttu-id="7ae83-117">Den här variabeln finns inte i PowerShell 4 och lägre.</span><span class="sxs-lookup"><span data-stu-id="7ae83-117">In PowerShell 4 and below, this variable does not exist.</span></span> <span data-ttu-id="7ae83-118">`$PSEdition` null ska behandlas som det samma som värdet `Desktop` .</span><span class="sxs-lookup"><span data-stu-id="7ae83-118">`$PSEdition` being null should be treated as the same as having the value `Desktop`.</span></span>

### <a name="edition-in-psversiontable"></a><span data-ttu-id="7ae83-119">Utgåva i `$PSVersionTable`</span><span class="sxs-lookup"><span data-stu-id="7ae83-119">Edition in `$PSVersionTable`</span></span>

<span data-ttu-id="7ae83-120">Den `$PSVersionTable` automatiska variabeln har även versions information i PowerShell 5,1 och senare:</span><span class="sxs-lookup"><span data-stu-id="7ae83-120">The `$PSVersionTable` automatic variable also has edition information in PowerShell 5.1 and above:</span></span>

```powershell
$PSVersionTable
```

```Output
Name                           Value
----                           -----
PSVersion                      6.2.0-rc.1
PSEdition                      Core           # <-- Edition information
GitCommitId                    6.2.0-rc.1
OS                             Microsoft Windows 10.0.18865
Platform                       Win32NT
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
WSManStackVersion              3.0
```

<span data-ttu-id="7ae83-121">`PSEdition`Fältet får samma värde som den `$PSEdition` automatiska variabeln.</span><span class="sxs-lookup"><span data-stu-id="7ae83-121">The `PSEdition` field will have the same value as the `$PSEdition` automatic variable.</span></span>

## <a name="the-compatiblepseditions-module-manifest-field"></a><span data-ttu-id="7ae83-122">`CompatiblePSEditions`Modulens manifest fält</span><span class="sxs-lookup"><span data-stu-id="7ae83-122">The `CompatiblePSEditions` module manifest field</span></span>

<span data-ttu-id="7ae83-123">PowerShell-moduler kan deklarera vilka utgåvor av PowerShell de är kompatibla med med hjälp av `CompatiblePSEditions` fältet i modul manifestet.</span><span class="sxs-lookup"><span data-stu-id="7ae83-123">PowerShell modules can declare what editions of PowerShell they are compatible with using the `CompatiblePSEditions` field of the module manifest.</span></span>

<span data-ttu-id="7ae83-124">Till exempel är ett modul manifest som deklarerar kompatibilitet med både `Desktop` och `Core` utgåvor av PowerShell:</span><span class="sxs-lookup"><span data-stu-id="7ae83-124">For example, a module manifest declaring compatibility with both `Desktop` and `Core` editions of PowerShell:</span></span>

```powershell
@{
    ModuleVersion = '1.0'
    FunctionsToExport = @('Test-MyModule')
    CompatiblePSEditions = @('Desktop', 'Core')
}
```

<span data-ttu-id="7ae83-125">Ett exempel på en modul manifest med endast `Desktop` kompatibilitet:</span><span class="sxs-lookup"><span data-stu-id="7ae83-125">An example of a module manifest with only `Desktop` compatibility:</span></span>

```powershell
@{
    ModuleVersion = '1.0'
    FunctionsToExport = @('Test-MyModule')
    CompatiblePSEditions = @('Desktop')
}
```

<span data-ttu-id="7ae83-126">Om du utelämnar `CompatiblePSEditions` fältet från ett modul-manifest får du samma resultat som att ställa in det på `Desktop` , eftersom moduler som skapats innan det här fältet introducerades implicit för den här utgåvan.</span><span class="sxs-lookup"><span data-stu-id="7ae83-126">Omitting the `CompatiblePSEditions` field from a module manifest will have the same effect as setting it to `Desktop`, since modules created before this field was introduced were implicitly written for this edition.</span></span>

<span data-ttu-id="7ae83-127">För moduler som inte levereras som en del av Windows (d.v.s. moduler som du skriver eller installerar från galleriet), är det här fältet endast information. PowerShell ändrar inte beteendet baserat på `CompatiblePSEditions` fältet, men visar det på `PSModuleInfo` objektet (returneras av `Get-Module` ) för din egen logik:</span><span class="sxs-lookup"><span data-stu-id="7ae83-127">For modules not shipped as part of Windows (i.e. modules you write or install from the gallery), this field is informational only; PowerShell does not change behavior based on the `CompatiblePSEditions` field, but does expose it on the `PSModuleInfo` object (returned by `Get-Module`) for your own logic:</span></span>

```powershell
New-ModuleManifest -Path .\TestModuleWithEdition.psd1 -CompatiblePSEditions Desktop,Core -PowerShellVersion '5.1'
$ModuleInfo = Test-ModuleManifest -Path .\TestModuleWithEdition.psd1
$ModuleInfo.CompatiblePSEditions
```

```Output
Desktop
Core
```

> [!NOTE]
> <span data-ttu-id="7ae83-128">Fältet `CompatiblePSEditions` modul är bara kompatibelt med PowerShell 5,1 och senare.</span><span class="sxs-lookup"><span data-stu-id="7ae83-128">The `CompatiblePSEditions` module field is only compatible with PowerShell 5.1 and above.</span></span> <span data-ttu-id="7ae83-129">Om du inkluderar det här fältet kommer en modul vara inkompatibel med PowerShell 4 och lägre.</span><span class="sxs-lookup"><span data-stu-id="7ae83-129">Including this field will cause a module to be incompatible with PowerShell 4 and below.</span></span> <span data-ttu-id="7ae83-130">Eftersom fältet är rent information kan det vara säkert utelämnat i senare PowerShell-versioner.</span><span class="sxs-lookup"><span data-stu-id="7ae83-130">Since the field is purely informational, it can be safely omitted in later PowerShell versions.</span></span>

<span data-ttu-id="7ae83-131">I PowerShell 6,1 `Get-Module -ListAvailable` har formateringen uppdaterats för att Visa utgåva-kompatibiliteten för varje modul:</span><span class="sxs-lookup"><span data-stu-id="7ae83-131">In PowerShell 6.1, `Get-Module -ListAvailable` has had its formatter updated to display the edition-compatibility of each module:</span></span>

```PowerShell
Get-Module -ListAvailable
```

```Output

    Directory: C:\Users\me\Documents\PowerShell\Modules

ModuleType Version    Name                   PSEdition ExportedCommands
---------- -------    ----                   --------- ----------------
Script     1.4.0      Az                     Core,Desk
Script     1.3.1      Az.Accounts            Core,Desk {Disable-AzDataCollection, Disable-AzContextAutosave, E...
Script     1.0.1      Az.Aks                 Core,Desk {Get-AzAks, New-AzAks, Remove-AzAks, Import-AzAksCreden...

...

Script     4.4.0      Pester                 Desk      {Describe, Context, It, Should...}
Script     1.18.0     PSScriptAnalyzer       Desk      {Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer, Invoke-...
Script     1.0.0      WindowsCompatibility   Core      {Initialize-WinSession, Add-WinFunction, Invoke-WinComm...

```

## <a name="edition-compatibility-for-modules-that-ship-as-part-of-windows"></a><span data-ttu-id="7ae83-132">Edition-kompatibilitet för moduler som levereras som en del av Windows</span><span class="sxs-lookup"><span data-stu-id="7ae83-132">Edition-compatibility for modules that ship as part of Windows</span></span>

<span data-ttu-id="7ae83-133">För moduler som ingår som en del av Windows (eller som installeras som en del av en roll eller funktion) behandlar PowerShell 6,1 och ovan `CompatiblePSEditions` fältet på olika sätt.</span><span class="sxs-lookup"><span data-stu-id="7ae83-133">For modules that come as part of Windows (or are installed as part of a role or feature), PowerShell 6.1 and above treat the `CompatiblePSEditions` field differently.</span></span> <span data-ttu-id="7ae83-134">Sådana moduler finns i Windows PowerShell-katalogen system modules ( `%windir%\System\WindowsPowerShell\v1.0\Modules` ).</span><span class="sxs-lookup"><span data-stu-id="7ae83-134">Such modules are found in the Windows PowerShell system modules directory (`%windir%\System\WindowsPowerShell\v1.0\Modules`).</span></span>

<span data-ttu-id="7ae83-135">För moduler som läses in från eller hittas i den här katalogen använder PowerShell 6,1 och senare `CompatiblePSEditions` fältet för att avgöra om modulen kommer att vara kompatibel med den aktuella sessionen och beter sig enligt detta.</span><span class="sxs-lookup"><span data-stu-id="7ae83-135">For modules loaded from or found in this directory, PowerShell 6.1 and above uses the `CompatiblePSEditions` field to determine whether the module will be compatible with the current session and behaves accordingly.</span></span>

<span data-ttu-id="7ae83-136">När används `Import-Module` , importeras inte en modul utan `Core` i `CompatiblePSEditions` och ett fel meddelande visas:</span><span class="sxs-lookup"><span data-stu-id="7ae83-136">When `Import-Module` is used, a module without `Core` in `CompatiblePSEditions` will not be imported and an error will be displayed:</span></span>

```powershell
Import-Module BitsTransfer
```

```Output
Import-Module : Module 'C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\BitsT
ransfer\BitsTransfer.psd1' does not support current PowerShell edition 'Core'.
Its supported editions are 'Desktop'. Use 'Import-Module -SkipEditionCheck' to i
gnore the compatibility of this module.
At line:1 char:1
+ Import-Module BitsTransfer
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : ResourceUnavailable: (C:\WINDOWS\system32\u2026r\BitsT
ransfer.psd1:String) [Import-Module], InvalidOperationException
+ FullyQualifiedErrorId : Modules_PSEditionNotSupported,Microsoft.PowerShell.Com
mands.ImportModuleCommand
```

<span data-ttu-id="7ae83-137">När används visas `Get-Module -ListAvailable` inte moduler utan `Core` i `CompatiblePSEditions` :</span><span class="sxs-lookup"><span data-stu-id="7ae83-137">When `Get-Module -ListAvailable` is used, modules without `Core` in `CompatiblePSEditions` will not be displayed:</span></span>

```powershell
Get-Module -ListAvailable BitsTransfer
```

```Output
# No output
```

<span data-ttu-id="7ae83-138">I båda fallen `-SkipEditionCheck` kan switch-parametern användas för att åsidosätta detta beteende:</span><span class="sxs-lookup"><span data-stu-id="7ae83-138">In both cases, the `-SkipEditionCheck` switch parameter can be used to override this behavior:</span></span>

```powershell
Get-Module -ListAvailable -SkipEditionCheck BitsTransfer
```

```Output
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name             PSEdition ExportedCommands
---------- -------    ----             --------- ----------------
Manifest   2.0.0.0    BitsTransfer     Desk      {Add-BitsFile, Complete-BitsTransfer, Get-BitsTransfer,...
```

> [!WARNING]
> <span data-ttu-id="7ae83-139">`Import-Module -SkipEditionCheck` kan verka som om en modul har körts, men med den modulen körs risken att en inkompatibilitet påträffas senare. När modulen lästes in initialt slutförs, kan ett kommando senare anropa ett inkompatibelt API och Miss lyckas spontant.</span><span class="sxs-lookup"><span data-stu-id="7ae83-139">`Import-Module -SkipEditionCheck` may appear to succeed for a module, but using that module runs the risk of encountering an incompatibility later on; while loading the module initially succeeds, a command may later call an incompatible API and fail spontaneously.</span></span>

## <a name="authoring-powershell-modules-for-edition-cross-compatibility"></a><span data-ttu-id="7ae83-140">Redigera PowerShell-moduler för kompatibilitet mellan versioner</span><span class="sxs-lookup"><span data-stu-id="7ae83-140">Authoring PowerShell modules for edition cross-compatibility</span></span>

<span data-ttu-id="7ae83-141">När du skriver en PowerShell-modul för att nå både `Desktop` och `Core` utgåvor av PowerShell finns det saker du kan göra för att säkerställa kompatibilitet mellan utgåvor.</span><span class="sxs-lookup"><span data-stu-id="7ae83-141">When writing a PowerShell module to target both `Desktop` and `Core` editions of PowerShell, there are things you can do to ensure cross-edition compatibility.</span></span>

<span data-ttu-id="7ae83-142">Det enda sanna sättet att bekräfta och validera kompatibilitet är dock att skriva tester för ditt skript eller din modul och köra dem på alla versioner och utgåvor av PowerShell som du behöver kompatibla med.</span><span class="sxs-lookup"><span data-stu-id="7ae83-142">The only true way to confirm and continually validate compatibility however is to write tests for your script or module and run them on all versions and editions of PowerShell you need compatibility with.</span></span> <span data-ttu-id="7ae83-143">Ett rekommenderat test ramverk för detta är [pester][].</span><span class="sxs-lookup"><span data-stu-id="7ae83-143">A recommended testing framework for this is [Pester][].</span></span>

### <a name="powershell-script"></a><span data-ttu-id="7ae83-144">PowerShell-skript</span><span class="sxs-lookup"><span data-stu-id="7ae83-144">PowerShell script</span></span>

<span data-ttu-id="7ae83-145">Som språk fungerar PowerShell likadant mellan versioner. Det är de cmdlets, moduler och .NET-API: er som du använder som påverkas av versionens kompatibilitet.</span><span class="sxs-lookup"><span data-stu-id="7ae83-145">As a language, PowerShell works the same between editions; it is the cmdlets, modules and .NET APIs you use that are affected by edition compatibility.</span></span>

<span data-ttu-id="7ae83-146">Vanligt vis fungerar skript som fungerar i PowerShell 6,1 och senare med Windows PowerShell 5,1, men det finns vissa undantag.</span><span class="sxs-lookup"><span data-stu-id="7ae83-146">Generally, scripts that work in PowerShell 6.1 and above will work with Windows PowerShell 5.1, but there are some exceptions.</span></span>

<span data-ttu-id="7ae83-147">Version 1.18.0 [PSScriptAnalyzer][] -modulen har regler som [PSUseCompatibleCommands][] och [PSUseCompatibleTypes][] som kan identifiera eventuellt inkompatibel användning av kommandon och .NET API: er i PowerShell-skript.</span><span class="sxs-lookup"><span data-stu-id="7ae83-147">Version 1.18.0 [PSScriptAnalyzer][] module has rules like [PSUseCompatibleCommands][] and [PSUseCompatibleTypes][] that are able to detect possibly incompatible usage of commands and .NET APIs in PowerShell scripts.</span></span>

### <a name="net-assemblies"></a><span data-ttu-id="7ae83-148">.NET-sammansättningar</span><span class="sxs-lookup"><span data-stu-id="7ae83-148">.NET assemblies</span></span>

<span data-ttu-id="7ae83-149">Om du skriver en binär modul eller en modul som införlivar .NET-sammansättningar (dll) som genereras från käll koden, bör du kompilera mot [.net standard][] och [PowerShell standard][] för autentisering vid kompilering av .net-och PowerShell API-kompatibilitet.</span><span class="sxs-lookup"><span data-stu-id="7ae83-149">If you are writing a binary module or a module that incorporates .NET assemblies (DLLs) generated from source code, you should compile against [.NET Standard][] and [PowerShell Standard][] for compile-time compatibility validation of .NET and PowerShell API compatibility.</span></span>

<span data-ttu-id="7ae83-150">Även om dessa bibliotek kan kontrol lera kompatibilitet vid kompilering, kan de inte fånga upp möjliga beteende skillnader mellan olika versioner.</span><span class="sxs-lookup"><span data-stu-id="7ae83-150">Although these libraries are able to check some compatibility at compile time, they won't be able to catch possible behavioral differences between editions.</span></span>
<span data-ttu-id="7ae83-151">För detta måste du fortfarande skriva tester.</span><span class="sxs-lookup"><span data-stu-id="7ae83-151">For this you must still write tests.</span></span>

## <a name="see-also"></a><span data-ttu-id="7ae83-152">Se även</span><span class="sxs-lookup"><span data-stu-id="7ae83-152">See also</span></span>

- [<span data-ttu-id="7ae83-153">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="7ae83-153">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)
- [<span data-ttu-id="7ae83-154">Importera-modul</span><span class="sxs-lookup"><span data-stu-id="7ae83-154">Import-Module</span></span>](xref:Microsoft.PowerShell.Core.Import-Module)
- [<span data-ttu-id="7ae83-155">Hämta modul</span><span class="sxs-lookup"><span data-stu-id="7ae83-155">Get-Module</span></span>](xref:Microsoft.PowerShell.Core.Get-Module)
- [<span data-ttu-id="7ae83-156">Moduler med kompatibla PowerShell-versioner</span><span class="sxs-lookup"><span data-stu-id="7ae83-156">Modules with compatible PowerShell Editions</span></span>](/powershell/scripting/gallery/concepts/module-psedition-support)

[Pester]: https://github.com/pester/Pester/wiki/Pester
[PSScriptAnalyzer]: https://github.com/PowerShell/PSScriptAnalyzer
[PSUseCompatibleCommands]: https://github.com/PowerShell/PSScriptAnalyzer/blob/master/RuleDocumentation/UseCompatibleCommands.md
[PSUseCompatibleTypes]: https://github.com/PowerShell/PSScriptAnalyzer/blob/master/RuleDocumentation/UseCompatibleTypes.md
[.NET Standard]: /dotnet/standard/net-standard
[PowerShell-standard]: https://devblogs.microsoft.com/powershell/powershell-standard-library-build-single-module-that-works-across-windows-powershell-and-powershell-core/
[PowerShell Standard]: https://devblogs.microsoft.com/powershell/powershell-standard-library-build-single-module-that-works-across-windows-powershell-and-powershell-core/
