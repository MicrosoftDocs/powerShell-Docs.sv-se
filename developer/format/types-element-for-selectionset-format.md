---
title: Datatyper Element för SelectionSet (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4606fec0-ff31-4d36-af68-227405335ec3
caps.latest.revision: 15
ms.openlocfilehash: 0427367efa2c8a7e352d718706d1341a0c8e3621
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851277"
---
# <a name="types-element-for-selectionset-format"></a><span data-ttu-id="ce7d4-102">Types-element för SelectionSet (format)</span><span class="sxs-lookup"><span data-stu-id="ce7d4-102">Types Element for SelectionSet (Format)</span></span>

<span data-ttu-id="ce7d4-103">Definierar de .NET-objekt som är i urvalet inställda.</span><span class="sxs-lookup"><span data-stu-id="ce7d4-103">Defines the .NET objects that are in the selection set.</span></span>

<span data-ttu-id="ce7d4-104">Elementet (Format) SelectionSets Element (Format) SelectionSet konfigurationselement (Format) datatyper Element (Format)</span><span class="sxs-lookup"><span data-stu-id="ce7d4-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Types Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ce7d4-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="ce7d4-105">Syntax</span></span>

```xml
<Types>
  <TypeName>Nameof.NetType</TypeName>
</Types>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="ce7d4-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="ce7d4-106">Attributes and Elements</span></span>

<span data-ttu-id="ce7d4-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `Types` element.</span><span class="sxs-lookup"><span data-stu-id="ce7d4-107">The following sections describe the attributes, child elements, and the parent element of the `Types` element.</span></span> <span data-ttu-id="ce7d4-108">Det måste finnas minst ett underordnat element, men det finns ingen högsta gräns för antalet underordnade element som kan läggas till.</span><span class="sxs-lookup"><span data-stu-id="ce7d4-108">There must be at least one child element, but there is no maximum limit to the number of child elements that can be added.</span></span>

### <a name="attributes"></a><span data-ttu-id="ce7d4-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="ce7d4-109">Attributes</span></span>

<span data-ttu-id="ce7d4-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="ce7d4-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ce7d4-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="ce7d4-111">Child Elements</span></span>

|<span data-ttu-id="ce7d4-112">Element</span><span class="sxs-lookup"><span data-stu-id="ce7d4-112">Element</span></span>|<span data-ttu-id="ce7d4-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ce7d4-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ce7d4-114">TypeName-elementet i typer (Format)</span><span class="sxs-lookup"><span data-stu-id="ce7d4-114">TypeName Element of Types (Format)</span></span>](./typename-element-for-types-format.md)|<span data-ttu-id="ce7d4-115">Element som krävs.</span><span class="sxs-lookup"><span data-stu-id="ce7d4-115">Required element.</span></span><br /><br /> <span data-ttu-id="ce7d4-116">Anger det .NET-objekt som hör till val av uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="ce7d4-116">Specifies the .NET object that belongs to the selection set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ce7d4-117">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="ce7d4-117">Parent Elements</span></span>

|<span data-ttu-id="ce7d4-118">Element</span><span class="sxs-lookup"><span data-stu-id="ce7d4-118">Element</span></span>|<span data-ttu-id="ce7d4-119">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ce7d4-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ce7d4-120">SelectionSet Element (Format)</span><span class="sxs-lookup"><span data-stu-id="ce7d4-120">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="ce7d4-121">Definierar en uppsättning av .NET-objekt som kan refereras av namnet på uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="ce7d4-121">Defines a set of .NET objects that can be referenced by the name of the set.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ce7d4-122">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="ce7d4-122">Remarks</span></span>

<span data-ttu-id="ce7d4-123">De objekt som definierats av det här elementet utgör en uppsättning för val av som kan användas av en vy av en definition av en vy (vyer kan ha flera definitioner), eller när du anger ett val av villkor.</span><span class="sxs-lookup"><span data-stu-id="ce7d4-123">The objects defined by this element make up a selection set that can be used by a view, by a definition of a view (views can have multiple definitions), or when specifying a selection condition.</span></span>  <span data-ttu-id="ce7d4-124">Mer information om inställningarna finns i [definiera anger av objekt](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="ce7d4-124">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="ce7d4-125">Exempel</span><span class="sxs-lookup"><span data-stu-id="ce7d4-125">Example</span></span>

<span data-ttu-id="ce7d4-126">Det här exemplet visar en `SelectionSet` -element som definierar fyra typer av .NET.</span><span class="sxs-lookup"><span data-stu-id="ce7d4-126">This example shows a `SelectionSet` element that defines four .NET types.</span></span>

```xml
<SelectionSets>
  <SelectionSet>
    <Name>FileSystemTypes</Name>
    <Types>
     <TypeName>System.IO.DirectoryInfo</TypeName>
     <TypeName>System.IO.FileInfo</TypeName>
     <TypeName>Deserialized.System.IO.DirectoryInfo</TypeName>
     <TypeName>Deserialized.System.IO.FileInfo</TypeName>
    </Types>
  </SelectionSet>
</SelectionSets>
```

## <a name="see-also"></a><span data-ttu-id="ce7d4-127">Se även</span><span class="sxs-lookup"><span data-stu-id="ce7d4-127">See Also</span></span>

[<span data-ttu-id="ce7d4-128">Definiera uppsättningar med objekt</span><span class="sxs-lookup"><span data-stu-id="ce7d4-128">Defining Sets of Objects</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="ce7d4-129">SelectionSet Element (Format)</span><span class="sxs-lookup"><span data-stu-id="ce7d4-129">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="ce7d4-130">TypeName-elementet i typer (Format)</span><span class="sxs-lookup"><span data-stu-id="ce7d4-130">TypeName Element of Types (Format)</span></span>](./typename-element-for-types-format.md)

[<span data-ttu-id="ce7d4-131">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="ce7d4-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
