---
ms.date: 12/14/2018
keywords: powershell,cmdlet
title: Writing Portable Modules
ms.openlocfilehash: 7871f524495c1ce5283b30696a24185d427edebf
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417640"
---
# <a name="portable-modules"></a><span data-ttu-id="c2a26-103">Portable Modules</span><span class="sxs-lookup"><span data-stu-id="c2a26-103">Portable Modules</span></span>

<span data-ttu-id="c2a26-104">Windows PowerShell is written for [.NET Framework][] while PowerShell Core is written for [.NET Core][].</span><span class="sxs-lookup"><span data-stu-id="c2a26-104">Windows PowerShell is written for [.NET Framework][] while PowerShell Core is written for [.NET Core][].</span></span> <span data-ttu-id="c2a26-105">Portable modules are modules that work in both Windows PowerShell and PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="c2a26-105">Portable modules are modules that work in both Windows PowerShell and PowerShell Core.</span></span> <span data-ttu-id="c2a26-106">While .NET Framework and .NET Core are highly compatible, there are differences in the available APIs between the two.</span><span class="sxs-lookup"><span data-stu-id="c2a26-106">While .NET Framework and .NET Core are highly compatible, there are differences in the available APIs between the two.</span></span> <span data-ttu-id="c2a26-107">There are also differences in the APIs available in Windows PowerShell and PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="c2a26-107">There are also differences in the APIs available in Windows PowerShell and PowerShell Core.</span></span> <span data-ttu-id="c2a26-108">Modules intended to be used in both environments need to be aware of these differences.</span><span class="sxs-lookup"><span data-stu-id="c2a26-108">Modules intended to be used in both environments need to be aware of these differences.</span></span>

## <a name="porting-an-existing-module"></a><span data-ttu-id="c2a26-109">Porting an Existing Module</span><span class="sxs-lookup"><span data-stu-id="c2a26-109">Porting an Existing Module</span></span>

### <a name="porting-a-pssnapin"></a><span data-ttu-id="c2a26-110">Porting a PSSnapIn</span><span class="sxs-lookup"><span data-stu-id="c2a26-110">Porting a PSSnapIn</span></span>

<span data-ttu-id="c2a26-111">PowerShell [SnapIns](/powershell/scripting/developer/cmdlet/modules-and-snap-ins) aren't supported in PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="c2a26-111">PowerShell [SnapIns](/powershell/scripting/developer/cmdlet/modules-and-snap-ins) aren't supported in PowerShell Core.</span></span> <span data-ttu-id="c2a26-112">However, it's trivial to convert a PSSnapIn to a PowerShell module.</span><span class="sxs-lookup"><span data-stu-id="c2a26-112">However, it's trivial to convert a PSSnapIn to a PowerShell module.</span></span> <span data-ttu-id="c2a26-113">Typically, the PSSnapIn registration code is in a single source file of a class that derives from [PSSnapIn][].</span><span class="sxs-lookup"><span data-stu-id="c2a26-113">Typically, the PSSnapIn registration code is in a single source file of a class that derives from [PSSnapIn][].</span></span>
<span data-ttu-id="c2a26-114">Remove this source file from the build; it's no longer needed.</span><span class="sxs-lookup"><span data-stu-id="c2a26-114">Remove this source file from the build; it's no longer needed.</span></span>

<span data-ttu-id="c2a26-115">Use [New-ModuleManifest][] to create a new module manifest that replaces the need for the PSSnapIn registration code.</span><span class="sxs-lookup"><span data-stu-id="c2a26-115">Use [New-ModuleManifest][] to create a new module manifest that replaces the need for the PSSnapIn registration code.</span></span> <span data-ttu-id="c2a26-116">Some of the values from the **PSSnapIn** (such as **Description**) can be reused within the module manifest.</span><span class="sxs-lookup"><span data-stu-id="c2a26-116">Some of the values from the **PSSnapIn** (such as **Description**) can be reused within the module manifest.</span></span>

<span data-ttu-id="c2a26-117">The **RootModule** property in the module manifest should be set to the name of the assembly (dll) implementing the cmdlets.</span><span class="sxs-lookup"><span data-stu-id="c2a26-117">The **RootModule** property in the module manifest should be set to the name of the assembly (dll) implementing the cmdlets.</span></span>

