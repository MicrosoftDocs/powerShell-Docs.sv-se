---
title: Skapa en binär standard biblioteks-modul
description: Med PowerShell-standardbiblioteket kan vi skapa moduler för flera plattformar som fungerar både i PowerShell Core och med Windows PowerShell 5,1.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: ff6a49f70a3fb77f5a30cc909d53bb77b3cd7d43
ms.sourcegitcommit: 8c01e56f0c10ff2637955dc892ea78432d563a7b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/21/2020
ms.locfileid: "88702753"
---
# <a name="how-to-create-a-standard-library-binary-module"></a><span data-ttu-id="515c1-103">Såhär skapar du en binär modul för standardbibliotek</span><span class="sxs-lookup"><span data-stu-id="515c1-103">How to create a Standard Library binary module</span></span>

<span data-ttu-id="515c1-104">Jag hade nyligen en idé för modulen som jag ville implementera som en binär modul.</span><span class="sxs-lookup"><span data-stu-id="515c1-104">I recently had an idea for module that I wanted to implement as a binary module.</span></span> <span data-ttu-id="515c1-105">Jag har ännu inte skapat en med hjälp av [PowerShell-standardbiblioteket][] , så det här är en bra möjlighet.</span><span class="sxs-lookup"><span data-stu-id="515c1-105">I have yet to create one using the [PowerShell Standard Library][] so this felt like a good opportunity.</span></span> <span data-ttu-id="515c1-106">Jag använde guiden [skapa en plattforms oberoende binär modul][] för att skapa den här modulen utan någon hindren.</span><span class="sxs-lookup"><span data-stu-id="515c1-106">I used the [Creating a cross-platform binary module][] guide to create this module without any roadblocks.</span></span>
<span data-ttu-id="515c1-107">Vi ska gå vidare till samma process och lägga till en lite extra kommentarer på vägen.</span><span class="sxs-lookup"><span data-stu-id="515c1-107">We're going to walk that same process and I'll add a little extra commentary along the way.</span></span>

> [!NOTE]
> <span data-ttu-id="515c1-108">Den [ursprungliga versionen][] av den här artikeln visas på bloggen som skrivits av [@KevinMarquette][] .</span><span class="sxs-lookup"><span data-stu-id="515c1-108">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="515c1-109">PowerShell-teamet tackar för att dela det här innehållet med oss.</span><span class="sxs-lookup"><span data-stu-id="515c1-109">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="515c1-110">Ta en titt på hans blogg på [PowerShellExplained.com][].</span><span class="sxs-lookup"><span data-stu-id="515c1-110">Please check out his blog at [PowerShellExplained.com][].</span></span>

## <a name="what-is-the-powershell-standard-library"></a><span data-ttu-id="515c1-111">Vad är PowerShell standard library?</span><span class="sxs-lookup"><span data-stu-id="515c1-111">What is the PowerShell Standard Library?</span></span>

<span data-ttu-id="515c1-112">Med PowerShell-standardbiblioteket kan vi skapa moduler för flera plattformar som fungerar både i PowerShell Core och med Windows PowerShell 5,1 (eller 3,0).</span><span class="sxs-lookup"><span data-stu-id="515c1-112">The PowerShell Standard Library allows us to create cross platform modules that work in both PowerShell Core and with Windows PowerShell 5.1 (or 3.0).</span></span>

## <a name="planning-our-module"></a><span data-ttu-id="515c1-113">Planera vår modul</span><span class="sxs-lookup"><span data-stu-id="515c1-113">Planning our module</span></span>

<span data-ttu-id="515c1-114">Planen för den här modulen är att skapa en `src` mapp för C#-koden och strukturera resten på samma sätt som för en-skript-modul.</span><span class="sxs-lookup"><span data-stu-id="515c1-114">The plan for this module is to create a `src` folder for the C# code and structure the rest like I would for a script module.</span></span> <span data-ttu-id="515c1-115">Detta omfattar att använda ett build-skript för att kompilera allt i en `output` mapp.</span><span class="sxs-lookup"><span data-stu-id="515c1-115">This includes using a build script to compile everything into an `output` folder.</span></span> <span data-ttu-id="515c1-116">Mappstrukturen ser ut så här:</span><span class="sxs-lookup"><span data-stu-id="515c1-116">The folder structure looks like this:</span></span>

```
MyModule
├───src
├───Output
│   └───MyModule
├───MyModule
│   ├───Data
│   ├───Private
│   └───Public
└───Tests
```

## <a name="getting-started"></a><span data-ttu-id="515c1-117">Komma igång</span><span class="sxs-lookup"><span data-stu-id="515c1-117">Getting Started</span></span>

