---
ms.date: 09/13/2016
ms.topic: reference
title: Windows PowerShell API-exempel
description: Windows PowerShell API-exempel
ms.openlocfilehash: b6336ae7a2abb98cbbaa69bf6c9455f893db2d94
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92657538"
---
# <a name="windows-powershell-api-samples"></a>Windows PowerShell API-exempel

Det här avsnittet innehåller exempel kod som visar hur du skapar körnings utrymmen som begränsar funktionerna och hur du kan köra kommandon asynkront med hjälp av en körnings utrymme-pool för att ange körnings utrymmen. Du kan använda Microsoft Visual Studio för att skapa ett konsol program och sedan kopiera koden från ämnena i det här avsnittet till värd programmet.

## <a name="in-this-section"></a>I det här avsnittet

[PowerShell01-exempel](./windows-powershell01-sample.md) Det här exemplet visar hur du använder ett [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -objekt för att begränsa funktionerna i en körnings utrymme. Utdata från det här exemplet visar hur du begränsar språk läget för körnings utrymme, hur du markerar en cmdlet som privat, hur du lägger till och tar bort cmdlets och providers, hur du lägger till ett proxy-kommando med mera.

[PowerShell02-exempel](./windows-powershell02-sample.md) Det här exemplet visar hur du kör kommandon asynkront med hjälp av körnings utrymmen i en körnings utrymme-pool. Exemplet genererar en lista med kommandon och kör sedan kommandona medan Windows PowerShell-motorn öppnar en körnings utrymme från poolen när den behövs.
