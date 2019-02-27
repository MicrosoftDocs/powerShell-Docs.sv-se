---
title: Exempel på Cmdlet-kod | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6fed2f68-ce6d-4a8f-bf21-f94f27a155c2
caps.latest.revision: 9
ms.openlocfilehash: 39c0814faf72cdb4b24730acb2ae429a2f465b32
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851802"
---
# <a name="examples-of-cmdlet-code"></a><span data-ttu-id="bce5c-102">Exempel på cmdlet-kod</span><span class="sxs-lookup"><span data-stu-id="bce5c-102">Examples of Cmdlet Code</span></span>

<span data-ttu-id="bce5c-103">Det här avsnittet innehåller exempel på cmdlet-kod som du kan använda för att börja skriva din egen cmdletar.</span><span class="sxs-lookup"><span data-stu-id="bce5c-103">This section contains examples of cmdlet code that you can use to start writing your own cmdlets.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bce5c-104">Om du vill stegvisa instruktioner för att skriva cmdlets, se [självstudier för skrivning cmdletar](./tutorials-for-writing-cmdlets.md).</span><span class="sxs-lookup"><span data-stu-id="bce5c-104">If you want step-by-step instructions for writing cmdlets, see [Tutorials for Writing Cmdlets](./tutorials-for-writing-cmdlets.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="bce5c-105">I detta avsnitt</span><span class="sxs-lookup"><span data-stu-id="bce5c-105">In This Section</span></span>

<span data-ttu-id="bce5c-106">[Hur du skriver en enkel Cmdlet](./how-to-write-a-simple-cmdlet.md) det här exemplet visar den grundläggande strukturen i cmdlet-kod.</span><span class="sxs-lookup"><span data-stu-id="bce5c-106">[How to Write a Simple Cmdlet](./how-to-write-a-simple-cmdlet.md) This example shows the basic structure of cmdlet code.</span></span>

<span data-ttu-id="bce5c-107">[Hur du deklarera Cmdlet-parametrarna](./how-to-declare-cmdlet-parameters.md) det här exemplet visar hur du deklarera de olika typerna av parametrar.</span><span class="sxs-lookup"><span data-stu-id="bce5c-107">[How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md) This example shows how to declare the different types of parameters.</span></span>

<span data-ttu-id="bce5c-108">[Hur du deklarera parametern anger](./how-to-declare-parameter-sets.md) det här exemplet visar hur du deklarera uppsättningar med parametrar som kan ändra den åtgärd som en cmdlet utför.</span><span class="sxs-lookup"><span data-stu-id="bce5c-108">[How to Declare Parameter Sets](./how-to-declare-parameter-sets.md) This example shows how to declare sets of parameters that can change the action a cmdlet performs.</span></span>

<span data-ttu-id="bce5c-109">[Så här för att verifiera parametern inkommande](./how-to-validate-parameter-input.md) exemplen visar hur du verifierar indata för parametern.</span><span class="sxs-lookup"><span data-stu-id="bce5c-109">[How to Validate Parameter Input](./how-to-validate-parameter-input.md) These examples show how to validate parameter input.</span></span>

<span data-ttu-id="bce5c-110">[Hur du deklarera dynamiska parametrar](./how-to-declare-dynamic-parameters.md) det här exemplet visar hur du deklarera en parameter som har lagts till under körning.</span><span class="sxs-lookup"><span data-stu-id="bce5c-110">[How to Declare Dynamic Parameters](./how-to-declare-dynamic-parameters.md) This example shows how to declare a parameter that is added at runtime.</span></span>

<span data-ttu-id="bce5c-111">[Hur du anropar skript i en Cmdlet](./how-to-invoke-scripts-within-a-cmdlet.md) det här exemplet visar hur du anropar ett skript som har angetts för en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bce5c-111">[How to Invoke Scripts Within a Cmdlet](./how-to-invoke-scripts-within-a-cmdlet.md) This example shows how to invoke a script that is supplied to a cmdlet.</span></span>

<span data-ttu-id="bce5c-112">[Åsidosätta indata bearbetningsmetoder](./how-to-override-input-processing-methods.md) alltså den grundläggande strukturen som används för att åsidosätta BeginProcessing och ProcessRecord EndProcessing metoder.</span><span class="sxs-lookup"><span data-stu-id="bce5c-112">[How To Override Input Processing Methods](./how-to-override-input-processing-methods.md) These examples show the basic structure used to override the BeginProcessing, ProcessRecord, and EndProcessing methods.</span></span>

<span data-ttu-id="bce5c-113">[Så här ShouldProcess supportsamtal](./how-to-request-confirmations.md) det här exemplet visar hur [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) och [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)metoder ska anropas från en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bce5c-113">[How to Support ShouldProcess Calls](./how-to-request-confirmations.md) This example shows how the [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods should be called from within a cmdlet.</span></span>

<span data-ttu-id="bce5c-114">[Hur du stöd för transaktioner](./how-to-support-transactions.md) det här exemplet visar hur du anger att cmdleten har stöd för transaktioner och hur du implementerar vad som händer när cmdlet: en används i en transaktion.</span><span class="sxs-lookup"><span data-stu-id="bce5c-114">[How to Support Transactions](./how-to-support-transactions.md) This example shows how to indicate that the cmdlet supports transactions and how to implement the action that is taken when the cmdlet is used within a transaction.</span></span>

<span data-ttu-id="bce5c-115">[Så här stöder jobb](./how-to-support-jobs.md) det här exemplet visar hur du ger stöd jobb när du skriver cmdletar.</span><span class="sxs-lookup"><span data-stu-id="bce5c-115">[How to Support Jobs](./how-to-support-jobs.md) This example shows how to support jobs when you write cmdlets.</span></span>

<span data-ttu-id="bce5c-116">[Hur du anropar en Cmdlet från inom en Cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md) det här exemplet visar hur du anropar en cmdlet från inom en annan cmdlet, där du kan lägga till funktioner för anropade cmdlet: en till den cmdlet som du utvecklar.</span><span class="sxs-lookup"><span data-stu-id="bce5c-116">[How to Invoke a Cmdlet From Within a Cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md) This example shows how to invoke a cmdlet from within another cmdlet, which allows you to add the functionality of the invoked cmdlet to the cmdlet you are developing.</span></span>

## <a name="see-also"></a><span data-ttu-id="bce5c-117">Se även</span><span class="sxs-lookup"><span data-stu-id="bce5c-117">See Also</span></span>

[<span data-ttu-id="bce5c-118">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="bce5c-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
