---
title: ValidateLength-Attribute-deklaration | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- ValidateLength attribute, described
- attributes, ValidateLength
- ValidateLength attribute
ms.openlocfilehash: 7145dde55e79eeea6e3ceb91dfc1c93043a8857c
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786313"
---
# <a name="validatelength-attribute-declaration"></a><span data-ttu-id="ef57e-102">Deklaration av attributet ValidateLength</span><span class="sxs-lookup"><span data-stu-id="ef57e-102">ValidateLength Attribute Declaration</span></span>

<span data-ttu-id="ef57e-103">Attributet ValidateLength anger det lägsta och högsta antalet tecken för ett cmdlet parameter argument.</span><span class="sxs-lookup"><span data-stu-id="ef57e-103">The ValidateLength attribute specifies the minimum and maximum number of characters for a cmdlet parameter argument.</span></span> <span data-ttu-id="ef57e-104">Det här attributet kan också användas av Windows PowerShell-funktioner.</span><span class="sxs-lookup"><span data-stu-id="ef57e-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="ef57e-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="ef57e-105">Syntax</span></span>

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="ef57e-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ef57e-106">Parameters</span></span>

<span data-ttu-id="ef57e-107">`MinLength` ([System. Int32](/dotnet/api/System.Int32)) krävs.</span><span class="sxs-lookup"><span data-stu-id="ef57e-107">`MinLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="ef57e-108">Anger det minsta antalet tecken som tillåts.</span><span class="sxs-lookup"><span data-stu-id="ef57e-108">Specifies the minimum number of characters allowed.</span></span>

<span data-ttu-id="ef57e-109">`MaxLength` ([System. Int32](/dotnet/api/System.Int32)) krävs.</span><span class="sxs-lookup"><span data-stu-id="ef57e-109">`MaxLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="ef57e-110">Anger det maximala antalet tecken som tillåts.</span><span class="sxs-lookup"><span data-stu-id="ef57e-110">Specifies the maximum number of characters allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="ef57e-111">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="ef57e-111">Remarks</span></span>

- <span data-ttu-id="ef57e-112">Mer information om hur du deklarerar det här attributet finns i [så här deklarerar du validerings regler för indata](./how-to-validate-parameter-input.md).</span><span class="sxs-lookup"><span data-stu-id="ef57e-112">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](./how-to-validate-parameter-input.md).</span></span>

- <span data-ttu-id="ef57e-113">Om det här attributet inte används kan motsvarande parameter argument vara en valfri längd.</span><span class="sxs-lookup"><span data-stu-id="ef57e-113">When this attribute is not used, the corresponding parameter argument can be of any length.</span></span>

- <span data-ttu-id="ef57e-114">Windows PowerShell-körningsmiljön genererar ett fel under följande förhållanden:</span><span class="sxs-lookup"><span data-stu-id="ef57e-114">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

  - <span data-ttu-id="ef57e-115">När värdet för `MaxLength` attributet Attribute är mindre än värdet för `MinLength` parametern Attribute.</span><span class="sxs-lookup"><span data-stu-id="ef57e-115">When the value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

  - <span data-ttu-id="ef57e-116">När `MaxLength` parametern Attribute anges till 0.</span><span class="sxs-lookup"><span data-stu-id="ef57e-116">When the `MaxLength` attribute parameter is set to 0.</span></span>

  - <span data-ttu-id="ef57e-117">Om argumentet inte är en sträng.</span><span class="sxs-lookup"><span data-stu-id="ef57e-117">When the argument is not a string.</span></span>

- <span data-ttu-id="ef57e-118">Attributet ValidateLength definieras av klassen [system. Management. Automation. Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) .</span><span class="sxs-lookup"><span data-stu-id="ef57e-118">The ValidateLength attribute is defined by the [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="ef57e-119">Se även</span><span class="sxs-lookup"><span data-stu-id="ef57e-119">See Also</span></span>

[<span data-ttu-id="ef57e-120">System. Management. Automation. Validatelengthattribute</span><span class="sxs-lookup"><span data-stu-id="ef57e-120">System.Management.Automation.Validatelengthattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[<span data-ttu-id="ef57e-121">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="ef57e-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
