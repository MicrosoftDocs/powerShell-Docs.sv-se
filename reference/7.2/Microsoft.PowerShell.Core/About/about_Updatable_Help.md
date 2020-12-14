---
description: Beskriver det uppdaterings bara hjälp systemet i PowerShell.
Locale: en-US
ms.date: 08/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_updatable_help?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Updatable_Help
ms.openlocfilehash: d688448b5aab8ec35ab5d57b444ad9902b8e8ecd
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710512"
---
# <a name="about-updatable-help"></a><span data-ttu-id="160ee-103">Om uppdaterbar hjälp</span><span class="sxs-lookup"><span data-stu-id="160ee-103">About Updatable Help</span></span>

## <a name="short-description"></a><span data-ttu-id="160ee-104">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="160ee-104">Short description</span></span>
<span data-ttu-id="160ee-105">Beskriver det uppdaterings bara hjälp systemet i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="160ee-105">Describes the updatable help system in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="160ee-106">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="160ee-106">Long description</span></span>

<span data-ttu-id="160ee-107">PowerShell tillhandahåller flera olika sätt att komma åt de mest aktuella hjälp avsnitten för PowerShell-cmdletar och-koncept.</span><span class="sxs-lookup"><span data-stu-id="160ee-107">PowerShell provides several different ways to access the most up-to-date help topics for PowerShell cmdlets and concepts.</span></span>

<span data-ttu-id="160ee-108">Det uppdaterings bara hjälp systemet, som introducerades i PowerShell 3,0, är utformat för att säkerställa att du alltid har de senaste hjälp avsnitten på den lokala datorn så att du kan läsa dem på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="160ee-108">The Updatable Help system, introduced in PowerShell 3.0, is designed to assure that you always have the newest help topics on your local computer so that you can read them at the command line.</span></span> <span data-ttu-id="160ee-109">Det gör det enkelt att hämta och installera hjälpfiler och att uppdatera dem när nya hjälpfiler blir tillgängliga.</span><span class="sxs-lookup"><span data-stu-id="160ee-109">It makes it easy to download and install help files and to update them whenever newer help files become available.</span></span>

<span data-ttu-id="160ee-110">Om du vill tillhandahålla uppdaterad hjälp för flera datorer i ett företag och för datorer som inte har åtkomst till Internet, kan du hämta hjälp filen till en fil Systems katalog eller fil resurs och sedan installera hjälpfilerna från fil resursen.</span><span class="sxs-lookup"><span data-stu-id="160ee-110">To provide updated help for multiple computers in an enterprise and for computers that do not have access to the internet, Updatable Help lets you download help files to a filesystem directory or file share, and then install the help files from the file share.</span></span>

<span data-ttu-id="160ee-111">I PowerShell 4,0 bevaras egenskapen **HelpInfoUri** över Windows PowerShell-fjärrkommunikation, som gör `Save-Help` att du kan arbeta med moduler som är installerade på en fjärrdator, men som inte nödvändigt vis är installerade på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="160ee-111">In PowerShell 4.0, the **HelpInfoUri** property is preserved over Windows PowerShell remoting, which allows `Save-Help` to work for modules that are installed on a remote computer, but are not necessarily installed on the local computer.</span></span> <span data-ttu-id="160ee-112">Du kan spara ett **PSModuleInfo** -objekt på en disk eller ett flyttbart medium (till exempel en USB-enhet) genom `Export-Clixml` att köra på en dator som inte har Internet åtkomst, importera **PSModuleInfo** -objektet på en dator som har Internet åtkomst och sedan köra `Save-Help` på **PSModuleInfo** -objektet.</span><span class="sxs-lookup"><span data-stu-id="160ee-112">You can save a **PSModuleInfo** object to disk or removable media (such as a USB drive) by running `Export-Clixml` on a computer that does not have internet access, importing the **PSModuleInfo** object on a computer that does have internet access, and then running `Save-Help` on the **PSModuleInfo** object.</span></span> <span data-ttu-id="160ee-113">Den sparade hjälpen kan kopieras till fjärrdatorn, frånkopplad dator med hjälp av ett flyttbart medium och sedan installeras genom att köra `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="160ee-113">The saved help can be copied to the remote, disconnected computer by using removable media, and then installed by running `Update-Help`.</span></span> <span data-ttu-id="160ee-114">Med de här förbättringarna av `Save-Help` funktioner kan du installera hjälp på datorer som inte har någon typ av nätverks åtkomst.</span><span class="sxs-lookup"><span data-stu-id="160ee-114">These improvements in `Save-Help` functionality let you install help on computers that are without any kind of network access.</span></span> <span data-ttu-id="160ee-115">Ett exempel på hur du använder de nya `Save-Help` funktionerna finns i [så här uppdaterar du hjälpen från en fil resurs](#how-to-update-help-from-a-file-share) i det här avsnittet.</span><span class="sxs-lookup"><span data-stu-id="160ee-115">For an example of how to use the new `Save-Help` functionality, see [How to update help from a file share](#how-to-update-help-from-a-file-share) in this topic.</span></span>

<span data-ttu-id="160ee-116">Uppdaterings bar hjälp stöder också online-åtkomst till de senaste hjälp avsnitten och Basic-hjälpen för cmdlets, även om det inte finns några hjälpfiler på datorn.</span><span class="sxs-lookup"><span data-stu-id="160ee-116">Updatable Help also supports online access to the newest help topics and basic help for cmdlets, even when there are no help files on the computer.</span></span>

<span data-ttu-id="160ee-117">PowerShell 3,0 kommer inte med hjälpfilerna.</span><span class="sxs-lookup"><span data-stu-id="160ee-117">PowerShell 3.0 does not come with Help files.</span></span> <span data-ttu-id="160ee-118">Du kan använda funktionen uppdaterbar hjälp för att installera hjälpfilerna för alla kommandon som ingår som standard i PowerShell och för alla Windows-moduler.</span><span class="sxs-lookup"><span data-stu-id="160ee-118">You can use the Updatable Help feature to install the help files for all of the commands that are included by default in PowerShell and for all Windows modules.</span></span>

## <a name="updatable-help-cmdlets"></a><span data-ttu-id="160ee-119">Uppdaterings bara hjälp-cmdletar</span><span class="sxs-lookup"><span data-stu-id="160ee-119">Updatable help cmdlets</span></span>

- <span data-ttu-id="160ee-120">`Update-Help`: Laddar ned de senaste hjälpfilerna från Internet eller en fil resurs och installerar dem på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="160ee-120">`Update-Help`: Downloads the newest help files from the internet or a file share, and installs them on the local computer.</span></span>

- <span data-ttu-id="160ee-121">`Save-Help`: Laddar ned de senaste hjälpfilerna från Internet och sparar dem i fil system katalogen eller fil resursen.</span><span class="sxs-lookup"><span data-stu-id="160ee-121">`Save-Help`: Downloads the newest help files from the internet and saves them in a filesystem directory or file share.</span></span> <span data-ttu-id="160ee-122">Om du vill installera hjälpfilerna på datorer använder du `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="160ee-122">To install the help files on computers, use `Update-Help`.</span></span>

