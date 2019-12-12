---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Kortkommandon för Windows PowerShell ISE
ms.openlocfilehash: f71aea16f7a98ff7b6427237dc90104e4ea0db71
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030935"
---
# <a name="keyboard-shortcuts-for-the-windows-powershell-ise"></a>Kortkommandon för Windows PowerShell ISE

Använd följande kortkommandon för att utföra åtgärder i Windows PowerShell® ISE (Integrated Scripting Environment). Windows PowerShell ISE är tillgängligt som en del av Windows Server-och Windows-klientens operativ system, men kan även installeras på vissa äldre Windows-operativsystem som en del av [hämtnings paketet för Windows Management Framework 4,0](https://go.microsoft.com/fwlink/?LinkID=293881).

## <a name="keyboard-shortcuts-for-editing-text"></a>Kortkommandon för att redigera text

Du kan använda följande kortkommandon när du redigerar text.

|Åtgärd|Kortkommandon|Använd i|
|----------|----------------------|----------|
|**Hjälp**|F1|Skript fönster **viktigt:** du kan ange att F1-hjälpen kommer från TechNet-biblioteket på webben eller den nedladdade hjälpen (se uppdatering-hjälp). Välj genom att klicka på **verktyg**, **alternativ**, på fliken **allmänna inställningar**, ange eller avmarkera **Använd lokalt hjälp innehåll i stället för online-innehåll.**|
|**Copy**|CTRL+C|Skript fönstret, kommando fönstret, fönstret utdata|
|**Styckning**|CTRL + X|Skript fönster, kommando fönster|
|**Visa eller Dölj disposition**|CTRL+M|Skript fönster|
|**Sök i skript**|CTRL+F|Skript fönster|
|**Sök nästa i skriptet**|F3|Skript fönster|
|**Hitta föregående i skript**|SHIFT + F3|Skript fönster|
|**Hitta en matchande klammerparentes**|CTRL +]|Skript fönster|
|**Inklistringsfel**|CTRL+V|Skript fönster, kommando fönster|
|**Tidigare**|CTRL + Y|Skript fönster, kommando fönster|
|**Ersätt i skript**|CTRL + H|Skript fönster|
|**Spara**|CTRL+S|Skript fönster|
|**Markera alla**|CTRL+A|Skript fönstret, kommando fönstret, fönstret utdata|
|**Visa kodfragment**|CTRL+J|Skript fönster, kommando fönster|
|**Göra**|CTRL + Z|Skript fönster, kommando fönster|

## <a name="keyboard-shortcuts-for-running-scripts"></a>Kortkommandon för skript som körs

Du kan använda följande kortkommandon när du kör skript i skript fönstret.

|Åtgärd|Kortkommando|
|----------|---------------------|
|**Ny**|CTRL + N|
|**Öppna**|CTRL + O|
|**Kör**|F5|
|**Kör val**|F8|
|**Stoppa körning**|CTRL + BREAK. CTRL + C kan användas när kontexten är oklar (när det inte finns någon text markerad).|
|**TABB** (till nästa skript)|CTRL + TABB- **anteckning:** Tab till nästa skript fungerar bara när du har en enda Windows PowerShell-flik öppen, eller när du har fler än en Windows PowerShell-flik öppen, men fokus är i skript fönstret.|
|**TABB** (till föregående skript)|CTRL + SHIFT + TABB- **anteckning:** TABB till föregående skript fungerar när du bara har en Windows PowerShell-flik öppen, eller om du har fler än en Windows PowerShell-flik öppen och fokus är i skript fönstret.|

## <a name="keyboard-shortcuts-for-customizing-the-view"></a>Kortkommandon för att anpassa vyn

Du kan använda följande kortkommandon för att anpassa vyn i Windows PowerShell ISE. De är tillgängliga från alla rutor i programmet.

|Åtgärd|Kortkommando|
|----------|---------------------|
|**Gå till kommando (v2) eller konsol (v3 och senare) fönster**|CTRL+D|
|**Gå till fönstret utdata (endast v2)**|CTRL + SHIFT + O|
|**Gå till skript fönstret**|CTRL + I|
|**Visa skript fönstret**|CTRL + R|
|**Dölj skript fönstret**|CTRL + R|
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
> Du kan också använda kortkommandon som är utformade för Windows PowerShell-konsolen när du felsöker skript i Windows PowerShell ISE. Om du vill använda dessa genvägar måste du skriva genvägen i kommando fönstret och trycka på RETUR.

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
|**Föregående PowerShell-flik**|CTRL + SHIFT + TABB. Den här genvägen fungerar bara när inga filer är öppna på någon Windows PowerShell-flik.|
|**Nästa Windows PowerShell-flik**|CTRL + TAB. Den här genvägen fungerar bara när inga filer är öppna på någon Windows PowerShell-flik.|

## <a name="keyboard-shortcuts-for-starting-and-exiting"></a>Kortkommandon för att starta och avsluta

Du kan använda följande kortkommandon för att starta Windows PowerShell-konsolen (PowerShell. exe) eller avsluta Windows PowerShell ISE.

|Åtgärd|Kortkommando|
|----------|---------------------|
|**Avsluta**|ALT+F4|
|**Starta PowerShell. exe** (Windows PowerShell-konsol)|CTRL + SHIFT + P|

## <a name="see-also"></a>Se även

- [PowerShell-magasin: den fullständiga listan med Windows PowerShell ISE kortkommandon](https://www.powershellmagazine.com/2013/01/29/the-complete-list-of-powershell-ise-3-0-keyboard-shortcuts/)
