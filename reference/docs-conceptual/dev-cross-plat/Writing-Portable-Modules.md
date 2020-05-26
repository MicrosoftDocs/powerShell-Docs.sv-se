---
ms.date: 01/10/2020
keywords: powershell,cmdlet
title: Skriva portabla moduler
ms.openlocfilehash: 124e6efadfd07b8c5214a5c0446b1589f7142388
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83810962"
---
# <a name="portable-modules"></a><span data-ttu-id="cd0ef-103">Bärbara moduler</span><span class="sxs-lookup"><span data-stu-id="cd0ef-103">Portable Modules</span></span>

<span data-ttu-id="cd0ef-104">Windows PowerShell är skrivet för [.NET Framework][] medan PowerShell-kärnan skrivs för [.net Core][].</span><span class="sxs-lookup"><span data-stu-id="cd0ef-104">Windows PowerShell is written for [.NET Framework][] while PowerShell Core is written for [.NET Core][].</span></span> <span data-ttu-id="cd0ef-105">Bärbara moduler är moduler som fungerar både i Windows PowerShell och PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="cd0ef-105">Portable modules are modules that work in both Windows PowerShell and PowerShell Core.</span></span> <span data-ttu-id="cd0ef-106">Även om .NET Framework och .NET Core är mycket kompatibla finns det skillnader i de tillgängliga API: erna mellan de två.</span><span class="sxs-lookup"><span data-stu-id="cd0ef-106">While .NET Framework and .NET Core are highly compatible, there are differences in the available APIs between the two.</span></span> <span data-ttu-id="cd0ef-107">Det finns också skillnader i de API: er som är tillgängliga i Windows PowerShell och PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="cd0ef-107">There are also differences in the APIs available in Windows PowerShell and PowerShell Core.</span></span> <span data-ttu-id="cd0ef-108">Moduler som är avsedda att användas i båda miljöerna måste vara medvetna om dessa skillnader.</span><span class="sxs-lookup"><span data-stu-id="cd0ef-108">Modules intended to be used in both environments need to be aware of these differences.</span></span>

## <a name="porting-an-existing-module"></a><span data-ttu-id="cd0ef-109">Portning av en befintlig modul</span><span class="sxs-lookup"><span data-stu-id="cd0ef-109">Porting an Existing Module</span></span>

### <a name="porting-a-pssnapin"></a><span data-ttu-id="cd0ef-110">Porting a PSSnapIn</span><span class="sxs-lookup"><span data-stu-id="cd0ef-110">Porting a PSSnapIn</span></span>

<span data-ttu-id="cd0ef-111">PowerShell- [modulerna](/powershell/scripting/developer/cmdlet/modules-and-snap-ins) stöds inte i PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="cd0ef-111">PowerShell [SnapIns](/powershell/scripting/developer/cmdlet/modules-and-snap-ins) aren't supported in PowerShell Core.</span></span> <span data-ttu-id="cd0ef-112">Det är dock enkelt att konvertera en PSSnapIn till en PowerShell-modul.</span><span class="sxs-lookup"><span data-stu-id="cd0ef-112">However, it's trivial to convert a PSSnapIn to a PowerShell module.</span></span> <span data-ttu-id="cd0ef-113">Normalt är registrerings koden PSSnapIn i en enda källfil för en klass som härleds från [PSSnapIn][].</span><span class="sxs-lookup"><span data-stu-id="cd0ef-113">Typically, the PSSnapIn registration code is in a single source file of a class that derives from [PSSnapIn][].</span></span>
<span data-ttu-id="cd0ef-114">Ta bort den här käll filen från versionen. det behövs inte längre.</span><span class="sxs-lookup"><span data-stu-id="cd0ef-114">Remove this source file from the build; it's no longer needed.</span></span>

<span data-ttu-id="cd0ef-115">Använd [New-ModuleManifest][] för att skapa ett nytt modul-manifest som ersätter behovet av registrerings koden för PSSnapIn.</span><span class="sxs-lookup"><span data-stu-id="cd0ef-115">Use [New-ModuleManifest][] to create a new module manifest that replaces the need for the PSSnapIn registration code.</span></span> <span data-ttu-id="cd0ef-116">Några av värdena från **PSSnapIn** (till exempel **Beskrivning**) kan återanvändas i manifestet för modulen.</span><span class="sxs-lookup"><span data-stu-id="cd0ef-116">Some of the values from the **PSSnapIn** (such as **Description**) can be reused within the module manifest.</span></span>

