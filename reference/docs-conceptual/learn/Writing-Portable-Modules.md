---
ms.date: 12/14/2018
keywords: PowerShell cmdlet
title: Skriva bärbar moduler
ms.openlocfilehash: 38a93b5b030d58784b91292e2cd060b3a2c19a00
ms.sourcegitcommit: d396d0e4cfe3d279f399c17e7337380a31d373ac
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/21/2018
ms.locfileid: "53747729"
---
# <a name="portable-modules"></a><span data-ttu-id="e36d3-103">Bärbar moduler</span><span class="sxs-lookup"><span data-stu-id="e36d3-103">Portable Modules</span></span>

<span data-ttu-id="e36d3-104">Windows PowerShell är avsedd för [.NET Framework][] medan PowerShell Core är avsedd för [.NET Core][].</span><span class="sxs-lookup"><span data-stu-id="e36d3-104">Windows PowerShell is written for [.NET Framework][] while PowerShell Core is written for [.NET Core][].</span></span> <span data-ttu-id="e36d3-105">Bärbar moduler är moduler som fungerar i både Windows PowerShell och PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="e36d3-105">Portable modules are modules that work in both Windows PowerShell and PowerShell Core.</span></span> <span data-ttu-id="e36d3-106">.NET Framework och .NET Core är mycket kompatibel, finns men det skillnader i de tillgängliga API: er mellan två.</span><span class="sxs-lookup"><span data-stu-id="e36d3-106">While .NET Framework and .NET Core are highly compatible, there are differences in the available APIs between the two.</span></span> <span data-ttu-id="e36d3-107">Det finns också skillnader i API: er i Windows PowerShell och PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="e36d3-107">There are also differences in the APIs available in Windows PowerShell and PowerShell Core.</span></span> <span data-ttu-id="e36d3-108">Moduler som är avsedd att användas i båda miljöerna behöver känna till dessa skillnader.</span><span class="sxs-lookup"><span data-stu-id="e36d3-108">Modules intended to be used in both environments need to be aware of these differences.</span></span>

## <a name="porting-an-existing-module"></a><span data-ttu-id="e36d3-109">Porta en modul</span><span class="sxs-lookup"><span data-stu-id="e36d3-109">Porting an Existing Module</span></span>

### <a name="porting-a-pssnapin"></a><span data-ttu-id="e36d3-110">Porta en PSSnapIn</span><span class="sxs-lookup"><span data-stu-id="e36d3-110">Porting a PSSnapIn</span></span>

<span data-ttu-id="e36d3-111">PowerShell SnapIns (PSSnapIn) stöds inte i PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="e36d3-111">PowerShell SnapIns (PSSnapIn) aren't supported in PowerShell Core.</span></span> <span data-ttu-id="e36d3-112">Dock är det enkelt att konvertera en PSSnapIn till en PowerShell-modul.</span><span class="sxs-lookup"><span data-stu-id="e36d3-112">However, it's trivial to convert a PSSnapIn to a PowerShell module.</span></span> <span data-ttu-id="e36d3-113">Registreringskod PSSnapIn är vanligtvis i en enda källa-fil av en klass som härleds från [PSSnapIn][].</span><span class="sxs-lookup"><span data-stu-id="e36d3-113">Typically, the PSSnapIn registration code is in a single source file of a class that derives from [PSSnapIn][].</span></span> <span data-ttu-id="e36d3-114">Ta bort den här källfilen från build; Det är inte längre behövs.</span><span class="sxs-lookup"><span data-stu-id="e36d3-114">Remove this source file from the build; it's no longer needed.</span></span>

<span data-ttu-id="e36d3-115">Använd [New-ModuleManifest][] att skapa en ny modulmanifestet som ersätter behovet av PSSnapIn Registreringskod.</span><span class="sxs-lookup"><span data-stu-id="e36d3-115">Use [New-ModuleManifest][] to create a new module manifest that replaces the need for the PSSnapIn registration code.</span></span> <span data-ttu-id="e36d3-116">Vissa värden från PSSnapIn (till exempel beskrivning) kan återanvändas i modulmanifestet.</span><span class="sxs-lookup"><span data-stu-id="e36d3-116">Some of the values from the PSSnapIn (such as Description) can be reused within the module manifest.</span></span>

