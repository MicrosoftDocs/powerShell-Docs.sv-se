---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Utforska Windows PowerShell ISE
ms.openlocfilehash: 7949b690cda73148f07922985b1fc30fe1e8b2d0
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74117450"
---
# <a name="exploring-the-windows-powershell-ise"></a>Utforska Windows PowerShell ISE

Du kan använda Windows PowerShell-® Integrated Scripting Environment (ISE) för att skapa, köra och felsöka kommandon och skript. Windows PowerShell ISE består av meny raden, Windows PowerShell-flikar, verktygsfältet, skript flikar, ett skript fönster, ett fönster, ett statusfält, ett skjutreglage för text storlek och Sammanhangs beroende hjälp.

> [!NOTE]
> Från och med Windows PowerShell ISE 3,0 kombineras kommando-och utdatafönstret i ett enda konsol fönster.

## <a name="menu-bar"></a>Menyrad

Meny raden innehåller **filen**, **Redigera**, **Visa**, **verktyg**, **Felsök**, **tillägg**och **Hjälp** menyer. Med knapparna på menyerna kan du utföra uppgifter som är relaterade till att skriva och köra skript och köra kommandon i Windows PowerShell ISE. Dessutom kan ett [tilläggs verktyg](object-model/The-ISEAddOnTool-Object.md) placeras på Meny raden genom att köra skript som använder- [hierarkin för objekt modellen ISE](object-model/The-ISE-Object-Model-Hierarchy.md).

> [!NOTE]
> I Windows PowerShell ISE 2,0 fanns inte **verktyg** -och **tilläggs** menyerna.

## <a name="windows-powershell-tabs"></a>Windows PowerShell-flikar

En Windows PowerShell-flik är den miljö där ett Windows PowerShell-skript körs. Du kan öppna nya Windows PowerShell-flikar i Windows PowerShell ISE för att skapa separata miljöer på din lokala dator eller på fjärrdatorer. Du kan ha högst åtta PowerShell-flikar öppna samtidigt.

## <a name="toolbar"></a>Verktygsfält

Följande knappar finns i verktygsfältet.

|Knapp|Funktion|
|----------|------------|
|**Ny**|Öppnar ett nytt skript.|
|**Öppna**|Öppnar ett befintligt skript eller en befintlig fil.|
|**Spara**|Sparar ett skript eller en fil.|
|**Styckning**|Klipper ut den markerade texten och kopierar den till Urklipp.|
|**Copy**|Kopierar den markerade texten till Urklipp.|
|**Inklistringsfel**|Klistrar in innehållet i Urklipp vid markörens plats.|
|**Fönstret rensa utdata**|Tar bort allt innehåll i fönstret utdata.|
|**Göra**|Ångrar den åtgärd som precis utfördes.|
|**Tidigare**|Utför den åtgärd som precis har återställts.|
|**Kör skript**|Kör ett skript.|
|**Kör val**|Kör en markerad del av ett skript.|
|**Stoppa körning**|Stoppar ett skript som körs.|
|**Fliken Ny fjärr-PowerShell**|Skapar en ny PowerShell-flik som upprättar en session på en fjärran sluten dator. En dialog ruta visas där du uppmanas att ange information som krävs för att upprätta en fjärr anslutning.|
|**Starta PowerShell. exe**|Öppnar en PowerShell-konsol.|
|**Visa skript fönstret överst**|Flyttar skript fönstret överst i visningen.|
|**Visa skript fönstrets höger**|Flyttar skript fönstret till höger i visningen.|
|**Visa skript fönstret maximerat**|Maximerar skript fönstret.|

## <a name="script-tab"></a>Fliken skript

Visar namnet på det skript som du redigerar. Du kan klicka på en skript-flik för att välja det skript som du vill redigera.

När du pekar på fliken skript visas den fullständigt kvalificerade sökvägen till skript filen i en knapp beskrivning.

## <a name="script-pane"></a>Skript fönster

Gör att du kan skapa och köra skript. Du kan öppna, redigera och köra befintliga skript i skript fönstret.

## <a name="output-pane"></a>Fönstret utdata

Visar resultatet av de kommandon och skript som du har kört. Du kan också kopiera och rensa innehållet i fönstret utdata.

## <a name="command-pane"></a>Kommando fönster

Gör att du kan skriva kommandon. Du kan köra ett kommando rads kommando eller ett flera rader kommando i kommando fönstret. Tryck på SKIFT + RETUR för att ange varje rad i ett flerradig kommando och tryck på RETUR efter den sista raden för att köra kommandot Multiline. Den prompt som visas överst i kommando fönstret visar sökvägen till den aktuella arbets katalogen.

## <a name="status-bar"></a>Statusfält

Gör att du kan se om de kommandon och skript som du kör är slutförda. Statusfältet visas längst ned i visningen. De valda delarna av fel meddelanden visas i statusfältet.

## <a name="text-size-slider"></a>Skjutreglage för text storlek

Ökar eller minskar storleken på texten på skärmen.

## <a name="help"></a>Hjälp

Hjälp för Windows PowerShell ISE finns på webben i TechNet-biblioteket. Du kan öppna hjälpen genom att klicka på **Windows PowerShell ISE hjälp** på **Hjälp** -menyn eller genom att trycka på F1-tangenten var som helst, förutom när markören är på ett cmdlet-namn i antingen skript fönstret eller konsol fönstret. På **Hjälp** -menyn kan du också köra cmdleten Update-Help och Visa kommando fönstret som hjälper dig att skapa kommandon genom att visa alla parametrar för en-cmdlet och göra det möjligt att fylla i parametrarna i ett lättanvänt formulär.

## <a name="see-also"></a>Se även

- [Vi presenterar Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)
