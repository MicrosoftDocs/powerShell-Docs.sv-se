---
title: Anpassade värd exempel | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 6a10d3da6d8bf93986a3f5b029fdae3afb23a903
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779530"
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
