---
ms.date: 01/02/2020
title: Utforska Windows PowerShell ISE
description: Den här artikeln är en översikt över funktionerna i Windows PowerShell ISE
ms.topic: conceptual
ms.custom: ISE-F1-page
ms.openlocfilehash: 91161763c817972a62b4da1558a7ca119d8c8616
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "97090454"
---
# <a name="exploring-the-windows-powershell-ise"></a>Utforska Windows PowerShell ISE

Du kan använda Windows PowerShell ISE (Integrated Scripting Environment) för att skapa, köra och felsöka kommandon och skript. Windows PowerShell ISE består av meny raden, Windows PowerShell-flikar, verktygsfältet, skript flikar, ett skript fönster, ett fönster, ett statusfält, ett skjutreglage för text storlek och Sammanhangs beroende hjälp.

## <a name="menu-bar"></a>Menyrad

Meny raden innehåller **filen**, **Redigera**, **Visa**, **verktyg**, **Felsök**, **tillägg** och **Hjälp** menyer. Med knapparna på menyerna kan du utföra uppgifter som är relaterade till att skriva och köra skript och köra kommandon i Windows PowerShell ISE. Dessutom kan ett [tilläggs verktyg](object-model/The-ISEAddOnTool-Object.md) placeras på Meny raden genom att köra skript som använder- [hierarkin för objekt modellen ISE](object-model/The-ISE-Object-Model-Hierarchy.md).

## <a name="windows-powershell-tabs"></a>Windows PowerShell-flikar

En Windows PowerShell-flik är den miljö där ett Windows PowerShell-skript körs. Du kan öppna nya Windows PowerShell-flikar i Windows PowerShell ISE för att skapa separata miljöer på din lokala dator eller på fjärrdatorer. Du kan ha högst åtta PowerShell-flikar öppna samtidigt.

Mer information finns i [så här skapar du en PowerShell-flik i Windows PowerShell ISE](How-to-Create-a-PowerShell-Tab-in-Windows-PowerShell-ISE.md).

## <a name="toolbar"></a>Verktygsfält

Följande knappar finns i verktygsfältet.

|             Button (Knapp)             |                                                                                     Funktion                                                                                     |
| ------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Nytt**                        | Öppnar ett nytt skript.                                                                                                                                                              |
| **Öppna**                       | Öppnar ett befintligt skript eller en befintlig fil.                                                                                                                                                |
| **Spara**                       | Sparar ett skript eller en fil.                                                                                                                                                          |
| **Klipp ut**                        | Klipper ut den markerade texten och kopierar den till Urklipp.                                                                                                                           |
| **Kopiera**                       | Kopierar den markerade texten till Urklipp.                                                                                                                                       |
| **Klistra in**                      | Klistrar in innehållet i Urklipp vid markörens plats.                                                                                                                     |
| **Fönstret rensa utdata**          | Tar bort allt innehåll i fönstret utdata.                                                                                                                                           |
| **Ångra**                       | Ångrar den åtgärd som precis utfördes.                                                                                                                                     |
| **Gör om**                       | Utför den åtgärd som precis har återställts.                                                                                                                                        |
| **Kör skript**                 | Kör ett skript.                                                                                                                                                                   |
| **Kör val**              | Kör en markerad del av ett skript.                                                                                                                                             |
| **Stoppa körning**             | Stoppar ett skript som körs.                                                                                                                                                  |
| **Fliken Ny fjärr-PowerShell**  | Skapar en ny PowerShell-flik som upprättar en session på en fjärran sluten dator. En dialog ruta visas där du uppmanas att ange information som krävs för att upprätta en fjärr anslutning. |
| **Starta PowerShell.exe**       | Öppnar en PowerShell-konsol.                                                                                                                                                      |
| **Visa skript fönstret överst**       | Flyttar skript fönstret överst i visningen.                                                                                                                                 |
| **Visa skript fönstrets höger**     | Flyttar skript fönstret till höger i visningen.                                                                                                                               |
| **Visa skript fönstret maximerat** | Maximerar skript fönstret.                                                                                                                                                       |

## <a name="script-tab"></a>Fliken skript

Visar namnet på det skript som du redigerar. Du kan klicka på en skript-flik för att välja det skript som du vill redigera.

När du pekar på fliken skript visas den fullständigt kvalificerade sökvägen till skript filen i en knapp beskrivning.

## <a name="script-pane"></a>Skript fönster

Gör att du kan skapa och köra skript. Du kan öppna, redigera och köra befintliga skript i skript fönstret. Mer information finns i [så här skriver du och kör skript i Windows PowerShell ISE](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md).

## <a name="console-pane"></a>Konsol fönster

Visar resultatet av de kommandon och skript som du har kört. Du kan köra kommandon i konsol fönstret. Du kan också kopiera och rensa innehållet i konsol fönstret.

Mer information finns i följande artiklar:

- [Använda konsol fönstret i Windows PowerShell ISE](How-to-Use-the-Console-Pane-in-the-Windows-PowerShell-ISE.md)
- [Felsöka skript i Windows PowerShell ISE](How-to-Debug-Scripts-in-Windows-PowerShell-ISE.md)
- [Använd tabbifyllning i skriptfönstret och konsolfönstret](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md)

## <a name="status-bar"></a>Statusfält

Gör att du kan se om de kommandon och skript som du kör är slutförda. Statusfältet visas längst ned i visningen. De valda delarna av fel meddelanden visas i statusfältet.

## <a name="text-size-slider"></a>Text-Size skjutreglage

Ökar eller minskar storleken på texten på skärmen.

## <a name="help"></a>Hjälp

Hjälp för Windows PowerShell ISE finns på docs.microsoft.com. Du kan öppna hjälpen genom att klicka på **Windows PowerShell ISE hjälp** på **Hjälp** -menyn eller genom att trycka på <kbd>F1</kbd> -tangenten var som helst, förutom när markören är på ett cmdlet-namn i antingen skript fönstret eller konsol fönstret.
På **Hjälp** -menyn kan du också köra- `Update-Help` cmdleten och Visa kommando fönstret som hjälper dig att skapa kommandon genom att visa alla parametrar för en cmdlet och göra det möjligt att fylla i parametrarna i ett lättanvänt formulär.

## <a name="see-also"></a>Se även

- [Vi presenterar Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)
- [Så här använder du profiler i Windows PowerShell ISE](How-to-Use-Profiles-in-Windows-PowerShell-ISE.md)
- [Hjälpmedelsfunktioner i Windows PowerShell ISE](Accessibility-in-Windows-PowerShell-ISE.md)
- [Kortkommandon för Windows PowerShell ISE](Keyboard-Shortcuts-for-the-Windows-PowerShell-ISE.md)