- <span data-ttu-id="160ee-123">`Get-Help`: Visar hjälp avsnitt på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="160ee-123">`Get-Help`: Displays help topics at the command line.</span></span> <span data-ttu-id="160ee-124">Hämtar hjälp från hjälp filen på datorn.</span><span class="sxs-lookup"><span data-stu-id="160ee-124">Gets help from the help files on the computer.</span></span> <span data-ttu-id="160ee-125">Visar automatiskt genererad hjälp för cmdletar och funktioner som inte har hjälpfiler.</span><span class="sxs-lookup"><span data-stu-id="160ee-125">Displays auto-generated help for cmdlets and functions that do not have help files.</span></span> <span data-ttu-id="160ee-126">Öppnar direkt hjälp avsnitt för cmdlets, functions, scripts och arbets flöden i din standard webbläsare.</span><span class="sxs-lookup"><span data-stu-id="160ee-126">Opens online help topics for cmdlets, functions, scripts, and workflows in your default internet browser.</span></span>

## <a name="auto-generated-help-help-without-help-files"></a><span data-ttu-id="160ee-127">Automatiskt genererad hjälp: hjälp utan hjälp filer</span><span class="sxs-lookup"><span data-stu-id="160ee-127">Auto-generated help: help without help files</span></span>

<span data-ttu-id="160ee-128">Om du inte har hjälp filen för en cmdlet, funktion eller ett arbets flöde på datorn, `Get-Help` visar cmdlet: en automatiskt genererad hjälp och du uppmanas att hämta hjälpfilerna eller läsa dem online.</span><span class="sxs-lookup"><span data-stu-id="160ee-128">If you do not have the help file for a cmdlet, function, or workflow on the computer, the `Get-Help` cmdlet displays auto-generated help and prompts you to download the help files or read them online.</span></span>

<span data-ttu-id="160ee-129">Automatiskt genererad hjälp innehåller syntax och alias och kommentarer som förklarar hur du använder de uppdaterbara hjälp-cmdletarna och för att få åtkomst till hjälp avsnitten online.</span><span class="sxs-lookup"><span data-stu-id="160ee-129">Auto-generated help includes syntax and aliases, and remarks that explain how to use the Updatable Help cmdlets and to access the online help topics.</span></span>

<span data-ttu-id="160ee-130">Följande kommando hämtar till exempel grundläggande hjälp för `Get-Culture` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="160ee-130">For example, the following command gets basic help for the `Get-Culture` cmdlet.</span></span> <span data-ttu-id="160ee-131">Utdata visar `Get-Help` visningen när det inte finns några hjälpfiler på datorn.</span><span class="sxs-lookup"><span data-stu-id="160ee-131">The output shows the `Get-Help` display when there are no help files on the computer.</span></span>

```powershell
Get-Help Get-Culture
```

```output
NAME
    Get-Culture

SYNTAX
    Get-Culture [<CommonParameters>]

ALIASES
    None

REMARKS
    To get the latest Help content including descriptions and examples
    type: Update-Help.
```

## <a name="help-files-for-modules"></a><span data-ttu-id="160ee-132">Hjälp filer för moduler</span><span class="sxs-lookup"><span data-stu-id="160ee-132">Help files for modules</span></span>

<span data-ttu-id="160ee-133">Den minsta enheten med uppdaterings bara hjälp är hjälp för en modul.</span><span class="sxs-lookup"><span data-stu-id="160ee-133">The smallest unit of Updatable Help is help for a module.</span></span> <span data-ttu-id="160ee-134">I modulen hjälp finns hjälp för alla cmdletar, funktioner, arbets flöden, providrar, skript och koncept i en modul.</span><span class="sxs-lookup"><span data-stu-id="160ee-134">Module help includes help for all of the cmdlets, functions, workflows, providers, scripts, and concepts in a module.</span></span> <span data-ttu-id="160ee-135">Du kan uppdatera hjälpen för alla moduler som är installerade på datorn, även om de inte importeras till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="160ee-135">You can update help for all modules that are installed on the computer, even if they are not imported into the current session.</span></span>

<span data-ttu-id="160ee-136">Du kan uppdatera hjälpen för hela modulen, men du kan inte uppdatera hjälpen för enskilda cmdlets.</span><span class="sxs-lookup"><span data-stu-id="160ee-136">You can update help for the entire module, but you cannot update help for individual cmdlets.</span></span>

<span data-ttu-id="160ee-137">Om du vill hitta modulen som innehåller en viss cmdlet använder du följande kommando format:</span><span class="sxs-lookup"><span data-stu-id="160ee-137">To find the module that contains a particular cmdlet, use the following command format:</span></span>

