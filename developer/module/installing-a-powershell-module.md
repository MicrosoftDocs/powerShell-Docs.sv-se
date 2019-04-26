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
ms.openlocfilehash: 7c2bfca50de4645676eafc01bbf23d9797e8b758
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082200"
---
# <a name="installing-a-powershell-module"></a><span data-ttu-id="94ee2-102">Installera en PowerShell-modul</span><span class="sxs-lookup"><span data-stu-id="94ee2-102">Installing a PowerShell Module</span></span>

<span data-ttu-id="94ee2-103">När du har skapat din PowerShell-modulen, kommer troligen du att installera modulen på ett system, så att du eller andra kan använda den.</span><span class="sxs-lookup"><span data-stu-id="94ee2-103">After you have created your PowerShell module, you will likely want to install the module on a system, so that you or others may use it.</span></span> <span data-ttu-id="94ee2-104">Generellt sett består detta bara modulen filerna kopieras (.psm1, eller binära sammansättningen, modulmanifestet, och andra tillhörande filer) till en katalog på datorn.</span><span class="sxs-lookup"><span data-stu-id="94ee2-104">Generally speaking, this simply consists of copying the module files (ie, the .psm1, or the binary assembly, the module manifest, and any other associated files) onto a directory on that computer.</span></span> <span data-ttu-id="94ee2-105">För ett mycket små projekt, och detta kan vara lika enkelt som att kopiera och klistra in filerna med Windows Explorer till en fjärransluten dator. men för större lösningar kan du använda en mer avancerad installationsprocess.</span><span class="sxs-lookup"><span data-stu-id="94ee2-105">For a very small project, this may be as simple as copying and pasting the files with Windows Explorer onto a single remote computer; however, for larger solutions you may wish to use a more sophisticated installation process.</span></span> <span data-ttu-id="94ee2-106">Oavsett hur du får din modul till systemet, kan PowerShell använda flera olika tekniker som låter användarna hitta och använda dina moduler.</span><span class="sxs-lookup"><span data-stu-id="94ee2-106">Regardless of how you get your module onto the system, PowerShell can use a number of techniques that will let users find and use your modules.</span></span> <span data-ttu-id="94ee2-107">(Mer information finns i [importera en PowerShell-modul](./importing-a-powershell-module.md).) Största problemet för installation därför se till att PowerShell kommer att kunna hitta din modul.</span><span class="sxs-lookup"><span data-stu-id="94ee2-107">(For more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md).) Therefore, the main issue for installation is ensuring that PowerShell will be able to find your module.</span></span>

<span data-ttu-id="94ee2-108">Det här avsnittet består av följande underavsnitt:</span><span class="sxs-lookup"><span data-stu-id="94ee2-108">This topic contains the following sections:</span></span>

- <span data-ttu-id="94ee2-109">Regler för att installera moduler</span><span class="sxs-lookup"><span data-stu-id="94ee2-109">Rules for Installing Modules</span></span>

- <span data-ttu-id="94ee2-110">Var du vill installera moduler</span><span class="sxs-lookup"><span data-stu-id="94ee2-110">Where to Install Modules</span></span>

- <span data-ttu-id="94ee2-111">Installera flera versioner av en modul</span><span class="sxs-lookup"><span data-stu-id="94ee2-111">Installing Multiple Versions of a Module</span></span>

- <span data-ttu-id="94ee2-112">Hantering av kommandot namnet står i konflikt</span><span class="sxs-lookup"><span data-stu-id="94ee2-112">Handling Command Name Conflicts</span></span>

## <a name="rules-for-installing-modules"></a><span data-ttu-id="94ee2-113">Regler för att installera moduler</span><span class="sxs-lookup"><span data-stu-id="94ee2-113">Rules for Installing Modules</span></span>

<span data-ttu-id="94ee2-114">Följande information gäller alla moduler, inklusive moduler som du skapar för användning, moduler som du får från andra parter och moduler som du distribuerar till andra.</span><span class="sxs-lookup"><span data-stu-id="94ee2-114">The following information pertains to all modules, including modules that you create for your own use, modules that you get from other parties, and modules that you distribute to others.</span></span>

