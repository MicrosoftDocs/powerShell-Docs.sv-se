---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: "Hjälpmedelsfunktioner i Windows PowerShell ISE"
ms.assetid: a078f9d1-dd6b-4323-b16d-0622cd993aa8
ms.openlocfilehash: 505ec3aca84b5ad0b9d58a1ec84d80e3aa86db7a
ms.sourcegitcommit: 3720ce4efb6735694cfb53a1b793d949af5d1bc5
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/29/2017
---
# <a name="accessibility-in-windows-powershell-ise"></a>Hjälpmedelsfunktioner i Windows PowerShell ISE
Det här avsnittet beskriver hjälpmedelsfunktionerna i Windows PowerShell Integrated Scripting Environment (ISE) som kan vara användbara.

* [Ändra storlek och plats för konsolen och skript fönster](#how-to-change-the-size-and-location-of-the-console-and-script-panes)
* [Kortkommandon för textredigering](#keyboard-shortcuts-for-editing-text)
* [Kortkommandon för att köra skript](#keyboard-shortcuts-for-running-scripts)
* [Kortkommandon för att anpassa vyn](#keyboard-shortcuts-for-customizing-the-view)
* [Kortkommandon för att felsöka skript](#keyboard-shortcuts-for-debugging-scripts)
* [Kortkommandon för Windows PowerShell-flikar](#keyboard-shortcuts-for-windows-powershell-tabs)
* [Kortkommandon för att starta och avsluta](#keyboard-shortcuts-for-starting-and-exiting)

Microsoft arbetar ständigt med att göra sina produkter och tjänster lättare att använda för alla. Följande avsnitt innehåller information om de funktioner, produkter och tjänster som gör Windows PowerShell ISE mer tillgängligt för personer med funktionshinder.

Windows PowerShell ISE stöder hög kontrast läge. För nedsatt, brytpunktsinformation är tillgänglig via cmdletar för att hantera brytpunkter, t.ex [Get-PSBreakpoint](https://technet.microsoft.com/en-us/library/0bf48936-00ab-411c-b5e0-9b10a812a3c6) och [Set PSBreakpoint](https://technet.microsoft.com/en-us/library/6afd5d2c-a285-4796-8607-3cbf49471420). Mer information finns, hur du hanterar brytpunkter' i [hur du felsöker skript i Windows PowerShell ISE](../core-powershell/ise/How-to-Debug-Scripts-in-Windows-PowerShell-ISE.md). Förutom hjälpmedelsfunktionerna och verktygen i Microsoft Windows kan gör följande funktioner Windows PowerShell ISE mer tillgängligt för personer med funktionshinder:

- Kortkommandon

- Syntaxen färg tabell och möjligheten att ändra flera andra färginställningar med hjälp av den [$psISE.Options](https://technet.microsoft.com/en-us/library/75e2a76f-f3d1-490b-ad5d-e3829946aabb) scripting objekt.

- Storlek ändras

## <a name="how-to-change-the-size-and-location-of-the-console-and-script-panes"></a>Ändra storlek och plats för konsolen och skript fönster
Du kan använda följande steg för att ändra storlek och placering för konsolfönstret och skriptfönstret. När du öppnar Windows PowerShell ISE, kommer storlek och plats ändringarna att sparas.

### <a name="to-resize-the-script-pane-and-console-pane"></a>Ändra storlek på rutan skript och konsolen

1. Placera pekaren på raden dela mellan rutan skript och konsolen.

2. När muspekaren ändras till en dubbelpil, drar du kantlinjen för att ändra storleken på fönstret.

### <a name="to-move-the-script-pane-and-console-pane"></a>Flytta fönstret skript och konsolen
Gör något av följande:

- Om du vill flytta skriptfönstret ovan konsolfönstret, trycker du på **CTRL + 1** i verktygsfältet klickar du på den **Visa skript fönstret översta** ikonen, eller i den **visa** -menyn klickar du på **visa Script fönstret upp**.

- Om du vill flytta skriptfönstret till höger om konsolfönstret, trycker du på **CTRL + 2** i verktygsfältet klickar du på den **Visa skript rutan höger** ikonen, eller i den **visa** -menyn klickar du på **Visa Skriptfönster höger**.

- Om du vill maximera skriptfönstret trycker du på **CTRL + 3** i verktygsfältet klickar du på den **Visa skript fönstret maximerat** ikonen, eller i den **visa** -menyn klickar du på **Visa skript Fönstret maximerat**.

- Om du vill maximera konsolfönstret och dölja rutan skript på raden på flikarna längst till höger kant klickar du på den **dölja Skriptfönster** ikonen i den **visa** -menyn, klicka om du vill avmarkera det **visa Skriptfönster** menyalternativet.

- Om du vill visa rutan skript när konsolfönstret är maximerat på raden på flikarna längst till höger kant klickar du på den **visa Skriptfönster** ikonen, eller i den **visa** -menyn, klickar du på den **Visa skript Fönstret** menyalternativet.

## <a name="keyboard-shortcuts-for-editing-text"></a>Kortkommandon för textredigering
Du kan använda följande kortkommandon när du redigerar text.

|Åtgärd|Kortkommandon|Använd i|
|----------|----------------------|----------|
|**Kopiera**|CTRL+C|Skriptfönster konsolfönstret|
|**Klipp ut**|CTRL + X|Skriptfönster konsolfönstret|
|**Sök i skript**|CTRL+F|Skriptfönster|
|**Sök nästa i skript**|F3|Skriptfönster|
|**Sök föregående i skript**|SKIFT + F3|Skriptfönster|
|**Klistra in**|CTRL+V|Skriptfönster konsolfönstret|
|**Gör om**|CTRL + Y|Skriptfönster konsolfönstret|
|**Ersätt i skript**|CTRL + H|Skriptfönster|
|**Spara**|CTRL+S|Skriptfönster|
|**Markera alla**|CTRL+A|Skriptfönster konsolfönstret|
|**Ångra**|CTRL + Z|Skriptfönster konsolfönstret|

## <a name="keyboard-shortcuts-for-running-scripts"></a>Kortkommandon för att köra skript
Du kan använda följande kortkommandon när du kör skript i skriptfönstret.

|Åtgärd|Kortkommando|
|----------|---------------------|
|**Ny**|CTRL + N|
|**Öppna**|CTRL + O|
|**Kör**|F5|
|**Kör markering**|F8|
|**Stoppa körning**|CTRL + BREAK. CTRL + C kan användas när kontexten är entydigt (när det finns ingen text som valts).|
|**Fliken** (för att nästa skript)|CTRL + TABB **Obs:** att nästa skriptet fungerar endast när du har en PowerShell flik öppna, eller när du har mer än en PowerShell-flik öppen, men fokus ligger i skriptfönstret.|
|**Fliken** (för att tidigare skript)|CTRL + SKIFT + TABB **Obs:** att föregående skriptet fungerar när du har öppnat med endast en PowerShell-fliken, eller om du har mer än en PowerShell-flik öppen och fokus ligger i skriptfönstret.|

## <a name="keyboard-shortcuts-for-customizing-the-view"></a>Kortkommandon för att anpassa vyn
Du kan använda följande kortkommandon för att anpassa vyn i Windows PowerShell ISE. De är tillgängliga från alla fönster i programmet.

|Åtgärd|Kortkommando|
|----------|---------------------|
|**Gå till konsolfönstret**|CTRL + D|
|**Gå till Skriptfönster**|CTRL + K|
|**Visa Skriptfönster**|CTRL + R|
|**Dölj Skriptfönster**|CTRL + R|
||
|**Flytta Skriptfönster upp**|CTRL + 1|
|**Flytta Skriptfönster åt höger**|CTRL + 2|
|**Maximera Skriptfönster**|CTRL + 3|
|**Zooma In**|CTRL + PLUSTECKEN|
|**Zooma ut**|CTRL + MINUSTECKEN|

## <a name="keyboard-shortcuts-for-debugging-scripts"></a>Kortkommandon för att felsöka skript
Du kan använda följande kortkommandon när du felsöker skript.

|Åtgärd|Kortkommando|Använd i|
|----------|---------------------|----------|
|**Kör/fortsätta**|F5|Skriptfönster vid felsökning av ett skript|
|**Gå till**|F11|Skriptfönster vid felsökning av ett skript|
|**Hoppa över**|F10|Skriptfönster vid felsökning av ett skript|
|**Gå ut**|SKIFT + F11|Skriptfönster vid felsökning av ett skript|
|**Visa anropsstacken**|CTRL + SKIFT + D|Skriptfönster vid felsökning av ett skript|
|**Brytpunkter i listan**|CTRL + SKIFT + L|Skriptfönster vid felsökning av ett skript|
|**Brytpunkt**|F9|Skriptfönster vid felsökning av ett skript|
|**Ta bort alla brytpunkter**|CTRL + SKIFT + F9|Skriptfönster vid felsökning av ett skript|
|**Stoppa felsökare**|SKIFT + F5|Skriptfönster vid felsökning av ett skript|

> ![Obs](../core-powershell/web-access/images/Note.jpeg)**Obs!**
>
> Du kan också använda kortkommandon som är utformade för Windows PowerShell-konsolen när du felsöker skript i Windows PowerShell ISE. Om du vill använda dessa kortkommandon måste du ange genvägen i konsolfönstret och tryck på RETUR.

|Åtgärd|Kortkommando|Använd i|
|----------|---------------------|----------|
|**Fortsätt**|C|Konsolfönstret vid felsökning av ett skript|
|**Gå till**|S|Konsolfönstret vid felsökning av ett skript|
|**Hoppa över**|V|Konsolfönstret vid felsökning av ett skript|
|**Gå ut**|O|Konsolfönstret vid felsökning av ett skript|
|**Upprepa senaste kommandot** (för steget till eller hoppa över)|RETUR|Konsolfönstret vid felsökning av ett skript|
|**Visa anropsstacken**|K|Konsolfönstret vid felsökning av ett skript|
|**Stoppa felsökningen**|Q|Konsolfönstret vid felsökning av ett skript|
|**Visa en lista med skriptet**|L|Konsolfönstret vid felsökning av ett skript|
|**Visa konsolen felsökning kommandon**|H eller?|Konsolfönstret vid felsökning av ett skript|

## <a name="keyboard-shortcuts-for-windows-powershell-tabs"></a>Kortkommandon för Windows PowerShell-flikar
Du kan använda följande kortkommandon när du använder Windows PowerShell-flikar.

|Åtgärd|Kortkommando|
|----------|---------------------|
|**Stäng fliken PowerShell**|CTRL + W|
|**Nya PowerShell-fliken**|CTRL + T|
|**Föregående PowerShell flik**|CTRL + SKIFT + TABB. Den här genvägen fungerar endast när inga filer är öppna på någon av flikarna i PowerShell.|
|**Nästa flik för Windows PowerShell**|CTRL + TABB. Den här genvägen fungerar endast när inga filer är öppna på någon av flikarna i PowerShell.|

## <a name="keyboard-shortcuts-for-starting-and-exiting"></a>Kortkommandon för att starta och avsluta
Du kan använda följande kortkommandon om du vill starta Windows PowerShell-konsolen (PowerShell.exe) eller avsluta Windows PowerShell ISE.

|Åtgärd|Kortkommando|
|----------|---------------------|
|**Avsluta**|ALT+F4|
|**Starta PowerShell.exe** (Windows PowerShell-konsol)|CTRL + SKIFT + P|

## <a name="see-also"></a>Se även
- [Med hjälp av Windows PowerShell ISE](../core-powershell/ise/Using-the-Windows-PowerShell-ISE.md)