```powershell
(Get-Command <cmdlet-name>).ModuleName
```

<span data-ttu-id="160ee-138">Om du till exempel vill hitta modulen som innehåller `Set-ExecutionPolicy` cmdleten skriver du:</span><span class="sxs-lookup"><span data-stu-id="160ee-138">For example, to find the module that contains the `Set-ExecutionPolicy` cmdlet, type:</span></span>

```powershell
(Get-Command Set-ExecutionPolicy).ModuleName
```

<span data-ttu-id="160ee-139">Om du vill uppdatera hjälpen för en viss modul skriver du:</span><span class="sxs-lookup"><span data-stu-id="160ee-139">To update help for a particular module, type:</span></span>

```powershell
Update-Help -Module <ModuleName>
```

<span data-ttu-id="160ee-140">Om du till exempel vill uppdatera hjälpen för den modul som innehåller Set-ExecutionPolicy-cmdlet skriver du:</span><span class="sxs-lookup"><span data-stu-id="160ee-140">For example, to update help for the module that contains the Set-ExecutionPolicy cmdlet, type:</span></span>

```powershell
Update-Help -Module Microsoft.PowerShell.Security
```

## <a name="permissions-for-updatable-help"></a><span data-ttu-id="160ee-141">Behörigheter för uppdaterbar hjälp</span><span class="sxs-lookup"><span data-stu-id="160ee-141">Permissions for updatable help</span></span>

<span data-ttu-id="160ee-142">Om du vill uppdatera hjälpen för modulerna i katalogen `$pshome/Modules` måste du vara medlem i gruppen Administratörer på datorn.</span><span class="sxs-lookup"><span data-stu-id="160ee-142">To update help for the modules in the directory `$pshome/Modules`, you must be member of the Administrators group on the computer.</span></span>

<span data-ttu-id="160ee-143">Om du inte är medlem i gruppen Administratörer kan du inte uppdatera hjälpen för de här modulerna. men om du har till gång till Internet kan du Visa hjälp online.</span><span class="sxs-lookup"><span data-stu-id="160ee-143">If you are not a member of the Administrators group, you cannot update help for these modules; but if you have internet access, you can view help online.</span></span>

<span data-ttu-id="160ee-144">Att uppdatera hjälpen för moduler i katalogen `$home/Documents/PowerShell/Modules` eller modulerna i andra under kataloger i `$home` katalogen kräver inte särskilda behörigheter.</span><span class="sxs-lookup"><span data-stu-id="160ee-144">Updating help for modules in the directory `$home/Documents/PowerShell/Modules` or modules in other subdirectories of the `$home` directory does not require special permissions.</span></span>

<span data-ttu-id="160ee-145">`Update-Help` `Save-Help` Cmdletarna och har en **UseDefaultCredentials** -parameter som ger den aktuella användarens uttryckliga autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="160ee-145">The `Update-Help` and `Save-Help` cmdlets have a **UseDefaultCredentials** parameter that provides the explicit credentials of the current user.</span></span> <span data-ttu-id="160ee-146">Den här parametern är utformad för att komma åt säkra Internet-platser.</span><span class="sxs-lookup"><span data-stu-id="160ee-146">This parameter is designed for accessing secure internet locations.</span></span>

<span data-ttu-id="160ee-147">`Update-Help` `Save-Help` Cmdletarna och har också en parameter för **autentiseringsuppgifter** som gör att du kan köra kommandot på en fjärrdator och komma åt en fil resurs på en tredje dator.</span><span class="sxs-lookup"><span data-stu-id="160ee-147">The `Update-Help` and `Save-Help` cmdlets also have a **Credential** parameter that allows you to run the command on a remote computer and access a file share on a third computer.</span></span> <span data-ttu-id="160ee-148">Parametern **Credential** är bara giltig när du använder SourcePath-eller **LiteralPath** -parametrarna i `Update-Help` och **DestinationPath** -eller **LiteralPath** -parametrarna för `Save-Help` .</span><span class="sxs-lookup"><span data-stu-id="160ee-148">The **Credential** parameter is valid only when you use the SourcePath or **LiteralPath** parameters of `Update-Help` and the **DestinationPath** or **LiteralPath** parameters of `Save-Help`.</span></span>

## <a name="how-to-install-and-update-help-files"></a><span data-ttu-id="160ee-149">Installera och uppdatera hjälpfiler</span><span class="sxs-lookup"><span data-stu-id="160ee-149">How to install and update help files</span></span>

<span data-ttu-id="160ee-150">Om du vill hämta och installera hjälpfiler för första gången, eller om du vill uppdatera hjälpfilerna på datorn, använder du `Update-Help` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="160ee-150">To download and install help files for the first time, or to update the help files on your computer, use the `Update-Help` cmdlet.</span></span>

<span data-ttu-id="160ee-151">`Update-Help`Cmdleten gör allt det hårda arbetet åt dig, inklusive följande uppgifter.</span><span class="sxs-lookup"><span data-stu-id="160ee-151">The `Update-Help` cmdlet does all of the hard work for you, including the following tasks.</span></span>