### <a name="install-modules-in-psmodulepath"></a><span data-ttu-id="94ee2-115">Installera moduler i PSModulePath</span><span class="sxs-lookup"><span data-stu-id="94ee2-115">Install Modules in PSModulePath</span></span>

<span data-ttu-id="94ee2-116">När det är möjligt, installera alla moduler i en sökväg som anges i den **PSModulePath** miljövariabeln eller Lägg till modulen sökvägen till den **PSModulePath** miljövariabelvärdet.</span><span class="sxs-lookup"><span data-stu-id="94ee2-116">Whenever possible, install all modules in a path that is listed in the **PSModulePath** environment variable or add the module path to the **PSModulePath** environment variable value.</span></span>

<span data-ttu-id="94ee2-117">Den **PSModulePath** miljövariabeln ($Env: PSModulePath) innehåller platserna för Windows PowerShell-moduler.</span><span class="sxs-lookup"><span data-stu-id="94ee2-117">The **PSModulePath** environment variable ($Env:PSModulePath) contains the locations of Windows PowerShell modules.</span></span> <span data-ttu-id="94ee2-118">Cmdlet: ar är beroende av värdet för den här miljövariabeln för att hitta moduler.</span><span class="sxs-lookup"><span data-stu-id="94ee2-118">Cmdlets rely on the value of this environment variable to find modules.</span></span>

<span data-ttu-id="94ee2-119">Som standard den **PSModulePath** miljövariabelvärdet innehåller följande system och användaren modulen kataloger, men du kan lägga till och redigera värdet.</span><span class="sxs-lookup"><span data-stu-id="94ee2-119">By default, the **PSModulePath** environment variable value contains the following system and user module directories, but you can add to and edit the value.</span></span>

- <span data-ttu-id="94ee2-120">$PSHome\Modules (%Windir%\System32\WindowsPowerShell\v1.0\Modules)</span><span class="sxs-lookup"><span data-stu-id="94ee2-120">$PSHome\Modules (%Windir%\System32\WindowsPowerShell\v1.0\Modules)</span></span>

  > [!WARNING]
  > <span data-ttu-id="94ee2-121">Den här platsen är reserverad för moduler som medföljer Windows.</span><span class="sxs-lookup"><span data-stu-id="94ee2-121">This location is reserved for modules that ship with Windows.</span></span> <span data-ttu-id="94ee2-122">Installera inte moduler till den här platsen.</span><span class="sxs-lookup"><span data-stu-id="94ee2-122">Do not install modules to this location.</span></span>

- <span data-ttu-id="94ee2-123">$Home\Documents\WindowsPowerShell\Modules (% UserProfile%\Documents\WindowsPowerShell\Modules)</span><span class="sxs-lookup"><span data-stu-id="94ee2-123">$Home\Documents\WindowsPowerShell\Modules (%UserProfile%\Documents\WindowsPowerShell\Modules)</span></span>

