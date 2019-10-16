---
title: Verifierar parameter Indatatyp | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parameters, validation rules
- validation, examples
- validation
ms.assetid: 3f15bf20-a068-4a7d-a170-bc43f755d1fe
caps.latest.revision: 14
ms.openlocfilehash: 171e3e974619e197a0bcc9dfc759297005e34568
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354882"
---
# <a name="validating-parameter-input"></a><span data-ttu-id="caad8-102">Verifiera parameterindata</span><span class="sxs-lookup"><span data-stu-id="caad8-102">Validating Parameter Input</span></span>

<span data-ttu-id="caad8-103">PowerShell kan verifiera argumenten som skickas till cmdlet-parametrar på flera sätt.</span><span class="sxs-lookup"><span data-stu-id="caad8-103">PowerShell can validate the arguments passed to cmdlet parameters in several ways.</span></span>
<span data-ttu-id="caad8-104">PowerShell kan verifiera längden, intervallet och mönstret för tecknen i argumentet.</span><span class="sxs-lookup"><span data-stu-id="caad8-104">PowerShell can validate the length, the range, and the pattern of the characters of the argument.</span></span>
<span data-ttu-id="caad8-105">Det kan verifiera antalet tillgängliga argument (count).</span><span class="sxs-lookup"><span data-stu-id="caad8-105">It can validate the number of arguments available (the count).</span></span>
<span data-ttu-id="caad8-106">Dessa validerings regler definieras av verifierings-attribut som deklareras med attributet parameter i offentliga egenskaper för cmdlet-klassen.</span><span class="sxs-lookup"><span data-stu-id="caad8-106">These validation rules are defined by validation attributes that are declared with the Parameter attribute on public properties of the cmdlet class.</span></span>

<span data-ttu-id="caad8-107">För att validera ett parameter argument använder PowerShell-körningen den information som anges av verifierings-attributen för att bekräfta värdet för parametern innan cmdleten körs.</span><span class="sxs-lookup"><span data-stu-id="caad8-107">To validate a parameter argument, the PowerShell runtime uses the information provided by the validation attributes to confirm the value of the parameter before the cmdlet is run.</span></span>
<span data-ttu-id="caad8-108">Om parameter indata inte är giltiga får användaren ett fel meddelande.</span><span class="sxs-lookup"><span data-stu-id="caad8-108">If the parameter input is not valid, the user receives an error message.</span></span>
<span data-ttu-id="caad8-109">Varje validerings parameter definierar en validerings regel som tillämpas av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="caad8-109">Each validation parameter defines a validation rule that is enforced by PowerShell.</span></span>

<span data-ttu-id="caad8-110">PowerShell framtvingar verifierings reglerna baserat på följande attribut.</span><span class="sxs-lookup"><span data-stu-id="caad8-110">PowerShell enforces the validation rules based on the following attributes.</span></span>

### <a name="validatecount"></a><span data-ttu-id="caad8-111">ValidateCount</span><span class="sxs-lookup"><span data-stu-id="caad8-111">ValidateCount</span></span>

<span data-ttu-id="caad8-112">Anger det lägsta och högsta antalet argument som en parameter kan acceptera.</span><span class="sxs-lookup"><span data-stu-id="caad8-112">Specifies the minimum and maximum number of arguments that a parameter can accept.</span></span>
<span data-ttu-id="caad8-113">Mer information finns i [ValidateCount Attribute-deklaration](./validatecount-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="caad8-113">For more information, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

### <a name="validatelength"></a><span data-ttu-id="caad8-114">ValidateLength</span><span class="sxs-lookup"><span data-stu-id="caad8-114">ValidateLength</span></span>

<span data-ttu-id="caad8-115">Anger det lägsta och högsta antalet tecken i parameter argumentet.</span><span class="sxs-lookup"><span data-stu-id="caad8-115">Specifies the minimum and maximum number of characters in the parameter argument.</span></span>
<span data-ttu-id="caad8-116">Mer information finns i [ValidateLength Attribute-deklaration](./validatelength-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="caad8-116">For more information, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

### <a name="validatepattern"></a><span data-ttu-id="caad8-117">ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="caad8-117">ValidatePattern</span></span>

<span data-ttu-id="caad8-118">Anger ett reguljärt uttryck som validerar parameter argumentet.</span><span class="sxs-lookup"><span data-stu-id="caad8-118">Specifies a regular expression that validates the parameter argument.</span></span>
<span data-ttu-id="caad8-119">Mer information finns i [ValidatePattern Attribute-deklaration](./validatepattern-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="caad8-119">For more information, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

### <a name="validaterange"></a><span data-ttu-id="caad8-120">ValidateRange</span><span class="sxs-lookup"><span data-stu-id="caad8-120">ValidateRange</span></span>

<span data-ttu-id="caad8-121">Anger det lägsta och högsta värdet för parameter argumentet.</span><span class="sxs-lookup"><span data-stu-id="caad8-121">Specifies the minimum and maximum values of the parameter argument.</span></span>
<span data-ttu-id="caad8-122">Mer information finns i [ValidateRange Attribute-deklaration](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="caad8-122">For more information, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

### <a name="validateset"></a><span data-ttu-id="caad8-123">ValidateSet</span><span class="sxs-lookup"><span data-stu-id="caad8-123">ValidateSet</span></span>

<span data-ttu-id="caad8-124">Anger giltiga värden för parameter argumentet.</span><span class="sxs-lookup"><span data-stu-id="caad8-124">Specifies the valid values for the parameter argument.</span></span>
<span data-ttu-id="caad8-125">Mer information finns i [ValidateSet Attribute-deklaration](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="caad8-125">For more information, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="caad8-126">Se även</span><span class="sxs-lookup"><span data-stu-id="caad8-126">See Also</span></span>

[<span data-ttu-id="caad8-127">Verifiera parameter ingångar</span><span class="sxs-lookup"><span data-stu-id="caad8-127">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

[<span data-ttu-id="caad8-128">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="caad8-128">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
