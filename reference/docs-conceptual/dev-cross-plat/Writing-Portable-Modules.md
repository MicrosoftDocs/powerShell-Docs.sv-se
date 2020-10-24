---
ms.date: 10/21/2020
keywords: powershell,cmdlet
title: Skriva portabla moduler
description: Den här artikeln förklarar hur du skapar moduler nya moduler eller uppdaterar befintliga moduler så att de fungerar på de plattformar som stöds av PowerShell.
ms.openlocfilehash: 6d5c36263c3c6d1219f963cea2e94ae92b07e863
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500801"
---
# <a name="portable-modules"></a><span data-ttu-id="c3b30-104">Bärbara moduler</span><span class="sxs-lookup"><span data-stu-id="c3b30-104">Portable Modules</span></span>

<span data-ttu-id="c3b30-105">Windows PowerShell är skrivet för [.NET Framework][] medan PowerShell-kärnan skrivs för [.net Core][].</span><span class="sxs-lookup"><span data-stu-id="c3b30-105">Windows PowerShell is written for [.NET Framework][] while PowerShell Core is written for [.NET Core][].</span></span> <span data-ttu-id="c3b30-106">Bärbara moduler är moduler som fungerar både i Windows PowerShell och PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="c3b30-106">Portable modules are modules that work in both Windows PowerShell and PowerShell Core.</span></span> <span data-ttu-id="c3b30-107">Även om .NET Framework och .NET Core är mycket kompatibla finns det skillnader i de tillgängliga API: erna mellan de två.</span><span class="sxs-lookup"><span data-stu-id="c3b30-107">While .NET Framework and .NET Core are highly compatible, there are differences in the available APIs between the two.</span></span> <span data-ttu-id="c3b30-108">Det finns också skillnader i de API: er som är tillgängliga i Windows PowerShell och PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="c3b30-108">There are also differences in the APIs available in Windows PowerShell and PowerShell Core.</span></span> <span data-ttu-id="c3b30-109">Moduler som är avsedda att användas i båda miljöerna måste vara medvetna om dessa skillnader.</span><span class="sxs-lookup"><span data-stu-id="c3b30-109">Modules intended to be used in both environments need to be aware of these differences.</span></span>

## <a name="porting-an-existing-module"></a><span data-ttu-id="c3b30-110">Portning av en befintlig modul</span><span class="sxs-lookup"><span data-stu-id="c3b30-110">Porting an existing module</span></span>

### <a name="porting-a-pssnapin"></a><span data-ttu-id="c3b30-111">Porting a PSSnapIn</span><span class="sxs-lookup"><span data-stu-id="c3b30-111">Porting a PSSnapIn</span></span>

<span data-ttu-id="c3b30-112">PowerShell- [modulerna](/powershell/scripting/developer/cmdlet/modules-and-snap-ins) stöds inte i PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="c3b30-112">PowerShell [SnapIns](/powershell/scripting/developer/cmdlet/modules-and-snap-ins) aren't supported in PowerShell Core.</span></span> <span data-ttu-id="c3b30-113">Det är dock enkelt att konvertera en PSSnapIn till en PowerShell-modul.</span><span class="sxs-lookup"><span data-stu-id="c3b30-113">However, it's trivial to convert a PSSnapIn to a PowerShell module.</span></span> <span data-ttu-id="c3b30-114">Normalt är registrerings koden PSSnapIn i en enda källfil för en klass som härleds från [PSSnapIn][].</span><span class="sxs-lookup"><span data-stu-id="c3b30-114">Typically, the PSSnapIn registration code is in a single source file of a class that derives from [PSSnapIn][].</span></span> <span data-ttu-id="c3b30-115">Ta bort den här käll filen från versionen. det behövs inte längre.</span><span class="sxs-lookup"><span data-stu-id="c3b30-115">Remove this source file from the build; it's no longer needed.</span></span>

