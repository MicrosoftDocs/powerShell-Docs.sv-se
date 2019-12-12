---
title: ValidateSet-Attribute-deklaration | Microsoft Docs
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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355421"
---
# <a name="validateset-attribute-declaration"></a><span data-ttu-id="c9413-102">Deklaration av attributet ValidateSet</span><span class="sxs-lookup"><span data-stu-id="c9413-102">ValidateSet Attribute Declaration</span></span>

<span data-ttu-id="c9413-103">Attributet ValidateSetAttribute anger en uppsättning möjliga värden för ett cmdlet parameter argument.</span><span class="sxs-lookup"><span data-stu-id="c9413-103">The ValidateSetAttribute attribute specifies a set of possible values for a cmdlet parameter argument.</span></span> <span data-ttu-id="c9413-104">Det här attributet kan också användas av Windows PowerShell-funktioner.</span><span class="sxs-lookup"><span data-stu-id="c9413-104">This attribute can also be used by Windows PowerShell functions.</span></span>

<span data-ttu-id="c9413-105">När det här attributet anges avgör Windows PowerShell-körningsmiljön om det angivna argumentet för cmdlet-parametern matchar ett element i den angivna element uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="c9413-105">When this attribute is specified, the Windows PowerShell runtime determines whether the supplied argument for the cmdlet parameter matches an element in the supplied element set.</span></span> <span data-ttu-id="c9413-106">Cmdleten körs bara om parameter argumentet matchar ett element i mängden.</span><span class="sxs-lookup"><span data-stu-id="c9413-106">The cmdlet is run only if the parameter argument matches an element in the set.</span></span> <span data-ttu-id="c9413-107">Om ingen matchning hittas uppstår ett fel i Windows PowerShell-körningsmiljön.</span><span class="sxs-lookup"><span data-stu-id="c9413-107">If no match is found, an error is thrown by the Windows PowerShell runtime.</span></span>

## <a name="syntax"></a><span data-ttu-id="c9413-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="c9413-108">Syntax</span></span>

```csharp
[ValidateSetAttribute(params string[] validValues)]
[ValidateSetAttribute(params string[] validValues, Named Parameters)]
```

#### <a name="parameters"></a><span data-ttu-id="c9413-109">Parametrar</span><span class="sxs-lookup"><span data-stu-id="c9413-109">Parameters</span></span>

<span data-ttu-id="c9413-110">`ValidValues` ([system. String](/dotnet/api/System.String)) krävs.</span><span class="sxs-lookup"><span data-stu-id="c9413-110">`ValidValues` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="c9413-111">Anger giltiga parameter element värden.</span><span class="sxs-lookup"><span data-stu-id="c9413-111">Specifies the valid parameter element values.</span></span> <span data-ttu-id="c9413-112">I följande exempel visas hur du anger ett eller flera element.</span><span class="sxs-lookup"><span data-stu-id="c9413-112">The following sample shows how to specify one element or multiple elements.</span></span>

```csharp
[ValidateSetAttribute("Steve")]
[ValidateSetAttribute("Steve","Mary")]
```

<span data-ttu-id="c9413-113">`IgnoreCase` ([system. Boolean](/dotnet/api/System.Boolean)) valfri namngiven parameter.</span><span class="sxs-lookup"><span data-stu-id="c9413-113">`IgnoreCase` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="c9413-114">Standardvärdet för `true` indikerar att Skift läget ignoreras.</span><span class="sxs-lookup"><span data-stu-id="c9413-114">The default value of `true` indicates that case is ignored.</span></span> <span data-ttu-id="c9413-115">Värdet `false` gör cmdleten Skift läges känslig.</span><span class="sxs-lookup"><span data-stu-id="c9413-115">A value of `false` makes the cmdlet case-sensitive.</span></span>

## <a name="remarks"></a><span data-ttu-id="c9413-116">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="c9413-116">Remarks</span></span>

- <span data-ttu-id="c9413-117">Det här attributet kan bara användas en gång per parameter.</span><span class="sxs-lookup"><span data-stu-id="c9413-117">This attribute can be used only once per parameter.</span></span>

- <span data-ttu-id="c9413-118">Om parametervärdet är en matris måste varje element i matrisen matcha ett element i attribut uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="c9413-118">If the parameter value is an array, every element of the array must match an element of the attribute set.</span></span>

- <span data-ttu-id="c9413-119">Attributet ValidateSetAttribute definieras av klassen [system. Management. Automation. ValidateSetAttribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) .</span><span class="sxs-lookup"><span data-stu-id="c9413-119">The ValidateSetAttribute attribute is defined by the [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="c9413-120">Se även</span><span class="sxs-lookup"><span data-stu-id="c9413-120">See Also</span></span>

[<span data-ttu-id="c9413-121">System. Management. Automation. Validatesetattribute</span><span class="sxs-lookup"><span data-stu-id="c9413-121">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[<span data-ttu-id="c9413-122">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="c9413-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
