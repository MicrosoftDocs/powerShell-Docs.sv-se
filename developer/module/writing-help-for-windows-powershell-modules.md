---
title: Skrivhjälp för Windows PowerShell-moduler | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b58fa5-01bc-426c-a043-5c700d6578e9
caps.latest.revision: 16
ms.openlocfilehash: 443bf5f693d2ab161668de25a1097347826cb5c2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845460"
---
# <a name="writing-help-for-windows-powershell-modules"></a><span data-ttu-id="47f26-102">Skrivhjälp för Windows PowerShell-moduler</span><span class="sxs-lookup"><span data-stu-id="47f26-102">Writing Help for Windows PowerShell Modules</span></span>

<span data-ttu-id="47f26-103">Windows PowerShell-moduler kan innehålla hjälpavsnitt om modulen och om modulen medlemmarna, till exempel-cmdlet: ar, providers, funktioner och skript.</span><span class="sxs-lookup"><span data-stu-id="47f26-103">Windows PowerShell modules can include Help topics about the module and about the module members, such as cmdlets, providers, functions and scripts.</span></span> <span data-ttu-id="47f26-104">Den `Get-Help` cmdlet visar modulen hjälpavsnitten i samma format som den visar Hjälp för andra Windows PowerShell-objekt och användare använda standard `Get-Help` kommandon för att hämta hjälpavsnitten.</span><span class="sxs-lookup"><span data-stu-id="47f26-104">The `Get-Help` cmdlet displays the module Help topics in the same format as it displays Help for other Windows PowerShell items, and users use standard `Get-Help` commands to get the Help topics.</span></span>

<span data-ttu-id="47f26-105">Det här dokumentet beskriver format och korrekt placering av modulen hjälpavsnitt och riktlinjer för modulen hjälpinnehållet förslag.</span><span class="sxs-lookup"><span data-stu-id="47f26-105">This document explains the format and correct placement of module Help topics, and it suggests guidelines for module Help content.</span></span>

## <a name="types-of-module-help"></a><span data-ttu-id="47f26-106">Typer av modulen hjälp</span><span class="sxs-lookup"><span data-stu-id="47f26-106">Types of Module Help</span></span>

<span data-ttu-id="47f26-107">En modul kan innehålla följande typer av hjälp.</span><span class="sxs-lookup"><span data-stu-id="47f26-107">A module can include the following types of Help.</span></span>

- <span data-ttu-id="47f26-108">**Cmdlet-hjälpavsnitten**.</span><span class="sxs-lookup"><span data-stu-id="47f26-108">**Cmdlet Help**.</span></span> <span data-ttu-id="47f26-109">Hjälpavsnitt som beskriver cmdletar i en modul är XML-filer som använder kommandot att schemat</span><span class="sxs-lookup"><span data-stu-id="47f26-109">The Help topics that describe cmdlets in a module are XML files that use the command help schema</span></span>

- <span data-ttu-id="47f26-110">**Providern hjälp**.</span><span class="sxs-lookup"><span data-stu-id="47f26-110">**Provider Help**.</span></span> <span data-ttu-id="47f26-111">Hjälpavsnitt som beskriver leverantörer i en modul är XML-filer som använder providern att schemat.</span><span class="sxs-lookup"><span data-stu-id="47f26-111">The Help topics that describe providers in a module are XML files that use the provider help schema.</span></span>

- <span data-ttu-id="47f26-112">**Funktionen hjälp**.</span><span class="sxs-lookup"><span data-stu-id="47f26-112">**Function Help**.</span></span> <span data-ttu-id="47f26-113">Hjälpavsnitt som beskriver funktioner i en modul kan vara XML-filer som använder kommandot att schema eller kommentarbaserad hjälpavsnitt i funktionen, eller skript eller skriptmodul</span><span class="sxs-lookup"><span data-stu-id="47f26-113">The Help topics that describe functions in a module can be XML files that use the command help schema or comment-based Help topics within the function, or the script or script module</span></span>

- <span data-ttu-id="47f26-114">**Skriptet hjälp**.</span><span class="sxs-lookup"><span data-stu-id="47f26-114">**Script Help**.</span></span> <span data-ttu-id="47f26-115">Hjälpavsnitt som beskriver skript i en modul kan vara XML-filer som använder kommandot att schema eller kommentarbaserad hjälpavsnitten i skriptet eller skriptmodul.</span><span class="sxs-lookup"><span data-stu-id="47f26-115">The Help topics that describe scripts in a module can be XML files that use the command help schema or comment-based Help topics in the script or script module.</span></span>

