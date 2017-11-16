---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: "Kortkommandon för Windows PowerShell ISE"
ms.assetid: 8328b946-0f02-4ef4-ac28-2743a1b4043b
ms.openlocfilehash: 21c4b43b1ab94e2b533413362319ec42ac8a15aa
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/03/2017
---
# <a name="keyboard-shortcuts-for-the-windows-powershell-ise"></a>Kortkommandon för Windows PowerShell ISE
Använd följande kortkommandon för att utföra åtgärder i Windows PowerShell® Integrated Scripting Environment (ISE). Windows PowerShell ISE är tillgänglig som en del av Windows Server och Windows klientoperativsystem, men kan också installeras på en del äldre Windows-operativsystem som en del av den [Windows Management Framework 4.0-paketet](http://go.microsoft.com/fwlink/?LinkID=293881).

## <a name="keyboard-shortcuts-for-editing-text"></a>Kortkommandon för textredigering
Du kan använda följande kortkommandon när du redigerar text.

|Åtgärd|Kortkommandon|Använd i|
|----------|----------------------|----------|
|**Hjälp**|F1|Script fönstret **viktigt:** kan du ange att F1 hjälp hämtas från TechNet-biblioteket på webben eller hämtas hjälpen (se Update-Help). Klicka för att välja **verktyg**, **alternativ**, sedan på den **allmänna inställningar**fliken, ange eller ta bort **använda lokala hjälpinnehållet i stället för online-innehåll.**|
|**Kopiera**|CTRL+C|Skript, kommando-rutan, ruta utdata|
|**Klipp ut**|CTRL + X|Skriptfönster kommandot fönstret|
|**Visa eller Dölj disposition**|CTRL+M|Skriptfönster|
|**Sök i skript**|CTRL+F|Skriptfönster|
|**Sök nästa i skript**|F3|Skriptfönster|
|**Sök föregående i skript**|SKIFT + F3|Skriptfönster|
|**Sök efter matchande klammerparentes**|CTRL +]|Skriptfönster|
|**Klistra in**|CTRL+V|Skriptfönster kommandot fönstret|
|**Gör om**|CTRL + Y|Skriptfönster kommandot fönstret|
|**Ersätt i skript**|CTRL + H|Skriptfönster|
|**Spara**|CTRL+S|Skriptfönster|
|**Markera alla**|CTRL+A|Skript, kommando-rutan, ruta utdata|
|**Visa kodavsnitt**|CTRL+J|Skriptfönster kommandot fönstret|
|**Ångra**|CTRL + Z|Skriptfönster kommandot fönstret|

## <a name="keyboard-shortcuts-for-running-scripts"></a>Kortkommandon för att köra skript
Du kan använda följande kortkommandon när du kör skript i skriptfönstret.

|Åtgärd|Kortkommando|
|----------|---------------------|
|**Ny**|CTRL + N|
|**Öppna**|CTRL + O|
|**Kör**|F5|
|**Kör markering**|F8|
|**Stoppa körning**|CTRL + BREAK. CTRL + C kan användas när kontexten är entydigt (när det finns ingen text som valts).|
|**Fliken** (för att nästa skript)|CTRL + TABB **Obs:** att nästa skriptet fungerar endast när du har en enda Windows PowerShell-flik öppen, eller när du har mer än en Windows PowerShell-flik öppen, men fokus ligger i skriptfönstret.|
|**Fliken** (för att tidigare skript)|CTRL + SKIFT + TABB **Obs:** att föregående skriptet fungerar när du har en enda Windows PowerShell fliken Öppna, eller om du har mer än en Windows PowerShell-flik öppen och fokus ligger i skriptfönstret.|

## <a name="keyboard-shortcuts-for-customizing-the-view"></a>Kortkommandon för att anpassa vyn
Du kan använda följande kortkommandon för att anpassa vyn i Windows PowerShell ISE. De är tillgängliga från alla fönster i programmet.

|Åtgärd|Kortkommando|
|----------|---------------------|
|**Gå till kommandot (v2) eller konsolen (v3 och senare) fönstret**|CTRL + D|
|**Gå till rutan Testutdata (v2)**|CTRL + SKIFT + O|
|**Gå till Skriptfönster**|CTRL + K|
|**Visa Skriptfönster**|CTRL + R|
|**Dölj Skriptfönster**|CTRL + R|
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

> [!NOTE]
> Du kan också använda kortkommandon som är utformade för Windows PowerShell-konsolen när du felsöker skript i Windows PowerShell ISE. Om du vill använda dessa kortkommandon du skriver kortkommandot i fönstret kommando och tryck på RETUR.

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
|**Föregående PowerShell flik**|CTRL + SKIFT + TABB. Den här genvägen fungerar endast när inga filer är öppna på en Windows PowerShell-flik.|
|**Nästa flik för Windows PowerShell**|CTRL + TABB. Den här genvägen fungerar endast när inga filer är öppna på en Windows PowerShell-flik.|

## <a name="keyboard-shortcuts-for-starting-and-exiting"></a>Kortkommandon för att starta och avsluta
Du kan använda följande kortkommandon om du vill starta Windows PowerShell-konsolen (PowerShell.exe) eller avsluta Windows PowerShell ISE.

|Åtgärd|Kortkommando|
|----------|---------------------|
|**Avsluta**|ALT+F4|
|**Starta PowerShell.exe** (Windows PowerShell-konsol)|CTRL + SKIFT + P|

## <a name="see-also"></a>Se även
- [PowerShell Magazine: En fullständig lista över kortkommandon i Windows PowerShell ISE](http://www.powershellmagazine.com/2013/01/29/the-complete-list-of-powershell-ise-3-0-keyboard-shortcuts/)