<span data-ttu-id="cd0ef-117">Egenskapen **RootModule** i modulen manifest ska anges till namnet på sammansättningen (dll) som implementerar cmdletarna.</span><span class="sxs-lookup"><span data-stu-id="cd0ef-117">The **RootModule** property in the module manifest should be set to the name of the assembly (dll) implementing the cmdlets.</span></span>

### <a name="the-net-portability-analyzer-aka-apiport"></a><span data-ttu-id="cd0ef-118">.NET-portbaserad analys för aka (APIPort)</span><span class="sxs-lookup"><span data-stu-id="cd0ef-118">The .NET Portability Analyzer (aka APIPort)</span></span>

<span data-ttu-id="cd0ef-119">Om du vill att moduler som är skrivna för Windows PowerShell ska fungera med PowerShell-kärnan börjar du med [.net-ports Analyzer][].</span><span class="sxs-lookup"><span data-stu-id="cd0ef-119">To port modules written for Windows PowerShell to work with PowerShell Core, start with the [.NET Portability Analyzer][].</span></span> <span data-ttu-id="cd0ef-120">Kör det här verktyget mot den kompilerade sammansättningen för att avgöra om de .NET-API: er som används i modulen är kompatibla med .NET Framework, .NET Core och andra .NET-körningar.</span><span class="sxs-lookup"><span data-stu-id="cd0ef-120">Run this tool against your compiled assembly to determine if the .NET APIs used in the module are compatible with .NET Framework, .NET Core, and other .NET runtimes.</span></span> <span data-ttu-id="cd0ef-121">Verktyget föreslår alternativa API: er om de finns.</span><span class="sxs-lookup"><span data-stu-id="cd0ef-121">The tool suggests alternate APIs if they exist.</span></span> <span data-ttu-id="cd0ef-122">Annars kan du behöva lägga till [körnings kontroller][] och begränsa funktioner som inte är tillgängliga i vissa körningar.</span><span class="sxs-lookup"><span data-stu-id="cd0ef-122">Otherwise, you may need to add [runtime checks][] and restrict capabilities not available in specific runtimes.</span></span>

## <a name="creating-a-new-module"></a><span data-ttu-id="cd0ef-123">Skapa en ny modul</span><span class="sxs-lookup"><span data-stu-id="cd0ef-123">Creating a New Module</span></span>

<span data-ttu-id="cd0ef-124">Om du skapar en ny modul är rekommendationen att använda [.net CLI][].</span><span class="sxs-lookup"><span data-stu-id="cd0ef-124">If creating a new module, the recommendation is to use the [.NET CLI][].</span></span>

### <a name="installing-the-powershell-standard-module-template"></a><span data-ttu-id="cd0ef-125">Installera PowerShell-modulen för standard mal len</span><span class="sxs-lookup"><span data-stu-id="cd0ef-125">Installing the PowerShell Standard Module Template</span></span>

<span data-ttu-id="cd0ef-126">När .NET CLI har installerats installerar du ett mall bibliotek för att generera en enkel PowerShell-modul.</span><span class="sxs-lookup"><span data-stu-id="cd0ef-126">Once the .NET CLI is installed, install a template library to generate a simple PowerShell module.</span></span>
<span data-ttu-id="cd0ef-127">Modulen är kompatibel med Windows PowerShell, PowerShell Core, Windows, Linux och macOS.</span><span class="sxs-lookup"><span data-stu-id="cd0ef-127">The module will be compatible with Windows PowerShell, PowerShell Core, Windows, Linux, and macOS.</span></span>

<span data-ttu-id="cd0ef-128">I följande exempel visas hur du installerar mallen:</span><span class="sxs-lookup"><span data-stu-id="cd0ef-128">The following example shows how to install the template:</span></span>

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