- <span data-ttu-id="47f26-116">**Konceptuell (”information”) hjälp**.</span><span class="sxs-lookup"><span data-stu-id="47f26-116">**Conceptual ("About") Help**.</span></span> <span data-ttu-id="47f26-117">Du kan använda en konceptuell (”information”) hjälpavsnitt som beskriver modulen och dess medlemmar och som förklarar hur medlemmarna som kan användas tillsammans för att utföra uppgifter.</span><span class="sxs-lookup"><span data-stu-id="47f26-117">You can use a conceptual ("about") Help topic to describe the module and its members and to explain how the members can be used together to perform tasks.</span></span> <span data-ttu-id="47f26-118">Konceptuell hjälpavsnitt är textfiler med Unicode (UTF-8) kodning.</span><span class="sxs-lookup"><span data-stu-id="47f26-118">Conceptual Help topics are text files with Unicode (UTF-8) encoding.</span></span> <span data-ttu-id="47f26-119">Filnamnet måste använda den `about_<name>.help.txt` format, till exempel about_MyModule.help.txt.</span><span class="sxs-lookup"><span data-stu-id="47f26-119">The file name must use the `about_<name>.help.txt` format, such as about_MyModule.help.txt.</span></span> <span data-ttu-id="47f26-120">Som standard, Windows PowerShell innehåller över 100 av dessa grundläggande information om att och formateras som i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="47f26-120">By default, Windows PowerShell includes over 100 of these conceptual About Help topics, and they are formatted like the following example.</span></span>

  ```
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
      Text-only references for further reading. Hyperlinks cannot work in the Windows PowerShell console.

  ```

## <a name="placement-of-module-help"></a><span data-ttu-id="47f26-121">Placering av modulen hjälp</span><span class="sxs-lookup"><span data-stu-id="47f26-121">Placement of Module Help</span></span>

<span data-ttu-id="47f26-122">Den `Get-Help` cmdleten söker efter modulen hjälpavsnittsfiler i språkspecifika underkataloger i modulkatalogen.</span><span class="sxs-lookup"><span data-stu-id="47f26-122">The `Get-Help` cmdlet looks for module Help topic files in language-specific subdirectories of the module directory.</span></span>

<span data-ttu-id="47f26-123">Till exempel visar följande directory strukturdiagram platsen för hjälpavsnitten för modulen SampleModule.</span><span class="sxs-lookup"><span data-stu-id="47f26-123">For example, the following directory structure diagram shows the location of the Help topics for the SampleModule module.</span></span>

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
> <span data-ttu-id="47f26-124">I det här exemplet på  *\<ModulePath >* är en av sökvägarna i den `PSModulePath` miljövariabeln, till exempel $home\Documents\Modules, $pshome\Modules eller en anpassad sökväg som användaren anger.</span><span class="sxs-lookup"><span data-stu-id="47f26-124">In the example, the *\<ModulePath>* placeholder represents one of the paths in the `PSModulePath` environment variable, such as $home\Documents\Modules, $pshome\Modules, or a custom path that the user specifies.</span></span>

## <a name="getting-module-help"></a><span data-ttu-id="47f26-125">Få hjälp av modulen</span><span class="sxs-lookup"><span data-stu-id="47f26-125">Getting Module Help</span></span>

<span data-ttu-id="47f26-126">När en användare importerar en modul till en session, importeras hjälpavsnitt för modulen till sessionen tillsammans med modulen.</span><span class="sxs-lookup"><span data-stu-id="47f26-126">When a user imports a module into a session, the Help topics for that module are imported into the session along with the module.</span></span> <span data-ttu-id="47f26-127">Du kan visa hjälpavsnitt filerna i värdet för nyckeln FileList i modulmanifestet, men hjälpavsnitt påverkas inte av den `Export-ModuleMember` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="47f26-127">You can list the Help topic files in the value of the FileList key in the module manifest, but Help topics are not affected by the `Export-ModuleMember` cmdlet.</span></span>

<span data-ttu-id="47f26-128">Du kan ange modulen hjälpavsnitten i olika språk.</span><span class="sxs-lookup"><span data-stu-id="47f26-128">You can provide module Help topics in different languages.</span></span> <span data-ttu-id="47f26-129">Den `Get-Help` cmdlet visar automatiskt hjälpavsnitt för modulen på det språk som har angetts för den aktuella användaren i nationella inställningar och språkinställningar på Kontrollpanelen.</span><span class="sxs-lookup"><span data-stu-id="47f26-129">The `Get-Help` cmdlet automatically displays module Help topics in the language that is specified for the current user in the Regional and Language Options item in Control Panel.</span></span> <span data-ttu-id="47f26-130">I Windows Vista och senare versioner av Windows, `Get-Help` sökningar för hjälpavsnitten i språkspecifika underkataloger i modulkatalogen i enlighet med de språk som reserv standarder som upprättats för Windows.</span><span class="sxs-lookup"><span data-stu-id="47f26-130">In Windows Vista and later versions of Windows, `Get-Help` searches for the Help topics in language-specific subdirectories of the module directory in accordance with the language fallback standards established for Windows.</span></span>

