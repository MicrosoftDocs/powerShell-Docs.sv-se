---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: "Så här skapar du en PowerShell-flik i Windows PowerShell ISE"
ms.assetid: c10c18c7-9ece-4fd0-83dc-a19c53d4fd83
ms.openlocfilehash: 3cfeb18babe6b63f0e02da8cf0fd460950f1afce
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/08/2017
---
# <a name="how-to-create-a-powershell-tab-in-windows-powershell-ise"></a>Så här skapar du en PowerShell-flik i Windows PowerShell ISE
Flikarna i den Windows PowerShell Integrated Scripting Environment (ISE) kan du skapa och använda flera körning miljöer inom samma program samtidigt.
Varje flik PowerShell motsvarar en separat körningsmiljö eller session.

> **OBS**:
>
> Variabler, funktioner och alias som du skapar i en flik utför inte till en annan. De är olika Windows PowerShell-sessioner.

Använd följande steg för att öppna eller stänga en flik i Windows PowerShell.
Byt namn på en flik genom att ange den [DisplayName](The-PowerShellTab-Object.md#displayname) egenskapen i fliken i Windows PowerShell-skript objektet.

## <a name="to-create-and-use-a-new-powershell-tab"></a>Skapa och använda en ny flik i PowerShell

På den **filen** -menyn klickar du på **ny PowerShell-flik**. Fliken PowerShell öppnas alltid som det aktiva fönstret.
PowerShell-flikar numreras inkrementellt i den ordning som de är öppna.
Varje flik är associerad med sin egen Windows PowerShell-konsolfönster.
Du kan ha upp till 32 PowerShell flikar med sin egen session som är öppna samtidigt (detta är begränsad till 8 i Windows PowerShell ISE 2.0.)

Observera att klicka på den **ny** eller **öppna** ikoner i verktygsfältet inte skapa en ny flik med en separat session.
Knapparna Öppna i stället en ny eller befintlig skriptfil på fliken aktiva med en session.
Du kan ha flera skript filer öppna med varje flik och sessionen.
Flikarna skriptet för en session visas endast under flikarna sessionen när den associerade sessionen är aktiv.

Klicka på fliken om du vill aktivera en PowerShell-flik. Att välja från alla PowerShell flikar som är öppna på de **visa** -menyn klickar du på fliken PowerShell som du vill använda.

## <a name="to-create-and-use-a-new-remote-powershell-tab"></a>Skapa och använda en ny flik för fjärr-PowerShell

På den **filen** -menyn klickar du på **Remote PowerShell fliken** att upprätta en session på en fjärrdator.
En dialogruta visas och du uppmanas att ange information som krävs för att upprätta anslutningen.
Fliken fjärrsessioner funktioner precis som en lokal PowerShell-fliken, men kommandon och skript körs på fjärrdatorn.

## <a name="to-close-a-powershell-tab"></a>Att stänga en PowerShell-fliken

Du kan använda någon av följande metoder för att stänga en flik:

- Klicka på fliken som du vill avsluta.

- På den **filen** -menyn klickar du på **stänga PowerShell fliken**, eller klicka på knappen Stäng (**X**) på en aktiv fliken för att stänga fliken.

Om du har osparade öppna filer på fliken PowerShell att du stänger, du uppmanas att spara eller ta bort dem.
Mer information om hur du sparar ett skript finns [hur du sparar ett skriptet](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md#how-to-save-a-script).

## <a name="see-also"></a>Se även

- [Med hjälp av Windows PowerShell ISE](Using-the-Windows-PowerShell-ISE.md)
- [Hur du använder konsolfönstret i Windows PowerShell ISE](How-to-Use-the-Console-Pane-in-the-Windows-PowerShell-ISE.md)

