---
title: Installerar ett PowerShell-modulen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb82827e-fdb7-4cbf-b3d4-093e72b3ff0e
caps.latest.revision: 28
ms.openlocfilehash: 60ac4bf9089232a9fa879e835e32da53422489fd
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229450"
---
# <a name="installing-a-powershell-module"></a><span data-ttu-id="22a72-102">Installera en PowerShell-modul</span><span class="sxs-lookup"><span data-stu-id="22a72-102">Installing a PowerShell Module</span></span>

<span data-ttu-id="22a72-103">När du har skapat din PowerShell-modulen, kommer troligen du att installera modulen på ett system, så att du eller andra kan använda den.</span><span class="sxs-lookup"><span data-stu-id="22a72-103">After you have created your PowerShell module, you will likely want to install the module on a system, so that you or others may use it.</span></span> <span data-ttu-id="22a72-104">Generellt sett består detta av modulen filerna kopieras (.psm1, eller binära sammansättningen, modulmanifestet, och andra tillhörande filer) till en katalog på datorn.</span><span class="sxs-lookup"><span data-stu-id="22a72-104">Generally speaking, this consists of copying the module files (ie, the .psm1, or the binary assembly, the module manifest, and any other associated files) onto a directory on that computer.</span></span> <span data-ttu-id="22a72-105">För ett mycket små projekt, och detta kan vara lika enkelt som att kopiera och klistra in filerna med Windows Explorer till en fjärransluten dator. men för större lösningar kan du använda en mer avancerad installationsprocess.</span><span class="sxs-lookup"><span data-stu-id="22a72-105">For a very small project, this may be as simple as copying and pasting the files with Windows Explorer onto a single remote computer; however, for larger solutions you may wish to use a more sophisticated installation process.</span></span> <span data-ttu-id="22a72-106">Oavsett hur du får din modul till systemet, kan PowerShell använda flera olika tekniker som låter användarna hitta och använda dina moduler.</span><span class="sxs-lookup"><span data-stu-id="22a72-106">Regardless of how you get your module onto the system, PowerShell can use a number of techniques that will let users find and use your modules.</span></span> <span data-ttu-id="22a72-107">Största problemet för installation därför se till att PowerShell kommer att kunna hitta din modul.</span><span class="sxs-lookup"><span data-stu-id="22a72-107">Therefore, the main issue for installation is ensuring that PowerShell will be able to find your module.</span></span> <span data-ttu-id="22a72-108">Mer information finns i [importera en PowerShell-modul](./importing-a-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="22a72-108">For more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md).</span></span>

## <a name="rules-for-installing-modules"></a><span data-ttu-id="22a72-109">Regler för att installera moduler</span><span class="sxs-lookup"><span data-stu-id="22a72-109">Rules for Installing Modules</span></span>

<span data-ttu-id="22a72-110">Följande information gäller alla moduler, inklusive moduler som du skapar för användning, moduler som du får från andra parter och moduler som du distribuerar till andra.</span><span class="sxs-lookup"><span data-stu-id="22a72-110">The following information pertains to all modules, including modules that you create for your own use, modules that you get from other parties, and modules that you distribute to others.</span></span>

### <a name="install-modules-in-psmodulepath"></a><span data-ttu-id="22a72-111">Installera moduler i PSModulePath</span><span class="sxs-lookup"><span data-stu-id="22a72-111">Install Modules in PSModulePath</span></span>

<span data-ttu-id="22a72-112">När det är möjligt, installera alla moduler i en sökväg som anges i den **PSModulePath** miljövariabeln eller Lägg till modulen sökvägen till den **PSModulePath** miljövariabelvärdet.</span><span class="sxs-lookup"><span data-stu-id="22a72-112">Whenever possible, install all modules in a path that is listed in the **PSModulePath** environment variable or add the module path to the **PSModulePath** environment variable value.</span></span>

<span data-ttu-id="22a72-113">Den **PSModulePath** miljövariabeln ($Env: PSModulePath) innehåller platserna för Windows PowerShell-moduler.</span><span class="sxs-lookup"><span data-stu-id="22a72-113">The **PSModulePath** environment variable ($Env:PSModulePath) contains the locations of Windows PowerShell modules.</span></span> <span data-ttu-id="22a72-114">Cmdlet: ar är beroende av värdet för den här miljövariabeln för att hitta moduler.</span><span class="sxs-lookup"><span data-stu-id="22a72-114">Cmdlets rely on the value of this environment variable to find modules.</span></span>

