---
title: Deklaration av ValidateRange attribut | Microsoft Docs
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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067118"
---
# <a name="validaterange-attribute-declaration"></a><span data-ttu-id="f2399-102">Deklaration av attributet ValidateRange</span><span class="sxs-lookup"><span data-stu-id="f2399-102">ValidateRange Attribute Declaration</span></span>

<span data-ttu-id="f2399-103">Attributet ValidateRange anger de minsta och högsta värden (intervall) för cmdlet-argument för parametern.</span><span class="sxs-lookup"><span data-stu-id="f2399-103">The ValidateRange attribute specifies the minimum and maximum values (the range) for the cmdlet parameter argument.</span></span> <span data-ttu-id="f2399-104">Det här attributet kan också användas i Windows PowerShell-funktioner.</span><span class="sxs-lookup"><span data-stu-id="f2399-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="f2399-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="f2399-105">Syntax</span></span>

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a><span data-ttu-id="f2399-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="f2399-106">Parameters</span></span>

<span data-ttu-id="f2399-107">`MinRange` ([System.Object](/dotnet/api/system.object)) krävs.</span><span class="sxs-lookup"><span data-stu-id="f2399-107">`MinRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="f2399-108">Anger det minsta tillåtna värdet.</span><span class="sxs-lookup"><span data-stu-id="f2399-108">Specifies the minimum value allowed.</span></span>

<span data-ttu-id="f2399-109">`MaxRange` ([System.Object](/dotnet/api/system.object)) krävs.</span><span class="sxs-lookup"><span data-stu-id="f2399-109">`MaxRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="f2399-110">Anger det högsta tillåtna värdet.</span><span class="sxs-lookup"><span data-stu-id="f2399-110">Specifies the maximum value allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="f2399-111">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="f2399-111">Remarks</span></span>

- <span data-ttu-id="f2399-112">Windows PowerShell-runtime genererar en konstruktion fel när värdet för den `MinRange` parametern är större än värdet för den `MaxRange` parametern.</span><span class="sxs-lookup"><span data-stu-id="f2399-112">The Windows PowerShell runtime throws a construction error when the value of the `MinRange` parameter is greater than the value of the `MaxRange` parameter.</span></span>

- <span data-ttu-id="f2399-113">Windows PowerShell-runtime genererar ett valideringsfel under följande förhållanden:</span><span class="sxs-lookup"><span data-stu-id="f2399-113">The Windows PowerShell runtime throws a validation error under the following conditions:</span></span>

    - <span data-ttu-id="f2399-114">När värdet för argumentet är mindre än värdet `MinRange` gränsen med eller större än den `MaxRange` gränsen.</span><span class="sxs-lookup"><span data-stu-id="f2399-114">When the value of the argument is less than the `MinRange` limit or greater than the `MaxRange` limit.</span></span>

    - <span data-ttu-id="f2399-115">När argumentet är inte av samma typ som den `MinRange` och `MaxRange` parametrar.</span><span class="sxs-lookup"><span data-stu-id="f2399-115">When the argument is not of the same type as the `MinRange` and the `MaxRange` parameters.</span></span>

- <span data-ttu-id="f2399-116">Attributet ValidateRange definieras av den [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) klass.</span><span class="sxs-lookup"><span data-stu-id="f2399-116">The ValidateRange attribute is defined by the [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="f2399-117">Se även</span><span class="sxs-lookup"><span data-stu-id="f2399-117">See Also</span></span>

[<span data-ttu-id="f2399-118">System.Management.Automation.Validaterangeattribute</span><span class="sxs-lookup"><span data-stu-id="f2399-118">System.Management.Automation.Validaterangeattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[<span data-ttu-id="f2399-119">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="f2399-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
