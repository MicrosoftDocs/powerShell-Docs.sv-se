---
ms.date: 09/13/2016
ms.topic: reference
title: Deklaration av attributet ValidateCount
description: Deklaration av attributet ValidateCount
ms.openlocfilehash: 6acdd02a10ecc1bc2be0e6be88cf2f42a3673eb8
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92646274"
---
# <a name="validatecount-attribute-declaration"></a><span data-ttu-id="8807c-103">Deklaration av attributet ValidateCount</span><span class="sxs-lookup"><span data-stu-id="8807c-103">ValidateCount Attribute Declaration</span></span>

<span data-ttu-id="8807c-104">Attributet ValidateCount anger det lägsta och högsta antalet argument som tillåts för en cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="8807c-104">The ValidateCount attribute specifies the minimum and maximum number of arguments allowed for a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="8807c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="8807c-105">Syntax</span></span>

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="8807c-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="8807c-106">Parameters</span></span>

<span data-ttu-id="8807c-107">`MinLength` ([System. Int32][]) krävs.</span><span class="sxs-lookup"><span data-stu-id="8807c-107">`MinLength` ([System.Int32][]) Required.</span></span> <span data-ttu-id="8807c-108">Anger det minsta antalet argument.</span><span class="sxs-lookup"><span data-stu-id="8807c-108">Specifies the minimum number of arguments.</span></span>

<span data-ttu-id="8807c-109">`MaxLength`([System. Int32][]) krävs.</span><span class="sxs-lookup"><span data-stu-id="8807c-109">`MaxLength`([System.Int32][]) Required.</span></span> <span data-ttu-id="8807c-110">Anger det maximala antalet argument.</span><span class="sxs-lookup"><span data-stu-id="8807c-110">Specifies the maximum number of arguments.</span></span>

## <a name="remarks"></a><span data-ttu-id="8807c-111">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="8807c-111">Remarks</span></span>

- <span data-ttu-id="8807c-112">Mer information om hur du deklarerar det här attributet finns i [så här verifierar du ett argument antal][].</span><span class="sxs-lookup"><span data-stu-id="8807c-112">For more information about how to declare this attribute, see [How to Validate an Argument Count][].</span></span>

- <span data-ttu-id="8807c-113">När det här attributet inte anropas kan motsvarande cmdlet-parameter ha valfritt antal argument.</span><span class="sxs-lookup"><span data-stu-id="8807c-113">When this attribute is not invoked, the corresponding cmdlet parameter can have any number of arguments.</span></span>

- <span data-ttu-id="8807c-114">Windows PowerShell-körningsmiljön genererar ett fel under följande förhållanden:</span><span class="sxs-lookup"><span data-stu-id="8807c-114">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

  - <span data-ttu-id="8807c-115">`MinLength`Parametrarna och `MaxLength` är inte av typen [system. Int32][].</span><span class="sxs-lookup"><span data-stu-id="8807c-115">The `MinLength` and `MaxLength` attribute parameters are not of type [System.Int32][].</span></span>

  - <span data-ttu-id="8807c-116">Värdet för `MaxLength` attributet Attribute är mindre än värdet för `MinLength` parametern Attribute.</span><span class="sxs-lookup"><span data-stu-id="8807c-116">The value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

- <span data-ttu-id="8807c-117">Attributet ValidateCount definieras av klassen [system. Management. Automation. ValidateCountAttribute][] .</span><span class="sxs-lookup"><span data-stu-id="8807c-117">The ValidateCount attribute is defined by the [System.Management.Automation.ValidateCountAttribute][] class.</span></span>

## <a name="see-also"></a><span data-ttu-id="8807c-118">Se även</span><span class="sxs-lookup"><span data-stu-id="8807c-118">See Also</span></span>

<span data-ttu-id="8807c-119">[System. Management. Automation. ValidateCountAttribute][]</span><span class="sxs-lookup"><span data-stu-id="8807c-119">[System.Management.Automation.ValidateCountAttribute][]</span></span>

<span data-ttu-id="8807c-120">[Verifiera argumentantal][]</span><span class="sxs-lookup"><span data-stu-id="8807c-120">[How to Validate an Argument Count][]</span></span>

<span data-ttu-id="8807c-121">[Skriva en Windows PowerShell-cmdlet][]</span><span class="sxs-lookup"><span data-stu-id="8807c-121">[Writing a Windows PowerShell Cmdlet][]</span></span>

[Verifiera argumentantal]: how-to-validate-an-argument-count.md
[How to Validate an Argument Count]: how-to-validate-an-argument-count.md
[Skriva en Windows PowerShell-cmdlet]: writing-a-windows-powershell-cmdlet.md
[Writing a Windows PowerShell Cmdlet]: writing-a-windows-powershell-cmdlet.md

[System. Int32]: /dotnet/api/System.Int32
[System.Int32]: /dotnet/api/System.Int32
[System. Management. Automation. ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
[System.Management.Automation.ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
