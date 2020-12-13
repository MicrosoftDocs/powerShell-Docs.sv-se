---
ms.date: 09/13/2016
ms.topic: reference
title: Windows PowerShell02 – exempel
description: Windows PowerShell02 – exempel
ms.openlocfilehash: 61dedd72d93d4000edf9a12f12bbb49fbaeb9f3c
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92657353"
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
