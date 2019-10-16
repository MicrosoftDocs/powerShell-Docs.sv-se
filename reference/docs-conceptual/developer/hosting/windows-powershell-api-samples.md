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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353006"
---
# <a name="windows-powershell-api-samples"></a><span data-ttu-id="3e785-102">Windows PowerShell API-exempel</span><span class="sxs-lookup"><span data-stu-id="3e785-102">Windows PowerShell API Samples</span></span>

<span data-ttu-id="3e785-103">Det här avsnittet innehåller exempel kod som visar hur du skapar körnings utrymmen som begränsar funktionerna och hur du kan köra kommandon asynkront med hjälp av en körnings utrymme-pool för att ange körnings utrymmen.</span><span class="sxs-lookup"><span data-stu-id="3e785-103">This section includes sample code that shows how to create runspaces that restrict functionality, and how to asynchronously run commands by using a runspace pool to supply the runspaces.</span></span> <span data-ttu-id="3e785-104">Du kan använda Microsoft Visual Studio för att skapa ett konsol program och sedan kopiera koden från ämnena i det här avsnittet till värd programmet.</span><span class="sxs-lookup"><span data-stu-id="3e785-104">You can use Microsoft Visual Studio to create a console application and then copy the code from the topics in this section into your host application.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="3e785-105">I detta avsnitt</span><span class="sxs-lookup"><span data-stu-id="3e785-105">In This Section</span></span>

<span data-ttu-id="3e785-106">[PowerShell01-exempel](./windows-powershell01-sample.md) Det här exemplet visar hur du använder ett [system. Management. Automation. körnings utrymmen. Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -objekt för att begränsa funktionerna i en körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="3e785-106">[PowerShell01 Sample](./windows-powershell01-sample.md) This sample shows how to use an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object to limit the functionality of a runspace.</span></span> <span data-ttu-id="3e785-107">Utdata från det här exemplet visar hur du begränsar språk läget för körnings utrymme, hur du markerar en cmdlet som privat, hur du lägger till och tar bort cmdlets och providers, hur du lägger till ett proxy-kommando med mera.</span><span class="sxs-lookup"><span data-stu-id="3e785-107">The output of this sample demonstrates how to restrict the language mode of the runspace, how to mark a cmdlet as private, how to add and remove cmdlets and providers, how to add a proxy command, and more.</span></span>

<span data-ttu-id="3e785-108">[PowerShell02-exempel](./windows-powershell02-sample.md) Det här exemplet visar hur du kör kommandon asynkront med hjälp av körnings utrymmen i en körnings utrymme-pool.</span><span class="sxs-lookup"><span data-stu-id="3e785-108">[PowerShell02 Sample](./windows-powershell02-sample.md) This sample shows how to run commands asynchronously by using the runspaces of a runspace pool.</span></span> <span data-ttu-id="3e785-109">Exemplet genererar en lista med kommandon och kör sedan kommandona medan Windows PowerShell-motorn öppnar en körnings utrymme från poolen när den behövs.</span><span class="sxs-lookup"><span data-stu-id="3e785-109">The sample generates a list of commands, and then runs those commands while the Windows PowerShell engine opens a runspace from the pool when it is needed.</span></span>