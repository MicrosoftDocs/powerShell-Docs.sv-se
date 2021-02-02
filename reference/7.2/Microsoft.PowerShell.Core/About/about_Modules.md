---
description: Förklarar hur du installerar, importerar och använder PowerShell-moduler.
Locale: en-US
ms.date: 12/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_modules?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Modules
ms.openlocfilehash: b98c8b27b68c213ac43fbd350ecd920f813dec6b
ms.sourcegitcommit: 7b376314e7640c39a53aac9f0db8bb935514a960
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/03/2020
ms.locfileid: "96564593"
---
# <a name="about-modules"></a><span data-ttu-id="e8f38-103">Om moduler</span><span class="sxs-lookup"><span data-stu-id="e8f38-103">About Modules</span></span>

## <a name="short-description"></a><span data-ttu-id="e8f38-104">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="e8f38-104">Short Description</span></span>
<span data-ttu-id="e8f38-105">Förklarar hur du installerar, importerar och använder PowerShell-moduler.</span><span class="sxs-lookup"><span data-stu-id="e8f38-105">Explains how to install, import, and use PowerShell modules.</span></span>

## <a name="long-description"></a><span data-ttu-id="e8f38-106">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="e8f38-106">Long Description</span></span>

<span data-ttu-id="e8f38-107">En modul är ett paket som innehåller PowerShell-medlemmar, till exempel cmdlets, providrar, funktioner, arbets flöden, variabler och alias.</span><span class="sxs-lookup"><span data-stu-id="e8f38-107">A module is a package that contains PowerShell members, such as cmdlets, providers, functions, workflows, variables, and aliases.</span></span>

<span data-ttu-id="e8f38-108">Personer som skriver kommandon kan använda moduler för att organisera sina kommandon och dela dem med andra.</span><span class="sxs-lookup"><span data-stu-id="e8f38-108">People who write commands can use modules to organize their commands and share them with others.</span></span> <span data-ttu-id="e8f38-109">Personer som tar emot moduler kan lägga till kommandon i modulerna i sina PowerShell-sessioner och använda dem precis som de inbyggda kommandona.</span><span class="sxs-lookup"><span data-stu-id="e8f38-109">People who receive modules can add the commands in the modules to their PowerShell sessions and use them just like the built-in commands.</span></span>

<span data-ttu-id="e8f38-110">I det här avsnittet beskrivs hur du använder PowerShell-moduler.</span><span class="sxs-lookup"><span data-stu-id="e8f38-110">This topic explains how to use PowerShell modules.</span></span> <span data-ttu-id="e8f38-111">Information om hur du skriver PowerShell-moduler finns i [skriva en PowerShell-modul](/powershell/scripting/developer/module/writing-a-windows-powershell-module).</span><span class="sxs-lookup"><span data-stu-id="e8f38-111">For information about how to write PowerShell modules, see [Writing a PowerShell Module](/powershell/scripting/developer/module/writing-a-windows-powershell-module).</span></span>

## <a name="what-is-a-module"></a><span data-ttu-id="e8f38-112">Vad är en modul?</span><span class="sxs-lookup"><span data-stu-id="e8f38-112">What Is a Module?</span></span>

<span data-ttu-id="e8f38-113">En modul är ett paket som innehåller PowerShell-medlemmar, till exempel cmdlets, providrar, funktioner, arbets flöden, variabler och alias.</span><span class="sxs-lookup"><span data-stu-id="e8f38-113">A module is a package that contains PowerShell members, such as cmdlets, providers, functions, workflows, variables, and aliases.</span></span> <span data-ttu-id="e8f38-114">Medlemmarna i det här paketet kan implementeras i ett PowerShell-skript, en kompilerad DLL-fil eller en kombination av båda.</span><span class="sxs-lookup"><span data-stu-id="e8f38-114">The members of this package can be implemented in a PowerShell script, a compiled DLL, or a combination of both.</span></span> <span data-ttu-id="e8f38-115">De här filerna grupperas vanligt vis i en enda katalog.</span><span class="sxs-lookup"><span data-stu-id="e8f38-115">These files are usually grouped together in a single directory.</span></span> <span data-ttu-id="e8f38-116">Mer information finns i [förstå en Windows PowerShell-modul](/powershell/scripting/developer/module/understanding-a-windows-powershell-module) i SDK-dokumentationen.</span><span class="sxs-lookup"><span data-stu-id="e8f38-116">For more information, see [Understanding a Windows PowerShell Module](/powershell/scripting/developer/module/understanding-a-windows-powershell-module) in the SDK documentation.</span></span>

## <a name="module-auto-loading"></a><span data-ttu-id="e8f38-117">Automatisk inläsning av modul</span><span class="sxs-lookup"><span data-stu-id="e8f38-117">Module Auto-Loading</span></span>

<span data-ttu-id="e8f38-118">Från och med PowerShell 3,0 importerar PowerShell moduler automatiskt första gången du kör ett kommando i en installerad modul.</span><span class="sxs-lookup"><span data-stu-id="e8f38-118">Beginning in PowerShell 3.0, PowerShell imports modules automatically the first time that you run any command in an installed module.</span></span> <span data-ttu-id="e8f38-119">Du kan nu använda kommandona i en modul utan konfigurations konfiguration eller profil, så du behöver inte hantera moduler när du har installerat dem på din dator.</span><span class="sxs-lookup"><span data-stu-id="e8f38-119">You can now use the commands in a module without any set-up or profile configuration, so there's no need to manage modules after you install them on your computer.</span></span>

<span data-ttu-id="e8f38-120">Kommandona i en modul är också lättare att hitta.</span><span class="sxs-lookup"><span data-stu-id="e8f38-120">The commands in a module are also easier to find.</span></span> <span data-ttu-id="e8f38-121">`Get-Command`Cmdleten hämtar nu alla kommandon i alla installerade moduler, även om de inte är i sessionen än.</span><span class="sxs-lookup"><span data-stu-id="e8f38-121">The `Get-Command` cmdlet now gets all commands in all installed modules, even if they are not yet in the session.</span></span> <span data-ttu-id="e8f38-122">Du kan hitta ett kommando och använda det utan att importera behöver importera modulen först.</span><span class="sxs-lookup"><span data-stu-id="e8f38-122">You can find a command and use it without importing needing to import the module first.</span></span>

<span data-ttu-id="e8f38-123">Vart och ett av följande exempel orsakar CimCmdlets-modulen, som innehåller, som ska `Get-CimInstance` importeras till sessionen.</span><span class="sxs-lookup"><span data-stu-id="e8f38-123">Each of the following examples cause the CimCmdlets module, which contains `Get-CimInstance`, to be imported into your session.</span></span>

- <span data-ttu-id="e8f38-124">Kör kommandot</span><span class="sxs-lookup"><span data-stu-id="e8f38-124">Run the Command</span></span>

  ```powershell
  Get-CimInstance Win32_OperatingSystem
  ```

- <span data-ttu-id="e8f38-125">Hämta kommandot</span><span class="sxs-lookup"><span data-stu-id="e8f38-125">Get the Command</span></span>

  ```powershell
  Get-Command Get-CimInstance
  ```

- <span data-ttu-id="e8f38-126">Få hjälp med kommandot</span><span class="sxs-lookup"><span data-stu-id="e8f38-126">Get Help for the Command</span></span>

  ```powershell
  Get-Help Get-CimInstance
  ```

