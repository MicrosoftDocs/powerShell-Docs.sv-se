---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Utforska Windows PowerShell ISE
ms.assetid: e0d2c6e8-5126-40e7-a1e1-d1cff29fe94a
ms.openlocfilehash: 059651f159fb2636a93167709134788e90d062b8
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405369"
---
# <a name="exploring-the-windows-powershell-ise"></a>Utforska Windows PowerShell ISE

Du kan använda i Windows PowerShell® Integrated Scripting Environment (ISE) för att skapa, köra och felsöka kommandon och skript. Windows PowerShell ISE består av menyraden, Windows PowerShell-flikar, i verktygsfältet, skript flikar, en skriptfönstret, en konsolfönstret, ett statusfält, en textstorleken skjutreglaget och sammanhangsberoende hjälp.

> [!NOTE]
> Från och med Windows PowerShell ISE 3.0 kommandot och utdata fönster komprimerades i en enda konsolfönstret.

## <a name="menu-bar"></a>Menyraden

Menyraden består av den **filen**, **redigera**, **visa**, **verktyg**, **felsöka**,  **Tillägg**, och **hjälpa** menyer. Knapparna i menyerna kan du utföra uppgifter som rör skriva och köra skript och köra kommandon i Windows PowerShell ISE. Dessutom kan en [tilläggsverktyg](../../core-powershell/ise/The-ISEAddOnTool-Object.md) kan placeras på menyraden genom att köra skript som använder den [The Objektmodellhierarkin](../../core-powershell/ise/The-ISE-Object-Model-Hierarchy.md).

> [!NOTE]
> I Windows PowerShell ISE 2.0 den **verktyg** och **tillägg** menyer fanns inte.

## <a name="windows-powershell-tabs"></a>Windows PowerShell-flikar

En Windows PowerShell-flik är miljön som ett Windows PowerShell-skript körs. Du kan öppna nya Windows PowerShell-flikar i Windows PowerShell ISE att skapa separata miljöer på den lokala datorn eller på fjärrdatorer. Du kan ha högst åtta PowerShell flikar öppna samtidigt.

## <a name="toolbar"></a>Verktygsfältet

Följande knappar finns i verktygsfältet.

|Knappen|Funktion|
|----------|------------|
|**Ny**|Öppnas ett nytt skript.|
|**Öppna**|Öppnar ett befintligt skript eller en fil.|
|**Spara**|Sparar ett skript eller en fil.|
|**Klipp ut**|Minskar den markerade texten och kopierar den till Urklipp.|
|**Kopiera**|Kopierar den markerade texten till Urklipp.|
|**Klistra in**|Klistrar in innehållet i Urklipp på markören plats.|
|**Rensa rutan Testutdata**|Tar bort allt innehåll i Utdatarutan.|
|**Ångra**|Ångrar som precis har utförts.|
|**Gör om**|Utför den åtgärd som har bara ångra.|
|**Kör skript**|Kör ett skript.|
|**Kör val**|Kör en del av ett skript.|
|**Stoppa körning**|Stoppar ett skript som körs.|
|**Ny Remote PowerShell-flik**|Skapar en ny PowerShell-flik som upprättar en session på en fjärrdator. En dialogruta visas och du uppmanas att ange information som krävs för att upprätta anslutningen.|
|**Starta PowerShell.exe**|Öppna en PowerShell-konsol.|
|**Visa skript fönstret översta**|Flyttar skriptfönstret överst på skärmen.|
|**Visa Skriptfönster rätt**|Flyttar skriptfönstret till höger på skärmen.|
|**Visa Skriptfönster maximerat**|Maximerar skriptfönstret.|

## <a name="script-tab"></a>Fliken skript

Visar namnet på skriptet som du redigerar. Du kan klicka på en flik för skript för att välja det skript du vill redigera.

När du pekar på fliken skript, visas den fullständiga sökvägen till skriptfilen i en knappbeskrivning.

## <a name="script-pane"></a>Skriptfönstret

Kan du skapa och köra skript. Du kan öppna, redigera och köra befintliga skript i skriptfönstret.

## <a name="output-pane"></a>Utdatafönstret

Visar resultatet av kommandon och skript som du har kört. Du kan också kopiera och ta bort innehållet i Utdatarutan.

## <a name="command-pane"></a>Kommandot fönstret

Gör att du kan skriva kommandon. Du kan köra ett kommando för en rad eller en flerradig kommandot i rutan kommando. Tryck på SKIFT + RETUR för att ange varje rad i en flerradig kommando och tryck på RETUR efter den sista raden att köra kommandot består av flera rader. Uppmaningen visas överst i fönstret kommando visar sökvägen till den aktuella arbetskatalogen.

## <a name="status-bar"></a>Statusfält

Kan du se om kommandon och skript som du kör är klar. Statusfältet var mycket längst ned på skärmen. Delar av felmeddelanden visas i statusfältet.

## <a name="text-size-slider"></a>Textstorleken skjutreglaget

Ökar eller minskar storleken på text på skärmen.

## <a name="help"></a>Hjälp

För Windows PowerShell ISE finns tillgänglig på webben i TechNet-biblioteket. Du kan öppna hjälp genom att klicka på **hjälpen för Windows PowerShell ISE** på den **hjälpa** menyn eller genom att trycka på F1 var som helst förutom när markören är på en cmdlet-namn i skriptfönstret och konsolfönstret. Från den **hjälpa** menyn kan du också köra Update-Help cmdleten, och visa kommandofönstret som hjälper dig att konstruera kommandon som visar alla parametrar för en cmdlet, vilket gör att du kan fylla i parametrarna i en enkel att använda formuläret.

## <a name="see-also"></a>Se även

- [Introduktion till Windows PowerShell ISE](../../core-powershell/ise/Introducing-the-Windows-PowerShell-ISE.md)