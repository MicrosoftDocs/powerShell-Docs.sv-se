---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Använd konsolfönstret i Windows PowerShell ISE
ms.openlocfilehash: 114be19b86d98d829620a3718649bc3a3256cb07
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030576"
---
# <a name="how-to-use-the-console-pane-in-the-windows-powershell-ise"></a>Använd konsolfönstret i Windows PowerShell ISE

Konsol fönstret i Windows PowerShell ISE (Integrated Scripting Environment) fungerar precis som i det fristående Windows PowerShell ISE konsol fönstret.

Om du vill köra ett kommando i konsol fönstret skriver du ett kommando och trycker på RETUR. Om du vill ange flera kommandon som ska köras i följd, skriver du SHIFT + retur mellan kommandon. Se [hur du använder slut för ande av flikar i skript fönstret och konsol fönstret](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) för att få hjälp med att skriva kommandon.

Stoppa ett kommando genom att klicka på **stoppa åtgärd**i verktygsfältet eller trycka på Ctrl + Break. Du kan också använda CTRL + C för att stoppa ett kommando om kontexten är tvetydig. Om till exempel en text har marker ATS i den aktuella rutan, kommer CTRL + C att mappa till kopierings åtgärden.

Från och med Windows PowerShell v3 kombinerades fönstret utdata med konsol fönstret. Detta har fördelen att du fungerar som en fristående Windows PowerShell-konsol och eliminerar skillnaderna i de procedurer som behövdes när de var separata. Du kan:

- Markera och kopiera text från konsol fönstret till Urklipp för att klistra in i andra fönster. Om du vill markera text klickar du på och håller ned musen i fönstret utdata och drar musen över den text som du vill avbilda. Du kan också använda piltangenterna när du håller **SKIFT** för att markera text. Tryck på CTRL + C eller klicka på ikonen **Kopiera** i verktygsfältet.

- Klistra in den markerade texten vid en aktuell markör position. Klicka på ikonen **Klistra in** i verktygsfältet.

- Rensa all text i konsol fönstret. Om du vill rensa konsol fönstret kan du klicka på ikonen **Rensa konsol fönster** i verktygsfältet eller köra kommandot **Clear-Host** eller dess alias, **CLS**.

## <a name="see-also"></a>Se även

- [Vi presenterar Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)