- <span data-ttu-id="94ee2-124">$Env: ProgramFiles\WindowsPowerShell\Modules (% ProgramFiles%\WindowsPowerShell\Modules)</span><span class="sxs-lookup"><span data-stu-id="94ee2-124">$Env:ProgramFiles\WindowsPowerShell\Modules (%ProgramFiles%\WindowsPowerShell\Modules)</span></span>

  <span data-ttu-id="94ee2-125">Att hämta värdet för den **PSModulePath** miljövariabeln, använda någon av följande kommandon.</span><span class="sxs-lookup"><span data-stu-id="94ee2-125">To get the value of the **PSModulePath** environment variable, use either of the following commands.</span></span>

  ```powershell
  $Env:PSModulePath
  [Environment]::GetEnvironmentVariable("PSModulePath")
  ```

  <span data-ttu-id="94ee2-126">Att lägga till en modulsökväg till värdet för den **PSModulePath** miljövariabeln värde, använder du följande kommandoformat.</span><span class="sxs-lookup"><span data-stu-id="94ee2-126">To add a module path to value of the **PSModulePath** environment variable value, use the following command format.</span></span> <span data-ttu-id="94ee2-127">Det här formatet använder den **SetEnvironmentVariable** -metoden för den **System.Environment** klassen för att göra en ändring av sessionen oberoende den **PSModulePath** miljö variabeln.</span><span class="sxs-lookup"><span data-stu-id="94ee2-127">This format uses the **SetEnvironmentVariable** method of the **System.Environment** class to make a session-independent change to the **PSModulePath** environment variable.</span></span>

  ```powershell

  #Save the current value in the $p variable.
  $p = [Environment]::GetEnvironmentVariable("PSModulePath")

  #Add the new path to the $p variable. Begin with a semi-colon separator.
  $p += ";C:\Program Files (x86)\MyCompany\Modules\"

  #Add the paths in $p to the PSModulePath value.
  [Environment]::SetEnvironmentVariable("PSModulePath",$p)

  ```

  > [!IMPORTANT]
  > <span data-ttu-id="94ee2-128">När du har lagt till sökvägen till **PSModulePath**, bör du skicka meddelandet miljö om ändringen.</span><span class="sxs-lookup"><span data-stu-id="94ee2-128">Once you have added the path to **PSModulePath**, you should broadcast an environment message about the change.</span></span> <span data-ttu-id="94ee2-129">Sänder ändringen kan andra program, till exempel i gränssnittet och att välja ändringen.</span><span class="sxs-lookup"><span data-stu-id="94ee2-129">Broadcasting the change allows other applications, such as the shell, to pick up the change.</span></span> <span data-ttu-id="94ee2-130">Om du vill skicka ändringen har din kod för installation av produkten skicka en **uppdaterats** med `lParam` anger till strängen ”miljö”.</span><span class="sxs-lookup"><span data-stu-id="94ee2-130">To broadcast the change, have your product installation code send a **WM_SETTINGCHANGE** message with `lParam` set to the string "Environment".</span></span> <span data-ttu-id="94ee2-131">Se till att skicka meddelandet när modulen installationen koden har uppdaterats **PSModulePath**.</span><span class="sxs-lookup"><span data-stu-id="94ee2-131">Be sure to send the message after your module installation code has updated **PSModulePath**.</span></span>

### <a name="use-the-correct-module-directory-name"></a><span data-ttu-id="94ee2-132">Använd rätt modul katalognamn</span><span class="sxs-lookup"><span data-stu-id="94ee2-132">Use the Correct Module Directory Name</span></span>

<span data-ttu-id="94ee2-133">En ”välformulerad” modul är en modul som lagras i en mapp med samma namn som det grundläggande namnet på minst en fil i modulkatalogen.</span><span class="sxs-lookup"><span data-stu-id="94ee2-133">A "well-formed" module is a module that is stored in a directory that has the same name as the base name of at least one file in the module directory.</span></span> <span data-ttu-id="94ee2-134">Om en modul inte är korrekt formaterad, känner Windows PowerShell inte igen det som en modul.</span><span class="sxs-lookup"><span data-stu-id="94ee2-134">If a module is not well-formed, Windows PowerShell does not recognize it as a module.</span></span>

<span data-ttu-id="94ee2-135">”Huvudnamnet” för en fil är namn utan filnamnstillägget.</span><span class="sxs-lookup"><span data-stu-id="94ee2-135">The "base name" of a file is the name without the file name extension.</span></span> <span data-ttu-id="94ee2-136">I en giltig modul, måste namnet på den katalog som innehåller filerna som modulen matcha det grundläggande namnet på minst en fil i modulen.</span><span class="sxs-lookup"><span data-stu-id="94ee2-136">In a well-formed module, the name of the directory that contains the module files must match the base name of at least one file in the module.</span></span>

