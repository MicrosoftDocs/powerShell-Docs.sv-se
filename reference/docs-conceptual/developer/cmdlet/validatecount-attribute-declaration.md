---
ms.date: 09/13/2016
ms.topic: reference
title: Deklaration av attributet ValidateCount
description: Deklaration av attributet ValidateCount
ms.openlocfilehash: 6acdd02a10ecc1bc2be0e6be88cf2f42a3673eb8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646274"
---
# <a name="validatecount-attribute-declaration"></a><span data-ttu-id="54a29-103">Deklaration av attributet ValidateCount</span><span class="sxs-lookup"><span data-stu-id="54a29-103">ValidateCount Attribute Declaration</span></span>

<span data-ttu-id="54a29-104">Attributet ValidateCount anger det lägsta och högsta antalet argument som tillåts för en cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="54a29-104">The ValidateCount attribute specifies the minimum and maximum number of arguments allowed for a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="54a29-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="54a29-105">Syntax</span></span>

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="54a29-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="54a29-106">Parameters</span></span>

<span data-ttu-id="54a29-107">`MinLength` ([System. Int32][]) krävs.</span><span class="sxs-lookup"><span data-stu-id="54a29-107">`MinLength` ([System.Int32][]) Required.</span></span> <span data-ttu-id="54a29-108">Anger det minsta antalet argument.</span><span class="sxs-lookup"><span data-stu-id="54a29-108">Specifies the minimum number of arguments.</span></span>

<span data-ttu-id="54a29-109">`MaxLength`([System. Int32][]) krävs.</span><span class="sxs-lookup"><span data-stu-id="54a29-109">`MaxLength`([System.Int32][]) Required.</span></span> <span data-ttu-id="54a29-110">Anger det maximala antalet argument.</span><span class="sxs-lookup"><span data-stu-id="54a29-110">Specifies the maximum number of arguments.</span></span>

## <a name="remarks"></a><span data-ttu-id="54a29-111">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="54a29-111">Remarks</span></span>

- <span data-ttu-id="54a29-112">Mer information om hur du deklarerar det här attributet finns i [så här verifierar du ett argument antal][].</span><span class="sxs-lookup"><span data-stu-id="54a29-112">For more information about how to declare this attribute, see [How to Validate an Argument Count][].</span></span>

- <span data-ttu-id="54a29-113">När det här attributet inte anropas kan motsvarande cmdlet-parameter ha valfritt antal argument.</span><span class="sxs-lookup"><span data-stu-id="54a29-113">When this attribute is not invoked, the corresponding cmdlet parameter can have any number of arguments.</span></span>

- <span data-ttu-id="54a29-114">Windows PowerShell-körningsmiljön genererar ett fel under följande förhållanden:</span><span class="sxs-lookup"><span data-stu-id="54a29-114">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

  - <span data-ttu-id="54a29-115">`MinLength`Parametrarna och `MaxLength` är inte av typen [system. Int32][].</span><span class="sxs-lookup"><span data-stu-id="54a29-115">The `MinLength` and `MaxLength` attribute parameters are not of type [System.Int32][].</span></span>

  - <span data-ttu-id="54a29-116">Värdet för `MaxLength` attributet Attribute är mindre än värdet för `MinLength` parametern Attribute.</span><span class="sxs-lookup"><span data-stu-id="54a29-116">The value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

- <span data-ttu-id="54a29-117">Attributet ValidateCount definieras av klassen [system. Management. Automation. ValidateCountAttribute][] .</span><span class="sxs-lookup"><span data-stu-id="54a29-117">The ValidateCount attribute is defined by the [System.Management.Automation.ValidateCountAttribute][] class.</span></span>

## <a name="see-also"></a><span data-ttu-id="54a29-118">Se även</span><span class="sxs-lookup"><span data-stu-id="54a29-118">See Also</span></span>

<span data-ttu-id="54a29-119">[System. Management. Automation. ValidateCountAttribute][]</span><span class="sxs-lookup"><span data-stu-id="54a29-119">[System.Management.Automation.ValidateCountAttribute][]</span></span>

<span data-ttu-id="54a29-120">[Verifiera argumentantal][]</span><span class="sxs-lookup"><span data-stu-id="54a29-120">[How to Validate an Argument Count][]</span></span>

<span data-ttu-id="54a29-121">[Skriva en Windows PowerShell-cmdlet][]</span><span class="sxs-lookup"><span data-stu-id="54a29-121">[Writing a Windows PowerShell Cmdlet][]</span></span>

[Verifiera argumentantal]: how-to-validate-an-argument-count.md
[How to Validate an Argument Count]: how-to-validate-an-argument-count.md
[Skriva en Windows PowerShell-cmdlet]: writing-a-windows-powershell-cmdlet.md
[Writing a Windows PowerShell Cmdlet]: writing-a-windows-powershell-cmdlet.md

[System. Int32]: /dotnet/api/System.Int32
[System.Int32]: /dotnet/api/System.Int32
[System. Management. Automation. ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
[System.Management.Automation.ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
