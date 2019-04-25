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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082523"
---
# <a name="windows-powershell02-sample"></a><span data-ttu-id="32783-102">Windows PowerShell02 – exempel</span><span class="sxs-lookup"><span data-stu-id="32783-102">Windows PowerShell02 Sample</span></span>

<span data-ttu-id="32783-103">Detta exempel visar hur du kör kommandon asynkront med hjälp av körningsutrymmen av poolen körningsutrymme.</span><span class="sxs-lookup"><span data-stu-id="32783-103">This sample shows how to run commands asynchronously by using the runspaces of a runspace pool.</span></span> <span data-ttu-id="32783-104">Exemplet genererar en lista över kommandon och sedan kör dessa kommandon medan Windows PowerShell-motorn öppnas ett körningsutrymme från poolen när det behövs.</span><span class="sxs-lookup"><span data-stu-id="32783-104">The sample generates a list of commands, and then runs those commands while the Windows PowerShell engine opens a runspace from the pool when it is needed.</span></span>

## <a name="requirements"></a><span data-ttu-id="32783-105">Krav</span><span class="sxs-lookup"><span data-stu-id="32783-105">Requirements</span></span>

- <span data-ttu-id="32783-106">Det här exemplet kräver Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="32783-106">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="32783-107">Visar</span><span class="sxs-lookup"><span data-stu-id="32783-107">Demonstrates</span></span>

<span data-ttu-id="32783-108">Detta exempel visar följande:</span><span class="sxs-lookup"><span data-stu-id="32783-108">This sample demonstrates the following:</span></span>

- <span data-ttu-id="32783-109">Skapa ett RunspacePool-objekt med ett lägsta och högsta antal körningsutrymmen får vara öppna på samma gång.</span><span class="sxs-lookup"><span data-stu-id="32783-109">Creating a RunspacePool object with a minimum and maximum number of runspaces allowed to be open at the same time.</span></span>

- <span data-ttu-id="32783-110">Skapa en lista över kommandon.</span><span class="sxs-lookup"><span data-stu-id="32783-110">Creating a list of commands.</span></span>

- <span data-ttu-id="32783-111">Köra kommandona asynkront.</span><span class="sxs-lookup"><span data-stu-id="32783-111">Running the commands asynchronously.</span></span>

- <span data-ttu-id="32783-112">Anropa den [System.Management.Automation.Runspaces.Runspacepool.Getavailablerunspaces\*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) metod för att se hur många körningsutrymmen är kostnadsfria.</span><span class="sxs-lookup"><span data-stu-id="32783-112">Calling the [System.Management.Automation.Runspaces.Runspacepool.Getavailablerunspaces\*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) method to see how many runspaces are free.</span></span>

- <span data-ttu-id="32783-113">Samla in utdata från kommandot med den [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) metod.</span><span class="sxs-lookup"><span data-stu-id="32783-113">Capturing the command output with the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

## <a name="example"></a><span data-ttu-id="32783-114">Exempel</span><span class="sxs-lookup"><span data-stu-id="32783-114">Example</span></span>

<span data-ttu-id="32783-115">Detta exempel visar hur du öppnar körningsutrymmen av poolen körningsutrymme och hur du asynkront kör kommandon i dessa körningsutrymmen.</span><span class="sxs-lookup"><span data-stu-id="32783-115">This sample shows how to open the runspaces of a runspace pool, and how to asynchronously run commands in those runspaces.</span></span>

[!code-csharp[PowerShell02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/PowerShell02/PowerShell02.cs#L11-L96 "PowerShell02.cs")]

## <a name="see-also"></a><span data-ttu-id="32783-116">Se även</span><span class="sxs-lookup"><span data-stu-id="32783-116">See Also</span></span>

[<span data-ttu-id="32783-117">Skriva ett program för Windows PowerShell-värd</span><span class="sxs-lookup"><span data-stu-id="32783-117">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)