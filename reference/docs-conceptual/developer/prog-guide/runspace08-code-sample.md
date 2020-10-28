---
ms.date: 09/13/2016
ms.topic: reference
title: RunSpace08 – kodexempel
description: RunSpace08 – kodexempel
ms.openlocfilehash: f8d08e5b6bbd98d0901abe5b05c8b9ee682b8e04
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92654227"
---
# <a name="runspace08-code-sample"></a><span data-ttu-id="713c9-103">RunSpace08 – kodexempel</span><span class="sxs-lookup"><span data-stu-id="713c9-103">RunSpace08 Code Sample</span></span>

<span data-ttu-id="713c9-104">Här är käll koden för Runspace08-exemplet som beskrivs i [skapa ett konsol program som lägger till parametrar till ett kommando](https://msdn.microsoft.com/848b2b46-60f1-4a86-b448-cfc7c0cccfba).</span><span class="sxs-lookup"><span data-stu-id="713c9-104">Here is the source code for the Runspace08 sample described in [Creating a Console Application That Adds Parameters to a Command](https://msdn.microsoft.com/848b2b46-60f1-4a86-b448-cfc7c0cccfba).</span></span>
<span data-ttu-id="713c9-105">Det här exempel programmet skapar en körnings utrymme, skapar en pipeline, lägger till två kommandon i pipelinen, lägger till två parametrar till det andra kommandot och kör sedan pipelinen.</span><span class="sxs-lookup"><span data-stu-id="713c9-105">This sample application creates a runspace, creates a pipeline, adds two commands to the pipeline, adds two parameters to the second command, and then executes the pipeline.</span></span> <span data-ttu-id="713c9-106">De kommandon som läggs till i pipelinen är `Get-Process` `Sort-Object` cmdletarna och.</span><span class="sxs-lookup"><span data-stu-id="713c9-106">The commands that are added to the pipeline are the `Get-Process` and `Sort-Object` cmdlets.</span></span>

## <a name="code-sample"></a><span data-ttu-id="713c9-107">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="713c9-107">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace08/Runspace08.cs" range="11-86":::

## <a name="see-also"></a><span data-ttu-id="713c9-108">Se även</span><span class="sxs-lookup"><span data-stu-id="713c9-108">See Also</span></span>

[<span data-ttu-id="713c9-109">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="713c9-109">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
