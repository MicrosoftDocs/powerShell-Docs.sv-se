---
ms.date: 09/13/2016
ms.topic: reference
title: Types-element för SelectionSet (format)
description: Types-element för SelectionSet (format)
ms.openlocfilehash: ff3c24e7f52f862dc416b88d50983196ce907012
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645454"
---
# <a name="types-element-for-selectionset-format"></a><span data-ttu-id="2e768-103">Types-element för SelectionSet (format)</span><span class="sxs-lookup"><span data-stu-id="2e768-103">Types Element for SelectionSet (Format)</span></span>

<span data-ttu-id="2e768-104">Definierar de .NET-objekt som finns i urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="2e768-104">Defines the .NET objects that are in the selection set.</span></span>

<span data-ttu-id="2e768-105">Konfigurations element (format) SelectionSets-element (format) SelectionSet element (format) element (format)</span><span class="sxs-lookup"><span data-stu-id="2e768-105">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Types Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2e768-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="2e768-106">Syntax</span></span>

```xml
<Types>
  <TypeName>Nameof.NetType</TypeName>
</Types>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="2e768-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="2e768-107">Attributes and Elements</span></span>

<span data-ttu-id="2e768-108">I följande avsnitt beskrivs attributen, underordnade element och `Types` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="2e768-108">The following sections describe the attributes, child elements, and the parent element of the `Types` element.</span></span> <span data-ttu-id="2e768-109">Det måste finnas minst ett underordnat element, men det finns ingen övre gräns för antalet underordnade element som kan läggas till.</span><span class="sxs-lookup"><span data-stu-id="2e768-109">There must be at least one child element, but there is no maximum limit to the number of child elements that can be added.</span></span>

### <a name="attributes"></a><span data-ttu-id="2e768-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="2e768-110">Attributes</span></span>

<span data-ttu-id="2e768-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="2e768-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2e768-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="2e768-112">Child Elements</span></span>

|<span data-ttu-id="2e768-113">Element</span><span class="sxs-lookup"><span data-stu-id="2e768-113">Element</span></span>|<span data-ttu-id="2e768-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="2e768-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2e768-115">Element av typen TypeName (format)</span><span class="sxs-lookup"><span data-stu-id="2e768-115">TypeName Element of Types (Format)</span></span>](./typename-element-for-types-format.md)|<span data-ttu-id="2e768-116">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="2e768-116">Required element.</span></span><br /><br /> <span data-ttu-id="2e768-117">Anger det .NET-objekt som tillhör urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="2e768-117">Specifies the .NET object that belongs to the selection set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2e768-118">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="2e768-118">Parent Elements</span></span>

|<span data-ttu-id="2e768-119">Element</span><span class="sxs-lookup"><span data-stu-id="2e768-119">Element</span></span>|<span data-ttu-id="2e768-120">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="2e768-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2e768-121">SelectionSet-element (format)</span><span class="sxs-lookup"><span data-stu-id="2e768-121">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="2e768-122">Definierar en uppsättning .NET-objekt som kan refereras till i uppsättningens namn.</span><span class="sxs-lookup"><span data-stu-id="2e768-122">Defines a set of .NET objects that can be referenced by the name of the set.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2e768-123">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="2e768-123">Remarks</span></span>

<span data-ttu-id="2e768-124">De objekt som definieras av det här elementet utgör en urvals uppsättning som kan användas av en vy, i en definition av en vy (vyer kan ha flera definitioner) eller när du anger ett urvals villkor.</span><span class="sxs-lookup"><span data-stu-id="2e768-124">The objects defined by this element make up a selection set that can be used by a view, by a definition of a view (views can have multiple definitions), or when specifying a selection condition.</span></span>  <span data-ttu-id="2e768-125">Mer information om urvals uppsättningar finns i [definiera uppsättningar av objekt](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="2e768-125">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="2e768-126">Exempel</span><span class="sxs-lookup"><span data-stu-id="2e768-126">Example</span></span>

<span data-ttu-id="2e768-127">Det här exemplet visar ett- `SelectionSet` element som definierar fyra .net-typer.</span><span class="sxs-lookup"><span data-stu-id="2e768-127">This example shows a `SelectionSet` element that defines four .NET types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="2e768-128">Se även</span><span class="sxs-lookup"><span data-stu-id="2e768-128">See Also</span></span>

[<span data-ttu-id="2e768-129">Definiera uppsättningar av objekt</span><span class="sxs-lookup"><span data-stu-id="2e768-129">Defining Sets of Objects</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="2e768-130">SelectionSet-element (format)</span><span class="sxs-lookup"><span data-stu-id="2e768-130">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="2e768-131">Element av typen TypeName (format)</span><span class="sxs-lookup"><span data-stu-id="2e768-131">TypeName Element of Types (Format)</span></span>](./typename-element-for-types-format.md)

[<span data-ttu-id="2e768-132">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="2e768-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
