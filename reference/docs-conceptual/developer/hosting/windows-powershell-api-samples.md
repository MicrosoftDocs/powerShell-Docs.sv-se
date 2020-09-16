---
title: Windows PowerShell API-exempel | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: d7232bb16851f1d568cbdfc4374e287d0875adc8
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780176"
---
# <a name="windows-powershell-api-samples"></a>Windows PowerShell API-exempel

Det här avsnittet innehåller exempel kod som visar hur du skapar körnings utrymmen som begränsar funktionerna och hur du kan köra kommandon asynkront med hjälp av en körnings utrymme-pool för att ange körnings utrymmen. Du kan använda Microsoft Visual Studio för att skapa ett konsol program och sedan kopiera koden från ämnena i det här avsnittet till värd programmet.

## <a name="in-this-section"></a>I det här avsnittet

[PowerShell01-exempel](./windows-powershell01-sample.md) Det här exemplet visar hur du använder ett [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -objekt för att begränsa funktionerna i en körnings utrymme. Utdata från det här exemplet visar hur du begränsar språk läget för körnings utrymme, hur du markerar en cmdlet som privat, hur du lägger till och tar bort cmdlets och providers, hur du lägger till ett proxy-kommando med mera.

[PowerShell02-exempel](./windows-powershell02-sample.md) Det här exemplet visar hur du kör kommandon asynkront med hjälp av körnings utrymmen i en körnings utrymme-pool. Exemplet genererar en lista med kommandon och kör sedan kommandona medan Windows PowerShell-motorn öppnar en körnings utrymme från poolen när den behövs.