- <span data-ttu-id="160ee-152">Avgör vilka moduler som stöder uppdaterbar hjälp.</span><span class="sxs-lookup"><span data-stu-id="160ee-152">Determines which modules support Updatable Help.</span></span>
- <span data-ttu-id="160ee-153">Söker efter Internet-platsen där varje modul lagrar de uppdaterbara hjälpfilerna.</span><span class="sxs-lookup"><span data-stu-id="160ee-153">Finds the internet location where each module stores its Updatable Help files.</span></span>
- <span data-ttu-id="160ee-154">Jämför hjälpfilerna för varje modul på datorn med de senaste hjälpfilerna som är tillgängliga för varje modul.</span><span class="sxs-lookup"><span data-stu-id="160ee-154">Compares the help files for each module on your computer to the newest help files that are available for each module.</span></span>
- <span data-ttu-id="160ee-155">Laddar ned de nya filerna från Internet.</span><span class="sxs-lookup"><span data-stu-id="160ee-155">Downloads the new files from the internet.</span></span>
- <span data-ttu-id="160ee-156">Avbryter hjälp fils paketet.</span><span class="sxs-lookup"><span data-stu-id="160ee-156">Unwraps the help file package.</span></span>
- <span data-ttu-id="160ee-157">Kontrollerar att filerna är giltiga hjälpfiler.</span><span class="sxs-lookup"><span data-stu-id="160ee-157">Verifies that the files are valid help files.</span></span>
- <span data-ttu-id="160ee-158">Installerar hjälpfilerna i den språkspecifika under katalogen i modulens katalog.</span><span class="sxs-lookup"><span data-stu-id="160ee-158">Installs the help files in the language-specific subdirectory of the module directory.</span></span>

<span data-ttu-id="160ee-159">Använd cmdleten för att få åtkomst till de nya hjälp avsnitten `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="160ee-159">To access the new help topics, use the `Get-Help` cmdlet.</span></span> <span data-ttu-id="160ee-160">Du behöver inte starta om PowerShell.</span><span class="sxs-lookup"><span data-stu-id="160ee-160">You do not need to restart PowerShell.</span></span>

<span data-ttu-id="160ee-161">Om du vill installera eller uppdatera hjälpen för alla moduler på datorn som stöder uppdaterings bar hjälp skriver du:</span><span class="sxs-lookup"><span data-stu-id="160ee-161">To install or update help for all modules on the computer that supports Updatable Help, type:</span></span>

```powershell
Update-Help
```

<span data-ttu-id="160ee-162">Om du vill uppdatera hjälpen för vissa moduler lägger du till **modulen modul** för `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="160ee-162">To update help for particular modules, add the **Module** parameter of `Update-Help`.</span></span> <span data-ttu-id="160ee-163">Jokertecken tillåts i modulnamnet.</span><span class="sxs-lookup"><span data-stu-id="160ee-163">Wildcard characters are permitted in the module name.</span></span>

<span data-ttu-id="160ee-164">Om du till exempel vill uppdatera hjälp för ServerManager-modulen skriver du:</span><span class="sxs-lookup"><span data-stu-id="160ee-164">For example, to update help for the ServerManager module, type:</span></span>

```powershell
Update-Help -Module ServerManager
```

<span data-ttu-id="160ee-165">Utan parametrar kan du `Update-Help` Uppdatera hjälpen för alla moduler i sessionen och för alla installerade moduler som stöder uppdaterbar hjälp.</span><span class="sxs-lookup"><span data-stu-id="160ee-165">Without parameters, `Update-Help` updates help for all modules in the session and for all installed modules that support Updatable Help.</span></span> <span data-ttu-id="160ee-166">Moduler måste installeras i kataloger som anges i värdet för PSModulePath-miljövariabeln för att tas med.</span><span class="sxs-lookup"><span data-stu-id="160ee-166">To be included, modules must be installed in directories that are listed in the value of the PSModulePath environment variable.</span></span> <span data-ttu-id="160ee-167">Dessa är också moduler som returneras av kommandot "Get-Help-ListAvailable".</span><span class="sxs-lookup"><span data-stu-id="160ee-167">These are also modules that are returned by a "Get-Help -ListAvailable" command.</span></span>

<span data-ttu-id="160ee-168">Om värdet för **modulen modul** är `*` (alla) `Update-Help` försöker att uppdatera hjälpen för alla installerade moduler, inklusive moduler som inte stöder uppdaterbar hjälp.</span><span class="sxs-lookup"><span data-stu-id="160ee-168">If the value of the **Module** parameter is `*` (all), `Update-Help` attempts to update help for all installed modules, including modules that do not support Updatable Help.</span></span> <span data-ttu-id="160ee-169">Det här kommandot genererar vanligt vis många fel eftersom cmdleten påträffar moduler som inte stöder uppdaterbar hjälp.</span><span class="sxs-lookup"><span data-stu-id="160ee-169">This command typically generates many errors as the cmdlet encounters modules that do not support Updatable Help.</span></span>

## <a name="how-to-update-help-from-a-file-share"></a><span data-ttu-id="160ee-170">Så här uppdaterar du hjälpen från en fil resurs</span><span class="sxs-lookup"><span data-stu-id="160ee-170">How to update help from a file share</span></span>

<span data-ttu-id="160ee-171">Om du vill ha stöd för datorer som inte är anslutna till Internet, eller om du vill styra eller effektivisera hjälp med att uppdatera i ett företag, använder du `Save-Help` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="160ee-171">To support computers that are not connected to the internet, or to control or streamline help updating in an enterprise, use the `Save-Help` cmdlet.</span></span> <span data-ttu-id="160ee-172">`Save-Help`Cmdlet: en laddar ned hjälpfiler från Internet och sparar dem i en fil Systems katalog som du anger.</span><span class="sxs-lookup"><span data-stu-id="160ee-172">The `Save-Help` cmdlet downloads help files from the internet and saves them in a filesystem directory that you specify.</span></span>

<span data-ttu-id="160ee-173">`Save-Help` Jämför hjälpfilerna i den angivna katalogen med de senaste hjälpfilerna som är tillgängliga för varje modul.</span><span class="sxs-lookup"><span data-stu-id="160ee-173">`Save-Help` compares the help files in the specified directory to the newest help files that are available for each module.</span></span> <span data-ttu-id="160ee-174">Om katalogen inte innehåller några hjälpfiler eller om det finns nyare hjälpfiler för modulen, `Save-Help` laddar cmdleten ned de nya filerna från Internet.</span><span class="sxs-lookup"><span data-stu-id="160ee-174">If the directory has no help files or newer help files are available for the module, the `Save-Help` cmdlet downloads the new files from the internet.</span></span> <span data-ttu-id="160ee-175">Men det går inte att packa upp eller installera hjälpfilerna.</span><span class="sxs-lookup"><span data-stu-id="160ee-175">However, it does not unwrap or install the help files.</span></span>