<span data-ttu-id="e36d3-117">Den `RootModule` egenskapen i modulmanifestet ska anges till namnet på sammansättningen (dll) som implementerar cmdletarna.</span><span class="sxs-lookup"><span data-stu-id="e36d3-117">The `RootModule` property in the module manifest should be set to the name of the assembly (dll) implementing the cmdlets.</span></span>

### <a name="the-net-portability-analyzer-aka-apiport"></a><span data-ttu-id="e36d3-118">.NET portabilitet Analyzer (även kallat APIPort)</span><span class="sxs-lookup"><span data-stu-id="e36d3-118">The .NET Portability Analyzer (aka APIPort)</span></span>

<span data-ttu-id="e36d3-119">Till port moduler som skrivits för Windows PowerShell för att arbeta med PowerShell Core, börja med den [.NET portabilitet Analyzer][].</span><span class="sxs-lookup"><span data-stu-id="e36d3-119">To port modules written for Windows PowerShell to work with PowerShell Core, start with the [.NET Portability Analyzer][].</span></span> <span data-ttu-id="e36d3-120">Kör det här verktyget mot din kompilerad sammansättning att avgöra om .NET API: er används i modulen är kompatibla med .NET Framework, .NET Core och andra .NET-körningar.</span><span class="sxs-lookup"><span data-stu-id="e36d3-120">Run this tool against your compiled assembly to determine if the .NET APIs used in the module are compatible with .NET Framework, .NET Core, and other .NET runtimes.</span></span> <span data-ttu-id="e36d3-121">Verktyget föreslår alternativa API: er om de finns.</span><span class="sxs-lookup"><span data-stu-id="e36d3-121">The tool suggests alternate APIs if they exist.</span></span> <span data-ttu-id="e36d3-122">Annars kan du behöva lägga till [runtime kontroller][] och begränsa funktioner som inte ingår i specifika körningar.</span><span class="sxs-lookup"><span data-stu-id="e36d3-122">Otherwise, you may need to add [runtime checks][] and restrict capabilities not available in specific runtimes.</span></span>

## <a name="creating-a-new-module"></a><span data-ttu-id="e36d3-123">Skapa en ny modul</span><span class="sxs-lookup"><span data-stu-id="e36d3-123">Creating a New Module</span></span>

<span data-ttu-id="e36d3-124">Om du skapar en ny modul rekommendationen är att använda den [.NET CLI][].</span><span class="sxs-lookup"><span data-stu-id="e36d3-124">If creating a new module, the recommendation is to use the [.NET CLI][].</span></span>

### <a name="installing-the-powershell-standard-module-template"></a><span data-ttu-id="e36d3-125">Installera PowerShell Standard modulen mallen</span><span class="sxs-lookup"><span data-stu-id="e36d3-125">Installing the PowerShell Standard Module Template</span></span>

<span data-ttu-id="e36d3-126">När .NET CLI har installerats kan du installera en mallbibliotek för att generera en enkel PowerShell-modul.</span><span class="sxs-lookup"><span data-stu-id="e36d3-126">Once the .NET CLI is installed, install a template library to generate a simple PowerShell module.</span></span>
<span data-ttu-id="e36d3-127">Modulen är kompatibel med Windows PowerShell PowerShell Core, Windows, Linux och macOS.</span><span class="sxs-lookup"><span data-stu-id="e36d3-127">The module will be compatible with Windows PowerShell, PowerShell Core, Windows, Linux, and macOS.</span></span>

<span data-ttu-id="e36d3-128">I följande exempel visas hur du installerar mallen:</span><span class="sxs-lookup"><span data-stu-id="e36d3-128">The following example shows how to install the template:</span></span>

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

