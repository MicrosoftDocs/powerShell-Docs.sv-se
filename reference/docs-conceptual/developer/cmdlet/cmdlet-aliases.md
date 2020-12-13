---
ms.date: 09/13/2016
ms.topic: reference
title: Cmdlet-alias
description: Cmdlet-alias
ms.openlocfilehash: 734553a9911aef256df563afa6abcdb23d7a62e6
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660786"
---
# <a name="cmdlet-aliases"></a>Cmdlet-alias

Du kan använda cmdlet-alias för att förbättra användar upplevelsen för cmdleten. Du kan lägga till alias till ofta använda cmdletar för att minska inmatningen och göra det enklare att snabbt utföra uppgifter. Du kan inkludera inbyggda alias i dina cmdletar, eller så kan användarna definiera egna anpassade alias.

Till exempel har cmdleten [Get-Command](/powershell/module/microsoft.powershell.core/get-command) ett inbyggt `gcm` alias. Du kan också använda alias för att lägga till kommando namn från andra språk så att användarna inte behöver lära sig nya kommandon.

## <a name="alias-guidelines"></a>Rikt linjer för alias

Följ dessa rikt linjer när du skapar inbyggda alias för dina cmdlet: ar:

- Innan du tilldelar alias startar du Windows PowerShell och kör cmdleten [Get-alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) för att se de alias som redan används.

- Inkludera ett alias som refererar till verbet för cmdlet-namnet och ett alias som refererar till substantivet för cmdlet-namnet. Aliaset för `Import-Module` cmdleten är till exempel "ipmo". En lista över alla verb och deras alias finns i [cmdlet-verb](./approved-verbs-for-windows-powershell-commands.md).

- För cmdletar som har samma verb inkluderar du samma alias. Alias för alla Windows PowerShell-cmdletar som har verbet "Get" i namnet använder till exempel prefixet "g".

- För cmdletar som har samma Substantiv inkluderar du samma alias. Alias för alla Windows PowerShell-cmdletar som har "session" Substantiv i sitt namn använder till exempel suffixet "sn".

- För cmdletar som motsvarar kommandon på andra språk använder du namnet på kommandot.

- I allmänhet ska alias vara så kort som möjligt. Kontrol lera att aliaset har minst ett distinktt Character för verbet och ett distinkt Character för substantivet. Lägg till fler tecken vid behov för att göra aliaset unikt.

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
