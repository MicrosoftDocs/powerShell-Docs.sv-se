---
ms.date: 09/13/2016
ms.topic: reference
title: Windows PowerShell API-exempel
description: Windows PowerShell API-exempel
ms.openlocfilehash: b6336ae7a2abb98cbbaa69bf6c9455f893db2d94
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92657538"
---
# <a name="windows-powershell-api-samples"></a><span data-ttu-id="09271-103">Windows PowerShell API-exempel</span><span class="sxs-lookup"><span data-stu-id="09271-103">Windows PowerShell API Samples</span></span>

<span data-ttu-id="09271-104">Det här avsnittet innehåller exempel kod som visar hur du skapar körnings utrymmen som begränsar funktionerna och hur du kan köra kommandon asynkront med hjälp av en körnings utrymme-pool för att ange körnings utrymmen.</span><span class="sxs-lookup"><span data-stu-id="09271-104">This section includes sample code that shows how to create runspaces that restrict functionality, and how to asynchronously run commands by using a runspace pool to supply the runspaces.</span></span> <span data-ttu-id="09271-105">Du kan använda Microsoft Visual Studio för att skapa ett konsol program och sedan kopiera koden från ämnena i det här avsnittet till värd programmet.</span><span class="sxs-lookup"><span data-stu-id="09271-105">You can use Microsoft Visual Studio to create a console application and then copy the code from the topics in this section into your host application.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="09271-106">I det här avsnittet</span><span class="sxs-lookup"><span data-stu-id="09271-106">In This Section</span></span>

<span data-ttu-id="09271-107">[PowerShell01-exempel](./windows-powershell01-sample.md) Det här exemplet visar hur du använder ett [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -objekt för att begränsa funktionerna i en körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="09271-107">[PowerShell01 Sample](./windows-powershell01-sample.md) This sample shows how to use an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object to limit the functionality of a runspace.</span></span> <span data-ttu-id="09271-108">Utdata från det här exemplet visar hur du begränsar språk läget för körnings utrymme, hur du markerar en cmdlet som privat, hur du lägger till och tar bort cmdlets och providers, hur du lägger till ett proxy-kommando med mera.</span><span class="sxs-lookup"><span data-stu-id="09271-108">The output of this sample demonstrates how to restrict the language mode of the runspace, how to mark a cmdlet as private, how to add and remove cmdlets and providers, how to add a proxy command, and more.</span></span>

<span data-ttu-id="09271-109">[PowerShell02-exempel](./windows-powershell02-sample.md) Det här exemplet visar hur du kör kommandon asynkront med hjälp av körnings utrymmen i en körnings utrymme-pool.</span><span class="sxs-lookup"><span data-stu-id="09271-109">[PowerShell02 Sample](./windows-powershell02-sample.md) This sample shows how to run commands asynchronously by using the runspaces of a runspace pool.</span></span> <span data-ttu-id="09271-110">Exemplet genererar en lista med kommandon och kör sedan kommandona medan Windows PowerShell-motorn öppnar en körnings utrymme från poolen när den behövs.</span><span class="sxs-lookup"><span data-stu-id="09271-110">The sample generates a list of commands, and then runs those commands while the Windows PowerShell engine opens a runspace from the pool when it is needed.</span></span>
