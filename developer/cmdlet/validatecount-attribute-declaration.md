---
title: Deklaration av ValidateCount attribut | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateCount
- ValidateCount attribute, described
- ValidateCount attribute
ms.assetid: 516af1ef-2c2e-408d-84bc-865f5bccf761
caps.latest.revision: 11
ms.openlocfilehash: 1a7b5ea340fe5212d003c97a9017278d6c631355
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849023"
---
# <a name="validatecount-attribute-declaration"></a><span data-ttu-id="9f988-102">Deklaration av attributet ValidateCount</span><span class="sxs-lookup"><span data-stu-id="9f988-102">ValidateCount Attribute Declaration</span></span>

<span data-ttu-id="9f988-103">Attributet ValidateCount anger minsta och största antalet argument som tillåts för en cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="9f988-103">The ValidateCount attribute specifies the minimum and maximum number of arguments allowed for a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="9f988-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="9f988-104">Syntax</span></span>

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="9f988-105">Parametrar</span><span class="sxs-lookup"><span data-stu-id="9f988-105">Parameters</span></span>

<span data-ttu-id="9f988-106">`MinLength` ([System.Int32](/dotnet/api/System.Int32)) krävs.</span><span class="sxs-lookup"><span data-stu-id="9f988-106">`MinLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="9f988-107">Anger det minsta antalet argument.</span><span class="sxs-lookup"><span data-stu-id="9f988-107">Specifies the minimum number of arguments.</span></span>

<span data-ttu-id="9f988-108">`MaxLength`([System.Int32](/dotnet/api/System.Int32)) krävs.</span><span class="sxs-lookup"><span data-stu-id="9f988-108">`MaxLength`([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="9f988-109">Anger det maximala antalet argument.</span><span class="sxs-lookup"><span data-stu-id="9f988-109">Specifies the maximum number of arguments.</span></span>

## <a name="remarks"></a><span data-ttu-id="9f988-110">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="9f988-110">Remarks</span></span>

- <span data-ttu-id="9f988-111">Läs mer om hur du deklarera det här attributet [så deklarera indata valideringsregler](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span><span class="sxs-lookup"><span data-stu-id="9f988-111">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span></span>

- <span data-ttu-id="9f988-112">När det här attributet inte har anropats kan motsvarande cmdlet-parameter ha valfritt antal argument.</span><span class="sxs-lookup"><span data-stu-id="9f988-112">When this attribute is not invoked, the corresponding cmdlet parameter can have any number of arguments.</span></span>

- <span data-ttu-id="9f988-113">Windows PowerShell-runtime genererar ett fel under följande förhållanden:</span><span class="sxs-lookup"><span data-stu-id="9f988-113">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="9f988-114">Den `MinLength` och `MaxLength` attributet parametrar inte är av typen [System.Int32](/dotnet/api/System.Int32).</span><span class="sxs-lookup"><span data-stu-id="9f988-114">The `MinLength` and `MaxLength` attribute parameters are not of type [System.Int32](/dotnet/api/System.Int32).</span></span>

    - <span data-ttu-id="9f988-115">Värdet för den `MaxLength` attribut parameter är mindre än värdet för den `MinLength` attributet parameter.</span><span class="sxs-lookup"><span data-stu-id="9f988-115">The value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

- <span data-ttu-id="9f988-116">Attributet ValidateCount definieras av den [System.Management.Automation.Validatecount](/dotnet/api/System.Management.Automation.ValidateCount) klass.</span><span class="sxs-lookup"><span data-stu-id="9f988-116">The ValidateCount attribute is defined by the [System.Management.Automation.Validatecount](/dotnet/api/System.Management.Automation.ValidateCount) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="9f988-117">Se även</span><span class="sxs-lookup"><span data-stu-id="9f988-117">See Also</span></span>

[<span data-ttu-id="9f988-118">System.Management.Automation.Validatecount</span><span class="sxs-lookup"><span data-stu-id="9f988-118">System.Management.Automation.Validatecount</span></span>](/dotnet/api/System.Management.Automation.ValidateCount)

[<span data-ttu-id="9f988-119">Hur du deklarera verifiering av indata-regler</span><span class="sxs-lookup"><span data-stu-id="9f988-119">How to Declare Input Validation Rules</span></span>](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b)

[<span data-ttu-id="9f988-120">Hur du deklarera verifiering av indata-regler</span><span class="sxs-lookup"><span data-stu-id="9f988-120">How to Declare Input Validation Rules</span></span>](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b)

[<span data-ttu-id="9f988-121">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="9f988-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
