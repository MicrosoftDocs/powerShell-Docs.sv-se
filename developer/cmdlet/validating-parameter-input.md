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
ms.openlocfilehash: f7e5d4fb2f89bd6bc7036fdcff8f38e017d5d0e4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848806"
---
# <a name="validating-parameter-input"></a><span data-ttu-id="be025-102">Verifiera parameterindata</span><span class="sxs-lookup"><span data-stu-id="be025-102">Validating Parameter Input</span></span>

<span data-ttu-id="be025-103">Windows PowerShell kan verifiera argumenten som skickades till cmdlet-parametrarna på flera olika sätt.</span><span class="sxs-lookup"><span data-stu-id="be025-103">Windows PowerShell can validate the arguments passed to cmdlet parameters in several ways.</span></span> <span data-ttu-id="be025-104">Windows PowerShell kan verifiera längden och intervallet mönstret för tecken på argumentet.</span><span class="sxs-lookup"><span data-stu-id="be025-104">Windows PowerShell can validate the length, the range, and the pattern of the characters of the argument.</span></span> <span data-ttu-id="be025-105">Det kan verifiera antalet argument tillgängliga (antal).</span><span class="sxs-lookup"><span data-stu-id="be025-105">It can validate the number of arguments available (the count).</span></span> <span data-ttu-id="be025-106">Dessa valideringsregler definieras av verifiering attribut som deklareras med parametern-attributet på offentliga egenskaper för cmdlet-klassen.</span><span class="sxs-lookup"><span data-stu-id="be025-106">These validation rules are defined by validation attributes that are declared with the Parameter attribute on public properties of the cmdlet class.</span></span>

<span data-ttu-id="be025-107">För att verifiera ett argument för parametern, använder Windows PowerShell-runtime information som tillhandahålls av attributen verifiering för att bekräfta värdet för parametern innan cmdleten körs.</span><span class="sxs-lookup"><span data-stu-id="be025-107">To validate a parameter argument, the Windows PowerShell runtime uses the information provided by the validation attributes to confirm the value of the parameter before the cmdlet is run.</span></span> <span data-ttu-id="be025-108">Om parametern-indata inte är giltiga, får användaren ett felmeddelande.</span><span class="sxs-lookup"><span data-stu-id="be025-108">If the parameter input is not valid, the user receives an error message.</span></span> <span data-ttu-id="be025-109">Varje parameter för verifiering definierar en valideringsregel som används av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="be025-109">Each validation parameter defines a validation rule that is enforced by Windows PowerShell.</span></span>

<span data-ttu-id="be025-110">Windows PowerShell framtvingar valideringsregler baserat på följande attribut.</span><span class="sxs-lookup"><span data-stu-id="be025-110">Windows PowerShell enforces the validation rules based on the following attributes.</span></span>

<span data-ttu-id="be025-111">ValidateCount anger minsta och största antalet argument som en parameter kan godkänna.</span><span class="sxs-lookup"><span data-stu-id="be025-111">ValidateCount Specifies the minimum and maximum number of arguments that a parameter can accept.</span></span> <span data-ttu-id="be025-112">Läs mer om vilken syntax som används för att deklarera det här attributet [ValidateCount attributet deklarationen](./validatecount-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="be025-112">For more information about the syntax used to declare this attribute, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

<span data-ttu-id="be025-113">ValidateLength anger det minsta och högsta antalet tecken i Parameterargumentet.</span><span class="sxs-lookup"><span data-stu-id="be025-113">ValidateLength Specifies the minimum and maximum number of characters in the parameter argument.</span></span> <span data-ttu-id="be025-114">Läs mer om vilken syntax som används för att deklarera det här attributet [ValidateLength attributet deklarationen](./validatelength-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="be025-114">For more information about the syntax used to declare this attribute, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

<span data-ttu-id="be025-115">ValidatePattern anger ett reguljärt uttryck som validerar Parameterargumentet.</span><span class="sxs-lookup"><span data-stu-id="be025-115">ValidatePattern Specifies a regular expression that validates the parameter argument.</span></span> <span data-ttu-id="be025-116">Läs mer om vilken syntax som används för att deklarera det här attributet [ValidatePattern attributet deklarationen](./validatepattern-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="be025-116">For more information about the syntax used to declare this attribute, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

<span data-ttu-id="be025-117">ValidateRange anger minsta och högsta värden för Parameterargumentet.</span><span class="sxs-lookup"><span data-stu-id="be025-117">ValidateRange Specifies the minimum and maximum values of the parameter argument.</span></span> <span data-ttu-id="be025-118">Läs mer om vilken syntax som används för att deklarera det här attributet [ValidateRange attributet deklarationen](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="be025-118">For more information about the syntax used to declare this attribute, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

<span data-ttu-id="be025-119">ValidateSet anger giltiga värden för Parameterargumentet.</span><span class="sxs-lookup"><span data-stu-id="be025-119">ValidateSet Specifies the valid values for the parameter argument.</span></span> <span data-ttu-id="be025-120">Läs mer om vilken syntax som används för att deklarera det här attributet [ValidateSet attributet deklarationen](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="be025-120">For more information about the syntax used to declare this attribute, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="be025-121">Se även</span><span class="sxs-lookup"><span data-stu-id="be025-121">See Also</span></span>

[<span data-ttu-id="be025-122">Hur du verifierar indata för parametern</span><span class="sxs-lookup"><span data-stu-id="be025-122">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

[<span data-ttu-id="be025-123">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="be025-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