<span data-ttu-id="94ee2-137">Till exempel i Fabrikam exempelmodulen den katalog som innehåller filerna som modulen heter ”Fabrikam” och minst en fil har det grundläggande namnet ”Fabrikam”.</span><span class="sxs-lookup"><span data-stu-id="94ee2-137">For example, in the sample Fabrikam module, the directory that contains the module files is named "Fabrikam" and at least one file has the "Fabrikam" base name.</span></span> <span data-ttu-id="94ee2-138">I det här fallet har både Fabrikam.psd1 och Fabrikam.dll det grundläggande namnet ”Fabrikam”.</span><span class="sxs-lookup"><span data-stu-id="94ee2-138">In this case, both Fabrikam.psd1 and Fabrikam.dll have the "Fabrikam" base name.</span></span>

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

### <a name="effect-of-incorrect-installation"></a><span data-ttu-id="94ee2-139">Effekten av felaktig Installation</span><span class="sxs-lookup"><span data-stu-id="94ee2-139">Effect of Incorrect Installation</span></span>

<span data-ttu-id="94ee2-140">Om modulen är inte korrekt formaterad och dess plats ingår inte i värdet för den **PSModulePath** miljövariabeln, identifiering av grundläggande funktioner i Windows PowerShell, exempelvis följande, fungerar inte.</span><span class="sxs-lookup"><span data-stu-id="94ee2-140">If the module is not well-formed and its location is not included in the value of the **PSModulePath** environment variable, basic discovery features of Windows PowerShell, such as the following, do not work.</span></span>

- <span data-ttu-id="94ee2-141">Modulen automatisk inläsning-funktionen kan inte importera modulen automatiskt.</span><span class="sxs-lookup"><span data-stu-id="94ee2-141">The Module Auto-Loading feature cannot import the module automatically.</span></span>

