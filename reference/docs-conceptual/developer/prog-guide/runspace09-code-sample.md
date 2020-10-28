---
ms.date: 09/13/2016
ms.topic: reference
title: RunSpace09 – kodexempel
description: RunSpace09 – kodexempel
ms.openlocfilehash: 52ebfa5dcfd6c12d2ded78a41a6090caa5087149
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92654196"
---
# <a name="runspace09-code-sample"></a>RunSpace09 – kodexempel

Här är käll koden för Runspace09-exemplet som beskrivs i [skapa ett konsol program som anropar en pipeline asynkront](https://msdn.microsoft.com/198c1c94-2a06-457e-93ce-c0d910618e47).
Det här exempel programmet skapar och öppnar en körnings utrymme, skapar och asynkront anropar en pipeline och använder sedan pipeline-händelser för att bearbeta skriptet asynkront. Skriptet som körs av det här programmet skapar heltalen 1 till och med 10 i intervall om 0,5 sekunder (500 ms).

## <a name="code-sample"></a>Kod exempel

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace09/Runspace09.cs" range="11-113":::

## <a name="see-also"></a>Se även

[Windows PowerShell SDK](../windows-powershell-reference.md)