<span data-ttu-id="e8f38-127">`Get-Command` kommandon som innehåller ett jokertecken ( `*` ) anses vara för identifiering, används inte och importerar inte några moduler.</span><span class="sxs-lookup"><span data-stu-id="e8f38-127">`Get-Command` commands that include a wildcard character (`*`) are considered to be for discovery, not use, and do not import any modules.</span></span>

<span data-ttu-id="e8f38-128">Endast moduler som lagras på den plats som anges av PSModulePath-miljövariabeln importeras automatiskt.</span><span class="sxs-lookup"><span data-stu-id="e8f38-128">Only modules that are stored in the location specified by the PSModulePath environment variable are automatically imported.</span></span> <span data-ttu-id="e8f38-129">Moduler på andra platser måste importeras genom att köra `Import-Module` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e8f38-129">Modules in other locations must be imported by running the `Import-Module` cmdlet.</span></span>

<span data-ttu-id="e8f38-130">Kommandon som använder PowerShell-leverantörer importerar dessutom inte automatiskt en modul.</span><span class="sxs-lookup"><span data-stu-id="e8f38-130">Also, commands that use PowerShell providers do not automatically import a module.</span></span> <span data-ttu-id="e8f38-131">Om du till exempel använder ett kommando som kräver WSMan:-enheten, till exempel `Get-PSSessionConfiguration` cmdleten, kan du behöva köra `Import-Module` cmdleten för att importera **Microsoft. WSMan. Management** -modulen som innehåller `WSMan:` enheten.</span><span class="sxs-lookup"><span data-stu-id="e8f38-131">For example, if you use a command that requires the WSMan: drive, such as the `Get-PSSessionConfiguration` cmdlet, you might need to run the `Import-Module` cmdlet to import the **Microsoft.WSMan.Management** module that includes the `WSMan:` drive.</span></span>

