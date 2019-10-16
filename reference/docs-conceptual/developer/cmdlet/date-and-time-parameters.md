---
title: Datum-och tids parametrar | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71da921b-7c32-4155-b2f8-b19f30ec774d
caps.latest.revision: 7
ms.openlocfilehash: 5b1f093de5db364ac806e58c4ed8dbf2948cb6c6
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359389"
---
# <a name="date-and-time-parameters"></a>Datum- och tidsparametrar

I följande tabell visas rekommenderade namn och funktioner för parametrar som hanterar information om datum och tid. Datum-och tids parametrar används vanligt vis för att registrera när något skapas eller nås.

|Parameter|Funktioner|
|---|---|
|**Nås**<br>Datatyp: SwitchParameter|Implementera den här parametern så att cmdleten körs på de resurser som har öppnats baserat på det datum och den tid som anges av parametrarna **före** och **efter** . Om den här parametern anges får inte parametrarna **created** och **Modified** anges.|
|**När**<br>Datatyp: DateTime|Implementera den här parametern för att ange datum och tid då cmdleten användes. För att parametern **efter** ska fungera måste cmdlet: en ha en **åtkomst**, **skapad**eller **ändrad** parameter. Och, den parametern måste anges till **Sant** när cmdleten anropas.|
|**Framför**<br>Datatyp: DateTime|Implementera den här parametern för att ange datum och tid innan cmdleten användes. För att parametern **före** ska fungera måste cmdlet: en ha en **åtkomst**, **skapad**eller **ändrad** parameter. Och, den parametern måste anges till **Sant** när cmdleten anropas.|
|**Create**<br>Datatyp: SwitchParameter|Implementera den här parametern så att cmdleten körs på de resurser som har skapats baserat på det datum och den tid som anges av parametrarna **före** och **efter** . Om den här parametern anges får inte parametrarna för **åtkomst** och **ändrad** anges.|
|**Noggrann**<br>Datatyp: SwitchParameter|Implementera den här parametern så att resurs termen måste matcha resurs namnet exakt när den anges. Om parametern inte anges behöver inte resurs termen och namnet matcha exakt.|
|**Ändras**<br>Datatyp: DateTime|Implementera den här parametern så att cmdleten körs på resurser som har ändrats baserat på det datum och den tid som anges av parametrarna **före** och **efter** . Om den här parametern anges får inte parametrarna för **åtkomst** och **skapande** anges.|
## <a name="see-also"></a>Se även

[Cmdlet-parametrar](./cmdlet-parameters.md)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
