---
ms.date: 09/13/2016
ms.topic: reference
title: Expand-element (format)
description: Expand-element (format)
ms.openlocfilehash: 518e132e3e74b921d4e51966fc60088a22ef63f1
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667954"
---
# <a name="expand-element-format"></a><span data-ttu-id="1871b-103">Expand-element (format)</span><span class="sxs-lookup"><span data-stu-id="1871b-103">Expand Element (Format)</span></span>

<span data-ttu-id="1871b-104">Anger hur Collection-objektet expanderas för den här definitionen.</span><span class="sxs-lookup"><span data-stu-id="1871b-104">Specifies how the collection object is expanded for this definition.</span></span>

<span data-ttu-id="1871b-105">Konfigurations element (format) DefaultSettings-element (format) EnumerableExpansions-element (format) EnumerableExpansion-element (format) Expand-element (format)</span><span class="sxs-lookup"><span data-stu-id="1871b-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) Expand Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1871b-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="1871b-106">Syntax</span></span>

```xml
<Expand>EnumOnly, CoreOnly, Both</Expand>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1871b-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="1871b-107">Attributes and Elements</span></span>

<span data-ttu-id="1871b-108">I följande avsnitt beskrivs attribut, underordnade element och `Expand` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="1871b-108">The following sections describe attributes, child elements, and the parent element of the `Expand` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1871b-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="1871b-109">Attributes</span></span>

<span data-ttu-id="1871b-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="1871b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1871b-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="1871b-111">Child Elements</span></span>

<span data-ttu-id="1871b-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="1871b-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1871b-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="1871b-113">Parent Elements</span></span>

|<span data-ttu-id="1871b-114">Element</span><span class="sxs-lookup"><span data-stu-id="1871b-114">Element</span></span>|<span data-ttu-id="1871b-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="1871b-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1871b-116">EnumerableExpansion-element (format)</span><span class="sxs-lookup"><span data-stu-id="1871b-116">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="1871b-117">Definierar hur vissa .NET Collection-objekt expanderas när de visas i en vy.</span><span class="sxs-lookup"><span data-stu-id="1871b-117">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1871b-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="1871b-118">Text Value</span></span>

<span data-ttu-id="1871b-119">Ange ett av följande värden:</span><span class="sxs-lookup"><span data-stu-id="1871b-119">Specify one of the following values:</span></span>

- <span data-ttu-id="1871b-120">EnumOnly: visar endast egenskaperna för objekten i samlingen.</span><span class="sxs-lookup"><span data-stu-id="1871b-120">EnumOnly: Displays only the properties of the objects in the collection.</span></span>

- <span data-ttu-id="1871b-121">CoreOnly: visar endast egenskaperna för objektet samling.</span><span class="sxs-lookup"><span data-stu-id="1871b-121">CoreOnly: Displays only the properties of the collection object.</span></span>

- <span data-ttu-id="1871b-122">Båda: visar egenskaperna för objekten i samlingen och egenskaperna för objektet samling.</span><span class="sxs-lookup"><span data-stu-id="1871b-122">Both: Displays the properties of the objects in the collection and the properties of the collection object.</span></span>

## <a name="remarks"></a><span data-ttu-id="1871b-123">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="1871b-123">Remarks</span></span>

<span data-ttu-id="1871b-124">Det här elementet används för att definiera hur samlings objekt och objekten i samlingen ska visas.</span><span class="sxs-lookup"><span data-stu-id="1871b-124">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="1871b-125">I det här fallet refererar ett samlings objekt till alla objekt som stöder  **system. Collections. ICollection** -gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="1871b-125">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

<span data-ttu-id="1871b-126">Standard beteendet är att endast visa egenskaperna för objekten i samlingen.</span><span class="sxs-lookup"><span data-stu-id="1871b-126">The default behavior is to display only the properties of the objects in the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="1871b-127">Se även</span><span class="sxs-lookup"><span data-stu-id="1871b-127">See Also</span></span>

[<span data-ttu-id="1871b-128">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="1871b-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
