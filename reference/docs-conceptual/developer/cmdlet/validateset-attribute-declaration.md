---
ms.date: 09/13/2016
ms.topic: reference
title: Deklaration av attributet ValidateSet
description: Deklaration av attributet ValidateSet
ms.openlocfilehash: 7894d00561366ada492911e8147acbd8d3454a55
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660465"
---
# <a name="validateset-attribute-declaration"></a><span data-ttu-id="d193f-103">Deklaration av attributet ValidateSet</span><span class="sxs-lookup"><span data-stu-id="d193f-103">ValidateSet Attribute Declaration</span></span>

<span data-ttu-id="d193f-104">Attributet ValidateSetAttribute anger en uppsättning möjliga värden för ett cmdlet parameter argument.</span><span class="sxs-lookup"><span data-stu-id="d193f-104">The ValidateSetAttribute attribute specifies a set of possible values for a cmdlet parameter argument.</span></span> <span data-ttu-id="d193f-105">Det här attributet kan också användas av Windows PowerShell-funktioner.</span><span class="sxs-lookup"><span data-stu-id="d193f-105">This attribute can also be used by Windows PowerShell functions.</span></span>

<span data-ttu-id="d193f-106">När det här attributet anges avgör Windows PowerShell-körningsmiljön om det angivna argumentet för cmdlet-parametern matchar ett element i den angivna element uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="d193f-106">When this attribute is specified, the Windows PowerShell runtime determines whether the supplied argument for the cmdlet parameter matches an element in the supplied element set.</span></span> <span data-ttu-id="d193f-107">Cmdleten körs bara om parameter argumentet matchar ett element i mängden.</span><span class="sxs-lookup"><span data-stu-id="d193f-107">The cmdlet is run only if the parameter argument matches an element in the set.</span></span> <span data-ttu-id="d193f-108">Om ingen matchning hittas uppstår ett fel i Windows PowerShell-körningsmiljön.</span><span class="sxs-lookup"><span data-stu-id="d193f-108">If no match is found, an error is thrown by the Windows PowerShell runtime.</span></span>

## <a name="syntax"></a><span data-ttu-id="d193f-109">Syntax</span><span class="sxs-lookup"><span data-stu-id="d193f-109">Syntax</span></span>

```csharp
[ValidateSetAttribute(params string[] validValues)]
[ValidateSetAttribute(params string[] validValues, Named Parameters)]
```

#### <a name="parameters"></a><span data-ttu-id="d193f-110">Parametrar</span><span class="sxs-lookup"><span data-stu-id="d193f-110">Parameters</span></span>

<span data-ttu-id="d193f-111">`ValidValues` ([System. String](/dotnet/api/System.String)) krävs.</span><span class="sxs-lookup"><span data-stu-id="d193f-111">`ValidValues` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="d193f-112">Anger giltiga parameter element värden.</span><span class="sxs-lookup"><span data-stu-id="d193f-112">Specifies the valid parameter element values.</span></span> <span data-ttu-id="d193f-113">I följande exempel visas hur du anger ett eller flera element.</span><span class="sxs-lookup"><span data-stu-id="d193f-113">The following sample shows how to specify one element or multiple elements.</span></span>

```csharp
[ValidateSetAttribute("Steve")]
[ValidateSetAttribute("Steve","Mary")]
```

<span data-ttu-id="d193f-114">`IgnoreCase` ([System. Boolean](/dotnet/api/System.Boolean)) valfri namngiven parameter.</span><span class="sxs-lookup"><span data-stu-id="d193f-114">`IgnoreCase` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="d193f-115">Standardvärdet för `true` anger att Case ignoreras.</span><span class="sxs-lookup"><span data-stu-id="d193f-115">The default value of `true` indicates that case is ignored.</span></span> <span data-ttu-id="d193f-116">Värdet `false` gör cmdlet Skift läges känsligt.</span><span class="sxs-lookup"><span data-stu-id="d193f-116">A value of `false` makes the cmdlet case-sensitive.</span></span>

## <a name="remarks"></a><span data-ttu-id="d193f-117">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="d193f-117">Remarks</span></span>

- <span data-ttu-id="d193f-118">Det här attributet kan bara användas en gång per parameter.</span><span class="sxs-lookup"><span data-stu-id="d193f-118">This attribute can be used only once per parameter.</span></span>

- <span data-ttu-id="d193f-119">Om parametervärdet är en matris måste varje element i matrisen matcha ett element i attribut uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="d193f-119">If the parameter value is an array, every element of the array must match an element of the attribute set.</span></span>

- <span data-ttu-id="d193f-120">Attributet ValidateSetAttribute definieras av klassen [system. Management. Automation. ValidateSetAttribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) .</span><span class="sxs-lookup"><span data-stu-id="d193f-120">The ValidateSetAttribute attribute is defined by the [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="d193f-121">Se även</span><span class="sxs-lookup"><span data-stu-id="d193f-121">See Also</span></span>

[<span data-ttu-id="d193f-122">System. Management. Automation. Validatesetattribute</span><span class="sxs-lookup"><span data-stu-id="d193f-122">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[<span data-ttu-id="d193f-123">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="d193f-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
