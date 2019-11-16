---
ms.date: 09/06/2019
keywords: PowerShell, cmdlet
title: Nyheter i PowerShell 5,0 ISE
ms.openlocfilehash: f687c409a1a4b0e6b872863e9f132f7cf5baff20
ms.sourcegitcommit: a6e54a305fdeb6482321c77da8066d2f991c93e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/15/2019
ms.locfileid: "74117515"
---
# <a name="whats-new-in-the-windows-powershell-50-ise"></a>Vad är nytt i Windows PowerShell 5,0 ISE

I det här avsnittet beskrivs nya och uppdaterade funktioner som har introducerats i versioner av Windows PowerShell ISE (Integrated Scripting Environment).

## <a name="feature-description"></a>Funktionsbeskrivning

Windows PowerShell ISE är ett värd program som gör det möjligt att skriva, köra och testa skript och moduler i en grafisk och intuitiv miljö. Viktiga funktioner som syntax-färgning, TABB-slutförande, visuell fel sökning, Unicode-kompatibilitet och Sammanhangs beroende hjälp ger en omfattande skript upplevelse.

Mer information finns i [Introduktion till Windows PowerShell ISE](../components/ise/Introducing-the-Windows-PowerShell-ISE.md).

I följande tabell visas de nya och ändrade funktionerna i den här versionen av Windows PowerShell ISE i Windows PowerShell.

## <a name="intellisense"></a>Tillhandahåller

> Tillagt i ISE 3,0

IntelliSense är en hjälp funktion för automatisk komplettering som är en del av Windows PowerShell ISE.
IntelliSense visar klicknings bara menyer med potentiellt matchande cmdlets, parametrar, parameter värden, filer eller mappar medan du skriver.

**Vilket värde lägger den här ändringen till?**

Med tillägget av IntelliSense är det lättare att identifiera cmdlets och syntax när du använder Windows PowerShell ISE för att skapa skript. Du kan också använda Windows PowerShell ISE för att lära dig Windows PowerShell medan du skapar nya skript.

**Vad fungerar annorlunda?**

När du skriver cmdlets i Windows PowerShell ISE visas en rullnings bar och klickande meny, så att du kan bläddra och välja lämpliga kommandon.

## <a name="snippets"></a>kodfragment

> Tillagt i ISE 3,0

*Kodfragment* är korta avsnitt med Windows PowerShell-kod som du kan infoga i de skript som du skapar i Windows PowerShell ISE. Windows PowerShell ISE levereras med en standard uppsättning kod avsnitt. Du kan lägga till kodfragment med hjälp av `New-Snippet` cmdlet när du arbetar i Windows PowerShell ISE.

**Vilket värde lägger den här ändringen till?**

Genom att använda kodfragment kan du snabbt sätta samman och skapa skript för att automatisera din miljö.

**Vad fungerar annorlunda?**

Om du vill använda kodfragment i Windows PowerShell 3,0 eller senare klickar du på **Starta kodfragment**på **Redigera** -menyn eller trycker på <kbd>CTRL</kbd>+<kbd>J</kbd>.

## <a name="add-on-tools"></a>Tilläggs verktyg

> Tillagt i PowerShell 3,0

Windows PowerShell ISE stöder nu tilläggs verktyg med hjälp av objekt modellen. Dessa tillägg är Windows Presentation Foundation-kontroller (WPF) som visas som ett lodrätt eller vågrätt fönster i-konsolen. Flera tilläggs verktyg i ett fönster visas som en tabbad kontroll. Du kan också lägga till eller ta bort tilläggs verktyg som produceras av icke-Microsoft-parter. Mer information finns i [syftet med Windows PowerShell ISE skript objekt modell](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md).

**Vilket värde lägger den här ändringen till?**

Med tillägg kan du utöka och anpassa Windows PowerShell ISE med verktyg som lägger till funktioner och förbättrar skript upplevelsen.

**Vad fungerar annorlunda?**

Windows PowerShell ISE 3,0 och senare levereras med **kommando** tillägg. Med **kommandona kommando** tillägg kan du bläddra bland cmdletar och få åtkomst till hjälp om cmdlets sida vid sida med **skript** -och **konsol** Fönstren.

Du hittar ytterligare tillägg med hjälp av kommandot **Öppna tilläggs verktyg webbplats** på menyn **tillägg** .

## <a name="restart-manager-and-auto-save"></a>Starta om hanteraren och Spara automatiskt

> Tillagt i PowerShell 3,0

Windows PowerShell ISE sparar nu automatiskt de öppna skripten var två: e minut, på en annan plats. När Windows PowerShell ISE startar om efter en oväntad krasch eller omstart återställer den skript som var öppna i den senaste sessionen, även om skripten inte sparades.

