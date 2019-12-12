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
ms.openlocfilehash: 155a406b9855c435041fe175ac7d983a4b4eb8b7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359134"
---
# <a name="validaterange-attribute-declaration"></a><span data-ttu-id="bea84-102">Deklaration av attributet ValidateRange</span><span class="sxs-lookup"><span data-stu-id="bea84-102">ValidateRange Attribute Declaration</span></span>

<span data-ttu-id="bea84-103">Attributet ValidateRange anger det lägsta och högsta värdet (intervallet) för argumentet cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="bea84-103">The ValidateRange attribute specifies the minimum and maximum values (the range) for the cmdlet parameter argument.</span></span> <span data-ttu-id="bea84-104">Det här attributet kan också användas av Windows PowerShell-funktioner.</span><span class="sxs-lookup"><span data-stu-id="bea84-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="bea84-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="bea84-105">Syntax</span></span>

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a><span data-ttu-id="bea84-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="bea84-106">Parameters</span></span>

<span data-ttu-id="bea84-107">`MinRange` ([system. Object](/dotnet/api/system.object)) krävs.</span><span class="sxs-lookup"><span data-stu-id="bea84-107">`MinRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="bea84-108">Anger det lägsta tillåtna värdet.</span><span class="sxs-lookup"><span data-stu-id="bea84-108">Specifies the minimum value allowed.</span></span>

<span data-ttu-id="bea84-109">`MaxRange` ([system. Object](/dotnet/api/system.object)) krävs.</span><span class="sxs-lookup"><span data-stu-id="bea84-109">`MaxRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="bea84-110">Anger det högsta tillåtna värdet.</span><span class="sxs-lookup"><span data-stu-id="bea84-110">Specifies the maximum value allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="bea84-111">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="bea84-111">Remarks</span></span>

- <span data-ttu-id="bea84-112">Windows PowerShell-körningsmiljön genererar ett konstruktions fel när värdet för parametern `MinRange` är större än värdet för parametern `MaxRange`.</span><span class="sxs-lookup"><span data-stu-id="bea84-112">The Windows PowerShell runtime throws a construction error when the value of the `MinRange` parameter is greater than the value of the `MaxRange` parameter.</span></span>

- <span data-ttu-id="bea84-113">Windows PowerShell-körningsmiljön genererar ett verifierings fel under följande förhållanden:</span><span class="sxs-lookup"><span data-stu-id="bea84-113">The Windows PowerShell runtime throws a validation error under the following conditions:</span></span>

    - <span data-ttu-id="bea84-114">När värdet för argumentet är mindre än `MinRange` gränsen eller större än `MaxRange` gränsen.</span><span class="sxs-lookup"><span data-stu-id="bea84-114">When the value of the argument is less than the `MinRange` limit or greater than the `MaxRange` limit.</span></span>

    - <span data-ttu-id="bea84-115">Om argumentet inte är av samma typ som `MinRange` och `MaxRange` parametrar.</span><span class="sxs-lookup"><span data-stu-id="bea84-115">When the argument is not of the same type as the `MinRange` and the `MaxRange` parameters.</span></span>

- <span data-ttu-id="bea84-116">Attributet ValidateRange definieras av klassen [system. Management. Automation. Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) .</span><span class="sxs-lookup"><span data-stu-id="bea84-116">The ValidateRange attribute is defined by the [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="bea84-117">Se även</span><span class="sxs-lookup"><span data-stu-id="bea84-117">See Also</span></span>

[<span data-ttu-id="bea84-118">System. Management. Automation. Validaterangeattribute</span><span class="sxs-lookup"><span data-stu-id="bea84-118">System.Management.Automation.Validaterangeattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[<span data-ttu-id="bea84-119">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="bea84-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
