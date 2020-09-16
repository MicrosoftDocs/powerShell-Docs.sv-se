---
title: RunSpace08 kod exempel | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 67172a0f8d6daf2f5b9965d1a18f7698daddbe1a
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784698"
---
# <a name="runspace08-code-sample"></a><span data-ttu-id="28f1c-102">RunSpace08 – kodexempel</span><span class="sxs-lookup"><span data-stu-id="28f1c-102">RunSpace08 Code Sample</span></span>

<span data-ttu-id="28f1c-103">Här är käll koden för Runspace08-exemplet som beskrivs i [skapa ett konsol program som lägger till parametrar till ett kommando](https://msdn.microsoft.com/848b2b46-60f1-4a86-b448-cfc7c0cccfba).</span><span class="sxs-lookup"><span data-stu-id="28f1c-103">Here is the source code for the Runspace08 sample described in [Creating a Console Application That Adds Parameters to a Command](https://msdn.microsoft.com/848b2b46-60f1-4a86-b448-cfc7c0cccfba).</span></span>
<span data-ttu-id="28f1c-104">Det här exempel programmet skapar en körnings utrymme, skapar en pipeline, lägger till två kommandon i pipelinen, lägger till två parametrar till det andra kommandot och kör sedan pipelinen.</span><span class="sxs-lookup"><span data-stu-id="28f1c-104">This sample application creates a runspace, creates a pipeline, adds two commands to the pipeline, adds two parameters to the second command, and then executes the pipeline.</span></span> <span data-ttu-id="28f1c-105">De kommandon som läggs till i pipelinen är `Get-Process` `Sort-Object` cmdletarna och.</span><span class="sxs-lookup"><span data-stu-id="28f1c-105">The commands that are added to the pipeline are the `Get-Process` and `Sort-Object` cmdlets.</span></span>

## <a name="code-sample"></a><span data-ttu-id="28f1c-106">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="28f1c-106">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace08/Runspace08.cs" range="11-86":::

## <a name="see-also"></a><span data-ttu-id="28f1c-107">Se även</span><span class="sxs-lookup"><span data-stu-id="28f1c-107">See Also</span></span>

[<span data-ttu-id="28f1c-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="28f1c-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