### <a name="the-net-portability-analyzer-aka-apiport"></a><span data-ttu-id="c2a26-118">The .NET Portability Analyzer (aka APIPort)</span><span class="sxs-lookup"><span data-stu-id="c2a26-118">The .NET Portability Analyzer (aka APIPort)</span></span>

<span data-ttu-id="c2a26-119">To port modules written for Windows PowerShell to work with PowerShell Core, start with the [.NET Portability Analyzer][].</span><span class="sxs-lookup"><span data-stu-id="c2a26-119">To port modules written for Windows PowerShell to work with PowerShell Core, start with the [.NET Portability Analyzer][].</span></span> <span data-ttu-id="c2a26-120">Run this tool against your compiled assembly to determine if the .NET APIs used in the module are compatible with .NET Framework, .NET Core, and other .NET runtimes.</span><span class="sxs-lookup"><span data-stu-id="c2a26-120">Run this tool against your compiled assembly to determine if the .NET APIs used in the module are compatible with .NET Framework, .NET Core, and other .NET runtimes.</span></span> <span data-ttu-id="c2a26-121">The tool suggests alternate APIs if they exist.</span><span class="sxs-lookup"><span data-stu-id="c2a26-121">The tool suggests alternate APIs if they exist.</span></span> <span data-ttu-id="c2a26-122">Otherwise, you may need to add [runtime checks][] and restrict capabilities not available in specific runtimes.</span><span class="sxs-lookup"><span data-stu-id="c2a26-122">Otherwise, you may need to add [runtime checks][] and restrict capabilities not available in specific runtimes.</span></span>

## <a name="creating-a-new-module"></a><span data-ttu-id="c2a26-123">Creating a New Module</span><span class="sxs-lookup"><span data-stu-id="c2a26-123">Creating a New Module</span></span>

<span data-ttu-id="c2a26-124">If creating a new module, the recommendation is to use the [.NET CLI][].</span><span class="sxs-lookup"><span data-stu-id="c2a26-124">If creating a new module, the recommendation is to use the [.NET CLI][].</span></span>

### <a name="installing-the-powershell-standard-module-template"></a><span data-ttu-id="c2a26-125">Installing the PowerShell Standard Module Template</span><span class="sxs-lookup"><span data-stu-id="c2a26-125">Installing the PowerShell Standard Module Template</span></span>

<span data-ttu-id="c2a26-126">Once the .NET CLI is installed, install a template library to generate a simple PowerShell module.</span><span class="sxs-lookup"><span data-stu-id="c2a26-126">Once the .NET CLI is installed, install a template library to generate a simple PowerShell module.</span></span>
<span data-ttu-id="c2a26-127">The module will be compatible with Windows PowerShell, PowerShell Core, Windows, Linux, and macOS.</span><span class="sxs-lookup"><span data-stu-id="c2a26-127">The module will be compatible with Windows PowerShell, PowerShell Core, Windows, Linux, and macOS.</span></span>

<span data-ttu-id="c2a26-128">The following example shows how to install the template:</span><span class="sxs-lookup"><span data-stu-id="c2a26-128">The following example shows how to install the template:</span></span>

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

### <a name="creating-a-new-module-project"></a><span data-ttu-id="c2a26-129">Creating a New Module Project</span><span class="sxs-lookup"><span data-stu-id="c2a26-129">Creating a New Module Project</span></span>

<span data-ttu-id="c2a26-130">After the template is installed, you can create a new PowerShell module project using that template.</span><span class="sxs-lookup"><span data-stu-id="c2a26-130">After the template is installed, you can create a new PowerShell module project using that template.</span></span> <span data-ttu-id="c2a26-131">In this example, the sample module is called 'myModule'.</span><span class="sxs-lookup"><span data-stu-id="c2a26-131">In this example, the sample module is called 'myModule'.</span></span>

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

### <a name="building-the-module"></a><span data-ttu-id="c2a26-132">Building the Module</span><span class="sxs-lookup"><span data-stu-id="c2a26-132">Building the Module</span></span>

<span data-ttu-id="c2a26-133">Use standard .NET CLI commands to build the project.</span><span class="sxs-lookup"><span data-stu-id="c2a26-133">Use standard .NET CLI commands to build the project.</span></span>

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

### <a name="testing-the-module"></a><span data-ttu-id="c2a26-134">Testing the Module</span><span class="sxs-lookup"><span data-stu-id="c2a26-134">Testing the Module</span></span>

<span data-ttu-id="c2a26-135">After building the module, you can import it and execute the sample cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c2a26-135">After building the module, you can import it and execute the sample cmdlet.</span></span>

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

