---
title: ValidateRange-Attribute-deklaration | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateRange, described
- ValidateRange attribute
- attributes, ValidateRange
ms.assetid: 1f8066e6-e5d3-4f4e-8948-a90af5dace82
caps.latest.revision: 11
ms.openlocfilehash: 560fa105ac3f93ae6334df0112f5290dfa20576c
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/20/2020
ms.locfileid: "83692005"
---
# <a name="validaterange-attribute-declaration"></a><span data-ttu-id="9d510-102">Deklaration av attributet ValidateRange</span><span class="sxs-lookup"><span data-stu-id="9d510-102">ValidateRange Attribute Declaration</span></span>

<span data-ttu-id="9d510-103">Attributet ValidateRange anger det lägsta och högsta värdet (intervallet) för argumentet cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="9d510-103">The ValidateRange attribute specifies the minimum and maximum values (the range) for the cmdlet parameter argument.</span></span> <span data-ttu-id="9d510-104">Det här attributet kan också användas av Windows PowerShell-funktioner.</span><span class="sxs-lookup"><span data-stu-id="9d510-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="9d510-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="9d510-105">Syntax</span></span>

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a><span data-ttu-id="9d510-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="9d510-106">Parameters</span></span>

<span data-ttu-id="9d510-107">`MinRange`([System. Object](/dotnet/api/system.object)) krävs.</span><span class="sxs-lookup"><span data-stu-id="9d510-107">`MinRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="9d510-108">Anger det lägsta tillåtna värdet.</span><span class="sxs-lookup"><span data-stu-id="9d510-108">Specifies the minimum value allowed.</span></span>

<span data-ttu-id="9d510-109">`MaxRange`([System. Object](/dotnet/api/system.object)) krävs.</span><span class="sxs-lookup"><span data-stu-id="9d510-109">`MaxRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="9d510-110">Anger det högsta tillåtna värdet.</span><span class="sxs-lookup"><span data-stu-id="9d510-110">Specifies the maximum value allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="9d510-111">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="9d510-111">Remarks</span></span>

- <span data-ttu-id="9d510-112">Windows PowerShell-körningsmiljön genererar ett konstruktions fel när värdet för `MinRange` parametern är större än värdet för `MaxRange` parametern.</span><span class="sxs-lookup"><span data-stu-id="9d510-112">The Windows PowerShell runtime throws a construction error when the value of the `MinRange` parameter is greater than the value of the `MaxRange` parameter.</span></span>

- <span data-ttu-id="9d510-113">Windows PowerShell-körningsmiljön genererar ett verifierings fel under följande förhållanden:</span><span class="sxs-lookup"><span data-stu-id="9d510-113">The Windows PowerShell runtime throws a validation error under the following conditions:</span></span>

  - <span data-ttu-id="9d510-114">När värdet för argumentet är mindre än `MinRange` gränsen eller större än `MaxRange` gränsen.</span><span class="sxs-lookup"><span data-stu-id="9d510-114">When the value of the argument is less than the `MinRange` limit or greater than the `MaxRange` limit.</span></span>

  - <span data-ttu-id="9d510-115">Om argumentet inte är av samma typ som `MinRange` `MaxRange` parametrarna och.</span><span class="sxs-lookup"><span data-stu-id="9d510-115">When the argument is not of the same type as the `MinRange` and the `MaxRange` parameters.</span></span>

- <span data-ttu-id="9d510-116">Attributet ValidateRange definieras av klassen [system. Management. Automation. Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) .</span><span class="sxs-lookup"><span data-stu-id="9d510-116">The ValidateRange attribute is defined by the [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="9d510-117">Se även</span><span class="sxs-lookup"><span data-stu-id="9d510-117">See Also</span></span>

[<span data-ttu-id="9d510-118">System. Management. Automation. Validaterangeattribute</span><span class="sxs-lookup"><span data-stu-id="9d510-118">System.Management.Automation.Validaterangeattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[<span data-ttu-id="9d510-119">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="9d510-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
