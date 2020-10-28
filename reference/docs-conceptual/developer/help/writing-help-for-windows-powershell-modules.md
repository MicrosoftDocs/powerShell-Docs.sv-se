---
ms.date: 04/10/2020
ms.topic: reference
title: Skriva hjälp för PowerShell-moduler
description: Skriva hjälp för PowerShell-moduler
ms.openlocfilehash: 3bef45c0dd8a7e63bc419bb3e5a7a1783810105b
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92654660"
---
# <a name="writing-help-for-powershell-modules"></a><span data-ttu-id="1bc08-103">Skriva hjälp för PowerShell-moduler</span><span class="sxs-lookup"><span data-stu-id="1bc08-103">Writing Help for PowerShell Modules</span></span>

<span data-ttu-id="1bc08-104">PowerShell-moduler kan innehålla hjälp avsnitt om modulen och om modul medlemmar, till exempel cmdlets, providrar, funktioner och skript.</span><span class="sxs-lookup"><span data-stu-id="1bc08-104">PowerShell modules can include Help topics about the module and about the module members, such as cmdlets, providers, functions and scripts.</span></span> <span data-ttu-id="1bc08-105">`Get-Help`Cmdleten visar hjälp avsnitten för modulen i samma format som den visar hjälp för andra PowerShell-objekt och användare använder standard `Get-Help` kommandon för att hämta hjälp avsnitten.</span><span class="sxs-lookup"><span data-stu-id="1bc08-105">The `Get-Help` cmdlet displays the module Help topics in the same format as it displays Help for other PowerShell items, and users use standard `Get-Help` commands to get the Help topics.</span></span>

<span data-ttu-id="1bc08-106">I det här dokumentet beskrivs formatet och rätt placering av hjälp avsnitt för moduler, och det föreslår rikt linjer för hjälp innehåll i modulen.</span><span class="sxs-lookup"><span data-stu-id="1bc08-106">This document explains the format and correct placement of module Help topics, and it suggests guidelines for module Help content.</span></span>

## <a name="types-of-module-help"></a><span data-ttu-id="1bc08-107">Typer av modul-hjälp</span><span class="sxs-lookup"><span data-stu-id="1bc08-107">Types of Module Help</span></span>

<span data-ttu-id="1bc08-108">En modul kan innehålla följande typer av hjälp.</span><span class="sxs-lookup"><span data-stu-id="1bc08-108">A module can include the following types of Help.</span></span>

- <span data-ttu-id="1bc08-109">**Cmdlet-hjälp** .</span><span class="sxs-lookup"><span data-stu-id="1bc08-109">**Cmdlet Help** .</span></span> <span data-ttu-id="1bc08-110">Hjälp avsnitten som beskriver cmdlets i en modul är XML-filer som använder kommandot hjälp schema för kommandot</span><span class="sxs-lookup"><span data-stu-id="1bc08-110">The Help topics that describe cmdlets in a module are XML files that use the command help schema</span></span>

- <span data-ttu-id="1bc08-111">**Leverantörs hjälp** .</span><span class="sxs-lookup"><span data-stu-id="1bc08-111">**Provider Help** .</span></span> <span data-ttu-id="1bc08-112">Hjälp avsnitten som beskriver leverantörer i en modul är XML-filer som använder providerns hjälp schema.</span><span class="sxs-lookup"><span data-stu-id="1bc08-112">The Help topics that describe providers in a module are XML files that use the provider help schema.</span></span>

- <span data-ttu-id="1bc08-113">**Funktions hjälp** .</span><span class="sxs-lookup"><span data-stu-id="1bc08-113">**Function Help** .</span></span> <span data-ttu-id="1bc08-114">Hjälp avsnitten som beskriver funktioner i en modul kan vara XML-filer som använder kommandot hjälp schema eller kommentarer baserade hjälp avsnitt i funktionen, skript-eller skript-modulen</span><span class="sxs-lookup"><span data-stu-id="1bc08-114">The Help topics that describe functions in a module can be XML files that use the command help schema or comment-based Help topics within the function, or the script or script module</span></span>

