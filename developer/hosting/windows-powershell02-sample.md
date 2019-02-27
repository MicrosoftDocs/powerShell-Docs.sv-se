---
title: Windows PowerShell02 exemplet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92492a7e-257d-47d3-b119-89df3c5545e8
caps.latest.revision: 9
ms.openlocfilehash: 89ad17257ebac56105a93672317a149515e80d32
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850360"
---
# <a name="windows-powershell02-sample"></a>Windows PowerShell02 – exempel

Detta exempel visar hur du kör kommandon asynkront med hjälp av körningsutrymmen av poolen körningsutrymme. Exemplet genererar en lista över kommandon och sedan kör dessa kommandon medan Windows PowerShell-motorn öppnas ett körningsutrymme från poolen när det behövs.

## <a name="requirements"></a>Krav

- Det här exemplet kräver Windows PowerShell 2.0.

## <a name="demonstrates"></a>Visar

Detta exempel visar följande:

- Skapa ett RunspacePool-objekt med ett lägsta och högsta antal körningsutrymmen får vara öppna på samma gång.

- Skapa en lista över kommandon.

- Köra kommandona asynkront.

- Anropa den [System.Management.Automation.Runspaces.Runspacepool.Getavailablerunspaces*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) metod för att se hur många körningsutrymmen är kostnadsfria.

- Samla in utdata från kommandot med den [System.Management.Automation.Powershell.Endinvoke*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) metod.

## <a name="example"></a>Exempel

Detta exempel visar hur du öppnar körningsutrymmen av poolen körningsutrymme och hur du asynkront kör kommandon i dessa körningsutrymmen.

[!code-csharp[PowerShell02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/PowerShell02/PowerShell02.cs#L11-L96 "PowerShell02.cs")]

## <a name="see-also"></a>Se även

[Skriva ett program för Windows PowerShell-värd](./writing-a-windows-powershell-host-application.md)