<span data-ttu-id="160ee-176">Om du vill installera eller uppdatera hjälpfilerna på en dator från hjälpfiler som sparats i en fil Systems katalog använder du cmdlet: en **SourcePath** -parameter `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="160ee-176">To install or update the help files on a computer from help files that were saved to a filesystem directory, use the **SourcePath** parameter of the `Update-Help` cmdlet.</span></span> <span data-ttu-id="160ee-177">`Update-Help`Cmdleten identifierar de senaste hjälpfilerna, avbryter och validerar dem och installerar dem i språkspecifika under kataloger i modulernas kataloger.</span><span class="sxs-lookup"><span data-stu-id="160ee-177">The `Update-Help` cmdlet identifies the newest help files, unwraps and validates them, and installs them in the language-specific subdirectories of the module directories.</span></span>

<span data-ttu-id="160ee-178">Om du till exempel vill spara hjälpen för alla installerade moduler till `\\Server\Share` katalogen skriver du:</span><span class="sxs-lookup"><span data-stu-id="160ee-178">For example, to save help for all installed modules to the `\\Server\Share` directory, type:</span></span>

```powershell
Save-Help -DestinationPath \\Server\Share
```

<span data-ttu-id="160ee-179">Om du vill uppdatera hjälpen från `\\Server\Share` katalogen skriver du:</span><span class="sxs-lookup"><span data-stu-id="160ee-179">Then, to update help from the `\\Server\Share` directory, type:</span></span>

```powershell
Update-Help -SourcePath \\Server\Share
```

<span data-ttu-id="160ee-180">I följande exempel visas användningen av `Save-Help` för att spara hjälp för moduler som inte är installerade på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="160ee-180">The following examples show the use of `Save-Help` to save help for modules that are not installed on the local computer.</span></span> <span data-ttu-id="160ee-181">I det här exemplet körs administratören för `Save-Help` att spara hjälpen för modulen DHCP server från en Internet-ansluten klient dator, utan att installera den DHCP-modul eller DHCP-serverrollen på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="160ee-181">In this example, the administrator runs `Save-Help` to save the help for the DhcpServer module from an internet-connected client computer, without installing the DhcpServer module or DHCP Server role on the local computer.</span></span>

<span data-ttu-id="160ee-182">Alternativ 1: kör `Invoke-Command` för att hämta **PSModuleInfo** -objektet för fjärrmodulen, spara det i en variabel `$m` och kör sedan `Save-Help` på **PSModuleInfo** -objektet genom att ange variabeln `$m` som modulnamn.</span><span class="sxs-lookup"><span data-stu-id="160ee-182">Option 1: Run `Invoke-Command` to get the **PSModuleInfo** object for the remote module, save it in a variable, `$m`, and then run `Save-Help` on the **PSModuleInfo** object by specifying the variable `$m` as the module name.</span></span>

```powershell
$m = Invoke-Command -ComputerName RemoteServer -ScriptBlock
{ Get-Module -Name DhcpServer -ListAvailable }
Save-Help -Module $m -DestinationPath C:\SavedHelp
```

<span data-ttu-id="160ee-183">Alternativ 2: öppna en PSSession som är riktad mot den dator som kör DHCP-server-modulen för att hämta **PSModuleInfo** -objektet för modulen, spara den i en variabel `$m` och sedan köra `Save-Help` på det objekt som har sparats i `$m` variabeln.</span><span class="sxs-lookup"><span data-stu-id="160ee-183">Option 2: Open a PSSession targeted at the computer that is running the DHCP Server module, to get the **PSModuleInfo** object for the module, save it in a variable `$m`, and then run `Save-Help` on the object that is saved in the `$m` variable.</span></span>

```powershell
$s = New-PSSession -ComputerName RemoteServer
$m = Get-Module -PSSession $s -Name DhcpServer -ListAvailable
Save-Help -Module $m -DestinationPath C:\SavedHelp
```

<span data-ttu-id="160ee-184">Alternativ 3: öppna en CIM-session, riktad mot den dator som kör DHCP-server-modulen, för att hämta **PSModuleInfo** -objektet för modulen, spara den i en variabel `$m` och kör sedan `Save-Help` på det objekt som har sparats i `$m` variabeln.</span><span class="sxs-lookup"><span data-stu-id="160ee-184">Option 3: Open a CIM session, targeted at the computer that is running the DHCP Server module, to get the **PSModuleInfo** object for the module, save it in a variable `$m`, and then run `Save-Help` on the object that is saved in the `$m` variable.</span></span>

```powershell
$c = New-CimSession -ComputerName RemoteServer
$m = Get-Module -CimSession $c -Name DhcpServer -ListAvailable
Save-Help -Module $m -DestinationPath C:\SavedHelp
```

<span data-ttu-id="160ee-185">I följande exempel installerar administratören hjälp för DHCP-modulen på en dator som inte har nätverks åtkomst.</span><span class="sxs-lookup"><span data-stu-id="160ee-185">In the following example, the administrator installs help for the DHCP Server module on a computer that does not have network access.</span></span>

<span data-ttu-id="160ee-186">Kör först `Export-Clixml` för att exportera **PSModuleInfo** -objektet till en delad mapp eller till ett flyttbart medium.</span><span class="sxs-lookup"><span data-stu-id="160ee-186">First, run `Export-Clixml` to export the **PSModuleInfo** object to a shared folder or to removable media.</span></span>

```powershell
$m = Get-Module -Name DhcpServer -ListAvailable
Export-Clixml -Path E:\UsbFlashDrive\DhcpModule.xml -InputObject $m
```

<span data-ttu-id="160ee-187">Nu ska du transportera det flyttbara mediet till en dator som har Internet åtkomst och sedan importera **PSModuleInfo** -objektet med `Import-Clixml` .</span><span class="sxs-lookup"><span data-stu-id="160ee-187">Next, transport the removable media to a computer that has internet access, and then import the **PSModuleInfo** object with `Import-Clixml`.</span></span> <span data-ttu-id="160ee-188">Kör för `Save-Help` att spara hjälpen för **PSModuleInfo** -objektet importerad DHCP-modul.</span><span class="sxs-lookup"><span data-stu-id="160ee-188">Run `Save-Help` to save the Help for the imported DhcpServer module **PSModuleInfo** object.</span></span>

```powershell
$deserialized_m = Import-Clixml E:\UsbFlashDrive\DhcpModule.xml
Save-Help -Module $deserialized_m -DestinationPath E:\UsbFlashDrive\SavedHelp
```

<span data-ttu-id="160ee-189">Slutligen kan du överföra det flyttbara mediet till datorn som inte har nätverks åtkomst och sedan installera hjälpen genom att köra `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="160ee-189">Finally, transport the removable media back to the computer that does not have network access, and then install the help by running `Update-Help`.</span></span>

