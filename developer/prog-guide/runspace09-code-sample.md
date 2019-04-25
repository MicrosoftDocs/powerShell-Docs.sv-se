---
title: RunSpace09 kodexempel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 136e451f-767b-42e0-bd6f-6486693abd5e
caps.latest.revision: 6
ms.openlocfilehash: e21ef8685598db9a1ae0fcd86051386af526f2a5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081231"
---
# <a name="runspace09-code-sample"></a>RunSpace09 – kodexempel

Här är källkoden för Runspace09-exemplet som beskrivs i [skapar en konsolen program som anropar en Pipeline asynkront](http://msdn.microsoft.com/en-us/198c1c94-2a06-457e-93ce-c0d910618e47). Det här exempelprogrammet skapar och öppnar ett körningsutrymme, skapar och asynkront anropar en pipeline och sedan använder pipeline-händelser för att bearbeta skriptet asynkront. Det skript som körs av det här programmet skapar heltal mellan 1 och 10 i 0,5-sekunder intervall (500 ms).

## <a name="code-sample"></a>Kodexempel

[!code-csharp[Runspace09.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace09/Runspace09.cs#L11-L113 "Runspace09.cs")]

## <a name="see-also"></a>Se även

[Windows PowerShell SDK](../windows-powershell-reference.md)