---
description: Förklarar hur du installerar, importerar och använder PowerShell-moduler.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 07/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_modules?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Modules
ms.openlocfilehash: 2668c722bfc7bb49517054767491a17a716a0720
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93272103"
---
# <a name="about-modules"></a><span data-ttu-id="4cfbf-104">Om moduler</span><span class="sxs-lookup"><span data-stu-id="4cfbf-104">About Modules</span></span>

## <a name="short-description"></a><span data-ttu-id="4cfbf-105">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="4cfbf-105">Short Description</span></span>
<span data-ttu-id="4cfbf-106">Förklarar hur du installerar, importerar och använder PowerShell-moduler.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-106">Explains how to install, import, and use PowerShell modules.</span></span>

## <a name="long-description"></a><span data-ttu-id="4cfbf-107">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="4cfbf-107">Long Description</span></span>

<span data-ttu-id="4cfbf-108">En modul är ett paket som innehåller PowerShell-kommandon, till exempel cmdlets, providrar, funktioner, arbets flöden, variabler och alias.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-108">A module is a package that contains PowerShell commands, such as cmdlets, providers, functions, workflows, variables, and aliases.</span></span>

<span data-ttu-id="4cfbf-109">Personer som skriver kommandon kan använda moduler för att organisera sina kommandon och dela dem med andra.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-109">People who write commands can use modules to organize their commands and share them with others.</span></span> <span data-ttu-id="4cfbf-110">Personer som tar emot moduler kan lägga till kommandon i modulerna i sina PowerShell-sessioner och använda dem precis som de inbyggda kommandona.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-110">People who receive modules can add the commands in the modules to their PowerShell sessions and use them just like the built-in commands.</span></span>

<span data-ttu-id="4cfbf-111">I det här avsnittet beskrivs hur du använder PowerShell-moduler.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-111">This topic explains how to use PowerShell modules.</span></span> <span data-ttu-id="4cfbf-112">Information om hur du skriver PowerShell-moduler finns i [skriva en PowerShell-modul](/powershell/scripting/developer/module/writing-a-windows-powershell-module).</span><span class="sxs-lookup"><span data-stu-id="4cfbf-112">For information about how to write PowerShell modules, see [Writing a PowerShell Module](/powershell/scripting/developer/module/writing-a-windows-powershell-module).</span></span>

## <a name="what-is-a-module"></a><span data-ttu-id="4cfbf-113">Vad är en modul?</span><span class="sxs-lookup"><span data-stu-id="4cfbf-113">What Is a Module?</span></span>

<span data-ttu-id="4cfbf-114">En modul är ett paket med kommandon.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-114">A module is a package of commands.</span></span> <span data-ttu-id="4cfbf-115">Alla cmdlets och providers i din session läggs till av en modul eller en snapin-modul.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-115">All cmdlets and providers in your session are added by a module or a snap-in.</span></span>

## <a name="module-auto-loading"></a><span data-ttu-id="4cfbf-116">Automatisk inläsning av modul</span><span class="sxs-lookup"><span data-stu-id="4cfbf-116">Module Auto-Loading</span></span>

<span data-ttu-id="4cfbf-117">Från och med PowerShell 3,0 importerar PowerShell moduler automatiskt första gången du kör ett kommando i en installerad modul.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-117">Beginning in PowerShell 3.0, PowerShell imports modules automatically the first time that you run any command in an installed module.</span></span> <span data-ttu-id="4cfbf-118">Du kan nu använda kommandona i en modul utan konfigurations konfiguration eller profil, så du behöver inte hantera moduler när du har installerat dem på din dator.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-118">You can now use the commands in a module without any set-up or profile configuration, so there's no need to manage modules after you install them on your computer.</span></span>

<span data-ttu-id="4cfbf-119">Kommandona i en modul är också lättare att hitta.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-119">The commands in a module are also easier to find.</span></span> <span data-ttu-id="4cfbf-120">`Get-Command`Cmdleten hämtar nu alla kommandon i alla installerade moduler, även om de inte finns i sessionen än, så att du kan hitta ett kommando och använda det utan att importera.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-120">The `Get-Command` cmdlet now gets all commands in all installed modules, even if they are not yet in the session, so you can find a command and use it without importing.</span></span>

<span data-ttu-id="4cfbf-121">Vart och ett av följande exempel orsakar CimCmdlets-modulen, som innehåller, som ska `Get-CimInstance` importeras till sessionen.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-121">Each of the following examples cause the CimCmdlets module, which contains `Get-CimInstance`, to be imported into your session.</span></span>

- <span data-ttu-id="4cfbf-122">Kör kommandot</span><span class="sxs-lookup"><span data-stu-id="4cfbf-122">Run the Command</span></span>

  ```powershell
  Get-CimInstance Win32_OperatingSystem
  ```

- <span data-ttu-id="4cfbf-123">Hämta kommandot</span><span class="sxs-lookup"><span data-stu-id="4cfbf-123">Get the Command</span></span>

  ```powershell
  Get-Command Get-CimInstance
  ```

- <span data-ttu-id="4cfbf-124">Få hjälp med kommandot</span><span class="sxs-lookup"><span data-stu-id="4cfbf-124">Get Help for the Command</span></span>

  ```powershell
  Get-Help Get-CimInstance
  ```

<span data-ttu-id="4cfbf-125">`Get-Command` kommandon som innehåller ett jokertecken ( `*` ) anses vara för identifiering, används inte och importerar inte några moduler.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-125">`Get-Command` commands that include a wildcard character (`*`) are considered to be for discovery, not use, and do not import any modules.</span></span>

<span data-ttu-id="4cfbf-126">Endast moduler som lagras på den plats som anges av PSModulePath-miljövariabeln importeras automatiskt.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-126">Only modules that are stored in the location specified by the PSModulePath environment variable are automatically imported.</span></span> <span data-ttu-id="4cfbf-127">Moduler på andra platser måste importeras genom att köra `Import-Module` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-127">Modules in other locations must be imported by running the `Import-Module` cmdlet.</span></span>

<span data-ttu-id="4cfbf-128">Kommandon som använder PowerShell-leverantörer importerar dessutom inte automatiskt en modul.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-128">Also, commands that use PowerShell providers do not automatically import a module.</span></span> <span data-ttu-id="4cfbf-129">Om du till exempel använder ett kommando som kräver WSMan:-enheten, till exempel `Get-PSSessionConfiguration` cmdleten, kan du behöva köra `Import-Module` cmdleten för att importera **Microsoft. WSMan. Management** -modulen som innehåller `WSMan:` enheten.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-129">For example, if you use a command that requires the WSMan: drive, such as the `Get-PSSessionConfiguration` cmdlet, you might need to run the `Import-Module` cmdlet to import the **Microsoft.WSMan.Management** module that includes the `WSMan:` drive.</span></span>