- <span data-ttu-id="1bc08-115">**Skript hjälp** .</span><span class="sxs-lookup"><span data-stu-id="1bc08-115">**Script Help** .</span></span> <span data-ttu-id="1bc08-116">De hjälp avsnitt som beskriver skript i en modul kan vara XML-filer som använder kommandot hjälp schema eller kommentarer baserade hjälp avsnitt i skript-eller skript-modulen.</span><span class="sxs-lookup"><span data-stu-id="1bc08-116">The Help topics that describe scripts in a module can be XML files that use the command help schema or comment-based Help topics in the script or script module.</span></span>

- <span data-ttu-id="1bc08-117">**Konceptuell ("About") hjälp** .</span><span class="sxs-lookup"><span data-stu-id="1bc08-117">**Conceptual ("About") Help** .</span></span> <span data-ttu-id="1bc08-118">Du kan använda ett konceptuellt hjälp avsnitt för att beskriva modulen och dess medlemmar och förklara hur medlemmarna kan användas tillsammans för att utföra uppgifter.</span><span class="sxs-lookup"><span data-stu-id="1bc08-118">You can use a conceptual ("about") Help topic to describe the module and its members and to explain how the members can be used together to perform tasks.</span></span>
  <span data-ttu-id="1bc08-119">Konceptuella hjälp ämnen är textfiler med Unicode-kodning (UTF-8).</span><span class="sxs-lookup"><span data-stu-id="1bc08-119">Conceptual Help topics are text files with Unicode (UTF-8) encoding.</span></span> <span data-ttu-id="1bc08-120">Fil namnet måste använda `about_<name>.help.txt` formatet, till exempel `about_MyModule.help.txt` .</span><span class="sxs-lookup"><span data-stu-id="1bc08-120">The filename must use the `about_<name>.help.txt` format, such as `about_MyModule.help.txt`.</span></span> <span data-ttu-id="1bc08-121">Som standard innehåller PowerShell över 100 av dessa begrepp om hjälp avsnitt och de formateras som i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="1bc08-121">By default, PowerShell includes over 100 of these conceptual About Help topics, and they are formatted like the following example.</span></span>

  ```Output
  TOPIC
      about_<subject or module name>

  SHORT DESCRIPTION
      A short, one-line description of the topic contents.

  LONG DESCRIPTION
      A detailed, full description of the subject or purpose of the module.

  EXAMPLES
      Examples of how to use the module or how the subject feature works in practice.

  KEYWORDS
      Terms or titles on which you might expect your users to search for the information in this topic.

  SEE ALSO
      Text-only references for further reading. Hyperlinks cannot work in the PowerShell console.

  ```

<span data-ttu-id="1bc08-122">Du hittar alla schemafiler i `$PSHOME\Schemas\PSMaml` mappen.</span><span class="sxs-lookup"><span data-stu-id="1bc08-122">All of the schema files can be found in the `$PSHOME\Schemas\PSMaml` folder.</span></span>

## <a name="placement-of-module-help"></a><span data-ttu-id="1bc08-123">Placering av modulens hjälp</span><span class="sxs-lookup"><span data-stu-id="1bc08-123">Placement of Module Help</span></span>

<span data-ttu-id="1bc08-124">`Get-Help`Cmdleten söker efter modulens hjälp ämnes filer i språkspecifika under kataloger i modulens katalog.</span><span class="sxs-lookup"><span data-stu-id="1bc08-124">The `Get-Help` cmdlet looks for module Help topic files in language-specific subdirectories of the module directory.</span></span>

<span data-ttu-id="1bc08-125">Följande katalog struktur diagram visar till exempel platsen för hjälp avsnitten för SampleModule-modulen.</span><span class="sxs-lookup"><span data-stu-id="1bc08-125">For example, the following directory structure diagram shows the location of the Help topics for the SampleModule module.</span></span>

```
<ModulePath>
         \SampleModule
               \<en-US>
                     \about_SampleModule.help.txt
                     \SampleModule.dll-help.xml
                     \SampleNestedModule.dll-help.xml
               \<fr-FR>
                     \about_SampleModule.help.txt
                     \SampleModule.dll-help.xml
                     \SampleNestedModule.dll-help.xml

```