### <a name="creating-a-new-module-project"></a><span data-ttu-id="e36d3-129">Skapa ett nytt projekt i modulen</span><span class="sxs-lookup"><span data-stu-id="e36d3-129">Creating a New Module Project</span></span>

<span data-ttu-id="e36d3-130">När mallen har installerats kan skapa du ett nytt PowerShell-modulen projekt med hjälp av mallen.</span><span class="sxs-lookup"><span data-stu-id="e36d3-130">After the template is installed, you can create a new PowerShell module project using that template.</span></span> <span data-ttu-id="e36d3-131">I det här exemplet kallas exempelmodulen 'myModule'.</span><span class="sxs-lookup"><span data-stu-id="e36d3-131">In this example, the sample module is called 'myModule'.</span></span>

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

### <a name="building-the-module"></a><span data-ttu-id="e36d3-132">Att skapa modulen</span><span class="sxs-lookup"><span data-stu-id="e36d3-132">Building the Module</span></span>

<span data-ttu-id="e36d3-133">Använd standard .NET CLI-kommandon för att skapa projektet.</span><span class="sxs-lookup"><span data-stu-id="e36d3-133">Use standard .NET CLI commands to build the project.</span></span>

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

### <a name="testing-the-module"></a><span data-ttu-id="e36d3-134">Testa modulen</span><span class="sxs-lookup"><span data-stu-id="e36d3-134">Testing the Module</span></span>

<span data-ttu-id="e36d3-135">När du har skapat modulen kan du importera den och kör exempel-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e36d3-135">After building the module, you can import it and execute the sample cmdlet.</span></span>

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

<span data-ttu-id="e36d3-136">I följande avsnitt beskrivs i detalj några av de tekniker som används av den här mallen.</span><span class="sxs-lookup"><span data-stu-id="e36d3-136">The following sections describe in detail some of the technologies used by this template.</span></span>

## <a name="net-standard-library"></a><span data-ttu-id="e36d3-137">.NET-standardbibliotek</span><span class="sxs-lookup"><span data-stu-id="e36d3-137">.NET Standard Library</span></span>

<span data-ttu-id="e36d3-138">[.NET standard][] är en formella specifikation av .NET API: er som är tillgängliga i alla .NET-implementeringar.</span><span class="sxs-lookup"><span data-stu-id="e36d3-138">[.NET Standard][] is a formal specification of .NET APIs that are available in all .NET implementations.</span></span> <span data-ttu-id="e36d3-139">Hanterad kod som riktar in sig på .NET Standard fungerar med .NET Framework och .NET Core-versioner som är kompatibla med den versionen av .NET-Standard.</span><span class="sxs-lookup"><span data-stu-id="e36d3-139">Managed code targeting .NET Standard works with the .NET Framework and .NET Core versions that are compatible with that version of the .NET Standard.</span></span>

> [!NOTE]
> <span data-ttu-id="e36d3-140">Även om ett API kan finnas i .NET Standard API-implementering i .NET Core kan vara en `PlatformNotSupportedException` vid körning, så för att verifiera kompatibilitet med Windows PowerShell och PowerShell Core bästa praxis är att köra tester för i båda miljöerna.</span><span class="sxs-lookup"><span data-stu-id="e36d3-140">Although an API may exist in .NET Standard, the API implementation in .NET Core may throw a `PlatformNotSupportedException` at runtime, so to verify compatibility with Windows PowerShell and PowerShell Core, the best practice is to run tests for your module within both environments.</span></span>
> <span data-ttu-id="e36d3-141">Köra testerna på Linux och macOS om din modul är avsedd att vara plattformsoberoende.</span><span class="sxs-lookup"><span data-stu-id="e36d3-141">Also run tests on Linux and macOS if your module is intended to be cross-platform.</span></span>

<span data-ttu-id="e36d3-142">Inriktning på .NET Standard hjälper till att säkerställa att som modulen utvecklas inkompatibla API: er inte av misstag bli presenterade i modulen.</span><span class="sxs-lookup"><span data-stu-id="e36d3-142">Targeting .NET Standard helps ensure that, as the module evolves, incompatible APIs don't accidentally get introduced into the module.</span></span> <span data-ttu-id="e36d3-143">Inkompatibiliteter identifieras vid kompilering i stället för körning.</span><span class="sxs-lookup"><span data-stu-id="e36d3-143">Incompatibilities are discovered at compile time instead of runtime.</span></span>

