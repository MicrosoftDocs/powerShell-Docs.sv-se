---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Skapa en PowerShell-flik i Windows PowerShell ISE
ms.openlocfilehash: 7baf9a4051a196045d53eebf8ce5260bdc1bc55a
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030582"
---
# <a name="how-to-create-a-powershell-tab-in-windows-powershell-ise"></a>Skapa en PowerShell-flik i Windows PowerShell ISE

Flikarna i den Windows PowerShell Integrated Scripting Environment (ISE) kan du samtidigt skapar och använder flera körningsmiljöer inom samma program.
Varje PowerShell-flik motsvarar en separat körningsmiljö eller -session.

> [!NOTE]
> Variabler, funktioner och alias som du skapar i en flik överför inte till en annan. De är olika Windows PowerShell-sessioner.

Använd följande steg för att öppna eller stänga en flik i Windows PowerShell.
Byt namn på en flik genom att ange den [DisplayName](object-model/The-PowerShellTab-Object.md#displayname) egenskap i Windows PowerShell-flik skript-objektet.

## <a name="to-create-and-use-a-new-powershell-tab"></a>Du skapar och använder en ny PowerShell-flik

På den **filen** -menyn klickar du på **nya PowerShell-flik**. Den nya PowerShell-fliken öppnas alltid som det aktiva fönstret.
PowerShell-flikar numreras stegvis i den ordning som de är öppna.
Varje flik är associerad med sin egen Windows PowerShell-konsolfönster.
Du kan ha upp till 32 PowerShell flikar med sin egen session som är öppna samtidigt (detta är begränsade till 8 om Windows PowerShell ISE 2.0.)

Observera att klicka på den **New** eller **öppna** ikoner i verktygsfältet inte skapa en ny flik med en separat session.
Dessa knappar öppna i stället en ny eller befintlig skriptfil på fliken är aktiva för tillfället med en session.
Du kan ha flera skript öppnas filerna med varje flik och sessionen.
Flikarna skriptet för en session visas endast under flikarna sessionen när den associerade sessionen är aktiv.

Klicka på fliken om du vill aktivera en PowerShell-flik. Att välja från alla PowerShell-flikar som är öppna på de **visa** menyn, klicka på fliken PowerShell som du vill använda.

## <a name="to-create-and-use-a-new-remote-powershell-tab"></a>Du skapar och använder en ny flik för fjärr-PowerShell

På den **filen** -menyn klickar du på **ny Remote PowerShell-flik** att upprätta en session på en fjärrdator.
En dialogruta visas och du uppmanas att ange information som krävs för att upprätta anslutningen.
Fliken fjärrsessioner funktioner precis som en lokal PowerShell-flik men kommandon och skript körs på fjärrdatorn.

## <a name="to-close-a-powershell-tab"></a>Att stänga en PowerShell-flik

Du kan använda någon av följande metoder för att stänga en flik:

- Klicka på fliken som du vill stänga.

- På den **filen** -menyn klickar du på **stänger PowerShell-flik**, eller klicka på Stäng (**X**) på en aktiv flik att Stäng fliken.

Om du har osparade öppna filer i PowerShell-flik att du stänger, uppmanas du att spara eller ta bort dem.
Läs mer om hur du sparar ett skript, [så Spara ett skriptet](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md#how-to-save-a-script).

## <a name="see-also"></a>Se även

- [Introduktion till Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)
- [Hur du använder konsolfönstret i Windows PowerShell ISE](How-to-Use-the-Console-Pane-in-the-Windows-PowerShell-ISE.md)
