---
ms.date: 01/02/2020
keywords: powershell,cmdlet
title: Använd konsolfönstret i Windows PowerShell ISE
ms.openlocfilehash: f0ef07e410ed494f5732eab360c4e050c9c09a7f
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83810227"
---
# <a name="how-to-use-the-console-pane-in-the-windows-powershell-ise"></a>Använd konsolfönstret i Windows PowerShell ISE

Konsol fönstret i Windows PowerShell ISE (Integrated Scripting Environment) fungerar precis som i det fristående Windows PowerShell ISE konsol fönstret.

Om du vill köra ett kommando i konsol fönstret skriver du ett kommando och trycker på <kbd>RETUR</kbd>. Ange flera kommandon som du vill köra i följd genom att skriva <kbd>Shift</kbd> + <kbd>RETUR</kbd> mellan kommandon. Se [hur du använder slut för ande av flikar i skript fönstret och konsol fönstret](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) för att få hjälp med att skriva kommandon.

Stoppa ett kommando genom att klicka på **stoppa åtgärd**i verktygsfältet eller trycka på <kbd>CTRL</kbd> + <kbd>Break</kbd>. Du kan också använda <kbd>CTRL</kbd> + <kbd>C</kbd> för att stoppa ett kommando om kontexten är tvetydig. Om t. ex. en text har marker ATS i den aktuella rutan, <kbd>CTRL</kbd> + mappas CTRL<kbd>C</kbd> till kopierings åtgärden.

Från och med Windows PowerShell v3 kombinerades fönstret utdata med konsol fönstret. Detta har fördelen att du fungerar som en fristående Windows PowerShell-konsol och eliminerar skillnaderna i de procedurer som behövdes när de var separata. Du kan:

- Markera och kopiera text från konsol fönstret till Urklipp för att klistra in i andra fönster. Om du vill markera text klickar du på och håller ned musen i fönstret utdata och drar musen över den text som du vill avbilda. Du kan också använda piltangenterna när du håller <kbd>SKIFT</kbd> för att markera text. Tryck sedan på <kbd>CTRL</kbd> + <kbd>C</kbd> eller klicka på ikonen **Kopiera** i verktygsfältet.

- Klistra in den markerade texten vid en aktuell markör position. Klicka på ikonen **Klistra in** i verktygsfältet.

- Rensa all text i konsol fönstret. Om du vill rensa konsol fönstret kan du klicka på ikonen **Rensa konsol fönstret** i verktygsfältet eller köra kommandot `Clear-Host` eller dess alias `cls` .

## <a name="see-also"></a>Se även

- [Vi presenterar Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)
