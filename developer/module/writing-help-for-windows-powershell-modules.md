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
# <a name="writing-help-for-windows-powershell-modules"></a>Skrivhjälp för Windows PowerShell-moduler

Windows PowerShell-moduler kan innehålla hjälpavsnitt om modulen och om modulen medlemmarna, till exempel-cmdlet: ar, providers, funktioner och skript. Den `Get-Help` cmdlet visar modulen hjälpavsnitten i samma format som den visar Hjälp för andra Windows PowerShell-objekt och användare använda standard `Get-Help` kommandon för att hämta hjälpavsnitten.

Det här dokumentet beskriver format och korrekt placering av modulen hjälpavsnitt och riktlinjer för modulen hjälpinnehållet förslag.

## <a name="types-of-module-help"></a>Typer av modulen hjälp

En modul kan innehålla följande typer av hjälp.

- **Cmdlet-hjälpavsnitten**. Hjälpavsnitt som beskriver cmdletar i en modul är XML-filer som använder kommandot att schemat

- **Providern hjälp**. Hjälpavsnitt som beskriver leverantörer i en modul är XML-filer som använder providern att schemat.

- **Funktionen hjälp**. Hjälpavsnitt som beskriver funktioner i en modul kan vara XML-filer som använder kommandot att schema eller kommentarbaserad hjälpavsnitt i funktionen, eller skript eller skriptmodul

- **Skriptet hjälp**. Hjälpavsnitt som beskriver skript i en modul kan vara XML-filer som använder kommandot att schema eller kommentarbaserad hjälpavsnitten i skriptet eller skriptmodul.

- **Konceptuell (”information”) hjälp**. Du kan använda en konceptuell (”information”) hjälpavsnitt som beskriver modulen och dess medlemmar och som förklarar hur medlemmarna som kan användas tillsammans för att utföra uppgifter. Konceptuell hjälpavsnitt är textfiler med Unicode (UTF-8) kodning. Filnamnet måste använda den `about_<name>.help.txt` format, till exempel about_MyModule.help.txt. Som standard, Windows PowerShell innehåller över 100 av dessa grundläggande information om att och formateras som i följande exempel.

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

## <a name="placement-of-module-help"></a>Placering av modulen hjälp

Den `Get-Help` cmdleten söker efter modulen hjälpavsnittsfiler i språkspecifika underkataloger i modulkatalogen.

Till exempel visar följande directory strukturdiagram platsen för hjälpavsnitten för modulen SampleModule.

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
> I det här exemplet på  *\<ModulePath >* är en av sökvägarna i den `PSModulePath` miljövariabeln, till exempel $home\Documents\Modules, $pshome\Modules eller en anpassad sökväg som användaren anger.

## <a name="getting-module-help"></a>Få hjälp av modulen

När en användare importerar en modul till en session, importeras hjälpavsnitt för modulen till sessionen tillsammans med modulen. Du kan visa hjälpavsnitt filerna i värdet för nyckeln FileList i modulmanifestet, men hjälpavsnitt påverkas inte av den `Export-ModuleMember` cmdlet.

Du kan ange modulen hjälpavsnitten i olika språk. Den `Get-Help` cmdlet visar automatiskt hjälpavsnitt för modulen på det språk som har angetts för den aktuella användaren i nationella inställningar och språkinställningar på Kontrollpanelen. I Windows Vista och senare versioner av Windows, `Get-Help` sökningar för hjälpavsnitten i språkspecifika underkataloger i modulkatalogen i enlighet med de språk som reserv standarder som upprättats för Windows.

Från och med Windows PowerShell 3.0, som kör en `Get-Help` kommandon för en cmdlet eller funktionen utlöser automatisk import av modulen. Den `Get-Help` cmdlet omedelbart visar innehållet i hjälpavsnitten i modulen.

Om modulen innehåller inte hjälpavsnitt och det finns inga hjälpavsnitt för kommandon i modulen på användarens dator `Get-Help` visar automatiskt genererade hjälp. Den automatisk genererade hjälpen innehåller kommandosyntax, parametrar och typer av inkommande och utgående, men innehåller inte några beskrivningar. Den automatiskt genererade innehåller text som leder användaren till försöker använda den `Update-Help` cmdlet för att ladda ned hjälp för kommandot från Internet eller en filresurs. Den också rekommenderar att du använder den **Online** -parametern för den `Get-Help` cmdlet för att hämta onlineversionen av hjälpavsnittet.

## <a name="supporting-updatable-help"></a>Stöd för uppdateringsbar hjälp

Användare av Windows PowerShell 3.0 och senare versioner av Windows PowerShell kan hämta och installera uppdaterade filer för en modul från Internet eller från en lokal filresurs. Den `Update-Help` och `Save-Help` cmdletar Dölj hanteringsinformation från användaren. Användare som kör den `Update-Help` cmdlet och sedan använda den `Get-Help` cmdlet för att läsa de senaste hjälpfilerna för kommandotolken Windows PowerShell-modulen. Användarna behöver inte starta om Windows eller Windows PowerShell.

Användare bakom brandväggar och de som saknar Internetåtkomst kan använda uppdateringsbar hjälp. Administratörer med Internet åtkomst använder den `Save-Help` cmdlet för att ladda ned och installera de senaste hjälpfilerna till en filresurs. Sedan kan användarna använda den **sökväg** -parametern för den `Update-Help` cmdlet för att hämta de senaste hjälpfilerna från filresursen.

Modulskapare kan inkludera hjälpfiler i modulen och använder uppdateringsbar hjälp för att uppdatera hjälpfiler eller utelämna hjälpfiler från modulen och använda uppdateringsbar hjälp både att installera och uppdatera dem.

Mer information om uppdateringsbar hjälp finns i [stöd för uppdateringsbar hjälp](./supporting-updatable-help.md).

## <a name="supporting-online-help"></a>Stöd för onlinehjälp

Användare som inte kan eller inte installerar uppdaterad hjälp filer på sina datorer förlitar sig ofta på online-versionen av modulen hjälpavsnitt. Den **Online** -parametern för den `Get-Help` cmdlet öppnar onlineversionen av en cmdlet eller en avancerad funktion hjälpavsnittet för användaren i sina standardwebbläsare.

Den `Get-Help` cmdlet använder värdet för den **HelpUri** egenskapen för cmdlet eller funktionen för att hitta onlineversionen av hjälpavsnittet.

Från och med Windows PowerShell 3.0 kan du hjälpa användarna att hitta onlineversionen av cmdlet och funktionen hjälpavsnitt genom att definiera HelpUri-attributet i cmdlet-klassen eller **HelpUri** egenskapen för den **CmdletBinding** attribut. Värdet för attributet är värdet för den **HelpUri** egenskapen för cmdlet eller funktion.

Mer information finns i [stödja onlinehjälp](./supporting-online-help.md).

## <a name="see-also"></a>Se även

[Skriva ett Windows PowerShell-modul](./writing-a-windows-powershell-module.md)

[Stöd för uppdateringsbar hjälp](./supporting-updatable-help.md)

[Stöd för onlinehjälp](./supporting-online-help.md)