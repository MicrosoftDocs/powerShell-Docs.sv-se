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
ms.openlocfilehash: 49f6c667b0fd9678586559af39a33f982de0a68c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846713"
---
# <a name="date-and-time-parameters"></a>Datum- och tidsparametrar

I följande tabell visas rekommenderade namn och funktioner för parametrar som hanterar datum och tid. Datum och tid parametrar används vanligtvis för att registrera när något skapas eller öppnas.

Data som används skriver du: SwitchParameter

Implementera den här parametern så att när det anges cmdlet: en ska användas för de resurser som har öppnats baseras på datum och tid som anges av den `Before` och `After` parametrar.

Om den här parametern anges den `Created` och `Modified` måste vara inte anges.

Efter datatyp: Datum/tid

Implementera den här parametern om du vill ange datum och tid efter vilken cmdleten har använts. För den `After` parametern ska fungera, cmdlet: en måste också ha en `Accessed`, `Created`, eller `Modified` parametern. Och parametern måste anges till `true` när cmdlet anropas.

Innan du datatyp: Datum/tid

Implementera den här parametern om du vill ange datum och tid som användes för cmdlet: en. För den `Before` parametern ska fungera, cmdlet: en måste också ha en `Accessed`, `Created`, eller `Modified` parametern. Och parametern måste anges till `true` när cmdlet anropas.

Skapad datatyp: SwitchParameter

Implementera den här parametern så att när det anges cmdlet: en ska användas för de resurser som har skapats utifrån datum och tid som anges av den `Before` och `After` parametrar.

Om den här parametern anges den `Accessed` och `Modified` parametrar får inte anges.

Exakta datatyp: SwitchParameter

Implementera den här parametern så att när det anges att resursen termen måste matcha resursnamnet exakt. Om parametern inte anges behöver resource termen och namnet inte matcha varandra exakt.

Ändrade datatyp: Datum/tid

Implementera den här parametern så att när det anges cmdlet kommer att fungera på resurser som har ändrats baseras på datum och tid som anges av den `Before` och `After` parametrar.

Om den här parametern anges den `Accessed` och `Created` parametrar får inte anges.

## <a name="see-also"></a>Se även

[Cmdlet-parametrarna](./cmdlet-parameters.md)

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
