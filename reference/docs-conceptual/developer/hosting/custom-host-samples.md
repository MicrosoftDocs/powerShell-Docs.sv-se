---
title: Anpassade värd exempel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55aee25b-bbcb-4d41-a4c0-fb8e30c4cdc1
caps.latest.revision: 11
ms.openlocfilehash: 1e58b74cf1c37c70ebfb0f4970cfbf8a8263ec5c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72357682"
---
# <a name="custom-host-samples"></a>Exempel på anpassad värd

Det här avsnittet innehåller exempel kod för att skriva en anpassad värd. Du kan använda Microsoft Visual Studio för att skapa ett konsol program och sedan kopiera koden från ämnena i det här avsnittet till värd programmet.

## <a name="in-this-section"></a>I detta avsnitt

 [Host01-exempel](./host01-sample.md) Det här exemplet visar hur du implementerar ett värd program som använder en grundläggande anpassad värd.

 [Host02-exempel](./host02-sample.md) Det här exemplet visar hur du skriver ett värd program som använder Windows PowerShell-körningsmiljön tillsammans med en anpassad värd implementering. Värd programmet ställer in värd kulturen på tyska, kör cmdleten [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) och visar resultatet som du ser dem med hjälp av pwrsh. exe, och skriver sedan ut aktuella data och tid på tyska.

 [Host03-exempel](./host03-sample.md) Det här exemplet visar hur du skapar ett interaktivt konsolbaserade värd program som läser kommandon från kommando raden, kör kommandona och visar resultatet i-konsolen.

 [Host04-exempel](./host04-sample.md) Det här exemplet visar hur du skapar ett interaktivt konsolbaserade värd program som läser kommandon från kommando raden, kör kommandona och visar resultatet i-konsolen. Detta värd program har även stöd för att Visa prompter som gör att användaren kan ange flera alternativ.

 [Host05-exempel](./host05-sample.md) Det här exemplet visar hur du skapar ett interaktivt konsolbaserade värd program som läser kommandon från kommando raden, kör kommandona och visar resultatet i-konsolen. Detta värd program stöder även anrop till fjärrdatorer med hjälp av cmdletarna [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) och [exit-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession)

 [Host06-exempel](./host06-sample.md) Det här exemplet visar hur du skapar ett interaktivt konsolbaserade värd program som läser kommandon från kommando raden, kör kommandona och visar resultatet i-konsolen. I det här exemplet används dessutom Tokenizer-API: er för att ange färgen på texten som anges av användaren.

## <a name="see-also"></a>Se även
