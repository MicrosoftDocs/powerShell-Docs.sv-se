---
ms.date: 09/13/2016
ms.topic: reference
title: Datum- och tidsparametrar
description: Datum- och tidsparametrar
ms.openlocfilehash: 2f73d16ca8261ebc4ca8d2c18aff4176d7d7314c
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653187"
---
# <a name="date-and-time-parameters"></a>Datum- och tidsparametrar

I följande tabell visas rekommenderade namn och funktioner för parametrar som hanterar information om datum och tid. Datum-och tids parametrar används vanligt vis för att registrera när något skapas eller nås.

|Parameter|Funktioner|
|---|---|
|**Nås**<br>Datatyp: SwitchParameter|Implementera den här parametern så att cmdleten körs på de resurser som har öppnats baserat på det datum och den tid som anges av parametrarna **före** och **efter** . Om den här parametern anges får inte parametrarna **created** och **Modified** anges.|
|**Efter**<br>Datatyp: DateTime|Implementera den här parametern för att ange datum och tid då cmdleten användes. För att parametern **efter** ska fungera måste cmdlet: en ha en **åtkomst**, **skapad** eller **ändrad** parameter. Och, den parametern måste anges till **Sant** när cmdleten anropas.|
|**Före**<br>Datatyp: DateTime|Implementera den här parametern för att ange datum och tid innan cmdleten användes. För att parametern **före** ska fungera måste cmdlet: en ha en **åtkomst**, **skapad** eller **ändrad** parameter. Och, den parametern måste anges till **Sant** när cmdleten anropas.|
|**Skapad**<br>Datatyp: SwitchParameter|Implementera den här parametern så att cmdleten körs på de resurser som har skapats baserat på det datum och den tid som anges av parametrarna **före** och **efter** . Om den här parametern anges får inte parametrarna för **åtkomst** och **ändrad** anges.|
|**Noggrann**<br>Datatyp: SwitchParameter|Implementera den här parametern så att resurs termen måste matcha resurs namnet exakt när den anges. Om parametern inte anges behöver inte resurs termen och namnet matcha exakt.|
|**Ändras**<br>Datatyp: DateTime|Implementera den här parametern så att cmdleten körs på resurser som har ändrats baserat på det datum och den tid som anges av parametrarna **före** och **efter** . Om den här parametern anges får inte parametrarna för **åtkomst** och **skapande** anges.|
## <a name="see-also"></a>Se även

[Cmdlet-parametrar](./cmdlet-parameters.md)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