- <span data-ttu-id="94ee2-142">Den `ListAvailable` -parametern för den [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet kan inte hitta modulen.</span><span class="sxs-lookup"><span data-stu-id="94ee2-142">The `ListAvailable` parameter of the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet cannot find the module.</span></span>

- <span data-ttu-id="94ee2-143">Den [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet kan inte hitta modulen.</span><span class="sxs-lookup"><span data-stu-id="94ee2-143">The [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet cannot find the module.</span></span> <span data-ttu-id="94ee2-144">Du måste ange den fullständiga sökvägen till rot-filen för modulen eller modulen manifestfilen om du vill importera modulen.</span><span class="sxs-lookup"><span data-stu-id="94ee2-144">To import the module, you must provide the full path to the root module file or module manifest file.</span></span>

  <span data-ttu-id="94ee2-145">Ytterligare funktioner, till exempel följande, fungerar inte om inte modulen har importerats till sessionen.</span><span class="sxs-lookup"><span data-stu-id="94ee2-145">Additional features, such as the following, do not work unless the module is imported into the session.</span></span> <span data-ttu-id="94ee2-146">I rätt moduler i den **PSModulePath** miljövariabeln, dessa funktioner fungerar även om modulen inte importeras till sessionen.</span><span class="sxs-lookup"><span data-stu-id="94ee2-146">In well-formed modules in the **PSModulePath** environment variable, these features work even when the module is not imported into the session.</span></span>

- <span data-ttu-id="94ee2-147">Den [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet kan inte hitta kommandon i modulen.</span><span class="sxs-lookup"><span data-stu-id="94ee2-147">The [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet cannot find commands in the module.</span></span>

- <span data-ttu-id="94ee2-148">Den [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) och [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets kan inte uppdatera eller spara hjälp för modulen.</span><span class="sxs-lookup"><span data-stu-id="94ee2-148">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets cannot update or save help for the module.</span></span>

- <span data-ttu-id="94ee2-149">Den [visningskommandot](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) cmdlet: Det går inte att hitta och visa kommandon i modulen.</span><span class="sxs-lookup"><span data-stu-id="94ee2-149">The [Show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) cmdlet cannot find and display the commands in the module.</span></span>

  <span data-ttu-id="94ee2-150">Kommandona i modulen saknas från den `Show-Command` fönster i Windows PowerShell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="94ee2-150">The commands in the module are missing from the `Show-Command` window in Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="where-to-install-modules"></a><span data-ttu-id="94ee2-151">Var du vill installera moduler</span><span class="sxs-lookup"><span data-stu-id="94ee2-151">Where to Install Modules</span></span>

<span data-ttu-id="94ee2-152">Det här avsnittet beskrivs var i filsystemet för att installera Windows PowerShell-moduler.</span><span class="sxs-lookup"><span data-stu-id="94ee2-152">This section explains where in the file system to install Windows PowerShell modules.</span></span> <span data-ttu-id="94ee2-153">Platsen är beroende av hur modulen ska användas.</span><span class="sxs-lookup"><span data-stu-id="94ee2-153">The location depends on how the module is used.</span></span>

### <a name="installing-modules-for-a-specific-user"></a><span data-ttu-id="94ee2-154">Installera moduler för en viss användare</span><span class="sxs-lookup"><span data-stu-id="94ee2-154">Installing Modules for a Specific User</span></span>

<span data-ttu-id="94ee2-155">Om du skapar en egen modul eller få en modul från en annan part, till exempel en community-webbplatsen för Windows PowerShell, och du vill att modulen ska vara tillgängliga för ditt konto endast, installera modulen i katalogen användarspecifika moduler.</span><span class="sxs-lookup"><span data-stu-id="94ee2-155">If you create your own module or get a module from another party, such as a Windows PowerShell community website, and you want the module to be available for your user account only, install the module in your user-specific Modules directory.</span></span>

```
$home\Documents\WindowsPowerShell\Modules\<Module Folder>\<Module Files>
```

<span data-ttu-id="94ee2-156">Katalogen användarspecifika moduler läggs till i värdet för den **PSModulePath** miljövariabeln som standard.</span><span class="sxs-lookup"><span data-stu-id="94ee2-156">The user-specific Modules directory is added to the value of the **PSModulePath** environment variable by default.</span></span>

### <a name="installing-modules-for-all-users-in-program-files"></a><span data-ttu-id="94ee2-157">Installera moduler för alla användare i program</span><span class="sxs-lookup"><span data-stu-id="94ee2-157">Installing Modules for all Users in Program Files</span></span>

<span data-ttu-id="94ee2-158">Om du vill att en modul ska vara tillgängliga för alla användarkonton på datorn, installera modulen på platsen för programmet.</span><span class="sxs-lookup"><span data-stu-id="94ee2-158">If you want a module to be available to all user accounts on the computer, install the module in the Program Files location.</span></span>

```
$Env:ProgramFiles\WindowsPowerShell\Modules\<Module Folder>\<Module Files>
```

> [!NOTE]
> <span data-ttu-id="94ee2-159">Plats för programfiler läggs till värdet för miljövariabeln PSModulePath som standard i Windows PowerShell 4.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="94ee2-159">The Program Files location is added to the value of the PSModulePath environment variable by default in Windows PowerShell 4.0 and later.</span></span> <span data-ttu-id="94ee2-160">För tidigare versioner av Windows PowerShell kan du manuellt skapa programfiler plats ((%ProgramFiles%\WindowsPowerShell\Modules) och lägga till den här sökvägen i miljövariabeln PSModulePath enligt beskrivningen ovan.</span><span class="sxs-lookup"><span data-stu-id="94ee2-160">For earlier versions of Windows PowerShell, you can manually create the Program Files location ((%ProgramFiles%\WindowsPowerShell\Modules) and add this path to your PSModulePath environment variable as described above.</span></span>

### <a name="installing-modules-in-a-product-directory"></a><span data-ttu-id="94ee2-161">Installerar moduler i en produktkatalog</span><span class="sxs-lookup"><span data-stu-id="94ee2-161">Installing Modules in a Product Directory</span></span>

<span data-ttu-id="94ee2-162">Om du ska distribuera modulen till andra parter använda standardplatsen för programfiler som beskrivs ovan, eller skapa egna företagsspecifik eller produktspecifik underkatalog i katalogen % ProgramFiles %.</span><span class="sxs-lookup"><span data-stu-id="94ee2-162">If you are distributing the module to other parties, use the default Program Files location described above, or create your own company-specific or product-specific subdirectory of the %ProgramFiles% directory.</span></span>

<span data-ttu-id="94ee2-163">Fabrikam-tekniker, ett fiktivt företag, levereras till exempel en Windows PowerShell-modul för sina Fabrikam Manager-produkten.</span><span class="sxs-lookup"><span data-stu-id="94ee2-163">For example, Fabrikam Technologies, a fictitious company, is shipping a Windows PowerShell module for their Fabrikam Manager product.</span></span> <span data-ttu-id="94ee2-164">Sina modulen installer skapar en underkatalog moduler i underkatalogen Fabrikam Manager produkten.</span><span class="sxs-lookup"><span data-stu-id="94ee2-164">Their module installer creates a Modules subdirectory in the Fabrikam Manager product subdirectory.</span></span>

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

<span data-ttu-id="94ee2-165">Om du vill aktivera Windows PowerShell-modulen identifiering funktioner att hitta modulen Fabrikam Fabrikam modulen installationsprogrammet lägger till modulen platsen till värdet för den **PSModulePath** miljövariabeln.</span><span class="sxs-lookup"><span data-stu-id="94ee2-165">To enable the Windows PowerShell module discovery features to find the Fabrikam module, the Fabrikam module installer adds the module location to the value of the **PSModulePath** environment variable.</span></span>

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += "C:\Program Files\Fabrikam Technologies\Fabrikam Manager\Modules\"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

### <a name="installing-modules-in-the-common-files-directory"></a><span data-ttu-id="94ee2-166">Installerar moduler i katalogen med vanliga</span><span class="sxs-lookup"><span data-stu-id="94ee2-166">Installing Modules in the Common Files Directory</span></span>

<span data-ttu-id="94ee2-167">Om en modul används av flera komponenter i en produkt eller genom att flera versioner av en produkt, installera modulen i en modul-specifika underkatalog i underkatalogen %ProgramFiles%\Common Files\Modules.</span><span class="sxs-lookup"><span data-stu-id="94ee2-167">If a module is used by multiple components of a product or by multiple versions of a product, install the module in a module-specific subdirectory of the %ProgramFiles%\Common Files\Modules subdirectory.</span></span>

<span data-ttu-id="94ee2-168">I följande exempel installeras Fabrikam-modulen i en underkatalog för Fabrikam i underkatalogen %ProgramFiles%\Common Files\Modules.</span><span class="sxs-lookup"><span data-stu-id="94ee2-168">In the following example, the Fabrikam module is installed in a Fabrikam subdirectory of the %ProgramFiles%\Common Files\Modules subdirectory.</span></span> <span data-ttu-id="94ee2-169">Observera att varje modul finns i en egen underkatalog i underkatalogen moduler.</span><span class="sxs-lookup"><span data-stu-id="94ee2-169">Note that each module resides in its own subdirectory in the Modules subdirectory.</span></span>

```
C:\Program Files
  Common Files
    Modules
      Fabrikam
        Fabrikam.psd1 (module manifest)
        Fabrikam.dll (module assembly)

```

<span data-ttu-id="94ee2-170">Sedan kan installationsprogrammet säkerställer värdet för den **PSModulePath** miljövariabeln innehåller sökvägen i underkatalogen moduler vanliga filer.</span><span class="sxs-lookup"><span data-stu-id="94ee2-170">Then, the installer assures the value of the **PSModulePath** environment variable includes the path of the common files modules subdirectory.</span></span>

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

## <a name="installing-multiple-versions-of-a-module"></a><span data-ttu-id="94ee2-171">Installera flera versioner av en modul</span><span class="sxs-lookup"><span data-stu-id="94ee2-171">Installing Multiple Versions of a Module</span></span>

<span data-ttu-id="94ee2-172">Använd följande procedur för att installera flera versioner av samma modul.</span><span class="sxs-lookup"><span data-stu-id="94ee2-172">To install multiple versions of the same module, use the following procedure.</span></span>

1. <span data-ttu-id="94ee2-173">Skapa en katalog för varje version av modulen.</span><span class="sxs-lookup"><span data-stu-id="94ee2-173">Create a directory for each version of the module.</span></span> <span data-ttu-id="94ee2-174">Inkludera versionsnumret i katalognamnet.</span><span class="sxs-lookup"><span data-stu-id="94ee2-174">Include the version number in the directory name.</span></span>

2. <span data-ttu-id="94ee2-175">Skapa ett modulmanifest för varje version av modulen.</span><span class="sxs-lookup"><span data-stu-id="94ee2-175">Create a module manifest for each version of the module.</span></span> <span data-ttu-id="94ee2-176">I värdet för den **ModuleVersion** nyckeln i manifestet, ange versionsnummer för modulen.</span><span class="sxs-lookup"><span data-stu-id="94ee2-176">In the value of the **ModuleVersion** key in the manifest, enter the module version number.</span></span> <span data-ttu-id="94ee2-177">Spara manifestfilen (.psd1) i katalogen versionsspecifika för modulen.</span><span class="sxs-lookup"><span data-stu-id="94ee2-177">Save the manifest file (.psd1) in the version-specific directory for the module.</span></span>

3. <span data-ttu-id="94ee2-178">Lägg till sökvägen till rotmappen modulen till värdet för den **PSModulePath** miljövariabeln, som visas i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="94ee2-178">Add the module root folder path to the value of the **PSModulePath** environment variable, as shown in the following examples.</span></span>

<span data-ttu-id="94ee2-179">Om du vill importera en viss version av modulen, slutanvändaren kan använda den `MinimumVersion` eller `RequiredVersion` parametrarna för den [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="94ee2-179">To import a particular version of the module, the end-user can use the `MinimumVersion` or `RequiredVersion` parameters of the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span></span>

<span data-ttu-id="94ee2-180">Till exempel om modulen Fabrikam är tillgängliga i version 8.0 och 9.0, kan katalogstruktur för Fabrikam-modulen likna följande.</span><span class="sxs-lookup"><span data-stu-id="94ee2-180">For example, if the Fabrikam module is available in versions 8.0 and 9.0, the Fabrikam module directory structure might resemble the following.</span></span>

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

<span data-ttu-id="94ee2-181">Installationsprogrammet lägger till båda modulernas sökvägar till den **PSModulePath** miljövariabelvärdet.</span><span class="sxs-lookup"><span data-stu-id="94ee2-181">The installer adds both of the module paths to the **PSModulePath** environment variable value.</span></span>

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam\Fabrikam8;C:\Program Files\Fabrikam\Fabrikam9"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

<span data-ttu-id="94ee2-182">När dessa steg har slutförts, den **ListAvailable** -parametern för den [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet hämtar båda Fabrikam-moduler.</span><span class="sxs-lookup"><span data-stu-id="94ee2-182">When these steps are complete, the **ListAvailable** parameter of the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet gets both of the Fabrikam modules.</span></span> <span data-ttu-id="94ee2-183">Om du vill importera en viss modul, Använd den `MinimumVersion` eller `RequiredVersion` parametrarna för den [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="94ee2-183">To import a particular module, use the `MinimumVersion` or `RequiredVersion` parameters of the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span></span>

<span data-ttu-id="94ee2-184">Om båda moduler importeras till samma session, och moduler innehåller cmdletar och arbetsflöden med samma namn, gäller de cmdletar som importeras senast i sessionen.</span><span class="sxs-lookup"><span data-stu-id="94ee2-184">If both modules are imported into the same session, and the modules contain cmdlets with the same names, the cmdlets that are imported last are effective in the session.</span></span>

## <a name="handling-command-name-conflicts"></a><span data-ttu-id="94ee2-185">Hantering av kommandot namnet står i konflikt</span><span class="sxs-lookup"><span data-stu-id="94ee2-185">Handling Command Name Conflicts</span></span>

<span data-ttu-id="94ee2-186">Namnkonflikter i kommandot kan inträffa när de kommandon som en modul exporterar har samma namn som kommandon i sessionen.</span><span class="sxs-lookup"><span data-stu-id="94ee2-186">Command name conflicts can occur when the commands that a module exports have the same name as commands in the user's session.</span></span>

<span data-ttu-id="94ee2-187">När en session innehåller två kommandon som har samma namn, kör Windows PowerShell kommandotypen som företräde.</span><span class="sxs-lookup"><span data-stu-id="94ee2-187">When a session contains two commands that have the same name, Windows PowerShell runs the command type that takes precedence.</span></span> <span data-ttu-id="94ee2-188">När en session innehåller två kommandon som har samma namn och samma typ, kör Windows PowerShell-kommandot som har lagts till i sessionen senast.</span><span class="sxs-lookup"><span data-stu-id="94ee2-188">When a session contains two commands that have the same name and the same type, Windows PowerShell runs the command that was added to the session most recently.</span></span> <span data-ttu-id="94ee2-189">Om du vill köra ett kommando som inte körs som standard, kan användare kvalificera sig kommandonamnet med modulens namn.</span><span class="sxs-lookup"><span data-stu-id="94ee2-189">To run a command that is not run by default, users can qualify the command name with the module name.</span></span>

<span data-ttu-id="94ee2-190">Om sessionen innehåller till exempel en `Get-Date` funktion och `Get-Date` Windows PowerShell-cmdleten körs funktionen som standard.</span><span class="sxs-lookup"><span data-stu-id="94ee2-190">For example, if the session contains a `Get-Date` function and the `Get-Date` cmdlet, Windows PowerShell runs the function by default.</span></span> <span data-ttu-id="94ee2-191">För att köra cmdlet: en, måste du börja kommandot med modulens namn, till exempel:</span><span class="sxs-lookup"><span data-stu-id="94ee2-191">To run the cmdlet, preface the command with the module name, such as:</span></span>

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

<span data-ttu-id="94ee2-192">För att förhindra namnkonflikter modulskapare kan använda den **DefaultCommandPrefix** exportera nyckeln i modulmanifestet att ange ett substantivprefix för alla kommandon från modulen.</span><span class="sxs-lookup"><span data-stu-id="94ee2-192">To prevent name conflicts, module authors can use the **DefaultCommandPrefix** key in the module manifest to specify a noun prefix for all commands exported from the module.</span></span>

<span data-ttu-id="94ee2-193">Användare kan använda den **Prefix** -parametern för den `Import-Module` cmdlet för att använda en annan prefix.</span><span class="sxs-lookup"><span data-stu-id="94ee2-193">Users can use the **Prefix** parameter of the `Import-Module` cmdlet to use an alternate prefix.</span></span> <span data-ttu-id="94ee2-194">Värdet för den **prefixet** parametern har företräde framför värdet för den **DefaultCommandPrefix** nyckel.</span><span class="sxs-lookup"><span data-stu-id="94ee2-194">The value of the **Prefix** parameter takes precedence over the value of the **DefaultCommandPrefix** key.</span></span>

## <a name="see-also"></a><span data-ttu-id="94ee2-195">Se även</span><span class="sxs-lookup"><span data-stu-id="94ee2-195">See Also</span></span>

[<span data-ttu-id="94ee2-196">about_Command_Precedence</span><span class="sxs-lookup"><span data-stu-id="94ee2-196">about_Command_Precedence</span></span>](/powershell/module/microsoft.powershell.core/about/about_command_precedence)

[<span data-ttu-id="94ee2-197">Skriva ett Windows PowerShell-modul</span><span class="sxs-lookup"><span data-stu-id="94ee2-197">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
