---
ms.date: 09/13/2016
ms.topic: reference
title: Installera en PowerShell-modul
description: Installera en PowerShell-modul
ms.openlocfilehash: 3c7a4413168934ca4de1912c9615a6ae0fc45788
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92645344"
---
# <a name="installing-a-powershell-module"></a><span data-ttu-id="20cc6-103">Installera en PowerShell-modul</span><span class="sxs-lookup"><span data-stu-id="20cc6-103">Installing a PowerShell Module</span></span>

<span data-ttu-id="20cc6-104">När du har skapat din PowerShell-modul vill du förmodligen installera modulen i ett system, så att du eller andra kan använda den.</span><span class="sxs-lookup"><span data-stu-id="20cc6-104">After you have created your PowerShell module, you will likely want to install the module on a system, so that you or others may use it.</span></span> <span data-ttu-id="20cc6-105">Detta består vanligt vis av att kopiera modulblad (IE,. psm1 eller binär sammansättning, modulens manifest och andra tillhör ande filer) till en katalog på den datorn.</span><span class="sxs-lookup"><span data-stu-id="20cc6-105">Generally speaking, this consists of copying the module files (ie, the .psm1, or the binary assembly, the module manifest, and any other associated files) onto a directory on that computer.</span></span> <span data-ttu-id="20cc6-106">För ett mycket litet projekt kan detta vara lika enkelt som att kopiera och klistra in filerna med Utforskaren på en enskild fjärrdator. men för större lösningar kanske du vill använda en mer avancerad installations process.</span><span class="sxs-lookup"><span data-stu-id="20cc6-106">For a very small project, this may be as simple as copying and pasting the files with Windows Explorer onto a single remote computer; however, for larger solutions you may wish to use a more sophisticated installation process.</span></span> <span data-ttu-id="20cc6-107">Oavsett hur du hämtar modulen till systemet, kan PowerShell använda ett antal tekniker som gör det möjligt för användarna att hitta och använda dina moduler.</span><span class="sxs-lookup"><span data-stu-id="20cc6-107">Regardless of how you get your module onto the system, PowerShell can use a number of techniques that will let users find and use your modules.</span></span> <span data-ttu-id="20cc6-108">Därför säkerställer det huvudsakliga problemet för installationen att PowerShell kan hitta modulen.</span><span class="sxs-lookup"><span data-stu-id="20cc6-108">Therefore, the main issue for installation is ensuring that PowerShell will be able to find your module.</span></span> <span data-ttu-id="20cc6-109">Mer information finns i [Importera en PowerShell-modul](./importing-a-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="20cc6-109">For more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md).</span></span>

## <a name="rules-for-installing-modules"></a><span data-ttu-id="20cc6-110">Regler för att installera moduler</span><span class="sxs-lookup"><span data-stu-id="20cc6-110">Rules for Installing Modules</span></span>

<span data-ttu-id="20cc6-111">Följande information gäller alla moduler, inklusive moduler som du skapar för din egen användning, moduler som du hämtar från andra parter och moduler som du distribuerar till andra.</span><span class="sxs-lookup"><span data-stu-id="20cc6-111">The following information pertains to all modules, including modules that you create for your own use, modules that you get from other parties, and modules that you distribute to others.</span></span>

### <a name="install-modules-in-psmodulepath"></a><span data-ttu-id="20cc6-112">Installera moduler i PSModulePath</span><span class="sxs-lookup"><span data-stu-id="20cc6-112">Install Modules in PSModulePath</span></span>

<span data-ttu-id="20cc6-113">När det är möjligt kan du installera alla moduler i en sökväg som anges i **PSModulePath** -miljövariabeln eller lägga till modulens sökväg i variabeln **PSModulePath** Environment.</span><span class="sxs-lookup"><span data-stu-id="20cc6-113">Whenever possible, install all modules in a path that is listed in the **PSModulePath** environment variable or add the module path to the **PSModulePath** environment variable value.</span></span>

<span data-ttu-id="20cc6-114">**PSModulePath** -miljövariabeln ($env:P smodulepath) innehåller platserna för Windows PowerShell-moduler.</span><span class="sxs-lookup"><span data-stu-id="20cc6-114">The **PSModulePath** environment variable ($Env:PSModulePath) contains the locations of Windows PowerShell modules.</span></span> <span data-ttu-id="20cc6-115">-Cmdletar är beroende av värdet för den här miljövariabeln för att hitta moduler.</span><span class="sxs-lookup"><span data-stu-id="20cc6-115">Cmdlets rely on the value of this environment variable to find modules.</span></span>