<span data-ttu-id="515c1-118">Jag använder normalt en gips-mall, men min aktuella mall har inte stöd för binär modul än.</span><span class="sxs-lookup"><span data-stu-id="515c1-118">I normally use a Plaster template but my current template doesn't have any binary module support yet.</span></span> <span data-ttu-id="515c1-119">Inte ett stort avtal.</span><span class="sxs-lookup"><span data-stu-id="515c1-119">Not a big deal.</span></span> <span data-ttu-id="515c1-120">Jag skapar den här gången för tillfället.</span><span class="sxs-lookup"><span data-stu-id="515c1-120">I'll create this one by hand this time.</span></span>

<span data-ttu-id="515c1-121">Först måste jag skapa mappen och skapa git-lagrings platsen.</span><span class="sxs-lookup"><span data-stu-id="515c1-121">First I need to create the folder and create the git repo.</span></span> <span data-ttu-id="515c1-122">Jag använder `$module` som plats hållare för modulnamnet.</span><span class="sxs-lookup"><span data-stu-id="515c1-122">I'm using `$module` as a placeholder for the module name.</span></span> <span data-ttu-id="515c1-123">Detta gör det enklare för dig att återanvända dessa exempel vid behov.</span><span class="sxs-lookup"><span data-stu-id="515c1-123">This should make it easier for you to reuse these examples if needed.</span></span>

```powershell
$module = 'MyModule'
New-Item -Path $module -Type Directory
Set-Location $module
git init
```

<span data-ttu-id="515c1-124">Skapa sedan rot nivåns mappar.</span><span class="sxs-lookup"><span data-stu-id="515c1-124">Then create the root level folders.</span></span>

```powershell
New-Item -Path 'src' -Type Directory
New-Item -Path 'Output' -Type Directory
New-Item -Path 'Tests' -Type Directory
New-Item -Path $module -Type Directory
```

### <a name="binary-module-setup"></a><span data-ttu-id="515c1-125">Installation av binär modul</span><span class="sxs-lookup"><span data-stu-id="515c1-125">Binary module setup</span></span>

<span data-ttu-id="515c1-126">Artikeln OS fokuserar på den binära modulen så att vi startar.</span><span class="sxs-lookup"><span data-stu-id="515c1-126">This article os focused on the binary module so that is where we'll start.</span></span> <span data-ttu-id="515c1-127">Det här avsnittet hämtar exempel från guiden [skapa en binär plattforms oberoende modul][] .</span><span class="sxs-lookup"><span data-stu-id="515c1-127">This section pulls examples from the [Creating a cross-platform binary module][] guide.</span></span> <span data-ttu-id="515c1-128">Läs den här guiden om du behöver mer information eller om du har problem.</span><span class="sxs-lookup"><span data-stu-id="515c1-128">Review that guide if you need more details or have any issues.</span></span>

<span data-ttu-id="515c1-129">Det första du vill göra är att kontrol lera vilken version av [dotNet Core SDK][] som vi har installerat.</span><span class="sxs-lookup"><span data-stu-id="515c1-129">First thing we want to do is check the version of the [dotnet core SDK][] that we installed.</span></span> <span data-ttu-id="515c1-130">Jag använder 2.1.4, men du bör ha 2.0.0 eller senare innan du fortsätter.</span><span class="sxs-lookup"><span data-stu-id="515c1-130">I'm using 2.1.4, but you should have 2.0.0 or newer before continuing.</span></span>

```powershell
PS> dotnet --version
2.1.4
```

<span data-ttu-id="515c1-131">Jag arbetar i `src` mappen för det här avsnittet.</span><span class="sxs-lookup"><span data-stu-id="515c1-131">I'm working out of the `src` folder for this section.</span></span>

```powershell
Set-Location 'src'
```

<span data-ttu-id="515c1-132">Skapa ett nytt klass bibliotek med kommandot dotNet.</span><span class="sxs-lookup"><span data-stu-id="515c1-132">Using the dotnet command, create a new class library.</span></span>

```powershell
dotnet new classlib --name $module
```

<span data-ttu-id="515c1-133">Detta skapade biblioteks projektet i en undermapp men jag vill inte ha den extra kapslings nivån.</span><span class="sxs-lookup"><span data-stu-id="515c1-133">This created the library project in a subfolder but I don't want that extra level of nesting.</span></span> <span data-ttu-id="515c1-134">Jag ska flytta filerna uppåt en nivå.</span><span class="sxs-lookup"><span data-stu-id="515c1-134">I'm going to move those files up a level.</span></span>

```powershell
Move-Item -Path .\$module\* -Destination .\
Remove-Item $module -Recurse
```