<span data-ttu-id="22a72-115">Som standard den **PSModulePath** miljövariabelvärdet innehåller följande system och användaren modulen kataloger, men du kan lägga till och redigera värdet.</span><span class="sxs-lookup"><span data-stu-id="22a72-115">By default, the **PSModulePath** environment variable value contains the following system and user module directories, but you can add to and edit the value.</span></span>

- <span data-ttu-id="22a72-116">`$PSHome\Modules` (% Windir%\System32\WindowsPowerShell\v1.0\Modules)</span><span class="sxs-lookup"><span data-stu-id="22a72-116">`$PSHome\Modules` (%Windir%\System32\WindowsPowerShell\v1.0\Modules)</span></span>

  > [!WARNING]
  > <span data-ttu-id="22a72-117">Den här platsen är reserverad för moduler som medföljer Windows.</span><span class="sxs-lookup"><span data-stu-id="22a72-117">This location is reserved for modules that ship with Windows.</span></span> <span data-ttu-id="22a72-118">Installera inte moduler till den här platsen.</span><span class="sxs-lookup"><span data-stu-id="22a72-118">Do not install modules to this location.</span></span>

- <span data-ttu-id="22a72-119">`$Home\Documents\WindowsPowerShell\Modules` (% UserProfile%\Documents\WindowsPowerShell\Modules)</span><span class="sxs-lookup"><span data-stu-id="22a72-119">`$Home\Documents\WindowsPowerShell\Modules` (%UserProfile%\Documents\WindowsPowerShell\Modules)</span></span>

- <span data-ttu-id="22a72-120">`$Env:ProgramFiles\WindowsPowerShell\Modules` (% ProgramFiles%\WindowsPowerShell\Modules)</span><span class="sxs-lookup"><span data-stu-id="22a72-120">`$Env:ProgramFiles\WindowsPowerShell\Modules` (%ProgramFiles%\WindowsPowerShell\Modules)</span></span>

  <span data-ttu-id="22a72-121">Att hämta värdet för den **PSModulePath** miljövariabeln, använda någon av följande kommandon.</span><span class="sxs-lookup"><span data-stu-id="22a72-121">To get the value of the **PSModulePath** environment variable, use either of the following commands.</span></span>

  ```powershell
  $Env:PSModulePath
  [Environment]::GetEnvironmentVariable("PSModulePath")
  ```

  <span data-ttu-id="22a72-122">Att lägga till en modulsökväg till värdet för den **PSModulePath** miljövariabeln värde, använder du följande kommandoformat.</span><span class="sxs-lookup"><span data-stu-id="22a72-122">To add a module path to value of the **PSModulePath** environment variable value, use the following command format.</span></span> <span data-ttu-id="22a72-123">Det här formatet använder den **SetEnvironmentVariable** -metoden för den **System.Environment** klassen för att göra en ändring av sessionen oberoende den **PSModulePath** miljö variabeln.</span><span class="sxs-lookup"><span data-stu-id="22a72-123">This format uses the **SetEnvironmentVariable** method of the **System.Environment** class to make a session-independent change to the **PSModulePath** environment variable.</span></span>

  ```powershell
  #Save the current value in the $p variable.
  $p = [Environment]::GetEnvironmentVariable("PSModulePath")

  #Add the new path to the $p variable. Begin with a semi-colon separator.
  $p += ";C:\Program Files (x86)\MyCompany\Modules\"

  #Add the paths in $p to the PSModulePath value.
  [Environment]::SetEnvironmentVariable("PSModulePath",$p)

  ```

  > [!IMPORTANT]
  > <span data-ttu-id="22a72-124">När du har lagt till sökvägen till **PSModulePath**, bör du skicka meddelandet miljö om ändringen.</span><span class="sxs-lookup"><span data-stu-id="22a72-124">Once you have added the path to **PSModulePath**, you should broadcast an environment message about the change.</span></span> <span data-ttu-id="22a72-125">Sänder ändringen kan andra program, till exempel i gränssnittet och att välja ändringen.</span><span class="sxs-lookup"><span data-stu-id="22a72-125">Broadcasting the change allows other applications, such as the shell, to pick up the change.</span></span> <span data-ttu-id="22a72-126">Om du vill skicka ändringen har din kod för installation av produkten skicka en **uppdaterats** med `lParam` anger till strängen ”miljö”.</span><span class="sxs-lookup"><span data-stu-id="22a72-126">To broadcast the change, have your product installation code send a **WM_SETTINGCHANGE** message with `lParam` set to the string "Environment".</span></span> <span data-ttu-id="22a72-127">Se till att skicka meddelandet när modulen installationen koden har uppdaterats **PSModulePath**.</span><span class="sxs-lookup"><span data-stu-id="22a72-127">Be sure to send the message after your module installation code has updated **PSModulePath**.</span></span>

