---
title: RunSpace08 kod exempel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f286201-8a02-4b00-9a2c-1b833ccdbdbf
caps.latest.revision: 7
ms.openlocfilehash: 20032913969606f722f3768b0433775aeaa8c3a8
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356961"
---
# <a name="runspace08-code-sample"></a><span data-ttu-id="b9ae0-102">RunSpace08 – kodexempel</span><span class="sxs-lookup"><span data-stu-id="b9ae0-102">RunSpace08 Code Sample</span></span>

<span data-ttu-id="b9ae0-103">Här är käll koden för Runspace08-exemplet som beskrivs i [skapa ett konsol program som lägger till parametrar till ett kommando](https://msdn.microsoft.com/en-us/848b2b46-60f1-4a86-b448-cfc7c0cccfba).</span><span class="sxs-lookup"><span data-stu-id="b9ae0-103">Here is the source code for the Runspace08 sample described in [Creating a Console Application That Adds Parameters to a Command](https://msdn.microsoft.com/en-us/848b2b46-60f1-4a86-b448-cfc7c0cccfba).</span></span> <span data-ttu-id="b9ae0-104">Det här exempel programmet skapar en körnings utrymme, skapar en pipeline, lägger till två kommandon i pipelinen, lägger till två parametrar till det andra kommandot och kör sedan pipelinen.</span><span class="sxs-lookup"><span data-stu-id="b9ae0-104">This sample application creates a runspace, creates a pipeline, adds two commands to the pipeline, adds two parameters to the second command, and then executes the pipeline.</span></span> <span data-ttu-id="b9ae0-105">De kommandon som läggs till i pipelinen är `Get-Process`-och `Sort-Object`-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="b9ae0-105">The commands that are added to the pipeline are the `Get-Process` and `Sort-Object` cmdlets.</span></span>

## <a name="code-sample"></a><span data-ttu-id="b9ae0-106">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="b9ae0-106">Code Sample</span></span>

[!code-csharp[Runspace08.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace08/Runspace08.cs#L11-L86 "Runspace08.cs")]

## <a name="see-also"></a><span data-ttu-id="b9ae0-107">Se även</span><span class="sxs-lookup"><span data-stu-id="b9ae0-107">See Also</span></span>

[<span data-ttu-id="b9ae0-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="b9ae0-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
