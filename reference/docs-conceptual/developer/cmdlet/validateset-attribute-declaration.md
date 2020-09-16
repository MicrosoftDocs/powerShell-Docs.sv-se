---
title: ValidateSet-Attribute-deklaration | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- attributes, ValidateSet
- ValidateSet attribute, described
- ValidateSet attribute
ms.openlocfilehash: 0b6833efb0ce8e9474e9d91049fd201fc845cbea
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787775"
---
# <a name="validateset-attribute-declaration"></a><span data-ttu-id="9553d-102">Deklaration av attributet ValidateSet</span><span class="sxs-lookup"><span data-stu-id="9553d-102">ValidateSet Attribute Declaration</span></span>

<span data-ttu-id="9553d-103">Attributet ValidateSetAttribute anger en uppsättning möjliga värden för ett cmdlet parameter argument.</span><span class="sxs-lookup"><span data-stu-id="9553d-103">The ValidateSetAttribute attribute specifies a set of possible values for a cmdlet parameter argument.</span></span> <span data-ttu-id="9553d-104">Det här attributet kan också användas av Windows PowerShell-funktioner.</span><span class="sxs-lookup"><span data-stu-id="9553d-104">This attribute can also be used by Windows PowerShell functions.</span></span>

<span data-ttu-id="9553d-105">När det här attributet anges avgör Windows PowerShell-körningsmiljön om det angivna argumentet för cmdlet-parametern matchar ett element i den angivna element uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="9553d-105">When this attribute is specified, the Windows PowerShell runtime determines whether the supplied argument for the cmdlet parameter matches an element in the supplied element set.</span></span> <span data-ttu-id="9553d-106">Cmdleten körs bara om parameter argumentet matchar ett element i mängden.</span><span class="sxs-lookup"><span data-stu-id="9553d-106">The cmdlet is run only if the parameter argument matches an element in the set.</span></span> <span data-ttu-id="9553d-107">Om ingen matchning hittas uppstår ett fel i Windows PowerShell-körningsmiljön.</span><span class="sxs-lookup"><span data-stu-id="9553d-107">If no match is found, an error is thrown by the Windows PowerShell runtime.</span></span>

## <a name="syntax"></a><span data-ttu-id="9553d-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="9553d-108">Syntax</span></span>

```csharp
[ValidateSetAttribute(params string[] validValues)]
[ValidateSetAttribute(params string[] validValues, Named Parameters)]
```

#### <a name="parameters"></a><span data-ttu-id="9553d-109">Parametrar</span><span class="sxs-lookup"><span data-stu-id="9553d-109">Parameters</span></span>

<span data-ttu-id="9553d-110">`ValidValues` ([System. String](/dotnet/api/System.String)) krävs.</span><span class="sxs-lookup"><span data-stu-id="9553d-110">`ValidValues` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="9553d-111">Anger giltiga parameter element värden.</span><span class="sxs-lookup"><span data-stu-id="9553d-111">Specifies the valid parameter element values.</span></span> <span data-ttu-id="9553d-112">I följande exempel visas hur du anger ett eller flera element.</span><span class="sxs-lookup"><span data-stu-id="9553d-112">The following sample shows how to specify one element or multiple elements.</span></span>

```csharp
[ValidateSetAttribute("Steve")]
[ValidateSetAttribute("Steve","Mary")]
```

<span data-ttu-id="9553d-113">`IgnoreCase` ([System. Boolean](/dotnet/api/System.Boolean)) valfri namngiven parameter.</span><span class="sxs-lookup"><span data-stu-id="9553d-113">`IgnoreCase` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="9553d-114">Standardvärdet för `true` anger att Case ignoreras.</span><span class="sxs-lookup"><span data-stu-id="9553d-114">The default value of `true` indicates that case is ignored.</span></span> <span data-ttu-id="9553d-115">Värdet `false` gör cmdlet Skift läges känsligt.</span><span class="sxs-lookup"><span data-stu-id="9553d-115">A value of `false` makes the cmdlet case-sensitive.</span></span>

## <a name="remarks"></a><span data-ttu-id="9553d-116">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="9553d-116">Remarks</span></span>

- <span data-ttu-id="9553d-117">Det här attributet kan bara användas en gång per parameter.</span><span class="sxs-lookup"><span data-stu-id="9553d-117">This attribute can be used only once per parameter.</span></span>

- <span data-ttu-id="9553d-118">Om parametervärdet är en matris måste varje element i matrisen matcha ett element i attribut uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="9553d-118">If the parameter value is an array, every element of the array must match an element of the attribute set.</span></span>

- <span data-ttu-id="9553d-119">Attributet ValidateSetAttribute definieras av klassen [system. Management. Automation. ValidateSetAttribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) .</span><span class="sxs-lookup"><span data-stu-id="9553d-119">The ValidateSetAttribute attribute is defined by the [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="9553d-120">Se även</span><span class="sxs-lookup"><span data-stu-id="9553d-120">See Also</span></span>

[<span data-ttu-id="9553d-121">System. Management. Automation. Validatesetattribute</span><span class="sxs-lookup"><span data-stu-id="9553d-121">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[<span data-ttu-id="9553d-122">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="9553d-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