Om du vill ändra intervallet för automatisk sparande kör du följande kommando i konsol fönstret: `$psise.Options.AutoSaveMinuteInterval`.

**Vilket värde lägger den här ändringen till?**

Nu kan du arbeta inom Windows PowerShell ISE vet att dina öppna skript sparas automatiskt.

**Vad fungerar annorlunda?**

Windows PowerShell ISE 2,0 sparar inte skripten automatiskt.

## <a name="most-recently-used-list"></a>Lista över senast använda

> Tillagt i PowerShell 3,0

Windows PowerShell ISE har nu en lista med senast använda filer för filer. När du öppnar en fil i Windows PowerShell ISE läggs filen till i listan över senast använda på **Arkiv** -menyn.

Om du vill ändra standardvärdet för antal filer i listan senast använda, kör du följande kommando i konsol fönstret: `$psise.Options.MruCount`.

**Vilket värde lägger den här ändringen till?**

Nu kan du använda listan med senast använda listan för att enkelt komma åt dina ofta använda filer.

**Vad fungerar annorlunda?**

Windows PowerShell ISE 2,0 har inte någon lista som du nyligen har använt.

## <a name="console-pane"></a>Konsol fönster

> Tillagt i PowerShell 3,0

De separata kommando-och utdatafönstret som var tillgängliga i den första versionen av Windows PowerShell ISE har kombinerats till ett enda konsol fönster. Konsol fönstret liknar en typisk Windows PowerShell-konsol, men den innehåller följande förbättringar:

- Syntax för inmatnings text (inte text), inklusive XML-syntax
- Tillhandahåller
- Matchning av klammerparentes
- Fel indikation
- Fullständigt Unicode-stöd
- <kbd>F1</kbd> Sammanhangs beroende hjälp
- <kbd>Ctrl</kbd>+<kbd>F1</kbd> kontext känsligt show-Command
- Komplext skript och stöd från höger till vänster
- Stöd för teckensnitt
- Förhindra
- Linje – Välj och blockera – Välj lägen
- Bevarande av typ av innehåll på kommando raden när du trycker på <kbd>nedåtpilen</kbd> för att visa historiken i-konsolen

**Vilket värde lägger den här ändringen till?**

Att lägga till dessa ändringar i konsol fönstret är en skript upplevelse som är mer konsekvent med konsol gränssnittet.

**Vad fungerar annorlunda?**

Windows PowerShell ISE 2,0 har separata kommando-och utmatnings fönster.

## <a name="command-line-switches"></a>Kommando rads växlar

> Tillagt i PowerShell 3,0

Om du startar Windows PowerShell ISE från kommando raden (genom att skriva **powershell_ise. exe**) kan du lägga till följande nya kommando rads växlar.

- `-NoProfile`: startar Windows PowerShell ISE utan att köra `$profile`
- `-Help`: visar ett hjälp fönster
- `-mta`: börjar Windows PowerShell ISE i flertrådadt Apartment-läge. Standard åtgärds läget för Windows PowerShell ISE är ett entrådat Apartment-läge, eller `-sta`.

**Vilket värde lägger den här ändringen till?**

Genom att lägga till dessa kommando rads växlar kan du kontrol lera miljön där Windows PowerShell ISE körs.

**Vad fungerar annorlunda?**

Windows PowerShell ISE 2,0 känner inte igen kommando rads växlarna.

## <a name="new-editor-features"></a>Nya redigerings funktioner

> Tillagt i PowerShell 3,0

Andra Windows PowerShell ISE redigerings funktioner är:

