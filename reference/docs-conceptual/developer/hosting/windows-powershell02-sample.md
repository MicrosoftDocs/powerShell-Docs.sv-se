---
title: Windows PowerShell02-exempel | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: a82366a88addb08e186eede79e621d90d915c50f
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779394"
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
