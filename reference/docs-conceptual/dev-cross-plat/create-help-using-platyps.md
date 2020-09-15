---
title: Skapa XML-baserad hjälp med PlatyPS
description: Att använda PlatyPS är ett snabbt och effektivt sätt att skapa en XML-baserad hjälp.
ms.date: 07/21/2020
ms.openlocfilehash: 79cf8c077a07bf1e7aa8ea1ea799be5f8d4af12c
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2020
ms.locfileid: "86972623"
---
# <a name="create-xml-based-help-using-platyps"></a>Skapa XML-baserad hjälp med PlatyPS

När du skapar en PowerShell-modul rekommenderar vi alltid att du inkluderar detaljerad hjälp för de cmdlets som du skapar. Om dina cmdletar implementeras i kompilerad kod måste du använda den XML-baserade hjälpen. Detta XML-format kallas MAML (Microsoft Assistance Markup Language).

Den äldre PowerShell SDK-dokumentationen innehåller information om hur du skapar hjälp för PowerShell-cmdlets paketerade i moduler. PowerShell tillhandahåller dock inga verktyg för att skapa den XML-baserade hjälpen. SDK-dokumentationen förklarar strukturen i MAML-hjälpen, men låter dig skapa det komplexa och djupt kapslade, MAML innehållet manuellt.

Det är här som [PlatyPS][] -modulen kan hjälpa dig.

## <a name="what-is-platyps"></a>Vad är PlatyPS?

PlatyPS är ett verktyg med [öppen källkod][platyps-repo] som startas som ett _Hackathon_ -projekt för att skapa och underhålla MAML enklare. PlatyPS dokumenterar syntaxen för parameter uppsättningar och de enskilda parametrarna för varje cmdlet i modulen. PlatyPS skapar strukturerade [markdown][] -filer som innehåller information om syntaxen. Det går inte att skapa beskrivningar eller ange exempel.

PlatyPS skapar plats hållare där du kan fylla i beskrivningar och exempel. När du har lagt till nödvändig information kompilerar PlatyPS markdown-filerna till MAML-filer. PowerShell: s hjälp system tillåter även vanliga hjälp filer för konceptuell text (om ämnen). PlatyPS har en cmdlet för att skapa en strukturerad markdown-mall för en ny _om_ -fil, men dessa filer måste bevaras `about_*.help.txt` manuellt.

Du kan inkludera MAML-och text-hjälpfiler med modulen. Du kan också använda PlatyPS för att kompilera hjälpfilerna till ett CAB-paket som kan vara värd för uppdaterings bara hjälp.

## <a name="get-started-using-platyps"></a>Kom igång med PlatyPS

Först måste du installera PlatyPS från PowerShell-galleriet.

```powershell
Install-Module platyps -Force
Import-Module platyps
```

Följande flödes schema beskriver processen för att skapa eller uppdatera PowerShell-referensens innehåll.

:::image type="content" source="./media/create-help-using-platyps/cmdlet-ref-flow-v2.png" alt-text="Arbets flödet för att skapa XML-baserad hjälp med PlatyPS":::

##  <a name="create-markdown-content-for-a-powershell-module"></a>Skapa markdown-innehåll för en PowerShell-modul

1. Importera din nya modul till sessionen. Upprepa det här steget för varje modul du behöver för att dokumentera.

   Kör följande kommando för att importera dina moduler:

   ```powershell
   Import-Module <your module name>
   ```

