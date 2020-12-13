---
ms.date: 09/13/2016
ms.topic: reference
title: Exempel på cmdlet-kod
description: Exempel på cmdlet-kod
ms.openlocfilehash: 91dd2019300504697ad9a7a0c155a04600d09c58
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652914"
---
# <a name="examples-of-cmdlet-code"></a><span data-ttu-id="fdc99-103">Exempel på cmdlet-kod</span><span class="sxs-lookup"><span data-stu-id="fdc99-103">Examples of Cmdlet Code</span></span>

<span data-ttu-id="fdc99-104">Det här avsnittet innehåller exempel på en cmdlet-kod som du kan använda för att börja skriva dina egna cmdletar.</span><span class="sxs-lookup"><span data-stu-id="fdc99-104">This section contains examples of cmdlet code that you can use to start writing your own cmdlets.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fdc99-105">Om du vill ha steg-för-steg-instruktioner för att skriva cmdlet: ar, se [självstudier för att skriva cmdletar](./tutorials-for-writing-cmdlets.md).</span><span class="sxs-lookup"><span data-stu-id="fdc99-105">If you want step-by-step instructions for writing cmdlets, see [Tutorials for Writing Cmdlets](./tutorials-for-writing-cmdlets.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="fdc99-106">I det här avsnittet</span><span class="sxs-lookup"><span data-stu-id="fdc99-106">In This Section</span></span>

<span data-ttu-id="fdc99-107">Så [här skriver du en enkel cmdlet](./how-to-write-a-simple-cmdlet.md) I det här exemplet visas den grundläggande strukturen för cmdlet-kod.</span><span class="sxs-lookup"><span data-stu-id="fdc99-107">[How to Write a Simple Cmdlet](./how-to-write-a-simple-cmdlet.md) This example shows the basic structure of cmdlet code.</span></span>

<span data-ttu-id="fdc99-108">[Så här deklarerar du cmdlet-parametrar](./how-to-declare-cmdlet-parameters.md) Det här exemplet visar hur du deklarerar olika typer av parametrar.</span><span class="sxs-lookup"><span data-stu-id="fdc99-108">[How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md) This example shows how to declare the different types of parameters.</span></span>

<span data-ttu-id="fdc99-109">[Så här deklarerar du parameter uppsättningar](./how-to-declare-parameter-sets.md) Det här exemplet visar hur du deklarerar uppsättningar med parametrar som kan ändra vilken åtgärd en cmdlet utför.</span><span class="sxs-lookup"><span data-stu-id="fdc99-109">[How to Declare Parameter Sets](./how-to-declare-parameter-sets.md) This example shows how to declare sets of parameters that can change the action a cmdlet performs.</span></span>

<span data-ttu-id="fdc99-110">[Verifiera parameter ingångar](./how-to-validate-parameter-input.md) I de här exemplen visas hur du verifierar parameter ingångar.</span><span class="sxs-lookup"><span data-stu-id="fdc99-110">[How to Validate Parameter Input](./how-to-validate-parameter-input.md) These examples show how to validate parameter input.</span></span>

<span data-ttu-id="fdc99-111">[Så här deklarerar du dynamiska parametrar](./how-to-declare-dynamic-parameters.md) Det här exemplet visar hur du deklarerar en parameter som läggs till vid körning.</span><span class="sxs-lookup"><span data-stu-id="fdc99-111">[How to Declare Dynamic Parameters](./how-to-declare-dynamic-parameters.md) This example shows how to declare a parameter that is added at runtime.</span></span>

<span data-ttu-id="fdc99-112">[Så här anropar du skript i en cmdlet](./how-to-invoke-scripts-within-a-cmdlet.md) Det här exemplet visar hur du anropar ett skript som anges för en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fdc99-112">[How to Invoke Scripts Within a Cmdlet](./how-to-invoke-scripts-within-a-cmdlet.md) This example shows how to invoke a script that is supplied to a cmdlet.</span></span>

<span data-ttu-id="fdc99-113">[Åsidosätta indata bearbetnings metoder](./how-to-override-input-processing-methods.md) I de här exemplen visas den grundläggande struktur som används för att åsidosätta metoderna BeginProcessing, ProcessRecord och EndProcessing.</span><span class="sxs-lookup"><span data-stu-id="fdc99-113">[How To Override Input Processing Methods](./how-to-override-input-processing-methods.md) These examples show the basic structure used to override the BeginProcessing, ProcessRecord, and EndProcessing methods.</span></span>

<span data-ttu-id="fdc99-114">[Så här stöder du ShouldProcess-anrop](./how-to-request-confirmations.md) Det här exemplet visar hur metoden [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) och [system. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) ska anropas inifrån en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fdc99-114">[How to Support ShouldProcess Calls](./how-to-request-confirmations.md) This example shows how the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods should be called from within a cmdlet.</span></span>

<span data-ttu-id="fdc99-115">[Så här stöder du transaktioner](./how-to-support-transactions.md) Det här exemplet visar hur du anger att cmdleten stöder transaktioner och hur du implementerar den åtgärd som vidtas när cmdleten används i en transaktion.</span><span class="sxs-lookup"><span data-stu-id="fdc99-115">[How to Support Transactions](./how-to-support-transactions.md) This example shows how to indicate that the cmdlet supports transactions and how to implement the action that is taken when the cmdlet is used within a transaction.</span></span>

<span data-ttu-id="fdc99-116">[Så här stöder du jobb](./how-to-support-jobs.md) Det här exemplet visar hur du stöder jobb när du skriver-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="fdc99-116">[How to Support Jobs](./how-to-support-jobs.md) This example shows how to support jobs when you write cmdlets.</span></span>

<span data-ttu-id="fdc99-117">[Så här anropar du en cmdlet inifrån en cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md) Det här exemplet visar hur du anropar en cmdlet från en annan cmdlet, vilket gör att du kan lägga till funktionerna i den anropade cmdleten till den cmdlet som du utvecklar.</span><span class="sxs-lookup"><span data-stu-id="fdc99-117">[How to Invoke a Cmdlet From Within a Cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md) This example shows how to invoke a cmdlet from within another cmdlet, which allows you to add the functionality of the invoked cmdlet to the cmdlet you are developing.</span></span>

## <a name="see-also"></a><span data-ttu-id="fdc99-118">Se även</span><span class="sxs-lookup"><span data-stu-id="fdc99-118">See Also</span></span>

[<span data-ttu-id="fdc99-119">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="fdc99-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
