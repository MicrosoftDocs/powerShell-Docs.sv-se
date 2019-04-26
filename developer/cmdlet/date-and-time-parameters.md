---
title: Datum och tidsparametrar | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71da921b-7c32-4155-b2f8-b19f30ec774d
caps.latest.revision: 7
ms.openlocfilehash: 5b1f093de5db364ac806e58c4ed8dbf2948cb6c6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068240"
---
# <a name="date-and-time-parameters"></a>Datum- och tidsparametrar

I följande tabell visas rekommenderade namn och funktioner för parametrar som hanterar datum och tid. Datum och tid parametrar används vanligtvis för att registrera när något skapas eller öppnas.

|Parameter|Funktioner|
|---|---|
|**Accessed**<br>Datatyp: SwitchParameter|Implementera den här parametern så att när det anges cmdlet: en ska användas för de resurser som har öppnats baseras på datum och tid som anges av den **innan** och **efter** parametrar. Om den här parametern anges den **Skapad** och **modifierats** måste vara inte anges.|
|**När du har**<br>Datatyp: Datetime|Implementera den här parametern om du vill ange datum och tid efter vilken cmdleten har använts. För den **efter** parametern ska fungera, cmdlet: en måste också ha en **Accessed**, **Skapad**, eller **modifierats** parametern. Och parametern måste anges till **SANT** när cmdlet anropas.|
|**Innan du**<br>Datatyp: Datetime|Implementera den här parametern om du vill ange datum och tid som användes för cmdlet: en. För den **innan** parametern ska fungera, cmdlet: en måste också ha en **Accessed**, **Skapad**, eller **modifierats** parametern. Och parametern måste anges till **SANT** när cmdlet anropas.|
|**Skapat**<br>Datatyp: SwitchParameter|Implementera den här parametern så att när det anges cmdlet: en ska användas för de resurser som har skapats utifrån datum och tid som anges av den **innan** och **efter** parametrar. Om den här parametern anges den **Accessed** och **modifierats** parametrar får inte anges.|
|**Exakt**<br>Datatyp: SwitchParameter|Implementera den här parametern så att när det anges att resursen termen måste matcha resursnamnet exakt. Om parametern inte anges behöver resource termen och namnet inte matcha varandra exakt.|
|**Ändrade**<br>Datatyp: Datetime|Implementera den här parametern så att när det anges cmdlet kommer att fungera på resurser som har ändrats baseras på datum och tid som anges av den **innan** och **efter** parametrar. Om den här parametern anges den **Accessed** och **Skapad** parametrar får inte anges.|
## <a name="see-also"></a>Se även

[Cmdlet-parametrarna](./cmdlet-parameters.md)

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