<span data-ttu-id="4cfbf-130">Du kan fortfarande köra `Import-Module` kommandot för att importera en modul och använda `$PSModuleAutoloadingPreference` variabeln för att aktivera, inaktivera och konfigurera automatisk import av moduler.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-130">You can still run the `Import-Module` command to import a module and use the `$PSModuleAutoloadingPreference` variable to enable, disable and configure automatic importing of modules.</span></span> <span data-ttu-id="4cfbf-131">Mer information finns i [about_Preference_Variables](about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="4cfbf-131">For more information, see [about_Preference_Variables](about_Preference_Variables.md).</span></span>

## <a name="how-to-use-a-module"></a><span data-ttu-id="4cfbf-132">Använda en modul</span><span class="sxs-lookup"><span data-stu-id="4cfbf-132">How to Use a Module</span></span>

<span data-ttu-id="4cfbf-133">Utför följande uppgifter om du vill använda en modul:</span><span class="sxs-lookup"><span data-stu-id="4cfbf-133">To use a module, perform the following tasks:</span></span>

1. <span data-ttu-id="4cfbf-134">Installera modulen.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-134">Install the module.</span></span> <span data-ttu-id="4cfbf-135">(Detta görs ofta åt dig.)</span><span class="sxs-lookup"><span data-stu-id="4cfbf-135">(This is often done for you.)</span></span>
1. <span data-ttu-id="4cfbf-136">Hitta de kommandon som modulen har lagt till.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-136">Find the commands that the module added.</span></span>
1. <span data-ttu-id="4cfbf-137">Använd de kommandon som modulen har lagt till.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-137">Use the commands that the module added.</span></span>

<span data-ttu-id="4cfbf-138">I det här avsnittet beskrivs hur du utför dessa uppgifter.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-138">This topic explains how to perform these tasks.</span></span> <span data-ttu-id="4cfbf-139">Den innehåller även annan användbar information om hur du hanterar moduler.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-139">It also includes other useful information about managing modules.</span></span>

## <a name="how-to-install-a-module"></a><span data-ttu-id="4cfbf-140">Så här installerar du en modul</span><span class="sxs-lookup"><span data-stu-id="4cfbf-140">How to Install a Module</span></span>

<span data-ttu-id="4cfbf-141">Om du får en modul som en mapp med filer i den måste du installera den på datorn innan du kan använda den i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-141">If you receive a module as a folder with files in it, you need to install it on your computer before you can use it in PowerShell.</span></span>

<span data-ttu-id="4cfbf-142">De flesta moduler är installerade åt dig.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-142">Most modules are installed for you.</span></span> <span data-ttu-id="4cfbf-143">PowerShell innehåller flera förinstallerade moduler, ibland kallade _Core_ -moduler.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-143">PowerShell comes with several preinstalled modules, sometimes called the _core_ modules.</span></span> <span data-ttu-id="4cfbf-144">På Windows-baserade datorer, om funktioner som ingår i operativ systemet har cmdlets för att hantera dem, förinstalleras dessa moduler.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-144">On Windows-based computers, if features that are included with the operating system have cmdlets to manage them, those modules are preinstalled.</span></span> <span data-ttu-id="4cfbf-145">När du installerar en Windows-funktion med hjälp av, till exempel guiden Lägg till roller och funktioner i Serverhanteraren eller i dialog rutan Aktivera eller inaktivera Windows-funktioner på kontroll panelen, installeras alla PowerShell-moduler som ingår i funktionen.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-145">When you install a Windows feature, by using, for example, the Add Roles and Features Wizard in Server Manager, or the Turn Windows features on or off dialog box in Control Panel, any PowerShell modules that are part of the feature are installed.</span></span> <span data-ttu-id="4cfbf-146">Många andra moduler ingår i ett installations program eller installations program som installerar modulen.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-146">Many other modules come in an installer or Setup program that installs the module.</span></span>

<span data-ttu-id="4cfbf-147">Använd följande kommando för att skapa en **modul** -katalog för den aktuella användaren:</span><span class="sxs-lookup"><span data-stu-id="4cfbf-147">Use the following command to create a **Modules** directory for the current user:</span></span>

```powershell
New-Item -Type Directory -Path $HOME\Documents\WindowsPowerShell\Modules
```

<span data-ttu-id="4cfbf-148">Kopiera hela modul-mappen till katalogen modules.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-148">Copy the entire module folder into the Modules directory.</span></span> <span data-ttu-id="4cfbf-149">Du kan använda valfri metod för att kopiera mappen, inklusive Windows Explorer och Cmd.exe, samt PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-149">You can use any method to copy the folder, including Windows Explorer and Cmd.exe, as well as PowerShell.</span></span> <span data-ttu-id="4cfbf-150">I PowerShell använder du `Copy-Item` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-150">In PowerShell use the `Copy-Item` cmdlet.</span></span> <span data-ttu-id="4cfbf-151">Om du till exempel vill kopiera mappen för mina `C:\ps-test\MyModule` moduler från till katalogen moduler skriver du:</span><span class="sxs-lookup"><span data-stu-id="4cfbf-151">For example, to copy the MyModule folder from `C:\ps-test\MyModule` to the Modules directory, type:</span></span>

```powershell
Copy-Item -Path C:\ps-test\MyModule -Destination `
    $HOME\Documents\WindowsPowerShell\Modules