<span data-ttu-id="515c1-135">Ange .NET Core SDK-versionen för projektet.</span><span class="sxs-lookup"><span data-stu-id="515c1-135">Set the .NET core SDK version for the project.</span></span> <span data-ttu-id="515c1-136">Jag har 2,1 SDK så jag ska ange 2.1.0.</span><span class="sxs-lookup"><span data-stu-id="515c1-136">I have the 2.1 SDK so I'm going to specify 2.1.0.</span></span>
<span data-ttu-id="515c1-137">Använd 2.0.0 om du använder 2,0 SDK: n.</span><span class="sxs-lookup"><span data-stu-id="515c1-137">Use 2.0.0 if you're using the 2.0 SDK.</span></span>

```powershell
dotnet new globaljson --sdk-version 2.1.0
```

<span data-ttu-id="515c1-138">Lägg till PowerShell- [NuGet-paketet][] för standard bibliotek i projektet.</span><span class="sxs-lookup"><span data-stu-id="515c1-138">Add the PowerShell Standard Library [NuGet package][] to the project.</span></span> <span data-ttu-id="515c1-139">Se till att du använder den senaste versionen som är tillgänglig för den kompatibilitetsnivå du behöver.</span><span class="sxs-lookup"><span data-stu-id="515c1-139">Make sure you use the most recent version available for the level of compatibility that you need.</span></span> <span data-ttu-id="515c1-140">Jag skulle använda den senaste versionen som standard, men jag tycker inte att den här modulen använder några funktioner som är nyare än PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="515c1-140">I would default to the latest version but I don't think this module leverages any features newer than PowerShell 3.0.</span></span>

```powershell
dotnet add package PowerShellStandard.Library --version 7.0.0-preview.1
```

<span data-ttu-id="515c1-141">Vi bör ha en src-mapp som ser ut så här:</span><span class="sxs-lookup"><span data-stu-id="515c1-141">We should have a src folder that looks like this:</span></span>

```powershell
PS> Get-ChildItem
    Directory: \MyModule\src

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        7/14/2018   9:51 PM                obj
-a----        7/14/2018   9:51 PM             86 Class1.cs
-a----        7/14/2018  10:03 PM            259 MyModule.csproj
-a----        7/14/2018  10:05 PM             45 global.json
```

<span data-ttu-id="515c1-142">Nu är vi redo att lägga till vår egen kod i projektet.</span><span class="sxs-lookup"><span data-stu-id="515c1-142">Now we're ready to add our own code to the project.</span></span>

### <a name="building-a-binary-cmdlet"></a><span data-ttu-id="515c1-143">Skapa en binär cmdlet</span><span class="sxs-lookup"><span data-stu-id="515c1-143">Building a binary cmdlet</span></span>

<span data-ttu-id="515c1-144">Vi måste uppdatera `src\Class1.cs` för att innehålla denna start-cmdlet:</span><span class="sxs-lookup"><span data-stu-id="515c1-144">We need to update the `src\Class1.cs` to contain this starter cmdlet:</span></span>

```csharp
using System;
using System.Management.Automation;

namespace MyModule
{
    [Cmdlet( VerbsDiagnostic.Resolve , "MyCmdlet")]
    public class ResolveMyCmdletCommand : PSCmdlet
    {
        [Parameter(Position=0)]
        public Object InputObject { get; set; }

        protected override void EndProcessing()
        {
            this.WriteObject(this.InputObject);
            base.EndProcessing();
        }
    }
}
```

<span data-ttu-id="515c1-145">Byt namn på filen så att den matchar klass namnet.</span><span class="sxs-lookup"><span data-stu-id="515c1-145">Rename the file to match the class name.</span></span>

```powershell
Rename-Item .\Class1.cs .\ResolveMyCmdletCommand.cs
```

<span data-ttu-id="515c1-146">Sedan kan vi bygga vår modul.</span><span class="sxs-lookup"><span data-stu-id="515c1-146">Then we can build our module.</span></span>

```powershell
PS> dotnet build

Microsoft (R) Build Engine version 15.5.180.51428 for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

Restore completed in 18.19 ms for C:\workspace\MyModule\src\MyModule.csproj.
MyModule -> C:\workspace\MyModule\src\bin\Debug\netstandard2.0\MyModule.dll

Build succeeded.
    0 Warning(s)
    0 Error(s)

Time Elapsed 00:00:02.19
```

<span data-ttu-id="515c1-147">Vi kan anropa `Import-Module` den nya DLL-filen för att läsa in vår nya CMDlet.</span><span class="sxs-lookup"><span data-stu-id="515c1-147">We can call `Import-Module` on the new dll to load our new CMDlet.</span></span>

