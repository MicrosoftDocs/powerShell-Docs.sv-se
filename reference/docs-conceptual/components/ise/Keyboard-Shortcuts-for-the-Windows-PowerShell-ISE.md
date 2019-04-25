---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Kortkommandon för Windows PowerShell ISE
ms.assetid: 8328b946-0f02-4ef4-ac28-2743a1b4043b
ms.openlocfilehash: 1abae849ce599b586357fd2a8db46c608932bd4e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086841"
---
# <a name="keyboard-shortcuts-for-the-windows-powershell-ise"></a>Kortkommandon för Windows PowerShell ISE

Du kan använda följande kortkommandon för att utföra åtgärder i Windows PowerShell® Integrated Scripting Environment (ISE). Windows PowerShell ISE är tillgänglig som en del av Windows Server- och Windows klientoperativsystem, men kan även installeras på vissa äldre Windows-operativsystem som en del av den [paketet Windows Management Framework 4.0](https://go.microsoft.com/fwlink/?LinkID=293881).

## <a name="keyboard-shortcuts-for-editing-text"></a>Kortkommandon för att redigera text

Du kan använda följande kortkommandon när du redigerar text.

|Åtgärd|Kortkommandon|Använd i|
|----------|----------------------|----------|
|**Hjälp**|F1|Skriptet fönstret **viktiga:** Du kan ange att F1 hjälp kommer från TechNet-biblioteket på webben eller hämtas hjälpen (se Update-Help). Klicka för att välja **verktyg**, **alternativ**, sedan på den **allmänna inställningar**fliken, ställa in eller ta bort **använda lokala hjälpinnehållet i stället för onlineinnehåll.**|
|**Kopiera**|CTRL+C|Skript, kommando fönstret, ruta utdata|
|**Klipp ut**|CTRL+X|Skriptfönstret, kommandot fönstret|
|**Visa eller Dölj disposition**|CTRL+M|Skriptfönstret|
|**Hitta i skriptet**|CTRL+F|Skriptfönstret|
|**Sök nästa i skriptet**|F3|Skriptfönstret|
|**Sök föregående i skriptet**|SKIFT + F3|Skriptfönstret|
|**Sök efter matchande klammerparentes**|CTRL +]|Skriptfönstret|
|**Klistra in**|CTRL+V|Skriptfönstret, kommandot fönstret|
|**Gör om**|CTRL + Y|Skriptfönstret, kommandot fönstret|
|**Ersätt i skriptet**|CTRL+H|Skriptfönstret|
|**Spara**|CTRL+S|Skriptfönstret|
|**Markera alla**|CTRL+A|Skript, kommando fönstret, ruta utdata|
|**Visa kodfragment**|CTRL+J|Skriptfönstret, kommandot fönstret|
|**Ångra**|CTRL+Z|Skriptfönstret, kommandot fönstret|

## <a name="keyboard-shortcuts-for-running-scripts"></a>Kortkommandon för att köra skript

Du kan använda följande kortkommandon när du kör skript i skriptfönstret.

|Åtgärd|Kortkommando|
|----------|---------------------|
|**Ny**|CTRL + N|
|**Öppna**|CTRL+O|
|**Kör**|F5|
|**Kör val**|F8|
|**Stoppa körning**|CTRL + BREAK. CTRL + C kan användas när kontexten är entydiga (när det finns ingen text är markerad).|
|**Fliken** (till nästa skript)|CTRL + TABB **Obs:** Fliken till nästa skript fungerar bara när du har en enda Windows PowerShell-flik öppnas eller när du har fler än en Windows PowerShell-flik öppnas, men fokus ligger i skriptfönstret.|
|**Fliken** (till föregående skript)|CTRL + SKIFT + TABB **Obs:** Fliken till föregående skript fungerar när du har bara en Windows PowerShell-flik öppnas, eller om du har fler än en Windows PowerShell-flik öppnas och fokus ligger i skriptfönstret.|

## <a name="keyboard-shortcuts-for-customizing-the-view"></a>Kortkommandon för att anpassa vyn

Du kan använda följande kortkommandon för att anpassa vyn i Windows PowerShell ISE. De är tillgängliga från alla fönster i programmet.

|Åtgärd|Kortkommando|
|----------|---------------------|
|**Gå till kommandot (v2) eller konsolen (v3 och senare) fönstret**|CTRL+D|
|**Gå till rutan Testutdata (v2)**|CTRL + SKIFT + O|
|**Gå till skriptfönstret**|CTRL + I|
|**Visa skriptfönstret**|CTRL+R|
|**Dölj skriptfönstret**|CTRL+R|
|**Flytta skriptfönstret upp**|CTRL+1|
|**Flytta skriptfönstret åt höger**|CTRL+2|
|**Maximera skriptfönstret**|CTRL+3|
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
|**Stop Debugger**|SKIFT + F5|När du felsöker ett skript skriptfönstret|

> [!NOTE]
> Du kan också använda kortkommandon som är utformad för Windows PowerShell-konsolen när du felsöker skript i Windows PowerShell ISE. Om du vill använda dessa genvägar, måste du skriver genvägen i fönstret kommando och tryck på RETUR.

|Åtgärd|Kortkommando|Använd i|
|----------|---------------------|----------|
|**Fortsätta**|C|Konsolfönstret när du felsöker ett skript|
|**Stega in**|S|Konsolfönstret när du felsöker ett skript|
|**Hoppa över**|V|Konsolfönstret när du felsöker ett skript|
|**Stega ut**|O|Konsolfönstret när du felsöker ett skript|
|**Upprepa sista kommandot** (för steget på eller hoppa över)|ANGE|Konsolfönstret när du felsöker ett skript|
|**Visa anropsstacken**|K|Konsolfönstret när du felsöker ett skript|
|**Stoppa felsökningen**|Q|Konsolfönstret när du felsöker ett skript|
|**Lista över skriptet**|L|Konsolfönstret när du felsöker ett skript|
|**Visa konsolen felsökning kommandon**|H eller?|Konsolfönstret när du felsöker ett skript|

## <a name="keyboard-shortcuts-for-windows-powershell-tabs"></a>Kortkommandon för Windows PowerShell-flikar

Du kan använda följande kortkommandon när du använder Windows PowerShell-flikar.

|Åtgärd|Kortkommando|
|----------|---------------------|
|**Stäng PowerShell-flik**|CTRL+W|
|**Nya PowerShell-flik**|CTRL+T|
|**Föregående PowerShell-flik**|CTRL + SKIFT + TABB. Den här genvägen fungerar bara när det finns inga filer är öppna på alla Windows PowerShell-flik.|
|**Nästa Windows PowerShell-flik**|CTRL+TAB. Den här genvägen fungerar bara när det finns inga filer är öppna på alla Windows PowerShell-flik.|

## <a name="keyboard-shortcuts-for-starting-and-exiting"></a>Kortkommandon för att starta och avslutas

Du kan använda följande kortkommandon för att starta Windows PowerShell-konsolen (PowerShell.exe) eller för att avsluta Windows PowerShell ISE.

|Åtgärd|Kortkommando|
|----------|---------------------|
|**Avsluta**|ALT+F4|
|**Starta PowerShell.exe** (Windows PowerShell-konsolen)|CTRL + SKIFT + P|

## <a name="see-also"></a>Se även

- [PowerShell-tidningen: Den fullständiga listan med kortkommandon för Windows PowerShell ISE](https://www.powershellmagazine.com/2013/01/29/the-complete-list-of-powershell-ise-3-0-keyboard-shortcuts/)