<span data-ttu-id="c3b30-116">Använd [New-ModuleManifest][] för att skapa ett nytt modul-manifest som ersätter behovet av registrerings koden för PSSnapIn.</span><span class="sxs-lookup"><span data-stu-id="c3b30-116">Use [New-ModuleManifest][] to create a new module manifest that replaces the need for the PSSnapIn registration code.</span></span> <span data-ttu-id="c3b30-117">Några av värdena från **PSSnapIn** (till exempel **Beskrivning**) kan återanvändas i manifestet för modulen.</span><span class="sxs-lookup"><span data-stu-id="c3b30-117">Some of the values from the **PSSnapIn** (such as **Description**) can be reused within the module manifest.</span></span>

<span data-ttu-id="c3b30-118">Egenskapen **RootModule** i modulen manifest ska anges till namnet på sammansättningen (dll) som implementerar cmdletarna.</span><span class="sxs-lookup"><span data-stu-id="c3b30-118">The **RootModule** property in the module manifest should be set to the name of the assembly (dll) implementing the cmdlets.</span></span>

### <a name="the-net-portability-analyzer-aka-apiport"></a><span data-ttu-id="c3b30-119">.NET-portbaserad analys för aka (APIPort)</span><span class="sxs-lookup"><span data-stu-id="c3b30-119">The .NET Portability Analyzer (aka APIPort)</span></span>

<span data-ttu-id="c3b30-120">Om du vill att moduler som är skrivna för Windows PowerShell ska fungera med PowerShell-kärnan börjar du med [.net-ports Analyzer][].</span><span class="sxs-lookup"><span data-stu-id="c3b30-120">To port modules written for Windows PowerShell to work with PowerShell Core, start with the [.NET Portability Analyzer][].</span></span> <span data-ttu-id="c3b30-121">Kör det här verktyget mot den kompilerade sammansättningen för att avgöra om de .NET-API: er som används i modulen är kompatibla med .NET Framework, .NET Core och andra .NET-körningar.</span><span class="sxs-lookup"><span data-stu-id="c3b30-121">Run this tool against your compiled assembly to determine if the .NET APIs used in the module are compatible with .NET Framework, .NET Core, and other .NET runtimes.</span></span> <span data-ttu-id="c3b30-122">Verktyget föreslår alternativa API: er om de finns.</span><span class="sxs-lookup"><span data-stu-id="c3b30-122">The tool suggests alternate APIs if they exist.</span></span> <span data-ttu-id="c3b30-123">Annars kan du behöva lägga till [körnings kontroller][] och begränsa funktioner som inte är tillgängliga i vissa körningar.</span><span class="sxs-lookup"><span data-stu-id="c3b30-123">Otherwise, you may need to add [runtime checks][] and restrict capabilities not available in specific runtimes.</span></span>

## <a name="creating-a-new-module"></a><span data-ttu-id="c3b30-124">Skapa en ny modul</span><span class="sxs-lookup"><span data-stu-id="c3b30-124">Creating a new module</span></span>

<span data-ttu-id="c3b30-125">Om du skapar en ny modul är rekommendationen att använda [.net CLI][].</span><span class="sxs-lookup"><span data-stu-id="c3b30-125">If creating a new module, the recommendation is to use the [.NET CLI][].</span></span>

### <a name="installing-the-powershell-standard-module-template"></a><span data-ttu-id="c3b30-126">Installera PowerShell-modulen för standard mal len</span><span class="sxs-lookup"><span data-stu-id="c3b30-126">Installing the PowerShell Standard module template</span></span>

<span data-ttu-id="c3b30-127">När .NET CLI har installerats installerar du ett mall bibliotek för att generera en enkel PowerShell-modul.</span><span class="sxs-lookup"><span data-stu-id="c3b30-127">Once the .NET CLI is installed, install a template library to generate a simple PowerShell module.</span></span>
<span data-ttu-id="c3b30-128">Modulen är kompatibel med Windows PowerShell, PowerShell Core, Windows, Linux och macOS.</span><span class="sxs-lookup"><span data-stu-id="c3b30-128">The module will be compatible with Windows PowerShell, PowerShell Core, Windows, Linux, and macOS.</span></span>

<span data-ttu-id="c3b30-129">I följande exempel visas hur du installerar mallen:</span><span class="sxs-lookup"><span data-stu-id="c3b30-129">The following example shows how to install the template:</span></span>