<span data-ttu-id="e8f38-132">Du kan fortfarande köra `Import-Module` kommandot för att importera en modul och använda `$PSModuleAutoloadingPreference` variabeln för att aktivera, inaktivera och konfigurera automatisk import av moduler.</span><span class="sxs-lookup"><span data-stu-id="e8f38-132">You can still run the `Import-Module` command to import a module and use the `$PSModuleAutoloadingPreference` variable to enable, disable and configure automatic importing of modules.</span></span> <span data-ttu-id="e8f38-133">Mer information finns i [about_Preference_Variables](about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="e8f38-133">For more information, see [about_Preference_Variables](about_Preference_Variables.md).</span></span>

## <a name="how-to-use-a-module"></a><span data-ttu-id="e8f38-134">Använda en modul</span><span class="sxs-lookup"><span data-stu-id="e8f38-134">How to Use a Module</span></span>

<span data-ttu-id="e8f38-135">Utför följande uppgifter om du vill använda en modul:</span><span class="sxs-lookup"><span data-stu-id="e8f38-135">To use a module, perform the following tasks:</span></span>

1. <span data-ttu-id="e8f38-136">Installera modulen.</span><span class="sxs-lookup"><span data-stu-id="e8f38-136">Install the module.</span></span> <span data-ttu-id="e8f38-137">(Detta görs ofta åt dig.)</span><span class="sxs-lookup"><span data-stu-id="e8f38-137">(This is often done for you.)</span></span>
1. <span data-ttu-id="e8f38-138">Hitta de kommandon som modulen har lagt till.</span><span class="sxs-lookup"><span data-stu-id="e8f38-138">Find the commands that the module added.</span></span>
1. <span data-ttu-id="e8f38-139">Använd de kommandon som modulen har lagt till.</span><span class="sxs-lookup"><span data-stu-id="e8f38-139">Use the commands that the module added.</span></span>

<span data-ttu-id="e8f38-140">I det här avsnittet beskrivs hur du utför dessa uppgifter.</span><span class="sxs-lookup"><span data-stu-id="e8f38-140">This topic explains how to perform these tasks.</span></span> <span data-ttu-id="e8f38-141">Den innehåller även annan användbar information om hur du hanterar moduler.</span><span class="sxs-lookup"><span data-stu-id="e8f38-141">It also includes other useful information about managing modules.</span></span>

## <a name="how-to-install-a-module"></a><span data-ttu-id="e8f38-142">Så här installerar du en modul</span><span class="sxs-lookup"><span data-stu-id="e8f38-142">How to Install a Module</span></span>

<span data-ttu-id="e8f38-143">Om du får en modul som en mapp med filer i den måste du installera den på datorn innan du kan använda den i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e8f38-143">If you receive a module as a folder with files in it, you need to install it on your computer before you can use it in PowerShell.</span></span>

<span data-ttu-id="e8f38-144">De flesta moduler är installerade åt dig.</span><span class="sxs-lookup"><span data-stu-id="e8f38-144">Most modules are installed for you.</span></span> <span data-ttu-id="e8f38-145">PowerShell innehåller flera förinstallerade moduler, ibland kallade _Core_ -moduler.</span><span class="sxs-lookup"><span data-stu-id="e8f38-145">PowerShell comes with several preinstalled modules, sometimes called the _core_ modules.</span></span> <span data-ttu-id="e8f38-146">På Windows-baserade datorer, om funktioner som ingår i operativ systemet har cmdlets för att hantera dem, förinstalleras dessa moduler.</span><span class="sxs-lookup"><span data-stu-id="e8f38-146">On Windows-based computers, if features that are included with the operating system have cmdlets to manage them, those modules are preinstalled.</span></span> <span data-ttu-id="e8f38-147">När du installerar en Windows-funktion med hjälp av, till exempel guiden Lägg till roller och funktioner i Serverhanteraren eller i dialog rutan Aktivera eller inaktivera Windows-funktioner på kontroll panelen, installeras alla PowerShell-moduler som ingår i funktionen.</span><span class="sxs-lookup"><span data-stu-id="e8f38-147">When you install a Windows feature, by using, for example, the Add Roles and Features Wizard in Server Manager, or the Turn Windows features on or off dialog box in Control Panel, any PowerShell modules that are part of the feature are installed.</span></span> <span data-ttu-id="e8f38-148">Många andra moduler ingår i ett installations program eller installations program som installerar modulen.</span><span class="sxs-lookup"><span data-stu-id="e8f38-148">Many other modules come in an installer or Setup program that installs the module.</span></span>

<span data-ttu-id="e8f38-149">Använd följande kommando för att skapa en **modul** -katalog för den aktuella användaren:</span><span class="sxs-lookup"><span data-stu-id="e8f38-149">Use the following command to create a **Modules** directory for the current user:</span></span>

```powershell
New-Item -Type Directory -Path $HOME\Documents\PowerShell\Modules
```

<span data-ttu-id="e8f38-150">Kopiera hela modul-mappen till katalogen modules.</span><span class="sxs-lookup"><span data-stu-id="e8f38-150">Copy the entire module folder into the Modules directory.</span></span> <span data-ttu-id="e8f38-151">Du kan använda valfri metod för att kopiera mappen, inklusive Windows Explorer och Cmd.exe, samt PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e8f38-151">You can use any method to copy the folder, including Windows Explorer and Cmd.exe, as well as PowerShell.</span></span> <span data-ttu-id="e8f38-152">I PowerShell använder du `Copy-Item` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e8f38-152">In PowerShell use the `Copy-Item` cmdlet.</span></span> <span data-ttu-id="e8f38-153">Om du till exempel vill kopiera mappen för mina `C:\ps-test\MyModule` moduler från till katalogen moduler skriver du:</span><span class="sxs-lookup"><span data-stu-id="e8f38-153">For example, to copy the MyModule folder from `C:\ps-test\MyModule` to the Modules directory, type:</span></span>

```powershell
Copy-Item -Path C:\ps-test\MyModule -Destination `
    $HOME\Documents\PowerShell\Modules
```

<span data-ttu-id="e8f38-154">Du kan installera en modul på vilken plats som helst, men om du installerar modulerna på en standardmodul blir det enklare att hantera dem.</span><span class="sxs-lookup"><span data-stu-id="e8f38-154">You can install a module in any location, but installing your modules in a default module location makes them easier to manage.</span></span> <span data-ttu-id="e8f38-155">Mer information om standardmodulens platser finns i modulen för [modul-och DSC-resurser och PSModulePath-](#module-and-dsc-resource-locations-and-psmodulepath) avsnittet.</span><span class="sxs-lookup"><span data-stu-id="e8f38-155">For more information about the default module locations, see the [Module and DSC Resource Locations, and PSModulePath](#module-and-dsc-resource-locations-and-psmodulepath) section.</span></span>

## <a name="how-to-find-installed-modules"></a><span data-ttu-id="e8f38-156">Så här hittar du installerade moduler</span><span class="sxs-lookup"><span data-stu-id="e8f38-156">How to Find Installed Modules</span></span>

<span data-ttu-id="e8f38-157">Om du vill hitta moduler som är installerade på en standardmodul, men som ännu inte har importer ATS till din session, skriver du:</span><span class="sxs-lookup"><span data-stu-id="e8f38-157">To find modules that are installed in a default module location, but not yet imported into your session, type:</span></span>

```powershell
Get-Module -ListAvailable
```

<span data-ttu-id="e8f38-158">Om du vill hitta de moduler som redan har importer ATS till din-session skriver du följande i PowerShell-prompten:</span><span class="sxs-lookup"><span data-stu-id="e8f38-158">To find the modules that have already been imported into your session, at the PowerShell prompt, type:</span></span>

```powershell
Get-Module
```

<span data-ttu-id="e8f38-159">Mer information om `Get-Module` cmdleten finns i [Get-module](xref:Microsoft.PowerShell.Core.Get-Module).</span><span class="sxs-lookup"><span data-stu-id="e8f38-159">For more information about the `Get-Module` cmdlet, see [Get-Module](xref:Microsoft.PowerShell.Core.Get-Module).</span></span>

## <a name="how-to-find-the-commands-in-a-module"></a><span data-ttu-id="e8f38-160">Så här hittar du kommandon i en modul</span><span class="sxs-lookup"><span data-stu-id="e8f38-160">How to Find the Commands in a Module</span></span>

<span data-ttu-id="e8f38-161">Använd `Get-Command` cmdleten för att hitta alla tillgängliga kommandon.</span><span class="sxs-lookup"><span data-stu-id="e8f38-161">Use the `Get-Command` cmdlet to find all available commands.</span></span> <span data-ttu-id="e8f38-162">Du kan använda parametrarna för `Get-Command` cmdlet: en för att filtrera kommandon som till exempel efter modul, namn och substantiv.</span><span class="sxs-lookup"><span data-stu-id="e8f38-162">You can use the parameters of the `Get-Command` cmdlet to filter commands such as by module, name, and noun.</span></span>

<span data-ttu-id="e8f38-163">Om du vill söka efter alla kommandon i en modul skriver du:</span><span class="sxs-lookup"><span data-stu-id="e8f38-163">To find all commands in a module, type:</span></span>

```powershell
Get-Command -Module <module-name>
```

<span data-ttu-id="e8f38-164">Om du till exempel vill hitta kommandona i BitsTransfer-modulen skriver du:</span><span class="sxs-lookup"><span data-stu-id="e8f38-164">For example, to find the commands in the BitsTransfer module, type:</span></span>

```powershell
Get-Command -Module BitsTransfer
```

<span data-ttu-id="e8f38-165">Mer information om `Get-Command` cmdleten finns i [Get-Command](xref:Microsoft.PowerShell.Core.Get-Command).</span><span class="sxs-lookup"><span data-stu-id="e8f38-165">For more information about the `Get-Command` cmdlet, see [Get-Command](xref:Microsoft.PowerShell.Core.Get-Command).</span></span>

## <a name="how-to-get-help-for-the-commands-in-a-module"></a><span data-ttu-id="e8f38-166">Så här får du hjälp med kommandon i en modul</span><span class="sxs-lookup"><span data-stu-id="e8f38-166">How to Get Help for the Commands in a Module</span></span>

<span data-ttu-id="e8f38-167">Om modulen innehåller hjälpfiler för de kommandon som den exporterar, `Get-Help` visas hjälp avsnitten i cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e8f38-167">If the module contains Help files for the commands that it exports, the `Get-Help` cmdlet will display the Help topics.</span></span> <span data-ttu-id="e8f38-168">Använd samma `Get-Help` kommando format som du kan använda för att få hjälp med kommandon i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e8f38-168">Use the same `Get-Help` command format that you would use to get help for any command in PowerShell.</span></span>

<span data-ttu-id="e8f38-169">Från och med PowerShell 3,0 kan du hämta hjälpfiler för en modul och ladda ned uppdateringar till hjälpfilerna så att de aldrig är föråldrade.</span><span class="sxs-lookup"><span data-stu-id="e8f38-169">Beginning in PowerShell 3.0, you can download Help files for a module and download updates to the Help files so they are never obsolete.</span></span>

<span data-ttu-id="e8f38-170">Om du vill ha hjälp med kommandon i en modul skriver du:</span><span class="sxs-lookup"><span data-stu-id="e8f38-170">To get help for a commands in a module, type:</span></span>

```powershell
Get-Help <command-name>
```

<span data-ttu-id="e8f38-171">Om du vill få hjälp online för kommandot i en modul skriver du:</span><span class="sxs-lookup"><span data-stu-id="e8f38-171">To get help online for command in a module, type:</span></span>

```powershell
Get-Help <command-name> -Online
```

<span data-ttu-id="e8f38-172">Om du vill hämta och installera hjälpfilerna för kommandon i en modul skriver du:</span><span class="sxs-lookup"><span data-stu-id="e8f38-172">To download and install the help files for the commands in a module, type:</span></span>

```powershell
Update-Help -Module <module-name>
```

<span data-ttu-id="e8f38-173">Mer information finns i [få hjälp](xref:Microsoft.PowerShell.Core.Get-Help) och [Uppdatera – hjälp](xref:Microsoft.PowerShell.Core.Update-Help).</span><span class="sxs-lookup"><span data-stu-id="e8f38-173">For more information, see [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) and [Update-Help](xref:Microsoft.PowerShell.Core.Update-Help).</span></span>

## <a name="how-to-import-a-module"></a><span data-ttu-id="e8f38-174">Så här importerar du en modul</span><span class="sxs-lookup"><span data-stu-id="e8f38-174">How to Import a Module</span></span>

<span data-ttu-id="e8f38-175">Du kan behöva importera en modul eller importera en modul-fil.</span><span class="sxs-lookup"><span data-stu-id="e8f38-175">You might have to import a module or import a module file.</span></span> <span data-ttu-id="e8f38-176">Import krävs när en modul inte är installerad på de platser som anges av **PSModulePath** -miljövariabeln, `$env:PSModulePath` eller om modulen består av en fil, till exempel en. dll-eller. psm1-fil, i stället för en typisk modul som levereras som en mapp.</span><span class="sxs-lookup"><span data-stu-id="e8f38-176">Importing is required when a module is not installed in the locations specified by the **PSModulePath** environment variable, `$env:PSModulePath`, or the module consists of file, such as a .dll or .psm1 file, instead of typical module that is delivered as a folder.</span></span>

<span data-ttu-id="e8f38-177">Du kan också välja att importera en modul så att du kan använda parametrarna för `Import-Module` kommandot, till exempel parametern prefix, som lägger till ett särskiljande prefix till Substantiv namnen för alla importerade kommandon, eller parametern **NoClobber** , som förhindrar att modulen lägger till kommandon som döljer eller ersätter befintliga kommandon i sessionen.</span><span class="sxs-lookup"><span data-stu-id="e8f38-177">You might also choose to import a module so that you can use the parameters of the `Import-Module` command, such as the Prefix parameter, which adds a distinctive prefix to the noun names of all imported commands, or the **NoClobber** parameter, which prevents the module from adding commands that would hide or replace existing commands in the session.</span></span>

<span data-ttu-id="e8f38-178">Använd cmdleten för att importera moduler `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="e8f38-178">To import modules, use the `Import-Module` cmdlet.</span></span>

<span data-ttu-id="e8f38-179">Om du vill importera moduler på en PSModulePath plats till den aktuella sessionen använder du följande kommando format.</span><span class="sxs-lookup"><span data-stu-id="e8f38-179">To import modules in a PSModulePath location into the current session, use the following command format.</span></span>

```powershell
Import-Module <module-name>
```

<span data-ttu-id="e8f38-180">Följande kommando importerar till exempel modulen BitsTransfer till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="e8f38-180">For example, the following command imports the BitsTransfer module into the current session.</span></span>

```powershell
Import-Module BitsTransfer
```

<span data-ttu-id="e8f38-181">Om du vill importera en modul som inte finns på en standardmodul, använder du den fullständiga sökvägen till mappen modul i kommandot.</span><span class="sxs-lookup"><span data-stu-id="e8f38-181">To import a module that is not in a default module location, use the fully qualified path to the module folder in the command.</span></span>

<span data-ttu-id="e8f38-182">Om du till exempel vill lägga till modulen TestCmdlets i `C:\ps-test` katalogen i din session skriver du:</span><span class="sxs-lookup"><span data-stu-id="e8f38-182">For example, to add the TestCmdlets module in the `C:\ps-test` directory to your session, type:</span></span>

```powershell
Import-Module C:\ps-test\TestCmdlets
```

<span data-ttu-id="e8f38-183">Om du vill importera en modul som inte finns i en modul-mapp använder du den fullständiga sökvägen till filen i kommandot.</span><span class="sxs-lookup"><span data-stu-id="e8f38-183">To import a module file that is not contained in a module folder, use the fully qualified path to the module file in the command.</span></span>

<span data-ttu-id="e8f38-184">Om du till exempel vill lägga till modulen TestCmdlets.dll i `C:\ps-test` katalogen i din session skriver du:</span><span class="sxs-lookup"><span data-stu-id="e8f38-184">For example, to add the TestCmdlets.dll module in the `C:\ps-test` directory to your session, type:</span></span>

```powershell
Import-Module C:\ps-test\TestCmdlets.dll
```

<span data-ttu-id="e8f38-185">Mer information om hur du lägger till moduler i din session finns i [import-module](xref:Microsoft.PowerShell.Core.Import-Module).</span><span class="sxs-lookup"><span data-stu-id="e8f38-185">For more information about adding modules to your session, see [Import-Module](xref:Microsoft.PowerShell.Core.Import-Module).</span></span>

## <a name="how-to-import-a-module-into-every-session"></a><span data-ttu-id="e8f38-186">Så här importerar du en modul till varje session</span><span class="sxs-lookup"><span data-stu-id="e8f38-186">How to Import a Module into Every Session</span></span>

<span data-ttu-id="e8f38-187">`Import-Module`Kommandot importerar moduler till din aktuella PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="e8f38-187">The `Import-Module` command imports modules into your current PowerShell session.</span></span> <span data-ttu-id="e8f38-188">Om du vill importera en modul till varje PowerShell-session som du startar lägger du till `Import-Module` kommandot i din PowerShell-profil.</span><span class="sxs-lookup"><span data-stu-id="e8f38-188">To import a module into every PowerShell session that you start, add the `Import-Module` command to your PowerShell profile.</span></span>

<span data-ttu-id="e8f38-189">Mer information om profiler finns [about_Profiles](about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="e8f38-189">For more information about profiles, see [about_Profiles](about_Profiles.md).</span></span>

## <a name="how-to-remove-a-module"></a><span data-ttu-id="e8f38-190">Ta bort en modul</span><span class="sxs-lookup"><span data-stu-id="e8f38-190">How to Remove a Module</span></span>

<span data-ttu-id="e8f38-191">När du tar bort en modul tas de kommandon som läggs till i modulen bort från sessionen.</span><span class="sxs-lookup"><span data-stu-id="e8f38-191">When you remove a module, the commands that the module added are deleted from the session.</span></span>

<span data-ttu-id="e8f38-192">Om du vill ta bort en modul från sessionen använder du följande kommando format.</span><span class="sxs-lookup"><span data-stu-id="e8f38-192">To remove a module from your session, use the following command format.</span></span>

```powershell
Remove-Module <module-name>
```

<span data-ttu-id="e8f38-193">Följande kommando tar till exempel bort modulen BitsTransfer från den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="e8f38-193">For example, the following command removes the BitsTransfer module from the current session.</span></span>

```powershell
Remove-Module BitsTransfer
```

<span data-ttu-id="e8f38-194">Om du tar bort en modul ångras åtgärden för att importera en modul.</span><span class="sxs-lookup"><span data-stu-id="e8f38-194">Removing a module reverses the operation of importing a module.</span></span> <span data-ttu-id="e8f38-195">Att ta bort en modul avinstallerar inte modulen.</span><span class="sxs-lookup"><span data-stu-id="e8f38-195">Removing a module does not uninstall the module.</span></span> <span data-ttu-id="e8f38-196">Mer information finns i [Remove-module](xref:Microsoft.PowerShell.Core.Remove-Module).</span><span class="sxs-lookup"><span data-stu-id="e8f38-196">For more information, see [Remove-Module](xref:Microsoft.PowerShell.Core.Remove-Module).</span></span>

## <a name="module-and-dsc-resource-locations-and-psmodulepath"></a><span data-ttu-id="e8f38-197">Modul-och DSC-resurs platser och PSModulePath</span><span class="sxs-lookup"><span data-stu-id="e8f38-197">Module and DSC Resource Locations, and PSModulePath</span></span>

<span data-ttu-id="e8f38-198">`$env:PSModulePath`Miljövariabeln innehåller en lista över mappar som genomsöks för att hitta moduler och resurser.</span><span class="sxs-lookup"><span data-stu-id="e8f38-198">The `$env:PSModulePath` environment variable contains a list of folder locations that are searched to find modules and resources.</span></span>

<span data-ttu-id="e8f38-199">Som standard är de effektiva platser som `$env:PSModulePath` är tilldelade:</span><span class="sxs-lookup"><span data-stu-id="e8f38-199">By default, the effective locations assigned to `$env:PSModulePath` are:</span></span>

- <span data-ttu-id="e8f38-200">Platser i hela systemet: `$PSHOME\Modules`</span><span class="sxs-lookup"><span data-stu-id="e8f38-200">System-wide locations: `$PSHOME\Modules`</span></span>

  <span data-ttu-id="e8f38-201">Dessa mappar innehåller moduler som levereras med Windows och PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e8f38-201">These folders contain modules that ship with Windows and PowerShell.</span></span>

  <span data-ttu-id="e8f38-202">DSC-resurser som ingår i PowerShell lagras i `$PSHOME\Modules\PSDesiredStateConfiguration\DSCResources` mappen.</span><span class="sxs-lookup"><span data-stu-id="e8f38-202">DSC resources that are included with PowerShell are stored in the `$PSHOME\Modules\PSDesiredStateConfiguration\DSCResources` folder.</span></span>

- <span data-ttu-id="e8f38-203">Användarspecifika moduler: de här är moduler som installeras av användaren i användarens omfång.</span><span class="sxs-lookup"><span data-stu-id="e8f38-203">User-specific modules: These are modules installed by the user in the user's scope.</span></span> <span data-ttu-id="e8f38-204">`Install-Module` har en **omfattnings** parameter som gör att du kan ange om modulen är installerad för den aktuella användaren eller för alla användare.</span><span class="sxs-lookup"><span data-stu-id="e8f38-204">`Install-Module` has a **Scope** parameter that allows you to specify whether the module is installed for the current user or for all users.</span></span> <span data-ttu-id="e8f38-205">Mer information finns i [install-module](xref:PowerShellGet.Install-Module).</span><span class="sxs-lookup"><span data-stu-id="e8f38-205">For more information, see [Install-Module](xref:PowerShellGet.Install-Module).</span></span>

  <span data-ttu-id="e8f38-206">Den användarspecifika **CurrentUser** -platsen i Windows är `PowerShell\Modules` mappen som finns på **dokument** platsen i din användar profil.</span><span class="sxs-lookup"><span data-stu-id="e8f38-206">The user-specific **CurrentUser** location on Windows is the `PowerShell\Modules` folder located in the **Documents** location in your user profile.</span></span> <span data-ttu-id="e8f38-207">Den angivna sökvägen till platsen varierar efter Windows-version och om du använder mappomdirigering.</span><span class="sxs-lookup"><span data-stu-id="e8f38-207">The specific path of that location varies by version of Windows and whether or not you are using folder redirection.</span></span> <span data-ttu-id="e8f38-208">Microsoft OneDrive kan också ändra platsen för mappen **dokument** .</span><span class="sxs-lookup"><span data-stu-id="e8f38-208">Microsoft OneDrive can also change the location of your **Documents** folder.</span></span>

  <span data-ttu-id="e8f38-209">Som standard är den platsen i Windows 10 `$HOME\Documents\PowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="e8f38-209">By default, on Windows 10, that location is `$HOME\Documents\PowerShell\Modules`.</span></span> <span data-ttu-id="e8f38-210">På Linux eller Mac är **CurrentUser** -platsen `$HOME/.local/share/powershell/Modules` .</span><span class="sxs-lookup"><span data-stu-id="e8f38-210">On Linux or Mac, the **CurrentUser** location is `$HOME/.local/share/powershell/Modules`.</span></span>

  > [!NOTE]
  > <span data-ttu-id="e8f38-211">Du kan kontrol lera platsen för mappen **dokument** med hjälp av följande kommando: `[Environment]::GetFolderPath('MyDocuments')` .</span><span class="sxs-lookup"><span data-stu-id="e8f38-211">You can verify the location of your **Documents** folder using the following command: `[Environment]::GetFolderPath('MyDocuments')`.</span></span>

- <span data-ttu-id="e8f38-212">**Allusers** -platsen finns `$env:PROGRAMFILES\PowerShell\Modules` i Windows.</span><span class="sxs-lookup"><span data-stu-id="e8f38-212">The **AllUsers** location is `$env:PROGRAMFILES\PowerShell\Modules` on Windows.</span></span> <span data-ttu-id="e8f38-213">I Linux eller Mac lagras modulerna på `/usr/local/share/powershell/Modules` .</span><span class="sxs-lookup"><span data-stu-id="e8f38-213">On Linux or Mac the modules are stored at `/usr/local/share/powershell/Modules`.</span></span>

> [!NOTE]
> <span data-ttu-id="e8f38-214">Om du vill lägga till eller ändra filer i `$env:Windir\System32` katalogen startar du PowerShell med alternativet **Kör som administratör** .</span><span class="sxs-lookup"><span data-stu-id="e8f38-214">To add or change files in the `$env:Windir\System32` directory, start PowerShell with the **Run as administrator** option.</span></span>

<span data-ttu-id="e8f38-215">Du kan ändra standard platserna för modulen i systemet genom att ändra värdet för **PSModulePath** -miljövariabeln `$Env:PSModulePath` .</span><span class="sxs-lookup"><span data-stu-id="e8f38-215">You can change the default module locations on your system by changing the value of the **PSModulePath** environment variable, `$Env:PSModulePath`.</span></span> <span data-ttu-id="e8f38-216">Miljövariabeln **PSModulePath** är modellerad i miljövariabeln PATH och har samma format.</span><span class="sxs-lookup"><span data-stu-id="e8f38-216">The **PSModulePath** environment variable is modeled on the Path environment variable and has the same format.</span></span>

<span data-ttu-id="e8f38-217">Om du vill visa standard platserna för modulen skriver du:</span><span class="sxs-lookup"><span data-stu-id="e8f38-217">To view the default module locations, type:</span></span>

```powershell
$Env:PSModulePath
```

<span data-ttu-id="e8f38-218">Använd följande kommando format om du vill lägga till en standard-modul.</span><span class="sxs-lookup"><span data-stu-id="e8f38-218">To add a default module location, use the following command format.</span></span>

```powershell
$Env:PSModulePath = $Env:PSModulePath + ";<path>"
```

<span data-ttu-id="e8f38-219">Semikolon ( `;` ) i kommandot avgränsar den nya sökvägen från den sökväg som föregår den i listan.</span><span class="sxs-lookup"><span data-stu-id="e8f38-219">The semi-colon (`;`) in the command separates the new path from the path that precedes it in the list.</span></span>

<span data-ttu-id="e8f38-220">Om du till exempel vill lägga till `C:\ps-test\Modules` katalogen skriver du:</span><span class="sxs-lookup"><span data-stu-id="e8f38-220">For example, to add the `C:\ps-test\Modules` directory, type:</span></span>

```powershell
$Env:PSModulePath + ";C:\ps-test\Modules"
```

<span data-ttu-id="e8f38-221">Om du vill lägga till en standard-modul på Linux eller MacOS, använder du följande kommando format:</span><span class="sxs-lookup"><span data-stu-id="e8f38-221">To add a default module location on Linux or MacOS, use the following command format:</span></span>

```powershell
$Env:PSModulePath += ":<path>"
```

<span data-ttu-id="e8f38-222">Om du till exempel vill lägga till `/usr/local/Fabrikam/Modules` katalogen till värdet för **PSModulePath** -miljövariabeln, skriver du:</span><span class="sxs-lookup"><span data-stu-id="e8f38-222">For example, to add the `/usr/local/Fabrikam/Modules` directory to the value of the **PSModulePath** environment variable, type:</span></span>

```powershell
$Env:PSModulePath += ":/usr/local/Fabrikam/Modules"
```

<span data-ttu-id="e8f38-223">Kolon () i kommandot på Linux eller MacOS `:` separerar den nya sökvägen från den sökväg som föregår den i listan.</span><span class="sxs-lookup"><span data-stu-id="e8f38-223">On Linux or MacOS, the colon (`:`) in the command separates the new path from the path that precedes it in the list.</span></span>

<span data-ttu-id="e8f38-224">När du lägger till en sökväg i PSModulePath `Get-Module` och `Import-Module` kommandon innehåller moduler i den sökvägen.</span><span class="sxs-lookup"><span data-stu-id="e8f38-224">When you add a path to **PSModulePath**, `Get-Module` and `Import-Module` commands include modules in that path.</span></span>

<span data-ttu-id="e8f38-225">Värdet som du anger påverkar endast den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="e8f38-225">The value that you set affects only the current session.</span></span> <span data-ttu-id="e8f38-226">Om du vill göra ändringen permanent lägger du till kommandot i din PowerShell-profil eller använder system på kontroll panelen för att ändra värdet för **PSModulePath** -miljövariabeln i registret.</span><span class="sxs-lookup"><span data-stu-id="e8f38-226">To make the change persistent, add the command to your PowerShell profile or use System in Control Panel to change the value of the **PSModulePath** environment variable in the registry.</span></span>

<span data-ttu-id="e8f38-227">Om du vill göra ändringen beständig kan du också använda metoden **SetEnvironmentVariable** i klassen **system. Environment** för att lägga till en sökväg till **PSModulePath** -miljövariabeln.</span><span class="sxs-lookup"><span data-stu-id="e8f38-227">Also, to make the change persistent, you can also use the **SetEnvironmentVariable** method of the **System.Environment** class to add a Path to the **PSModulePath** environment variable.</span></span>

<span data-ttu-id="e8f38-228">Mer information om variabeln **PSModulePath** finns i [about_Environment_Variables](about_Environment_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="e8f38-228">For more information about the **PSModulePath** variable, see [about_Environment_Variables](about_Environment_Variables.md).</span></span>

## <a name="modules-and-name-conflicts"></a><span data-ttu-id="e8f38-229">Moduler och namn konflikter</span><span class="sxs-lookup"><span data-stu-id="e8f38-229">Modules and Name Conflicts</span></span>

<span data-ttu-id="e8f38-230">Namn konflikter uppstår när mer än ett kommando i sessionen har samma namn.</span><span class="sxs-lookup"><span data-stu-id="e8f38-230">Name conflicts occur when more than one command in the session has the same name.</span></span> <span data-ttu-id="e8f38-231">Om du importerar en modul uppstår en namn konflikt när kommandon i modulen har samma namn som kommandon eller objekt i sessionen.</span><span class="sxs-lookup"><span data-stu-id="e8f38-231">Importing a module causes a name conflict when commands in the module have the same names as commands or items in the session.</span></span>

<span data-ttu-id="e8f38-232">Namn konflikter kan resultera i att kommandon döljs eller ersätts.</span><span class="sxs-lookup"><span data-stu-id="e8f38-232">Name conflicts can result in commands being hidden or replaced.</span></span>

### <a name="hidden"></a><span data-ttu-id="e8f38-233">Dold</span><span class="sxs-lookup"><span data-stu-id="e8f38-233">Hidden</span></span>

<span data-ttu-id="e8f38-234">Ett kommando är dolt när det inte är det kommando som körs när du skriver kommandots namn, men du kan köra det med en annan metod, till exempel genom att kvalificera kommando namnet med namnet på modulen eller snapin-modulen där det kom.</span><span class="sxs-lookup"><span data-stu-id="e8f38-234">A command is hidden when it is not the command that runs when you type the command name, but you can run it by using another method, such as by qualifying the command name with the name of the module or snap-in in which it originated.</span></span>

### <a name="replaced"></a><span data-ttu-id="e8f38-235">Ersätter</span><span class="sxs-lookup"><span data-stu-id="e8f38-235">Replaced</span></span>

<span data-ttu-id="e8f38-236">Ett kommando ersätts när du inte kan köra det eftersom det har skrivits över av ett kommando med samma namn.</span><span class="sxs-lookup"><span data-stu-id="e8f38-236">A command is replaced when you cannot run it because it has been overwritten by a command with the same name.</span></span> <span data-ttu-id="e8f38-237">Även om du tar bort modulen som orsakade konflikten kan du inte köra ett ersatt kommando om du inte startar om sessionen.</span><span class="sxs-lookup"><span data-stu-id="e8f38-237">Even when you remove the module that caused the conflict, you cannot run a replaced command unless you restart the session.</span></span>

<span data-ttu-id="e8f38-238">`Import-Module` kan lägga till kommandon som döljer och ersätter kommandon i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="e8f38-238">`Import-Module` might add commands that hide and replace commands in the current session.</span></span> <span data-ttu-id="e8f38-239">Dessutom kan kommandon i din session dölja kommandon som har lagts till i modulen.</span><span class="sxs-lookup"><span data-stu-id="e8f38-239">Also, commands in your session can hide commands that the module added.</span></span>

<span data-ttu-id="e8f38-240">Använd parametern **all** för cmdleten om du vill identifiera namn konflikter `Get-Command` .</span><span class="sxs-lookup"><span data-stu-id="e8f38-240">To detect name conflicts, use the **All** parameter of the `Get-Command` cmdlet.</span></span> <span data-ttu-id="e8f38-241">Från och med PowerShell 3,0 `Get-Command` hämtas bara kommandon som körs när du skriver kommandots namn.</span><span class="sxs-lookup"><span data-stu-id="e8f38-241">Beginning in PowerShell 3.0, `Get-Command` gets only that commands that run when you type the command name.</span></span> <span data-ttu-id="e8f38-242">Parametern **all** hämtar alla kommandon med det angivna namnet i sessionen.</span><span class="sxs-lookup"><span data-stu-id="e8f38-242">The **All** parameter gets all commands with the specific name in the session.</span></span>

<span data-ttu-id="e8f38-243">Om du vill förhindra namn konflikter använder du **NoClobber** -eller **prefixvärde** -parametrarna för `Import-Module` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e8f38-243">To prevent name conflicts, use the **NoClobber** or **Prefix** parameters of the `Import-Module` cmdlet.</span></span> <span data-ttu-id="e8f38-244">Parametern **prefix** lägger till ett prefix till namnen på importerade kommandon så att de är unika i sessionen.</span><span class="sxs-lookup"><span data-stu-id="e8f38-244">The **Prefix** parameter adds a prefix to the names of imported commands so that they are unique in the session.</span></span> <span data-ttu-id="e8f38-245">**NoClobber** -parametern importerar inte några kommandon som döljer eller ersätter befintliga kommandon i sessionen.</span><span class="sxs-lookup"><span data-stu-id="e8f38-245">The **NoClobber** parameter does not import any commands that would hide or replace existing commands in the session.</span></span>

<span data-ttu-id="e8f38-246">Du kan också använda **alias**-, **cmdlet**-, **Function**-och **Variable** -parametrarna för `Import-Module` för att välja de kommandon som du vill importera, och du kan utesluta kommandon som orsakar namn konflikter i sessionen.</span><span class="sxs-lookup"><span data-stu-id="e8f38-246">You can also use the **Alias**, **Cmdlet**, **Function**, and **Variable** parameters of `Import-Module` to select only the commands that you want to import, and you can exclude commands that cause name conflicts in your session.</span></span>

<span data-ttu-id="e8f38-247">Modulens författare kan förhindra namn konflikter genom att använda **DefaultCommandPrefix** -egenskapen för modulens manifest för att lägga till ett standardprefix i alla kommando namn.</span><span class="sxs-lookup"><span data-stu-id="e8f38-247">Module authors can prevent name conflicts by using the **DefaultCommandPrefix** property of the module manifest to add a default prefix to all command names.</span></span>
<span data-ttu-id="e8f38-248">Värdet för parametern **prefix** har företräde framför värdet för **DefaultCommandPrefix**.</span><span class="sxs-lookup"><span data-stu-id="e8f38-248">The value of the **Prefix** parameter takes precedence over the value of **DefaultCommandPrefix**.</span></span>

<span data-ttu-id="e8f38-249">Även om ett kommando är dolt kan du köra det genom att kvalificera kommando namnet med namnet på modulen eller snapin-modulen där det kom.</span><span class="sxs-lookup"><span data-stu-id="e8f38-249">Even if a command is hidden, you can run it by qualifying the command name with the name of the module or snap-in in which it originated.</span></span>

<span data-ttu-id="e8f38-250">Regel reglerna för PowerShell-kommandot avgör vilket kommando som körs när sessionen innehåller kommandon med samma namn.</span><span class="sxs-lookup"><span data-stu-id="e8f38-250">The PowerShell command precedence rules determine which command runs when the session includes commands with the same name.</span></span>

<span data-ttu-id="e8f38-251">Till exempel, när en session innehåller en funktion och en cmdlet med samma namn, kör PowerShell funktionen som standard.</span><span class="sxs-lookup"><span data-stu-id="e8f38-251">For example, when a session includes a function and a cmdlet with the same name, PowerShell runs the function by default.</span></span> <span data-ttu-id="e8f38-252">När sessionen innehåller kommandon av samma typ med samma namn, till exempel två cmdlets med samma namn, körs det senast tillagda kommandot som standard.</span><span class="sxs-lookup"><span data-stu-id="e8f38-252">When the session includes commands of the same type with the same name, such as two cmdlets with the same name, by default, it runs the most recently added command.</span></span>

<span data-ttu-id="e8f38-253">Mer information, inklusive en förklaring av prioritets reglerna och instruktioner för att köra dolda kommandon, finns [about_Command_Precedence](about_Command_Precedence.md).</span><span class="sxs-lookup"><span data-stu-id="e8f38-253">For more information, including an explanation of the precedence rules and instructions for running hidden commands, see [about_Command_Precedence](about_Command_Precedence.md).</span></span>

## <a name="modules-and-snap-ins"></a><span data-ttu-id="e8f38-254">Moduler och snapin-moduler</span><span class="sxs-lookup"><span data-stu-id="e8f38-254">Modules and Snap-ins</span></span>

<span data-ttu-id="e8f38-255">Du kan lägga till kommandon i-sessionen från moduler och snapin-moduler. Moduler kan lägga till alla typer av kommandon, inklusive cmdlet: ar, providers och funktioner och objekt, till exempel variabler, alias och PowerShell-enheter.</span><span class="sxs-lookup"><span data-stu-id="e8f38-255">You can add commands to your session from modules and snap-ins. Modules can add all types of commands, including cmdlets, providers, and functions, and items, such as variables, aliases, and PowerShell drives.</span></span> <span data-ttu-id="e8f38-256">Snapin-moduler kan bara lägga till cmdlets och providers.</span><span class="sxs-lookup"><span data-stu-id="e8f38-256">Snap-ins can add only cmdlets and providers.</span></span>

<span data-ttu-id="e8f38-257">Innan du tar bort en modul eller snapin-modul från din session kan du använda följande kommandon för att avgöra vilka kommandon som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="e8f38-257">Before removing a module or snap-in from your session, use the following commands to determine which commands will be removed.</span></span>

<span data-ttu-id="e8f38-258">Om du vill hitta källan till en cmdlet i din-session använder du följande kommando format:</span><span class="sxs-lookup"><span data-stu-id="e8f38-258">To find the source of a cmdlet in your session, use the following command format:</span></span>

```powershell
Get-Command <cmdlet-name> | Format-List -Property verb,noun,pssnapin,module
```

<span data-ttu-id="e8f38-259">Om du till exempel vill hitta källan till `Get-Date` cmdleten skriver du:</span><span class="sxs-lookup"><span data-stu-id="e8f38-259">For example, to find the source of the `Get-Date` cmdlet, type:</span></span>

```powershell
Get-Command Get-Date | Format-List -Property verb,noun,module
```

## <a name="module-related-warnings-and-errors"></a><span data-ttu-id="e8f38-260">Moduler-relaterade varningar och fel</span><span class="sxs-lookup"><span data-stu-id="e8f38-260">Module-related Warnings and Errors</span></span>

<span data-ttu-id="e8f38-261">De kommandon som en modul exporterar till följer PowerShell-kommandot namngivnings regler.</span><span class="sxs-lookup"><span data-stu-id="e8f38-261">The commands that a module exports should follow the PowerShell command naming rules.</span></span> <span data-ttu-id="e8f38-262">Om modulen som du importerar exporterar cmdletar eller funktioner som har icke godkända verb i sina namn, `Import-Module` visar cmdleten följande varnings meddelande.</span><span class="sxs-lookup"><span data-stu-id="e8f38-262">If the module that you import exports cmdlets or functions that have unapproved verbs in their names, the `Import-Module` cmdlet displays the following warning message.</span></span>

> <span data-ttu-id="e8f38-263">Varning! vissa importerade kommando namn innehåller icke-godkända verb som kan göra dem mindre synliga.</span><span class="sxs-lookup"><span data-stu-id="e8f38-263">WARNING: Some imported command names include unapproved verbs which might make them less discoverable.</span></span> <span data-ttu-id="e8f38-264">Använd verbose-parametern för mer information eller Skriv Get-Verb om du vill visa en lista över godkända verb.</span><span class="sxs-lookup"><span data-stu-id="e8f38-264">Use the Verbose parameter for more detail or type Get-Verb to see the list of approved verbs.</span></span>

<span data-ttu-id="e8f38-265">Det här meddelandet är bara en varning.</span><span class="sxs-lookup"><span data-stu-id="e8f38-265">This message is only a warning.</span></span> <span data-ttu-id="e8f38-266">Den kompletta modulen importeras fortfarande, inklusive kommandon som inte överensstämmer.</span><span class="sxs-lookup"><span data-stu-id="e8f38-266">The complete module is still imported, including the non-conforming commands.</span></span> <span data-ttu-id="e8f38-267">Även om meddelandet visas för modulen användare, bör namngivnings problemet åtgärdas av den som skapade modulen.</span><span class="sxs-lookup"><span data-stu-id="e8f38-267">Although the message is displayed to module users, the naming problem should be fixed by the module author.</span></span>

<span data-ttu-id="e8f38-268">Om du vill utelämna varnings meddelandet använder du parametern **DisableNameChecking** för `Import-Module` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e8f38-268">To suppress the warning message, use the **DisableNameChecking** parameter of the `Import-Module` cmdlet.</span></span>

## <a name="built-in-modules-and-snap-ins"></a><span data-ttu-id="e8f38-269">Inbyggda moduler och snapin-moduler</span><span class="sxs-lookup"><span data-stu-id="e8f38-269">Built-in Modules and Snap-ins</span></span>

<span data-ttu-id="e8f38-270">I PowerShell 2,0 och i äldre värd program i PowerShell 3,0 och senare, paketeras de grundläggande kommandon som installeras med PowerShell i snapin-moduler som läggs till automatiskt till varje PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="e8f38-270">In PowerShell 2.0 and in older-style host programs in PowerShell 3.0 and later, the core commands that are installed with PowerShell are packaged in snap-ins that are added automatically to every PowerShell session.</span></span>

<span data-ttu-id="e8f38-271">Från och med PowerShell 3,0, för värd program som implementerar det `InitialSessionState.CreateDefault2` inledande session State-API: t, läggs Microsoft. PowerShell. Core-snapin-modulen till i varje session som standard.</span><span class="sxs-lookup"><span data-stu-id="e8f38-271">Beginning in PowerShell 3.0, for host programs that implement the `InitialSessionState.CreateDefault2` initial session state API the Microsoft.PowerShell.Core snap-in is added to every session by default.</span></span> <span data-ttu-id="e8f38-272">Moduler läses in automatiskt vid första användning.</span><span class="sxs-lookup"><span data-stu-id="e8f38-272">Modules are loaded automatically on first-use.</span></span>

> [!NOTE]
> <span data-ttu-id="e8f38-273">Fjärrsessioner, inklusive sessioner som startas med hjälp av `New-PSSession` cmdleten, är äldre sessioner där de inbyggda kommandona paketeras i snapin-moduler.</span><span class="sxs-lookup"><span data-stu-id="e8f38-273">Remote sessions, including sessions that are started by using the `New-PSSession` cmdlet, are older-style sessions in which the built-in commands are packaged in snap-ins.</span></span>

<span data-ttu-id="e8f38-274">Följande moduler (eller snapin-moduler) installeras med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e8f38-274">The following modules (or snap-ins) are installed with PowerShell.</span></span>

- <span data-ttu-id="e8f38-275">CimCmdlets</span><span class="sxs-lookup"><span data-stu-id="e8f38-275">CimCmdlets</span></span>
- <span data-ttu-id="e8f38-276">Microsoft. PowerShell. Archive</span><span class="sxs-lookup"><span data-stu-id="e8f38-276">Microsoft.PowerShell.Archive</span></span>
- <span data-ttu-id="e8f38-277">Microsoft. PowerShell. Core</span><span class="sxs-lookup"><span data-stu-id="e8f38-277">Microsoft.PowerShell.Core</span></span>
- <span data-ttu-id="e8f38-278">Microsoft. PowerShell. Diagnostics</span><span class="sxs-lookup"><span data-stu-id="e8f38-278">Microsoft.PowerShell.Diagnostics</span></span>
- <span data-ttu-id="e8f38-279">Microsoft. PowerShell. Host</span><span class="sxs-lookup"><span data-stu-id="e8f38-279">Microsoft.PowerShell.Host</span></span>
- <span data-ttu-id="e8f38-280">Microsoft. PowerShell. Management</span><span class="sxs-lookup"><span data-stu-id="e8f38-280">Microsoft.PowerShell.Management</span></span>
- <span data-ttu-id="e8f38-281">Microsoft. PowerShell. Security</span><span class="sxs-lookup"><span data-stu-id="e8f38-281">Microsoft.PowerShell.Security</span></span>
- <span data-ttu-id="e8f38-282">Microsoft.PowerShell.Utility</span><span class="sxs-lookup"><span data-stu-id="e8f38-282">Microsoft.PowerShell.Utility</span></span>
- <span data-ttu-id="e8f38-283">Microsoft. WSMan. Management</span><span class="sxs-lookup"><span data-stu-id="e8f38-283">Microsoft.WSMan.Management</span></span>
- <span data-ttu-id="e8f38-284">PackageManagement</span><span class="sxs-lookup"><span data-stu-id="e8f38-284">PackageManagement</span></span>
- <span data-ttu-id="e8f38-285">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="e8f38-285">PowerShellGet</span></span>
- <span data-ttu-id="e8f38-286">PSDesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e8f38-286">PSDesiredStateConfiguration</span></span>
- <span data-ttu-id="e8f38-287">PSDiagnostics</span><span class="sxs-lookup"><span data-stu-id="e8f38-287">PSDiagnostics</span></span>
- <span data-ttu-id="e8f38-288">PSReadline</span><span class="sxs-lookup"><span data-stu-id="e8f38-288">PSReadline</span></span>

## <a name="logging-module-events"></a><span data-ttu-id="e8f38-289">Loggning av module-händelser</span><span class="sxs-lookup"><span data-stu-id="e8f38-289">Logging Module Events</span></span>

<span data-ttu-id="e8f38-290">Från och med PowerShell 3,0 kan du registrera körnings händelser för cmdlets och Functions i PowerShell-moduler och snapin-moduler genom att ange egenskapen **LogPipelineExecutionDetails** för moduler och snapin-moduler till `$True` .</span><span class="sxs-lookup"><span data-stu-id="e8f38-290">Beginning in PowerShell 3.0, you can record execution events for the cmdlets and functions in PowerShell modules and snap-ins by setting the **LogPipelineExecutionDetails** property of modules and snap-ins to `$True`.</span></span>
<span data-ttu-id="e8f38-291">Du kan också använda en grupprincip inställning, aktivera modulreferensen för att aktivera modul loggning i alla PowerShell-sessioner.</span><span class="sxs-lookup"><span data-stu-id="e8f38-291">You can also use a Group Policy setting, Turn on Module Logging, to enable module logging in all PowerShell sessions.</span></span> <span data-ttu-id="e8f38-292">Mer information finns i artikeln om loggning och grup principer.</span><span class="sxs-lookup"><span data-stu-id="e8f38-292">For more information, see the logging and group policy articles.</span></span>

## <a name="see-also"></a><span data-ttu-id="e8f38-293">Se även</span><span class="sxs-lookup"><span data-stu-id="e8f38-293">See Also</span></span>

[<span data-ttu-id="e8f38-294">about_Logging_Windows</span><span class="sxs-lookup"><span data-stu-id="e8f38-294">about_Logging_Windows</span></span>](about_Logging_Windows.md)

[<span data-ttu-id="e8f38-295">about_Logging_Non-Windows</span><span class="sxs-lookup"><span data-stu-id="e8f38-295">about_Logging_Non-Windows</span></span>](about_Logging_Non-Windows.md)

[<span data-ttu-id="e8f38-296">about_Group_Policy_Settings</span><span class="sxs-lookup"><span data-stu-id="e8f38-296">about_Group_Policy_Settings</span></span>](about_Group_Policy_Settings.md)

[<span data-ttu-id="e8f38-297">about_Command_Precedence</span><span class="sxs-lookup"><span data-stu-id="e8f38-297">about_Command_Precedence</span></span>](about_Command_Precedence.md)

[<span data-ttu-id="e8f38-298">about_Group_Policy_Settings</span><span class="sxs-lookup"><span data-stu-id="e8f38-298">about_Group_Policy_Settings</span></span>](about_Group_Policy_Settings.md)

[<span data-ttu-id="e8f38-299">Get-Command</span><span class="sxs-lookup"><span data-stu-id="e8f38-299">Get-Command</span></span>](xref:Microsoft.PowerShell.Core.Get-Command)

[<span data-ttu-id="e8f38-300">Get – hjälp</span><span class="sxs-lookup"><span data-stu-id="e8f38-300">Get-Help</span></span>](xref:Microsoft.PowerShell.Core.Get-Help)

[<span data-ttu-id="e8f38-301">Hämta modul</span><span class="sxs-lookup"><span data-stu-id="e8f38-301">Get-Module</span></span>](xref:Microsoft.PowerShell.Core.Get-Module)

[<span data-ttu-id="e8f38-302">Importera-modul</span><span class="sxs-lookup"><span data-stu-id="e8f38-302">Import-Module</span></span>](xref:Microsoft.PowerShell.Core.Import-Module)

[<span data-ttu-id="e8f38-303">Ta bort modul</span><span class="sxs-lookup"><span data-stu-id="e8f38-303">Remove-Module</span></span>](xref:Microsoft.PowerShell.Core.Remove-Module)