```powershell
Update-Help -Module DhcpServer -SourcePath E:\UsbFlashDrive\SavedHelp
```

<span data-ttu-id="160ee-190">Utan parametrar kan du `Save-Help` Hämta hjälpen för alla moduler i sessionen och för alla installerade moduler som stöder uppdaterbar hjälp.</span><span class="sxs-lookup"><span data-stu-id="160ee-190">Without parameters, `Save-Help` downloads help for all modules in the session and for all installed modules that support Updatable Help.</span></span> <span data-ttu-id="160ee-191">Moduler måste installeras i kataloger som anges i värdet för `$env:PSModulePath` miljövariabeln, antingen på den lokala datorn eller på en fjärrdator som du vill spara hjälpen för.</span><span class="sxs-lookup"><span data-stu-id="160ee-191">To be included, modules must be installed in directories that are listed in the value of the `$env:PSModulePath` environment variable, on either the local computer or on a remote computer for which you want to save help.</span></span> <span data-ttu-id="160ee-192">Dessa är också moduler som returneras genom att köra ett `Get-Help -ListAvailable` kommando.</span><span class="sxs-lookup"><span data-stu-id="160ee-192">These are also modules that are returned by running a `Get-Help -ListAvailable` command.</span></span>

## <a name="how-to-update-help-files-in-different-languages"></a><span data-ttu-id="160ee-193">Så här uppdaterar du hjälpfiler på olika språk</span><span class="sxs-lookup"><span data-stu-id="160ee-193">How to update help files in different languages</span></span>

<span data-ttu-id="160ee-194">Som standard `Update-Help` `Save-Help` laddar cmdletarna ned hjälpen i användar gränssnitts kulturen och språket som är inställda för Windows på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="160ee-194">By default, the `Update-Help` and `Save-Help` cmdlets download help in the UI culture and language that is set for Windows on the local computer.</span></span> <span data-ttu-id="160ee-195">Om hjälpfilerna för de angivna modulerna inte är tillgängliga i den lokala användar gränssnitts kulturen, `Update-Help` och `Save-Help` Använd Windows språk återställnings regler för att hitta det språk som stöds bäst.</span><span class="sxs-lookup"><span data-stu-id="160ee-195">If help files for the specified modules are not available in the local UI culture, `Update-Help` and `Save-Help` use the Windows language fallback rules to find the best supported language.</span></span>

<span data-ttu-id="160ee-196">Du kan dock använda **värdet** -parametrarna för `Update-Help` `Save-Help` cmdletarna och för att hämta och installera hjälpfiler i alla användar gränssnitts kulturer där de är tillgängliga.</span><span class="sxs-lookup"><span data-stu-id="160ee-196">However, you can use the **UICulture** parameters of the `Update-Help` and `Save-Help` cmdlets to download and install help files in any UI cultures in which they are available.</span></span>

<span data-ttu-id="160ee-197">Om du till exempel vill spara de senaste hjälpfilerna för alla moduler i sessionen på japanska (ja-JP) och franska (fr-FR) skriver du:</span><span class="sxs-lookup"><span data-stu-id="160ee-197">For example, to save the newest help files for all modules on the session in Japanese (Ja-jp) and French (fr-FR), type:</span></span>

```powershell
Save-Help -Path \Server\Share -UICulture ja-jp, fr-fr
```

<span data-ttu-id="160ee-198">Om hjälpfilerna för modulerna inte är tillgängliga på de språk som du har angett `Update-Help` `Save-Help` returnerar cmdletarna och ett fel meddelande som visar de språk som hjälpen för varje modul är tillgänglig för, så att du kan välja det alternativ som bäst passar dina behov.</span><span class="sxs-lookup"><span data-stu-id="160ee-198">If help files for the modules are not available in the languages that you specified, the `Update-Help` and `Save-Help` cmdlets return an error message that lists the languages in which help for each module is available so you can choose the alternative that best meets your needs.</span></span>

> [!NOTE]
> <span data-ttu-id="160ee-199">Uppdaterings bara hjälp innehåll publiceras för närvarande bara på engelska (en-US).</span><span class="sxs-lookup"><span data-stu-id="160ee-199">Currently, Updateable Help content is only published in English (en-US).</span></span> <span data-ttu-id="160ee-200">På vissa icke-Windows-system måste du använda parametern **värdet** för att begära `en-US` innehållet explicit.</span><span class="sxs-lookup"><span data-stu-id="160ee-200">On some non-Windows systems you must use the **UICulture** parameter to explicitly request the `en-US` content.</span></span>

## <a name="how-to-use-online-help"></a><span data-ttu-id="160ee-201">Så här använder du onlinehjälpen</span><span class="sxs-lookup"><span data-stu-id="160ee-201">How to use online help</span></span>