<span data-ttu-id="20cc6-116">Som standard innehåller variabeln **PSModulePath** följande kataloger för system-och användar moduler, men du kan lägga till och redigera värdet.</span><span class="sxs-lookup"><span data-stu-id="20cc6-116">By default, the **PSModulePath** environment variable value contains the following system and user module directories, but you can add to and edit the value.</span></span>

- <span data-ttu-id="20cc6-117">`$PSHome\Modules` (%Windir%\System32\WindowsPowerShell\v1.0\Modules)</span><span class="sxs-lookup"><span data-stu-id="20cc6-117">`$PSHome\Modules` (%Windir%\System32\WindowsPowerShell\v1.0\Modules)</span></span>

  > [!WARNING]
  > <span data-ttu-id="20cc6-118">Den här platsen är reserverad för moduler som levereras med Windows.</span><span class="sxs-lookup"><span data-stu-id="20cc6-118">This location is reserved for modules that ship with Windows.</span></span> <span data-ttu-id="20cc6-119">Installera inte moduler på den här platsen.</span><span class="sxs-lookup"><span data-stu-id="20cc6-119">Do not install modules to this location.</span></span>

- <span data-ttu-id="20cc6-120">`$Home\Documents\WindowsPowerShell\Modules` (%UserProfile%\Documents\WindowsPowerShell\Modules)</span><span class="sxs-lookup"><span data-stu-id="20cc6-120">`$Home\Documents\WindowsPowerShell\Modules` (%UserProfile%\Documents\WindowsPowerShell\Modules)</span></span>

- <span data-ttu-id="20cc6-121">`$Env:ProgramFiles\WindowsPowerShell\Modules` (%ProgramFiles%\WindowsPowerShell\Modules)</span><span class="sxs-lookup"><span data-stu-id="20cc6-121">`$Env:ProgramFiles\WindowsPowerShell\Modules` (%ProgramFiles%\WindowsPowerShell\Modules)</span></span>

  <span data-ttu-id="20cc6-122">Använd något av följande kommandon för att hämta värdet för **PSModulePath** -miljövariabeln.</span><span class="sxs-lookup"><span data-stu-id="20cc6-122">To get the value of the **PSModulePath** environment variable, use either of the following commands.</span></span>

  ```powershell
  $Env:PSModulePath
  [Environment]::GetEnvironmentVariable("PSModulePath")
  ```

  <span data-ttu-id="20cc6-123">Om du vill lägga till en modul Sök väg till värdet för **PSModulePath** -miljövariabeln värde, använder du följande kommando format.</span><span class="sxs-lookup"><span data-stu-id="20cc6-123">To add a module path to value of the **PSModulePath** environment variable value, use the following command format.</span></span> <span data-ttu-id="20cc6-124">I det här formatet används **SetEnvironmentVariable** -metoden i klassen **system. Environment** för att göra en sessions oberoende ändring i miljövariabeln **PSModulePath** .</span><span class="sxs-lookup"><span data-stu-id="20cc6-124">This format uses the **SetEnvironmentVariable** method of the **System.Environment** class to make a session-independent change to the **PSModulePath** environment variable.</span></span>

  ```powershell
  #Save the current value in the $p variable.
  $p = [Environment]::GetEnvironmentVariable("PSModulePath")

  #Add the new path to the $p variable. Begin with a semi-colon separator.
  $p += ";C:\Program Files (x86)\MyCompany\Modules\"

  #Add the paths in $p to the PSModulePath value.
  [Environment]::SetEnvironmentVariable("PSModulePath",$p)

  ```

  > [!IMPORTANT]
  > <span data-ttu-id="20cc6-125">När du har lagt till sökvägen till **PSModulePath** bör du sända ett miljö meddelande om ändringen.</span><span class="sxs-lookup"><span data-stu-id="20cc6-125">Once you have added the path to **PSModulePath** , you should broadcast an environment message about the change.</span></span> <span data-ttu-id="20cc6-126">Genom att sända ändringen kan andra program, till exempel gränssnittet, Hämta ändringen.</span><span class="sxs-lookup"><span data-stu-id="20cc6-126">Broadcasting the change allows other applications, such as the shell, to pick up the change.</span></span> <span data-ttu-id="20cc6-127">Om du vill sända ändringen ska du be din produkt installations kod att skicka ett **WM_SETTINGCHANGE** meddelande med `lParam` inställningen "miljö".</span><span class="sxs-lookup"><span data-stu-id="20cc6-127">To broadcast the change, have your product installation code send a **WM_SETTINGCHANGE** message with `lParam` set to the string "Environment".</span></span> <span data-ttu-id="20cc6-128">Se till att skicka meddelandet efter att modulens installations kod har uppdaterats **PSModulePath** .</span><span class="sxs-lookup"><span data-stu-id="20cc6-128">Be sure to send the message after your module installation code has updated **PSModulePath** .</span></span>