```powershell
PS> Import-Module .\bin\Debug\netstandard2.0\$module.dll
PS> Get-Command -Module $module

CommandType Name                    Version Source
----------- ----                    ------- ------
Cmdlet      Resolve-MyCmdlet        1.0.0.0 MyModule
```

<span data-ttu-id="515c1-148">Om importen Miss lyckas på systemet kan du prova att uppdatera .NET till 4.7.1 eller senare.</span><span class="sxs-lookup"><span data-stu-id="515c1-148">If the import fails on your system, try updating .NET to 4.7.1 or newer.</span></span> <span data-ttu-id="515c1-149">Guiden [skapa en binär plattforms oberoende modul][] innehåller mer information om .net-support och kompatibilitet för äldre versioner av .net.</span><span class="sxs-lookup"><span data-stu-id="515c1-149">The [Creating a cross-platform binary module][] guide goes into more details on .NET support and compatibility for older versions of .NET.</span></span>

### <a name="module-manifest"></a><span data-ttu-id="515c1-150">Modul manifest</span><span class="sxs-lookup"><span data-stu-id="515c1-150">Module manifest</span></span>

<span data-ttu-id="515c1-151">Det är bra att vi kan importera DLL-filen och ha en fungerande modul.</span><span class="sxs-lookup"><span data-stu-id="515c1-151">It's cool that we can import the dll and have a working module.</span></span> <span data-ttu-id="515c1-152">Jag vill fortsätta med den och skapa ett modul manifest.</span><span class="sxs-lookup"><span data-stu-id="515c1-152">I like to keep going with it and create a module manifest.</span></span> <span data-ttu-id="515c1-153">Vi behöver manifestet om vi vill publicera till PSGallery senare.</span><span class="sxs-lookup"><span data-stu-id="515c1-153">We need the manifest if we want to publish to the PSGallery later.</span></span>

<span data-ttu-id="515c1-154">Från roten av vårt projekt kan vi köra det här kommandot för att skapa modulens manifest som vi behöver.</span><span class="sxs-lookup"><span data-stu-id="515c1-154">From the root of our project, we can run this command to create the module manifest that we need.</span></span>

```powershell
$manifestSplat = @{
    Path              = ".\$module\$module.psd1"
    Author            = 'Kevin Marquette'
    NestedModules     = @('bin\MyModule.dll')
    RootModule        = "$module.psm1"
    FunctionsToExport = @('Resolve-MyCmdlet')
}
New-ModuleManifest @manifestSplat
```

<span data-ttu-id="515c1-155">Jag ska också skapa en tom modul för framtida PowerShell-funktioner.</span><span class="sxs-lookup"><span data-stu-id="515c1-155">I'm also going to create an empty root module for future PowerShell functions.</span></span>

```powershell
Set-Content -Value '' -Path ".\$module\$module.psm1"
```

<span data-ttu-id="515c1-156">Detta gör att jag kan blanda både normala PowerShell-funktioner och binära cmdlets i samma projekt.</span><span class="sxs-lookup"><span data-stu-id="515c1-156">This allows me to mix both normal PowerShell functions and binary Cmdlets in the same project.</span></span>

### <a name="building-the-full-module"></a><span data-ttu-id="515c1-157">Skapa hela modulen</span><span class="sxs-lookup"><span data-stu-id="515c1-157">Building the full module</span></span>

<span data-ttu-id="515c1-158">Jag kompilerar allt tillsammans i en mapp för utdata.</span><span class="sxs-lookup"><span data-stu-id="515c1-158">I compile everything together into an output folder.</span></span> <span data-ttu-id="515c1-159">Vi behöver skapa ett build-skript för att göra det.</span><span class="sxs-lookup"><span data-stu-id="515c1-159">We need to create a build script to do that.</span></span> <span data-ttu-id="515c1-160">Jag lägger normalt till detta i ett `Invoke-Build` skript, men vi kan hålla det enkelt för det här exemplet.</span><span class="sxs-lookup"><span data-stu-id="515c1-160">I would normally add this to an `Invoke-Build` script, but we can keep it simple for this example.</span></span> <span data-ttu-id="515c1-161">Lägg till detta i en `build.ps1` rot i projektet.</span><span class="sxs-lookup"><span data-stu-id="515c1-161">Add this to a `build.ps1` at the root of the project.</span></span>

```powershell
$module = 'MyModule'
Push-Location $PSScriptRoot

dotnet build $PSScriptRoot\src -o $PSScriptRoot\output\$module\bin
Copy-Item "$PSScriptRoot\$module\*" "$PSScriptRoot\output\$module" -Recurse -Force

Import-Module "$PSScriptRoot\Output\$module\$module.psd1"
Invoke-Pester "$PSScriptRoot\Tests"
```