### <a name="use-the-correct-module-directory-name"></a><span data-ttu-id="22a72-128">Använd rätt modul katalognamn</span><span class="sxs-lookup"><span data-stu-id="22a72-128">Use the Correct Module Directory Name</span></span>

<span data-ttu-id="22a72-129">En giltig modul är en modul som lagras i en mapp med samma namn som det grundläggande namnet på minst en fil i modulkatalogen.</span><span class="sxs-lookup"><span data-stu-id="22a72-129">A well-formed module is a module that is stored in a directory that has the same name as the base name of at least one file in the module directory.</span></span> <span data-ttu-id="22a72-130">Om en modul inte är korrekt formaterad, känner Windows PowerShell inte igen det som en modul.</span><span class="sxs-lookup"><span data-stu-id="22a72-130">If a module is not well-formed, Windows PowerShell does not recognize it as a module.</span></span>

<span data-ttu-id="22a72-131">”Huvudnamnet” för en fil är namn utan filnamnstillägget.</span><span class="sxs-lookup"><span data-stu-id="22a72-131">The "base name" of a file is the name without the file name extension.</span></span> <span data-ttu-id="22a72-132">I en giltig modul, måste namnet på den katalog som innehåller filerna som modulen matcha det grundläggande namnet på minst en fil i modulen.</span><span class="sxs-lookup"><span data-stu-id="22a72-132">In a well-formed module, the name of the directory that contains the module files must match the base name of at least one file in the module.</span></span>

<span data-ttu-id="22a72-133">Till exempel i Fabrikam exempelmodulen den katalog som innehåller filerna som modulen heter ”Fabrikam” och minst en fil har det grundläggande namnet ”Fabrikam”.</span><span class="sxs-lookup"><span data-stu-id="22a72-133">For example, in the sample Fabrikam module, the directory that contains the module files is named "Fabrikam" and at least one file has the "Fabrikam" base name.</span></span> <span data-ttu-id="22a72-134">I det här fallet har både Fabrikam.psd1 och Fabrikam.dll det grundläggande namnet ”Fabrikam”.</span><span class="sxs-lookup"><span data-stu-id="22a72-134">In this case, both Fabrikam.psd1 and Fabrikam.dll have the "Fabrikam" base name.</span></span>

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

### <a name="effect-of-incorrect-installation"></a><span data-ttu-id="22a72-135">Effekten av felaktig Installation</span><span class="sxs-lookup"><span data-stu-id="22a72-135">Effect of Incorrect Installation</span></span>

<span data-ttu-id="22a72-136">Om modulen är inte korrekt formaterad och dess plats ingår inte i värdet för den **PSModulePath** miljövariabeln, identifiering av grundläggande funktioner i Windows PowerShell, exempelvis följande, fungerar inte.</span><span class="sxs-lookup"><span data-stu-id="22a72-136">If the module is not well-formed and its location is not included in the value of the **PSModulePath** environment variable, basic discovery features of Windows PowerShell, such as the following, do not work.</span></span>

- <span data-ttu-id="22a72-137">Modulen automatisk inläsning-funktionen kan inte importera modulen automatiskt.</span><span class="sxs-lookup"><span data-stu-id="22a72-137">The Module Auto-Loading feature cannot import the module automatically.</span></span>

