---
ms.date: 09/13/2016
ms.topic: reference
title: Exempel på anpassad värd
description: Exempel på anpassad värd
ms.openlocfilehash: 939b9f5d6bbc3ccf1ac95343e897ecffef0a2f42
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92649310"
---
# <a name="custom-host-samples"></a>Exempel på anpassad värd

Det här avsnittet innehåller exempel kod för att skriva en anpassad värd. Du kan använda Microsoft Visual Studio för att skapa ett konsol program och sedan kopiera koden från ämnena i det här avsnittet till värd programmet.

## <a name="in-this-section"></a>I det här avsnittet

 [Host01-exempel](./host01-sample.md) Det här exemplet visar hur du implementerar ett värd program som använder en grundläggande anpassad värd.

 [Host02-exempel](./host02-sample.md) Det här exemplet visar hur du skriver ett värd program som använder Windows PowerShell-körningsmiljön tillsammans med en anpassad värd implementering. Värd programmet ställer in värd kulturen på tyska, kör cmdleten [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) och visar resultatet som du ser dem med pwrsh.exe och skriver sedan ut aktuella data och tid på tyska.

 [Host03-exempel](./host03-sample.md) Det här exemplet visar hur du skapar ett interaktivt konsolbaserade värd program som läser kommandon från kommando raden, kör kommandona och visar resultatet i-konsolen.

 [Host04-exempel](./host04-sample.md) Det här exemplet visar hur du skapar ett interaktivt konsolbaserade värd program som läser kommandon från kommando raden, kör kommandona och visar resultatet i-konsolen. Detta värd program har även stöd för att Visa prompter som gör att användaren kan ange flera alternativ.

 [Host05-exempel](./host05-sample.md) Det här exemplet visar hur du skapar ett interaktivt konsolbaserade värd program som läser kommandon från kommando raden, kör kommandona och visar resultatet i-konsolen. Detta värd program stöder även anrop till fjärrdatorer med hjälp av cmdletarna [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) och [exit-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession)

 [Host06-exempel](./host06-sample.md) Det här exemplet visar hur du skapar ett interaktivt konsolbaserade värd program som läser kommandon från kommando raden, kör kommandona och visar resultatet i-konsolen. I det här exemplet används dessutom Tokenizer-API: er för att ange färgen på texten som anges av användaren.

## <a name="see-also"></a>Se även
