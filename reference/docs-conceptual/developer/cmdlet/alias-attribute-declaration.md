---
ms.date: 09/13/2016
ms.topic: reference
title: Deklaration av attributet Alias
description: Deklaration av attributet Alias
ms.openlocfilehash: f2fe49578da2c795643b1f80fa44deefe1dbff09
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92668311"
---
# <a name="alias-attribute-declaration"></a><span data-ttu-id="30a86-103">Deklaration av attributet Alias</span><span class="sxs-lookup"><span data-stu-id="30a86-103">Alias Attribute Declaration</span></span>

<span data-ttu-id="30a86-104">Attributet alias gör att användaren kan ange olika namn för en cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="30a86-104">The Alias attribute allows the user to specify different names for a cmdlet parameter.</span></span> <span data-ttu-id="30a86-105">Alias kan användas för att ange genvägar för ett parameter namn, eller så kan de ange olika namn som passar för olika scenarier.</span><span class="sxs-lookup"><span data-stu-id="30a86-105">Aliases can be used to provide shortcuts for a parameter name, or they can provide different names that are appropriate for different scenarios.</span></span>

## <a name="syntax"></a><span data-ttu-id="30a86-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="30a86-106">Syntax</span></span>

```csharp
[Alias(aliasNames)]
```

#### <a name="parameters"></a><span data-ttu-id="30a86-107">Parametrar</span><span class="sxs-lookup"><span data-stu-id="30a86-107">Parameters</span></span>

<span data-ttu-id="30a86-108">`aliasName` (Sträng []) Kunna.</span><span class="sxs-lookup"><span data-stu-id="30a86-108">`aliasName` (String[]) Required.</span></span> <span data-ttu-id="30a86-109">Anger en uppsättning kommaavgränsade aliasnamn för cmdlet-parametern.</span><span class="sxs-lookup"><span data-stu-id="30a86-109">Specifies a set of comma-separated alias names for the cmdlet parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="30a86-110">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="30a86-110">Remarks</span></span>

- <span data-ttu-id="30a86-111">Attributet alias används med attributet parameter när du anger en cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="30a86-111">The Alias attribute is used with the Parameter attribute when you specify a cmdlet parameter.</span></span> <span data-ttu-id="30a86-112">Mer information om hur du deklarerar dessa attribut finns i [så här deklarerar du cmdlet-parametrar](./how-to-declare-cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="30a86-112">For more information about how to declare these attributes, see [How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).</span></span>

- <span data-ttu-id="30a86-113">Varje aliasnamn måste vara unikt inom en-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="30a86-113">Each alias name must be unique within a cmdlet.</span></span> <span data-ttu-id="30a86-114">Windows PowerShell söker inte efter dubbla aliasnamn.</span><span class="sxs-lookup"><span data-stu-id="30a86-114">Windows PowerShell does not check for duplicate alias names.</span></span>

- <span data-ttu-id="30a86-115">Attributet alias används en gång för varje parameter i en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="30a86-115">The Alias attribute is used once for each parameter in a cmdlet.</span></span>

- <span data-ttu-id="30a86-116">Attributet alias definieras av klassen [system. Management. Automation. Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) .</span><span class="sxs-lookup"><span data-stu-id="30a86-116">The Alias attribute is defined by the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="30a86-117">Se även</span><span class="sxs-lookup"><span data-stu-id="30a86-117">See Also</span></span>

[<span data-ttu-id="30a86-118">Parameteralias</span><span class="sxs-lookup"><span data-stu-id="30a86-118">Parameter Aliases</span></span>](./parameter-aliases.md)

[<span data-ttu-id="30a86-119">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="30a86-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
