---
title: RunSpace09 kod exempel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 136e451f-767b-42e0-bd6f-6486693abd5e
caps.latest.revision: 6
ms.openlocfilehash: 122a40dea93d874a7c131774e3d1abb148bcd4fc
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72352509"
---
# <a name="runspace09-code-sample"></a><span data-ttu-id="93c6e-102">RunSpace09 – kodexempel</span><span class="sxs-lookup"><span data-stu-id="93c6e-102">RunSpace09 Code Sample</span></span>

<span data-ttu-id="93c6e-103">Här är käll koden för Runspace09-exemplet som beskrivs i [skapa ett konsol program som anropar en pipeline asynkront](https://msdn.microsoft.com/en-us/198c1c94-2a06-457e-93ce-c0d910618e47).</span><span class="sxs-lookup"><span data-stu-id="93c6e-103">Here is the source code for the Runspace09 sample described in [Creating a Console Application That Invokes a Pipeline Asynchronously](https://msdn.microsoft.com/en-us/198c1c94-2a06-457e-93ce-c0d910618e47).</span></span> <span data-ttu-id="93c6e-104">Det här exempel programmet skapar och öppnar en körnings utrymme, skapar och asynkront anropar en pipeline och använder sedan pipeline-händelser för att bearbeta skriptet asynkront.</span><span class="sxs-lookup"><span data-stu-id="93c6e-104">This sample application creates and opens a runspace, creates and asynchronously invokes a pipeline, and then uses pipeline events to process the script asynchronously.</span></span> <span data-ttu-id="93c6e-105">Skriptet som körs av det här programmet skapar heltalen 1 till och med 10 i intervall om 0,5 sekunder (500 ms).</span><span class="sxs-lookup"><span data-stu-id="93c6e-105">The script that is run by this application creates the integers 1 through 10 in 0.5-second intervals (500 ms).</span></span>

## <a name="code-sample"></a><span data-ttu-id="93c6e-106">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="93c6e-106">Code Sample</span></span>

[!code-csharp[Runspace09.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace09/Runspace09.cs#L11-L113 "Runspace09.cs")]

## <a name="see-also"></a><span data-ttu-id="93c6e-107">Se även</span><span class="sxs-lookup"><span data-stu-id="93c6e-107">See Also</span></span>

[<span data-ttu-id="93c6e-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="93c6e-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
