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
# <a name="windows-powershell-api-samples"></a><span data-ttu-id="260ee-102">Windows PowerShell API-exempel</span><span class="sxs-lookup"><span data-stu-id="260ee-102">Windows PowerShell API Samples</span></span>

<span data-ttu-id="260ee-103">Det här avsnittet innehåller exempelkod som visar hur du skapar körningsutrymmen som begränsar funktioner och hur du kör asynkront kommandon med hjälp av en körningsutrymme pool för att ange körningsutrymmen.</span><span class="sxs-lookup"><span data-stu-id="260ee-103">This section includes sample code that shows how to create runspaces that restrict functionality, and how to asynchronously run commands by using a runspace pool to supply the runspaces.</span></span> <span data-ttu-id="260ee-104">Du kan använda Microsoft Visual Studio för att skapa ett konsolprogram och sedan kopiera koden från avsnitten i det här avsnittet i din värdapp.</span><span class="sxs-lookup"><span data-stu-id="260ee-104">You can use Microsoft Visual Studio to create a console application and then copy the code from the topics in this section into your host application.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="260ee-105">I detta avsnitt</span><span class="sxs-lookup"><span data-stu-id="260ee-105">In This Section</span></span>

<span data-ttu-id="260ee-106">[PowerShell01 exempel](./windows-powershell01-sample.md) i det här exemplet visar hur du använder en [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objekt för att begränsa funktionerna i ett körningsutrymme.</span><span class="sxs-lookup"><span data-stu-id="260ee-106">[PowerShell01 Sample](./windows-powershell01-sample.md) This sample shows how to use an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object to limit the functionality of a runspace.</span></span> <span data-ttu-id="260ee-107">Utdata från det här exemplet visar hur du begränsar språkläge för körningsutrymmet, hur du markerar en cmdlet som privat, hur du lägger till och ta bort cmdletar och providers, hur du lägger till ett kommando för proxy och mycket mer.</span><span class="sxs-lookup"><span data-stu-id="260ee-107">The output of this sample demonstrates how to restrict the language mode of the runspace, how to mark a cmdlet as private, how to add and remove cmdlets and providers, how to add a proxy command, and more.</span></span>

<span data-ttu-id="260ee-108">[PowerShell02 exempel](./windows-powershell02-sample.md) det här exemplet visas hur du kör kommandon asynkront med hjälp av körningsutrymmen av poolen körningsutrymme.</span><span class="sxs-lookup"><span data-stu-id="260ee-108">[PowerShell02 Sample](./windows-powershell02-sample.md) This sample shows how to run commands asynchronously by using the runspaces of a runspace pool.</span></span> <span data-ttu-id="260ee-109">Exemplet genererar en lista över kommandon och sedan kör dessa kommandon medan Windows PowerShell-motorn öppnas ett körningsutrymme från poolen när det behövs.</span><span class="sxs-lookup"><span data-stu-id="260ee-109">The sample generates a list of commands, and then runs those commands while the Windows PowerShell engine opens a runspace from the pool when it is needed.</span></span>