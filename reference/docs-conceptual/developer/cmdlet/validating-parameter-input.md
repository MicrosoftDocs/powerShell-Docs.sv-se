---
ms.date: 09/13/2016
ms.topic: reference
title: Verifiera parameterindata
description: Verifiera parameterindata
ms.openlocfilehash: a97b5c670e8c36463a85bbef1506f6311bdd5ec3
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660396"
---
# <a name="validating-parameter-input"></a><span data-ttu-id="d13ef-103">Verifiera parameterindata</span><span class="sxs-lookup"><span data-stu-id="d13ef-103">Validating Parameter Input</span></span>

<span data-ttu-id="d13ef-104">PowerShell kan verifiera argumenten som skickas till cmdlet-parametrar på flera sätt.</span><span class="sxs-lookup"><span data-stu-id="d13ef-104">PowerShell can validate the arguments passed to cmdlet parameters in several ways.</span></span>
<span data-ttu-id="d13ef-105">PowerShell kan verifiera längden, intervallet och mönstret för tecknen i argumentet.</span><span class="sxs-lookup"><span data-stu-id="d13ef-105">PowerShell can validate the length, the range, and the pattern of the characters of the argument.</span></span>
<span data-ttu-id="d13ef-106">Det kan verifiera antalet tillgängliga argument (count).</span><span class="sxs-lookup"><span data-stu-id="d13ef-106">It can validate the number of arguments available (the count).</span></span>
<span data-ttu-id="d13ef-107">Dessa validerings regler definieras av verifierings-attribut som deklareras med attributet parameter i offentliga egenskaper för cmdlet-klassen.</span><span class="sxs-lookup"><span data-stu-id="d13ef-107">These validation rules are defined by validation attributes that are declared with the Parameter attribute on public properties of the cmdlet class.</span></span>

<span data-ttu-id="d13ef-108">För att validera ett parameter argument använder PowerShell-körningen den information som anges av verifierings-attributen för att bekräfta värdet för parametern innan cmdleten körs.</span><span class="sxs-lookup"><span data-stu-id="d13ef-108">To validate a parameter argument, the PowerShell runtime uses the information provided by the validation attributes to confirm the value of the parameter before the cmdlet is run.</span></span>
<span data-ttu-id="d13ef-109">Om parameter indata inte är giltiga får användaren ett fel meddelande.</span><span class="sxs-lookup"><span data-stu-id="d13ef-109">If the parameter input is not valid, the user receives an error message.</span></span>
<span data-ttu-id="d13ef-110">Varje validerings parameter definierar en validerings regel som tillämpas av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d13ef-110">Each validation parameter defines a validation rule that is enforced by PowerShell.</span></span>

<span data-ttu-id="d13ef-111">PowerShell framtvingar verifierings reglerna baserat på följande attribut.</span><span class="sxs-lookup"><span data-stu-id="d13ef-111">PowerShell enforces the validation rules based on the following attributes.</span></span>

### <a name="validatecount"></a><span data-ttu-id="d13ef-112">ValidateCount</span><span class="sxs-lookup"><span data-stu-id="d13ef-112">ValidateCount</span></span>

<span data-ttu-id="d13ef-113">Anger det lägsta och högsta antalet argument som en parameter kan acceptera.</span><span class="sxs-lookup"><span data-stu-id="d13ef-113">Specifies the minimum and maximum number of arguments that a parameter can accept.</span></span>
<span data-ttu-id="d13ef-114">Mer information finns i [ValidateCount Attribute-deklaration](./validatecount-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="d13ef-114">For more information, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

### <a name="validatelength"></a><span data-ttu-id="d13ef-115">ValidateLength</span><span class="sxs-lookup"><span data-stu-id="d13ef-115">ValidateLength</span></span>

<span data-ttu-id="d13ef-116">Anger det lägsta och högsta antalet tecken i parameter argumentet.</span><span class="sxs-lookup"><span data-stu-id="d13ef-116">Specifies the minimum and maximum number of characters in the parameter argument.</span></span>
<span data-ttu-id="d13ef-117">Mer information finns i [ValidateLength Attribute-deklaration](./validatelength-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="d13ef-117">For more information, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

### <a name="validatepattern"></a><span data-ttu-id="d13ef-118">ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="d13ef-118">ValidatePattern</span></span>

<span data-ttu-id="d13ef-119">Anger ett reguljärt uttryck som validerar parameter argumentet.</span><span class="sxs-lookup"><span data-stu-id="d13ef-119">Specifies a regular expression that validates the parameter argument.</span></span>
<span data-ttu-id="d13ef-120">Mer information finns i [ValidatePattern Attribute-deklaration](./validatepattern-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="d13ef-120">For more information, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

### <a name="validaterange"></a><span data-ttu-id="d13ef-121">ValidateRange</span><span class="sxs-lookup"><span data-stu-id="d13ef-121">ValidateRange</span></span>

<span data-ttu-id="d13ef-122">Anger det lägsta och högsta värdet för parameter argumentet.</span><span class="sxs-lookup"><span data-stu-id="d13ef-122">Specifies the minimum and maximum values of the parameter argument.</span></span>
<span data-ttu-id="d13ef-123">Mer information finns i [ValidateRange Attribute-deklaration](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="d13ef-123">For more information, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

### <a name="validateset"></a><span data-ttu-id="d13ef-124">ValidateSet</span><span class="sxs-lookup"><span data-stu-id="d13ef-124">ValidateSet</span></span>

<span data-ttu-id="d13ef-125">Anger giltiga värden för parameter argumentet.</span><span class="sxs-lookup"><span data-stu-id="d13ef-125">Specifies the valid values for the parameter argument.</span></span>
<span data-ttu-id="d13ef-126">Mer information finns i [ValidateSet Attribute-deklaration](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="d13ef-126">For more information, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d13ef-127">Se även</span><span class="sxs-lookup"><span data-stu-id="d13ef-127">See Also</span></span>

[<span data-ttu-id="d13ef-128">Verifiera parameterindata</span><span class="sxs-lookup"><span data-stu-id="d13ef-128">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

[<span data-ttu-id="d13ef-129">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="d13ef-129">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
