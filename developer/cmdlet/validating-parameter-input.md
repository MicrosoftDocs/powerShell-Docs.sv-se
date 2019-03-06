---
title: Verifierar indata för parametern | Microsoft Docs
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
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429847"
---
# <a name="validating-parameter-input"></a><span data-ttu-id="b4d62-102">Verifiera parameterindata</span><span class="sxs-lookup"><span data-stu-id="b4d62-102">Validating Parameter Input</span></span>

<span data-ttu-id="b4d62-103">PowerShell kan verifiera argumenten som skickades till cmdlet-parametrarna på flera olika sätt.</span><span class="sxs-lookup"><span data-stu-id="b4d62-103">PowerShell can validate the arguments passed to cmdlet parameters in several ways.</span></span>
<span data-ttu-id="b4d62-104">PowerShell kan verifiera längden och intervallet mönstret för tecken på argumentet.</span><span class="sxs-lookup"><span data-stu-id="b4d62-104">PowerShell can validate the length, the range, and the pattern of the characters of the argument.</span></span>
<span data-ttu-id="b4d62-105">Det kan verifiera antalet argument tillgängliga (antal).</span><span class="sxs-lookup"><span data-stu-id="b4d62-105">It can validate the number of arguments available (the count).</span></span>
<span data-ttu-id="b4d62-106">Dessa valideringsregler definieras av verifiering attribut som deklareras med parametern-attributet på offentliga egenskaper för cmdlet-klassen.</span><span class="sxs-lookup"><span data-stu-id="b4d62-106">These validation rules are defined by validation attributes that are declared with the Parameter attribute on public properties of the cmdlet class.</span></span>

<span data-ttu-id="b4d62-107">För att verifiera en Parameterargumentet använder PowerShell-runtime information som tillhandahålls av attributen verifiering för att bekräfta värdet för parametern innan cmdleten körs.</span><span class="sxs-lookup"><span data-stu-id="b4d62-107">To validate a parameter argument, the PowerShell runtime uses the information provided by the validation attributes to confirm the value of the parameter before the cmdlet is run.</span></span>
<span data-ttu-id="b4d62-108">Om parametern-indata inte är giltiga, får användaren ett felmeddelande.</span><span class="sxs-lookup"><span data-stu-id="b4d62-108">If the parameter input is not valid, the user receives an error message.</span></span>
<span data-ttu-id="b4d62-109">Varje parameter för verifiering definierar en verifieringsregel som påtvingas av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b4d62-109">Each validation parameter defines a validation rule that is enforced by PowerShell.</span></span>

<span data-ttu-id="b4d62-110">PowerShell framtvingar valideringsregler baserat på följande attribut.</span><span class="sxs-lookup"><span data-stu-id="b4d62-110">PowerShell enforces the validation rules based on the following attributes.</span></span>

### <a name="validatecount"></a><span data-ttu-id="b4d62-111">ValidateCount</span><span class="sxs-lookup"><span data-stu-id="b4d62-111">ValidateCount</span></span>

<span data-ttu-id="b4d62-112">Anger minsta och största antalet argument som en parameter kan godkänna.</span><span class="sxs-lookup"><span data-stu-id="b4d62-112">Specifies the minimum and maximum number of arguments that a parameter can accept.</span></span>
<span data-ttu-id="b4d62-113">Mer information finns i [ValidateCount attributet deklarationen](./validatecount-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="b4d62-113">For more information, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

### <a name="validatelength"></a><span data-ttu-id="b4d62-114">ValidateLength</span><span class="sxs-lookup"><span data-stu-id="b4d62-114">ValidateLength</span></span>

<span data-ttu-id="b4d62-115">Anger det minsta och högsta antalet tecken i Parameterargumentet.</span><span class="sxs-lookup"><span data-stu-id="b4d62-115">Specifies the minimum and maximum number of characters in the parameter argument.</span></span>
<span data-ttu-id="b4d62-116">Mer information finns i [ValidateLength attributet deklarationen](./validatelength-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="b4d62-116">For more information, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

### <a name="validatepattern"></a><span data-ttu-id="b4d62-117">ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="b4d62-117">ValidatePattern</span></span>

<span data-ttu-id="b4d62-118">Anger ett reguljärt uttryck som validerar Parameterargumentet.</span><span class="sxs-lookup"><span data-stu-id="b4d62-118">Specifies a regular expression that validates the parameter argument.</span></span>
<span data-ttu-id="b4d62-119">Mer information finns i [ValidatePattern attributet deklarationen](./validatepattern-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="b4d62-119">For more information, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

### <a name="validaterange"></a><span data-ttu-id="b4d62-120">ValidateRange</span><span class="sxs-lookup"><span data-stu-id="b4d62-120">ValidateRange</span></span>

<span data-ttu-id="b4d62-121">Anger de lägsta och högsta värden för Parameterargumentet.</span><span class="sxs-lookup"><span data-stu-id="b4d62-121">Specifies the minimum and maximum values of the parameter argument.</span></span>
<span data-ttu-id="b4d62-122">Mer information finns i [ValidateRange attributet deklarationen](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="b4d62-122">For more information, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

### <a name="validateset"></a><span data-ttu-id="b4d62-123">ValidateSet</span><span class="sxs-lookup"><span data-stu-id="b4d62-123">ValidateSet</span></span>

<span data-ttu-id="b4d62-124">Anger de giltiga värdena för Parameterargumentet.</span><span class="sxs-lookup"><span data-stu-id="b4d62-124">Specifies the valid values for the parameter argument.</span></span>
<span data-ttu-id="b4d62-125">Mer information finns i [ValidateSet attributet deklarationen](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="b4d62-125">For more information, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b4d62-126">Se även</span><span class="sxs-lookup"><span data-stu-id="b4d62-126">See Also</span></span>

[<span data-ttu-id="b4d62-127">Hur du verifierar indata för parametern</span><span class="sxs-lookup"><span data-stu-id="b4d62-127">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

[<span data-ttu-id="b4d62-128">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b4d62-128">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
