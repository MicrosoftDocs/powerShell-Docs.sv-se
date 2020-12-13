---
ms.date: 09/13/2016
ms.topic: reference
title: Deklaration av attributet ValidateRange
description: Deklaration av attributet ValidateRange
ms.openlocfilehash: 1fec9d1bd36cd21b7f0f23bf6d72338d276dce91
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660597"
---
# <a name="validaterange-attribute-declaration"></a><span data-ttu-id="8ccc4-103">Deklaration av attributet ValidateRange</span><span class="sxs-lookup"><span data-stu-id="8ccc4-103">ValidateRange Attribute Declaration</span></span>

<span data-ttu-id="8ccc4-104">Attributet ValidateRange anger det lägsta och högsta värdet (intervallet) för argumentet cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="8ccc4-104">The ValidateRange attribute specifies the minimum and maximum values (the range) for the cmdlet parameter argument.</span></span> <span data-ttu-id="8ccc4-105">Det här attributet kan också användas av Windows PowerShell-funktioner.</span><span class="sxs-lookup"><span data-stu-id="8ccc4-105">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="8ccc4-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="8ccc4-106">Syntax</span></span>

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a><span data-ttu-id="8ccc4-107">Parametrar</span><span class="sxs-lookup"><span data-stu-id="8ccc4-107">Parameters</span></span>

<span data-ttu-id="8ccc4-108">`MinRange` ([System. Object](/dotnet/api/system.object)) krävs.</span><span class="sxs-lookup"><span data-stu-id="8ccc4-108">`MinRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="8ccc4-109">Anger det lägsta tillåtna värdet.</span><span class="sxs-lookup"><span data-stu-id="8ccc4-109">Specifies the minimum value allowed.</span></span>

<span data-ttu-id="8ccc4-110">`MaxRange` ([System. Object](/dotnet/api/system.object)) krävs.</span><span class="sxs-lookup"><span data-stu-id="8ccc4-110">`MaxRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="8ccc4-111">Anger det högsta tillåtna värdet.</span><span class="sxs-lookup"><span data-stu-id="8ccc4-111">Specifies the maximum value allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="8ccc4-112">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="8ccc4-112">Remarks</span></span>

- <span data-ttu-id="8ccc4-113">Windows PowerShell-körningsmiljön genererar ett konstruktions fel när värdet för `MinRange` parametern är större än värdet för `MaxRange` parametern.</span><span class="sxs-lookup"><span data-stu-id="8ccc4-113">The Windows PowerShell runtime throws a construction error when the value of the `MinRange` parameter is greater than the value of the `MaxRange` parameter.</span></span>

- <span data-ttu-id="8ccc4-114">Windows PowerShell-körningsmiljön genererar ett verifierings fel under följande förhållanden:</span><span class="sxs-lookup"><span data-stu-id="8ccc4-114">The Windows PowerShell runtime throws a validation error under the following conditions:</span></span>

  - <span data-ttu-id="8ccc4-115">När värdet för argumentet är mindre än `MinRange` gränsen eller större än `MaxRange` gränsen.</span><span class="sxs-lookup"><span data-stu-id="8ccc4-115">When the value of the argument is less than the `MinRange` limit or greater than the `MaxRange` limit.</span></span>

  - <span data-ttu-id="8ccc4-116">Om argumentet inte är av samma typ som `MinRange` `MaxRange` parametrarna och.</span><span class="sxs-lookup"><span data-stu-id="8ccc4-116">When the argument is not of the same type as the `MinRange` and the `MaxRange` parameters.</span></span>

- <span data-ttu-id="8ccc4-117">Attributet ValidateRange definieras av klassen [system. Management. Automation. Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) .</span><span class="sxs-lookup"><span data-stu-id="8ccc4-117">The ValidateRange attribute is defined by the [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="8ccc4-118">Se även</span><span class="sxs-lookup"><span data-stu-id="8ccc4-118">See Also</span></span>

[<span data-ttu-id="8ccc4-119">System. Management. Automation. Validaterangeattribute</span><span class="sxs-lookup"><span data-stu-id="8ccc4-119">System.Management.Automation.Validaterangeattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[<span data-ttu-id="8ccc4-120">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="8ccc4-120">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