```

<span data-ttu-id="4cfbf-152">Du kan installera en modul på vilken plats som helst, men om du installerar modulerna på en standardmodul blir det enklare att hantera dem.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-152">You can install a module in any location, but installing your modules in a default module location makes them easier to manage.</span></span> <span data-ttu-id="4cfbf-153">Mer information om standardmodulens platser finns i modulen för [modul-och DSC-resurser och PSModulePath-](#module-and-dsc-resource-locations-and-psmodulepath) avsnittet.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-153">For more information about the default module locations, see the [Module and DSC Resource Locations, and PSModulePath](#module-and-dsc-resource-locations-and-psmodulepath) section.</span></span>

## <a name="how-to-find-installed-modules"></a><span data-ttu-id="4cfbf-154">Så här hittar du installerade moduler</span><span class="sxs-lookup"><span data-stu-id="4cfbf-154">How to Find Installed Modules</span></span>

<span data-ttu-id="4cfbf-155">Om du vill hitta moduler som är installerade på en standardmodul, men som ännu inte har importer ATS till din session, skriver du:</span><span class="sxs-lookup"><span data-stu-id="4cfbf-155">To find modules that are installed in a default module location, but not yet imported into your session, type:</span></span>

```powershell
Get-Module -ListAvailable
```

<span data-ttu-id="4cfbf-156">Om du vill hitta de moduler som redan har importer ATS till din-session skriver du följande i PowerShell-prompten:</span><span class="sxs-lookup"><span data-stu-id="4cfbf-156">To find the modules that have already been imported into your session, at the PowerShell prompt, type:</span></span>

```powershell
Get-Module
```

<span data-ttu-id="4cfbf-157">Mer information om `Get-Module` cmdleten finns i [Get-module](xref:Microsoft.PowerShell.Core.Get-Module).</span><span class="sxs-lookup"><span data-stu-id="4cfbf-157">For more information about the `Get-Module` cmdlet, see [Get-Module](xref:Microsoft.PowerShell.Core.Get-Module).</span></span>

## <a name="how-to-find-the-commands-in-a-module"></a><span data-ttu-id="4cfbf-158">Så här hittar du kommandon i en modul</span><span class="sxs-lookup"><span data-stu-id="4cfbf-158">How to Find the Commands in a Module</span></span>

<span data-ttu-id="4cfbf-159">Använd `Get-Command` cmdleten för att hitta alla tillgängliga kommandon.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-159">Use the `Get-Command` cmdlet to find all available commands.</span></span> <span data-ttu-id="4cfbf-160">Du kan använda parametrarna för `Get-Command` cmdlet: en för att filtrera kommandon som till exempel efter modul, namn och substantiv.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-160">You can use the parameters of the `Get-Command` cmdlet to filter commands such as by module, name, and noun.</span></span>

<span data-ttu-id="4cfbf-161">Om du vill söka efter alla kommandon i en modul skriver du:</span><span class="sxs-lookup"><span data-stu-id="4cfbf-161">To find all commands in a module, type:</span></span>

```powershell
Get-Command -Module <module-name>
```

<span data-ttu-id="4cfbf-162">Om du till exempel vill hitta kommandona i BitsTransfer-modulen skriver du:</span><span class="sxs-lookup"><span data-stu-id="4cfbf-162">For example, to find the commands in the BitsTransfer module, type:</span></span>

```powershell
Get-Command -Module BitsTransfer
```

<span data-ttu-id="4cfbf-163">Mer information om `Get-Command` cmdleten finns i [Get-Command](xref:Microsoft.PowerShell.Core.Get-Command).</span><span class="sxs-lookup"><span data-stu-id="4cfbf-163">For more information about the `Get-Command` cmdlet, see [Get-Command](xref:Microsoft.PowerShell.Core.Get-Command).</span></span>

## <a name="how-to-get-help-for-the-commands-in-a-module"></a><span data-ttu-id="4cfbf-164">Så här får du hjälp med kommandon i en modul</span><span class="sxs-lookup"><span data-stu-id="4cfbf-164">How to Get Help for the Commands in a Module</span></span>

<span data-ttu-id="4cfbf-165">Om modulen innehåller hjälpfiler för de kommandon som den exporterar, `Get-Help` visas hjälp avsnitten i cmdleten.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-165">If the module contains Help files for the commands that it exports, the `Get-Help` cmdlet will display the Help topics.</span></span> <span data-ttu-id="4cfbf-166">Använd samma `Get-Help` kommando format som du kan använda för att få hjälp med kommandon i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-166">Use the same `Get-Help` command format that you would use to get help for any command in PowerShell.</span></span>

<span data-ttu-id="4cfbf-167">Från och med PowerShell 3,0 kan du hämta hjälpfiler för en modul och ladda ned uppdateringar till hjälpfilerna så att de aldrig är föråldrade.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-167">Beginning in PowerShell 3.0, you can download Help files for a module and download updates to the Help files so they are never obsolete.</span></span>

<span data-ttu-id="4cfbf-168">Om du vill ha hjälp med kommandon i en modul skriver du:</span><span class="sxs-lookup"><span data-stu-id="4cfbf-168">To get help for a commands in a module, type:</span></span>

```powershell
Get-Help <command-name>
```

<span data-ttu-id="4cfbf-169">Om du vill få hjälp online för kommandot i en modul skriver du:</span><span class="sxs-lookup"><span data-stu-id="4cfbf-169">To get help online for command in a module, type:</span></span>

```powershell
Get-Help <command-name> -Online
```

<span data-ttu-id="4cfbf-170">Om du vill hämta och installera hjälpfilerna för kommandon i en modul skriver du:</span><span class="sxs-lookup"><span data-stu-id="4cfbf-170">To download and install the help files for the commands in a module, type:</span></span>

```powershell
Update-Help -Module <module-name>
```

<span data-ttu-id="4cfbf-171">Mer information finns i [få hjälp](xref:Microsoft.PowerShell.Core.Get-Help) och [Uppdatera – hjälp](xref:Microsoft.PowerShell.Core.Update-Help).</span><span class="sxs-lookup"><span data-stu-id="4cfbf-171">For more information, see [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) and [Update-Help](xref:Microsoft.PowerShell.Core.Update-Help).</span></span>

## <a name="how-to-import-a-module"></a><span data-ttu-id="4cfbf-172">Så här importerar du en modul</span><span class="sxs-lookup"><span data-stu-id="4cfbf-172">How to Import a Module</span></span>

<span data-ttu-id="4cfbf-173">Du kan behöva importera en modul eller importera en modul-fil.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-173">You might have to import a module or import a module file.</span></span> <span data-ttu-id="4cfbf-174">Import krävs när en modul inte är installerad på de platser som anges av **PSModulePath** -miljövariabeln, `$env:PSModulePath` eller om modulen består av en fil, till exempel en. dll-eller. psm1-fil, i stället för en typisk modul som levereras som en mapp.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-174">Importing is required when a module is not installed in the locations specified by the **PSModulePath** environment variable, `$env:PSModulePath`, or the module consists of file, such as a .dll or .psm1 file, instead of typical module that is delivered as a folder.</span></span>

<span data-ttu-id="4cfbf-175">Du kan också välja att importera en modul så att du kan använda parametrarna för `Import-Module` kommandot, till exempel parametern prefix, som lägger till ett särskiljande prefix till Substantiv namnen för alla importerade kommandon, eller parametern **NoClobber** , som förhindrar att modulen lägger till kommandon som döljer eller ersätter befintliga kommandon i sessionen.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-175">You might also choose to import a module so that you can use the parameters of the `Import-Module` command, such as the Prefix parameter, which adds a distinctive prefix to the noun names of all imported commands, or the **NoClobber** parameter, which prevents the module from adding commands that would hide or replace existing commands in the session.</span></span>

<span data-ttu-id="4cfbf-176">Använd cmdleten för att importera moduler `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="4cfbf-176">To import modules, use the `Import-Module` cmdlet.</span></span>

