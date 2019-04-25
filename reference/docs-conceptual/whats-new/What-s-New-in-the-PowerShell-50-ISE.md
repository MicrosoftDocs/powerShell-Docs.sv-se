---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Nyheter i PowerShell 50 ISE
ms.assetid: 38648d47-7c27-4b37-a40e-ad29948519c2
ms.openlocfilehash: 2d953bc4553de7720c590304d29750b84a1ef3b2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058190"
---
# <a name="what39s-new-in-the-windows-powershell-ise"></a>Vad&#39;nytt i Windows PowerShell ISE
Det här avsnittet beskrivs nya och uppdaterade funktioner som har införts i versioner av Windows PowerShell Integrated Scripting Environment (ISE).

## <a name="feature-description"></a>Funktionsbeskrivning
Windows PowerShell ISE är ett program som hjälper dig att skriva, köra och testa skript och moduler i en grafisk och intuitiv miljö. Viktiga funktioner, till exempel syntaxfärgning, fliken slutförande, visual-felsökning, Unicode-efterlevnad och sammanhangsberoende hjälp ger en rik upplevelse för skript.

En översikt över Windows PowerShell ISE, se [översikt över Windows PowerShell Integrated Scripting Environment](https://technet.microsoft.com/library/3c1892c2-bf84-4cb6-af26-1f453be9e671).

## <a name="new-and-changed-functionality-in-windows-powershell-ise"></a>Nya och ändrade funktioner i Windows PowerShell ISE
I följande tabell visas de nya och ändrade funktionerna för den här versionen av Windows PowerShell ISE i Windows PowerShell.

|Funktion/funktionalitet|Windows PowerShell ISE 4.0|Windows PowerShell ISE 3.0|Windows PowerShell ISE 2.0|
|--------------------------|-----------------------------------------------|-----------------------------------------------|-----------------------------------------------|
|**[IntelliSense](#intellisense)**|X|X||
|**[Kodfragment](#snippets)**|X|X||
|**[Tilläggsverktyg](#add-on-tools)**|X|X||
|**[Starta om Manager och spara automatiskt](#restart-manager-and-auto-save)**|X|X||
|**[Lista över senast använda](#most-recently-used-list)**|X|X||
|**[Konsolfönstret](#console-pane)**|X|X||
|**[Kommandoradsväxlar](#command-line-switches)**|X|X||
|**[Nya funktioner i Redigeraren](#new-editor-features)**|X|X||
|**[Nya visningsprogrammet hjälpfönstret](#new-help-viewer-window)**|X|X||
|**[Visa-Command-cmdlet](#show-command-cmdlet)**|X|X||

### <a name="intellisense"></a>IntelliSense
**Har lagts till i ISE 3.0**

IntelliSense är en funktion för automatisk komplettering hjälp som ingår i Windows PowerShell ISE. IntelliSense visar klickbara menyer av potentiellt matchande cmdletar, parametrar, parametervärden, filer eller mappar som du skriver.

**Vilket värde medför den här ändringen?**

Med IntelliSense dessutom är det lättare att upptäcka cmdlet: ar och syntax när du använder Windows PowerShell ISE för att skapa skript. Du kan också använda Windows PowerShell ISE för att lära dig Windows PowerShell när du skapar nya skript.

**Vad fungerar annorlunda?**

När du skriver cmdlets i Windows PowerShell ISE 3.0 eller senare, visas en meny för bläddringsbara och klickbara så att du kan bläddra och väljer sedan lämpliga kommandon.

### <a name="snippets"></a>Kodfragment
**Har lagts till i ISE 3.0**

*Kodfragment* är korta avsnitt av Windows PowerShell-kod som du kan lägga till i de skript som du skapar i Windows PowerShell ISE. Windows PowerShell ISE levereras med en standarduppsättning med kodfragment. Du kan lägga till kodfragment med hjälp av den **New-kodfragment** cmdlet när du arbetar i Windows PowerShell ISE.

**Vilket värde medför den här ändringen?**

Du kan snabbt Assemblera och skapa skript för att automatisera din miljö genom att använda kodfragment.

**Vad fungerar annorlunda?**

Att använda kodfragment i Windows PowerShell 3.0 eller senare måste den **redigera** -menyn klickar du på **starta kodfragment**, eller tryck på **Ctrl-J**.

### <a name="add-on-tools"></a>Tilläggsverktyg
**Har lagts till i PowerShell 3.0**

Windows PowerShell ISE har nu stöd för tilläggsverktyg som är Windows Presentation Foundation (WPF)-kontroller som har lagts till med hjälp av objektmodellen. Tilläggsverktyg kan visas som en lodrät eller vågrät rutan i konsolen. Flera tilläggsverktyg i ett fönster visas som en flikar kontroll. Du kan också lägga till eller ta bort tilläggsverktyg som genereras av Microsoft-anknutna parter. Läs mer om hur du importerar eller ta bort tilläggsverktyg [Windows PowerShell ISE-åtgärder](https://technet.microsoft.com/library/cc732148.aspx).

**Vilket värde medför den här ändringen?**

Tillägg kan du utöka och anpassa Windows PowerShell ISE med verktyg som kan förbättra din upplevelse med skript eller lägga till funktioner i Windows PowerShell ISE.

**Vad fungerar annorlunda?**

Windows PowerShell ISE 3.0 och senare levereras med den **kommandon** tillägg. Den **kommandon** tillägg kan du bläddra cmdletar och få åtkomst till hjälp om de cmdlets sida vid sidan med de **skriptet** och **konsolen** fönster.

Ytterligare tillägg kan hittas genom att använda den **öppen tillägg verktyg webbplats** på den **tillägg** menyn.

### <a name="restart-manager-and-auto-save"></a>Starta om manager och spara automatiskt
**Har lagts till i PowerShell 3.0**

Windows PowerShell ISE nu sparas automatiskt skripten öppna varannan minut, på en annan plats.  Om Windows PowerShell ISE slutar fungera eller om operativsystemet startas när Windows PowerShell ISE har startats om, återställs det öppna skript som har på den senaste sessionen även om skripten inte sparades.

Om du vill ändra intervall för automatisk sparar, kör du följande kommando i konsolfönstret: **$psise. Options.AutoSaveMinuteInterval**.

**Vilket värde medför den här ändringen?**

Nu kan du arbeta i Windows PowerShell ISE att känna till att öppna skripten sparas automatiskt i händelse av en oväntad omstart.

**Vad fungerar annorlunda?**

Windows PowerShell ISE 2.0 sparas inte skripten automatiskt i händelse av en omstart.

### <a name="most-recently-used-list"></a>Lista över senast använda
**Har lagts till i PowerShell 3.0**

Windows PowerShell ISE har nu en senast använda lista för filer. När du öppnar en fil i Windows PowerShell ISE filen läggs till listan över senast använda på den **filen** menyn.

Om du vill ändra standardvärdet för antal filer i listan över senast använda, kör du följande kommando i konsolfönstret: **$psise. Options.MruCount**.

**Vilket värde medför den här ändringen?**

Du kan nu använda listan över senast använda för att enkelt komma åt dina vanliga filer.

**Vad fungerar annorlunda?**

Windows PowerShell ISE 2.0 har inte en senast använda lista.

### <a name="console-pane"></a>Konsolfönstret
**Har lagts till i PowerShell 3.0**

Separata kommandot och utdata-fönster som var tillgängliga i den första versionen av Windows PowerShell ISE har nu kombinerats till en enda konsolfönstret. Konsolfönstret är liknande funktion och utseende i en typisk Windows PowerShell-konsol, men den innehåller följande förbättringar (de flesta är beskrivs i det här avsnittet).

- Syntaxfärgning för indata-text (inte returnerar text), inklusive XML-syntax

- IntelliSense

- Klammerparentes matchar

- Fel-uppgift

- Fullständigt stöd för Unicode

- **F1** sammanhangsberoende hjälp

- **CTRL + F1** sammanhangsberoende visningskommandot

- Komplicerade skriftspråk och stöd för höger-till-vänster

- Stöd för teckensnitt

- Zooma

- Rad-Välj och blockera väljer lägen

- Bevara skrivet innehåll på kommandoraden när du trycker på den **upp** pilen för att visa historik i konsolen

**Vilket värde medför den här ändringen?**

Tillägg av ändringarna konsolfönstret är det skript som är mer konsekvent med gränssnittet konsolen.

**Vad fungerar annorlunda?**

Windows PowerShell ISE 2.0 har separata kommandot och utdata-fönster.

### <a name="command-line-switches"></a>Kommandoradsväxlar
**Har lagts till i PowerShell 3.0**

Om du startar Windows PowerShell ISE från kommandoraden (genom att skriva **powershell_ise.exe**), kan du lägga till följande nya kommandoradsväxlar.

- *-NoProfile*: Startar Windows PowerShell ISE utan att köra **$profile**

- *-Hjälpa*: Visar en Hjälp-fönstret

- *-mta*: Startar Windows PowerShell ISE i flertrådat lägenhetsnummer läge. Standardläget för åtgärden för Windows PowerShell ISE är flertrådade läge eller *- sta*.

**Vilket värde medför den här ändringen?**

Tillägget av dessa kan du kontrollera miljön där Windows PowerShell ISE körs.

**Vad fungerar annorlunda?**

Windows PowerShell ISE 2.0 känner inte dessa kommandoradsväxlar.

### <a name="new-editor-features"></a>Nya funktioner i Redigeraren
**Har lagts till i PowerShell 3.0**

Andra funktioner för redigering av Windows PowerShell ISE är:

- **XML-syntaxfärgning**Windows PowerShell ISE färger nu XML-syntaxen på samma sätt som den färger Windows PowerShell-syntax.

- **Klammerparentes matchar** Windows PowerShell ISE innehåller klammerparentes matchar och markering och kan användas på följande sätt: (till exempel med hjälp av den **går att matcha** kommando eller **Ctrl +]** hittar den klammerparentes, om du har en inledande klammerparentesen valt).

- **Beskriver visa** i skriptfönstret stöder disposition, vilket gör att dölja eller expandera avsnitt med kod genom att klicka på plus eller minus loggar i vänster marginal. Du kan använda klammerparenteser eller **#region** och **#endregion** taggar om du vill markera början eller slutet av ett komprimerbart avsnitt. Om du vill visa eller dölja alla regioner, trycker du på **Ctrl + M**.

- **Dra och släpp textredigering**Windows PowerShell ISE nu har stöd för dra och släpp textredigering. Du kan markera alla textblock och dra texten till en annan plats i redigeraren eller konsolen för att flytta texten. Om du håller ned Ctrl-tangenten medan du drar den markerade texten när du släpper musknappen har texten kopierats till den nya platsen. I den här versionen av Windows PowerShell ISE, samt den tidigare versionen av Windows PowerShell ISE öppnar Windows PowerShell ISE filen när du drar och släpper filer till Windows PowerShell ISE.

- **Parsa fel visas** parsningsfel anges med röd understrykning. När du hovrar över ett angivet fel visar Knappbeskrivningstext problemet som hittades i koden.

- **Zooma** zoomning procentandelen konsolens innehåll kan anges med hjälp av skjutreglaget (i det nedre högra hörnet av Windows PowerShell ISE-fönster) eller genom att ange kommandot **$psise.options.Zoom** i konsolfönstret.

- **Rich text kopiera och klistra in** kopiera till Urklipp i Windows PowerShell ISE bevarar teckensnitt, storlek och färginformation för den ursprungliga markeringen.

- **Blockera val av** du kan välja ett textblock genom att hålla ned ALT-tangenten medan du markerar text i skriptfönstret med musen eller genom att trycka på **Alt + Skift + pil**.

**Vilket värde medför den här ändringen?**

Ytterligare funktioner för redigering ger en mer enhetlig och kraftfulla Kodredigering.

**Vad fungerar annorlunda?**

Dessa förbättringar av redigering fanns inte i Windows PowerShell ISE 2.0.

### <a name="new-help-viewer-window"></a>Nya visningsprogrammet hjälpfönstret
**Har lagts till i PowerShell 3.0**

Om du trycker på **F1** när markören är i en cmdlet, eller du har en del av en cmdlet markerat, nya hjälpprogrammet öppnas sammanhangsberoende hjälp om cmdleten markerade. Visa Windows PowerShell om hjälp, skriva **operatörer** i konsolfönstret och tryck sedan på **F1**.

Innan du använder den här funktionen kan du ladda ned den senaste versionen av Windows PowerShell-hjälpen från Microsofts webbplats. Den enklaste metoden för att ladda ned hjälpavsnitten är att köra den **Update-Help** cmdlet i konsolfönstret när du kör Windows PowerShell ISE som administratör.

Du kan ändra var den **F1** nyckeln ser ut för att få hjälp. I den **verktyg**/**alternativ** menyn på den **allmänna inställningar** fliken, under **andra inställningar**, du kan ange eller ta bort den kryssrutan **använda lokala hjälpinnehållet i stället för onlineinnehåll**. Om du söker klienten efter cmdleten hjälp i hämtade hjälpen finns i modulmappen.  Om kryssrutan är avmarkerad försvinner söker klienten på TechNet-biblioteket för cmdlet-hjälpen.

**Vilket värde medför den här ändringen?**

Sammanhangsberoende hjälp utan att lämna din aktuella cmdlet eller ett skript ger en sömlös inlärningsupplevelse.

**Vad fungerar annorlunda?**

Om du trycker på F1 i tidigare versioner av Windows PowerShell ISE öppnas hjälpfilen på den lokala datorn. I Windows PowerShell ISE 3.0 och senare, öppnas ett fönster som innehåller hjälpen för cmdlet: en som är sökbart och kan konfigureras. Den här hjälpfunktionen är nytt för Windows PowerShell ISE 3.0 och uppdateringsbar hjälp är nytt för Windows PowerShell 3.0.

### <a name="show-command-cmdlet"></a>Visa-Command-cmdlet
**Har lagts till i PowerShell 3.0**

Den **visningskommandot** kan du skapa eller kör en cmdlet eller funktion genom att fylla i en grafisk form. Formuläret kan användarna arbeta med Windows PowerShell i en grafisk miljö. **Visa kommando** också möjliggör avancerade utvecklare att skapa en snabb GUI för Windows PowerShell-baserade av skript.

**Vilket värde medför den här ändringen?**

Med hjälp av **visningskommandot** i din Windows PowerShell-skript, du kan ge användarna grafisk miljö som de är vana. **Visa kommando** kan också inledande användare Läs Windows PowerShell.

**Vad fungerar annorlunda?**

Visa-kommandot är nya Windows PowerShell ISE 3.0.

## <a name="see-also"></a>Se även
Mer information om hur du använder Windows PowerShell ISE i Windows PowerShell finns i följande länkar.

- [Utforska Windows PowerShell Integrated Scripting Environment](../getting-started/fundamental/exploring-the-windows-powershell-ise.md)
- [ISE på TechNet Wiki](https://social.technet.microsoft.com/wiki/search/searchresults.aspx?q=ISE)
- [Skriptcenter](https://technet.microsoft.com/scriptcenter/default)