<span data-ttu-id="160ee-202">Om du inte kan eller väljer att inte uppdatera hjälpfilerna på den lokala datorn kan du fortfarande hämta de senaste hjälpfilerna online.</span><span class="sxs-lookup"><span data-stu-id="160ee-202">If you cannot or choose not to update the help files on your local computer, you can still get the newest help files online.</span></span>

<span data-ttu-id="160ee-203">Om du vill öppna onlinehjälpen för en cmdlet eller funktion använder du cmdleten **online** för `Get-Help` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="160ee-203">To open the online help topic for any cmdlet or function, use the **Online** parameter of the `Get-Help` cmdlet.</span></span>

<span data-ttu-id="160ee-204">Följande kommando öppnar exempelvis onlinehjälpen för `Get-Job` cmdlet: en i din standard webbläsare:</span><span class="sxs-lookup"><span data-stu-id="160ee-204">For example, the following command opens the online help topic for the `Get-Job` cmdlet in your default internet browser:</span></span>

```powershell
Get-Help Get-Job -Online
```

<span data-ttu-id="160ee-205">Om du vill ha Onlinehjälp för ett skript använder du parametern **online** och den fullständiga sökvägen till skriptet.</span><span class="sxs-lookup"><span data-stu-id="160ee-205">To get online help for a script, use the **Online** parameter and the full path to the script.</span></span>

<span data-ttu-id="160ee-206">Parametern **online** fungerar inte med about-ämnen.</span><span class="sxs-lookup"><span data-stu-id="160ee-206">The **Online** parameter does not work with About topics.</span></span> <span data-ttu-id="160ee-207">Om du vill se avsnitten om PowerShell, inklusive hjälp avsnitt om PowerShell-språket, kan du läsa mer i [PowerShell om ämnen](about.md).</span><span class="sxs-lookup"><span data-stu-id="160ee-207">To see the about topics for PowerShell, including help topics about the PowerShell language, see [PowerShell About Topics](about.md).</span></span>

## <a name="how-to-minimize-or-prevent-internet-downloads"></a><span data-ttu-id="160ee-208">Minimera eller förhindra Internet hämtningar</span><span class="sxs-lookup"><span data-stu-id="160ee-208">How to minimize or prevent internet downloads</span></span>

<span data-ttu-id="160ee-209">Använd cmdleten för att minimera hämtning av Internet och tillhandahålla uppdaterings bar hjälp till användare som inte är anslutna till Internet. `Save-Help`</span><span class="sxs-lookup"><span data-stu-id="160ee-209">To minimize internet downloads and provide Updatable Help to users who are not connected to the internet, use the `Save-Help` cmdlet.</span></span> <span data-ttu-id="160ee-210">Hämta hjälpen från Internet och spara den på en nätverks resurs.</span><span class="sxs-lookup"><span data-stu-id="160ee-210">Download help from the internet and save it to a network share.</span></span> <span data-ttu-id="160ee-211">Skapa sedan en grupprincip inställning eller ett schemalagt jobb som kör ett `Update-Help` kommando på alla datorer.</span><span class="sxs-lookup"><span data-stu-id="160ee-211">Then, create a Group Policy setting or scheduled job that runs an `Update-Help` command on all computers.</span></span> <span data-ttu-id="160ee-212">Ange värdet för cmdlet- **parametern för** `Update-Help` cmdlet: en till nätverks resursen.</span><span class="sxs-lookup"><span data-stu-id="160ee-212">Set the value of the **SourcePath** parameter of the `Update-Help` cmdlet to the network share.</span></span>

<span data-ttu-id="160ee-213">Om du vill förhindra att användare som har Internet åtkomst laddar ned uppdaterings bar hjälp från Internet använder du inställningen **Ange standard Sök väg för uppdatering – hjälp** Grupprincip.</span><span class="sxs-lookup"><span data-stu-id="160ee-213">To prevent users who have internet access from downloading Updatable Help from the internet, use the **Set the default source path for Update-Help** Group Policy setting.</span></span>

<span data-ttu-id="160ee-214">Den här grupprincip inställningen lägger implicit till **SourcePath** -parametern, med den fil Systems plats som du anger, till alla `Update-Help` kommandon på varje dator som påverkas.</span><span class="sxs-lookup"><span data-stu-id="160ee-214">This Group Policy setting implicitly adds the **SourcePath** parameter, with the filesystem location that you specify, to every `Update-Help` command on every affected computer.</span></span> <span data-ttu-id="160ee-215">Användare kan använda **SourcePath** -parametern explicit för att ange en annan plats för fil systemet, men de kan inte utesluta **SourcePath** -parametern och hämta hjälpen från Internet.</span><span class="sxs-lookup"><span data-stu-id="160ee-215">Users can use the **SourcePath** parameter explicitly to specify a different filesystem location, but they cannot exclude the **SourcePath** parameter and download help from the internet.</span></span>

> [!NOTE]
> <span data-ttu-id="160ee-216">Inställningen **Ange standard käll Sök väg för uppdatering – hjälp för** grup princip visas under **dator konfiguration** och **användar konfiguration**.</span><span class="sxs-lookup"><span data-stu-id="160ee-216">The **Set the default source path for Update-Help** group policy setting appears under **Computer Configuration** and **User Configuration**.</span></span> <span data-ttu-id="160ee-217">Men endast princip inställningen under **dator konfiguration** är effektiv.</span><span class="sxs-lookup"><span data-stu-id="160ee-217">However, only the policy setting under **Computer Configuration** is effective.</span></span> <span data-ttu-id="160ee-218">Princip inställningen under **användar konfiguration** ignoreras.</span><span class="sxs-lookup"><span data-stu-id="160ee-218">The policy setting under **User Configuration** is ignored.</span></span>

