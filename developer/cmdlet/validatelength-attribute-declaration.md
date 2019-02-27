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
ms.openlocfilehash: 1e8364c78abba5272007019550ffcb2cedaf9fd0
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848820"
---
# <a name="validatelength-attribute-declaration"></a><span data-ttu-id="8046b-102">Deklaration av attributet ValidateLength</span><span class="sxs-lookup"><span data-stu-id="8046b-102">ValidateLength Attribute Declaration</span></span>

<span data-ttu-id="8046b-103">Attributet ValidateLength anger minsta och högsta antalet tillåtna tecken för en cmdlet-argument för parametern.</span><span class="sxs-lookup"><span data-stu-id="8046b-103">The ValidateLength attribute specifies the minimum and maximum number of characters for a cmdlet parameter argument.</span></span> <span data-ttu-id="8046b-104">Det här attributet kan också användas i Windows PowerShell-funktioner.</span><span class="sxs-lookup"><span data-stu-id="8046b-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="8046b-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="8046b-105">Syntax</span></span>

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="8046b-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="8046b-106">Parameters</span></span>

<span data-ttu-id="8046b-107">`MinLength` ([System.Integer](/dotnet/api/System.Integer)) Required.</span><span class="sxs-lookup"><span data-stu-id="8046b-107">`MinLength` ([System.Integer](/dotnet/api/System.Integer)) Required.</span></span> <span data-ttu-id="8046b-108">Anger det minsta antalet tecken som tillåts.</span><span class="sxs-lookup"><span data-stu-id="8046b-108">Specifies the minimum number of characters allowed.</span></span>

<span data-ttu-id="8046b-109">`MaxLength` ([System.Integer](/dotnet/api/System.Integer)) Required.</span><span class="sxs-lookup"><span data-stu-id="8046b-109">`MaxLength` ([System.Integer](/dotnet/api/System.Integer)) Required.</span></span> <span data-ttu-id="8046b-110">Anger det maximala antalet tecken som tillåts.</span><span class="sxs-lookup"><span data-stu-id="8046b-110">Specifies the maximum number of characters allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="8046b-111">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="8046b-111">Remarks</span></span>

- <span data-ttu-id="8046b-112">Läs mer om hur du deklarera det här attributet [så deklarera indata valideringsregler](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span><span class="sxs-lookup"><span data-stu-id="8046b-112">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span></span>
- <span data-ttu-id="8046b-113">Läs mer om hur du deklarera det här attributet [så deklarera indata valideringsregler](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span><span class="sxs-lookup"><span data-stu-id="8046b-113">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span></span>

- <span data-ttu-id="8046b-114">När det här attributet inte används, kan motsvarande Parameterargumentet vara av valfri längd.</span><span class="sxs-lookup"><span data-stu-id="8046b-114">When this attribute is not used, the corresponding parameter argument can be of any length.</span></span>

- <span data-ttu-id="8046b-115">Windows PowerShell-runtime genererar ett fel under följande förhållanden:</span><span class="sxs-lookup"><span data-stu-id="8046b-115">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="8046b-116">När värdet för den `MaxLength` attribut parameter är mindre än värdet för den `MinLength` attributet parameter.</span><span class="sxs-lookup"><span data-stu-id="8046b-116">When the value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

    - <span data-ttu-id="8046b-117">När den `MaxLength` attributet parametern anges till 0.</span><span class="sxs-lookup"><span data-stu-id="8046b-117">When the `MaxLength` attribute parameter is set to 0.</span></span>

    - <span data-ttu-id="8046b-118">När argumentet är inte en sträng.</span><span class="sxs-lookup"><span data-stu-id="8046b-118">When the argument is not a string.</span></span>

- <span data-ttu-id="8046b-119">Attributet ValidateLength definieras av den [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) klass.</span><span class="sxs-lookup"><span data-stu-id="8046b-119">The ValidateLength attribute is defined by the [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="8046b-120">Se även</span><span class="sxs-lookup"><span data-stu-id="8046b-120">See Also</span></span>

[<span data-ttu-id="8046b-121">System.Management.Automation.Validatelengthattribute</span><span class="sxs-lookup"><span data-stu-id="8046b-121">System.Management.Automation.Validatelengthattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[<span data-ttu-id="8046b-122">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="8046b-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
