---
title: Windows PowerShell API-exempel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82df2cde-ba12-46d2-b6ec-da5455fd9b57
caps.latest.revision: 8
ms.openlocfilehash: a472f07cb24b0de8e5dcdfcaddd2802575318d7a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850157"
---
# <a name="windows-powershell-api-samples"></a>Windows PowerShell API-exempel

Det här avsnittet innehåller exempelkod som visar hur du skapar körningsutrymmen som begränsar funktioner och hur du kör asynkront kommandon med hjälp av en körningsutrymme pool för att ange körningsutrymmen. Du kan använda Microsoft Visual Studio för att skapa ett konsolprogram och sedan kopiera koden från avsnitten i det här avsnittet i din värdapp.

## <a name="in-this-section"></a>I detta avsnitt

[PowerShell01 exempel](./windows-powershell01-sample.md) i det här exemplet visar hur du använder en [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objekt för att begränsa funktionerna i ett körningsutrymme. Utdata från det här exemplet visar hur du begränsar språkläge för körningsutrymmet, hur du markerar en cmdlet som privat, hur du lägger till och ta bort cmdletar och providers, hur du lägger till ett kommando för proxy och mycket mer.

[PowerShell02 exempel](./windows-powershell02-sample.md) det här exemplet visas hur du kör kommandon asynkront med hjälp av körningsutrymmen av poolen körningsutrymme. Exemplet genererar en lista över kommandon och sedan kör dessa kommandon medan Windows PowerShell-motorn öppnas ett körningsutrymme från poolen när det behövs.