---
title: ValidateLength-Attribute-deklaration | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateLength attribute, described
- attributes, ValidateLength
- ValidateLength attribute
ms.assetid: 82fe3a35-a94b-4bc1-ad9e-dfc5f1e788b3
caps.latest.revision: 13
ms.openlocfilehash: a25fa2410fcc6803563573596af1bc99052c3ffa
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359148"
---
# <a name="validatelength-attribute-declaration"></a><span data-ttu-id="7a270-102">Deklaration av attributet ValidateLength</span><span class="sxs-lookup"><span data-stu-id="7a270-102">ValidateLength Attribute Declaration</span></span>

<span data-ttu-id="7a270-103">Attributet ValidateLength anger det lägsta och högsta antalet tecken för ett cmdlet parameter argument.</span><span class="sxs-lookup"><span data-stu-id="7a270-103">The ValidateLength attribute specifies the minimum and maximum number of characters for a cmdlet parameter argument.</span></span> <span data-ttu-id="7a270-104">Det här attributet kan också användas av Windows PowerShell-funktioner.</span><span class="sxs-lookup"><span data-stu-id="7a270-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="7a270-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="7a270-105">Syntax</span></span>

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="7a270-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7a270-106">Parameters</span></span>

<span data-ttu-id="7a270-107">`MinLength` ([system. Int32](/dotnet/api/System.Int32)) krävs.</span><span class="sxs-lookup"><span data-stu-id="7a270-107">`MinLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="7a270-108">Anger det minsta antalet tecken som tillåts.</span><span class="sxs-lookup"><span data-stu-id="7a270-108">Specifies the minimum number of characters allowed.</span></span>

<span data-ttu-id="7a270-109">`MaxLength` ([system. Int32](/dotnet/api/System.Int32)) krävs.</span><span class="sxs-lookup"><span data-stu-id="7a270-109">`MaxLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="7a270-110">Anger det maximala antalet tecken som tillåts.</span><span class="sxs-lookup"><span data-stu-id="7a270-110">Specifies the maximum number of characters allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="7a270-111">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="7a270-111">Remarks</span></span>

- <span data-ttu-id="7a270-112">Mer information om hur du deklarerar det här attributet finns i [så här deklarerar du validerings regler för indata](./how-to-validate-parameter-input.md).</span><span class="sxs-lookup"><span data-stu-id="7a270-112">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](./how-to-validate-parameter-input.md).</span></span>

- <span data-ttu-id="7a270-113">Om det här attributet inte används kan motsvarande parameter argument vara en valfri längd.</span><span class="sxs-lookup"><span data-stu-id="7a270-113">When this attribute is not used, the corresponding parameter argument can be of any length.</span></span>

- <span data-ttu-id="7a270-114">Windows PowerShell-körningsmiljön genererar ett fel under följande förhållanden:</span><span class="sxs-lookup"><span data-stu-id="7a270-114">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="7a270-115">När värdet för attributet `MaxLength` är mindre än värdet för parametern `MinLength`.</span><span class="sxs-lookup"><span data-stu-id="7a270-115">When the value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

    - <span data-ttu-id="7a270-116">När parametern `MaxLength` anges till 0.</span><span class="sxs-lookup"><span data-stu-id="7a270-116">When the `MaxLength` attribute parameter is set to 0.</span></span>

    - <span data-ttu-id="7a270-117">Om argumentet inte är en sträng.</span><span class="sxs-lookup"><span data-stu-id="7a270-117">When the argument is not a string.</span></span>

- <span data-ttu-id="7a270-118">Attributet ValidateLength definieras av klassen [system. Management. Automation. Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) .</span><span class="sxs-lookup"><span data-stu-id="7a270-118">The ValidateLength attribute is defined by the [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="7a270-119">Se även</span><span class="sxs-lookup"><span data-stu-id="7a270-119">See Also</span></span>

[<span data-ttu-id="7a270-120">System. Management. Automation. Validatelengthattribute</span><span class="sxs-lookup"><span data-stu-id="7a270-120">System.Management.Automation.Validatelengthattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[<span data-ttu-id="7a270-121">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="7a270-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
