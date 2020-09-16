---
title: ValidateRange-Attribute-deklaration | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- ValidateRange, described
- ValidateRange attribute
- attributes, ValidateRange
ms.openlocfilehash: 9aeaa6f03c170389ff61a058b505dbcf74df6958
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787792"
---
# <a name="validaterange-attribute-declaration"></a><span data-ttu-id="cda36-102">Deklaration av attributet ValidateRange</span><span class="sxs-lookup"><span data-stu-id="cda36-102">ValidateRange Attribute Declaration</span></span>

<span data-ttu-id="cda36-103">Attributet ValidateRange anger det lägsta och högsta värdet (intervallet) för argumentet cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="cda36-103">The ValidateRange attribute specifies the minimum and maximum values (the range) for the cmdlet parameter argument.</span></span> <span data-ttu-id="cda36-104">Det här attributet kan också användas av Windows PowerShell-funktioner.</span><span class="sxs-lookup"><span data-stu-id="cda36-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="cda36-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="cda36-105">Syntax</span></span>

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a><span data-ttu-id="cda36-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="cda36-106">Parameters</span></span>

<span data-ttu-id="cda36-107">`MinRange` ([System. Object](/dotnet/api/system.object)) krävs.</span><span class="sxs-lookup"><span data-stu-id="cda36-107">`MinRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="cda36-108">Anger det lägsta tillåtna värdet.</span><span class="sxs-lookup"><span data-stu-id="cda36-108">Specifies the minimum value allowed.</span></span>

<span data-ttu-id="cda36-109">`MaxRange` ([System. Object](/dotnet/api/system.object)) krävs.</span><span class="sxs-lookup"><span data-stu-id="cda36-109">`MaxRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="cda36-110">Anger det högsta tillåtna värdet.</span><span class="sxs-lookup"><span data-stu-id="cda36-110">Specifies the maximum value allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="cda36-111">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="cda36-111">Remarks</span></span>

- <span data-ttu-id="cda36-112">Windows PowerShell-körningsmiljön genererar ett konstruktions fel när värdet för `MinRange` parametern är större än värdet för `MaxRange` parametern.</span><span class="sxs-lookup"><span data-stu-id="cda36-112">The Windows PowerShell runtime throws a construction error when the value of the `MinRange` parameter is greater than the value of the `MaxRange` parameter.</span></span>

- <span data-ttu-id="cda36-113">Windows PowerShell-körningsmiljön genererar ett verifierings fel under följande förhållanden:</span><span class="sxs-lookup"><span data-stu-id="cda36-113">The Windows PowerShell runtime throws a validation error under the following conditions:</span></span>

  - <span data-ttu-id="cda36-114">När värdet för argumentet är mindre än `MinRange` gränsen eller större än `MaxRange` gränsen.</span><span class="sxs-lookup"><span data-stu-id="cda36-114">When the value of the argument is less than the `MinRange` limit or greater than the `MaxRange` limit.</span></span>

  - <span data-ttu-id="cda36-115">Om argumentet inte är av samma typ som `MinRange` `MaxRange` parametrarna och.</span><span class="sxs-lookup"><span data-stu-id="cda36-115">When the argument is not of the same type as the `MinRange` and the `MaxRange` parameters.</span></span>

- <span data-ttu-id="cda36-116">Attributet ValidateRange definieras av klassen [system. Management. Automation. Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) .</span><span class="sxs-lookup"><span data-stu-id="cda36-116">The ValidateRange attribute is defined by the [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="cda36-117">Se även</span><span class="sxs-lookup"><span data-stu-id="cda36-117">See Also</span></span>

[<span data-ttu-id="cda36-118">System. Management. Automation. Validaterangeattribute</span><span class="sxs-lookup"><span data-stu-id="cda36-118">System.Management.Automation.Validaterangeattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[<span data-ttu-id="cda36-119">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="cda36-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