<span data-ttu-id="160ee-219">Mer information finns i [about_Group_Policy_Settings](about_Group_Policy_Settings.md).</span><span class="sxs-lookup"><span data-stu-id="160ee-219">For more information, see [about_Group_Policy_Settings](about_Group_Policy_Settings.md).</span></span>

## <a name="how-to-update-help-for-non-standard-modules"></a><span data-ttu-id="160ee-220">Så här uppdaterar du hjälpen för moduler som inte är standard</span><span class="sxs-lookup"><span data-stu-id="160ee-220">How to update help for non-standard modules</span></span>

<span data-ttu-id="160ee-221">Om du vill uppdatera eller spara hjälp för en modul som inte returneras av **ListAvailable** -parametern för `Get-Module` cmdleten importerar du modulen till den aktuella sessionen innan du kör ett `Update-Help` eller- `Save-Help` kommando.</span><span class="sxs-lookup"><span data-stu-id="160ee-221">To update or save help for a module that is not returned by the **ListAvailable** parameter of the `Get-Module` cmdlet, import the module into the current session before running an `Update-Help` or `Save-Help` command.</span></span> <span data-ttu-id="160ee-222">`Save-Help`Importera modulen till den aktuella sessionen eller `Invoke-Command` skript blocket som är anslutet till fjärrdatorn innan du kör kommandot på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="160ee-222">On a remote computer, before running the `Save-Help` command, import the module into the current Session, or `Invoke-Command` script block, that is connected to the remote computer.</span></span>

<span data-ttu-id="160ee-223">När modulen är i den aktuella sessionen kör du `Update-Help` `Save-Help` cmdletarna eller utan parametrar eller använder parametern **module** för att ange modulnamnet.</span><span class="sxs-lookup"><span data-stu-id="160ee-223">When the module is in the current session, run the `Update-Help` or `Save-Help` cmdlets without parameters, or use the **Module** parameter to specify the module name.</span></span>

<span data-ttu-id="160ee-224">**Modul** parametrarna för `Update-Help` `Save-Help` cmdletarna och accepterar bara ett modulnamn.</span><span class="sxs-lookup"><span data-stu-id="160ee-224">The **Module** parameters of the `Update-Help` and `Save-Help` cmdlets accept only a module name.</span></span> <span data-ttu-id="160ee-225">De accepterar inte sökvägen till en modul-fil.</span><span class="sxs-lookup"><span data-stu-id="160ee-225">They do not accept the path to a module file.</span></span>

<span data-ttu-id="160ee-226">Använd den här metoden för att uppdatera eller spara hjälp för en modul som inte returneras av **ListAvailable** -parametern för `Get-Module` cmdleten, till exempel en modul som är installerad på en plats som inte finns med i `$env:PSModulePath` miljövariabeln, eller en modul som inte är korrekt formaterad (modulens katalog innehåller inte minst en fil vars basename är samma som katalog namnet).</span><span class="sxs-lookup"><span data-stu-id="160ee-226">Use this technique to update or save help for any module that is not returned by the **ListAvailable** parameter of the `Get-Module` cmdlet, such as a module that is installed in a location that is not listed in the `$env:PSModulePath` environment variable, or a module that is not well-formed (the module directory does not contain at least one file whose basename is the same as the directory name).</span></span>

## <a name="how-to-support-updatable-help"></a><span data-ttu-id="160ee-227">Så här stöder du uppdaterings bar hjälp</span><span class="sxs-lookup"><span data-stu-id="160ee-227">How to support updatable help</span></span>

<span data-ttu-id="160ee-228">Om du skapar en modul kan du använda onlinehjälp och uppdaterings bar hjälp för dina moduler.</span><span class="sxs-lookup"><span data-stu-id="160ee-228">If you author a module, you can support online help and Updatable Help for your modules.</span></span> <span data-ttu-id="160ee-229">Mer information finns i [support uppdaterings bar hjälp](/powershell/scripting/developer/help/supporting-updatable-help) och [support online](/powershell/scripting/developer/module/supporting-online-help) i Microsoft docs.</span><span class="sxs-lookup"><span data-stu-id="160ee-229">For more information, see [Supporting Updatable Help](/powershell/scripting/developer/help/supporting-updatable-help) and [Supporting Online Help](/powershell/scripting/developer/module/supporting-online-help) in the Microsoft Docs.</span></span>

<span data-ttu-id="160ee-230">Uppdaterings bar hjälp är inte tillgänglig för PowerShell-snapin-moduler eller kommenterings-baserad hjälp.</span><span class="sxs-lookup"><span data-stu-id="160ee-230">Updatable help not available for PowerShell snap-ins or comment-based help.</span></span>

## <a name="remarks"></a><span data-ttu-id="160ee-231">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="160ee-231">Remarks</span></span>

<span data-ttu-id="160ee-232">`Update-Help` `Save-Help` Cmdletarna och stöds inte på Windows Preinstallation Environment (Windows PE).</span><span class="sxs-lookup"><span data-stu-id="160ee-232">The `Update-Help` and `Save-Help` cmdlets are not supported on Windows Preinstallation Environment (Windows PE).</span></span>

## <a name="see-also"></a><span data-ttu-id="160ee-233">Se även</span><span class="sxs-lookup"><span data-stu-id="160ee-233">See also</span></span>

[<span data-ttu-id="160ee-234">Get – hjälp</span><span class="sxs-lookup"><span data-stu-id="160ee-234">Get-Help</span></span>](xref:Microsoft.PowerShell.Core.Get-Help)

[<span data-ttu-id="160ee-235">Spara – hjälp</span><span class="sxs-lookup"><span data-stu-id="160ee-235">Save-Help</span></span>](xref:Microsoft.PowerShell.Core.Save-Help)

[<span data-ttu-id="160ee-236">Uppdatera – hjälp</span><span class="sxs-lookup"><span data-stu-id="160ee-236">Update-Help</span></span>](xref:Microsoft.PowerShell.Core.Update-Help)
