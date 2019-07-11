---
title: RunSpace09 kodexempel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 136e451f-767b-42e0-bd6f-6486693abd5e
caps.latest.revision: 6
ms.openlocfilehash: 1a21af4b48a414d9c9fee57871eacb0a39c9ab11
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734906"
---
# <a name="runspace09-code-sample"></a><span data-ttu-id="c773d-102">RunSpace09 – kodexempel</span><span class="sxs-lookup"><span data-stu-id="c773d-102">RunSpace09 Code Sample</span></span>

<span data-ttu-id="c773d-103">Här är källkoden för Runspace09-exemplet som beskrivs i [skapar en konsolen program som anropar en Pipeline asynkront](https://msdn.microsoft.com/en-us/198c1c94-2a06-457e-93ce-c0d910618e47).</span><span class="sxs-lookup"><span data-stu-id="c773d-103">Here is the source code for the Runspace09 sample described in [Creating a Console Application That Invokes a Pipeline Asynchronously](https://msdn.microsoft.com/en-us/198c1c94-2a06-457e-93ce-c0d910618e47).</span></span> <span data-ttu-id="c773d-104">Det här exempelprogrammet skapar och öppnar ett körningsutrymme, skapar och asynkront anropar en pipeline och sedan använder pipeline-händelser för att bearbeta skriptet asynkront.</span><span class="sxs-lookup"><span data-stu-id="c773d-104">This sample application creates and opens a runspace, creates and asynchronously invokes a pipeline, and then uses pipeline events to process the script asynchronously.</span></span> <span data-ttu-id="c773d-105">Det skript som körs av det här programmet skapar heltal mellan 1 och 10 i 0,5-sekunder intervall (500 ms).</span><span class="sxs-lookup"><span data-stu-id="c773d-105">The script that is run by this application creates the integers 1 through 10 in 0.5-second intervals (500 ms).</span></span>

## <a name="code-sample"></a><span data-ttu-id="c773d-106">Kodexempel</span><span class="sxs-lookup"><span data-stu-id="c773d-106">Code Sample</span></span>

[!code-csharp[Runspace09.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace09/Runspace09.cs#L11-L113 "Runspace09.cs")]

## <a name="see-also"></a><span data-ttu-id="c773d-107">Se även</span><span class="sxs-lookup"><span data-stu-id="c773d-107">See Also</span></span>

[<span data-ttu-id="c773d-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="c773d-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)