---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Utforska Windows PowerShell ISE
ms.assetid: e0d2c6e8-5126-40e7-a1e1-d1cff29fe94a
ms.openlocfilehash: 979209d4b200728b7e78e341bb9595741d2b8e68
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/03/2017
---
# <a name="exploring-the-windows-powershell-ise"></a>Utforska Windows PowerShell ISE
Du kan använda i Windows PowerShell® Integrated Scripting Environment (ISE) för att skapa, köra och felsöka kommandon och skript. Windows PowerShell ISE består av menyraden, Windows PowerShell-flikar, verktygsfältet, skript flikar, en Skriptfönster, en konsolfönstret, ett statusfält, textstorlek skjutreglaget och sammanhangsberoende hjälp.

> [!NOTE]
> Från och med Windows PowerShell ISE 3.0 kommandot och utdata fönster har kombineras till en enda konsolfönstret.

## <a name="menu-bar"></a>Menyraden
Menyraden består av **filen**, **redigera**, **visa**, **verktyg**, **felsöka**,  **Tillägg**, och **hjälp** menyer. Knapparna på menyerna kan du utföra uppgifter för att skriva och köra skript och köra kommandon i Windows PowerShell ISE. Dessutom kan en [tilläggsverktyg](../../core-powershell/ise/The-ISEAddOnTool-Object.md) kan placeras på menyraden genom att köra skript som använder den [Scripting objektmodellen för Windows PowerShell ISE](../../core-powershell/ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md).

> [!NOTE]
> I Windows PowerShell ISE 2.0 på **verktyg** och **tillägg** menyer finns inte.

## <a name="windows-powershell-tabs"></a>Windows PowerShell-flikar
En Windows PowerShell-flik är miljö där ett Windows PowerShell-skript körs. Du kan öppna nya Windows PowerShell-flikar i Windows PowerShell ISE att skapa separata miljöer på den lokala datorn eller på fjärrdatorer. Du kan ha högst åtta PowerShell flikar öppna samtidigt.

## <a name="toolbar"></a>Verktygsfältet
Följande knappar finns i verktygsfältet.

|Knappen|Funktion|
|----------|------------|
|**Ny**|Öppnar ett nytt skript.|
|**Öppna**|Öppnar ett befintligt skript eller en fil.|
|**Spara**|Sparar ett skript eller en fil.|
|**Klipp ut**|Minskar den markerade texten och kopierar den till Urklipp.|
|**Kopiera**|Kopierar den markerade texten till Urklipp.|
|**Klistra in**|Klistrar in innehållet i Urklipp på markören plats.|
|**Rensa utdatafönstret**|Tar bort allt innehåll i Utdatarutan.|
|**Ångra**|Ångrar som precis har utförts.|
|**Gör om**|Utför den åtgärd som var bara ångra.|
|**Kör skript**|Kör ett skript.|
|**Kör markering**|Kör en del av ett skript.|
|**Stoppa körning**|Stoppar ett skript som körs.|
|**Ny flik för fjärranslutna PowerShell**|Skapar en ny flik i PowerShell som upprättar en session på en fjärrdator. En dialogruta visas och du uppmanas att ange information som krävs för att upprätta anslutningen.|
|**Starta PowerShell.exe**|Öppnar en PowerShell-konsol.|
|**Visa skript fönstret översta**|Flyttar skriptfönstret överst på skärmen.|
|**Visa Skriptfönster höger**|Flyttar skriptfönstret till höger på skärmen.|
|**Visa Skriptfönster maximerat**|Maximerar skriptfönstret.|

## <a name="script-tab"></a>Fliken skript
Visar namnet på det skript som du redigerar. Du kan klicka på fliken ett skript för att välja det skript du vill redigera.

När du pekar på fliken skript visas den fullständiga sökvägen till skriptfilen i en knappbeskrivning.

## <a name="script-pane"></a>Skriptfönster
Kan du skapa och köra skript. Du kan öppna, redigera och köra befintliga skript i skriptfönstret.

## <a name="output-pane"></a>Utdatafönstret
Visar resultatet av kommandon och skript som du har kört. Du kan också kopiera och ta bort innehållet i Utdatarutan.

## <a name="command-pane"></a>Kommandot fönstret
Kan du skriva kommandon. Du kan köra ett kommando i en rad eller en flerradig kommando kommando-rutan. På SKIFT + RETUR för att ange varje rad i en flerradig kommando och tryck på RETUR efter den sista raden att köra kommandot flera rader. Uppmaningen visas ovanpå fönstret kommando visar sökvägen till den aktuella arbetskatalogen.

## <a name="status-bar"></a>Statusfältet
Kan du se om kommandon och skript som du kör är klar. Statusfältet är mycket längst ned på skärmen. Delar av felmeddelanden visas i statusfältet.

## <a name="text-size-slider"></a>Textstorlek skjutreglaget
Ökar eller minskar storleken på texten på skärmen.

## <a name="help"></a>Hjälp
För Windows PowerShell ISE finns tillgänglig på webben i TechNet-biblioteket. Du kan öppna hjälpen genom att klicka på **hjälpen för Windows PowerShell ISE** på den **hjälp** menyn eller genom att trycka på F1 var som helst, utom när markören är på en cmdlet-namn i rutan skript eller konsolfönstret. Från den **hjälp** menyn kan du också köra Update-Help cmdleten, och visa kommandofönstret som hjälper dig att konstruera kommandon genom att visa alla parametrar för en cmdlet och gör att du kan fylla i parametrarna i en lätt att använda formuläret.

## <a name="see-also"></a>Se även
- [Med hjälp av Windows PowerShell ISE](../../core-powershell/ise/Using-the-Windows-PowerShell-ISE.md)

