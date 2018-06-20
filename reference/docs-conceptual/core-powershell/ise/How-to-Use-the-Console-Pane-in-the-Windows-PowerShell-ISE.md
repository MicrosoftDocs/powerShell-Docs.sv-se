---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Använd konsolfönstret i Windows PowerShell ISE
ms.assetid: 44d67705-87c7-4a69-a53e-6471fdebb757
ms.openlocfilehash: 5bbbdd3b1f0324ff1a4f2298459f58640c4dc9a6
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
ms.locfileid: "30950795"
---
# <a name="how-to-use-the-console-pane-in-the-windows-powershell-ise"></a>Använd konsolfönstret i Windows PowerShell ISE

Konsolfönstret i i Windows PowerShell Integrated Scripting Environment (ISE) fungerar precis som Windows PowerShell ISE fristående konsolfönstret.

Om du vill köra ett kommando i konsolfönstret, skriver du ett kommando och tryck på RETUR. Skriv SKIFT + RETUR mellan kommandon för att ange flera kommandon som du vill köra i följd. Se [så Använd Flikavslutande i fönstret skript och konsolfönstret](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) för hjälp med att skriva kommandon.

Ett kommando i verktygsfältet klickar du på **stoppa åtgärden**, eller tryck på CTRL + BREAK. Du kan också använda CTRL + C för att stoppa ett kommando om kontexten är tvetydigt. Till exempel om du har markerat lite text i det aktuella fönstret mappar sedan CTRL + C till kopieringen.

Från och med Windows PowerShell v3 har utdatarutan kombineras med konsolfönstret. Detta har fördelen att fungerar som fristående Windows PowerShell-konsolen och eliminerar skillnader i procedurer som behövs när de har separat. Du kan:

- Markera och kopiera text från konsolfönstret till Urklipp och klistra in i andra fönster. Klicka och håll muspekaren i utdatarutan medan du drar över texten som du vill samla in om du vill markera text. Du kan också använda piltangenterna markören vid anläggningen **SKIFT** Markera text. Tryck på CTRL + C eller klicka på den **kopiera** ikonen i verktygsfältet.

- Klistra in den markerade texten på den aktuella pekarpositionen. Klicka på den **klistra in** ikonen i verktygsfältet.

- Rensar du texten i konsolfönstret. Om du vill rensa konsolfönstret, kan du klicka på den **Rensa konsolfönstret** ikonen i verktygsfältet, eller kör kommandot **rensa värden** eller dess alias **cls**.

## <a name="see-also"></a>Se även

- [Introduktion till Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)