<span data-ttu-id="e36d3-144">Det inte krävs till målet för .NET Standard för en modul med både Windows PowerShell och PowerShell Core, så länge du använder kompatibla API: er.</span><span class="sxs-lookup"><span data-stu-id="e36d3-144">However, it isn't required to target .NET Standard for a module to work with both Windows PowerShell and PowerShell Core, as long as you use compatible APIs.</span></span> <span data-ttu-id="e36d3-145">Mellanliggande språk (IL) är kompatibelt mellan två körningar.</span><span class="sxs-lookup"><span data-stu-id="e36d3-145">The Intermediate Language (IL) is compatible between the two runtimes.</span></span> <span data-ttu-id="e36d3-146">Du kan använda .NET Framework 4.6.1, som är kompatibel med .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="e36d3-146">You can target .NET Framework 4.6.1, which is compatible with .NET Standard 2.0.</span></span> <span data-ttu-id="e36d3-147">Om du inte använder API: er utanför .NET Standard 2.0 fungerar modulens med PowerShell Core 6 utan att kompileras om.</span><span class="sxs-lookup"><span data-stu-id="e36d3-147">If you don't use APIs outside of .NET Standard 2.0, then your module works with PowerShell Core 6 without recompilation.</span></span>

## <a name="powershell-standard-library"></a><span data-ttu-id="e36d3-148">PowerShell-Standard-biblioteket</span><span class="sxs-lookup"><span data-stu-id="e36d3-148">PowerShell Standard Library</span></span>

<span data-ttu-id="e36d3-149">Den [PowerShell Standard][] biblioteket är en formella specifikation av PowerShell APIs tillgänglig i alla PowerShell-versioner är större än eller lika med versionen av som standard.</span><span class="sxs-lookup"><span data-stu-id="e36d3-149">The [PowerShell Standard][] library is a formal specification of PowerShell APIs available in all PowerShell versions greater than or equal to the version of that standard.</span></span>

<span data-ttu-id="e36d3-150">Till exempel [PowerShell Standard 5.1][] är kompatibelt med Windows PowerShell 5.1- och PowerShell Core 6.0 eller senare.</span><span class="sxs-lookup"><span data-stu-id="e36d3-150">For example, [PowerShell Standard 5.1][] is compatible with both Windows PowerShell 5.1 and PowerShell Core 6.0 or newer.</span></span>

<span data-ttu-id="e36d3-151">Vi rekommenderar att du kompilera modulens med hjälp av PowerShell-standardbibliotek.</span><span class="sxs-lookup"><span data-stu-id="e36d3-151">We recommend you compile your module using PowerShell Standard Library.</span></span> <span data-ttu-id="e36d3-152">Biblioteket säkerställer API: er är tillgängliga och implementerade både i Windows PowerShell och PowerShell Core 6.</span><span class="sxs-lookup"><span data-stu-id="e36d3-152">The library ensures the APIs are available and implemented in both Windows PowerShell and PowerShell Core 6.</span></span>
<span data-ttu-id="e36d3-153">PowerShell är tänkt att alltid vara vidarebefordran-kompatibel.</span><span class="sxs-lookup"><span data-stu-id="e36d3-153">PowerShell Standard is intended to always be forwards-compatible.</span></span> <span data-ttu-id="e36d3-154">En modul som skapats med hjälp av PowerShell Standard biblioteket 5.1 kommer alltid att vara kompatibel med framtida versioner av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e36d3-154">A module built using PowerShell Standard Library 5.1 will always be compatible with future versions of PowerShell.</span></span>

## <a name="module-manifest"></a><span data-ttu-id="e36d3-155">Modulmanifestet</span><span class="sxs-lookup"><span data-stu-id="e36d3-155">Module Manifest</span></span>

