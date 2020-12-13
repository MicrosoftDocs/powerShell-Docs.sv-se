---
ms.date: 09/13/2016
ms.topic: reference
title: RunSpace09 – kodexempel
description: RunSpace09 – kodexempel
ms.openlocfilehash: 52ebfa5dcfd6c12d2ded78a41a6090caa5087149
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654196"
---
# <a name="runspace09-code-sample"></a><span data-ttu-id="89dbf-103">RunSpace09 – kodexempel</span><span class="sxs-lookup"><span data-stu-id="89dbf-103">RunSpace09 Code Sample</span></span>

<span data-ttu-id="89dbf-104">Här är käll koden för Runspace09-exemplet som beskrivs i [skapa ett konsol program som anropar en pipeline asynkront](https://msdn.microsoft.com/198c1c94-2a06-457e-93ce-c0d910618e47).</span><span class="sxs-lookup"><span data-stu-id="89dbf-104">Here is the source code for the Runspace09 sample described in [Creating a Console Application That Invokes a Pipeline Asynchronously](https://msdn.microsoft.com/198c1c94-2a06-457e-93ce-c0d910618e47).</span></span>
<span data-ttu-id="89dbf-105">Det här exempel programmet skapar och öppnar en körnings utrymme, skapar och asynkront anropar en pipeline och använder sedan pipeline-händelser för att bearbeta skriptet asynkront.</span><span class="sxs-lookup"><span data-stu-id="89dbf-105">This sample application creates and opens a runspace, creates and asynchronously invokes a pipeline, and then uses pipeline events to process the script asynchronously.</span></span> <span data-ttu-id="89dbf-106">Skriptet som körs av det här programmet skapar heltalen 1 till och med 10 i intervall om 0,5 sekunder (500 ms).</span><span class="sxs-lookup"><span data-stu-id="89dbf-106">The script that is run by this application creates the integers 1 through 10 in 0.5-second intervals (500 ms).</span></span>

## <a name="code-sample"></a><span data-ttu-id="89dbf-107">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="89dbf-107">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace09/Runspace09.cs" range="11-113":::

## <a name="see-also"></a><span data-ttu-id="89dbf-108">Se även</span><span class="sxs-lookup"><span data-stu-id="89dbf-108">See Also</span></span>

[<span data-ttu-id="89dbf-109">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="89dbf-109">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