- <span data-ttu-id="22a72-138">Den `ListAvailable` -parametern för den [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet kan inte hitta modulen.</span><span class="sxs-lookup"><span data-stu-id="22a72-138">The `ListAvailable` parameter of the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet cannot find the module.</span></span>

- <span data-ttu-id="22a72-139">Den [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet kan inte hitta modulen.</span><span class="sxs-lookup"><span data-stu-id="22a72-139">The [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet cannot find the module.</span></span> <span data-ttu-id="22a72-140">Du måste ange den fullständiga sökvägen till rot-filen för modulen eller modulen manifestfilen om du vill importera modulen.</span><span class="sxs-lookup"><span data-stu-id="22a72-140">To import the module, you must provide the full path to the root module file or module manifest file.</span></span>

  <span data-ttu-id="22a72-141">Ytterligare funktioner, till exempel följande, fungerar inte om inte modulen har importerats till sessionen.</span><span class="sxs-lookup"><span data-stu-id="22a72-141">Additional features, such as the following, do not work unless the module is imported into the session.</span></span> <span data-ttu-id="22a72-142">I rätt moduler i den **PSModulePath** miljövariabeln, dessa funktioner fungerar även om modulen inte importeras till sessionen.</span><span class="sxs-lookup"><span data-stu-id="22a72-142">In well-formed modules in the **PSModulePath** environment variable, these features work even when the module is not imported into the session.</span></span>

- <span data-ttu-id="22a72-143">Den [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet kan inte hitta kommandon i modulen.</span><span class="sxs-lookup"><span data-stu-id="22a72-143">The [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet cannot find commands in the module.</span></span>

- <span data-ttu-id="22a72-144">Den [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) och [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets kan inte uppdatera eller spara hjälp för modulen.</span><span class="sxs-lookup"><span data-stu-id="22a72-144">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets cannot update or save help for the module.</span></span>

- <span data-ttu-id="22a72-145">Den [visningskommandot](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) cmdlet: Det går inte att hitta och visa kommandon i modulen.</span><span class="sxs-lookup"><span data-stu-id="22a72-145">The [Show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) cmdlet cannot find and display the commands in the module.</span></span>

  <span data-ttu-id="22a72-146">Kommandona i modulen saknas från den `Show-Command` fönster i Windows PowerShell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="22a72-146">The commands in the module are missing from the `Show-Command` window in Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="where-to-install-modules"></a><span data-ttu-id="22a72-147">Var du vill installera moduler</span><span class="sxs-lookup"><span data-stu-id="22a72-147">Where to Install Modules</span></span>

<span data-ttu-id="22a72-148">Det här avsnittet beskrivs var i filsystemet för att installera Windows PowerShell-moduler.</span><span class="sxs-lookup"><span data-stu-id="22a72-148">This section explains where in the file system to install Windows PowerShell modules.</span></span> <span data-ttu-id="22a72-149">Platsen är beroende av hur modulen ska användas.</span><span class="sxs-lookup"><span data-stu-id="22a72-149">The location depends on how the module is used.</span></span>

### <a name="installing-modules-for-a-specific-user"></a><span data-ttu-id="22a72-150">Installera moduler för en viss användare</span><span class="sxs-lookup"><span data-stu-id="22a72-150">Installing Modules for a Specific User</span></span>

<span data-ttu-id="22a72-151">Om du skapar en egen modul eller få en modul från en annan part, till exempel en community-webbplatsen för Windows PowerShell, och du vill att modulen ska vara tillgängliga för ditt konto endast, installera modulen i katalogen användarspecifika moduler.</span><span class="sxs-lookup"><span data-stu-id="22a72-151">If you create your own module or get a module from another party, such as a Windows PowerShell community website, and you want the module to be available for your user account only, install the module in your user-specific Modules directory.</span></span>

`$home\Documents\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

<span data-ttu-id="22a72-152">Katalogen användarspecifika moduler läggs till i värdet för den **PSModulePath** miljövariabeln som standard.</span><span class="sxs-lookup"><span data-stu-id="22a72-152">The user-specific Modules directory is added to the value of the **PSModulePath** environment variable by default.</span></span>

### <a name="installing-modules-for-all-users-in-program-files"></a><span data-ttu-id="22a72-153">Installera moduler för alla användare i program</span><span class="sxs-lookup"><span data-stu-id="22a72-153">Installing Modules for all Users in Program Files</span></span>

<span data-ttu-id="22a72-154">Om du vill att en modul ska vara tillgängliga för alla användarkonton på datorn, installera modulen på platsen för programmet.</span><span class="sxs-lookup"><span data-stu-id="22a72-154">If you want a module to be available to all user accounts on the computer, install the module in the Program Files location.</span></span>

`$Env:ProgramFiles\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

> [!NOTE]
> <span data-ttu-id="22a72-155">Plats för programfiler läggs till värdet för miljövariabeln PSModulePath som standard i Windows PowerShell 4.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="22a72-155">The Program Files location is added to the value of the PSModulePath environment variable by default in Windows PowerShell 4.0 and later.</span></span> <span data-ttu-id="22a72-156">För tidigare versioner av Windows PowerShell kan du manuellt skapa programfiler plats ((%ProgramFiles%\WindowsPowerShell\Modules) och lägga till den här sökvägen i miljövariabeln PSModulePath enligt beskrivningen ovan.</span><span class="sxs-lookup"><span data-stu-id="22a72-156">For earlier versions of Windows PowerShell, you can manually create the Program Files location ((%ProgramFiles%\WindowsPowerShell\Modules) and add this path to your PSModulePath environment variable as described above.</span></span>

### <a name="installing-modules-in-a-product-directory"></a><span data-ttu-id="22a72-157">Installerar moduler i en produktkatalog</span><span class="sxs-lookup"><span data-stu-id="22a72-157">Installing Modules in a Product Directory</span></span>

<span data-ttu-id="22a72-158">Om du ska distribuera modulen till andra parter använda standardplatsen för programfiler som beskrivs ovan, eller skapa egna företagsspecifik eller produktspecifik underkatalog i katalogen % ProgramFiles %.</span><span class="sxs-lookup"><span data-stu-id="22a72-158">If you are distributing the module to other parties, use the default Program Files location described above, or create your own company-specific or product-specific subdirectory of the %ProgramFiles% directory.</span></span>

<span data-ttu-id="22a72-159">Fabrikam-tekniker, ett fiktivt företag, levereras till exempel en Windows PowerShell-modul för sina Fabrikam Manager-produkten.</span><span class="sxs-lookup"><span data-stu-id="22a72-159">For example, Fabrikam Technologies, a fictitious company, is shipping a Windows PowerShell module for their Fabrikam Manager product.</span></span> <span data-ttu-id="22a72-160">Sina modulen installer skapar en underkatalog moduler i underkatalogen Fabrikam Manager produkten.</span><span class="sxs-lookup"><span data-stu-id="22a72-160">Their module installer creates a Modules subdirectory in the Fabrikam Manager product subdirectory.</span></span>

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

<span data-ttu-id="22a72-161">Om du vill aktivera Windows PowerShell-modulen identifiering funktioner att hitta modulen Fabrikam Fabrikam modulen installationsprogrammet lägger till modulen platsen till värdet för den **PSModulePath** miljövariabeln.</span><span class="sxs-lookup"><span data-stu-id="22a72-161">To enable the Windows PowerShell module discovery features to find the Fabrikam module, the Fabrikam module installer adds the module location to the value of the **PSModulePath** environment variable.</span></span>

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam Technologies\Fabrikam Manager\Modules\"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

### <a name="installing-modules-in-the-common-files-directory"></a><span data-ttu-id="22a72-162">Installerar moduler i katalogen med vanliga</span><span class="sxs-lookup"><span data-stu-id="22a72-162">Installing Modules in the Common Files Directory</span></span>

<span data-ttu-id="22a72-163">Om en modul används av flera komponenter i en produkt eller genom att flera versioner av en produkt, installera modulen i en modul-specifika underkatalog i underkatalogen %ProgramFiles%\Common Files\Modules.</span><span class="sxs-lookup"><span data-stu-id="22a72-163">If a module is used by multiple components of a product or by multiple versions of a product, install the module in a module-specific subdirectory of the %ProgramFiles%\Common Files\Modules subdirectory.</span></span>

<span data-ttu-id="22a72-164">I följande exempel Fabrikam-modulen installeras i en underkatalog för Fabrikam till den `%ProgramFiles%\Common Files\Modules` underkatalog.</span><span class="sxs-lookup"><span data-stu-id="22a72-164">In the following example, the Fabrikam module is installed in a Fabrikam subdirectory of the `%ProgramFiles%\Common Files\Modules` subdirectory.</span></span> <span data-ttu-id="22a72-165">Observera att varje modul finns i en egen underkatalog i underkatalogen moduler.</span><span class="sxs-lookup"><span data-stu-id="22a72-165">Note that each module resides in its own subdirectory in the Modules subdirectory.</span></span>

```
C:\Program Files
  Common Files
    Modules
      Fabrikam
        Fabrikam.psd1 (module manifest)
        Fabrikam.dll (module assembly)
```

<span data-ttu-id="22a72-166">Sedan kan installationsprogrammet säkerställer värdet för den **PSModulePath** miljövariabeln innehåller sökvägen i underkatalogen moduler vanliga filer.</span><span class="sxs-lookup"><span data-stu-id="22a72-166">Then, the installer assures the value of the **PSModulePath** environment variable includes the path of the common files modules subdirectory.</span></span>

```powershell
$m = $env:ProgramFiles + '\Common Files\Modules'
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$q = $p -split ';'
if ($q -notContains $m) {
    $q += ";$m"
}
$p = $q -join ';'
[Environment]::SetEnvironmentVariable("PSModulePath", $p)
```

## <a name="installing-multiple-versions-of-a-module"></a><span data-ttu-id="22a72-167">Installera flera versioner av en modul</span><span class="sxs-lookup"><span data-stu-id="22a72-167">Installing Multiple Versions of a Module</span></span>

<span data-ttu-id="22a72-168">Använd följande procedur för att installera flera versioner av samma modul.</span><span class="sxs-lookup"><span data-stu-id="22a72-168">To install multiple versions of the same module, use the following procedure.</span></span>

1. <span data-ttu-id="22a72-169">Skapa en katalog för varje version av modulen.</span><span class="sxs-lookup"><span data-stu-id="22a72-169">Create a directory for each version of the module.</span></span> <span data-ttu-id="22a72-170">Inkludera versionsnumret i katalognamnet.</span><span class="sxs-lookup"><span data-stu-id="22a72-170">Include the version number in the directory name.</span></span>
2. <span data-ttu-id="22a72-171">Skapa ett modulmanifest för varje version av modulen.</span><span class="sxs-lookup"><span data-stu-id="22a72-171">Create a module manifest for each version of the module.</span></span> <span data-ttu-id="22a72-172">I värdet för den **ModuleVersion** nyckeln i manifestet, ange versionsnummer för modulen.</span><span class="sxs-lookup"><span data-stu-id="22a72-172">In the value of the **ModuleVersion** key in the manifest, enter the module version number.</span></span> <span data-ttu-id="22a72-173">Spara manifestfilen (.psd1) i katalogen versionsspecifika för modulen.</span><span class="sxs-lookup"><span data-stu-id="22a72-173">Save the manifest file (.psd1) in the version-specific directory for the module.</span></span>
3. <span data-ttu-id="22a72-174">Lägg till sökvägen till rotmappen modulen till värdet för den **PSModulePath** miljövariabeln, som visas i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="22a72-174">Add the module root folder path to the value of the **PSModulePath** environment variable, as shown in the following examples.</span></span>

<span data-ttu-id="22a72-175">Om du vill importera en viss version av modulen, slutanvändaren kan använda den `MinimumVersion` eller `RequiredVersion` parametrarna för den [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="22a72-175">To import a particular version of the module, the end-user can use the `MinimumVersion` or `RequiredVersion` parameters of the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span></span>

<span data-ttu-id="22a72-176">Till exempel om modulen Fabrikam är tillgängliga i version 8.0 och 9.0, kan katalogstruktur för Fabrikam-modulen likna följande.</span><span class="sxs-lookup"><span data-stu-id="22a72-176">For example, if the Fabrikam module is available in versions 8.0 and 9.0, the Fabrikam module directory structure might resemble the following.</span></span>

 ```
C:\Program Files
Fabrikam Manager
  Fabrikam8
    Fabrikam
      Fabrikam.psd1 (module manifest: ModuleVersion = "8.0")
      Fabrikam.dll (module assembly)
  Fabrikam9
    Fabrikam
      Fabrikam.psd1 (module manifest: ModuleVersion = "9.0")
      Fabrikam.dll (module assembly)
```

<span data-ttu-id="22a72-177">Installationsprogrammet lägger till båda modulernas sökvägar till den **PSModulePath** miljövariabelvärdet.</span><span class="sxs-lookup"><span data-stu-id="22a72-177">The installer adds both of the module paths to the **PSModulePath** environment variable value.</span></span>

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam\Fabrikam8;C:\Program Files\Fabrikam\Fabrikam9"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

<span data-ttu-id="22a72-178">När dessa steg har slutförts, den **ListAvailable** -parametern för den [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet hämtar båda Fabrikam-moduler.</span><span class="sxs-lookup"><span data-stu-id="22a72-178">When these steps are complete, the **ListAvailable** parameter of the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet gets both of the Fabrikam modules.</span></span> <span data-ttu-id="22a72-179">Om du vill importera en viss modul, Använd den `MinimumVersion` eller `RequiredVersion` parametrarna för den [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="22a72-179">To import a particular module, use the `MinimumVersion` or `RequiredVersion` parameters of the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span></span>

<span data-ttu-id="22a72-180">Om båda moduler importeras till samma session, och moduler innehåller cmdletar och arbetsflöden med samma namn, gäller de cmdletar som importeras senast i sessionen.</span><span class="sxs-lookup"><span data-stu-id="22a72-180">If both modules are imported into the same session, and the modules contain cmdlets with the same names, the cmdlets that are imported last are effective in the session.</span></span>

## <a name="handling-command-name-conflicts"></a><span data-ttu-id="22a72-181">Hantering av kommandot namnet står i konflikt</span><span class="sxs-lookup"><span data-stu-id="22a72-181">Handling Command Name Conflicts</span></span>

<span data-ttu-id="22a72-182">Namnkonflikter i kommandot kan inträffa när de kommandon som en modul exporterar har samma namn som kommandon i sessionen.</span><span class="sxs-lookup"><span data-stu-id="22a72-182">Command name conflicts can occur when the commands that a module exports have the same name as commands in the user's session.</span></span>

<span data-ttu-id="22a72-183">När en session innehåller två kommandon som har samma namn, kör Windows PowerShell kommandotypen som företräde.</span><span class="sxs-lookup"><span data-stu-id="22a72-183">When a session contains two commands that have the same name, Windows PowerShell runs the command type that takes precedence.</span></span> <span data-ttu-id="22a72-184">När en session innehåller två kommandon som har samma namn och samma typ, kör Windows PowerShell-kommandot som har lagts till i sessionen senast.</span><span class="sxs-lookup"><span data-stu-id="22a72-184">When a session contains two commands that have the same name and the same type, Windows PowerShell runs the command that was added to the session most recently.</span></span> <span data-ttu-id="22a72-185">Om du vill köra ett kommando som inte körs som standard, kan användare kvalificera sig kommandonamnet med modulens namn.</span><span class="sxs-lookup"><span data-stu-id="22a72-185">To run a command that is not run by default, users can qualify the command name with the module name.</span></span>

<span data-ttu-id="22a72-186">Om sessionen innehåller till exempel en `Get-Date` funktion och `Get-Date` Windows PowerShell-cmdleten körs funktionen som standard.</span><span class="sxs-lookup"><span data-stu-id="22a72-186">For example, if the session contains a `Get-Date` function and the `Get-Date` cmdlet, Windows PowerShell runs the function by default.</span></span> <span data-ttu-id="22a72-187">För att köra cmdlet: en, måste du börja kommandot med modulens namn, till exempel:</span><span class="sxs-lookup"><span data-stu-id="22a72-187">To run the cmdlet, preface the command with the module name, such as:</span></span>

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

<span data-ttu-id="22a72-188">För att förhindra namnkonflikter modulskapare kan använda den **DefaultCommandPrefix** exportera nyckeln i modulmanifestet att ange ett substantivprefix för alla kommandon från modulen.</span><span class="sxs-lookup"><span data-stu-id="22a72-188">To prevent name conflicts, module authors can use the **DefaultCommandPrefix** key in the module manifest to specify a noun prefix for all commands exported from the module.</span></span>

<span data-ttu-id="22a72-189">Användare kan använda den **Prefix** -parametern för den `Import-Module` cmdlet för att använda en annan prefix.</span><span class="sxs-lookup"><span data-stu-id="22a72-189">Users can use the **Prefix** parameter of the `Import-Module` cmdlet to use an alternate prefix.</span></span> <span data-ttu-id="22a72-190">Värdet för den **prefixet** parametern har företräde framför värdet för den **DefaultCommandPrefix** nyckel.</span><span class="sxs-lookup"><span data-stu-id="22a72-190">The value of the **Prefix** parameter takes precedence over the value of the **DefaultCommandPrefix** key.</span></span>

## <a name="see-also"></a><span data-ttu-id="22a72-191">Se även</span><span class="sxs-lookup"><span data-stu-id="22a72-191">See Also</span></span>

[<span data-ttu-id="22a72-192">about_Command_Precedence</span><span class="sxs-lookup"><span data-stu-id="22a72-192">about_Command_Precedence</span></span>](/powershell/module/microsoft.powershell.core/about/about_command_precedence)

[<span data-ttu-id="22a72-193">Skriva ett Windows PowerShell-modul</span><span class="sxs-lookup"><span data-stu-id="22a72-193">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