<span data-ttu-id="515c1-162">Dessa kommandon skapar vår DLL och placerar den i vår `output\$module\bin` mapp.</span><span class="sxs-lookup"><span data-stu-id="515c1-162">These commands build our DLL and place it into our `output\$module\bin` folder.</span></span> <span data-ttu-id="515c1-163">Den kopierar sedan de andra modulens filer till plats.</span><span class="sxs-lookup"><span data-stu-id="515c1-163">It then copies the other module files into place.</span></span>

```
Output
└───MyModule
    │   MyModule.psd1
    │   MyModule.psm1
    │
    └───bin
            MyModule.deps.json
            MyModule.dll
            MyModule.pdb
```

<span data-ttu-id="515c1-164">Vi kan nu importera vår modul med psd1-filen.</span><span class="sxs-lookup"><span data-stu-id="515c1-164">At this point, we can import our module with the psd1 file.</span></span>

```powershell
Import-Module ".\Output\$module\$module.psd1"
```

<span data-ttu-id="515c1-165">Härifrån kan vi släppa `.\Output\$module` mappen i vår `$env:PSModulePath` katalog så laddar den automatiskt in vårt kommando när vi behöver det.</span><span class="sxs-lookup"><span data-stu-id="515c1-165">From here, we can drop the `.\Output\$module` folder into our `$env:PSModulePath` directory and it autoloads our command whenever we need it.</span></span>

### <a name="update-dotnet-new-psmodule"></a><span data-ttu-id="515c1-166">Uppdatera: dotNet New PSModule</span><span class="sxs-lookup"><span data-stu-id="515c1-166">Update: dotnet new PSModule</span></span>

<span data-ttu-id="515c1-167">Jag har lärt dig att `dotnet` verktyget har en `PSModule` mall.</span><span class="sxs-lookup"><span data-stu-id="515c1-167">I learned that the `dotnet` tool has a `PSModule` template.</span></span>

<span data-ttu-id="515c1-168">Alla steg som beskrivs ovan är fortfarande giltiga, men den här mallen delar ut många av dem. Det är fortfarande en ganska ny mall som fortfarande kommer att få lite polska att placeras på den.</span><span class="sxs-lookup"><span data-stu-id="515c1-168">All the steps that I outlined above are still valid, but this template cuts many of them out. It's still a fairly new template that is still getting some polish placed on it.</span></span> <span data-ttu-id="515c1-169">Det kan vara bättre att komma igång.</span><span class="sxs-lookup"><span data-stu-id="515c1-169">Expect it to keep getting better from here.</span></span>

<span data-ttu-id="515c1-170">Så här använder du installera och använder PSModule-mallen.</span><span class="sxs-lookup"><span data-stu-id="515c1-170">This is how you use install and use the PSModule template.</span></span>

```powershell
dotnet new -i Microsoft.PowerShell.Standard.Module.Template
dotnet new psmodule
dotnet build
Import-Module "bin\Debug\netstandard2.0\$module.dll"
Get-Module $module
```

<span data-ttu-id="515c1-171">Den här minimala mallen tar hand om att lägga till .NET SDK, PowerShell standard-biblioteket och skapar en exempel klass i projektet.</span><span class="sxs-lookup"><span data-stu-id="515c1-171">This minimally-viable template takes care of adding the .NET SDK, PowerShell Standard Library, and creates an example class in the project.</span></span> <span data-ttu-id="515c1-172">Du kan skapa den och köra den direkt.</span><span class="sxs-lookup"><span data-stu-id="515c1-172">You can build it and run it right away.</span></span>

## <a name="important-details"></a><span data-ttu-id="515c1-173">Viktig information</span><span class="sxs-lookup"><span data-stu-id="515c1-173">Important details</span></span>

<span data-ttu-id="515c1-174">Innan vi slutför den här artikeln är här några andra detaljer som är värda att nämna.</span><span class="sxs-lookup"><span data-stu-id="515c1-174">Before we end this article, here are a few other details worth mentioning.</span></span>

### <a name="unloading-dlls"></a><span data-ttu-id="515c1-175">Laddar bort dll: er</span><span class="sxs-lookup"><span data-stu-id="515c1-175">Unloading DLLs</span></span>