```powershell
dotnet new -i Microsoft.PowerShell.Standard.Module.Template
```

```output
  Restoring packages for C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\restore.csproj...
  Installing Microsoft.PowerShell.Standard.Module.Template 0.1.3.
  Generating MSBuild file C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\obj\restore.csproj.nuget.g.props.
  Generating MSBuild file C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\obj\restore.csproj.nuget.g.targets.
  Restore completed in 1.66 sec for C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\restore.csproj.

Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.
  -n, --name          The name for the output being created. If no name is specified, the name of the current directory is used.
  -o, --output        Location to place the generated output.
  -i, --install       Installs a source or a template pack.
  -u, --uninstall     Uninstalls a source or a template pack.
  --nuget-source      Specifies a NuGet source to use during install.
  --type              Filters templates based on available types. Predefined values are "project", "item" or "other".
  --force             Forces content to be generated even if it would change existing files.
  -lang, --language   Filters templates based on language and specifies the language of the template to create.


Templates                        Short Name         Language          Tags
-----------------------------------------------------------------------------------------------
Console Application              console            [C#], F#, VB      Common/Console
Class library                    classlib           [C#], F#, VB      Common/Library
PowerShell Standard Module       psmodule           [C#]              Library/PowerShell/Module
...
```

### <a name="creating-a-new-module-project"></a><span data-ttu-id="c3b30-130">Skapa ett nytt modul-projekt</span><span class="sxs-lookup"><span data-stu-id="c3b30-130">Creating a new module project</span></span>

<span data-ttu-id="c3b30-131">När mallen har installerats kan du skapa ett nytt PowerShell-Modulnamn med den mallen.</span><span class="sxs-lookup"><span data-stu-id="c3b30-131">After the template is installed, you can create a new PowerShell module project using that template.</span></span> <span data-ttu-id="c3b30-132">I det här exemplet kallas exempel modulen "module".</span><span class="sxs-lookup"><span data-stu-id="c3b30-132">In this example, the sample module is called 'myModule'.</span></span>

```
PS> mkdir myModule

    Directory: C:\Users\Steve

Mode LastWriteTime Length Name
---- ------------- ------ ----
d----- 8/3/2018 2:41 PM myModule

PS> cd myModule
PS C:\Users\Steve\myModule> dotnet new psmodule

The template "PowerShell Standard Module" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on C:\Users\Steve\myModule\myModule.csproj...
  Restoring packages for C:\Users\Steve\myModule\myModule.csproj...
  Installing PowerShellStandard.Library 5.1.0.
  Generating MSBuild file C:\Users\Steve\myModule\obj\myModule.csproj.nuget.g.props.
  Generating MSBuild file C:\Users\Steve\myModule\obj\myModule.csproj.nuget.g.targets.
  Restore completed in 1.76 sec for C:\Users\Steve\myModule\myModule.csproj.

Restore succeeded.
```

### <a name="building-the-module"></a><span data-ttu-id="c3b30-133">Modulen skapas</span><span class="sxs-lookup"><span data-stu-id="c3b30-133">Building the module</span></span>

<span data-ttu-id="c3b30-134">Använd standard .NET CLI-kommandon för att bygga projektet.</span><span class="sxs-lookup"><span data-stu-id="c3b30-134">Use standard .NET CLI commands to build the project.</span></span>

```powershell
dotnet build
```

```output
PS C:\Users\Steve\myModule> dotnet build
Microsoft (R) Build Engine version 15.7.179.6572 for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 76.85 ms for C:\Users\Steve\myModule\myModule.csproj.
  myModule -> C:\Users\Steve\myModule\bin\Debug\netstandard2.0\myModule.dll

Build succeeded.
    0 Warning(s)
    0 Error(s)

Time Elapsed 00:00:05.40
```

### <a name="testing-the-module"></a><span data-ttu-id="c3b30-135">Testa modulen</span><span class="sxs-lookup"><span data-stu-id="c3b30-135">Testing the module</span></span>

