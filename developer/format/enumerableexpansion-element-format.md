---
title: EnumerableExpansion Element (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93d27173-9ae4-46e5-bb78-90525915cd70
caps.latest.revision: 9
ms.openlocfilehash: bc1e58c00ca8419f9204076f0a46050281e704db
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847399"
---
# <a name="enumerableexpansion-element-format"></a><span data-ttu-id="868f6-102">EnumerableExpansion-element (format)</span><span class="sxs-lookup"><span data-stu-id="868f6-102">EnumerableExpansion Element (Format)</span></span>

<span data-ttu-id="868f6-103">Definierar hur specifik .NET samling objekt visas när de visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="868f6-103">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="868f6-104">Elementet (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion konfigurationselement (Format)</span><span class="sxs-lookup"><span data-stu-id="868f6-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="868f6-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="868f6-105">Syntax</span></span>

```xml
<EnumerableExpansion>
  <EntrySelectedBy>...</EntrySelectedBy>
  <Expand>EnumOnly, CoreOnly, Both</Expand>
</EnumerableExpansion>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="868f6-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="868f6-106">Attributes and Elements</span></span>

<span data-ttu-id="868f6-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `EnumerableExpansion` element.</span><span class="sxs-lookup"><span data-stu-id="868f6-107">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansion` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="868f6-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="868f6-108">Attributes</span></span>

<span data-ttu-id="868f6-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="868f6-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="868f6-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="868f6-110">Child Elements</span></span>

|<span data-ttu-id="868f6-111">Element</span><span class="sxs-lookup"><span data-stu-id="868f6-111">Element</span></span>|<span data-ttu-id="868f6-112">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="868f6-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="868f6-113">EntrySelectedBy Element för EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="868f6-113">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="868f6-114">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="868f6-114">Optional element.</span></span><br /><br /> <span data-ttu-id="868f6-115">Definierar vilka .NET samling objekt byggs med den här definitionen.</span><span class="sxs-lookup"><span data-stu-id="868f6-115">Defines which .NET collection objects are expanded by this definition.</span></span>|
|[<span data-ttu-id="868f6-116">Expandera Element (Format)</span><span class="sxs-lookup"><span data-stu-id="868f6-116">Expand Element (Format)</span></span>](./expand-element-format.md)|<span data-ttu-id="868f6-117">Anger hur samlingsobjektet utökas för den här definitionen.</span><span class="sxs-lookup"><span data-stu-id="868f6-117">Specifies how the collection object is expanded for this definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="868f6-118">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="868f6-118">Parent Elements</span></span>

|<span data-ttu-id="868f6-119">Element</span><span class="sxs-lookup"><span data-stu-id="868f6-119">Element</span></span>|<span data-ttu-id="868f6-120">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="868f6-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="868f6-121">EnumerableExpansions Element (Format)</span><span class="sxs-lookup"><span data-stu-id="868f6-121">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="868f6-122">Definierar de olika sätten .NET samlingen objekt visas när de visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="868f6-122">Defines the different ways that .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="868f6-123">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="868f6-123">Remarks</span></span>

<span data-ttu-id="868f6-124">Det här elementet används för att definiera hur samlingen och objekt i samlingen visas.</span><span class="sxs-lookup"><span data-stu-id="868f6-124">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="868f6-125">I det här fallet en samling objekt refererar till ett objekt som stöder den **System.Collections.ICollection** gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="868f6-125">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

<span data-ttu-id="868f6-126">Standardinställningen är att visa endast egenskaperna för objekten i samlingen.</span><span class="sxs-lookup"><span data-stu-id="868f6-126">The default behavior is to display only the properties of the objects in the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="868f6-127">Se även</span><span class="sxs-lookup"><span data-stu-id="868f6-127">See Also</span></span>

[<span data-ttu-id="868f6-128">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="868f6-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
