---
title: Windows PowerShell02-exempel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92492a7e-257d-47d3-b119-89df3c5545e8
caps.latest.revision: 9
ms.openlocfilehash: 4d697e73ff4ab4cc4b88593f814d589f89005663
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978652"
---
# <a name="windows-powershell02-sample"></a>Windows PowerShell02 – exempel

Det här exemplet visar hur du kör kommandon asynkront med körnings utrymmen i en körnings utrymme-pool. Exemplet genererar en lista med kommandon och kör sedan kommandona medan Windows PowerShell-motorn öppnar en körnings utrymme från poolen när den behövs.

## <a name="requirements"></a>Krav

- Det här exemplet kräver Windows PowerShell 2,0.

## <a name="demonstrates"></a>Demonstrationer

Det här exemplet demonstrerar följande:

- Att skapa ett RunspacePool-objekt med ett minsta och maximalt antal körnings utrymmen får vara öppet samtidigt.
- Skapa en lista med kommandon.
- Kör kommandona asynkront.
- Anropa metoden [system. Management. Automation. körnings utrymmen. RunspacePool. Getavailablerunspaces *](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) för att se hur många körnings utrymmen som är kostnads fria.
- Fångar kommandoutdata med metoden [system. Management. Automation. PowerShell. EndInvoke *](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) .

## <a name="example"></a>Exempel

Det här exemplet visar hur du öppnar körnings utrymmen i en körnings utrymme-pool och hur du kan köra kommandon asynkront i dessa körnings utrymmen.

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/PowerShell02/PowerShell02.cs" range="11-96":::

## <a name="see-also"></a>Se även

[Skriva ett Windows PowerShell-värdprogram](./writing-a-windows-powershell-host-application.md)