<span data-ttu-id="c3b30-136">När du har skapat modulen kan du importera den och köra exempel-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c3b30-136">After building the module, you can import it and execute the sample cmdlet.</span></span>

```powershell
Import-Module .\bin\Debug\netstandard2.0\myModule.dll
Test-SampleCmdlet -?
Test-SampleCmdlet -FavoriteNumber 7 -FavoritePet Cat
```

```output
NAME
    Test-SampleCmdlet

SYNTAX
    Test-SampleCmdlet [-FavoriteNumber] <int> [[-FavoritePet] {Cat | Dog | Horse}] [<CommonParameters>]


ALIASES
    None


REMARKS
    None


FavoriteNumber FavoritePet
-------------- -----------
             7 Cat
```

### <a name="debugging-the-module"></a><span data-ttu-id="c3b30-137">Felsöka modulen</span><span class="sxs-lookup"><span data-stu-id="c3b30-137">Debugging the module</span></span>

<span data-ttu-id="c3b30-138">En guide om hur du konfigurerar Visual Studio Code för att felsöka modulen finns i [använda Visual Studio Code för fel sökning av kompilerade cmdlets][].</span><span class="sxs-lookup"><span data-stu-id="c3b30-138">For a guide on setting up Visual Studio Code to debug the module, see [Using Visual Studio Code for debugging compiled cmdlets][].</span></span>

## <a name="supporting-technologies"></a><span data-ttu-id="c3b30-139">Stöd tekniker</span><span class="sxs-lookup"><span data-stu-id="c3b30-139">Supporting technologies</span></span>

<span data-ttu-id="c3b30-140">I följande avsnitt beskrivs några av de tekniker som används av den här mallen.</span><span class="sxs-lookup"><span data-stu-id="c3b30-140">The following sections describe in detail some of the technologies used by this template.</span></span>

### <a name="net-standard-library"></a><span data-ttu-id="c3b30-141">.NET standard-bibliotek</span><span class="sxs-lookup"><span data-stu-id="c3b30-141">.NET Standard Library</span></span>

<span data-ttu-id="c3b30-142">[.Net standard][] är en formell specifikation av .NET-API: er som är tillgängliga i alla .net-implementeringar.</span><span class="sxs-lookup"><span data-stu-id="c3b30-142">[.NET Standard][] is a formal specification of .NET APIs that are available in all .NET implementations.</span></span> <span data-ttu-id="c3b30-143">Hanterad kod för .NET standard fungerar med de .NET Framework-och .NET Core-versioner som är kompatibla med den versionen av .NET standard.</span><span class="sxs-lookup"><span data-stu-id="c3b30-143">Managed code targeting .NET Standard works with the .NET Framework and .NET Core versions that are compatible with that version of the .NET Standard.</span></span>

> [!NOTE]
> <span data-ttu-id="c3b30-144">Även om ett API kan finnas i .NET standard kan API-implementeringen i .NET Core medföra en `PlatformNotSupportedException` vid körning, så för att kontrol lera kompatibilitet med Windows PowerShell och PowerShell Core är det bästa sättet att köra tester för modulen i båda miljöerna.</span><span class="sxs-lookup"><span data-stu-id="c3b30-144">Although an API may exist in .NET Standard, the API implementation in .NET Core may throw a `PlatformNotSupportedException` at runtime, so to verify compatibility with Windows PowerShell and PowerShell Core, the best practice is to run tests for your module within both environments.</span></span>
> <span data-ttu-id="c3b30-145">Kör även tester på Linux och macOS om modulen är avsedd att vara plattforms oberoende.</span><span class="sxs-lookup"><span data-stu-id="c3b30-145">Also run tests on Linux and macOS if your module is intended to be cross-platform.</span></span>

<span data-ttu-id="c3b30-146">Genom att använda .NET standard kan du se till att inkompatibla API: er inte har introducerats av misstag i modulen, eftersom modulen utvecklas.</span><span class="sxs-lookup"><span data-stu-id="c3b30-146">Targeting .NET Standard helps ensure that, as the module evolves, incompatible APIs don't accidentally get introduced into the module.</span></span> <span data-ttu-id="c3b30-147">Inkompatibiliteter upptäcks vid kompilering i stället för körning.</span><span class="sxs-lookup"><span data-stu-id="c3b30-147">Incompatibilities are discovered at compile time instead of runtime.</span></span>

