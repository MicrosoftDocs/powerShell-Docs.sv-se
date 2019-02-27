---
title: Deklaration av ValidateSet attribut | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateSet
- ValidateSet attribute, described
- ValidateSet attribute
ms.assetid: 4a6f97ab-45b2-4f3d-84d4-30acf8e074d0
caps.latest.revision: 12
ms.openlocfilehash: b036f39cd01ffe4b4ce7db9627cb6da0d5327190
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850458"
---
# <a name="validateset-attribute-declaration"></a><span data-ttu-id="9f014-102">Deklaration av attributet ValidateSet</span><span class="sxs-lookup"><span data-stu-id="9f014-102">ValidateSet Attribute Declaration</span></span>

<span data-ttu-id="9f014-103">Attributet ValidateSetAttribute anger en uppsättning möjliga värden för en cmdlet-argument för parametern.</span><span class="sxs-lookup"><span data-stu-id="9f014-103">The ValidateSetAttribute attribute specifies a set of possible values for a cmdlet parameter argument.</span></span> <span data-ttu-id="9f014-104">Det här attributet kan också användas i Windows PowerShell-funktioner.</span><span class="sxs-lookup"><span data-stu-id="9f014-104">This attribute can also be used by Windows PowerShell functions.</span></span>

<span data-ttu-id="9f014-105">När det här attributet anges avgör Windows PowerShell-körningen om det angivna argumentet för cmdlet-parameter matchar ett element i den angivna element uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="9f014-105">When this attribute is specified, the Windows PowerShell runtime determines whether the supplied argument for the cmdlet parameter matches an element in the supplied element set.</span></span> <span data-ttu-id="9f014-106">Cmdleten körs bara om Parameterargumentet matchar ett element i mängden.</span><span class="sxs-lookup"><span data-stu-id="9f014-106">The cmdlet is run only if the parameter argument matches an element in the set.</span></span> <span data-ttu-id="9f014-107">Om ingen matchning hittas returneras ett fel av Windows PowerShell-körningen.</span><span class="sxs-lookup"><span data-stu-id="9f014-107">If no match is found, an error is thrown by the Windows PowerShell runtime.</span></span>

## <a name="syntax"></a><span data-ttu-id="9f014-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="9f014-108">Syntax</span></span>

```csharp
[ValidateSetAttribute(params string[] validValues)]
[ValidateSetAttribute(params string[] validValues, Named Parameters)]
```

#### <a name="parameters"></a><span data-ttu-id="9f014-109">Parametrar</span><span class="sxs-lookup"><span data-stu-id="9f014-109">Parameters</span></span>

<span data-ttu-id="9f014-110">`ValidValues` ([System.String](/dotnet/api/System.String)) krävs.</span><span class="sxs-lookup"><span data-stu-id="9f014-110">`ValidValues` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="9f014-111">Anger de giltiga parametervärdena för elementet.</span><span class="sxs-lookup"><span data-stu-id="9f014-111">Specifies the valid parameter element values.</span></span> <span data-ttu-id="9f014-112">I följande exempel visas hur du anger en eller flera element.</span><span class="sxs-lookup"><span data-stu-id="9f014-112">The following sample shows how to specify one element or multiple elements.</span></span>

```csharp
[ValidateSetAttribute("Steve")]
[ValidateSetAttribute("Steve","Mary")]
```

<span data-ttu-id="9f014-113">`IgnoreCase` ([System.Boolean](/dotnet/api/System.Boolean)) valfritt med namnet parametern.</span><span class="sxs-lookup"><span data-stu-id="9f014-113">`IgnoreCase` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="9f014-114">Standardvärdet för `true` anger att inte är skiftlägeskänsliga.</span><span class="sxs-lookup"><span data-stu-id="9f014-114">The default value of `true` indicates that case is ignored.</span></span> <span data-ttu-id="9f014-115">Värdet `false` gör cmdleten skiftlägeskänsliga.</span><span class="sxs-lookup"><span data-stu-id="9f014-115">A value of `false` makes the cmdlet case-sensitive.</span></span>

## <a name="remarks"></a><span data-ttu-id="9f014-116">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="9f014-116">Remarks</span></span>

- <span data-ttu-id="9f014-117">Det här attributet kan användas endast en gång per parametern.</span><span class="sxs-lookup"><span data-stu-id="9f014-117">This attribute can be used only once per parameter.</span></span>

- <span data-ttu-id="9f014-118">Om värdet för parametern är en matris, måste varje element i matrisen matcha ett element i attributuppsättningen.</span><span class="sxs-lookup"><span data-stu-id="9f014-118">If the parameter value is an array, every element of the array must match an element of the attribute set.</span></span>

- <span data-ttu-id="9f014-119">Attributet ValidateSetAttribute definieras av den [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) klass.</span><span class="sxs-lookup"><span data-stu-id="9f014-119">The ValidateSetAttribute attribute is defined by the [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="9f014-120">Se även</span><span class="sxs-lookup"><span data-stu-id="9f014-120">See Also</span></span>

[<span data-ttu-id="9f014-121">System.Management.Automation.Validatesetattribute</span><span class="sxs-lookup"><span data-stu-id="9f014-121">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[<span data-ttu-id="9f014-122">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="9f014-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