1. Använd PlatyPS för att generera markdown-filer för din modul-sida och alla associerade cmdlets i modulen. Upprepa det här steget för varje modul du behöver för att dokumentera.

   ```powershell
   $OutputFolder = <output path>
   $parameters = @{
       Module = <ModuleName>
       OutputFolder = $OutputFolder
       AlphabeticParamsOrder = $true
       WithModulePage = $true
       ExcludeDontShow = $true
       Encoding = 'UTF8BOM'
   }
   New-MarkdownHelp @parameters

   New-MarkdownAboutHelp -OutputFolder $OutputFolder -AboutName "topic_name"
   ```

   Om mappen utdata inte finns `New-MarkdownHelp` skapar den. I det här exemplet `New-MarkdownHelp` skapar en MARKDOWN-fil för varje cmdlet i modulen. Dessutom skapas _sidan modul_ i en fil med namnet `<ModuleName>.md` . Den här modulen innehåller en lista över de cmdletar som finns i modulen och plats hållarna för **sammanfattnings** beskrivningen. Metadata på sidan modul kommer från modulen manifest och används av PlatyPS för att skapa HelpInfo XML-filen (som beskrivs [nedan](#creating-an-updateable-help-package)).

   `New-MarkdownAboutHelp` skapar en ny _om_ -fil med namnet `about_topic_name.md` .

   Mer information finns i [New-MarkdownHelp][] och [New-MarkdownAboutHelp][].

### <a name="update-existing-markdown-content-when-the-module-changes"></a>Uppdatera befintligt markdown-innehåll när modulen ändras

PlatyPS kan också uppdatera befintliga markdown-filer för en modul. Använd det här steget för att uppdatera befintliga moduler som har nya cmdlets, nya parametrar eller parametrar som har ändrats.

1. Importera din nya modul till sessionen. Upprepa det här steget för varje modul du behöver för att dokumentera.

   Kör följande kommando för att importera dina moduler:

   ```powershell
   Import-Module <your module name>
   ```

1. Använd PlatyPS för att uppdatera markdown-filer för modulens landnings sida och alla associerade cmdlets i modulen. Upprepa det här steget för varje modul du behöver för att dokumentera.

   ```powershell
   $parameters = @{
       Path = <folder with Markdown>
       RefreshModulePage = $true
       AlphabeticParamsOrder = $true
       UpdateInputOutput = $true
       ExcludeDontShow = $true
       LogPath = <path to store log file>
       Encoding = 'UTF8BOM'
   }
   Update-MarkdownHelpModule @parameters
   ```

   `Update-MarkdownHelpModule` uppdaterar cmdlet-och modulens markdown-filer i den angivna mappen.
   Filerna uppdateras inte `about_*.md` . Modul filen ( `ModuleName.md` ) tar emot alla nya **sammanfattnings** texter som har lagts till i cmdlet-filerna. Uppdateringar av cmdlet-filer innehåller följande ändring:

   - Nya parameter uppsättningar
   - Nya parametrar
   - Uppdaterade metadata för parameter
   - Uppdaterad information om indata och Utdatatyp

   Mer information finns i [Update-MarkdownHelpModule][].

## <a name="edit-the-new-or-updated-markdown-files"></a>Redigera nya eller uppdaterade markdown-filer

PlatyPS dokumenterar syntaxen för parameter uppsättningarna och de enskilda parametrarna. Det går inte att skapa beskrivningar eller ange exempel. De olika områdena där innehåll behövs finns i klammerparenteser. Exempelvis: `{{ Fill in the Description }}`

:::image type="content" source="./media/create-help-using-platyps/placeholders-example.png" alt-text="Markdown-mall som visar plats hållarna i VS Code":::

Du måste lägga till en sammanfattning, en beskrivning av cmdleten, beskrivningar för varje parameter och minst ett exempel.

Detaljerad information om hur du skriver PowerShell-innehåll finns i följande artiklar:

- [PowerShell-format guide](/powershell/scripting/community/contributing/powershell-style-guide)
- [Redigera referens artiklar](/powershell/scripting/community/contributing/editing-cmdlet-ref)

> [!NOTE]
> PlatyPS har ett särskilt schema som används för cmdlet-referensen. Schemat tillåter endast vissa markdown-block i specifika delar av dokumentet. Om du har placerat innehåll på fel plats Miss lyckas PlatyPS build-steget. Mer information finns i [schema][] dokumentationen i PlatyPS-lagringsplatsen. Ett fullständigt exempel på välformulerad cmdlet-referens finns i [Get-item][].

När du har angett nödvändigt innehåll för var och en av dina cmdletar måste du se till att uppdatera modulens landnings sida. Kontrol lera att modulen har rätt `Module Guid` `Download Help Link` värden och värden i yaml metadata för `<module-name>.md` filen. Lägg till metadata som saknas.

Du kan också märka att vissa cmdlets kan sakna en **Sammanfattning** (_kort beskrivning_). Följande kommando uppdaterar modulens landnings sida med din **sammanfattnings** beskrivnings text. Öppna modulens landnings sida för att kontrol lera beskrivningarna.

```powershell
Update-MarkdownHelpModule –Path <full path output folder> -RefreshModulePage
```

Nu när du har angett allt innehåll kan du skapa MAML-hjälpfiler som visas `Get-Help` i PowerShell-konsolen.

## <a name="create-the-external-help-files"></a>Skapa de externa hjälpfilerna

Det här steget skapar MAML-hjälpfilerna som visas `Get-Help` i PowerShell-konsolen.

Kör följande kommando för att skapa MAML-filerna:

```powershell
New-ExternalHelp –Path <folder with MDs> -OutputPath <output help folder>
```

`New-ExternalHelp` konverterar alla cmdlet markdown-filer till en (eller flera) MAML-filer. Om filer konverteras till oformaterade filer med följande namn format: `about_topic_name.help.txt` .
Markdown-innehållet måste uppfylla kraven för PlatyPS-schemat. `New-ExternalHelp` kommer att avslutas med fel när innehållet inte följer schemat. Du måste redigera filerna för att åtgärda schema felen.

> [!CAUTION]
> PlatyPS gör `about_*.md` att filerna konverteras till oformaterad text med ett dåligt jobb. Du måste använda mycket enkla markdown för att få godtagbara resultat. Du kanske vill underhålla filerna i oformaterat text `about_topic_name.help.txt` format, i stället för att tillåta PlatyPS att konvertera dem.

När det här steget har slutförts visas `*-help.xml` och `about_*.help.txt` filer i målmappen.

Mer information finns i [New-ExternalHelp][]

### <a name="test-the-compiled-help-files"></a>Testa de kompilerade hjälpfilerna

Du kan verifiera innehållet med cmdleten [Get-HelpPreview][] :

```powershell
Get-HelpPreview -Path "<ModuleName>-Help.xml"
```

Cmdlet: en läser den kompilerade MAML-filen och matar ut innehållet i samma format som du skulle ta emot från `Get-Help` . På så sätt kan du granska resultaten för att kontrol lera att markdown-filerna kompileras korrekt och ger önskade resultat. Om du hittar ett fel redigerar du markdown-filerna igen och kompilerar om MAML.

Nu är du redo att publicera dina hjälpfiler.

## <a name="publishing-your-help"></a>Publicera din hjälp

Nu när du har kompilerat markdown-filerna till PowerShell-hjälpfilerna är du redo att göra filerna tillgängliga för användarna. Det finns två alternativ för att tillhandahålla hjälp i PowerShell-konsolen.

- Paketera hjälpfilerna med modulen
- Skapa ett uppdaterings bara hjälp paket som användare installerar med `Update-Help` cmdleten

### <a name="packaging-help-with-the-module"></a>Paketera hjälp med modulen

Hjälpfilerna kan paketeras med modulen. Mer information om mappstrukturen finns i [skriva hjälp för moduler][] . Du bör inkludera listan över hjälpfiler i värdet för nyckeln **filelist** i modulen manifest.

### <a name="creating-an-updateable-help-package"></a>Skapa ett uppdaterings bara hjälp paket

Stegen för att skapa uppdaterings bara hjälp finns på en hög nivå:

1. Hitta en Internet plats som värd för dina hjälpfiler
1. Lägg till en **HelpInfoURI** -nyckel till modulen manifest
1. Skapa en HelpInfo XML-fil
1. Skapa CAB-filer
1. Ladda upp filer

Mer information finns i [stöd för att uppdatera hjälp: steg-för-steg][step-by-step].

PlatyPS hjälper dig med några av de här stegen.

**HelpInfoURI** är en URL som pekar på platsen där dina hjälpfiler finns på Internet. Det här värdet konfigureras i manifestet för modulen. `Update-Help` läser modulens manifest för att hämta den här URL: en och hämta det uppdaterings bara hjälp innehållet. URL: en ska bara peka på mappens plats och inte till enskilda filer. `Update-Help` skapar de fil namn som ska laddas ned baserat på annan information från modulens manifest och XML-filen HelpInfo.

> [!IMPORTANT]
> **HelpInfoURI** måste avslutas med ett snedstreck ( `/` ). Utan det tecknen kan `Update-Help` inte skapa rätt sökvägar för att ladda ned innehållet. De flesta HTTP-baserade fil tjänster är också Skift läges känsliga. Det är viktigt att modulens metadata i XML-filen HelpInfo innehåller rätt bokstavs fall.

`New-ExternalHelp`Cmdleten skapar XML-filen HelpInfo i mappen utdata. XML-filen HelpInfo skapas med YAML-metadata som finns i modulen markdown Files ( `ModuleName.md` ).

`New-ExternalHelpCab`Cmdleten skapar zip-och CAB-filer som innehåller de MAML och `about_*.help.txt` filer som du har kompilerat. CAB-filer är kompatibla med alla versioner av PowerShell.
PowerShell 6 och senare kan använda ZIP-filer.

```powershell
$helpCabParameters = @{
    CabFilesFolder = $MamlOutputFolder
    LandingPagePath = $LandingPage
    OutputFolder = $CabOutputFolder
}
New-ExternalHelpCab @helpCabParameters
```

När du har skapat ZIP-och CAB-filerna laddar du upp ZIP-, CAB-och HelpInfo-XML-filerna till HTTP-filservern. Lägg filerna på den plats som anges i **HelpInfoURI**.

Mer information finns i [New-ExternalHelpCab][].

### <a name="other-publishing-options"></a>Andra publicerings alternativ

Markdown är ett mångsidigt format som är enkelt att transformera till andra format för publicering. Genom att använda ett verktyg som [pandoc][]kan du konvertera dina markdown-hjälpfiler till många olika dokument format, inklusive formaten oformaterad text, HTML, PDF och Office-dokument.

Dessutom kan cmdletarna [ConvertFrom-markdown][] och [show-markdown][] i PowerShell 6 och senare användas för att konvertera markdown till HTML eller skapa en färgad skärm i PowerShell-konsolen.

## <a name="known-issues"></a>Kända problem

PlatyPS är mycket känslig för [schemat][] för strukturen för de markdown-filer som skapas och kompileras. Det är mycket enkelt att skriva giltiga markdown som strider mot schemat. Mer information finns i PowerShell- [stils guiden][] och [Redigera referens artiklar][].

<!-- link references -->
[platyps-repo]: https://github.com/PowerShell/platyps
[PlatyPS]: https://www.powershellgallery.com/packages/platyPS/
[Markdown]: https://commonmark.org
[markdig]: https://github.com/lunet-io/markdig
[schema]: https://github.com/PowerShell/platyPS/blob/master/platyPS.schema.md
[Hämta objekt]: https://github.com/MicrosoftDocs/PowerShell-Docs/blob/staging/reference/7.0/Microsoft.PowerShell.Management/Get-Item.md
[New-MarkdownHelp]: https://github.com/PowerShell/platyPS/blob/master/docs/New-MarkdownHelp.md
[Uppdatera – MarkdownHelpModule]: https://github.com/PowerShell/platyPS/blob/master/docs/Update-MarkdownHelpModule.md
[New-MarkdownAboutHelp]: https://github.com/PowerShell/platyPS/blob/master/docs/New-MarkdownAboutHelp.md
[New-ExternalHelp]: https://github.com/PowerShell/platyPS/blob/master/docs/New-ExternalHelp.md
[Get-HelpPreview]: https://github.com/PowerShell/platyPS/blob/master/docs/Get-HelpPreview.md
[New-ExternalHelpCab]: https://github.com/PowerShell/platyPS/blob/master/docs/New-ExternalHelpCab.md
[PowerShell-format guide]: /powershell/scripting/community/contributing/powershell-style-guide
[Redigera referens artiklar]: /powershell/scripting/community/contributing/editing-cmdlet-ref
[Skriver hjälp för moduler]: /powershell/scripting/developer/help/writing-help-for-windows-powershell-modules
[step-by-step]: /powershell/scripting/developer/help/updatable-help-authoring-step-by-step
[Pandoc]: https://pandoc.org
[ConvertFrom – markdown]: /powershell/module/microsoft.powershell.utility/convertfrom-markdown
[Visa markdown]: /powershell/module/microsoft.powershell.utility/show-markdown