<span data-ttu-id="c3b30-148">Men det är inte nödvändigt att använda .NET standard för att en modul ska fungera med både Windows PowerShell och PowerShell Core, så länge du använder kompatibla API: er.</span><span class="sxs-lookup"><span data-stu-id="c3b30-148">However, it isn't required to target .NET Standard for a module to work with both Windows PowerShell and PowerShell Core, as long as you use compatible APIs.</span></span> <span data-ttu-id="c3b30-149">Det mellanliggande språket (IL) är kompatibelt mellan de två körningarna.</span><span class="sxs-lookup"><span data-stu-id="c3b30-149">The Intermediate Language (IL) is compatible between the two runtimes.</span></span> <span data-ttu-id="c3b30-150">Du kan rikta .NET Framework 4.6.1, som är kompatibel med .NET standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="c3b30-150">You can target .NET Framework 4.6.1, which is compatible with .NET Standard 2.0.</span></span> <span data-ttu-id="c3b30-151">Om du inte använder API: er utanför .NET standard 2,0, fungerar modulen med PowerShell Core 6 utan att kompilera om.</span><span class="sxs-lookup"><span data-stu-id="c3b30-151">If you don't use APIs outside of .NET Standard 2.0, then your module works with PowerShell Core 6 without recompilation.</span></span>

### <a name="powershell-standard-library"></a><span data-ttu-id="c3b30-152">PowerShell-standardbibliotek</span><span class="sxs-lookup"><span data-stu-id="c3b30-152">PowerShell Standard Library</span></span>

<span data-ttu-id="c3b30-153">[PowerShell][] -standardbiblioteket är en formell specifikation av PowerShell-API: er som är tillgängliga i alla PowerShell-versioner som är större än eller lika med den standard versionen.</span><span class="sxs-lookup"><span data-stu-id="c3b30-153">The [PowerShell Standard][] library is a formal specification of PowerShell APIs available in all PowerShell versions greater than or equal to the version of that standard.</span></span>

<span data-ttu-id="c3b30-154">Till exempel är [PowerShell Standard 5,1][] kompatibelt med både Windows PowerShell 5,1 och PowerShell Core 6,0 eller senare.</span><span class="sxs-lookup"><span data-stu-id="c3b30-154">For example, [PowerShell Standard 5.1][] is compatible with both Windows PowerShell 5.1 and PowerShell Core 6.0 or newer.</span></span>

<span data-ttu-id="c3b30-155">Vi rekommenderar att du kompilerar modulen med PowerShell-standardbiblioteket.</span><span class="sxs-lookup"><span data-stu-id="c3b30-155">We recommend you compile your module using PowerShell Standard Library.</span></span> <span data-ttu-id="c3b30-156">Biblioteket säkerställer att API: erna är tillgängliga och implementerade i både Windows PowerShell och PowerShell Core 6.</span><span class="sxs-lookup"><span data-stu-id="c3b30-156">The library ensures the APIs are available and implemented in both Windows PowerShell and PowerShell Core 6.</span></span>
<span data-ttu-id="c3b30-157">PowerShell-standarden är avsedd att alltid vidarebefordras-kompatibel.</span><span class="sxs-lookup"><span data-stu-id="c3b30-157">PowerShell Standard is intended to always be forwards-compatible.</span></span> <span data-ttu-id="c3b30-158">En modul som skapats med PowerShell standard library 5,1 är alltid kompatibel med framtida versioner av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c3b30-158">A module built using PowerShell Standard Library 5.1 will always be compatible with future versions of PowerShell.</span></span>

### <a name="module-manifest"></a><span data-ttu-id="c3b30-159">Modul manifest</span><span class="sxs-lookup"><span data-stu-id="c3b30-159">Module Manifest</span></span>

