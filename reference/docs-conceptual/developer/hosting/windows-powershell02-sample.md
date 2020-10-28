---
ms.date: 09/13/2016
ms.topic: reference
title: Windows PowerShell02 – exempel
description: Windows PowerShell02 – exempel
ms.openlocfilehash: 61dedd72d93d4000edf9a12f12bbb49fbaeb9f3c
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92657353"
---
# <a name="windows-powershell02-sample"></a><span data-ttu-id="451b0-103">Windows PowerShell02 – exempel</span><span class="sxs-lookup"><span data-stu-id="451b0-103">Windows PowerShell02 Sample</span></span>

<span data-ttu-id="451b0-104">Det här exemplet visar hur du kör kommandon asynkront med körnings utrymmen i en körnings utrymme-pool.</span><span class="sxs-lookup"><span data-stu-id="451b0-104">This sample shows how to run commands asynchronously using the runspaces of a runspace pool.</span></span> <span data-ttu-id="451b0-105">Exemplet genererar en lista med kommandon och kör sedan kommandona medan Windows PowerShell-motorn öppnar en körnings utrymme från poolen när den behövs.</span><span class="sxs-lookup"><span data-stu-id="451b0-105">The sample generates a list of commands, and then runs those commands while the Windows PowerShell engine opens a runspace from the pool when it is needed.</span></span>

## <a name="requirements"></a><span data-ttu-id="451b0-106">Krav</span><span class="sxs-lookup"><span data-stu-id="451b0-106">Requirements</span></span>

- <span data-ttu-id="451b0-107">Det här exemplet kräver Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="451b0-107">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="451b0-108">Demonstrationer</span><span class="sxs-lookup"><span data-stu-id="451b0-108">Demonstrates</span></span>

<span data-ttu-id="451b0-109">Det här exemplet demonstrerar följande:</span><span class="sxs-lookup"><span data-stu-id="451b0-109">This sample demonstrates the following:</span></span>

- <span data-ttu-id="451b0-110">Att skapa ett RunspacePool-objekt med ett minsta och maximalt antal körnings utrymmen får vara öppet samtidigt.</span><span class="sxs-lookup"><span data-stu-id="451b0-110">Creating a RunspacePool object with a minimum and maximum number of runspaces allowed to be open at the same time.</span></span>
- <span data-ttu-id="451b0-111">Skapa en lista med kommandon.</span><span class="sxs-lookup"><span data-stu-id="451b0-111">Creating a list of commands.</span></span>
- <span data-ttu-id="451b0-112">Kör kommandona asynkront.</span><span class="sxs-lookup"><span data-stu-id="451b0-112">Running the commands asynchronously.</span></span>
- <span data-ttu-id="451b0-113">Anropa metoden [system. Management. Automation. körnings utrymmen. RunspacePool. Getavailablerunspaces \*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) för att se hur många körnings utrymmen som är kostnads fria.</span><span class="sxs-lookup"><span data-stu-id="451b0-113">Calling the [System.Management.Automation.Runspaces.Runspacepool.Getavailablerunspaces\*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) method to see how many runspaces are free.</span></span>
- <span data-ttu-id="451b0-114">Fångar kommandoutdata med metoden [system. Management. Automation. PowerShell. EndInvoke \*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) .</span><span class="sxs-lookup"><span data-stu-id="451b0-114">Capturing the command output with the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

## <a name="example"></a><span data-ttu-id="451b0-115">Exempel</span><span class="sxs-lookup"><span data-stu-id="451b0-115">Example</span></span>

<span data-ttu-id="451b0-116">Det här exemplet visar hur du öppnar körnings utrymmen i en körnings utrymme-pool och hur du kan köra kommandon asynkront i dessa körnings utrymmen.</span><span class="sxs-lookup"><span data-stu-id="451b0-116">This sample shows how to open the runspaces of a runspace pool, and how to asynchronously run commands in those runspaces.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/PowerShell02/PowerShell02.cs" range="11-96":::

## <a name="see-also"></a><span data-ttu-id="451b0-117">Se även</span><span class="sxs-lookup"><span data-stu-id="451b0-117">See Also</span></span>

[<span data-ttu-id="451b0-118">Skriva ett Windows PowerShell-värdprogram</span><span class="sxs-lookup"><span data-stu-id="451b0-118">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)