### <a name="indicating-compatibility-with-windows-powershell-and-powershell-core"></a><span data-ttu-id="e36d3-156">Som visar kompatibilitet med Windows PowerShell och PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="e36d3-156">Indicating Compatibility With Windows PowerShell and PowerShell Core</span></span>

<span data-ttu-id="e36d3-157">När du har validerat att modulens fungerar både med Windows PowerShell och PowerShell Core modulmanifestet uttryckligen ska indikera kompatibilitet med hjälp av den [CompatiblePSEditions][] egenskapen.</span><span class="sxs-lookup"><span data-stu-id="e36d3-157">After validating that your module works with both Windows PowerShell and PowerShell Core, the module manifest should explicitly indicate compatibility by using the [CompatiblePSEditions][] property.</span></span> <span data-ttu-id="e36d3-158">Värdet `Desktop` innebär att modulen är kompatibel med Windows PowerShell, vid värdet `Core` innebär att modulen är kompatibel med PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="e36d3-158">A value of `Desktop` means that the module is compatible with Windows PowerShell, while a value of `Core` means that the module is compatible with PowerShell Core.</span></span> <span data-ttu-id="e36d3-159">Både `Desktop` och `Core` innebär att modulen är kompatibelt med Windows PowerShell- och PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="e36d3-159">Including both `Desktop` and `Core` means that the module is compatible with both Windows PowerShell and PowerShell Core.</span></span>

> [!NOTE]
> <span data-ttu-id="e36d3-160">`Core` automatiskt innebär inte att modulen är kompatibel med Windows, Linux och macOS.</span><span class="sxs-lookup"><span data-stu-id="e36d3-160">`Core` does not automatically mean that the module is compatible with Windows, Linux, and macOS.</span></span>
> <span data-ttu-id="e36d3-161">Den **CompatiblePSEditions** egenskapen introducerades i PowerShell v5.</span><span class="sxs-lookup"><span data-stu-id="e36d3-161">The **CompatiblePSEditions** property was introduced in PowerShell v5.</span></span> <span data-ttu-id="e36d3-162">Modulen manifest som använder den **CompatiblePSEditions** egenskapen inte att läsa in i tidigare versioner än PowerShell v5.</span><span class="sxs-lookup"><span data-stu-id="e36d3-162">Module manifests that use the **CompatiblePSEditions** property fail to load in versions prior to PowerShell v5.</span></span>

### <a name="indicating-os-compatibility"></a><span data-ttu-id="e36d3-163">Om OS-kompatibilitet</span><span class="sxs-lookup"><span data-stu-id="e36d3-163">Indicating OS Compatibility</span></span>

<span data-ttu-id="e36d3-164">Verifiera först att modulens fungerar på Linux och macOS.</span><span class="sxs-lookup"><span data-stu-id="e36d3-164">First, validate that your module works on Linux and macOS.</span></span> <span data-ttu-id="e36d3-165">Därefter visa kompatibilitet med dessa operativsystem i modulmanifestet.</span><span class="sxs-lookup"><span data-stu-id="e36d3-165">Next, indicate compatibility with those operating systems in the module manifest.</span></span> <span data-ttu-id="e36d3-166">Detta gör det enklare för användarna att hitta din modul för deras operativsystem när publiceras till den [PowerShell-galleriet][].</span><span class="sxs-lookup"><span data-stu-id="e36d3-166">This makes it easier for users to find your module for their operating system when published to the [PowerShell Gallery][].</span></span>

<span data-ttu-id="e36d3-167">I modulmanifestet, den `PrivateData` egenskapen har en `PSData` underordnade egenskapen.</span><span class="sxs-lookup"><span data-stu-id="e36d3-167">Within the module manifest, the `PrivateData` property has a `PSData` sub-property.</span></span> <span data-ttu-id="e36d3-168">Den valfria `Tags` egenskapen för `PSData` tar en matris med värden som visas i PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="e36d3-168">The optional `Tags` property of `PSData` takes an array of values that show up in PowerShell Gallery.</span></span> <span data-ttu-id="e36d3-169">PowerShell-galleriet har stöd för följande kompatibilitet värden:</span><span class="sxs-lookup"><span data-stu-id="e36d3-169">The PowerShell Gallery supports the following compatibility values:</span></span>