<span data-ttu-id="47f26-131">Från och med Windows PowerShell 3.0, som kör en `Get-Help` kommandon för en cmdlet eller funktionen utlöser automatisk import av modulen.</span><span class="sxs-lookup"><span data-stu-id="47f26-131">Beginning in Windows PowerShell 3.0, running a `Get-Help` command for a cmdlet or function triggers automatic importing of the module.</span></span> <span data-ttu-id="47f26-132">Den `Get-Help` cmdlet omedelbart visar innehållet i hjälpavsnitten i modulen.</span><span class="sxs-lookup"><span data-stu-id="47f26-132">The `Get-Help` cmdlet immediately displays the contents of the help topics in the module.</span></span>

<span data-ttu-id="47f26-133">Om modulen innehåller inte hjälpavsnitt och det finns inga hjälpavsnitt för kommandon i modulen på användarens dator `Get-Help` visar automatiskt genererade hjälp.</span><span class="sxs-lookup"><span data-stu-id="47f26-133">If the module does not contain help topics and there are no help topics for the commands in the module on the user's computer, `Get-Help` displays auto-generated help.</span></span> <span data-ttu-id="47f26-134">Den automatisk genererade hjälpen innehåller kommandosyntax, parametrar och typer av inkommande och utgående, men innehåller inte några beskrivningar.</span><span class="sxs-lookup"><span data-stu-id="47f26-134">The auto-generated help includes the command syntax, parameters, and input and output types, but does not include any descriptions.</span></span> <span data-ttu-id="47f26-135">Den automatiskt genererade innehåller text som leder användaren till försöker använda den `Update-Help` cmdlet för att ladda ned hjälp för kommandot från Internet eller en filresurs.</span><span class="sxs-lookup"><span data-stu-id="47f26-135">The auto-generated help includes text that directs the user to try to use the `Update-Help` cmdlet to download help for the command from the Internet or a file share.</span></span> <span data-ttu-id="47f26-136">Den också rekommenderar att du använder den **Online** -parametern för den `Get-Help` cmdlet för att hämta onlineversionen av hjälpavsnittet.</span><span class="sxs-lookup"><span data-stu-id="47f26-136">It also recommends using the **Online** parameter of the `Get-Help` cmdlet to get the online version of the help topic.</span></span>

## <a name="supporting-updatable-help"></a><span data-ttu-id="47f26-137">Stöd för uppdateringsbar hjälp</span><span class="sxs-lookup"><span data-stu-id="47f26-137">Supporting Updatable Help</span></span>

<span data-ttu-id="47f26-138">Användare av Windows PowerShell 3.0 och senare versioner av Windows PowerShell kan hämta och installera uppdaterade filer för en modul från Internet eller från en lokal filresurs.</span><span class="sxs-lookup"><span data-stu-id="47f26-138">Users of Windows PowerShell 3.0 and later versions of Windows PowerShell can download and install updated help files for a module from the Internet or from a local file share.</span></span> <span data-ttu-id="47f26-139">Den `Update-Help` och `Save-Help` cmdletar Dölj hanteringsinformation från användaren.</span><span class="sxs-lookup"><span data-stu-id="47f26-139">The `Update-Help` and `Save-Help` cmdlets hide the management details from the user.</span></span> <span data-ttu-id="47f26-140">Användare som kör den `Update-Help` cmdlet och sedan använda den `Get-Help` cmdlet för att läsa de senaste hjälpfilerna för kommandotolken Windows PowerShell-modulen.</span><span class="sxs-lookup"><span data-stu-id="47f26-140">Users run the `Update-Help` cmdlet and then use the `Get-Help` cmdlet to read the newest help files for the module at the Windows PowerShell command prompt.</span></span> <span data-ttu-id="47f26-141">Användarna behöver inte starta om Windows eller Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="47f26-141">Users do not need to restart Windows or Windows PowerShell.</span></span>

<span data-ttu-id="47f26-142">Användare bakom brandväggar och de som saknar Internetåtkomst kan använda uppdateringsbar hjälp.</span><span class="sxs-lookup"><span data-stu-id="47f26-142">Users behind firewalls and those without Internet access can use Updatable Help, as well.</span></span> <span data-ttu-id="47f26-143">Administratörer med Internet åtkomst använder den `Save-Help` cmdlet för att ladda ned och installera de senaste hjälpfilerna till en filresurs.</span><span class="sxs-lookup"><span data-stu-id="47f26-143">Administrators with Internet access use the `Save-Help` cmdlet to download and install the newest help files to a file share.</span></span> <span data-ttu-id="47f26-144">Sedan kan användarna använda den **sökväg** -parametern för den `Update-Help` cmdlet för att hämta de senaste hjälpfilerna från filresursen.</span><span class="sxs-lookup"><span data-stu-id="47f26-144">Then, users use the **Path** parameter of the `Update-Help` cmdlet to get the newest help files from the file share.</span></span>

