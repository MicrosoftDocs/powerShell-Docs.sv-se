---
title: RunSpace09 kod exempel | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: fc5d8d4d182cca6bfc42d63c68a14a7a5e5f9c97
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784681"
---
# <a name="runspace09-code-sample"></a><span data-ttu-id="50ce0-102">RunSpace09 – kodexempel</span><span class="sxs-lookup"><span data-stu-id="50ce0-102">RunSpace09 Code Sample</span></span>

<span data-ttu-id="50ce0-103">Här är käll koden för Runspace09-exemplet som beskrivs i [skapa ett konsol program som anropar en pipeline asynkront](https://msdn.microsoft.com/198c1c94-2a06-457e-93ce-c0d910618e47).</span><span class="sxs-lookup"><span data-stu-id="50ce0-103">Here is the source code for the Runspace09 sample described in [Creating a Console Application That Invokes a Pipeline Asynchronously](https://msdn.microsoft.com/198c1c94-2a06-457e-93ce-c0d910618e47).</span></span>
<span data-ttu-id="50ce0-104">Det här exempel programmet skapar och öppnar en körnings utrymme, skapar och asynkront anropar en pipeline och använder sedan pipeline-händelser för att bearbeta skriptet asynkront.</span><span class="sxs-lookup"><span data-stu-id="50ce0-104">This sample application creates and opens a runspace, creates and asynchronously invokes a pipeline, and then uses pipeline events to process the script asynchronously.</span></span> <span data-ttu-id="50ce0-105">Skriptet som körs av det här programmet skapar heltalen 1 till och med 10 i intervall om 0,5 sekunder (500 ms).</span><span class="sxs-lookup"><span data-stu-id="50ce0-105">The script that is run by this application creates the integers 1 through 10 in 0.5-second intervals (500 ms).</span></span>

## <a name="code-sample"></a><span data-ttu-id="50ce0-106">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="50ce0-106">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace09/Runspace09.cs" range="11-113":::

## <a name="see-also"></a><span data-ttu-id="50ce0-107">Se även</span><span class="sxs-lookup"><span data-stu-id="50ce0-107">See Also</span></span>

[<span data-ttu-id="50ce0-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="50ce0-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