| <span data-ttu-id="e36d3-170">Tagg</span><span class="sxs-lookup"><span data-stu-id="e36d3-170">Tag</span></span>               | <span data-ttu-id="e36d3-171">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e36d3-171">Description</span></span>                                |
|-------------------|--------------------------------------------|
| <span data-ttu-id="e36d3-172">PSEdition_Core</span><span class="sxs-lookup"><span data-stu-id="e36d3-172">PSEdition_Core</span></span>    | <span data-ttu-id="e36d3-173">Kompatibel med PowerShell Core 6</span><span class="sxs-lookup"><span data-stu-id="e36d3-173">Compatible with PowerShell Core 6</span></span>          |
| <span data-ttu-id="e36d3-174">PSEdition_Desktop</span><span class="sxs-lookup"><span data-stu-id="e36d3-174">PSEdition_Desktop</span></span> | <span data-ttu-id="e36d3-175">Kompatibel med Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e36d3-175">Compatible with Windows PowerShell</span></span>         |
| <span data-ttu-id="e36d3-176">Windows</span><span class="sxs-lookup"><span data-stu-id="e36d3-176">Windows</span></span>           | <span data-ttu-id="e36d3-177">Kompatibel med Windows</span><span class="sxs-lookup"><span data-stu-id="e36d3-177">Compatible with Windows</span></span>                    |
| <span data-ttu-id="e36d3-178">Linux</span><span class="sxs-lookup"><span data-stu-id="e36d3-178">Linux</span></span>             | <span data-ttu-id="e36d3-179">Kompatibel med Linux (ingen specifik distribution)</span><span class="sxs-lookup"><span data-stu-id="e36d3-179">Compatible with Linux (no specific distro)</span></span> |
| <span data-ttu-id="e36d3-180">macOS</span><span class="sxs-lookup"><span data-stu-id="e36d3-180">macOS</span></span>             | <span data-ttu-id="e36d3-181">Kompatibla med macOS</span><span class="sxs-lookup"><span data-stu-id="e36d3-181">Compatible with macOS</span></span>                      |

<span data-ttu-id="e36d3-182">Exempel:</span><span class="sxs-lookup"><span data-stu-id="e36d3-182">Example:</span></span>

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

<!-- reference links -->
[.NET framework]: /dotnet/framework/
[.NET Framework]: /dotnet/framework/
[.NET core]: /dotnet/core/
[.NET Core]: /dotnet/core/
[PSSnapIn]: /dotnet/api/system.management.automation.pssnapin
[New-ModuleManifest]: /powershell/module/microsoft.powershell.core/new-modulemanifest
[runtime kontroller]: /dotnet/api/system.runtime.interopservices.runtimeinformation.frameworkdescription#System_Runtime_InteropServices_RuntimeInformation_FrameworkDescription
[runtime checks]: /dotnet/api/system.runtime.interopservices.runtimeinformation.frameworkdescription#System_Runtime_InteropServices_RuntimeInformation_FrameworkDescription
[.NET CLI]: /dotnet/core/tools/?tabs=netcore2x
[.NET standard]: /dotnet/standard/net-standard
[.NET Standard]: /dotnet/standard/net-standard
[PowerShell Standard]: https://github.com/PowerShell/PowerShellStandard
[PowerShell Standard 5.1]: https://www.nuget.org/packages/PowerShellStandard.Library/5.1.0
[PowerShell-galleriet]: https://www.powershellgallery.com
[PowerShell Gallery]: https://www.powershellgallery.com
[.NET portabilitet Analyzer]: https://github.com/Microsoft/dotnet-apiport
[.NET Portability Analyzer]: https://github.com/Microsoft/dotnet-apiport
[CompatiblePSEditions]: /powershell/gallery/concepts/module-psedition-support