### <a name="use-the-correct-module-directory-name"></a><span data-ttu-id="20cc6-129">Använd rätt katalog namn för modul</span><span class="sxs-lookup"><span data-stu-id="20cc6-129">Use the Correct Module Directory Name</span></span>

<span data-ttu-id="20cc6-130">En välformulerad modul är en modul som lagras i en katalog som har samma namn som grund namnet på minst en fil i modul katalogen.</span><span class="sxs-lookup"><span data-stu-id="20cc6-130">A well-formed module is a module that is stored in a directory that has the same name as the base name of at least one file in the module directory.</span></span> <span data-ttu-id="20cc6-131">Om en modul inte är korrekt utformad känner Windows PowerShell inte igen som en modul.</span><span class="sxs-lookup"><span data-stu-id="20cc6-131">If a module is not well-formed, Windows PowerShell does not recognize it as a module.</span></span>

<span data-ttu-id="20cc6-132">"Grund namnet" i en fil är namnet utan fil namns tillägget.</span><span class="sxs-lookup"><span data-stu-id="20cc6-132">The "base name" of a file is the name without the file name extension.</span></span> <span data-ttu-id="20cc6-133">I en välformulerad modul måste namnet på den katalog som innehåller module-filerna matcha bas namnet för minst en fil i modulen.</span><span class="sxs-lookup"><span data-stu-id="20cc6-133">In a well-formed module, the name of the directory that contains the module files must match the base name of at least one file in the module.</span></span>

<span data-ttu-id="20cc6-134">I exempel Fabrikam-modulen är katalogen som innehåller filerna namnet "Fabrikam" och minst en fil har bas namnet "Fabrikam".</span><span class="sxs-lookup"><span data-stu-id="20cc6-134">For example, in the sample Fabrikam module, the directory that contains the module files is named "Fabrikam" and at least one file has the "Fabrikam" base name.</span></span> <span data-ttu-id="20cc6-135">I det här fallet måste både Fabrikam.psd1 och Fabrikam.dll ha "Fabrikam"-bas namnet.</span><span class="sxs-lookup"><span data-stu-id="20cc6-135">In this case, both Fabrikam.psd1 and Fabrikam.dll have the "Fabrikam" base name.</span></span>

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

### <a name="effect-of-incorrect-installation"></a><span data-ttu-id="20cc6-136">Påverkan av felaktig installation</span><span class="sxs-lookup"><span data-stu-id="20cc6-136">Effect of Incorrect Installation</span></span>

<span data-ttu-id="20cc6-137">Om modulen inte är korrekt utformad och dess plats inte ingår i värdet för **PSModulePath** -miljövariabeln, så fungerar inte grundläggande identifierings funktioner i Windows PowerShell, till exempel följande.</span><span class="sxs-lookup"><span data-stu-id="20cc6-137">If the module is not well-formed and its location is not included in the value of the **PSModulePath** environment variable, basic discovery features of Windows PowerShell, such as the following, do not work.</span></span>

- <span data-ttu-id="20cc6-138">Funktionen för automatisk inläsning av modulen kan inte automatiskt importera modulen.</span><span class="sxs-lookup"><span data-stu-id="20cc6-138">The Module Auto-Loading feature cannot import the module automatically.</span></span>

- <span data-ttu-id="20cc6-139">`ListAvailable`Parametern för cmdleten [Get-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) kan inte hitta modulen.</span><span class="sxs-lookup"><span data-stu-id="20cc6-139">The `ListAvailable` parameter of the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet cannot find the module.</span></span>