<span data-ttu-id="4cfbf-177">Om du vill importera moduler på en PSModulePath plats till den aktuella sessionen använder du följande kommando format.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-177">To import modules in a PSModulePath location into the current session, use the following command format.</span></span>

```powershell
Import-Module <module-name>
```

<span data-ttu-id="4cfbf-178">Följande kommando importerar till exempel modulen BitsTransfer till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-178">For example, the following command imports the BitsTransfer module into the current session.</span></span>

```powershell
Import-Module BitsTransfer
```

<span data-ttu-id="4cfbf-179">Om du vill importera en modul som inte finns på en standardmodul, använder du den fullständiga sökvägen till mappen modul i kommandot.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-179">To import a module that is not in a default module location, use the fully qualified path to the module folder in the command.</span></span>

<span data-ttu-id="4cfbf-180">Om du till exempel vill lägga till modulen TestCmdlets i `C:\ps-test` katalogen i din session skriver du:</span><span class="sxs-lookup"><span data-stu-id="4cfbf-180">For example, to add the TestCmdlets module in the `C:\ps-test` directory to your session, type:</span></span>

```powershell
Import-Module C:\ps-test\TestCmdlets
```

<span data-ttu-id="4cfbf-181">Om du vill importera en modul som inte finns i en modul-mapp använder du den fullständiga sökvägen till filen i kommandot.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-181">To import a module file that is not contained in a module folder, use the fully qualified path to the module file in the command.</span></span>

<span data-ttu-id="4cfbf-182">Om du till exempel vill lägga till modulen TestCmdlets.dll i `C:\ps-test` katalogen i din session skriver du:</span><span class="sxs-lookup"><span data-stu-id="4cfbf-182">For example, to add the TestCmdlets.dll module in the `C:\ps-test` directory to your session, type:</span></span>

```powershell
Import-Module C:\ps-test\TestCmdlets.dll
```

<span data-ttu-id="4cfbf-183">Mer information om hur du lägger till moduler i din session finns i [import-module](xref:Microsoft.PowerShell.Core.Import-Module).</span><span class="sxs-lookup"><span data-stu-id="4cfbf-183">For more information about adding modules to your session, see [Import-Module](xref:Microsoft.PowerShell.Core.Import-Module).</span></span>

## <a name="how-to-import-a-module-into-every-session"></a><span data-ttu-id="4cfbf-184">Så här importerar du en modul till varje session</span><span class="sxs-lookup"><span data-stu-id="4cfbf-184">How to Import a Module into Every Session</span></span>

<span data-ttu-id="4cfbf-185">`Import-Module`Kommandot importerar moduler till din aktuella PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-185">The `Import-Module` command imports modules into your current PowerShell session.</span></span> <span data-ttu-id="4cfbf-186">Om du vill importera en modul till varje PowerShell-session som du startar lägger du till `Import-Module` kommandot i din PowerShell-profil.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-186">To import a module into every PowerShell session that you start, add the `Import-Module` command to your PowerShell profile.</span></span>