<span data-ttu-id="c2a26-136">The following sections describe in detail some of the technologies used by this template.</span><span class="sxs-lookup"><span data-stu-id="c2a26-136">The following sections describe in detail some of the technologies used by this template.</span></span>

## <a name="net-standard-library"></a><span data-ttu-id="c2a26-137">.NET Standard Library</span><span class="sxs-lookup"><span data-stu-id="c2a26-137">.NET Standard Library</span></span>

<span data-ttu-id="c2a26-138">[.NET Standard][] is a formal specification of .NET APIs that are available in all .NET implementations.</span><span class="sxs-lookup"><span data-stu-id="c2a26-138">[.NET Standard][] is a formal specification of .NET APIs that are available in all .NET implementations.</span></span> <span data-ttu-id="c2a26-139">Managed code targeting .NET Standard works with the .NET Framework and .NET Core versions that are compatible with that version of the .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="c2a26-139">Managed code targeting .NET Standard works with the .NET Framework and .NET Core versions that are compatible with that version of the .NET Standard.</span></span>

> [!NOTE]
> <span data-ttu-id="c2a26-140">Although an API may exist in .NET Standard, the API implementation in .NET Core may throw a `PlatformNotSupportedException` at runtime, so to verify compatibility with Windows PowerShell and PowerShell Core, the best practice is to run tests for your module within both environments.</span><span class="sxs-lookup"><span data-stu-id="c2a26-140">Although an API may exist in .NET Standard, the API implementation in .NET Core may throw a `PlatformNotSupportedException` at runtime, so to verify compatibility with Windows PowerShell and PowerShell Core, the best practice is to run tests for your module within both environments.</span></span>
> <span data-ttu-id="c2a26-141">Also run tests on Linux and macOS if your module is intended to be cross-platform.</span><span class="sxs-lookup"><span data-stu-id="c2a26-141">Also run tests on Linux and macOS if your module is intended to be cross-platform.</span></span>

<span data-ttu-id="c2a26-142">Targeting .NET Standard helps ensure that, as the module evolves, incompatible APIs don't accidentally get introduced into the module.</span><span class="sxs-lookup"><span data-stu-id="c2a26-142">Targeting .NET Standard helps ensure that, as the module evolves, incompatible APIs don't accidentally get introduced into the module.</span></span> <span data-ttu-id="c2a26-143">Incompatibilities are discovered at compile time instead of runtime.</span><span class="sxs-lookup"><span data-stu-id="c2a26-143">Incompatibilities are discovered at compile time instead of runtime.</span></span>

<span data-ttu-id="c2a26-144">However, it isn't required to target .NET Standard for a module to work with both Windows PowerShell and PowerShell Core, as long as you use compatible APIs.</span><span class="sxs-lookup"><span data-stu-id="c2a26-144">However, it isn't required to target .NET Standard for a module to work with both Windows PowerShell and PowerShell Core, as long as you use compatible APIs.</span></span> <span data-ttu-id="c2a26-145">The Intermediate Language (IL) is compatible between the two runtimes.</span><span class="sxs-lookup"><span data-stu-id="c2a26-145">The Intermediate Language (IL) is compatible between the two runtimes.</span></span> <span data-ttu-id="c2a26-146">You can target .NET Framework 4.6.1, which is compatible with .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="c2a26-146">You can target .NET Framework 4.6.1, which is compatible with .NET Standard 2.0.</span></span> <span data-ttu-id="c2a26-147">If you don't use APIs outside of .NET Standard 2.0, then your module works with PowerShell Core 6 without recompilation.</span><span class="sxs-lookup"><span data-stu-id="c2a26-147">If you don't use APIs outside of .NET Standard 2.0, then your module works with PowerShell Core 6 without recompilation.</span></span>

## <a name="powershell-standard-library"></a><span data-ttu-id="c2a26-148">PowerShell Standard Library</span><span class="sxs-lookup"><span data-stu-id="c2a26-148">PowerShell Standard Library</span></span>

<span data-ttu-id="c2a26-149">The [PowerShell Standard][] library is a formal specification of PowerShell APIs available in all PowerShell versions greater than or equal to the version of that standard.</span><span class="sxs-lookup"><span data-stu-id="c2a26-149">The [PowerShell Standard][] library is a formal specification of PowerShell APIs available in all PowerShell versions greater than or equal to the version of that standard.</span></span>