<span data-ttu-id="515c1-176">När en binär modul har lästs in kan du verkligen ta bort den.</span><span class="sxs-lookup"><span data-stu-id="515c1-176">Once a binary module is loaded, you can't really unload it.</span></span> <span data-ttu-id="515c1-177">DLL-filen är låst tills du tar bort den.</span><span class="sxs-lookup"><span data-stu-id="515c1-177">The DLL file is locked until you unload it.</span></span> <span data-ttu-id="515c1-178">Detta kan vara irriterande när du utvecklar eftersom varje gång du gör en ändring och vill skapa den, är filen ofta låst.</span><span class="sxs-lookup"><span data-stu-id="515c1-178">This can be annoying when developing because every time you make a change and want to build it, the file is often locked.</span></span> <span data-ttu-id="515c1-179">Det enda pålitliga sättet att lösa detta är att stänga PowerShell-sessionen som laddade DLL-filen.</span><span class="sxs-lookup"><span data-stu-id="515c1-179">The only reliable way to resolve this is to close the PowerShell session that loaded the DLL.</span></span>

### <a name="vs-code-reload-window-action"></a><span data-ttu-id="515c1-180">VS Code Omladdnings fönster åtgärd</span><span class="sxs-lookup"><span data-stu-id="515c1-180">VS Code reload window action</span></span>

<span data-ttu-id="515c1-181">Jag gör det mesta av min PowerShell-dev i [vs Code][].</span><span class="sxs-lookup"><span data-stu-id="515c1-181">I do most of my PowerShell dev work in [VS Code][].</span></span> <span data-ttu-id="515c1-182">När jag arbetar med en binär modul (eller en modul med klasser) har jag fått till gång till att läsa in VS Code varje gång jag skapar.</span><span class="sxs-lookup"><span data-stu-id="515c1-182">When I'm working on a binary module (or a module with classes), I've gotten into the habit of reloading VS Code every time I build.</span></span>
<span data-ttu-id="515c1-183"><kbd>CTRL</kbd> + <kbd>Shift</kbd> + <kbd>P</kbd> pop-kommando fönstret och `Reload Window` är alltid överst i listan.</span><span class="sxs-lookup"><span data-stu-id="515c1-183"><kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> pops the command window and `Reload Window` is always at the top of my list.</span></span>

### <a name="nested-powershell-sessions"></a><span data-ttu-id="515c1-184">Kapslade PowerShell-sessioner</span><span class="sxs-lookup"><span data-stu-id="515c1-184">Nested PowerShell sessions</span></span>

<span data-ttu-id="515c1-185">Ett annat alternativ är att ha en lämplig pester test täckning.</span><span class="sxs-lookup"><span data-stu-id="515c1-185">One other option is to have good Pester test coverage.</span></span> <span data-ttu-id="515c1-186">Sedan kan du justera build.ps1-skriptet för att starta en ny PowerShell-session, utföra bygget, köra testerna och stänga sessionen.</span><span class="sxs-lookup"><span data-stu-id="515c1-186">Then you can adjust the build.ps1 script to start a new PowerShell session, perform the build, run the tests, and close the session.</span></span>

### <a name="updating-installed-modules"></a><span data-ttu-id="515c1-187">Uppdaterar installerade moduler</span><span class="sxs-lookup"><span data-stu-id="515c1-187">Updating installed modules</span></span>

<span data-ttu-id="515c1-188">Den här låsningen kan vara irriterande vid försök att uppdatera den lokalt installerade modulen.</span><span class="sxs-lookup"><span data-stu-id="515c1-188">This locking can be annoying when trying to update your locally installed module.</span></span> <span data-ttu-id="515c1-189">Om en session har lästs in måste du leta efter den och stänga den.</span><span class="sxs-lookup"><span data-stu-id="515c1-189">If any session has it loaded, you have to go hunt it down and close it.</span></span> <span data-ttu-id="515c1-190">Detta är mindre av ett problem när du installerar från en PSGallery eftersom en modul version placerar den nya i en annan mapp.</span><span class="sxs-lookup"><span data-stu-id="515c1-190">This is less of an issue when installing from a PSGallery because module versioning places the new one in a different folder.</span></span>

<span data-ttu-id="515c1-191">Du kan konfigurera en lokal PSGallery och publicera den som en del av din version.</span><span class="sxs-lookup"><span data-stu-id="515c1-191">You can set up a local PSGallery and publish to that as part of your build.</span></span> <span data-ttu-id="515c1-192">Gör sedan din lokala installation från den PSGallery.</span><span class="sxs-lookup"><span data-stu-id="515c1-192">Then do your local install from that PSGallery.</span></span> <span data-ttu-id="515c1-193">Detta låter till exempel mycket arbete, men det kan vara lika enkelt som att starta en Docker-behållare.</span><span class="sxs-lookup"><span data-stu-id="515c1-193">This sounds like a lot of work, but this can be as simple as starting a docker container.</span></span> <span data-ttu-id="515c1-194">Jag får ett sätt att göra det i mitt inlägg på att [använda en NuGet-Server för en PSRepository][].</span><span class="sxs-lookup"><span data-stu-id="515c1-194">I cover a way to do that in my post on [Using a NuGet server for a PSRepository][].</span></span>

