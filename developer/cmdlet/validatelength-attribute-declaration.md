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
ms.openlocfilehash: 3a4c5f279ce8587eeb5d583376ea3d2286210b83
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067169"
---
# <a name="validatelength-attribute-declaration"></a><span data-ttu-id="43076-102">Deklaration av attributet ValidateLength</span><span class="sxs-lookup"><span data-stu-id="43076-102">ValidateLength Attribute Declaration</span></span>

<span data-ttu-id="43076-103">Attributet ValidateLength anger minsta och högsta antalet tillåtna tecken för en cmdlet-argument för parametern.</span><span class="sxs-lookup"><span data-stu-id="43076-103">The ValidateLength attribute specifies the minimum and maximum number of characters for a cmdlet parameter argument.</span></span> <span data-ttu-id="43076-104">Det här attributet kan också användas i Windows PowerShell-funktioner.</span><span class="sxs-lookup"><span data-stu-id="43076-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="43076-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="43076-105">Syntax</span></span>

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="43076-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="43076-106">Parameters</span></span>

<span data-ttu-id="43076-107">`MinLength` ([System.Integer](/dotnet/api/System.Integer)) Required.</span><span class="sxs-lookup"><span data-stu-id="43076-107">`MinLength` ([System.Integer](/dotnet/api/System.Integer)) Required.</span></span> <span data-ttu-id="43076-108">Anger det minsta antalet tecken som tillåts.</span><span class="sxs-lookup"><span data-stu-id="43076-108">Specifies the minimum number of characters allowed.</span></span>

<span data-ttu-id="43076-109">`MaxLength` ([System.Integer](/dotnet/api/System.Integer)) Required.</span><span class="sxs-lookup"><span data-stu-id="43076-109">`MaxLength` ([System.Integer](/dotnet/api/System.Integer)) Required.</span></span> <span data-ttu-id="43076-110">Anger det maximala antalet tecken som tillåts.</span><span class="sxs-lookup"><span data-stu-id="43076-110">Specifies the maximum number of characters allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="43076-111">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="43076-111">Remarks</span></span>

- <span data-ttu-id="43076-112">Läs mer om hur du deklarera det här attributet [så deklarera indata valideringsregler](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span><span class="sxs-lookup"><span data-stu-id="43076-112">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span></span>

- <span data-ttu-id="43076-113">När det här attributet inte används, kan motsvarande Parameterargumentet vara av valfri längd.</span><span class="sxs-lookup"><span data-stu-id="43076-113">When this attribute is not used, the corresponding parameter argument can be of any length.</span></span>

- <span data-ttu-id="43076-114">Windows PowerShell-runtime genererar ett fel under följande förhållanden:</span><span class="sxs-lookup"><span data-stu-id="43076-114">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="43076-115">När värdet för den `MaxLength` attribut parameter är mindre än värdet för den `MinLength` attributet parameter.</span><span class="sxs-lookup"><span data-stu-id="43076-115">When the value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

    - <span data-ttu-id="43076-116">När den `MaxLength` attributet parametern anges till 0.</span><span class="sxs-lookup"><span data-stu-id="43076-116">When the `MaxLength` attribute parameter is set to 0.</span></span>

    - <span data-ttu-id="43076-117">När argumentet är inte en sträng.</span><span class="sxs-lookup"><span data-stu-id="43076-117">When the argument is not a string.</span></span>

- <span data-ttu-id="43076-118">Attributet ValidateLength definieras av den [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) klass.</span><span class="sxs-lookup"><span data-stu-id="43076-118">The ValidateLength attribute is defined by the [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="43076-119">Se även</span><span class="sxs-lookup"><span data-stu-id="43076-119">See Also</span></span>

[<span data-ttu-id="43076-120">System.Management.Automation.Validatelengthattribute</span><span class="sxs-lookup"><span data-stu-id="43076-120">System.Management.Automation.Validatelengthattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[<span data-ttu-id="43076-121">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="43076-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
