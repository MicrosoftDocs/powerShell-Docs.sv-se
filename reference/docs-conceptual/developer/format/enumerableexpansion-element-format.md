---
ms.date: 09/13/2016
ms.topic: reference
title: EnumerableExpansion-element (format)
description: EnumerableExpansion-element (format)
ms.openlocfilehash: 207ad99d5335e99701660159ab77279b55b0b6b5
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92668022"
---
# <a name="enumerableexpansion-element-format"></a><span data-ttu-id="2e214-103">EnumerableExpansion-element (format)</span><span class="sxs-lookup"><span data-stu-id="2e214-103">EnumerableExpansion Element (Format)</span></span>

<span data-ttu-id="2e214-104">Definierar hur vissa .NET Collection-objekt expanderas när de visas i en vy.</span><span class="sxs-lookup"><span data-stu-id="2e214-104">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="2e214-105">Konfigurations element (format) DefaultSettings-element (format) EnumerableExpansions-element (format) element för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="2e214-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2e214-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="2e214-106">Syntax</span></span>

```xml
<EnumerableExpansion>
  <EntrySelectedBy>...</EntrySelectedBy>
  <Expand>EnumOnly, CoreOnly, Both</Expand>
</EnumerableExpansion>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2e214-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="2e214-107">Attributes and Elements</span></span>

<span data-ttu-id="2e214-108">I följande avsnitt beskrivs attribut, underordnade element och `EnumerableExpansion` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="2e214-108">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansion` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2e214-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="2e214-109">Attributes</span></span>

<span data-ttu-id="2e214-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="2e214-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2e214-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="2e214-111">Child Elements</span></span>

|<span data-ttu-id="2e214-112">Element</span><span class="sxs-lookup"><span data-stu-id="2e214-112">Element</span></span>|<span data-ttu-id="2e214-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="2e214-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2e214-114">EntrySelectedBy-element för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="2e214-114">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="2e214-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="2e214-115">Optional element.</span></span><br /><br /> <span data-ttu-id="2e214-116">Definierar vilka .NET-samlings objekt som expanderas av den här definitionen.</span><span class="sxs-lookup"><span data-stu-id="2e214-116">Defines which .NET collection objects are expanded by this definition.</span></span>|
|[<span data-ttu-id="2e214-117">Expand-element (format)</span><span class="sxs-lookup"><span data-stu-id="2e214-117">Expand Element (Format)</span></span>](./expand-element-format.md)|<span data-ttu-id="2e214-118">Anger hur Collection-objektet expanderas för den här definitionen.</span><span class="sxs-lookup"><span data-stu-id="2e214-118">Specifies how the collection object is expanded for this definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2e214-119">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="2e214-119">Parent Elements</span></span>

|<span data-ttu-id="2e214-120">Element</span><span class="sxs-lookup"><span data-stu-id="2e214-120">Element</span></span>|<span data-ttu-id="2e214-121">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="2e214-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2e214-122">EnumerableExpansions-element (format)</span><span class="sxs-lookup"><span data-stu-id="2e214-122">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="2e214-123">Definierar de olika sätt som .NET-samlings objekt expanderas när de visas i en vy.</span><span class="sxs-lookup"><span data-stu-id="2e214-123">Defines the different ways that .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2e214-124">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="2e214-124">Remarks</span></span>

<span data-ttu-id="2e214-125">Det här elementet används för att definiera hur samlings objekt och objekten i samlingen ska visas.</span><span class="sxs-lookup"><span data-stu-id="2e214-125">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="2e214-126">I det här fallet refererar ett samlings objekt till alla objekt som stöder  **system. Collections. ICollection** -gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="2e214-126">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

<span data-ttu-id="2e214-127">Standard beteendet är att endast visa egenskaperna för objekten i samlingen.</span><span class="sxs-lookup"><span data-stu-id="2e214-127">The default behavior is to display only the properties of the objects in the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="2e214-128">Se även</span><span class="sxs-lookup"><span data-stu-id="2e214-128">See Also</span></span>

[<span data-ttu-id="2e214-129">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="2e214-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
