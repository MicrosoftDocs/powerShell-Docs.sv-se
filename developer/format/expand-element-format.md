---
title: Expandera Element (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: faa0314b-f6f1-44fd-ad2b-b00cbe38923f
caps.latest.revision: 9
ms.openlocfilehash: 8b924c989133b47e4d95d8429778003c76595d58
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066013"
---
# <a name="expand-element-format"></a><span data-ttu-id="840f3-102">Expand-element (format)</span><span class="sxs-lookup"><span data-stu-id="840f3-102">Expand Element (Format)</span></span>

<span data-ttu-id="840f3-103">Anger hur samlingsobjektet utökas för den här definitionen.</span><span class="sxs-lookup"><span data-stu-id="840f3-103">Specifies how the collection object is expanded for this definition.</span></span>

<span data-ttu-id="840f3-104">Elementet (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion konfigurationselement (Format) expanderar Element (Format)</span><span class="sxs-lookup"><span data-stu-id="840f3-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) Expand Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="840f3-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="840f3-105">Syntax</span></span>

```xml
<Expand>EnumOnly, CoreOnly, Both</Expand>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="840f3-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="840f3-106">Attributes and Elements</span></span>

<span data-ttu-id="840f3-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `Expand` element.</span><span class="sxs-lookup"><span data-stu-id="840f3-107">The following sections describe attributes, child elements, and the parent element of the `Expand` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="840f3-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="840f3-108">Attributes</span></span>

<span data-ttu-id="840f3-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="840f3-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="840f3-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="840f3-110">Child Elements</span></span>

<span data-ttu-id="840f3-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="840f3-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="840f3-112">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="840f3-112">Parent Elements</span></span>

|<span data-ttu-id="840f3-113">Element</span><span class="sxs-lookup"><span data-stu-id="840f3-113">Element</span></span>|<span data-ttu-id="840f3-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="840f3-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="840f3-115">EnumerableExpansion Element (Format)</span><span class="sxs-lookup"><span data-stu-id="840f3-115">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="840f3-116">Definierar hur specifik .NET samling objekt visas när de visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="840f3-116">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="840f3-117">Textvärde</span><span class="sxs-lookup"><span data-stu-id="840f3-117">Text Value</span></span>

<span data-ttu-id="840f3-118">Ange en av följande värden:</span><span class="sxs-lookup"><span data-stu-id="840f3-118">Specify one of the following values:</span></span>

- <span data-ttu-id="840f3-119">EnumOnly: Visar endast egenskaperna för objekten i samlingen.</span><span class="sxs-lookup"><span data-stu-id="840f3-119">EnumOnly: Displays only the properties of the objects in the collection.</span></span>

- <span data-ttu-id="840f3-120">CoreOnly: Visar endast egenskaperna för samlingsobjektet.</span><span class="sxs-lookup"><span data-stu-id="840f3-120">CoreOnly: Displays only the properties of the collection object.</span></span>

- <span data-ttu-id="840f3-121">Both: Visar egenskaperna för objekten i samlingen och egenskaperna för samlingsobjektet.</span><span class="sxs-lookup"><span data-stu-id="840f3-121">Both: Displays the properties of the objects in the collection and the properties of the collection object.</span></span>

## <a name="remarks"></a><span data-ttu-id="840f3-122">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="840f3-122">Remarks</span></span>

<span data-ttu-id="840f3-123">Det här elementet används för att definiera hur samlingen och objekt i samlingen visas.</span><span class="sxs-lookup"><span data-stu-id="840f3-123">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="840f3-124">I det här fallet en samling objekt refererar till ett objekt som stöder den **System.Collections.ICollection** gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="840f3-124">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

<span data-ttu-id="840f3-125">Standardinställningen är att visa endast egenskaperna för objekten i samlingen.</span><span class="sxs-lookup"><span data-stu-id="840f3-125">The default behavior is to display only the properties of the objects in the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="840f3-126">Se även</span><span class="sxs-lookup"><span data-stu-id="840f3-126">See Also</span></span>

[<span data-ttu-id="840f3-127">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="840f3-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