> [!NOTE]
> <span data-ttu-id="1bc08-126">I exemplet `<ModulePath>` representerar plats hållaren en av Sök vägarna i `PSModulePath` miljö variabeln, till exempel `$HOME\Documents\Modules` , `$PSHOME\Modules` eller en anpassad sökväg som användaren anger.</span><span class="sxs-lookup"><span data-stu-id="1bc08-126">In the example, the `<ModulePath>` placeholder represents one of the paths in the `PSModulePath` environment variable, such as `$HOME\Documents\Modules`, `$PSHOME\Modules`, or a custom path that the user specifies.</span></span>

## <a name="getting-module-help"></a><span data-ttu-id="1bc08-127">Hjälp för att hämta modul</span><span class="sxs-lookup"><span data-stu-id="1bc08-127">Getting Module Help</span></span>

<span data-ttu-id="1bc08-128">När en användare importerar en modul till en session, importeras hjälp avsnitten för modulen till sessionen tillsammans med modulen.</span><span class="sxs-lookup"><span data-stu-id="1bc08-128">When a user imports a module into a session, the Help topics for that module are imported into the session along with the module.</span></span> <span data-ttu-id="1bc08-129">Du kan visa hjälp ämnets filer i värdet för nyckeln FileList i modulen manifest, men hjälp ämnen påverkas inte av `Export-ModuleMember` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="1bc08-129">You can list the Help topic files in the value of the FileList key in the module manifest, but Help topics are not affected by the `Export-ModuleMember` cmdlet.</span></span>

<span data-ttu-id="1bc08-130">Du kan tillhandahålla hjälp avsnitt för moduler på olika språk.</span><span class="sxs-lookup"><span data-stu-id="1bc08-130">You can provide module Help topics in different languages.</span></span> <span data-ttu-id="1bc08-131">`Get-Help`Cmdleten visar automatiskt hjälp avsnitt för modulen på det språk som har angetts för den aktuella användaren i objektet nationella inställningar och språk inställningar på kontroll panelen.</span><span class="sxs-lookup"><span data-stu-id="1bc08-131">The `Get-Help` cmdlet automatically displays module Help topics in the language that is specified for the current user in the Regional and Language Options item in Control Panel.</span></span> <span data-ttu-id="1bc08-132">I Windows Vista och senare versioner av Windows kan du `Get-Help` söka efter hjälp avsnitten i språkspecifika under kataloger i modulens katalog i enlighet med de språk reserv standarder som har upprättats för Windows.</span><span class="sxs-lookup"><span data-stu-id="1bc08-132">In Windows Vista and later versions of Windows, `Get-Help` searches for the Help topics in language-specific subdirectories of the module directory in accordance with the language fallback standards established for Windows.</span></span>

<span data-ttu-id="1bc08-133">Från och med PowerShell 3,0 körs ett `Get-Help` kommando för en cmdlet eller funktion som aktiverar automatisk import av modulen.</span><span class="sxs-lookup"><span data-stu-id="1bc08-133">Beginning in PowerShell 3.0, running a `Get-Help` command for a cmdlet or function triggers automatic importing of the module.</span></span> <span data-ttu-id="1bc08-134">`Get-Help`Cmdleten visar omedelbart innehållet i hjälp avsnitten i modulen.</span><span class="sxs-lookup"><span data-stu-id="1bc08-134">The `Get-Help` cmdlet immediately displays the contents of the help topics in the module.</span></span>