## <a name="why-binary-modules"></a><span data-ttu-id="515c1-195">Varför binära moduler?</span><span class="sxs-lookup"><span data-stu-id="515c1-195">Why binary modules?</span></span>

<span data-ttu-id="515c1-196">Jag har direkt till gång till hur man skapar en binär modul och inte ville säga varför du vill skapa en.</span><span class="sxs-lookup"><span data-stu-id="515c1-196">I jumped right into how to make a binary module and didn't mention why you want to make one.</span></span> <span data-ttu-id="515c1-197">I verkligheten skriver du C# och ger enkel åtkomst till PowerShell-cmdlets och functions.</span><span class="sxs-lookup"><span data-stu-id="515c1-197">In reality, you are writing C# and give up easy access to PowerShell Cmdlets and functions.</span></span> <span data-ttu-id="515c1-198">Det är den viktigaste anledningen till varför jag inte har växlat till de binära modulerna tidigare.</span><span class="sxs-lookup"><span data-stu-id="515c1-198">That is the main reason why I have not shifted to binary modules sooner.</span></span>

<span data-ttu-id="515c1-199">Men om du skapar en modul som inte är beroende av många andra PowerShell-kommandon kan prestanda förmånen vara betydande.</span><span class="sxs-lookup"><span data-stu-id="515c1-199">But if you are creating a module that doesn't depend on a lot of other PowerShell commands, the performance benefit can be significant.</span></span> <span data-ttu-id="515c1-200">Genom att släppa i C# får du till gång till den extra kostnad som har lagts till av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="515c1-200">By dropping into C#, you get to shed the overhead added by PowerShell.</span></span> <span data-ttu-id="515c1-201">PowerShell optimerades för administratören, inte på datorn, och det lägger till en lite extra kostnad.</span><span class="sxs-lookup"><span data-stu-id="515c1-201">PowerShell was optimized for the administrator, not the computer, and that adds a little overhead.</span></span>

<span data-ttu-id="515c1-202">På arbetet har vi en kritisk process som gör mycket arbete med JSON och hash.</span><span class="sxs-lookup"><span data-stu-id="515c1-202">At work, we have a critical process that does a lot of work with JSON and Hashtables.</span></span> <span data-ttu-id="515c1-203">Vi optimerade PowerShell så mycket som vi kunde, men den här processen kördes fortfarande i 12 minuter.</span><span class="sxs-lookup"><span data-stu-id="515c1-203">We optimized the PowerShell as much as we could but this process was still running for 12 minutes.</span></span> <span data-ttu-id="515c1-204">Modulen innehåller redan en mängd C#-format PowerShell.</span><span class="sxs-lookup"><span data-stu-id="515c1-204">The module already contained a lot of C# style PowerShell.</span></span> <span data-ttu-id="515c1-205">Detta gjorde konverteringen till en binär modul ren och lätt att göra.</span><span class="sxs-lookup"><span data-stu-id="515c1-205">This made the conversion to a binary module clean and easy to do.</span></span> <span data-ttu-id="515c1-206">Vår konvertering klipper ut från över 12 minuter till under fyra minuter.</span><span class="sxs-lookup"><span data-stu-id="515c1-206">Our conversion cut that process down from over 12 minutes to under four minutes.</span></span>

### <a name="hybrid-modules"></a><span data-ttu-id="515c1-207">Hybrid moduler</span><span class="sxs-lookup"><span data-stu-id="515c1-207">Hybrid modules</span></span>

<span data-ttu-id="515c1-208">Du kan blanda binära cmdletar med avancerade PowerShell-funktioner.</span><span class="sxs-lookup"><span data-stu-id="515c1-208">You can mix binary Cmdlets with PowerShell advanced functions.</span></span> <span data-ttu-id="515c1-209">Det är precis vad jag gör i den här guiden.</span><span class="sxs-lookup"><span data-stu-id="515c1-209">That is exactly what I'm doing in this guide.</span></span> <span data-ttu-id="515c1-210">Du kan ta allt du känner till om skript moduler och allt används på samma sätt.</span><span class="sxs-lookup"><span data-stu-id="515c1-210">You can take everything you know about script modules and it all applies the same way.</span></span>
<span data-ttu-id="515c1-211">Den tomma `psm1` filen som jag skapade idag finns bara så att du kan släppa andra PowerShell-funktioner senare.</span><span class="sxs-lookup"><span data-stu-id="515c1-211">The empty `psm1` file that I created today is there just so you can drop in other PowerShell functions later.</span></span>