<span data-ttu-id="c2a26-150">For example, [PowerShell Standard 5.1][] is compatible with both Windows PowerShell 5.1 and PowerShell Core 6.0 or newer.</span><span class="sxs-lookup"><span data-stu-id="c2a26-150">For example, [PowerShell Standard 5.1][] is compatible with both Windows PowerShell 5.1 and PowerShell Core 6.0 or newer.</span></span>

<span data-ttu-id="c2a26-151">We recommend you compile your module using PowerShell Standard Library.</span><span class="sxs-lookup"><span data-stu-id="c2a26-151">We recommend you compile your module using PowerShell Standard Library.</span></span> <span data-ttu-id="c2a26-152">The library ensures the APIs are available and implemented in both Windows PowerShell and PowerShell Core 6.</span><span class="sxs-lookup"><span data-stu-id="c2a26-152">The library ensures the APIs are available and implemented in both Windows PowerShell and PowerShell Core 6.</span></span>
<span data-ttu-id="c2a26-153">PowerShell Standard is intended to always be forwards-compatible.</span><span class="sxs-lookup"><span data-stu-id="c2a26-153">PowerShell Standard is intended to always be forwards-compatible.</span></span> <span data-ttu-id="c2a26-154">A module built using PowerShell Standard Library 5.1 will always be compatible with future versions of PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c2a26-154">A module built using PowerShell Standard Library 5.1 will always be compatible with future versions of PowerShell.</span></span>

## <a name="module-manifest"></a><span data-ttu-id="c2a26-155">Module Manifest</span><span class="sxs-lookup"><span data-stu-id="c2a26-155">Module Manifest</span></span>

### <a name="indicating-compatibility-with-windows-powershell-and-powershell-core"></a><span data-ttu-id="c2a26-156">Indicating Compatibility With Windows PowerShell and PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="c2a26-156">Indicating Compatibility With Windows PowerShell and PowerShell Core</span></span>

<span data-ttu-id="c2a26-157">After validating that your module works with both Windows PowerShell and PowerShell Core, the module manifest should explicitly indicate compatibility by using the [CompatiblePSEditions][] property.</span><span class="sxs-lookup"><span data-stu-id="c2a26-157">After validating that your module works with both Windows PowerShell and PowerShell Core, the module manifest should explicitly indicate compatibility by using the [CompatiblePSEditions][] property.</span></span> <span data-ttu-id="c2a26-158">A value of `Desktop` means that the module is compatible with Windows PowerShell, while a value of `Core` means that the module is compatible with PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="c2a26-158">A value of `Desktop` means that the module is compatible with Windows PowerShell, while a value of `Core` means that the module is compatible with PowerShell Core.</span></span> <span data-ttu-id="c2a26-159">Including both `Desktop` and `Core` means that the module is compatible with both Windows PowerShell and PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="c2a26-159">Including both `Desktop` and `Core` means that the module is compatible with both Windows PowerShell and PowerShell Core.</span></span>

> [!NOTE]
> <span data-ttu-id="c2a26-160">`Core` does not automatically mean that the module is compatible with Windows, Linux, and macOS.</span><span class="sxs-lookup"><span data-stu-id="c2a26-160">`Core` does not automatically mean that the module is compatible with Windows, Linux, and macOS.</span></span>
> <span data-ttu-id="c2a26-161">The **CompatiblePSEditions** property was introduced in PowerShell v5.</span><span class="sxs-lookup"><span data-stu-id="c2a26-161">The **CompatiblePSEditions** property was introduced in PowerShell v5.</span></span> <span data-ttu-id="c2a26-162">Module manifests that use the **CompatiblePSEditions** property fail to load in versions prior to PowerShell v5.</span><span class="sxs-lookup"><span data-stu-id="c2a26-162">Module manifests that use the **CompatiblePSEditions** property fail to load in versions prior to PowerShell v5.</span></span>

### <a name="indicating-os-compatibility"></a><span data-ttu-id="c2a26-163">Indicating OS Compatibility</span><span class="sxs-lookup"><span data-stu-id="c2a26-163">Indicating OS Compatibility</span></span>