<span data-ttu-id="1bc08-135">Om modulen inte innehåller hjälp ämnen och det inte finns några hjälp avsnitt för kommandona i modulen på användarens dator, `Get-Help` visar den automatiskt genererade hjälpen.</span><span class="sxs-lookup"><span data-stu-id="1bc08-135">If the module does not contain help topics and there are no help topics for the commands in the module on the user's computer, `Get-Help` displays auto-generated help.</span></span> <span data-ttu-id="1bc08-136">Den automatiskt genererade hjälpen innehåller kommandosyntaxen, parametrarna och indata-och utdatatyperna, men innehåller inte några beskrivningar.</span><span class="sxs-lookup"><span data-stu-id="1bc08-136">The auto-generated help includes the command syntax, parameters, and input and output types, but does not include any descriptions.</span></span> <span data-ttu-id="1bc08-137">Den automatiskt genererade hjälpen innehåller text som instruerar användaren att försöka använda `Update-Help` cmdleten för att hämta hjälp för kommandot från Internet eller en fil resurs.</span><span class="sxs-lookup"><span data-stu-id="1bc08-137">The auto-generated help includes text that directs the user to try to use the `Update-Help` cmdlet to download help for the command from the internet or a file share.</span></span> <span data-ttu-id="1bc08-138">Det rekommenderar också att du **Online** använder `Get-Help` cmdleten online för att hämta online-versionen av hjälp avsnittet.</span><span class="sxs-lookup"><span data-stu-id="1bc08-138">It also recommends using the **Online** parameter of the `Get-Help` cmdlet to get the online version of the help topic.</span></span>

## <a name="supporting-updatable-help"></a><span data-ttu-id="1bc08-139">Stöd för uppdateringsbar hjälp</span><span class="sxs-lookup"><span data-stu-id="1bc08-139">Supporting Updatable Help</span></span>

<span data-ttu-id="1bc08-140">Användare av PowerShell 3,0 och senare versioner av PowerShell kan ladda ned och installera uppdaterade hjälpfiler för en modul från Internet eller från en lokal fil resurs.</span><span class="sxs-lookup"><span data-stu-id="1bc08-140">Users of PowerShell 3.0 and later versions of PowerShell can download and install updated help files for a module from the internet or from a local file share.</span></span> <span data-ttu-id="1bc08-141">`Update-Help` `Save-Help` Cmdletarna och döljer hanterings detaljerna från användaren.</span><span class="sxs-lookup"><span data-stu-id="1bc08-141">The `Update-Help` and `Save-Help` cmdlets hide the management details from the user.</span></span> <span data-ttu-id="1bc08-142">Användare kör `Update-Help` cmdleten och använder sedan `Get-Help` cmdleten för att läsa de senaste hjälpfilerna för modulen i PowerShell-Kommandotolken.</span><span class="sxs-lookup"><span data-stu-id="1bc08-142">Users run the `Update-Help` cmdlet and then use the `Get-Help` cmdlet to read the newest help files for the module at the PowerShell command prompt.</span></span>
<span data-ttu-id="1bc08-143">Användarna behöver inte starta om Windows eller PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1bc08-143">Users do not need to restart Windows or PowerShell.</span></span>

<span data-ttu-id="1bc08-144">Användare bakom brand väggar och sådana utan Internet åtkomst kan också använda uppdaterings bara hjälp.</span><span class="sxs-lookup"><span data-stu-id="1bc08-144">Users behind firewalls and those without internet access can use Updatable Help, as well.</span></span>
<span data-ttu-id="1bc08-145">Administratörer med Internet åtkomst använder `Save-Help` cmdleten för att hämta och installera de senaste hjälpfilerna till en fil resurs.</span><span class="sxs-lookup"><span data-stu-id="1bc08-145">Administrators with internet access use the `Save-Help` cmdlet to download and install the newest help files to a file share.</span></span> <span data-ttu-id="1bc08-146">Sedan använder användarna **Sök vägs** parametern för `Update-Help` cmdleten för att hämta de senaste hjälpfilerna från fil resursen.</span><span class="sxs-lookup"><span data-stu-id="1bc08-146">Then, users use the **Path** parameter of the `Update-Help` cmdlet to get the newest help files from the file share.</span></span>

