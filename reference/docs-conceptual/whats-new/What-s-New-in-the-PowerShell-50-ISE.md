---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Vilka s i PowerShell 50 ISE
ms.assetid: 38648d47-7c27-4b37-a40e-ad29948519c2
ms.openlocfilehash: 35b825cfa6ea720d0af3537c5d1b16c5ececb701
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
ms.locfileid: "30953590"
---
# <a name="what39s-new-in-the-windows-powershell-ise"></a>Vad&#39;s nya i Windows PowerShell ISE
Det här avsnittet beskriver nya och uppdaterade funktioner som har införts i versioner av Windows PowerShell Integrated Scripting Environment (ISE).

## <a name="feature-description"></a>Funktionsbeskrivning
Windows PowerShell ISE är ett program som gör att du kan skriva, köra och testa skript och moduler i en grafisk och intuitiv miljö. Viktiga funktioner, till exempel syntax färgläggning fliken slutförande, visual felsökning, Unicode-kompatibilitet och sammanhangsberoende hjälp ger en omfattande scripting upplevelse.

En översikt över Windows PowerShell ISE finns [översikt över Windows PowerShell Integrated Scripting Environment](https://technet.microsoft.com/library/3c1892c2-bf84-4cb6-af26-1f453be9e671).

## <a name="new-and-changed-functionality-in-windows-powershell-ise"></a>Nya och ändrade funktioner i Windows PowerShell ISE
I följande tabell visas de nya och förändrade funktionerna för den här versionen av Windows PowerShell ISE i Windows PowerShell.

|Funktion/funktionalitet|Windows PowerShell ISE 4.0|Windows PowerShell ISE 3.0|Windows PowerShell ISE 2.0|
|--------------------------|-----------------------------------------------|-----------------------------------------------|-----------------------------------------------|
|**[IntelliSense](#intellisense)**|X|X||
|**[Kodavsnitt](#snippets)**|X|X||
|**[Tilläggsverktyg](#add-on-tools)**|X|X||
|**[Starta om Manager och spara automatiskt](#restart-manager-and-auto-save)**|X|X||
|**[Lista över senast använda](#most-recently-used-list)**|X|X||
|**[Konsolfönstret](#console-pane)**|X|X||
|**[Kommandoradsväxlar](#command-line-switches)**|X|X||
|**[Nya funktioner](#new-editor-features)**|X|X||
|**[Nya viewer hjälpfönstret](#new-help-viewer-window)**|X|X||
|**[Visa-Command-cmdlet](#show-command-cmdlet)**|X|X||

### <a name="intellisense"></a>IntelliSense
**Lades till i ISE 3.0**

IntelliSense är en funktion för automatisk komplettering hjälp som ingår i Windows PowerShell ISE. IntelliSense visar klickbara menyer potentiellt matchande cmdlets, parametrar, parametervärden, filer och mappar när du skriver.

**Vilket värde medför den här ändringen?**

Med IntelliSense dessutom är det lättare att upptäcka cmdlet: ar och syntax när du använder Windows PowerShell ISE för att skapa skript. Du kan också använda Windows PowerShell ISE för att lära sig Windows PowerShell när du skapar nya skript.

**Vad fungerar annorlunda?**

När du skriver cmdlets i Windows PowerShell ISE 3.0 eller senare, visas en meny för bläddringsbara och klickbar så att du kan bläddra och väljer sedan lämpliga kommandon.

### <a name="snippets"></a>Kodavsnitt
**Lades till i ISE 3.0**

*Kodavsnitt* är kortare delar av Windows PowerShell-kod som du kan infoga i skript som du skapar i Windows PowerShell ISE. Windows PowerShell ISE levereras med en standarduppsättning kodavsnitt. Du kan lägga till kodavsnitt med hjälp av den **ny fragment** cmdlet när du arbetar i Windows PowerShell ISE.

**Vilket värde medför den här ändringen?**

Genom att använda kodavsnitt kan du snabbt montera och skapa skript för att automatisera din miljö.

**Vad fungerar annorlunda?**

Att använda kodavsnitt i Windows PowerShell 3.0 eller senare, på den **redigera** -menyn klickar du på **starta kodavsnitt**, eller tryck på **Ctrl-J**.

### <a name="add-on-tools"></a>Tilläggsverktyg
**Lades till i PowerShell 3.0**

Windows PowerShell ISE stöder nu tilläggsverktyg som är Windows Presentation Foundation (WPF)-kontroller som lagts till med objektmodellen. Tilläggsverktyg kan visas som en lodrät eller vågrät rutan i konsolen. Flera tilläggsverktyg i en ruta visas som en streckad kontroll. Du kan också lägga till eller ta bort tilläggsverktyg som genereras av Microsoft-anknutna parter. Mer information om hur du importerar eller ta bort tilläggsverktyg finns [Windows PowerShell ISE-åtgärder](http://technet.microsoft.com/library/cc732148.aspx).

**Vilket värde medför den här ändringen?**

Tillägg kan du utöka och anpassa Windows PowerShell ISE med verktyg som kan förbättra upplevelsen skript eller lägga till funktioner till Windows PowerShell ISE.

**Vad fungerar annorlunda?**

Windows PowerShell ISE 3.0 och senare som medföljer den **kommandon** tillägg. Den **kommandon** tillägg kan du bläddra cmdlets och ha åtkomst till hjälp om de cmdlets sida vid sidan med den **skriptet** och **konsolen** fönster.

Ytterligare tillägg kan hittas med hjälp av den **öppna tillägget Verktyg webbplats** på den **tillägg** menyn.

### <a name="restart-manager-and-auto-save"></a>Starta om manager och spara automatiskt
**Lades till i PowerShell 3.0**

Windows PowerShell ISE nu sparas automatiskt öppna skripten varannan minut på en annan plats.  Om Windows PowerShell ISE slutar fungera eller om operativsystemet startas när Windows PowerShell ISE har startat om, återställer öppna skript som har på den senaste sessionen, även om skripten inte sparades.

Om du vill ändra intervall för automatisk sparas, kör du följande kommando i konsolfönstret: **$psise. Options.AutoSaveMinuteInterval**.

**Vilket värde medför den här ändringen?**

Nu kan du arbeta i Windows PowerShell ISE veta att öppna skripten sparas automatiskt vid en oväntad omstart.

**Vad fungerar annorlunda?**

Windows PowerShell ISE 2.0 sparas inte skript automatiskt vid en omstart.

### <a name="most-recently-used-list"></a>Lista över senast använda
**Lades till i PowerShell 3.0**

Windows PowerShell ISE har nu en senast använda lista för filer. När du öppnar en fil i Windows PowerShell ISE filen läggs till i listan över senast använda på den **filen** menyn.

Om du vill ändra hur många filer i listan över senast använda kör du följande kommando i konsolfönstret: **$psise. Options.MruCount**.

**Vilket värde medför den här ändringen?**

Du kan nu använda senast använda listan för att enkelt komma åt dina filer som används ofta.

**Vad fungerar annorlunda?**

Windows PowerShell ISE 2.0 har inte en senast använda lista.

### <a name="console-pane"></a>Konsolfönstret
**Lades till i PowerShell 3.0**

Separata kommandot och utdata fönster som fanns i den första versionen av Windows PowerShell ISE har kombinerats till en enda konsolfönstret. Konsolfönstret är liknande funktion och utseende i en typisk Windows PowerShell-konsol, men den innehåller följande förbättringar (beskrivs i det här avsnittet är mest).

- Syntaxen färgläggning för inkommande text (inte utdatatext), inklusive XML-syntax

- IntelliSense

- Klammerparentes matchar

- Fel-uppgift

- Fullständigt stöd för Unicode

- **F1** sammanhangsberoende hjälp

- **CTRL + F1** sammanhangsberoende visa-kommando

- Komplexa skript och höger-till-vänster-support

- Stöd för teckensnitt

- Zooma

- Välj rad och blockera väljer lägen

- Bevarande av typifierat innehåll på kommandoraden när du trycker på den **in** pilen för att visa historik i konsolen

**Vilket värde medför den här ändringen?**

Tillägg av ändringarna konsolfönstret tillhandahåller en skript som är mer konsekvent med konsolen gränssnitt.

**Vad fungerar annorlunda?**

Windows PowerShell ISE 2.0 har separata kommandot och utdata fönster.

### <a name="command-line-switches"></a>Kommandoradsväxlar
**Lades till i PowerShell 3.0**

Om du startar Windows PowerShell ISE från kommandoraden (genom att skriva **powershell_ise.exe**), kan du lägga till följande nya kommandoradsväxlar.

- *-NoProfile*: startar Windows PowerShell ISE utan att köra **$profile**

- *-Hjälp*: Visar en Hjälp-fönstret

- *mta -*: startar Windows PowerShell ISE i flertrådade apartment-läge. Åtgärden standardläget för Windows PowerShell ISE är enkeltrådad inneslutning läge eller *- sta*.

**Vilket värde medför den här ändringen?**

För att lägga till dessa kommandoradsväxlar kan du kontrollera miljön där Windows PowerShell ISE körs.

**Vad fungerar annorlunda?**

Windows PowerShell ISE 2.0 kan inte identifiera dessa kommandoradsväxlar.

### <a name="new-editor-features"></a>Nya funktioner
**Lades till i PowerShell 3.0**

Andra Windows PowerShell ISE redigera funktioner omfattar:

- **XML-syntax färgläggning**Windows PowerShell ISE färger nu XML-syntaxen på samma sätt som den färger Windows PowerShell-syntax.

- **Klammerparentes matchar** Windows PowerShell ISE innehåller matchande klammerparentes och markering och kan användas på följande sätt: (till exempel med hjälp av den **går du till matchar** kommando eller **Ctrl +]** hittar den klammerparentes, om du har en inledande klammerparentesen markerat).

- **Visa disposition** i Skriptfönster stöder disposition, vilket gör att dölja eller expandera kodavsnitt genom att klicka på plus eller minus loggar i vänster marginal. Du kan använda klammerparenteser eller **#region** och **#endregion** taggar om du vill markera början eller slutet av ett avsnitt ska döljas. Om du vill visa eller Dölj alla regioner, trycker du på **Ctrl + M**.

- **Dra och släpp textredigering**Windows PowerShell ISE nu stöder dra och släpp textredigering. Du kan markera alla textblock och dra texten till en annan plats i redigeraren eller konsolen för att flytta texten. Om du håller ned Ctrl-tangenten medan du drar den markerade texten när du släpper musknappen kopieras texten till den nya platsen. I den här versionen av Windows PowerShell ISE som den tidigare versionen av Windows PowerShell ISE, när du drar och släpper filer till Windows PowerShell ISE öppnar Windows PowerShell ISE filen.

- **Parsa fel visas** Parse fel anges med röd understrykning. När du hovrar över ett angivet fel visar knappbeskrivning problemet som hittades i koden.

- **Zooma** zoom-procenttal i konsolen '™ s innehåll kan anges med hjälp av skjutreglaget (i det nedre högra hörnet i fönstret Windows PowerShell ISE) eller genom att ange kommandot **$psise.options.Zoom** i konsolfönstret.

- **Omfattande text kopiera och klistra in** kopiera till Urklipp i Windows PowerShell ISE bevarar teckensnitt, storlek och färginformation för den ursprungliga markeringen.

- **Blockera markeringen** du kan välja ett textblock genom att hålla ned ALT-tangenten medan du markerar text i skriptfönstret med musen eller genom att trycka på **Alt + Skift + pil**.

**Vilket värde medför den här ändringen?**

Redigera funktioner ger en mer enhetlig och kraftfull redigeringsmiljö.

**Vad fungerar annorlunda?**

Det gick inte dessa redigera förbättringar i Windows PowerShell ISE 2.0.

### <a name="new-help-viewer-window"></a>Nya viewer hjälpfönstret
**Lades till i PowerShell 3.0**

Om du trycker på **F1** när markören är i en cmdlet eller du har en del av en cmdlet markerat, nya hjälpprogrammet öppnas sammanhangsberoende hjälp om cmdlet markerade. För att visa Windows PowerShell om hjälp, Skriv **operatörer** i konsolfönstret och tryck sedan på **F1**.

Innan du använder den här funktionen kan du hämta den senaste versionen av Windows PowerShell-hjälpen från Microsofts webbplats. Den enklaste metoden för att ladda ned hjälpavsnitten är att köra den **Update-Help** cmdlet i konsolfönstret när du kör Windows PowerShell ISE som administratör.

Du kan ändra var den **F1** nyckel söker efter hjälp. I den **verktyg**/**alternativ** menyn klickar du på den **allmänna inställningar** fliken, under **andra inställningar**, du kan ange eller ta bort den kryssrutan **använda lokala hjälpinnehållet i stället för onlineinnehåll**. Om alternativet är markerat söker klienten efter cmdlet hjälp i hämtade hjälpen finns i modulmappen.  Om kryssrutan är avmarkerad söker klienten på TechNet-biblioteket för cmdlet-hjälpen.

**Vilket värde medför den här ändringen?**

Sammanhangsberoende hjälp utan att lämna din aktuella cmdlet eller ett skript ger en sömlös learning-upplevelse.

**Vad fungerar annorlunda?**

Om du trycker på F1 i tidigare versioner av Windows PowerShell ISE öppnas hjälpfilen på den lokala datorn. I Windows PowerShell ISE 3.0 och senare, öppnas ett fönster som innehåller hjälpen för cmdleten sökbara och konfigureras. Denna hjälpupplevelse är ny för Windows PowerShell ISE 3.0 och uppdateringsbar hjälp är nya för Windows PowerShell 3.0.

### <a name="show-command-cmdlet"></a>Visa-Command-cmdlet
**Lades till i PowerShell 3.0**

Den **Visa kommandot** kan du skapa eller köra en cmdlet eller funktion genom att fylla i en grafisk form. Formuläret kan användarna arbeta med Windows PowerShell i en grafisk miljö. **Visa kommando** även möjliggör avancerade utvecklare av skript att skapa en snabb GUI för Windows PowerShell-baserade.

**Vilket värde medför den här ändringen?**

Med hjälp av **Visa kommandot** i Windows PowerShell-skript kan du förse användarna med grafisk miljö som de är bekanta. **Visa kommando** kan också inledande användare Läs Windows PowerShell.

**Vad fungerar annorlunda?**

Visa-kommandot är nytt Windows PowerShell ISE 3.0.

## <a name="see-also"></a>Se även
Mer information om hur du använder Windows PowerShell ISE i Windows PowerShell finns i följande länkar.

- [Utforska Windows PowerShell Integrated Scripting Environment](../getting-started/fundamental/exploring-the-windows-powershell-ise.md)
- [ISE på TechNet Wiki](http://social.technet.microsoft.com/wiki/search/searchresults.aspx?q=ISE)
- [Script Center](http://technet.microsoft.com/scriptcenter/default)