---
title: Deklaration av ValidateLength attribut | Microsoft Docs
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
ms.openlocfilehash: 4d3cdccc0fe3e24b1221e41beef4821b613aab93
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855147"
---
# <a name="validatelength-attribute-declaration"></a><span data-ttu-id="3272b-102">Deklaration av attributet ValidateLength</span><span class="sxs-lookup"><span data-stu-id="3272b-102">ValidateLength Attribute Declaration</span></span>

<span data-ttu-id="3272b-103">Attributet ValidateLength anger minsta och högsta antalet tillåtna tecken för en cmdlet-argument för parametern.</span><span class="sxs-lookup"><span data-stu-id="3272b-103">The ValidateLength attribute specifies the minimum and maximum number of characters for a cmdlet parameter argument.</span></span> <span data-ttu-id="3272b-104">Det här attributet kan också användas i Windows PowerShell-funktioner.</span><span class="sxs-lookup"><span data-stu-id="3272b-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="3272b-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="3272b-105">Syntax</span></span>

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="3272b-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="3272b-106">Parameters</span></span>

<span data-ttu-id="3272b-107">`MinLength` ([System.Integer](/dotnet/api/System.Integer)) Required.</span><span class="sxs-lookup"><span data-stu-id="3272b-107">`MinLength` ([System.Integer](/dotnet/api/System.Integer)) Required.</span></span> <span data-ttu-id="3272b-108">Anger det minsta antalet tecken som tillåts.</span><span class="sxs-lookup"><span data-stu-id="3272b-108">Specifies the minimum number of characters allowed.</span></span>

<span data-ttu-id="3272b-109">`MaxLength` ([System.Integer](/dotnet/api/System.Integer)) Required.</span><span class="sxs-lookup"><span data-stu-id="3272b-109">`MaxLength` ([System.Integer](/dotnet/api/System.Integer)) Required.</span></span> <span data-ttu-id="3272b-110">Anger det maximala antalet tecken som tillåts.</span><span class="sxs-lookup"><span data-stu-id="3272b-110">Specifies the maximum number of characters allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="3272b-111">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="3272b-111">Remarks</span></span>

- <span data-ttu-id="3272b-112">Läs mer om hur du deklarera det här attributet [så deklarera indata valideringsregler](./how-to-validate-parameter-input.md).</span><span class="sxs-lookup"><span data-stu-id="3272b-112">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](./how-to-validate-parameter-input.md).</span></span>

- <span data-ttu-id="3272b-113">När det här attributet inte används, kan motsvarande Parameterargumentet vara av valfri längd.</span><span class="sxs-lookup"><span data-stu-id="3272b-113">When this attribute is not used, the corresponding parameter argument can be of any length.</span></span>

- <span data-ttu-id="3272b-114">Windows PowerShell-runtime genererar ett fel under följande förhållanden:</span><span class="sxs-lookup"><span data-stu-id="3272b-114">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="3272b-115">När värdet för den `MaxLength` attribut parameter är mindre än värdet för den `MinLength` attributet parameter.</span><span class="sxs-lookup"><span data-stu-id="3272b-115">When the value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

    - <span data-ttu-id="3272b-116">När den `MaxLength` attributet parametern anges till 0.</span><span class="sxs-lookup"><span data-stu-id="3272b-116">When the `MaxLength` attribute parameter is set to 0.</span></span>

    - <span data-ttu-id="3272b-117">När argumentet är inte en sträng.</span><span class="sxs-lookup"><span data-stu-id="3272b-117">When the argument is not a string.</span></span>

- <span data-ttu-id="3272b-118">Attributet ValidateLength definieras av den [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) klass.</span><span class="sxs-lookup"><span data-stu-id="3272b-118">The ValidateLength attribute is defined by the [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="3272b-119">Se även</span><span class="sxs-lookup"><span data-stu-id="3272b-119">See Also</span></span>

[<span data-ttu-id="3272b-120">System.Management.Automation.Validatelengthattribute</span><span class="sxs-lookup"><span data-stu-id="3272b-120">System.Management.Automation.Validatelengthattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[<span data-ttu-id="3272b-121">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3272b-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