Templates                                         Short Name         Language          Tags
----------------------------------------------------------------------------------------------------------------------------
Console Application                               console            [C#], F#, VB      Common/Console
Class library                                     classlib           [C#], F#, VB      Common/Library
PowerShell Standard Module                        psmodule           [C#]              Library/PowerShell/Module
...
```

### <a name="creating-a-new-module-project"></a><span data-ttu-id="cd0ef-129">Skapa ett nytt modul-projekt</span><span class="sxs-lookup"><span data-stu-id="cd0ef-129">Creating a New Module Project</span></span>

<span data-ttu-id="cd0ef-130">När mallen har installerats kan du skapa ett nytt PowerShell-Modulnamn med den mallen.</span><span class="sxs-lookup"><span data-stu-id="cd0ef-130">After the template is installed, you can create a new PowerShell module project using that template.</span></span> <span data-ttu-id="cd0ef-131">I det här exemplet kallas exempel modulen "module".</span><span class="sxs-lookup"><span data-stu-id="cd0ef-131">In this example, the sample module is called 'myModule'.</span></span>

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

### <a name="building-the-module"></a><span data-ttu-id="cd0ef-132">Modulen skapas</span><span class="sxs-lookup"><span data-stu-id="cd0ef-132">Building the Module</span></span>

<span data-ttu-id="cd0ef-133">Använd standard .NET CLI-kommandon för att bygga projektet.</span><span class="sxs-lookup"><span data-stu-id="cd0ef-133">Use standard .NET CLI commands to build the project.</span></span>

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

### <a name="testing-the-module"></a><span data-ttu-id="cd0ef-134">Testa modulen</span><span class="sxs-lookup"><span data-stu-id="cd0ef-134">Testing the Module</span></span>

<span data-ttu-id="cd0ef-135">När du har skapat modulen kan du importera den och köra exempel-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="cd0ef-135">After building the module, you can import it and execute the sample cmdlet.</span></span>

```powershell
ipmo .\bin\Debug\netstandard2.0\myModule.dll
Test-SampleCmdlet -?
Test-SampleCmdlet -FavoriteNumber 7 -FavoritePet Cat
```

```output
PS C:\Users\Steve\myModule> ipmo .\bin\Debug\netstandard2.0\myModule.dll
PS C:\Users\Steve\myModule> Test-SampleCmdlet -?

NAME
    Test-SampleCmdlet

SYNTAX
    Test-SampleCmdlet [-FavoriteNumber] <int> [[-FavoritePet] {Cat | Dog | Horse}] [<CommonParameters>]


ALIASES
    None


REMARKS
    None


PS C:\Users\Steve\myModule> Test-SampleCmdlet -FavoriteNumber 7 -FavoritePet Cat

FavoriteNumber FavoritePet
-------------- -----------
             7 Cat
```

<span data-ttu-id="cd0ef-136">I följande avsnitt beskrivs några av de tekniker som används av den här mallen.</span><span class="sxs-lookup"><span data-stu-id="cd0ef-136">The following sections describe in detail some of the technologies used by this template.</span></span>

## <a name="net-standard-library"></a><span data-ttu-id="cd0ef-137">.NET standard-bibliotek</span><span class="sxs-lookup"><span data-stu-id="cd0ef-137">.NET Standard Library</span></span>

<span data-ttu-id="cd0ef-138">[.Net standard][] är en formell specifikation av .NET-API: er som är tillgängliga i alla .net-implementeringar.</span><span class="sxs-lookup"><span data-stu-id="cd0ef-138">[.NET Standard][] is a formal specification of .NET APIs that are available in all .NET implementations.</span></span> <span data-ttu-id="cd0ef-139">Hanterad kod för .NET standard fungerar med de .NET Framework-och .NET Core-versioner som är kompatibla med den versionen av .NET standard.</span><span class="sxs-lookup"><span data-stu-id="cd0ef-139">Managed code targeting .NET Standard works with the .NET Framework and .NET Core versions that are compatible with that version of the .NET Standard.</span></span>

> [!NOTE]
> <span data-ttu-id="cd0ef-140">Även om ett API kan finnas i .NET standard kan API-implementeringen i .NET Core medföra en `PlatformNotSupportedException` vid körning, så för att kontrol lera kompatibilitet med Windows PowerShell och PowerShell Core är det bästa sättet att köra tester för modulen i båda miljöerna.</span><span class="sxs-lookup"><span data-stu-id="cd0ef-140">Although an API may exist in .NET Standard, the API implementation in .NET Core may throw a `PlatformNotSupportedException` at runtime, so to verify compatibility with Windows PowerShell and PowerShell Core, the best practice is to run tests for your module within both environments.</span></span>
> <span data-ttu-id="cd0ef-141">Kör även tester på Linux och macOS om modulen är avsedd att vara plattforms oberoende.</span><span class="sxs-lookup"><span data-stu-id="cd0ef-141">Also run tests on Linux and macOS if your module is intended to be cross-platform.</span></span>

<span data-ttu-id="cd0ef-142">Genom att använda .NET standard kan du se till att inkompatibla API: er inte har introducerats av misstag i modulen, eftersom modulen utvecklas.</span><span class="sxs-lookup"><span data-stu-id="cd0ef-142">Targeting .NET Standard helps ensure that, as the module evolves, incompatible APIs don't accidentally get introduced into the module.</span></span> <span data-ttu-id="cd0ef-143">Inkompatibiliteter upptäcks vid kompilering i stället för körning.</span><span class="sxs-lookup"><span data-stu-id="cd0ef-143">Incompatibilities are discovered at compile time instead of runtime.</span></span>

<span data-ttu-id="cd0ef-144">Men det är inte nödvändigt att använda .NET standard för att en modul ska fungera med både Windows PowerShell och PowerShell Core, så länge du använder kompatibla API: er.</span><span class="sxs-lookup"><span data-stu-id="cd0ef-144">However, it isn't required to target .NET Standard for a module to work with both Windows PowerShell and PowerShell Core, as long as you use compatible APIs.</span></span> <span data-ttu-id="cd0ef-145">Det mellanliggande språket (IL) är kompatibelt mellan de två körningarna.</span><span class="sxs-lookup"><span data-stu-id="cd0ef-145">The Intermediate Language (IL) is compatible between the two runtimes.</span></span> <span data-ttu-id="cd0ef-146">Du kan rikta .NET Framework 4.6.1, som är kompatibel med .NET standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="cd0ef-146">You can target .NET Framework 4.6.1, which is compatible with .NET Standard 2.0.</span></span> <span data-ttu-id="cd0ef-147">Om du inte använder API: er utanför .NET standard 2,0, fungerar modulen med PowerShell Core 6 utan att kompilera om.</span><span class="sxs-lookup"><span data-stu-id="cd0ef-147">If you don't use APIs outside of .NET Standard 2.0, then your module works with PowerShell Core 6 without recompilation.</span></span>

## <a name="powershell-standard-library"></a><span data-ttu-id="cd0ef-148">PowerShell-standardbibliotek</span><span class="sxs-lookup"><span data-stu-id="cd0ef-148">PowerShell Standard Library</span></span>

<span data-ttu-id="cd0ef-149">[PowerShell][] -standardbiblioteket är en formell specifikation av PowerShell-API: er som är tillgängliga i alla PowerShell-versioner som är större än eller lika med den standard versionen.</span><span class="sxs-lookup"><span data-stu-id="cd0ef-149">The [PowerShell Standard][] library is a formal specification of PowerShell APIs available in all PowerShell versions greater than or equal to the version of that standard.</span></span>

<span data-ttu-id="cd0ef-150">Till exempel är [PowerShell Standard 5,1][] kompatibelt med både Windows PowerShell 5,1 och PowerShell Core 6,0 eller senare.</span><span class="sxs-lookup"><span data-stu-id="cd0ef-150">For example, [PowerShell Standard 5.1][] is compatible with both Windows PowerShell 5.1 and PowerShell Core 6.0 or newer.</span></span>

<span data-ttu-id="cd0ef-151">Vi rekommenderar att du kompilerar modulen med PowerShell-standardbiblioteket.</span><span class="sxs-lookup"><span data-stu-id="cd0ef-151">We recommend you compile your module using PowerShell Standard Library.</span></span> <span data-ttu-id="cd0ef-152">Biblioteket säkerställer att API: erna är tillgängliga och implementerade i både Windows PowerShell och PowerShell Core 6.</span><span class="sxs-lookup"><span data-stu-id="cd0ef-152">The library ensures the APIs are available and implemented in both Windows PowerShell and PowerShell Core 6.</span></span>
<span data-ttu-id="cd0ef-153">PowerShell-standarden är avsedd att alltid vidarebefordras-kompatibel.</span><span class="sxs-lookup"><span data-stu-id="cd0ef-153">PowerShell Standard is intended to always be forwards-compatible.</span></span> <span data-ttu-id="cd0ef-154">En modul som skapats med PowerShell standard library 5,1 är alltid kompatibel med framtida versioner av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cd0ef-154">A module built using PowerShell Standard Library 5.1 will always be compatible with future versions of PowerShell.</span></span>

## <a name="module-manifest"></a><span data-ttu-id="cd0ef-155">Modul manifest</span><span class="sxs-lookup"><span data-stu-id="cd0ef-155">Module Manifest</span></span>

### <a name="indicating-compatibility-with-windows-powershell-and-powershell-core"></a><span data-ttu-id="cd0ef-156">Indikerar kompatibilitet med Windows PowerShell och PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="cd0ef-156">Indicating Compatibility With Windows PowerShell and PowerShell Core</span></span>

<span data-ttu-id="cd0ef-157">När du har verifierat att modulen fungerar med både Windows PowerShell och PowerShell Core bör modulens manifest uttryckligen indikera kompatibilitet med hjälp av egenskapen [CompatiblePSEditions][] .</span><span class="sxs-lookup"><span data-stu-id="cd0ef-157">After validating that your module works with both Windows PowerShell and PowerShell Core, the module manifest should explicitly indicate compatibility by using the [CompatiblePSEditions][] property.</span></span> <span data-ttu-id="cd0ef-158">Värdet `Desktop` innebär att modulen är kompatibel med Windows PowerShell, medan värdet `Core` innebär att modulen är kompatibel med PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="cd0ef-158">A value of `Desktop` means that the module is compatible with Windows PowerShell, while a value of `Core` means that the module is compatible with PowerShell Core.</span></span> <span data-ttu-id="cd0ef-159">Inklusive både `Desktop` och `Core` innebär att modulen är kompatibel med både Windows PowerShell och PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="cd0ef-159">Including both `Desktop` and `Core` means that the module is compatible with both Windows PowerShell and PowerShell Core.</span></span>

> [!NOTE]
> <span data-ttu-id="cd0ef-160">`Core`innebär inte automatiskt att modulen är kompatibel med Windows, Linux och macOS.</span><span class="sxs-lookup"><span data-stu-id="cd0ef-160">`Core` does not automatically mean that the module is compatible with Windows, Linux, and macOS.</span></span>
> <span data-ttu-id="cd0ef-161">Egenskapen **CompatiblePSEditions** introducerades i PowerShell v5.</span><span class="sxs-lookup"><span data-stu-id="cd0ef-161">The **CompatiblePSEditions** property was introduced in PowerShell v5.</span></span> <span data-ttu-id="cd0ef-162">Modul manifest som använder egenskapen **CompatiblePSEditions** kan inte läsas in i tidigare versioner än PowerShell v5.</span><span class="sxs-lookup"><span data-stu-id="cd0ef-162">Module manifests that use the **CompatiblePSEditions** property fail to load in versions prior to PowerShell v5.</span></span>

### <a name="indicating-os-compatibility"></a><span data-ttu-id="cd0ef-163">Indikerar OS-kompatibilitet</span><span class="sxs-lookup"><span data-stu-id="cd0ef-163">Indicating OS Compatibility</span></span>

<span data-ttu-id="cd0ef-164">Kontrol lera först att modulen fungerar på Linux och macOS.</span><span class="sxs-lookup"><span data-stu-id="cd0ef-164">First, validate that your module works on Linux and macOS.</span></span> <span data-ttu-id="cd0ef-165">Sedan anger du kompatibiliteten med dessa operativ system i manifestet för modulen.</span><span class="sxs-lookup"><span data-stu-id="cd0ef-165">Next, indicate compatibility with those operating systems in the module manifest.</span></span> <span data-ttu-id="cd0ef-166">Detta gör det enklare för användarna att hitta modulen för sitt operativ system när de publiceras till [PowerShell-galleriet][].</span><span class="sxs-lookup"><span data-stu-id="cd0ef-166">This makes it easier for users to find your module for their operating system when published to the [PowerShell Gallery][].</span></span>

<span data-ttu-id="cd0ef-167">I modulen manifest `PrivateData` har egenskapen en `PSData` underordnad egenskap.</span><span class="sxs-lookup"><span data-stu-id="cd0ef-167">Within the module manifest, the `PrivateData` property has a `PSData` sub-property.</span></span> <span data-ttu-id="cd0ef-168">Den valfria `Tags` egenskapen för `PSData` tar en matris med värden som visas i PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="cd0ef-168">The optional `Tags` property of `PSData` takes an array of values that show up in PowerShell Gallery.</span></span> <span data-ttu-id="cd0ef-169">PowerShell-galleriet har stöd för följande kompatibilitetsinställningar:</span><span class="sxs-lookup"><span data-stu-id="cd0ef-169">The PowerShell Gallery supports the following compatibility values:</span></span>

| <span data-ttu-id="cd0ef-170">Tagga</span><span class="sxs-lookup"><span data-stu-id="cd0ef-170">Tag</span></span>               | <span data-ttu-id="cd0ef-171">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="cd0ef-171">Description</span></span>                                |
|-------------------|--------------------------------------------|
| <span data-ttu-id="cd0ef-172">PSEdition_Core</span><span class="sxs-lookup"><span data-stu-id="cd0ef-172">PSEdition_Core</span></span>    | <span data-ttu-id="cd0ef-173">Kompatibel med PowerShell Core 6</span><span class="sxs-lookup"><span data-stu-id="cd0ef-173">Compatible with PowerShell Core 6</span></span>          |
| <span data-ttu-id="cd0ef-174">PSEdition_Desktop</span><span class="sxs-lookup"><span data-stu-id="cd0ef-174">PSEdition_Desktop</span></span> | <span data-ttu-id="cd0ef-175">Kompatibel med Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="cd0ef-175">Compatible with Windows PowerShell</span></span>         |
| <span data-ttu-id="cd0ef-176">Windows</span><span class="sxs-lookup"><span data-stu-id="cd0ef-176">Windows</span></span>           | <span data-ttu-id="cd0ef-177">Kompatibel med Windows</span><span class="sxs-lookup"><span data-stu-id="cd0ef-177">Compatible with Windows</span></span>                    |
| <span data-ttu-id="cd0ef-178">Linux</span><span class="sxs-lookup"><span data-stu-id="cd0ef-178">Linux</span></span>             | <span data-ttu-id="cd0ef-179">Kompatibel med Linux (inga speciella distribution)</span><span class="sxs-lookup"><span data-stu-id="cd0ef-179">Compatible with Linux (no specific distro)</span></span> |
| <span data-ttu-id="cd0ef-180">macOS</span><span class="sxs-lookup"><span data-stu-id="cd0ef-180">macOS</span></span>             | <span data-ttu-id="cd0ef-181">Kompatibel med macOS</span><span class="sxs-lookup"><span data-stu-id="cd0ef-181">Compatible with macOS</span></span>                      |

<span data-ttu-id="cd0ef-182">Exempel:</span><span class="sxs-lookup"><span data-stu-id="cd0ef-182">Example:</span></span>

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

## <a name="dependency-on-native-libraries"></a><span data-ttu-id="cd0ef-183">Beroende av interna bibliotek</span><span class="sxs-lookup"><span data-stu-id="cd0ef-183">Dependency on Native Libraries</span></span>

<span data-ttu-id="cd0ef-184">Moduler som ska användas i olika operativ system eller processor arkitekturer kan vara beroende av ett hanterat bibliotek som är beroende av vissa interna bibliotek.</span><span class="sxs-lookup"><span data-stu-id="cd0ef-184">Modules intended for use across different operating systems or processor architectures may depend on a managed library that itself depends on some native libraries.</span></span>

<span data-ttu-id="cd0ef-185">Före PowerShell 7 måste det finnas en anpassad kod för att läsa in rätt inbyggda DLL-fil så att det hanterade biblioteket kan hitta det korrekt.</span><span class="sxs-lookup"><span data-stu-id="cd0ef-185">Prior to PowerShell 7, one would have to have custom code to load the appropriate native dll so that the managed library can find it correctly.</span></span>

<span data-ttu-id="cd0ef-186">Med PowerShell 7 genomsöks interna binärfiler i undermappar i det hanterade bibliotekets plats enligt en delmängd av [.net RID-katalogens][] notation.</span><span class="sxs-lookup"><span data-stu-id="cd0ef-186">With PowerShell 7, native binaries to load are searched in sub-folders within the managed library's location following a subset of the [.NET RID Catalog][] notation.</span></span>

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
[.NET RID-katalog]: https://docs.microsoft.com/dotnet/core/rid-catalog
[.NET RID Catalog]: https://docs.microsoft.com/dotnet/core/rid-catalog