<span data-ttu-id="c2a26-164">First, validate that your module works on Linux and macOS.</span><span class="sxs-lookup"><span data-stu-id="c2a26-164">First, validate that your module works on Linux and macOS.</span></span> <span data-ttu-id="c2a26-165">Next, indicate compatibility with those operating systems in the module manifest.</span><span class="sxs-lookup"><span data-stu-id="c2a26-165">Next, indicate compatibility with those operating systems in the module manifest.</span></span> <span data-ttu-id="c2a26-166">This makes it easier for users to find your module for their operating system when published to the [PowerShell Gallery][].</span><span class="sxs-lookup"><span data-stu-id="c2a26-166">This makes it easier for users to find your module for their operating system when published to the [PowerShell Gallery][].</span></span>

<span data-ttu-id="c2a26-167">Within the module manifest, the `PrivateData` property has a `PSData` sub-property.</span><span class="sxs-lookup"><span data-stu-id="c2a26-167">Within the module manifest, the `PrivateData` property has a `PSData` sub-property.</span></span> <span data-ttu-id="c2a26-168">The optional `Tags` property of `PSData` takes an array of values that show up in PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="c2a26-168">The optional `Tags` property of `PSData` takes an array of values that show up in PowerShell Gallery.</span></span> <span data-ttu-id="c2a26-169">The PowerShell Gallery supports the following compatibility values:</span><span class="sxs-lookup"><span data-stu-id="c2a26-169">The PowerShell Gallery supports the following compatibility values:</span></span>

| <span data-ttu-id="c2a26-170">Tagg</span><span class="sxs-lookup"><span data-stu-id="c2a26-170">Tag</span></span>               | <span data-ttu-id="c2a26-171">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c2a26-171">Description</span></span>                                |
|-------------------|--------------------------------------------|
| <span data-ttu-id="c2a26-172">PSEdition_Core</span><span class="sxs-lookup"><span data-stu-id="c2a26-172">PSEdition_Core</span></span>    | <span data-ttu-id="c2a26-173">Compatible with PowerShell Core 6</span><span class="sxs-lookup"><span data-stu-id="c2a26-173">Compatible with PowerShell Core 6</span></span>          |
| <span data-ttu-id="c2a26-174">PSEdition_Desktop</span><span class="sxs-lookup"><span data-stu-id="c2a26-174">PSEdition_Desktop</span></span> | <span data-ttu-id="c2a26-175">Compatible with Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c2a26-175">Compatible with Windows PowerShell</span></span>         |
| <span data-ttu-id="c2a26-176">Windows</span><span class="sxs-lookup"><span data-stu-id="c2a26-176">Windows</span></span>           | <span data-ttu-id="c2a26-177">Compatible with Windows</span><span class="sxs-lookup"><span data-stu-id="c2a26-177">Compatible with Windows</span></span>                    |
| <span data-ttu-id="c2a26-178">Linux</span><span class="sxs-lookup"><span data-stu-id="c2a26-178">Linux</span></span>             | <span data-ttu-id="c2a26-179">Compatible with Linux (no specific distro)</span><span class="sxs-lookup"><span data-stu-id="c2a26-179">Compatible with Linux (no specific distro)</span></span> |
| <span data-ttu-id="c2a26-180">macOS</span><span class="sxs-lookup"><span data-stu-id="c2a26-180">macOS</span></span>             | <span data-ttu-id="c2a26-181">Compatible with macOS</span><span class="sxs-lookup"><span data-stu-id="c2a26-181">Compatible with macOS</span></span>                      |

<span data-ttu-id="c2a26-182">Exempel:</span><span class="sxs-lookup"><span data-stu-id="c2a26-182">Example:</span></span>

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
[.NET Framework]: /dotnet/framework/
[.NET Core]: /dotnet/core/
[PSSnapIn]: /dotnet/api/system.management.automation.pssnapin
[New-ModuleManifest]: /powershell/module/microsoft.powershell.core/new-modulemanifest
[runtime checks]: /dotnet/api/system.runtime.interopservices.runtimeinformation.frameworkdescription#System_Runtime_InteropServices_RuntimeInformation_FrameworkDescription
[.NET CLI]: /dotnet/core/tools/?tabs=netcore2x
[.NET Standard]: /dotnet/standard/net-standard
[PowerShell Standard]: https://github.com/PowerShell/PowerShellStandard
[PowerShell Standard 5.1]: https://www.nuget.org/packages/PowerShellStandard.Library/5.1.0
[PowerShell Gallery]: https://www.powershellgallery.com
[.NET Portability Analyzer]: https://github.com/Microsoft/dotnet-apiport
[CompatiblePSEditions]: /powershell/scripting/gallery/concepts/module-psedition-support
