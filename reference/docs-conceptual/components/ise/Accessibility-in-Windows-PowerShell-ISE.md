---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Hjälpmedelsfunktioner i Windows PowerShell ISE
ms.assetid: a078f9d1-dd6b-4323-b16d-0622cd993aa8
ms.openlocfilehash: 78a001dbe43a0b005d10a817e05e4cc7a72f5bd0
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404930"
---
# <a name="accessibility-in-windows-powershell-ise"></a>Hjälpmedelsfunktioner i Windows PowerShell ISE

Det här avsnittet beskriver hjälpmedelsfunktionerna i Windows PowerShell Integrated Scripting Environment (ISE) som kan vara användbara.

* [Så här ändrar du storlek och plats-konsolen och fönster för skript](#how-to-change-the-size-and-location-of-the-console-and-script-panes)
* [Kortkommandon för att redigera text](#keyboard-shortcuts-for-editing-text)
* [Kortkommandon för att köra skript](#keyboard-shortcuts-for-running-scripts)
* [Kortkommandon för att anpassa vyn](#keyboard-shortcuts-for-customizing-the-view)
* [Kortkommandon för att felsöka skript](#keyboard-shortcuts-for-debugging-scripts)
* [Kortkommandon för Windows PowerShell-flikar](#keyboard-shortcuts-for-windows-powershell-tabs)
* [Kortkommandon för att starta och avslutas](#keyboard-shortcuts-for-starting-and-exiting)

Microsoft arbetar ständigt med att göra sina produkter och tjänster lättare att använda för alla. Följande avsnitt innehåller information om funktioner, produkter och tjänster som gör Windows PowerShell ISE mer tillgängligt för personer med funktionshinder.

Windows PowerShell ISE har stöd för läget för hög kontrast. För synskadade, brytpunktsinformation är tillgänglig via cmdletar för att hantera brytpunkter, till exempel [Get-PSBreakpoint](https://technet.microsoft.com/library/0bf48936-00ab-411c-b5e0-9b10a812a3c6) och [Set-PSBreakpoint](https://technet.microsoft.com/library/6afd5d2c-a285-4796-8607-3cbf49471420). Mer information se ”hur du hanterar brytpunkter' i [hur du felsöka skript i Windows PowerShell ISE](How-to-Debug-Scripts-in-Windows-PowerShell-ISE.md). Utöver hjälpmedelsfunktionerna och verktygen i Microsoft Windows finns följande funktioner för att göra Windows PowerShell ISE mer tillgängligt för personer med funktionshinder:

- Kortkommandon

- Syntax färg tabell och möjligheten att ändra flera andra färginställningar med hjälp av den [$psISE.Options](https://technet.microsoft.com/library/75e2a76f-f3d1-490b-ad5d-e3829946aabb) scripting objekt.

- Ändra text

## <a name="how-to-change-the-size-and-location-of-the-console-and-script-panes"></a>Så här ändrar du storlek och plats-konsolen och fönster för skript

Du kan använda följande steg för att ändra storlek och plats för konsolfönstret och skriptfönstret. När du öppnar Windows PowerShell ISE, ska storlek och plats ändringar du gjort behållas.

### <a name="to-resize-the-script-pane-and-console-pane"></a>Ändra storlek på skriptfönstret och konsolfönstret

1. Håll pekaren över raden delning mellan skriptfönstret och konsolfönstret.

2. När muspekaren ändras till en dubbelriktad pil, drar du kanten om du vill ändra storleken på fönstret.

### <a name="to-move-the-script-pane-and-console-pane"></a>Att flytta skriptfönstret och konsolfönstret

Gör något av följande:

- Om du vill flytta skriptfönstret ovan konsolfönstret trycker du på **CTRL + 1** i verktygsfältet klickar du på den **Visa skript fönstret översta** ikon, eller i den **visa** -menyn klickar du på **visa Skriptet längst upp i fönstret**.

- Om du vill flytta skriptfönstret till höger om konsolfönstret trycker du på **CTRL + 2** i verktygsfältet klickar du på den **Visa skript rutan till höger** ikon, eller i den **visa** -menyn klickar du på **Visa Skriptfönster rätt**.

- För att maximera skriptfönstret, trycker du på **CTRL + 3** i verktygsfältet klickar du på den **Visa skript fönstret maximerat** ikon, eller i den **visa** -menyn klickar du på **Visa skript Fönstret maximerat**.

- Om du vill maximera konsolfönstret och dölja rutan skript på raden i flikarna längst till höger kant klickar du på den **Dölj skriptfönstret** ikonen i den **visa** -menyn, klicka om du vill avmarkera den **visa Skriptfönster** menyalternativ.

- Om du vill visa skriptfönstret när konsolfönstret är maximerat på raden i flikarna längst till höger kant klickar du på den **visa Skriptfönster** ikon, eller i den **visa** -menyn, klickar du på den **Visa skript Fönstret** menyalternativ.

## <a name="keyboard-shortcuts-for-editing-text"></a>Kortkommandon för att redigera text

Du kan använda följande kortkommandon när du redigerar text.

|Åtgärd|Kortkommandon|Använd i|
|----------|----------------------|----------|
|**Kopiera**|CTRL+C|Skriptfönstret, konsolfönstret|
|**Klipp ut**|CTRL + X|Skriptfönstret, konsolfönstret|
|**Hitta i skriptet**|CTRL+F|Skriptfönstret|
|**Sök nästa i skriptet**|F3|Skriptfönstret|
|**Sök föregående i skriptet**|SKIFT + F3|Skriptfönstret|
|**Klistra in**|CTRL+V|Skriptfönstret, konsolfönstret|
|**Gör om**|CTRL + Y|Skriptfönstret, konsolfönstret|
|**Ersätt i skriptet**|CTRL + H|Skriptfönstret|
|**Spara**|CTRL+S|Skriptfönstret|
|**Markera alla**|CTRL+A|Skriptfönstret, konsolfönstret|
|**Ångra**|CTRL + Z|Skriptfönstret, konsolfönstret|

## <a name="keyboard-shortcuts-for-running-scripts"></a>Kortkommandon för att köra skript

Du kan använda följande kortkommandon när du kör skript i skriptfönstret.

|Åtgärd|Kortkommando|
|----------|---------------------|
|**Ny**|CTRL + N|
|**Öppna**|CTRL + O|
|**Kör**|F5|
|**Kör val**|F8|
|**Stoppa körning**|CTRL + BREAK. CTRL + C kan användas när kontexten är entydiga (när det finns ingen text är markerad).|
|**Fliken** (till nästa skript)|CTRL + TABB **Obs:** Fliken till nästa skript fungerar bara när du har en enda PowerShell-flik öppnas eller när du har mer än en PowerShell-flik öppnas, men fokus ligger i skriptfönstret.|
|**Fliken** (till föregående skript)|CTRL + SKIFT + TABB **Obs:** Fliken till föregående skript fungerar när du har bara en PowerShell-flik öppnas, eller om du har mer än en PowerShell-flik öppnas och fokus ligger i skriptfönstret.|

## <a name="keyboard-shortcuts-for-customizing-the-view"></a>Kortkommandon för att anpassa vyn

Du kan använda följande kortkommandon för att anpassa vyn i Windows PowerShell ISE. De är tillgängliga från alla fönster i programmet.

|Åtgärd|Kortkommando|
|----------|---------------------|
|**Gå till konsolfönstret**|CTRL+D|
|**Gå till skriptfönstret**|CTRL + I|
|**Visa skriptfönstret**|CTRL + R|
|**Dölj skriptfönstret**|CTRL + R|
||
|**Flytta skriptfönstret upp**|CTRL+1|
|**Flytta skriptfönstret åt höger**|CTRL+2|
|**Maximera skriptfönstret**|CTRL + 3|
|**Zooma In**|CTRL + PLUSTECKEN|
|**Zooma ut**|CTRL + MINUSTECKEN|

## <a name="keyboard-shortcuts-for-debugging-scripts"></a>Kortkommandon för att felsöka skript

Du kan använda följande kortkommandon när du felsöker skript.

|Åtgärd|Kortkommando|Använd i|
|----------|---------------------|----------|
|**Kör/fortsätta**|F5|När du felsöker ett skript skriptfönstret|
|**Stega in**|F11|När du felsöker ett skript skriptfönstret|
|**Hoppa över**|F10|När du felsöker ett skript skriptfönstret|
|**Stega ut**|SKIFT + F11|När du felsöker ett skript skriptfönstret|
|**Visa anropsstacken**|CTRL + SKIFT + D|När du felsöker ett skript skriptfönstret|
|**Lista brytpunkter**|CTRL + SKIFT + L|När du felsöker ett skript skriptfönstret|
|**Brytpunkt**|F9|När du felsöker ett skript skriptfönstret|
|**Ta bort alla brytpunkter**|CTRL + SKIFT + F9|När du felsöker ett skript skriptfönstret|
|**Stoppa felsökare**|SKIFT + F5|När du felsöker ett skript skriptfönstret|

> [!NOTE]
>
> Du kan också använda kortkommandon som är utformad för Windows PowerShell-konsolen när du felsöker skript i Windows PowerShell ISE. Om du vill använda dessa genvägar, måste du skriver genvägen i konsolfönstret och tryck på RETUR.

|Åtgärd|Kortkommando|Använd i|
|----------|---------------------|----------|
|**Fortsätta**|C|Konsolfönstret när du felsöker ett skript|
|**Stega in**|S|Konsolfönstret när du felsöker ett skript|
|**Hoppa över**|V|Konsolfönstret när du felsöker ett skript|
|**Stega ut**|O|Konsolfönstret när du felsöker ett skript|
|**Upprepa sista kommandot** (för steget på eller hoppa över)|RETUR|Konsolfönstret när du felsöker ett skript|
|**Visa anropsstacken**|K|Konsolfönstret när du felsöker ett skript|
|**Stoppa felsökningen**|FRÅGOR OCH|Konsolfönstret när du felsöker ett skript|
|**Lista över skriptet**|L|Konsolfönstret när du felsöker ett skript|
|**Visa konsolen felsökning kommandon**|H eller?|Konsolfönstret när du felsöker ett skript|

## <a name="keyboard-shortcuts-for-windows-powershell-tabs"></a>Kortkommandon för Windows PowerShell-flikar

Du kan använda följande kortkommandon när du använder Windows PowerShell-flikar.

|Åtgärd|Kortkommando|
|----------|---------------------|
|**Stäng PowerShell-flik**|CTRL + W|
|**Nya PowerShell-flik**|CTRL + T|
|**Föregående PowerShell-flik**|CTRL + SKIFT + TABB. Den här genvägen fungerar bara när det finns inga filer är öppna på alla PowerShell-flik.|
|**Nästa Windows PowerShell-flik**|CTRL + TABB. Den här genvägen fungerar bara när det finns inga filer är öppna på alla PowerShell-flik.|

## <a name="keyboard-shortcuts-for-starting-and-exiting"></a>Kortkommandon för att starta och avslutas

Du kan använda följande kortkommandon för att starta Windows PowerShell-konsolen (PowerShell.exe) eller för att avsluta Windows PowerShell ISE.

|Åtgärd|Kortkommando|
|----------|---------------------|
|**Avsluta**|ALT+F4|
|**Starta PowerShell.exe** (Windows PowerShell-konsolen)|CTRL + SKIFT + P|

## <a name="see-also"></a>Se även

[Introduktion till Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)