---
title: Windows PowerShell02-exempel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92492a7e-257d-47d3-b119-89df3c5545e8
caps.latest.revision: 9
ms.openlocfilehash: 4d697e73ff4ab4cc4b88593f814d589f89005663
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978652"
---
# <a name="windows-powershell02-sample"></a><span data-ttu-id="37753-102">Windows PowerShell02 – exempel</span><span class="sxs-lookup"><span data-stu-id="37753-102">Windows PowerShell02 Sample</span></span>

<span data-ttu-id="37753-103">Det här exemplet visar hur du kör kommandon asynkront med körnings utrymmen i en körnings utrymme-pool.</span><span class="sxs-lookup"><span data-stu-id="37753-103">This sample shows how to run commands asynchronously using the runspaces of a runspace pool.</span></span> <span data-ttu-id="37753-104">Exemplet genererar en lista med kommandon och kör sedan kommandona medan Windows PowerShell-motorn öppnar en körnings utrymme från poolen när den behövs.</span><span class="sxs-lookup"><span data-stu-id="37753-104">The sample generates a list of commands, and then runs those commands while the Windows PowerShell engine opens a runspace from the pool when it is needed.</span></span>

## <a name="requirements"></a><span data-ttu-id="37753-105">Krav</span><span class="sxs-lookup"><span data-stu-id="37753-105">Requirements</span></span>

- <span data-ttu-id="37753-106">Det här exemplet kräver Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="37753-106">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="37753-107">Demonstrationer</span><span class="sxs-lookup"><span data-stu-id="37753-107">Demonstrates</span></span>

<span data-ttu-id="37753-108">Det här exemplet demonstrerar följande:</span><span class="sxs-lookup"><span data-stu-id="37753-108">This sample demonstrates the following:</span></span>

- <span data-ttu-id="37753-109">Att skapa ett RunspacePool-objekt med ett minsta och maximalt antal körnings utrymmen får vara öppet samtidigt.</span><span class="sxs-lookup"><span data-stu-id="37753-109">Creating a RunspacePool object with a minimum and maximum number of runspaces allowed to be open at the same time.</span></span>
- <span data-ttu-id="37753-110">Skapa en lista med kommandon.</span><span class="sxs-lookup"><span data-stu-id="37753-110">Creating a list of commands.</span></span>
- <span data-ttu-id="37753-111">Kör kommandona asynkront.</span><span class="sxs-lookup"><span data-stu-id="37753-111">Running the commands asynchronously.</span></span>
- <span data-ttu-id="37753-112">Anropa metoden [system. Management. Automation. körnings utrymmen. RunspacePool. Getavailablerunspaces \*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) för att se hur många körnings utrymmen som är kostnads fria.</span><span class="sxs-lookup"><span data-stu-id="37753-112">Calling the [System.Management.Automation.Runspaces.Runspacepool.Getavailablerunspaces\*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) method to see how many runspaces are free.</span></span>
- <span data-ttu-id="37753-113">Fångar kommandoutdata med metoden [system. Management. Automation. PowerShell. EndInvoke \*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) .</span><span class="sxs-lookup"><span data-stu-id="37753-113">Capturing the command output with the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

## <a name="example"></a><span data-ttu-id="37753-114">Exempel</span><span class="sxs-lookup"><span data-stu-id="37753-114">Example</span></span>

<span data-ttu-id="37753-115">Det här exemplet visar hur du öppnar körnings utrymmen i en körnings utrymme-pool och hur du kan köra kommandon asynkront i dessa körnings utrymmen.</span><span class="sxs-lookup"><span data-stu-id="37753-115">This sample shows how to open the runspaces of a runspace pool, and how to asynchronously run commands in those runspaces.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/PowerShell02/PowerShell02.cs" range="11-96":::

## <a name="see-also"></a><span data-ttu-id="37753-116">Se även</span><span class="sxs-lookup"><span data-stu-id="37753-116">See Also</span></span>

[<span data-ttu-id="37753-117">Skriva ett Windows PowerShell-värdprogram</span><span class="sxs-lookup"><span data-stu-id="37753-117">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)