<span data-ttu-id="1bc08-147">Module-författare kan inkludera hjälpfiler i modulen och använda uppdaterings bara hjälp för att uppdatera hjälpfilerna eller utelämna hjälpfiler från modulen och använda uppdaterings bara hjälp både för att installera och uppdatera dem.</span><span class="sxs-lookup"><span data-stu-id="1bc08-147">Module authors can include help files in the module and use Updatable Help to update the help files, or omit help files from the module and use Updatable Help both to install and to update them.</span></span>

<span data-ttu-id="1bc08-148">Mer information om uppdaterings bar hjälp finns i [support uppdaterings bara hjälp](./supporting-updatable-help.md).</span><span class="sxs-lookup"><span data-stu-id="1bc08-148">For more information about Updatable Help, see [Supporting Updatable Help](./supporting-updatable-help.md).</span></span>

## <a name="supporting-online-help"></a><span data-ttu-id="1bc08-149">Stöd för onlinehjälp</span><span class="sxs-lookup"><span data-stu-id="1bc08-149">Supporting Online Help</span></span>

<span data-ttu-id="1bc08-150">Användare som inte kan eller inte installerar uppdaterade hjälpfiler på sina datorer förlitar sig ofta på online-versionen av hjälp avsnitten för modulen.</span><span class="sxs-lookup"><span data-stu-id="1bc08-150">Users who cannot or do not install updated help files on their computers often rely on the online version of module help topics.</span></span> <span data-ttu-id="1bc08-151">Cmdleten **online** för `Get-Help` cmdlet: en öppnar online-versionen av en cmdlet eller ett avancerad funktions hjälp avsnitt för användaren i standard webbläsaren.</span><span class="sxs-lookup"><span data-stu-id="1bc08-151">The **Online** parameter of the `Get-Help` cmdlet opens the online version of a cmdlet or advanced function help topic for the user in their default internet browser.</span></span>

<span data-ttu-id="1bc08-152">`Get-Help`Cmdlet: en använder värdet för **HelpUri** -egenskapen för cmdleten eller funktionen för att hitta online-versionen av hjälp avsnittet.</span><span class="sxs-lookup"><span data-stu-id="1bc08-152">The `Get-Help` cmdlet uses the value of the **HelpUri** property of the cmdlet or function to find the online version of the help topic.</span></span>

<span data-ttu-id="1bc08-153">Från och med PowerShell 3,0 kan du hjälpa användarna att hitta online-versionen av cmdlet-och Function-hjälp avsnitten genom att definiera attributet HelpUri i cmdlet-klassen eller egenskapen **HelpUri** för attributet **CmdletBinding** .</span><span class="sxs-lookup"><span data-stu-id="1bc08-153">Beginning in PowerShell 3.0, you can help users find the online version of cmdlet and function help topics by defining the HelpUri attribute on the cmdlet class or the **HelpUri** property of the **CmdletBinding** attribute.</span></span> <span data-ttu-id="1bc08-154">Värdet för attributet är värdet för **HelpUri** -egenskapen för cmdleten eller funktionen.</span><span class="sxs-lookup"><span data-stu-id="1bc08-154">The value of the attribute is the value of the **HelpUri** property of the cmdlet or function.</span></span>

<span data-ttu-id="1bc08-155">Mer information finns i [support online-hjälpen](./supporting-online-help.md).</span><span class="sxs-lookup"><span data-stu-id="1bc08-155">For more information, see [Supporting Online Help](./supporting-online-help.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1bc08-156">Se även</span><span class="sxs-lookup"><span data-stu-id="1bc08-156">See Also</span></span>

[<span data-ttu-id="1bc08-157">Skriva en PowerShell-modul</span><span class="sxs-lookup"><span data-stu-id="1bc08-157">Writing a PowerShell Module</span></span>](../module/writing-a-windows-powershell-module.md)

[<span data-ttu-id="1bc08-158">Stöd för uppdateringsbar hjälp</span><span class="sxs-lookup"><span data-stu-id="1bc08-158">Supporting Updatable Help</span></span>](./supporting-updatable-help.md)

[<span data-ttu-id="1bc08-159">Stöd för onlinehjälp</span><span class="sxs-lookup"><span data-stu-id="1bc08-159">Supporting Online Help</span></span>](./supporting-online-help.md)
