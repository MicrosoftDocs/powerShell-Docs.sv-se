---
ms.date: 09/13/2016
ms.topic: reference
title: Deklaration av attributet ValidateLength
description: Deklaration av attributet ValidateLength
ms.openlocfilehash: b35fe24c6fc44aaca6a39d819d6e3fc2d8a2cade
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92646190"
---
# <a name="validatelength-attribute-declaration"></a><span data-ttu-id="3b701-103">Deklaration av attributet ValidateLength</span><span class="sxs-lookup"><span data-stu-id="3b701-103">ValidateLength Attribute Declaration</span></span>

<span data-ttu-id="3b701-104">Attributet ValidateLength anger det lägsta och högsta antalet tecken för ett cmdlet parameter argument.</span><span class="sxs-lookup"><span data-stu-id="3b701-104">The ValidateLength attribute specifies the minimum and maximum number of characters for a cmdlet parameter argument.</span></span> <span data-ttu-id="3b701-105">Det här attributet kan också användas av Windows PowerShell-funktioner.</span><span class="sxs-lookup"><span data-stu-id="3b701-105">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="3b701-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="3b701-106">Syntax</span></span>

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="3b701-107">Parametrar</span><span class="sxs-lookup"><span data-stu-id="3b701-107">Parameters</span></span>

<span data-ttu-id="3b701-108">`MinLength` ([System. Int32](/dotnet/api/System.Int32)) krävs.</span><span class="sxs-lookup"><span data-stu-id="3b701-108">`MinLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="3b701-109">Anger det minsta antalet tecken som tillåts.</span><span class="sxs-lookup"><span data-stu-id="3b701-109">Specifies the minimum number of characters allowed.</span></span>

<span data-ttu-id="3b701-110">`MaxLength` ([System. Int32](/dotnet/api/System.Int32)) krävs.</span><span class="sxs-lookup"><span data-stu-id="3b701-110">`MaxLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="3b701-111">Anger det maximala antalet tecken som tillåts.</span><span class="sxs-lookup"><span data-stu-id="3b701-111">Specifies the maximum number of characters allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="3b701-112">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="3b701-112">Remarks</span></span>

- <span data-ttu-id="3b701-113">Mer information om hur du deklarerar det här attributet finns i [så här deklarerar du validerings regler för indata](./how-to-validate-parameter-input.md).</span><span class="sxs-lookup"><span data-stu-id="3b701-113">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](./how-to-validate-parameter-input.md).</span></span>

- <span data-ttu-id="3b701-114">Om det här attributet inte används kan motsvarande parameter argument vara en valfri längd.</span><span class="sxs-lookup"><span data-stu-id="3b701-114">When this attribute is not used, the corresponding parameter argument can be of any length.</span></span>

- <span data-ttu-id="3b701-115">Windows PowerShell-körningsmiljön genererar ett fel under följande förhållanden:</span><span class="sxs-lookup"><span data-stu-id="3b701-115">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

  - <span data-ttu-id="3b701-116">När värdet för `MaxLength` attributet Attribute är mindre än värdet för `MinLength` parametern Attribute.</span><span class="sxs-lookup"><span data-stu-id="3b701-116">When the value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

  - <span data-ttu-id="3b701-117">När `MaxLength` parametern Attribute anges till 0.</span><span class="sxs-lookup"><span data-stu-id="3b701-117">When the `MaxLength` attribute parameter is set to 0.</span></span>

  - <span data-ttu-id="3b701-118">Om argumentet inte är en sträng.</span><span class="sxs-lookup"><span data-stu-id="3b701-118">When the argument is not a string.</span></span>

- <span data-ttu-id="3b701-119">Attributet ValidateLength definieras av klassen [system. Management. Automation. Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) .</span><span class="sxs-lookup"><span data-stu-id="3b701-119">The ValidateLength attribute is defined by the [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="3b701-120">Se även</span><span class="sxs-lookup"><span data-stu-id="3b701-120">See Also</span></span>

[<span data-ttu-id="3b701-121">System. Management. Automation. Validatelengthattribute</span><span class="sxs-lookup"><span data-stu-id="3b701-121">System.Management.Automation.Validatelengthattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[<span data-ttu-id="3b701-122">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="3b701-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