<span data-ttu-id="4cfbf-187">Mer information om profiler finns [about_Profiles](about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="4cfbf-187">For more information about profiles, see [about_Profiles](about_Profiles.md).</span></span>

## <a name="how-to-remove-a-module"></a><span data-ttu-id="4cfbf-188">Ta bort en modul</span><span class="sxs-lookup"><span data-stu-id="4cfbf-188">How to Remove a Module</span></span>

<span data-ttu-id="4cfbf-189">När du tar bort en modul tas de kommandon som läggs till i modulen bort från sessionen.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-189">When you remove a module, the commands that the module added are deleted from the session.</span></span>

<span data-ttu-id="4cfbf-190">Om du vill ta bort en modul från sessionen använder du följande kommando format.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-190">To remove a module from your session, use the following command format.</span></span>

```powershell
Remove-Module <module-name>
```

<span data-ttu-id="4cfbf-191">Följande kommando tar till exempel bort modulen BitsTransfer från den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-191">For example, the following command removes the BitsTransfer module from the current session.</span></span>

```powershell
Remove-Module BitsTransfer
```

<span data-ttu-id="4cfbf-192">Om du tar bort en modul ångras åtgärden för att importera en modul.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-192">Removing a module reverses the operation of importing a module.</span></span> <span data-ttu-id="4cfbf-193">Att ta bort en modul avinstallerar inte modulen.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-193">Removing a module does not uninstall the module.</span></span> <span data-ttu-id="4cfbf-194">Mer information finns i [Remove-module](xref:Microsoft.PowerShell.Core.Remove-Module).</span><span class="sxs-lookup"><span data-stu-id="4cfbf-194">For more information, see [Remove-Module](xref:Microsoft.PowerShell.Core.Remove-Module).</span></span>

## <a name="module-and-dsc-resource-locations-and-psmodulepath"></a><span data-ttu-id="4cfbf-195">Modul-och DSC-resurs platser och PSModulePath</span><span class="sxs-lookup"><span data-stu-id="4cfbf-195">Module and DSC Resource Locations, and PSModulePath</span></span>

<span data-ttu-id="4cfbf-196">`$env:PSModulePath`Miljövariabeln innehåller en lista över mappar som genomsöks för att hitta moduler och resurser.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-196">The `$env:PSModulePath` environment variable contains a list of folder locations that are searched to find modules and resources.</span></span>

<span data-ttu-id="4cfbf-197">Som standard är de effektiva platser som `$env:PSModulePath` är tilldelade:</span><span class="sxs-lookup"><span data-stu-id="4cfbf-197">By default, the effective locations assigned to `$env:PSModulePath` are:</span></span>

- <span data-ttu-id="4cfbf-198">Platser i hela systemet: `$PSHOME\Modules`</span><span class="sxs-lookup"><span data-stu-id="4cfbf-198">System-wide locations: `$PSHOME\Modules`</span></span>

  <span data-ttu-id="4cfbf-199">Dessa mappar innehåller moduler som levereras med Windows och PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-199">These folders contain modules that ship with Windows and PowerShell.</span></span>

  <span data-ttu-id="4cfbf-200">DSC-resurser som ingår i PowerShell lagras i `$PSHOME\Modules\PSDesiredStateConfiguration\DSCResources` mappen.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-200">DSC resources that are included with PowerShell are stored in the `$PSHOME\Modules\PSDesiredStateConfiguration\DSCResources` folder.</span></span>

- <span data-ttu-id="4cfbf-201">Användarspecifika moduler: de här är moduler som installeras av användaren i användarens omfång.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-201">User-specific modules: These are modules installed by the user in the user's scope.</span></span> <span data-ttu-id="4cfbf-202">`Install-Module` har en **omfattnings** parameter som gör att du kan ange om modulen är installerad för den aktuella användaren eller för alla användare.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-202">`Install-Module` has a **Scope** parameter that allows you to specify whether the module is installed for the current user or for all users.</span></span> <span data-ttu-id="4cfbf-203">Mer information finns i [install-module](xref:PowerShellGet.Install-Module).</span><span class="sxs-lookup"><span data-stu-id="4cfbf-203">For more information, see [Install-Module](xref:PowerShellGet.Install-Module).</span></span>

  <span data-ttu-id="4cfbf-204">Den användarspecifika **CurrentUser** -platsen i Windows är `PowerShell\Modules` mappen som finns på **dokument** platsen i din användar profil.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-204">The user-specific **CurrentUser** location on Windows is the `PowerShell\Modules` folder located in the **Documents** location in your user profile.</span></span> <span data-ttu-id="4cfbf-205">Den angivna sökvägen till platsen varierar efter Windows-version och om du använder mappomdirigering.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-205">The specific path of that location varies by version of Windows and whether or not you are using folder redirection.</span></span> <span data-ttu-id="4cfbf-206">Microsoft OneDrive kan också ändra platsen för mappen **dokument** .</span><span class="sxs-lookup"><span data-stu-id="4cfbf-206">Microsoft OneDrive can also change the location of your **Documents** folder.</span></span>

  <span data-ttu-id="4cfbf-207">Som standard är den platsen i Windows 10 `$HOME\Documents\PowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="4cfbf-207">By default, on Windows 10, that location is `$HOME\Documents\PowerShell\Modules`.</span></span> <span data-ttu-id="4cfbf-208">På Linux eller Mac är **CurrentUser** -platsen `$HOME/.local/share/powershell/Modules` .</span><span class="sxs-lookup"><span data-stu-id="4cfbf-208">On Linux or Mac, the **CurrentUser** location is `$HOME/.local/share/powershell/Modules`.</span></span>

  > [!NOTE]
  > <span data-ttu-id="4cfbf-209">Du kan kontrol lera platsen för mappen **dokument** med hjälp av följande kommando: `[Environment]::GetFolderPath('MyDocuments')` .</span><span class="sxs-lookup"><span data-stu-id="4cfbf-209">You can verify the location of your **Documents** folder using the following command: `[Environment]::GetFolderPath('MyDocuments')`.</span></span>

- <span data-ttu-id="4cfbf-210">**Allusers** -platsen finns `$env:PROGRAMFILES\WindowsPowerShell\Modules` i Windows.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-210">The **AllUsers** location is `$env:PROGRAMFILES\WindowsPowerShell\Modules` on Windows.</span></span>

> [!NOTE]
> <span data-ttu-id="4cfbf-211">Om du vill lägga till eller ändra filer i `$env:Windir\System32` katalogen startar du PowerShell med alternativet **Kör som administratör** .</span><span class="sxs-lookup"><span data-stu-id="4cfbf-211">To add or change files in the `$env:Windir\System32` directory, start PowerShell with the **Run as administrator** option.</span></span>

<span data-ttu-id="4cfbf-212">Du kan ändra standard platserna för modulen i systemet genom att ändra värdet för **PSModulePath** -miljövariabeln `$Env:PSModulePath` .</span><span class="sxs-lookup"><span data-stu-id="4cfbf-212">You can change the default module locations on your system by changing the value of the **PSModulePath** environment variable, `$Env:PSModulePath`.</span></span> <span data-ttu-id="4cfbf-213">Miljövariabeln **PSModulePath** är modellerad i miljövariabeln PATH och har samma format.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-213">The **PSModulePath** environment variable is modeled on the Path environment variable and has the same format.</span></span>

<span data-ttu-id="4cfbf-214">Om du vill visa standard platserna för modulen skriver du:</span><span class="sxs-lookup"><span data-stu-id="4cfbf-214">To view the default module locations, type:</span></span>

```powershell
$Env:PSModulePath
```

<span data-ttu-id="4cfbf-215">Använd följande kommando format om du vill lägga till en standard-modul.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-215">To add a default module location, use the following command format.</span></span>

```powershell
$Env:PSModulePath = $Env:PSModulePath + ";<path>"
```

<span data-ttu-id="4cfbf-216">Semikolon ( `;` ) i kommandot avgränsar den nya sökvägen från den sökväg som föregår den i listan.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-216">The semi-colon (`;`) in the command separates the new path from the path that precedes it in the list.</span></span>

<span data-ttu-id="4cfbf-217">Om du till exempel vill lägga till `C:\ps-test\Modules` katalogen skriver du:</span><span class="sxs-lookup"><span data-stu-id="4cfbf-217">For example, to add the `C:\ps-test\Modules` directory, type:</span></span>

```powershell
$Env:PSModulePath + ";C:\ps-test\Modules"
```

<span data-ttu-id="4cfbf-218">När du lägger till en sökväg **PSModulePath** i PSModulePath `Get-Module` och `Import-Module` kommandon innehåller moduler i den sökvägen.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-218">When you add a path to **PSModulePath** , `Get-Module` and `Import-Module` commands include modules in that path.</span></span>

<span data-ttu-id="4cfbf-219">Värdet som du anger påverkar endast den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-219">The value that you set affects only the current session.</span></span> <span data-ttu-id="4cfbf-220">Om du vill göra ändringen permanent lägger du till kommandot i din PowerShell-profil eller använder system på kontroll panelen för att ändra värdet för **PSModulePath** -miljövariabeln i registret.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-220">To make the change persistent, add the command to your PowerShell profile or use System in Control Panel to change the value of the **PSModulePath** environment variable in the registry.</span></span>

<span data-ttu-id="4cfbf-221">Om du vill göra ändringen beständig kan du också använda metoden **SetEnvironmentVariable** i klassen **system. Environment** för att lägga till en sökväg till **PSModulePath** -miljövariabeln.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-221">Also, to make the change persistent, you can also use the **SetEnvironmentVariable** method of the **System.Environment** class to add a Path to the **PSModulePath** environment variable.</span></span>

<span data-ttu-id="4cfbf-222">Mer information om variabeln **PSModulePath** finns i [about_Environment_Variables](about_Environment_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="4cfbf-222">For more information about the **PSModulePath** variable, see [about_Environment_Variables](about_Environment_Variables.md).</span></span>

## <a name="modules-and-name-conflicts"></a><span data-ttu-id="4cfbf-223">Moduler och namn konflikter</span><span class="sxs-lookup"><span data-stu-id="4cfbf-223">Modules and Name Conflicts</span></span>

<span data-ttu-id="4cfbf-224">Namn konflikter uppstår när mer än ett kommando i sessionen har samma namn.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-224">Name conflicts occur when more than one command in the session has the same name.</span></span> <span data-ttu-id="4cfbf-225">Om du importerar en modul uppstår en namn konflikt när kommandon i modulen har samma namn som kommandon eller objekt i sessionen.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-225">Importing a module causes a name conflict when commands in the module have the same names as commands or items in the session.</span></span>

<span data-ttu-id="4cfbf-226">Namn konflikter kan resultera i att kommandon döljs eller ersätts.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-226">Name conflicts can result in commands being hidden or replaced.</span></span>

### <a name="hidden"></a><span data-ttu-id="4cfbf-227">Dold</span><span class="sxs-lookup"><span data-stu-id="4cfbf-227">Hidden</span></span>

<span data-ttu-id="4cfbf-228">Ett kommando är dolt när det inte är det kommando som körs när du skriver kommandots namn, men du kan köra det med en annan metod, till exempel genom att kvalificera kommando namnet med namnet på modulen eller snapin-modulen där det kom.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-228">A command is hidden when it is not the command that runs when you type the command name, but you can run it by using another method, such as by qualifying the command name with the name of the module or snap-in in which it originated.</span></span>

### <a name="replaced"></a><span data-ttu-id="4cfbf-229">Ersätter</span><span class="sxs-lookup"><span data-stu-id="4cfbf-229">Replaced</span></span>

<span data-ttu-id="4cfbf-230">Ett kommando ersätts när du inte kan köra det eftersom det har skrivits över av ett kommando med samma namn.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-230">A command is replaced when you cannot run it because it has been overwritten by a command with the same name.</span></span> <span data-ttu-id="4cfbf-231">Även om du tar bort modulen som orsakade konflikten kan du inte köra ett ersatt kommando om du inte startar om sessionen.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-231">Even when you remove the module that caused the conflict, you cannot run a replaced command unless you restart the session.</span></span>

<span data-ttu-id="4cfbf-232">`Import-Module` kan lägga till kommandon som döljer och ersätter kommandon i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-232">`Import-Module` might add commands that hide and replace commands in the current session.</span></span> <span data-ttu-id="4cfbf-233">Dessutom kan kommandon i din session dölja kommandon som har lagts till i modulen.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-233">Also, commands in your session can hide commands that the module added.</span></span>

<span data-ttu-id="4cfbf-234">Använd parametern **all** för cmdleten om du vill identifiera namn konflikter `Get-Command` .</span><span class="sxs-lookup"><span data-stu-id="4cfbf-234">To detect name conflicts, use the **All** parameter of the `Get-Command` cmdlet.</span></span> <span data-ttu-id="4cfbf-235">Från och med PowerShell 3,0 `Get-Command` hämtas bara kommandon som körs när du skriver kommandots namn.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-235">Beginning in PowerShell 3.0, `Get-Command` gets only that commands that run when you type the command name.</span></span> <span data-ttu-id="4cfbf-236">Parametern **all** hämtar alla kommandon med det angivna namnet i sessionen.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-236">The **All** parameter gets all commands with the specific name in the session.</span></span>

<span data-ttu-id="4cfbf-237">Om du vill förhindra namn konflikter använder du **NoClobber** -eller **prefixvärde** -parametrarna för `Import-Module` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-237">To prevent name conflicts, use the **NoClobber** or **Prefix** parameters of the `Import-Module` cmdlet.</span></span> <span data-ttu-id="4cfbf-238">Parametern **prefix** lägger till ett prefix till namnen på importerade kommandon så att de är unika i sessionen.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-238">The **Prefix** parameter adds a prefix to the names of imported commands so that they are unique in the session.</span></span> <span data-ttu-id="4cfbf-239">**NoClobber** -parametern importerar inte några kommandon som döljer eller ersätter befintliga kommandon i sessionen.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-239">The **NoClobber** parameter does not import any commands that would hide or replace existing commands in the session.</span></span>

<span data-ttu-id="4cfbf-240">Du kan också använda **alias** -, **cmdlet** -, **Function** -och **Variable** -parametrarna för `Import-Module` för att välja de kommandon som du vill importera, och du kan utesluta kommandon som orsakar namn konflikter i sessionen.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-240">You can also use the **Alias** , **Cmdlet** , **Function** , and **Variable** parameters of `Import-Module` to select only the commands that you want to import, and you can exclude commands that cause name conflicts in your session.</span></span>

<span data-ttu-id="4cfbf-241">Modulens författare kan förhindra namn konflikter genom att använda **DefaultCommandPrefix** -egenskapen för modulens manifest för att lägga till ett standardprefix i alla kommando namn.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-241">Module authors can prevent name conflicts by using the **DefaultCommandPrefix** property of the module manifest to add a default prefix to all command names.</span></span>
<span data-ttu-id="4cfbf-242">Värdet för parametern **prefix** har företräde framför värdet för **DefaultCommandPrefix**.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-242">The value of the **Prefix** parameter takes precedence over the value of **DefaultCommandPrefix**.</span></span>

<span data-ttu-id="4cfbf-243">Även om ett kommando är dolt kan du köra det genom att kvalificera kommando namnet med namnet på modulen eller snapin-modulen där det kom.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-243">Even if a command is hidden, you can run it by qualifying the command name with the name of the module or snap-in in which it originated.</span></span>

<span data-ttu-id="4cfbf-244">Regel reglerna för PowerShell-kommandot avgör vilket kommando som körs när sessionen innehåller kommandon med samma namn.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-244">The PowerShell command precedence rules determine which command runs when the session includes commands with the same name.</span></span>

<span data-ttu-id="4cfbf-245">Till exempel, när en session innehåller en funktion och en cmdlet med samma namn, kör PowerShell funktionen som standard.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-245">For example, when a session includes a function and a cmdlet with the same name, PowerShell runs the function by default.</span></span> <span data-ttu-id="4cfbf-246">När sessionen innehåller kommandon av samma typ med samma namn, till exempel två cmdlets med samma namn, körs det senast tillagda kommandot som standard.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-246">When the session includes commands of the same type with the same name, such as two cmdlets with the same name, by default, it runs the most recently added command.</span></span>

<span data-ttu-id="4cfbf-247">Mer information, inklusive en förklaring av prioritets reglerna och instruktioner för att köra dolda kommandon, finns [about_Command_Precedence](about_Command_Precedence.md).</span><span class="sxs-lookup"><span data-stu-id="4cfbf-247">For more information, including an explanation of the precedence rules and instructions for running hidden commands, see [about_Command_Precedence](about_Command_Precedence.md).</span></span>

## <a name="modules-and-snap-ins"></a><span data-ttu-id="4cfbf-248">Moduler och snapin-moduler</span><span class="sxs-lookup"><span data-stu-id="4cfbf-248">Modules and Snap-ins</span></span>

<span data-ttu-id="4cfbf-249">Du kan lägga till kommandon i-sessionen från moduler och snapin-moduler. Moduler kan lägga till alla typer av kommandon, inklusive cmdlet: ar, providers och funktioner och objekt, till exempel variabler, alias och PowerShell-enheter.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-249">You can add commands to your session from modules and snap-ins. Modules can add all types of commands, including cmdlets, providers, and functions, and items, such as variables, aliases, and PowerShell drives.</span></span> <span data-ttu-id="4cfbf-250">Snapin-moduler kan bara lägga till cmdlets och providers.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-250">Snap-ins can add only cmdlets and providers.</span></span>

<span data-ttu-id="4cfbf-251">Innan du tar bort en modul eller snapin-modul från din session kan du använda följande kommandon för att avgöra vilka kommandon som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-251">Before removing a module or snap-in from your session, use the following commands to determine which commands will be removed.</span></span>

<span data-ttu-id="4cfbf-252">Om du vill hitta källan till en cmdlet i din-session använder du följande kommando format:</span><span class="sxs-lookup"><span data-stu-id="4cfbf-252">To find the source of a cmdlet in your session, use the following command format:</span></span>

```powershell
Get-Command <cmdlet-name> | Format-List -Property verb,noun,pssnapin,module
```

<span data-ttu-id="4cfbf-253">Om du till exempel vill hitta källan till `Get-Date` cmdleten skriver du:</span><span class="sxs-lookup"><span data-stu-id="4cfbf-253">For example, to find the source of the `Get-Date` cmdlet, type:</span></span>

```powershell
Get-Command Get-Date | Format-List -Property verb,noun,module
```

<span data-ttu-id="4cfbf-254">Mer information om PowerShell-snapin-moduler finns i [about_PSSnapins](about_PSSnapins.md).</span><span class="sxs-lookup"><span data-stu-id="4cfbf-254">For more information about PowerShell snap-ins, see [about_PSSnapins](about_PSSnapins.md).</span></span>

## <a name="module-related-warnings-and-errors"></a><span data-ttu-id="4cfbf-255">Moduler-relaterade varningar och fel</span><span class="sxs-lookup"><span data-stu-id="4cfbf-255">Module-related Warnings and Errors</span></span>

<span data-ttu-id="4cfbf-256">De kommandon som en modul exporterar till följer PowerShell-kommandot namngivnings regler.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-256">The commands that a module exports should follow the PowerShell command naming rules.</span></span> <span data-ttu-id="4cfbf-257">Om modulen som du importerar exporterar cmdletar eller funktioner som har icke godkända verb i sina namn, `Import-Module` visar cmdleten följande varnings meddelande.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-257">If the module that you import exports cmdlets or functions that have unapproved verbs in their names, the `Import-Module` cmdlet displays the following warning message.</span></span>

> <span data-ttu-id="4cfbf-258">Varning! vissa importerade kommando namn innehåller icke-godkända verb som kan göra dem mindre synliga.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-258">WARNING: Some imported command names include unapproved verbs which might make them less discoverable.</span></span> <span data-ttu-id="4cfbf-259">Använd verbose-parametern för mer information eller Skriv Get-Verb om du vill visa en lista över godkända verb.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-259">Use the Verbose parameter for more detail or type Get-Verb to see the list of approved verbs.</span></span>

<span data-ttu-id="4cfbf-260">Det här meddelandet är bara en varning.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-260">This message is only a warning.</span></span> <span data-ttu-id="4cfbf-261">Den kompletta modulen importeras fortfarande, inklusive kommandon som inte överensstämmer.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-261">The complete module is still imported, including the non-conforming commands.</span></span> <span data-ttu-id="4cfbf-262">Även om meddelandet visas för modulen användare, bör namngivnings problemet åtgärdas av den som skapade modulen.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-262">Although the message is displayed to module users, the naming problem should be fixed by the module author.</span></span>

<span data-ttu-id="4cfbf-263">Om du vill utelämna varnings meddelandet använder du parametern **DisableNameChecking** för `Import-Module` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-263">To suppress the warning message, use the **DisableNameChecking** parameter of the `Import-Module` cmdlet.</span></span>

## <a name="built-in-modules-and-snap-ins"></a><span data-ttu-id="4cfbf-264">Inbyggda moduler och snapin-moduler</span><span class="sxs-lookup"><span data-stu-id="4cfbf-264">Built-in Modules and Snap-ins</span></span>

<span data-ttu-id="4cfbf-265">I PowerShell 2,0 och i äldre värd program i PowerShell 3,0 och senare, paketeras de grundläggande kommandon som installeras med PowerShell i snapin-moduler som läggs till automatiskt till varje PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-265">In PowerShell 2.0 and in older-style host programs in PowerShell 3.0 and later, the core commands that are installed with PowerShell are packaged in snap-ins that are added automatically to every PowerShell session.</span></span>

<span data-ttu-id="4cfbf-266">Från och med PowerShell 3,0, för värd program som implementerar det `InitialSessionState.CreateDefault2` inledande session State-API: t, läggs Microsoft. PowerShell. Core-snapin-modulen till i varje session som standard.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-266">Beginning in PowerShell 3.0, for host programs that implement the `InitialSessionState.CreateDefault2` initial session state API the Microsoft.PowerShell.Core snap-in is added to every session by default.</span></span> <span data-ttu-id="4cfbf-267">Moduler läses in automatiskt vid första användning.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-267">Modules are loaded automatically on first-use.</span></span>

> [!NOTE]
> <span data-ttu-id="4cfbf-268">Fjärrsessioner, inklusive sessioner som startas med hjälp av `New-PSSession` cmdleten, är äldre sessioner där de inbyggda kommandona paketeras i snapin-moduler.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-268">Remote sessions, including sessions that are started by using the `New-PSSession` cmdlet, are older-style sessions in which the built-in commands are packaged in snap-ins.</span></span>

<span data-ttu-id="4cfbf-269">Följande moduler (eller snapin-moduler) installeras med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-269">The following modules (or snap-ins) are installed with PowerShell.</span></span>

- <span data-ttu-id="4cfbf-270">CimCmdlets</span><span class="sxs-lookup"><span data-stu-id="4cfbf-270">CimCmdlets</span></span>
- <span data-ttu-id="4cfbf-271">Microsoft. PowerShell. Archive</span><span class="sxs-lookup"><span data-stu-id="4cfbf-271">Microsoft.PowerShell.Archive</span></span>
- <span data-ttu-id="4cfbf-272">Microsoft. PowerShell. Core</span><span class="sxs-lookup"><span data-stu-id="4cfbf-272">Microsoft.PowerShell.Core</span></span>
- <span data-ttu-id="4cfbf-273">Microsoft. PowerShell. Diagnostics</span><span class="sxs-lookup"><span data-stu-id="4cfbf-273">Microsoft.PowerShell.Diagnostics</span></span>
- <span data-ttu-id="4cfbf-274">Microsoft. PowerShell. Host</span><span class="sxs-lookup"><span data-stu-id="4cfbf-274">Microsoft.PowerShell.Host</span></span>
- <span data-ttu-id="4cfbf-275">Microsoft. PowerShell. Management</span><span class="sxs-lookup"><span data-stu-id="4cfbf-275">Microsoft.PowerShell.Management</span></span>
- <span data-ttu-id="4cfbf-276">Microsoft. PowerShell. ODataUtils</span><span class="sxs-lookup"><span data-stu-id="4cfbf-276">Microsoft.PowerShell.ODataUtils</span></span>
- <span data-ttu-id="4cfbf-277">Microsoft. PowerShell. Security</span><span class="sxs-lookup"><span data-stu-id="4cfbf-277">Microsoft.PowerShell.Security</span></span>
- <span data-ttu-id="4cfbf-278">Microsoft.PowerShell.Utility</span><span class="sxs-lookup"><span data-stu-id="4cfbf-278">Microsoft.PowerShell.Utility</span></span>
- <span data-ttu-id="4cfbf-279">Microsoft. WSMan. Management</span><span class="sxs-lookup"><span data-stu-id="4cfbf-279">Microsoft.WSMan.Management</span></span>
- <span data-ttu-id="4cfbf-280">PackageManagement</span><span class="sxs-lookup"><span data-stu-id="4cfbf-280">PackageManagement</span></span>
- <span data-ttu-id="4cfbf-281">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="4cfbf-281">PowerShellGet</span></span>
- <span data-ttu-id="4cfbf-282">PSDesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="4cfbf-282">PSDesiredStateConfiguration</span></span>
- <span data-ttu-id="4cfbf-283">PSDiagnostics</span><span class="sxs-lookup"><span data-stu-id="4cfbf-283">PSDiagnostics</span></span>
- <span data-ttu-id="4cfbf-284">PSScheduledJob</span><span class="sxs-lookup"><span data-stu-id="4cfbf-284">PSScheduledJob</span></span>
- <span data-ttu-id="4cfbf-285">PSWorkflow</span><span class="sxs-lookup"><span data-stu-id="4cfbf-285">PSWorkflow</span></span>
- <span data-ttu-id="4cfbf-286">PSWorkflowUtility</span><span class="sxs-lookup"><span data-stu-id="4cfbf-286">PSWorkflowUtility</span></span>
- <span data-ttu-id="4cfbf-287">ISE</span><span class="sxs-lookup"><span data-stu-id="4cfbf-287">ISE</span></span>

## <a name="logging-module-events"></a><span data-ttu-id="4cfbf-288">Loggning av module-händelser</span><span class="sxs-lookup"><span data-stu-id="4cfbf-288">Logging Module Events</span></span>

<span data-ttu-id="4cfbf-289">Från och med PowerShell 3,0 kan du registrera körnings händelser för cmdlets och Functions i PowerShell-moduler och snapin-moduler genom att ange egenskapen **LogPipelineExecutionDetails** för moduler och snapin-moduler till `$True` .</span><span class="sxs-lookup"><span data-stu-id="4cfbf-289">Beginning in PowerShell 3.0, you can record execution events for the cmdlets and functions in PowerShell modules and snap-ins by setting the **LogPipelineExecutionDetails** property of modules and snap-ins to `$True`.</span></span>
<span data-ttu-id="4cfbf-290">Du kan också använda en grupprincip inställning, aktivera modulreferensen för att aktivera modul loggning i alla PowerShell-sessioner.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-290">You can also use a Group Policy setting, Turn on Module Logging, to enable module logging in all PowerShell sessions.</span></span> <span data-ttu-id="4cfbf-291">Mer information finns i [about_EventLogs](about_EventLogs.md) och [about_Group_Policy_Settings](about_Group_Policy_Settings.md).</span><span class="sxs-lookup"><span data-stu-id="4cfbf-291">For more information, see [about_EventLogs](about_EventLogs.md) and [about_Group_Policy_Settings](about_Group_Policy_Settings.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4cfbf-292">Se även</span><span class="sxs-lookup"><span data-stu-id="4cfbf-292">See Also</span></span>

[<span data-ttu-id="4cfbf-293">about_Command_Precedence</span><span class="sxs-lookup"><span data-stu-id="4cfbf-293">about_Command_Precedence</span></span>](about_Command_Precedence.md)

[<span data-ttu-id="4cfbf-294">about_Group_Policy_Settings</span><span class="sxs-lookup"><span data-stu-id="4cfbf-294">about_Group_Policy_Settings</span></span>](about_Group_Policy_Settings.md)

[<span data-ttu-id="4cfbf-295">about_PSSnapins</span><span class="sxs-lookup"><span data-stu-id="4cfbf-295">about_PSSnapins</span></span>](about_PSSnapins.md)

[<span data-ttu-id="4cfbf-296">Get-Command</span><span class="sxs-lookup"><span data-stu-id="4cfbf-296">Get-Command</span></span>](xref:Microsoft.PowerShell.Core.Get-Command)

[<span data-ttu-id="4cfbf-297">Get – hjälp</span><span class="sxs-lookup"><span data-stu-id="4cfbf-297">Get-Help</span></span>](xref:Microsoft.PowerShell.Core.Get-Help)

[<span data-ttu-id="4cfbf-298">Hämta modul</span><span class="sxs-lookup"><span data-stu-id="4cfbf-298">Get-Module</span></span>](xref:Microsoft.PowerShell.Core.Get-Module)

[<span data-ttu-id="4cfbf-299">Importera-modul</span><span class="sxs-lookup"><span data-stu-id="4cfbf-299">Import-Module</span></span>](xref:Microsoft.PowerShell.Core.Import-Module)

[<span data-ttu-id="4cfbf-300">Ta bort modul</span><span class="sxs-lookup"><span data-stu-id="4cfbf-300">Remove-Module</span></span>](xref:Microsoft.PowerShell.Core.Remove-Module)
