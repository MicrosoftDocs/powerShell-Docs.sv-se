---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Använd konsolfönstret i Windows PowerShell ISE
ms.assetid: 44d67705-87c7-4a69-a53e-6471fdebb757
ms.openlocfilehash: 5bbbdd3b1f0324ff1a4f2298459f58640c4dc9a6
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405380"
---
# <a name="how-to-use-the-console-pane-in-the-windows-powershell-ise"></a>Använd konsolfönstret i Windows PowerShell ISE

Konsolfönstret i den Windows PowerShell Integrated Scripting Environment (ISE) fungerar precis som fristående Windows PowerShell ISE-konsolfönstret.

Om du vill köra ett kommando i konsolfönstret, anger du kommandot och tryck sedan på RETUR. Skriv SKIFT + RETUR mellan kommandon för att ange flera kommandon som du vill köra i följd. Se [så Använd Tabbifyllning i skriptfönstret och konsolfönstret](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) för hjälp med att skriva kommandon.

Om du vill stoppa ett kommando i verktygsfältet klickar du på **stoppa åtgärden**, eller tryck på CTRL + BREAK. Du kan också använda CTRL + C för att stoppa ett kommando om kontexten är entydiga. Till exempel om du har markerat text i det aktuella fönstret, mappar CTRL + C sedan att kopieringen.

Från och med Windows PowerShell v3, har utdatarutan kombineras med konsolfönstret. Detta har fördelen att fungerar som fristående Windows PowerShell-konsolen och eliminerar skillnader i procedurer som behövs när de separat. Du kan:

- Markera och kopiera text från konsolfönstret till Urklipp för att klistra in i ett annat fönster. Om du vill markera text, klickar du på och håller musen i utdatarutan medan dra musen över texten som du vill samla in. Du kan också använda markören piltangenterna och håll samtidigt **SKIFT** att välja text. Tryck på CTRL + C eller klicka på den **kopia** ikonen i verktygsfältet.

- Klistra in den markerade texten i en aktuella pekarpositionen. Klicka på den **klistra in** ikonen i verktygsfältet.

- Radera all text i konsolfönstret. Om du vill ta bort konsolfönstret, kan du klicka på den **Rensa konsolfönstret** ikonen i verktygsfältet, eller kör kommandot **Clear-Host** eller dess alias **cls**.

## <a name="see-also"></a>Se även

- [Introduktion till Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)