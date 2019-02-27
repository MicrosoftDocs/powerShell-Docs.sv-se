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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847539"
---
# <a name="validaterange-attribute-declaration"></a><span data-ttu-id="2deb8-102">Deklaration av attributet ValidateRange</span><span class="sxs-lookup"><span data-stu-id="2deb8-102">ValidateRange Attribute Declaration</span></span>

<span data-ttu-id="2deb8-103">Attributet ValidateRange anger de minsta och högsta värden (intervall) för cmdlet-argument för parametern.</span><span class="sxs-lookup"><span data-stu-id="2deb8-103">The ValidateRange attribute specifies the minimum and maximum values (the range) for the cmdlet parameter argument.</span></span> <span data-ttu-id="2deb8-104">Det här attributet kan också användas i Windows PowerShell-funktioner.</span><span class="sxs-lookup"><span data-stu-id="2deb8-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="2deb8-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="2deb8-105">Syntax</span></span>

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a><span data-ttu-id="2deb8-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="2deb8-106">Parameters</span></span>

<span data-ttu-id="2deb8-107">`MinRange` ([System.Object](/dotnet/api/system.object)) krävs.</span><span class="sxs-lookup"><span data-stu-id="2deb8-107">`MinRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="2deb8-108">Anger det minsta tillåtna värdet.</span><span class="sxs-lookup"><span data-stu-id="2deb8-108">Specifies the minimum value allowed.</span></span>

<span data-ttu-id="2deb8-109">`MaxRange` ([System.Object](/dotnet/api/system.object)) krävs.</span><span class="sxs-lookup"><span data-stu-id="2deb8-109">`MaxRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="2deb8-110">Anger det högsta tillåtna värdet.</span><span class="sxs-lookup"><span data-stu-id="2deb8-110">Specifies the maximum value allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="2deb8-111">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="2deb8-111">Remarks</span></span>

- <span data-ttu-id="2deb8-112">Windows PowerShell-runtime genererar en konstruktion fel när värdet för den `MinRange` parametern är större än värdet för den `MaxRange` parametern.</span><span class="sxs-lookup"><span data-stu-id="2deb8-112">The Windows PowerShell runtime throws a construction error when the value of the `MinRange` parameter is greater than the value of the `MaxRange` parameter.</span></span>

- <span data-ttu-id="2deb8-113">Windows PowerShell-runtime genererar ett valideringsfel under följande förhållanden:</span><span class="sxs-lookup"><span data-stu-id="2deb8-113">The Windows PowerShell runtime throws a validation error under the following conditions:</span></span>

    - <span data-ttu-id="2deb8-114">När värdet för argumentet är mindre än värdet `MinRange` gränsen med eller större än den `MaxRange` gränsen.</span><span class="sxs-lookup"><span data-stu-id="2deb8-114">When the value of the argument is less than the `MinRange` limit or greater than the `MaxRange` limit.</span></span>

    - <span data-ttu-id="2deb8-115">När argumentet är inte av samma typ som den `MinRange` och `MaxRange` parametrar.</span><span class="sxs-lookup"><span data-stu-id="2deb8-115">When the argument is not of the same type as the `MinRange` and the `MaxRange` parameters.</span></span>

- <span data-ttu-id="2deb8-116">Attributet ValidateRange definieras av den [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) klass.</span><span class="sxs-lookup"><span data-stu-id="2deb8-116">The ValidateRange attribute is defined by the [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="2deb8-117">Se även</span><span class="sxs-lookup"><span data-stu-id="2deb8-117">See Also</span></span>

[<span data-ttu-id="2deb8-118">System.Management.Automation.Validaterangeattribute</span><span class="sxs-lookup"><span data-stu-id="2deb8-118">System.Management.Automation.Validaterangeattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[<span data-ttu-id="2deb8-119">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2deb8-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
