---
ms.date: 01/02/2020
keywords: powershell,cmdlet
title: Skapa en PowerShell-flik i Windows PowerShell ISE
ms.openlocfilehash: 39df0b76c337bb7c02d36d66b325c5396afbbe00
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83810304"
---
# <a name="how-to-create-a-powershell-tab-in-windows-powershell-ise"></a>Skapa en PowerShell-flik i Windows PowerShell ISE

Med hjälp av flikarna i Windows PowerShell ISE (Integrated Scripting Environment) kan du samtidigt skapa och använda flera körnings miljöer i samma program. Varje PowerShell-flik motsvarar en annan körnings miljö eller-session.

> [!NOTE]
> Variabler, funktioner och alias som du skapar på en flik överför inte över till en annan. De är olika Windows PowerShell-sessioner.

Använd följande steg för att öppna eller stänga en flik i Windows PowerShell. Om du vill byta namn på en flik anger du egenskapen [DisplayName](object-model/The-PowerShellTab-Object.md#displayname) på Windows PowerShell-fliken skript objekt.

## <a name="to-create-and-use-a-new-powershell-tab"></a>Skapa och använda en ny PowerShell-flik

På **Arkiv** -menyn klickar du på **ny PowerShell-flik**. Den nya PowerShell-fliken öppnas alltid som det aktiva fönstret. PowerShell-flikar är stegvisa numrerade i den ordning som de är öppna. Varje flik är kopplad till ett eget fönster i Windows PowerShell-konsolen. Du kan ha upp till 32 PowerShell-flikar med sin egen session öppen i taget (detta är begränsat till 8 på Windows PowerShell ISE 2,0.)

Observera att om du klickar på de **nya** eller **Öppna** ikonerna i verktygsfältet skapas ingen ny flik med en separat session. I stället öppnar dessa knappar en ny eller befintlig skript fil på den aktuella aktiva fliken med en session. Du kan ha flera öppna skriptfiler med varje flik och session. Skript flikarna för en session visas bara under session-flikarna när den associerade sessionen är aktiv.

Klicka på fliken om du vill aktivera en PowerShell-flik. Om du vill välja bland alla PowerShell-flikar som är öppna, klickar du på den PowerShell-flik som du vill använda på **Visa** -menyn.

## <a name="to-create-and-use-a-new-remote-powershell-tab"></a>Skapa och använda en ny fjärran sluten PowerShell-flik

På **Arkiv** -menyn klickar du på **ny fjärran sluten PowerShell-flik** för att upprätta en session på en fjärrdator. En dialog ruta visas där du uppmanas att ange information som krävs för att upprätta en fjärr anslutning. Fjärrfliken fungerar precis som en lokal PowerShell-flik, men kommandona och skripten körs på fjärrdatorn.

## <a name="to-close-a-powershell-tab"></a>Stänga en PowerShell-flik

Om du vill stänga en flik kan du använda någon av följande metoder:

- Klicka på den flik som du vill stänga.

- På **Arkiv** -menyn klickar du på **Stäng PowerShell-fliken**eller på knappen Stäng (**X**) på en aktiv flik för att stänga fliken.

Om du har osparade filer öppna på fliken PowerShell som du stänger, uppmanas du att spara eller ta bort dem. Mer information om hur du sparar ett skript finns i [så här sparar du ett skript](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md#how-to-save-a-script).

## <a name="see-also"></a>Se även

- [Vi presenterar Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)
- [Använda konsol fönstret i Windows PowerShell ISE](How-to-Use-the-Console-Pane-in-the-Windows-PowerShell-ISE.md)
