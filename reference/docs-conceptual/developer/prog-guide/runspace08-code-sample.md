---
title: RunSpace08 kod exempel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f286201-8a02-4b00-9a2c-1b833ccdbdbf
caps.latest.revision: 7
ms.openlocfilehash: 20032913969606f722f3768b0433775aeaa8c3a8
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356961"
---
# <a name="runspace08-code-sample"></a>RunSpace08 – kodexempel

Här är käll koden för Runspace08-exemplet som beskrivs i [skapa ett konsol program som lägger till parametrar till ett kommando](https://msdn.microsoft.com/en-us/848b2b46-60f1-4a86-b448-cfc7c0cccfba). Det här exempel programmet skapar en körnings utrymme, skapar en pipeline, lägger till två kommandon i pipelinen, lägger till två parametrar till det andra kommandot och kör sedan pipelinen. De kommandon som läggs till i pipelinen är `Get-Process`-och `Sort-Object`-cmdletar.

## <a name="code-sample"></a>Kod exempel

[!code-csharp[Runspace08.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace08/Runspace08.cs#L11-L86 "Runspace08.cs")]

## <a name="see-also"></a>Se även

[Windows PowerShell SDK](../windows-powershell-reference.md)