#### <a name="indicating-compatibility-with-windows-powershell-and-powershell-core"></a><span data-ttu-id="c3b30-160">Indikerar kompatibilitet med Windows PowerShell och PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="c3b30-160">Indicating Compatibility With Windows PowerShell and PowerShell Core</span></span>

<span data-ttu-id="c3b30-161">När du har verifierat att modulen fungerar med både Windows PowerShell och PowerShell Core bör modulens manifest uttryckligen indikera kompatibilitet med hjälp av egenskapen [CompatiblePSEditions][] .</span><span class="sxs-lookup"><span data-stu-id="c3b30-161">After validating that your module works with both Windows PowerShell and PowerShell Core, the module manifest should explicitly indicate compatibility by using the [CompatiblePSEditions][] property.</span></span> <span data-ttu-id="c3b30-162">Värdet `Desktop` innebär att modulen är kompatibel med Windows PowerShell, medan värdet `Core` innebär att modulen är kompatibel med PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="c3b30-162">A value of `Desktop` means that the module is compatible with Windows PowerShell, while a value of `Core` means that the module is compatible with PowerShell Core.</span></span> <span data-ttu-id="c3b30-163">Inklusive både `Desktop` och `Core` innebär att modulen är kompatibel med både Windows PowerShell och PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="c3b30-163">Including both `Desktop` and `Core` means that the module is compatible with both Windows PowerShell and PowerShell Core.</span></span>

> [!NOTE]
> <span data-ttu-id="c3b30-164">`Core` innebär inte automatiskt att modulen är kompatibel med Windows, Linux och macOS.</span><span class="sxs-lookup"><span data-stu-id="c3b30-164">`Core` does not automatically mean that the module is compatible with Windows, Linux, and macOS.</span></span>
> <span data-ttu-id="c3b30-165">Egenskapen **CompatiblePSEditions** introducerades i PowerShell v5.</span><span class="sxs-lookup"><span data-stu-id="c3b30-165">The **CompatiblePSEditions** property was introduced in PowerShell v5.</span></span> <span data-ttu-id="c3b30-166">Modul manifest som använder egenskapen **CompatiblePSEditions** kan inte läsas in i tidigare versioner än PowerShell v5.</span><span class="sxs-lookup"><span data-stu-id="c3b30-166">Module manifests that use the **CompatiblePSEditions** property fail to load in versions prior to PowerShell v5.</span></span>

### <a name="indicating-os-compatibility"></a><span data-ttu-id="c3b30-167">Indikerar OS-kompatibilitet</span><span class="sxs-lookup"><span data-stu-id="c3b30-167">Indicating OS Compatibility</span></span>

<span data-ttu-id="c3b30-168">Kontrol lera först att modulen fungerar på Linux och macOS.</span><span class="sxs-lookup"><span data-stu-id="c3b30-168">First, validate that your module works on Linux and macOS.</span></span> <span data-ttu-id="c3b30-169">Sedan anger du kompatibiliteten med dessa operativ system i manifestet för modulen.</span><span class="sxs-lookup"><span data-stu-id="c3b30-169">Next, indicate compatibility with those operating systems in the module manifest.</span></span> <span data-ttu-id="c3b30-170">Detta gör det enklare för användarna att hitta modulen för sitt operativ system när de publiceras till [PowerShell-galleriet][].</span><span class="sxs-lookup"><span data-stu-id="c3b30-170">This makes it easier for users to find your module for their operating system when published to the [PowerShell Gallery][].</span></span>

<span data-ttu-id="c3b30-171">I modulen manifest `PrivateData` har egenskapen en `PSData` underordnad egenskap.</span><span class="sxs-lookup"><span data-stu-id="c3b30-171">Within the module manifest, the `PrivateData` property has a `PSData` sub-property.</span></span> <span data-ttu-id="c3b30-172">Den valfria `Tags` egenskapen för `PSData` tar en matris med värden som visas i PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="c3b30-172">The optional `Tags` property of `PSData` takes an array of values that show up in PowerShell Gallery.</span></span> <span data-ttu-id="c3b30-173">PowerShell-galleriet har stöd för följande kompatibilitetsinställningar:</span><span class="sxs-lookup"><span data-stu-id="c3b30-173">The PowerShell Gallery supports the following compatibility values:</span></span>