<span data-ttu-id="47f26-145">Modulskapare kan inkludera hjälpfiler i modulen och använder uppdateringsbar hjälp för att uppdatera hjälpfiler eller utelämna hjälpfiler från modulen och använda uppdateringsbar hjälp både att installera och uppdatera dem.</span><span class="sxs-lookup"><span data-stu-id="47f26-145">Module authors can include help files in the module and use Updatable Help to update the help files, or omit help files from the module and use Updatable Help both to install and to update them.</span></span>

<span data-ttu-id="47f26-146">Mer information om uppdateringsbar hjälp finns i [stöd för uppdateringsbar hjälp](./supporting-updatable-help.md).</span><span class="sxs-lookup"><span data-stu-id="47f26-146">For more information about Updatable Help, see [Supporting Updatable Help](./supporting-updatable-help.md).</span></span>

## <a name="supporting-online-help"></a><span data-ttu-id="47f26-147">Stöd för onlinehjälp</span><span class="sxs-lookup"><span data-stu-id="47f26-147">Supporting Online Help</span></span>

<span data-ttu-id="47f26-148">Användare som inte kan eller inte installerar uppdaterad hjälp filer på sina datorer förlitar sig ofta på online-versionen av modulen hjälpavsnitt.</span><span class="sxs-lookup"><span data-stu-id="47f26-148">Users who cannot or do not install updated help files on their computers often rely on the online version of module help topics.</span></span> <span data-ttu-id="47f26-149">Den **Online** -parametern för den `Get-Help` cmdlet öppnar onlineversionen av en cmdlet eller en avancerad funktion hjälpavsnittet för användaren i sina standardwebbläsare.</span><span class="sxs-lookup"><span data-stu-id="47f26-149">The **Online** parameter of the `Get-Help` cmdlet opens the online version of a cmdlet or advanced function help topic for the user in their default Internet browser.</span></span>

<span data-ttu-id="47f26-150">Den `Get-Help` cmdlet använder värdet för den **HelpUri** egenskapen för cmdlet eller funktionen för att hitta onlineversionen av hjälpavsnittet.</span><span class="sxs-lookup"><span data-stu-id="47f26-150">The `Get-Help` cmdlet uses the value of the **HelpUri** property of the cmdlet or function to find the online version of the help topic.</span></span>

<span data-ttu-id="47f26-151">Från och med Windows PowerShell 3.0 kan du hjälpa användarna att hitta onlineversionen av cmdlet och funktionen hjälpavsnitt genom att definiera HelpUri-attributet i cmdlet-klassen eller **HelpUri** egenskapen för den **CmdletBinding** attribut.</span><span class="sxs-lookup"><span data-stu-id="47f26-151">Beginning in Windows PowerShell 3.0, you can help users find the online version of cmdlet and function help topics by defining the HelpUri attribute on the cmdlet class or the **HelpUri** property of the **CmdletBinding** attribute.</span></span> <span data-ttu-id="47f26-152">Värdet för attributet är värdet för den **HelpUri** egenskapen för cmdlet eller funktion.</span><span class="sxs-lookup"><span data-stu-id="47f26-152">The value of the attribute is the value of the **HelpUri** property of the cmdlet or function.</span></span>

<span data-ttu-id="47f26-153">Mer information finns i [stödja onlinehjälp](./supporting-online-help.md).</span><span class="sxs-lookup"><span data-stu-id="47f26-153">For more information, see [Supporting Online Help](./supporting-online-help.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="47f26-154">Se även</span><span class="sxs-lookup"><span data-stu-id="47f26-154">See Also</span></span>

[<span data-ttu-id="47f26-155">Skriva ett Windows PowerShell-modul</span><span class="sxs-lookup"><span data-stu-id="47f26-155">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)

[<span data-ttu-id="47f26-156">Stöd för uppdateringsbar hjälp</span><span class="sxs-lookup"><span data-stu-id="47f26-156">Supporting Updatable Help</span></span>](./supporting-updatable-help.md)

[<span data-ttu-id="47f26-157">Stöd för onlinehjälp</span><span class="sxs-lookup"><span data-stu-id="47f26-157">Supporting Online Help</span></span>](./supporting-online-help.md)