<span data-ttu-id="515c1-212">Nästan alla kompilerade cmdlets som vi skapade startade som en PowerShell-funktion först.</span><span class="sxs-lookup"><span data-stu-id="515c1-212">Almost all of the compiled cmdlets that we created started out as a PowerShell function first.</span></span> <span data-ttu-id="515c1-213">Alla våra binära moduler är i själva verket hybrid moduler.</span><span class="sxs-lookup"><span data-stu-id="515c1-213">All of our binary modules are really hybrid modules.</span></span>

### <a name="build-scripts"></a><span data-ttu-id="515c1-214">Bygg skript</span><span class="sxs-lookup"><span data-stu-id="515c1-214">Build scripts</span></span>

<span data-ttu-id="515c1-215">Jag har bevarat Bygg skriptet enkelt här.</span><span class="sxs-lookup"><span data-stu-id="515c1-215">I kept the build script simple here.</span></span> <span data-ttu-id="515c1-216">Jag använder vanligt vis ett stort `Invoke-Build` skript som en del av min CI/CD-pipeline.</span><span class="sxs-lookup"><span data-stu-id="515c1-216">I generally use a large `Invoke-Build` script as part of my CI/CD pipeline.</span></span> <span data-ttu-id="515c1-217">Det är mer Magic som att köra pester-tester, köra PSScriptAnalyzer, hantera versions hantering och publicera till PSGallery.</span><span class="sxs-lookup"><span data-stu-id="515c1-217">It does more magic like running Pester tests, running PSScriptAnalyzer, managing versioning, and publishing to the PSGallery.</span></span> <span data-ttu-id="515c1-218">När jag har börjat använda ett build-skript för mina moduler kan jag hitta massor av saker att lägga till i det.</span><span class="sxs-lookup"><span data-stu-id="515c1-218">Once I started using a build script for my modules, I was able to find lots of things to add to it.</span></span>

## <a name="final-thoughts"></a><span data-ttu-id="515c1-219">Slutliga tankar</span><span class="sxs-lookup"><span data-stu-id="515c1-219">Final thoughts</span></span>

<span data-ttu-id="515c1-220">Det är enkelt att skapa binära moduler.</span><span class="sxs-lookup"><span data-stu-id="515c1-220">Binary modules are easy to create.</span></span> <span data-ttu-id="515c1-221">Jag har inte använt C#-syntaxen för att skapa en cmdlet, men det finns massor av dokumentation på den i [Windows POWERSHELL SDK][].</span><span class="sxs-lookup"><span data-stu-id="515c1-221">I didn't touch on the C# syntax for creating a Cmdlet, but there is plenty of documentation on it in the [Windows PowerShell SDK][].</span></span> <span data-ttu-id="515c1-222">Det är definitivt något som är värt att experimentera med som en stege-sten i mer allvarliga C#.</span><span class="sxs-lookup"><span data-stu-id="515c1-222">It is definitely something worth experimenting with as a stepping stone into more serious C#.</span></span>

<!-- link references -->
[ursprunglig version]: https://powershellexplained.com/2018-08-04-Powershell-Standard-Library-Binary-Module/
[original version]: https://powershellexplained.com/2018-08-04-Powershell-Standard-Library-Binary-Module/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[PowerShell-standardbibliotek]: https://github.com/PowerShell/PowerShellStandard
[PowerShell Standard Library]: https://github.com/PowerShell/PowerShellStandard
[Skapa en binär plattforms oberoende modul]: https://github.com/PowerShell/PowerShell/blob/master/docs/cmdlet-example/command-line-simple-example.md
[Creating a cross-platform binary module]: https://github.com/PowerShell/PowerShell/blob/master/docs/cmdlet-example/command-line-simple-example.md
[dotNet Core SDK]: https://www.microsoft.com/net/download/core
[dotnet core SDK]: https://www.microsoft.com/net/download/core
[Använda en NuGet-Server för en PSRepository]: https://powershellexplained.com/2018-03-03-Powershell-Using-a-NuGet-server-for-a-PSRepository/
[Using a NuGet server for a PSRepository]: https://powershellexplained.com/2018-03-03-Powershell-Using-a-NuGet-server-for-a-PSRepository/
[Windows PowerShell SDK]: /powershell/scripting/developer/windows-powershell-reference
[VS-kod]: https://code.visualstudio.com
[VS Code]: https://code.visualstudio.com
[NuGet-paket]: https://www.nuget.org/packages/PowerShellStandard.Library/
[nuget package]: https://www.nuget.org/packages/PowerShellStandard.Library/
