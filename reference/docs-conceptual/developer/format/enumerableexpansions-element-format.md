---
ms.date: 09/13/2016
ms.topic: reference
title: EnumerableExpansions-element (format)
description: EnumerableExpansions-element (format)
ms.openlocfilehash: 789599e6ff368b4685c7937d5b6eb38618752f9e
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92660176"
---
# <a name="enumerableexpansions-element-format"></a><span data-ttu-id="a63a3-103">EnumerableExpansions-element (format)</span><span class="sxs-lookup"><span data-stu-id="a63a3-103">EnumerableExpansions Element (Format)</span></span>

<span data-ttu-id="a63a3-104">Definierar hur .NET-samlings objekt expanderas när de visas i en vy.</span><span class="sxs-lookup"><span data-stu-id="a63a3-104">Defines how .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="a63a3-105">Konfigurations element (format) DefaultSettings-element (format) EnumerableExpansions-element (format)</span><span class="sxs-lookup"><span data-stu-id="a63a3-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a63a3-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="a63a3-106">Syntax</span></span>

```xml
<EnumerableExpansions>
  <EnumerableExpansion>...</EnumerableExpansion>
</EnumerableExpansions>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a63a3-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="a63a3-107">Attributes and Elements</span></span>

<span data-ttu-id="a63a3-108">I följande avsnitt beskrivs attribut, underordnade element och `EnumerableExpansions` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="a63a3-108">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansions` element.</span></span> <span data-ttu-id="a63a3-109">Det finns ingen gräns för antalet underordnade element som du kan använda.</span><span class="sxs-lookup"><span data-stu-id="a63a3-109">There is no limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="a63a3-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="a63a3-110">Attributes</span></span>

<span data-ttu-id="a63a3-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="a63a3-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a63a3-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="a63a3-112">Child Elements</span></span>

|<span data-ttu-id="a63a3-113">Element</span><span class="sxs-lookup"><span data-stu-id="a63a3-113">Element</span></span>|<span data-ttu-id="a63a3-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a63a3-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a63a3-115">EnumerableExpansion-element (format)</span><span class="sxs-lookup"><span data-stu-id="a63a3-115">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="a63a3-116">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="a63a3-116">Optional element.</span></span><br /><br /> <span data-ttu-id="a63a3-117">Definierar de olika .NET-samlings objekt som expanderas när de visas i en vy.</span><span class="sxs-lookup"><span data-stu-id="a63a3-117">Defines the specific .NET collection objects that are expanded when they are displayed in a view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a63a3-118">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="a63a3-118">Parent Elements</span></span>

|<span data-ttu-id="a63a3-119">Element</span><span class="sxs-lookup"><span data-stu-id="a63a3-119">Element</span></span>|<span data-ttu-id="a63a3-120">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a63a3-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a63a3-121">DefaultSettings-element (format)</span><span class="sxs-lookup"><span data-stu-id="a63a3-121">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="a63a3-122">Definierar vanliga inställningar som gäller för alla vyer i formaterings filen.</span><span class="sxs-lookup"><span data-stu-id="a63a3-122">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a63a3-123">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="a63a3-123">Remarks</span></span>

<span data-ttu-id="a63a3-124">Det här elementet används för att definiera hur samlings objekt och objekten i samlingen ska visas.</span><span class="sxs-lookup"><span data-stu-id="a63a3-124">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="a63a3-125">I det här fallet refererar ett samlings objekt till alla objekt som stöder  **system. Collections. ICollection** -gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="a63a3-125">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

## <a name="see-also"></a><span data-ttu-id="a63a3-126">Se även</span><span class="sxs-lookup"><span data-stu-id="a63a3-126">See Also</span></span>

[<span data-ttu-id="a63a3-127">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="a63a3-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
