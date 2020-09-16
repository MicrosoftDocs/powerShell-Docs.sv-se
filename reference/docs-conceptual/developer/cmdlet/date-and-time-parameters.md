---
title: Datum-och tids parametrar | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: f1b2bb3b3da2b73860298e36d88502bfd67c5b22
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774668"
---
# <a name="date-and-time-parameters"></a>Datum- och tidsparametrar

I följande tabell visas rekommenderade namn och funktioner för parametrar som hanterar information om datum och tid. Datum-och tids parametrar används vanligt vis för att registrera när något skapas eller nås.

|Parameter|Funktioner|
|---|---|
|**Nås**<br>Datatyp: SwitchParameter|Implementera den här parametern så att cmdleten körs på de resurser som har öppnats baserat på det datum och den tid som anges av parametrarna **före** och **efter** . Om den här parametern anges får inte parametrarna **created** och **Modified** anges.|
|**Efter**<br>Datatyp: DateTime|Implementera den här parametern för att ange datum och tid då cmdleten användes. För att parametern **efter** ska fungera måste cmdlet: en ha en **åtkomst**, **skapad**eller **ändrad** parameter. Och, den parametern måste anges till **Sant** när cmdleten anropas.|
|**Före**<br>Datatyp: DateTime|Implementera den här parametern för att ange datum och tid innan cmdleten användes. För att parametern **före** ska fungera måste cmdlet: en ha en **åtkomst**, **skapad**eller **ändrad** parameter. Och, den parametern måste anges till **Sant** när cmdleten anropas.|
|**Skapad**<br>Datatyp: SwitchParameter|Implementera den här parametern så att cmdleten körs på de resurser som har skapats baserat på det datum och den tid som anges av parametrarna **före** och **efter** . Om den här parametern anges får inte parametrarna för **åtkomst** och **ändrad** anges.|
|**Noggrann**<br>Datatyp: SwitchParameter|Implementera den här parametern så att resurs termen måste matcha resurs namnet exakt när den anges. Om parametern inte anges behöver inte resurs termen och namnet matcha exakt.|
|**Ändras**<br>Datatyp: DateTime|Implementera den här parametern så att cmdleten körs på resurser som har ändrats baserat på det datum och den tid som anges av parametrarna **före** och **efter** . Om den här parametern anges får inte parametrarna för **åtkomst** och **skapande** anges.|
## <a name="see-also"></a>Se även

[Cmdlet-parametrar](./cmdlet-parameters.md)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
