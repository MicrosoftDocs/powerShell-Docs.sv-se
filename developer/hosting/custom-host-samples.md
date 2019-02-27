---
title: Anpassade Host-exempel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55aee25b-bbcb-4d41-a4c0-fb8e30c4cdc1
caps.latest.revision: 11
ms.openlocfilehash: 2d88847e17371c4c04b783569fbd983218b6791b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848645"
---
# <a name="custom-host-samples"></a>Exempel på anpassad värd

Det här avsnittet innehåller exempelkod för att skriva en egen värd. Du kan använda Microsoft Visual Studio för att skapa ett konsolprogram och sedan kopiera koden från avsnitten i det här avsnittet i din värdapp.

## <a name="in-this-section"></a>I detta avsnitt

 [Host01 exempel](./host01-sample.md) det här exemplet visas hur du implementerar ett program som använder en grundläggande anpassad värd.

 [Host02 exempel](./host02-sample.md) det här exemplet visas hur du skriver ett program som använder Windows PowerShell-runtime tillsammans med implementering av anpassade värden. Värdprogrammet anger kulturen värden till tyska, körs den [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet och visar resultat som du ser dem med hjälp av pwrsh.exe och sedan visar du aktuella datum och tidpunkt på tyska.
Detta exempel visar hur du skriver ett program som använder Windows PowerShell-runtime tillsammans med implementering av anpassade värden. Värdprogrammet anger kulturen värden till tyska, körs den [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet och visar resultat som du ser dem med hjälp av pwrsh.exe och sedan visar du aktuella datum och tidpunkt på tyska.

 [Host03 exempel](./host03-sample.md) i det här exemplet visar hur du skapar en interaktiv konsol-baserad värd-program som läser kommandon från kommandoraden, kör kommandona och visar resultatet i konsolen.

 [Host04 exempel](./host04-sample.md) i det här exemplet visar hur du skapar en interaktiv konsol-baserad värd-program som läser kommandon från kommandoraden, kör kommandona och visar resultatet i konsolen. Den här värdprogrammet stöder också med frågor som används att ange flera val.

 [Host05 exempel](./host05-sample.md) i det här exemplet visar hur du skapar en interaktiv konsol-baserad värd-program som läser kommandon från kommandoraden, kör kommandona och visar resultatet i konsolen. Den här värdprogrammet stöder också anrop till fjärrdatorer med hjälp av den [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) och [avsluta-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) cmdletar som detta exempel visar hur du skapar en interaktiv konsol-baserad värd-App som läser kommandon från kommandoraden, kör kommandona och visar resultatet i konsolen. Den här värdprogrammet stöder också anrop till fjärrdatorer med hjälp av den [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) och [avsluta-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) cmdlet: ar

 [Host06 exempel](./host06-sample.md) i det här exemplet visar hur du skapar en interaktiv konsol-baserad värd-program som läser kommandon från kommandoraden, kör kommandona och visar resultatet i konsolen. Det här exemplet använder dessutom Tokenizer-API: er för att ange färgen på texten som anges av användaren.

## <a name="see-also"></a>Se även
