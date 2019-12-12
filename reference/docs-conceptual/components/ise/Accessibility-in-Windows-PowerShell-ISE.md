---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Hjälpmedelsfunktioner i Windows PowerShell ISE
ms.openlocfilehash: 416b18dd492ca04d98b5adf9f7f0f88ea495740a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030646"
---
# <a name="accessibility-in-windows-powershell-ise"></a>Hjälpmedelsfunktioner i Windows PowerShell ISE

I det här avsnittet beskrivs hjälpmedels funktionerna i Windows PowerShell ISE (Integrated Scripting Environment) som du kan ha nytta av.

* [Ändra storlek och plats för konsolen och skript Fönstren](#how-to-change-the-size-and-location-of-the-console-and-script-panes)
* [Kortkommandon för att redigera text](#keyboard-shortcuts-for-editing-text)
* [Kortkommandon för skript som körs](#keyboard-shortcuts-for-running-scripts)
* [Kortkommandon för att anpassa vyn](#keyboard-shortcuts-for-customizing-the-view)
* [Kortkommandon för fel sökning av skript](#keyboard-shortcuts-for-debugging-scripts)
* [Kortkommandon för Windows PowerShell-flikar](#keyboard-shortcuts-for-windows-powershell-tabs)
* [Kortkommandon för att starta och avsluta](#keyboard-shortcuts-for-starting-and-exiting)

Microsoft arbetar ständigt med att göra sina produkter och tjänster lättare att använda för alla. Följande avsnitt innehåller information om de funktioner, produkter och tjänster som gör Windows PowerShell ISE mer tillgängligt för personer med funktions nedsättning.

Windows PowerShell ISE stöder hög kontrast läge. För synskadade är Bryt punkts information tillgänglig via cmdletarna för att hantera Bryt punkter, till exempel [Get-PSBreakpoint](https://technet.microsoft.com/library/0bf48936-00ab-411c-b5e0-9b10a812a3c6) och [set-PSBreakpoint](https://technet.microsoft.com/library/6afd5d2c-a285-4796-8607-3cbf49471420). Mer information finns i "så här hanterar du Bryt punkter" i [fel sökning av skript i Windows PowerShell ISE](How-to-Debug-Scripts-in-Windows-PowerShell-ISE.md). Utöver hjälpmedels funktionerna i Microsoft Windows gör följande funktioner Windows PowerShell ISE mer tillgängliga för personer med funktions hinder:

- Kortkommandon

- Syntax färgning-tabellen och möjligheten att ändra flera andra färg inställningar med hjälp av skript kommandot [$psISE. alternativ](https://technet.microsoft.com/library/75e2a76f-f3d1-490b-ad5d-e3829946aabb) .

- Ändra text storlek

## <a name="how-to-change-the-size-and-location-of-the-console-and-script-panes"></a>Ändra storlek och plats för konsolen och skript Fönstren

Du kan använda följande steg för att ändra storlek och plats för konsol fönstret och skript fönstret. När du öppnar Windows PowerShell ISE igen bevaras storleks-och plats ändringar som du har gjort.

### <a name="to-resize-the-script-pane-and-console-pane"></a>Ändra storlek på skript fönstret och konsol fönstret

1. Pausa pekaren på delnings linjen mellan skript fönstret och konsol fönstret.

2. När mus pekaren ändras till en dubbelriktad pil, drar du kant linjen för att ändra fönstrets storlek.

### <a name="to-move-the-script-pane-and-console-pane"></a>Flytta skript fönstret och konsol fönstret

Gör något av följande:

- Om du vill flytta skript fönstret ovanför konsol fönstret trycker du på **CTRL + 1** eller, i verktygsfältet, klicka på ikonen **Visa skript fönstret överst** eller klicka på Visa **skript fönster överst**i menyn **Visa** .

- Om du vill flytta skript fönstret till höger om konsol fönstret trycker du på **CTRL + 2** eller, i verktygsfältet, på höger ikon i fönstret **Visa skript** eller på **Visa** -menyn, klickar du på **Visa skript fönstret**till höger.

- Maximera skript fönstret genom att trycka på **CTRL + 3** eller, i verktygsfältet, klicka på ikonen för att **Visa skript fönstret** , eller på **Visa** -menyn, klicka på **Visa skript fönstret maximerat**.

- Om du vill maximera konsol fönstret och dölja skript fönstret klickar du på ikonen **Dölj skript** fönster på menyn **Visa** på den högra kanten av raden med flikar. Klicka sedan på meny alternativet **Visa skript fönster** .

- Om du vill visa skript fönstret när konsol fönstret är maximerat, klickar du på ikonen **Visa** skript fönstret längst till höger på raden med flikar, eller på menyn **Visa** klickar du på meny alternativet **Visa skript fönster** .

## <a name="keyboard-shortcuts-for-editing-text"></a>Kortkommandon för att redigera text

Du kan använda följande kortkommandon när du redigerar text.

|Åtgärd|Kortkommandon|Använd i|
|----------|----------------------|----------|
|**Copy**|CTRL+C|Skript fönster, konsol fönster|
|**Styckning**|CTRL + X|Skript fönster, konsol fönster|
|**Sök i skript**|CTRL+F|Skript fönster|
|**Sök nästa i skriptet**|F3|Skript fönster|
|**Hitta föregående i skript**|SHIFT + F3|Skript fönster|
|**Inklistringsfel**|CTRL+V|Skript fönster, konsol fönster|
|**Tidigare**|CTRL + Y|Skript fönster, konsol fönster|
|**Ersätt i skript**|CTRL + H|Skript fönster|
|**Spara**|CTRL+S|Skript fönster|
|**Markera alla**|CTRL+A|Skript fönster, konsol fönster|
|**Göra**|CTRL + Z|Skript fönster, konsol fönster|

## <a name="keyboard-shortcuts-for-running-scripts"></a>Kortkommandon för skript som körs

Du kan använda följande kortkommandon när du kör skript i skript fönstret.

|Åtgärd|Kortkommando|
|----------|---------------------|
|**Ny**|CTRL + N|
|**Öppna**|CTRL + O|
|**Kör**|F5|
|**Kör val**|F8|
|**Stoppa körning**|CTRL + BREAK. CTRL + C kan användas när kontexten är oklar (när det inte finns någon text markerad).|
|**TABB** (till nästa skript)|CTRL + TABB- **anteckning:** Tab till nästa skript fungerar bara när du har en enda PowerShell-flik öppen, eller om du har fler än en PowerShell-flik öppen, men fokus är i skript fönstret.|
|**TABB** (till föregående skript)|CTRL + SHIFT + TABB- **anteckning:** TABB till föregående skript fungerar när du bara har en PowerShell-flik öppen, eller om du har fler än en PowerShell-flik öppen och fokus är i skript fönstret.|

## <a name="keyboard-shortcuts-for-customizing-the-view"></a>Kortkommandon för att anpassa vyn

Du kan använda följande kortkommandon för att anpassa vyn i Windows PowerShell ISE. De är tillgängliga från alla rutor i programmet.

|Åtgärd|Kortkommando|
|----------|---------------------|
|**Gå till konsol fönstret**|CTRL+D|
|**Gå till skript fönstret**|CTRL + I|
|**Visa skript fönstret**|CTRL + R|
|**Dölj skript fönstret**|CTRL + R|
||
|**Flytta skript fönstret uppåt**|CTRL+1|
|**Flytta skript fönstret åt höger**|CTRL+2|
|**Maximera skript fönstret**|CTRL+3|
|**Zooma in**|CTRL + PLUS TECKEN|
|**Zooma ut**|CTRL + MINUS TECKEN|

## <a name="keyboard-shortcuts-for-debugging-scripts"></a>Kortkommandon för fel sökning av skript

Du kan använda följande kortkommandon vid fel sökning av skript.

|Åtgärd|Kortkommando|Använd i|
|----------|---------------------|----------|
|**Kör/Fortsätt**|F5|Skript fönstret, vid fel sökning av ett skript|
|**Stega in**|F11|Skript fönstret, vid fel sökning av ett skript|
|**Steg över**|F10|Skript fönstret, vid fel sökning av ett skript|
|**Gå ut**|SHIFT + F11|Skript fönstret, vid fel sökning av ett skript|
|**Visa anrops stack**|CTRL + SHIFT + D|Skript fönstret, vid fel sökning av ett skript|
|**List Bryt punkter**|CTRL + SHIFT + L|Skript fönstret, vid fel sökning av ett skript|
|**Växla Bryt punkt**|F9|Skript fönstret, vid fel sökning av ett skript|
|**Ta bort alla Bryt punkter**|CTRL + SHIFT + F9|Skript fönstret, vid fel sökning av ett skript|
|**Stoppa fel sökning**|SHIFT + F5|Skript fönstret, vid fel sökning av ett skript|

> [!NOTE]
>
> Du kan också använda kortkommandon som är utformade för Windows PowerShell-konsolen när du felsöker skript i Windows PowerShell ISE. Om du vill använda dessa genvägar måste du skriva genvägen i konsol fönstret och trycka på RETUR.

|Åtgärd|Kortkommando|Använd i|
|----------|---------------------|----------|
|**Bestå**|C|Konsol fönster, vid fel sökning av ett skript|
|**Stega in**|S|Konsol fönster, vid fel sökning av ett skript|
|**Steg över**|V|Konsol fönster, vid fel sökning av ett skript|
|**Gå ut**|O|Konsol fönster, vid fel sökning av ett skript|
|**Upprepa det senaste kommandot** (för stega i eller Stega över)|RETUR|Konsol fönster, vid fel sökning av ett skript|
|**Visa anrops stack**|K|Konsol fönster, vid fel sökning av ett skript|
|**Stoppa fel sökning**|Q|Konsol fönster, vid fel sökning av ett skript|
|**Lista skriptet**|L|Konsol fönster, vid fel sökning av ett skript|
|**Visa kommandon för konsol fel sökning**|H eller?|Konsol fönster, vid fel sökning av ett skript|

## <a name="keyboard-shortcuts-for-windows-powershell-tabs"></a>Kortkommandon för Windows PowerShell-flikar

Du kan använda följande kortkommandon när du använder Windows PowerShell-flikar.

|Åtgärd|Kortkommando|
|----------|---------------------|
|**Stäng PowerShell-fliken**|CTRL + W|
|**Ny PowerShell-flik**|CTRL+T|
|**Föregående PowerShell-flik**|CTRL + SHIFT + TABB. Den här genvägen fungerar bara när inga filer är öppna på någon PowerShell-flik.|
|**Nästa Windows PowerShell-flik**|CTRL + TAB. Den här genvägen fungerar bara när inga filer är öppna på någon PowerShell-flik.|

## <a name="keyboard-shortcuts-for-starting-and-exiting"></a>Kortkommandon för att starta och avsluta

Du kan använda följande kortkommandon för att starta Windows PowerShell-konsolen (PowerShell. exe) eller avsluta Windows PowerShell ISE.

|Åtgärd|Kortkommando|
|----------|---------------------|
|**Avsluta**|ALT+F4|
|**Starta PowerShell. exe** (Windows PowerShell-konsol)|CTRL + SHIFT + P|

## <a name="see-also"></a>Se även

[Vi presenterar Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)