- Syntax för **XML-syntax** – Windows PowerShell ISE nu XML-syntax för färger på samma sätt som i Windows PowerShell-syntaxen.
- **Matchning av klamrar** – Windows PowerShell ISE innehåller matchning och markering av klamrar och kan användas på följande sätt: (om du till exempel använder kommandot **gå till matchning** eller <kbd>CTRL</kbd>+<kbd>]</kbd> hittar du en avslutande klammerparentes, om du har valt en inledande klammerparentes).
- **Dispositionsvy** Skript fönstret stöder disposition, vilket gör det möjligt att dölja eller expandera avsnitt i kod genom att klicka på plus eller minus tecken i vänstermarginalen. Du kan använda klammerparenteser eller taggarna `#region` och `#endregion` för att markera början eller slutet av ett komprimerbart avsnitt. Om du vill visa eller dölja alla regioner trycker du på <kbd>Ctrl</kbd>+<kbd>M</kbd>.
- **Dra och släpp text redigering** – Windows PowerShell ISE stöder nu text redigering med dra och släpp. Du kan välja ett valfritt textblock och dra texten till en annan plats i redigeraren eller till-konsolen för att flytta texten. Om du håller ned <kbd>CTRL</kbd> -tangenten medan du drar den markerade texten, kopieras texten till den nya platsen när du släpper mus knappen. I den här versionen av Windows PowerShell ISE när du drar och släpper filer till Windows PowerShell ISE Windows PowerShell ISE öppnar filen.
- **Fel vid visning av parsningsfel** – parsa fel visas med röda understrykningar. När du hovrar över ett indikerat fel visas det problem som påträffades i koden i knapp beskrivnings texten.
- **Zooma** – zoomnings procenten för konsolens innehåll kan ställas in med hjälp av skjutreglaget Zooma (i det nedre högra hörnet i Windows PowerShell ISE-fönstret) eller genom att ange kommandot `$psise.options.Zoom` i konsol fönstret.
- **RTF-kopiering och Inklistrings** kopiering till urklipp i Windows PowerShell ISE bevarar teckensnitt, storlek och färg information för den ursprungliga markeringen.
- **Block markering** – du kan välja ett textblock genom att hålla ned <kbd>Alt</kbd> -tangenten medan du väljer text i skript fönstret med musen, eller genom att trycka på <kbd>Alt</kbd>+<kbd>Shift</kbd>+<kbd>pilen</kbd>.

**Vilket värde lägger den här ändringen till?**

De ytterligare redigerings funktionerna ger en mer enhetlig och kraftfull redigerings miljö.

**Vad fungerar annorlunda?**

Dessa redigerings förbättringar fanns inte i Windows PowerShell ISE 2,0.

## <a name="new-help-viewer-window"></a>Nytt hjälp visnings fönster

> Tillagt i PowerShell 3,0

Om du trycker på <kbd>F1</kbd> när markören finns i en cmdlet, eller om du har en del av en-cmdlet markerad, öppnas den nya hjälp visningen av Sammanhangs beroende hjälp om den markerade cmdleten. **Om** du vill visa hjälp för Windows PowerShell skriver du `operators` i konsol fönstret och trycker sedan på <kbd>F1</kbd>.

Innan du använder den här funktionen kan du hämta den senaste versionen av hjälp avsnitten för Windows PowerShell från Microsofts webbplats. Den enklaste metoden för att hämta hjälp avsnitten är att köra cmdleten `Update-Help` i konsol fönstret när du kör Windows PowerShell ISE som administratör.

Du kan ändra var <kbd>F1</kbd> -nyckeln söker efter hjälp. På menyn **verktyg**/**alternativ** på fliken **allmänna inställningar** under **andra inställningar**, kan du ange eller avmarkera kryss rutan **Använd lokalt hjälp innehåll i stället för online-innehåll**. När det här alternativet är markerat söker klienten efter cmdlet-hjälpen i den nedladdade hjälpen i mappen moduler. Om kryss rutan är avmarkerad söker klienten efter hjälp online.

**Vilket värde lägger den här ändringen till?**

Sammanhangs beroende hjälp utan att lämna din aktuella cmdlet eller ditt skript är en integrerad inlärnings upplevelse.

**Vad fungerar annorlunda?**

Om <kbd>du</kbd> trycker på F1 i tidigare versioner av Windows PowerShell ISE öppnat hjälp filen på den lokala datorn. I Windows PowerShell ISE 3,0 och senare öppnas ett fönster som innehåller hjälpen för cmdleten som går att söka efter och som kan konfigureras. Den här hjälp versionen är ny för Windows PowerShell ISE 3,0 och uppdaterings bar hjälp är ny för Windows PowerShell 3,0.

## <a name="show-command-cmdlet"></a>Visa-kommando-cmdlet

> Tillagt i PowerShell 3,0

Med `Show-Command` cmdlet kan du skapa eller köra en cmdlet eller funktion genom att fylla i ett grafiskt formulär. I formuläret kan användarna arbeta med Windows PowerShell i en grafisk miljö.
`Show-Command` aktiverar även avancerade skript för att skapa ett snabb Windows PowerShell-baserat GUI.

**Vilket värde lägger den här ändringen till?**

Genom att använda `Show-Command` i dina Windows PowerShell-skript kan du ge användarna en grafisk miljö som de är bekanta med. `Show-Command` kan också hjälpa inledande användare att lära sig Windows PowerShell.

**Vad fungerar annorlunda?**

`Show-Command` är nytt Windows PowerShell ISE 3,0.

## <a name="see-also"></a>Se även

Mer information om hur du använder Windows PowerShell ISE finns i [utforska Windows PowerShell Integrated Scripting Environment](../components/ise/exploring-the-windows-powershell-ise.md).