- <span data-ttu-id="20cc6-140">Cmdleten [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) kan inte hitta modulen.</span><span class="sxs-lookup"><span data-stu-id="20cc6-140">The [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet cannot find the module.</span></span> <span data-ttu-id="20cc6-141">Om du vill importera modulen måste du ange den fullständiga sökvägen till rot modul filen eller manifest filen för modulen.</span><span class="sxs-lookup"><span data-stu-id="20cc6-141">To import the module, you must provide the full path to the root module file or module manifest file.</span></span>

  <span data-ttu-id="20cc6-142">Ytterligare funktioner, till exempel följande, fungerar inte om modulen inte importeras till sessionen.</span><span class="sxs-lookup"><span data-stu-id="20cc6-142">Additional features, such as the following, do not work unless the module is imported into the session.</span></span> <span data-ttu-id="20cc6-143">I välformulerade moduler i **PSModulePath** -miljövariabeln fungerar dessa funktioner även när modulen inte importeras till sessionen.</span><span class="sxs-lookup"><span data-stu-id="20cc6-143">In well-formed modules in the **PSModulePath** environment variable, these features work even when the module is not imported into the session.</span></span>

- <span data-ttu-id="20cc6-144">Cmdleten [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) kan inte hitta kommandon i modulen.</span><span class="sxs-lookup"><span data-stu-id="20cc6-144">The [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet cannot find commands in the module.</span></span>

- <span data-ttu-id="20cc6-145">Cmdletarna [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) och [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) kan inte uppdatera eller spara hjälp för modulen.</span><span class="sxs-lookup"><span data-stu-id="20cc6-145">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets cannot update or save help for the module.</span></span>

- <span data-ttu-id="20cc6-146">Cmdleten [show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) kan inte hitta och Visa kommandon i modulen.</span><span class="sxs-lookup"><span data-stu-id="20cc6-146">The [Show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) cmdlet cannot find and display the commands in the module.</span></span>

  <span data-ttu-id="20cc6-147">Kommandona i modulen saknas i `Show-Command` fönstret i Windows POWERSHELL Ise (Integrated Scripting Environment).</span><span class="sxs-lookup"><span data-stu-id="20cc6-147">The commands in the module are missing from the `Show-Command` window in Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="where-to-install-modules"></a><span data-ttu-id="20cc6-148">Installera moduler</span><span class="sxs-lookup"><span data-stu-id="20cc6-148">Where to Install Modules</span></span>

<span data-ttu-id="20cc6-149">I det här avsnittet beskrivs var i fil systemet det ska gå att installera Windows PowerShell-moduler.</span><span class="sxs-lookup"><span data-stu-id="20cc6-149">This section explains where in the file system to install Windows PowerShell modules.</span></span> <span data-ttu-id="20cc6-150">Platsen beror på hur modulen används.</span><span class="sxs-lookup"><span data-stu-id="20cc6-150">The location depends on how the module is used.</span></span>

### <a name="installing-modules-for-a-specific-user"></a><span data-ttu-id="20cc6-151">Installera moduler för en speciell användare</span><span class="sxs-lookup"><span data-stu-id="20cc6-151">Installing Modules for a Specific User</span></span>

<span data-ttu-id="20cc6-152">Om du skapar en egen modul eller hämtar en modul från en annan part, till exempel en Windows PowerShell Community-webbplats, och du vill att modulen bara ska vara tillgänglig för ditt användar konto, installerar du modulen i din användarspecifika katalog.</span><span class="sxs-lookup"><span data-stu-id="20cc6-152">If you create your own module or get a module from another party, such as a Windows PowerShell community website, and you want the module to be available for your user account only, install the module in your user-specific Modules directory.</span></span>

`$home\Documents\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

<span data-ttu-id="20cc6-153">Katalogen med användarspecifika moduler läggs till i värdet för miljövariabeln **PSModulePath** som standard.</span><span class="sxs-lookup"><span data-stu-id="20cc6-153">The user-specific Modules directory is added to the value of the **PSModulePath** environment variable by default.</span></span>

### <a name="installing-modules-for-all-users-in-program-files"></a><span data-ttu-id="20cc6-154">Installera moduler för alla användare i programfiler</span><span class="sxs-lookup"><span data-stu-id="20cc6-154">Installing Modules for all Users in Program Files</span></span>

<span data-ttu-id="20cc6-155">Om du vill att en modul ska vara tillgänglig för alla användar konton på datorn installerar du modulen på platsen program fil.</span><span class="sxs-lookup"><span data-stu-id="20cc6-155">If you want a module to be available to all user accounts on the computer, install the module in the Program Files location.</span></span>

`$Env:ProgramFiles\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

> [!NOTE]
> <span data-ttu-id="20cc6-156">Platsen för program filer läggs till i värdet för PSModulePath-miljövariabeln som standard i Windows PowerShell 4,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="20cc6-156">The Program Files location is added to the value of the PSModulePath environment variable by default in Windows PowerShell 4.0 and later.</span></span> <span data-ttu-id="20cc6-157">För tidigare versioner av Windows PowerShell kan du manuellt skapa platsen för programfiler (%ProgramFiles%\WindowsPowerShell\Modules) och lägga till den här sökvägen till PSModulePath-miljövariabeln enligt beskrivningen ovan.</span><span class="sxs-lookup"><span data-stu-id="20cc6-157">For earlier versions of Windows PowerShell, you can manually create the Program Files location (%ProgramFiles%\WindowsPowerShell\Modules) and add this path to your PSModulePath environment variable as described above.</span></span>

### <a name="installing-modules-in-a-product-directory"></a><span data-ttu-id="20cc6-158">Installera moduler i en produkt katalog</span><span class="sxs-lookup"><span data-stu-id="20cc6-158">Installing Modules in a Product Directory</span></span>

<span data-ttu-id="20cc6-159">Om du distribuerar modulen till andra parter använder du standard platsen för programfiler som beskrivs ovan eller skapar en egen företagsspecifik eller produktspecifik under katalog till katalogen% ProgramFiles%.</span><span class="sxs-lookup"><span data-stu-id="20cc6-159">If you are distributing the module to other parties, use the default Program Files location described above, or create your own company-specific or product-specific subdirectory of the %ProgramFiles% directory.</span></span>

<span data-ttu-id="20cc6-160">Exempelvis levererar Fabrikam Technologies, ett fiktivt företag, en Windows PowerShell-modul för sin Fabrikam Manager-produkt.</span><span class="sxs-lookup"><span data-stu-id="20cc6-160">For example, Fabrikam Technologies, a fictitious company, is shipping a Windows PowerShell module for their Fabrikam Manager product.</span></span> <span data-ttu-id="20cc6-161">Installations programmet för modulen skapar en underkatalog för moduler i under katalogen Fabrikam Manager-produkt.</span><span class="sxs-lookup"><span data-stu-id="20cc6-161">Their module installer creates a Modules subdirectory in the Fabrikam Manager product subdirectory.</span></span>

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

<span data-ttu-id="20cc6-162">Om du vill aktivera identifierings funktionerna i Windows PowerShell-modulen för att hitta Fabrikam-modulen lägger du till modulen i värdet för **PSModulePath** -miljövariabeln i installations programmet för Fabrikam-modulen.</span><span class="sxs-lookup"><span data-stu-id="20cc6-162">To enable the Windows PowerShell module discovery features to find the Fabrikam module, the Fabrikam module installer adds the module location to the value of the **PSModulePath** environment variable.</span></span>

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam Technologies\Fabrikam Manager\Modules\"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

### <a name="installing-modules-in-the-common-files-directory"></a><span data-ttu-id="20cc6-163">Installera moduler i Common Files-katalogen</span><span class="sxs-lookup"><span data-stu-id="20cc6-163">Installing Modules in the Common Files Directory</span></span>

<span data-ttu-id="20cc6-164">Om en modul används av flera komponenter i en produkt eller flera versioner av en produkt, installerar du modulen i en modul-Specific-underkatalogen i under katalogen%ProgramFiles%\Common Files\Modules.</span><span class="sxs-lookup"><span data-stu-id="20cc6-164">If a module is used by multiple components of a product or by multiple versions of a product, install the module in a module-specific subdirectory of the %ProgramFiles%\Common Files\Modules subdirectory.</span></span>

<span data-ttu-id="20cc6-165">I följande exempel installeras modulen Fabrikam i en Fabrikam-under katalog i under `%ProgramFiles%\Common Files\Modules` katalogen.</span><span class="sxs-lookup"><span data-stu-id="20cc6-165">In the following example, the Fabrikam module is installed in a Fabrikam subdirectory of the `%ProgramFiles%\Common Files\Modules` subdirectory.</span></span> <span data-ttu-id="20cc6-166">Observera att varje modul finns i en egen under katalog i under katalogen moduler.</span><span class="sxs-lookup"><span data-stu-id="20cc6-166">Note that each module resides in its own subdirectory in the Modules subdirectory.</span></span>

```
C:\Program Files
  Common Files
    Modules
      Fabrikam
        Fabrikam.psd1 (module manifest)
        Fabrikam.dll (module assembly)
```

<span data-ttu-id="20cc6-167">Installations programmet säkerställer sedan att värdet för **PSModulePath** -miljövariabeln innehåller sökvägen till under katalogen vanliga filer för moduler.</span><span class="sxs-lookup"><span data-stu-id="20cc6-167">Then, the installer assures the value of the **PSModulePath** environment variable includes the path of the common files modules subdirectory.</span></span>

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

## <a name="installing-multiple-versions-of-a-module"></a><span data-ttu-id="20cc6-168">Installera flera versioner av en modul</span><span class="sxs-lookup"><span data-stu-id="20cc6-168">Installing Multiple Versions of a Module</span></span>

<span data-ttu-id="20cc6-169">Om du vill installera flera versioner av samma modul använder du följande procedur.</span><span class="sxs-lookup"><span data-stu-id="20cc6-169">To install multiple versions of the same module, use the following procedure.</span></span>

1. <span data-ttu-id="20cc6-170">Skapa en katalog för varje version av modulen.</span><span class="sxs-lookup"><span data-stu-id="20cc6-170">Create a directory for each version of the module.</span></span> <span data-ttu-id="20cc6-171">Inkludera versions numret i katalog namnet.</span><span class="sxs-lookup"><span data-stu-id="20cc6-171">Include the version number in the directory name.</span></span>
2. <span data-ttu-id="20cc6-172">Skapa ett modul manifest för varje version av modulen.</span><span class="sxs-lookup"><span data-stu-id="20cc6-172">Create a module manifest for each version of the module.</span></span> <span data-ttu-id="20cc6-173">I värdet för nyckeln **ModuleVersion** i manifestet anger du versions numret för modulen.</span><span class="sxs-lookup"><span data-stu-id="20cc6-173">In the value of the **ModuleVersion** key in the manifest, enter the module version number.</span></span> <span data-ttu-id="20cc6-174">Spara manifest filen (. psd1) i den versions bara katalogen för modulen.</span><span class="sxs-lookup"><span data-stu-id="20cc6-174">Save the manifest file (.psd1) in the version-specific directory for the module.</span></span>
3. <span data-ttu-id="20cc6-175">Lägg till rotmappen för modulen rot i värdet för **PSModulePath** -miljövariabeln, som visas i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="20cc6-175">Add the module root folder path to the value of the **PSModulePath** environment variable, as shown in the following examples.</span></span>

<span data-ttu-id="20cc6-176">Om du vill importera en viss version av modulen kan slutanvändaren använda `MinimumVersion` `RequiredVersion` parametrarna eller för cmdleten [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) .</span><span class="sxs-lookup"><span data-stu-id="20cc6-176">To import a particular version of the module, the end-user can use the `MinimumVersion` or `RequiredVersion` parameters of the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span></span>

<span data-ttu-id="20cc6-177">Om till exempel Fabrikam-modulen är tillgänglig i versionerna 8,0 och 9,0 kan katalog strukturen Fabrikam likna följande.</span><span class="sxs-lookup"><span data-stu-id="20cc6-177">For example, if the Fabrikam module is available in versions 8.0 and 9.0, the Fabrikam module directory structure might resemble the following.</span></span>

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

<span data-ttu-id="20cc6-178">Installations programmet lägger till båda modulens sökvägar i **PSModulePath** -miljövariabeln-värde.</span><span class="sxs-lookup"><span data-stu-id="20cc6-178">The installer adds both of the module paths to the **PSModulePath** environment variable value.</span></span>

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam\Fabrikam8;C:\Program Files\Fabrikam\Fabrikam9"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

<span data-ttu-id="20cc6-179">När de här stegen är klara, hämtar parametern **ListAvailable** för cmdleten [Get-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) båda fabriks modulerna.</span><span class="sxs-lookup"><span data-stu-id="20cc6-179">When these steps are complete, the **ListAvailable** parameter of the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet gets both of the Fabrikam modules.</span></span> <span data-ttu-id="20cc6-180">Om du vill importera en viss modul använder `MinimumVersion` du `RequiredVersion` parametrarna eller för cmdleten [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) .</span><span class="sxs-lookup"><span data-stu-id="20cc6-180">To import a particular module, use the `MinimumVersion` or `RequiredVersion` parameters of the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span></span>

<span data-ttu-id="20cc6-181">Om båda modulerna importeras till samma session och modulerna innehåller cmdlets med samma namn, gäller cmdletarna som importeras sist i sessionen.</span><span class="sxs-lookup"><span data-stu-id="20cc6-181">If both modules are imported into the same session, and the modules contain cmdlets with the same names, the cmdlets that are imported last are effective in the session.</span></span>

## <a name="handling-command-name-conflicts"></a><span data-ttu-id="20cc6-182">Hantera kommando namns konflikter</span><span class="sxs-lookup"><span data-stu-id="20cc6-182">Handling Command Name Conflicts</span></span>

<span data-ttu-id="20cc6-183">Kommando namns konflikter kan uppstå när kommandon som en modul exporterar har samma namn som kommandon i användarens session.</span><span class="sxs-lookup"><span data-stu-id="20cc6-183">Command name conflicts can occur when the commands that a module exports have the same name as commands in the user's session.</span></span>

<span data-ttu-id="20cc6-184">När en session innehåller två kommandon som har samma namn, kör Windows PowerShell den kommando typ som har företräde.</span><span class="sxs-lookup"><span data-stu-id="20cc6-184">When a session contains two commands that have the same name, Windows PowerShell runs the command type that takes precedence.</span></span> <span data-ttu-id="20cc6-185">När en session innehåller två kommandon som har samma namn och samma typ, kör Windows PowerShell kommandot som har lagts till i sessionen senast.</span><span class="sxs-lookup"><span data-stu-id="20cc6-185">When a session contains two commands that have the same name and the same type, Windows PowerShell runs the command that was added to the session most recently.</span></span> <span data-ttu-id="20cc6-186">Om du vill köra ett kommando som inte körs som standard kan användare kvalificera sig med kommandots namn med namnet på modulen.</span><span class="sxs-lookup"><span data-stu-id="20cc6-186">To run a command that is not run by default, users can qualify the command name with the module name.</span></span>

<span data-ttu-id="20cc6-187">Om sessionen t. ex. innehåller en `Get-Date` funktion och `Get-Date` cmdleten körs funktionen som standard i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="20cc6-187">For example, if the session contains a `Get-Date` function and the `Get-Date` cmdlet, Windows PowerShell runs the function by default.</span></span> <span data-ttu-id="20cc6-188">Om du vill köra cmdleten, Inled kommandot med namnet på modulen, till exempel:</span><span class="sxs-lookup"><span data-stu-id="20cc6-188">To run the cmdlet, preface the command with the module name, such as:</span></span>

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

<span data-ttu-id="20cc6-189">För att förhindra namn konflikter kan modulen författare använda **DefaultCommandPrefix** -nyckeln i modulen manifest för att ange ett substantiv-prefix för alla kommandon som exporteras från modulen.</span><span class="sxs-lookup"><span data-stu-id="20cc6-189">To prevent name conflicts, module authors can use the **DefaultCommandPrefix** key in the module manifest to specify a noun prefix for all commands exported from the module.</span></span>

<span data-ttu-id="20cc6-190">Användare kan använda parametern **prefix** för `Import-Module` cmdleten för att använda ett alternativt prefix.</span><span class="sxs-lookup"><span data-stu-id="20cc6-190">Users can use the **Prefix** parameter of the `Import-Module` cmdlet to use an alternate prefix.</span></span> <span data-ttu-id="20cc6-191">Värdet för parametern **prefix** har företräde framför värdet för **DefaultCommandPrefix** -nyckeln.</span><span class="sxs-lookup"><span data-stu-id="20cc6-191">The value of the **Prefix** parameter takes precedence over the value of the **DefaultCommandPrefix** key.</span></span>

## <a name="see-also"></a><span data-ttu-id="20cc6-192">Se även</span><span class="sxs-lookup"><span data-stu-id="20cc6-192">See Also</span></span>

[<span data-ttu-id="20cc6-193">about_Command_Precedence</span><span class="sxs-lookup"><span data-stu-id="20cc6-193">about_Command_Precedence</span></span>](/powershell/module/microsoft.powershell.core/about/about_command_precedence)

[<span data-ttu-id="20cc6-194">Skriva en Windows PowerShell-modul</span><span class="sxs-lookup"><span data-stu-id="20cc6-194">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
