---
title: Alias för cmdleten | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0d70864-33fb-49ce-8054-c41ba19fd554
caps.latest.revision: 11
ms.openlocfilehash: 32f45702cc0d28e6652ef61ebdbe085291013408
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068733"
---
# <a name="cmdlet-aliases"></a>Cmdlet-alias

Du kan använda cmdleten alias för att förbättra användarupplevelsen cmdlet. Du kan lägga till alias ofta använda cmdlets för att minska att skriva och gör det enklare att utföra uppgifter snabbt. Du kan inkludera inbyggda alias i dina cmdlets eller användare kan definiera egna anpassade alias.

Till exempel den [Get-Command](/powershell/module/microsoft.powershell.core/get-command) cmdlet har en inbyggd `gcm` alias. Du kan också använda alias för att lägga till kommandonamn från andra språk så att användarna inte behöver lära dig nya kommandon.

## <a name="alias-guidelines"></a>Riktlinjer för alias

Följ dessa riktlinjer när du skapar inbyggda alias för dina cmdlets:

- Innan du tilldelar alias, starta Windows PowerShell och kör sedan den [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet för att se de alias som redan används.

- Inkludera ett alias-prefix som refererar till verbet i cmdlet-namn och en alias-suffix som refererar till substantiv av cmdlet-namn. Till exempel alias för den `Import-Module` cmdlet är ”ipmo”. En lista över alla verb och deras alias, se [Cmdlet verb](./approved-verbs-for-windows-powershell-commands.md).

- För cmdletar som har samma verb prefixet samma alias. Till exempel använda alias för alla Windows PowerShell-cmdlets som har ”Get”-verbet i sina namn prefixet ”g”.

- För cmdletar som har samma substantiv innehåller samma alias-suffix. Till exempel använda alias för alla Windows PowerShell-cmdlets som har ”Session” substantiv i sina namn med suffixet ”sn”.

- Använd namnet på kommandot för cmdletar som motsvarar kommandon på andra språk.

- I allmänhet kan göra alias så korta som möjligt. Kontrollera att aliaset som har minst ett tecken för verbet och ett distinkt tecken för substantivet. Lägga till fler tecken som behövs för att göra det alias som är unika.

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