| <span data-ttu-id="c3b30-174">Tagg</span><span class="sxs-lookup"><span data-stu-id="c3b30-174">Tag</span></span>               | <span data-ttu-id="c3b30-175">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c3b30-175">Description</span></span>                                |
|-------------------|--------------------------------------------|
| <span data-ttu-id="c3b30-176">PSEdition_Core</span><span class="sxs-lookup"><span data-stu-id="c3b30-176">PSEdition_Core</span></span>    | <span data-ttu-id="c3b30-177">Kompatibel med PowerShell Core 6</span><span class="sxs-lookup"><span data-stu-id="c3b30-177">Compatible with PowerShell Core 6</span></span>          |
| <span data-ttu-id="c3b30-178">PSEdition_Desktop</span><span class="sxs-lookup"><span data-stu-id="c3b30-178">PSEdition_Desktop</span></span> | <span data-ttu-id="c3b30-179">Kompatibel med Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c3b30-179">Compatible with Windows PowerShell</span></span>         |
| <span data-ttu-id="c3b30-180">Windows</span><span class="sxs-lookup"><span data-stu-id="c3b30-180">Windows</span></span>           | <span data-ttu-id="c3b30-181">Kompatibel med Windows</span><span class="sxs-lookup"><span data-stu-id="c3b30-181">Compatible with Windows</span></span>                    |
| <span data-ttu-id="c3b30-182">Linux</span><span class="sxs-lookup"><span data-stu-id="c3b30-182">Linux</span></span>             | <span data-ttu-id="c3b30-183">Kompatibel med Linux (inga speciella distribution)</span><span class="sxs-lookup"><span data-stu-id="c3b30-183">Compatible with Linux (no specific distro)</span></span> |
| <span data-ttu-id="c3b30-184">macOS</span><span class="sxs-lookup"><span data-stu-id="c3b30-184">macOS</span></span>             | <span data-ttu-id="c3b30-185">Kompatibel med macOS</span><span class="sxs-lookup"><span data-stu-id="c3b30-185">Compatible with macOS</span></span>                      |

<span data-ttu-id="c3b30-186">Exempel:</span><span class="sxs-lookup"><span data-stu-id="c3b30-186">Example:</span></span>

```powershell
@{
    GUID = "4ae9fd46-338a-459c-8186-07f910774cb8"
    Author = "Microsoft Corporation"
    CompanyName = "Microsoft Corporation"
    Copyright = "(C) Microsoft Corporation. All rights reserved."
    HelpInfoUri = "https://go.microsoft.com/fwlink/?linkid=855962"
    ModuleVersion = "1.2.4"
    PowerShellVersion = "3.0"
    ClrVersion = "4.0"
    RootModule = "PackageManagement.psm1"
    Description = 'PackageManagement (a.k.a. OneGet) is a new way to discover and install software packages from around the web.
 It is a manager or multiplexer of existing package managers (also called package providers) that unifies Windows package management with a single Windows PowerShell interface. With PackageManagement, you can do the following.
  - Manage a list of software repositories in which packages can be searched, acquired and installed
  - Discover software packages
  - Seamlessly install, uninstall, and inventory packages from one or more software repositories'

    CmdletsToExport = @(
        'Find-Package',
        'Get-Package',
        'Get-PackageProvider',
        'Get-PackageSource',
        'Install-Package',
        'Import-PackageProvider'
        'Find-PackageProvider'
        'Install-PackageProvider'
        'Register-PackageSource',
        'Set-PackageSource',
        'Unregister-PackageSource',
        'Uninstall-Package'
        'Save-Package'
    )

    FormatsToProcess  = @('PackageManagement.format.ps1xml')

    PrivateData = @{
        PSData = @{
            Tags = @('PackageManagement', 'PSEdition_Core', 'PSEdition_Desktop', 'Windows', 'Linux', 'macOS')
            ProjectUri = 'https://oneget.org'
        }
    }
}
```

