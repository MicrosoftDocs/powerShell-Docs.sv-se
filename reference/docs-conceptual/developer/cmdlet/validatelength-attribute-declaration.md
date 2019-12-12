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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359148"
---
# <a name="validatelength-attribute-declaration"></a><span data-ttu-id="73d0f-102">Deklaration av attributet ValidateLength</span><span class="sxs-lookup"><span data-stu-id="73d0f-102">ValidateLength Attribute Declaration</span></span>

<span data-ttu-id="73d0f-103">Attributet ValidateLength anger det lägsta och högsta antalet tecken för ett cmdlet parameter argument.</span><span class="sxs-lookup"><span data-stu-id="73d0f-103">The ValidateLength attribute specifies the minimum and maximum number of characters for a cmdlet parameter argument.</span></span> <span data-ttu-id="73d0f-104">Det här attributet kan också användas av Windows PowerShell-funktioner.</span><span class="sxs-lookup"><span data-stu-id="73d0f-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="73d0f-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="73d0f-105">Syntax</span></span>

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="73d0f-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="73d0f-106">Parameters</span></span>

<span data-ttu-id="73d0f-107">`MinLength` ([system. Int32](/dotnet/api/System.Int32)) krävs.</span><span class="sxs-lookup"><span data-stu-id="73d0f-107">`MinLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="73d0f-108">Anger det minsta antalet tecken som tillåts.</span><span class="sxs-lookup"><span data-stu-id="73d0f-108">Specifies the minimum number of characters allowed.</span></span>

<span data-ttu-id="73d0f-109">`MaxLength` ([system. Int32](/dotnet/api/System.Int32)) krävs.</span><span class="sxs-lookup"><span data-stu-id="73d0f-109">`MaxLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="73d0f-110">Anger det maximala antalet tecken som tillåts.</span><span class="sxs-lookup"><span data-stu-id="73d0f-110">Specifies the maximum number of characters allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="73d0f-111">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="73d0f-111">Remarks</span></span>

- <span data-ttu-id="73d0f-112">Mer information om hur du deklarerar det här attributet finns i [så här deklarerar du validerings regler för indata](./how-to-validate-parameter-input.md).</span><span class="sxs-lookup"><span data-stu-id="73d0f-112">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](./how-to-validate-parameter-input.md).</span></span>

- <span data-ttu-id="73d0f-113">Om det här attributet inte används kan motsvarande parameter argument vara en valfri längd.</span><span class="sxs-lookup"><span data-stu-id="73d0f-113">When this attribute is not used, the corresponding parameter argument can be of any length.</span></span>

- <span data-ttu-id="73d0f-114">Windows PowerShell-körningsmiljön genererar ett fel under följande förhållanden:</span><span class="sxs-lookup"><span data-stu-id="73d0f-114">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="73d0f-115">När värdet för parametern `MaxLength` attribut är mindre än värdet för parametern `MinLength` attribut.</span><span class="sxs-lookup"><span data-stu-id="73d0f-115">When the value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

    - <span data-ttu-id="73d0f-116">När parametern `MaxLength` attribut anges till 0.</span><span class="sxs-lookup"><span data-stu-id="73d0f-116">When the `MaxLength` attribute parameter is set to 0.</span></span>

    - <span data-ttu-id="73d0f-117">Om argumentet inte är en sträng.</span><span class="sxs-lookup"><span data-stu-id="73d0f-117">When the argument is not a string.</span></span>

- <span data-ttu-id="73d0f-118">Attributet ValidateLength definieras av klassen [system. Management. Automation. Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) .</span><span class="sxs-lookup"><span data-stu-id="73d0f-118">The ValidateLength attribute is defined by the [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="73d0f-119">Se även</span><span class="sxs-lookup"><span data-stu-id="73d0f-119">See Also</span></span>

[<span data-ttu-id="73d0f-120">System. Management. Automation. Validatelengthattribute</span><span class="sxs-lookup"><span data-stu-id="73d0f-120">System.Management.Automation.Validatelengthattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[<span data-ttu-id="73d0f-121">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="73d0f-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
