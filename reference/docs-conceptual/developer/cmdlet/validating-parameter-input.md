---
title: Verifierar parameter Indatatyp | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- parameters, validation rules
- validation, examples
- validation
ms.openlocfilehash: e12c715cfa24edfff958b12be1f3517b2f545256
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784001"
---
# <a name="validating-parameter-input"></a><span data-ttu-id="cef65-102">Verifiera parameterindata</span><span class="sxs-lookup"><span data-stu-id="cef65-102">Validating Parameter Input</span></span>

<span data-ttu-id="cef65-103">PowerShell kan verifiera argumenten som skickas till cmdlet-parametrar på flera sätt.</span><span class="sxs-lookup"><span data-stu-id="cef65-103">PowerShell can validate the arguments passed to cmdlet parameters in several ways.</span></span>
<span data-ttu-id="cef65-104">PowerShell kan verifiera längden, intervallet och mönstret för tecknen i argumentet.</span><span class="sxs-lookup"><span data-stu-id="cef65-104">PowerShell can validate the length, the range, and the pattern of the characters of the argument.</span></span>
<span data-ttu-id="cef65-105">Det kan verifiera antalet tillgängliga argument (count).</span><span class="sxs-lookup"><span data-stu-id="cef65-105">It can validate the number of arguments available (the count).</span></span>
<span data-ttu-id="cef65-106">Dessa validerings regler definieras av verifierings-attribut som deklareras med attributet parameter i offentliga egenskaper för cmdlet-klassen.</span><span class="sxs-lookup"><span data-stu-id="cef65-106">These validation rules are defined by validation attributes that are declared with the Parameter attribute on public properties of the cmdlet class.</span></span>

<span data-ttu-id="cef65-107">För att validera ett parameter argument använder PowerShell-körningen den information som anges av verifierings-attributen för att bekräfta värdet för parametern innan cmdleten körs.</span><span class="sxs-lookup"><span data-stu-id="cef65-107">To validate a parameter argument, the PowerShell runtime uses the information provided by the validation attributes to confirm the value of the parameter before the cmdlet is run.</span></span>
<span data-ttu-id="cef65-108">Om parameter indata inte är giltiga får användaren ett fel meddelande.</span><span class="sxs-lookup"><span data-stu-id="cef65-108">If the parameter input is not valid, the user receives an error message.</span></span>
<span data-ttu-id="cef65-109">Varje validerings parameter definierar en validerings regel som tillämpas av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cef65-109">Each validation parameter defines a validation rule that is enforced by PowerShell.</span></span>

<span data-ttu-id="cef65-110">PowerShell framtvingar verifierings reglerna baserat på följande attribut.</span><span class="sxs-lookup"><span data-stu-id="cef65-110">PowerShell enforces the validation rules based on the following attributes.</span></span>

### <a name="validatecount"></a><span data-ttu-id="cef65-111">ValidateCount</span><span class="sxs-lookup"><span data-stu-id="cef65-111">ValidateCount</span></span>

<span data-ttu-id="cef65-112">Anger det lägsta och högsta antalet argument som en parameter kan acceptera.</span><span class="sxs-lookup"><span data-stu-id="cef65-112">Specifies the minimum and maximum number of arguments that a parameter can accept.</span></span>
<span data-ttu-id="cef65-113">Mer information finns i [ValidateCount Attribute-deklaration](./validatecount-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="cef65-113">For more information, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

### <a name="validatelength"></a><span data-ttu-id="cef65-114">ValidateLength</span><span class="sxs-lookup"><span data-stu-id="cef65-114">ValidateLength</span></span>

<span data-ttu-id="cef65-115">Anger det lägsta och högsta antalet tecken i parameter argumentet.</span><span class="sxs-lookup"><span data-stu-id="cef65-115">Specifies the minimum and maximum number of characters in the parameter argument.</span></span>
<span data-ttu-id="cef65-116">Mer information finns i [ValidateLength Attribute-deklaration](./validatelength-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="cef65-116">For more information, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

### <a name="validatepattern"></a><span data-ttu-id="cef65-117">ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="cef65-117">ValidatePattern</span></span>

<span data-ttu-id="cef65-118">Anger ett reguljärt uttryck som validerar parameter argumentet.</span><span class="sxs-lookup"><span data-stu-id="cef65-118">Specifies a regular expression that validates the parameter argument.</span></span>
<span data-ttu-id="cef65-119">Mer information finns i [ValidatePattern Attribute-deklaration](./validatepattern-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="cef65-119">For more information, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

### <a name="validaterange"></a><span data-ttu-id="cef65-120">ValidateRange</span><span class="sxs-lookup"><span data-stu-id="cef65-120">ValidateRange</span></span>

<span data-ttu-id="cef65-121">Anger det lägsta och högsta värdet för parameter argumentet.</span><span class="sxs-lookup"><span data-stu-id="cef65-121">Specifies the minimum and maximum values of the parameter argument.</span></span>
<span data-ttu-id="cef65-122">Mer information finns i [ValidateRange Attribute-deklaration](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="cef65-122">For more information, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

### <a name="validateset"></a><span data-ttu-id="cef65-123">ValidateSet</span><span class="sxs-lookup"><span data-stu-id="cef65-123">ValidateSet</span></span>

<span data-ttu-id="cef65-124">Anger giltiga värden för parameter argumentet.</span><span class="sxs-lookup"><span data-stu-id="cef65-124">Specifies the valid values for the parameter argument.</span></span>
<span data-ttu-id="cef65-125">Mer information finns i [ValidateSet Attribute-deklaration](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="cef65-125">For more information, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cef65-126">Se även</span><span class="sxs-lookup"><span data-stu-id="cef65-126">See Also</span></span>

[<span data-ttu-id="cef65-127">Verifiera parameterindata</span><span class="sxs-lookup"><span data-stu-id="cef65-127">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

[<span data-ttu-id="cef65-128">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="cef65-128">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
