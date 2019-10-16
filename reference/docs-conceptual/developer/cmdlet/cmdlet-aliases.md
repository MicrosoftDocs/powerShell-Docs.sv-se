---
title: Cmdlet-alias | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0d70864-33fb-49ce-8054-c41ba19fd554
caps.latest.revision: 11
ms.openlocfilehash: 32f45702cc0d28e6652ef61ebdbe085291013408
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359457"
---
# <a name="cmdlet-aliases"></a>Cmdlet-alias

Du kan använda cmdlet-alias för att förbättra användar upplevelsen för cmdleten. Du kan lägga till alias till ofta använda cmdletar för att minska inmatningen och göra det enklare att snabbt utföra uppgifter. Du kan inkludera inbyggda alias i dina cmdletar, eller så kan användarna definiera egna anpassade alias.

Till exempel har cmdleten [Get-Command](/powershell/module/microsoft.powershell.core/get-command) ett inbyggt `gcm`-alias. Du kan också använda alias för att lägga till kommando namn från andra språk så att användarna inte behöver lära sig nya kommandon.

## <a name="alias-guidelines"></a>Rikt linjer för alias

Följ dessa rikt linjer när du skapar inbyggda alias för dina cmdlet: ar:

- Innan du tilldelar alias startar du Windows PowerShell och kör cmdleten [Get-alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) för att se de alias som redan används.

- Inkludera ett alias som refererar till verbet för cmdlet-namnet och ett alias som refererar till substantivet för cmdlet-namnet. Till exempel är aliaset för cmdleten `Import-Module` "ipmo". En lista över alla verb och deras alias finns i [cmdlet-verb](./approved-verbs-for-windows-powershell-commands.md).

- För cmdletar som har samma verb inkluderar du samma alias. Alias för alla Windows PowerShell-cmdletar som har verbet "Get" i namnet använder till exempel prefixet "g".

- För cmdletar som har samma Substantiv inkluderar du samma alias. Alias för alla Windows PowerShell-cmdletar som har "session" Substantiv i sitt namn använder till exempel suffixet "sn".

- För cmdletar som motsvarar kommandon på andra språk använder du namnet på kommandot.

- I allmänhet ska alias vara så kort som möjligt. Kontrol lera att aliaset har minst ett distinktt Character för verbet och ett distinkt Character för substantivet. Lägg till fler tecken vid behov för att göra aliaset unikt.

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