### <a name="dependency-on-native-libraries"></a><span data-ttu-id="c3b30-187">Beroende av interna bibliotek</span><span class="sxs-lookup"><span data-stu-id="c3b30-187">Dependency on Native Libraries</span></span>

<span data-ttu-id="c3b30-188">Moduler som ska användas i olika operativ system eller processor arkitekturer kan vara beroende av ett hanterat bibliotek som är beroende av vissa interna bibliotek.</span><span class="sxs-lookup"><span data-stu-id="c3b30-188">Modules intended for use across different operating systems or processor architectures may depend on a managed library that itself depends on some native libraries.</span></span>

<span data-ttu-id="c3b30-189">Före PowerShell 7 måste det finnas en anpassad kod för att läsa in rätt inbyggda DLL-fil så att det hanterade biblioteket kan hitta det korrekt.</span><span class="sxs-lookup"><span data-stu-id="c3b30-189">Prior to PowerShell 7, one would have to have custom code to load the appropriate native dll so that the managed library can find it correctly.</span></span>

<span data-ttu-id="c3b30-190">Med PowerShell 7 genomsöks interna binärfiler i undermappar i det hanterade bibliotekets plats enligt en delmängd av [.net RID-katalogens][] notation.</span><span class="sxs-lookup"><span data-stu-id="c3b30-190">With PowerShell 7, native binaries to load are searched in sub-folders within the managed library's location following a subset of the [.NET RID Catalog][] notation.</span></span>

```
managed.dll folder
    |
    |--- 'win-x64' folder
    |       |--- native.dll
    |
    |--- 'win-x86' folder
    |       |--- native.dll
    |
    |--- 'win-arm' folder
    |       |--- native.dll
    |
    |--- 'win-arm64' folder
    |       |--- native.dll
    |
    |--- 'linux-x64' folder
    |       |--- native.so
    |
    |--- 'linux-x86' folder
    |       |--- native.so
    |
    |--- 'linux-arm' folder
    |       |--- native.so
    |
    |--- 'linux-arm64' folder
    |       |--- native.so
    |
    |--- 'osx-x64' folder
    |       |--- native.dylib
```

<!-- reference links -->
[.NET Framework]: /dotnet/framework/
[.NET Core]: /dotnet/core/
[PSSnapIn]: /dotnet/api/system.management.automation.pssnapin
[New-ModuleManifest]: /powershell/module/microsoft.powershell.core/new-modulemanifest
[körnings kontroller]: /dotnet/api/system.runtime.interopservices.runtimeinformation.frameworkdescription#System_Runtime_InteropServices_RuntimeInformation_FrameworkDescription
[runtime checks]: /dotnet/api/system.runtime.interopservices.runtimeinformation.frameworkdescription#System_Runtime_InteropServices_RuntimeInformation_FrameworkDescription
[.NET CLI]: /dotnet/core/tools/?tabs=netcore2x
[Använda Visual Studio Code för fel sökning av kompilerade cmdlets]: vscode/using-vscode-for-debugging-compiled-cmdlets.md
[Using Visual Studio Code for debugging compiled cmdlets]: vscode/using-vscode-for-debugging-compiled-cmdlets.md
[.NET Standard]: /dotnet/standard/net-standard
[PowerShell-standard]: https://github.com/PowerShell/PowerShellStandard
[PowerShell Standard]: https://github.com/PowerShell/PowerShellStandard
[PowerShell standard 5,1]: https://www.nuget.org/packages/PowerShellStandard.Library/5.1.0
[PowerShell Standard 5.1]: https://www.nuget.org/packages/PowerShellStandard.Library/5.1.0
[PowerShell-galleriet]: https://www.powershellgallery.com
[PowerShell Gallery]: https://www.powershellgallery.com
[.NET-portbaserad analys]: https://github.com/Microsoft/dotnet-apiport
[.NET Portability Analyzer]: https://github.com/Microsoft/dotnet-apiport
[CompatiblePSEditions]: /powershell/scripting/gallery/concepts/module-psedition-support
[.NET RID-katalog]: /dotnet/core/rid-catalog
[.NET RID Catalog]: /dotnet/core/rid-catalog
