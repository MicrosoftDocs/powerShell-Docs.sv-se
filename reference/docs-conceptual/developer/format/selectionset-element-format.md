---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSet-element (format)
description: SelectionSet-element (format)
ms.openlocfilehash: 944aa83569ad8ca789746a71f60e5da5c19fbf01
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92647868"
---
# <a name="selectionset-element-format"></a><span data-ttu-id="d2d8e-103">SelectionSet-element (format)</span><span class="sxs-lookup"><span data-stu-id="d2d8e-103">SelectionSet Element (Format)</span></span>

<span data-ttu-id="d2d8e-104">Definierar en uppsättning .NET-objekt som kan refereras till i uppsättningens namn.</span><span class="sxs-lookup"><span data-stu-id="d2d8e-104">Defines a set of .NET objects that can be referenced by the name of the set.</span></span>

<span data-ttu-id="d2d8e-105">Konfigurations element (format) SelectionSets-element (format) SelectionSet-element (format)</span><span class="sxs-lookup"><span data-stu-id="d2d8e-105">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d2d8e-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="d2d8e-106">Syntax</span></span>

```xml
<SelectionSet>
  <Name>SelectionSetName</Name>
  <Types>...</Types>
</SelectionSet>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d2d8e-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="d2d8e-107">Attributes and Elements</span></span>

<span data-ttu-id="d2d8e-108">I följande avsnitt beskrivs attributen, underordnade element och `SelectionSet` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="d2d8e-108">The following sections describe the attributes, child elements, and the parent element of the `SelectionSet` element.</span></span> <span data-ttu-id="d2d8e-109">Varje urvals uppsättning måste ha ett namn och måste ange .NET-objekten för uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="d2d8e-109">Each selection set must have a name, and it must specify the .NET objects of the set.</span></span>

### <a name="attributes"></a><span data-ttu-id="d2d8e-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="d2d8e-110">Attributes</span></span>

<span data-ttu-id="d2d8e-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="d2d8e-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d2d8e-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="d2d8e-112">Child Elements</span></span>

|<span data-ttu-id="d2d8e-113">Element</span><span class="sxs-lookup"><span data-stu-id="d2d8e-113">Element</span></span>|<span data-ttu-id="d2d8e-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d2d8e-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d2d8e-115">Name-element för SelectionSet (format)</span><span class="sxs-lookup"><span data-stu-id="d2d8e-115">Name Element for SelectionSet (Format)</span></span>](./name-element-for-selectionset-format.md)|<span data-ttu-id="d2d8e-116">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="d2d8e-116">Required element.</span></span><br /><br /> <span data-ttu-id="d2d8e-117">Anger namnet som används för att referera till urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="d2d8e-117">Specifies the name used to reference the selection set.</span></span>|
|[<span data-ttu-id="d2d8e-118">Typ element (format)</span><span class="sxs-lookup"><span data-stu-id="d2d8e-118">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)|<span data-ttu-id="d2d8e-119">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="d2d8e-119">Required element.</span></span><br /><br /> <span data-ttu-id="d2d8e-120">Definierar de .NET-objekt som finns i urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="d2d8e-120">Defines the .NET objects that are in the selection set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d2d8e-121">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="d2d8e-121">Parent Elements</span></span>

|<span data-ttu-id="d2d8e-122">Element</span><span class="sxs-lookup"><span data-stu-id="d2d8e-122">Element</span></span>|<span data-ttu-id="d2d8e-123">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d2d8e-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d2d8e-124">SelectionSets element format</span><span class="sxs-lookup"><span data-stu-id="d2d8e-124">SelectionSets Element Format</span></span>](./selectionsets-element-format.md)|<span data-ttu-id="d2d8e-125">Definierar de gemensamma uppsättningar av .NET-objekt som kan användas av alla vyer i format filen.</span><span class="sxs-lookup"><span data-stu-id="d2d8e-125">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d2d8e-126">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="d2d8e-126">Remarks</span></span>

<span data-ttu-id="d2d8e-127">Du kan använda urvals uppsättningar när du har en uppsättning relaterade objekt som du vill referera till genom att använda ett enda namn, till exempel en uppsättning objekt som är relaterade till arv.</span><span class="sxs-lookup"><span data-stu-id="d2d8e-127">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="d2d8e-128">När du definierar dina vyer kan du ange en uppsättning objekt genom att använda namnet på urvals uppsättningen i stället för att visa alla objekt i varje vy.</span><span class="sxs-lookup"><span data-stu-id="d2d8e-128">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="d2d8e-129">Vanliga urvals uppsättningar anges med deras namn när du definierar vyerna för format filen eller definitionerna för vyerna.</span><span class="sxs-lookup"><span data-stu-id="d2d8e-129">Common selection sets are specified by their name when defining the views of the formatting file or the definitions of the views.</span></span> <span data-ttu-id="d2d8e-130">I dessa fall anger det `SelectionSetName` underordnade elementet i `ViewSelectedBy` `EntrySelectedBy` elementen och den uppsättning som ska användas.</span><span class="sxs-lookup"><span data-stu-id="d2d8e-130">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` and `EntrySelectedBy` elements specifies the set to be used.</span></span> <span data-ttu-id="d2d8e-131">Mer information om urvals uppsättningar finns i [definiera uppsättningar av objekt](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="d2d8e-131">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="d2d8e-132">Exempel</span><span class="sxs-lookup"><span data-stu-id="d2d8e-132">Example</span></span>

<span data-ttu-id="d2d8e-133">I följande exempel visas ett- `SelectionSet` element som definierar fyra .net-typer.</span><span class="sxs-lookup"><span data-stu-id="d2d8e-133">The following example shows a `SelectionSet` element that defines four .NET types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d2d8e-134">Se även</span><span class="sxs-lookup"><span data-stu-id="d2d8e-134">See Also</span></span>

[<span data-ttu-id="d2d8e-135">Definiera valuppsättningar</span><span class="sxs-lookup"><span data-stu-id="d2d8e-135">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="d2d8e-136">Namn element i SelectionSet (format)</span><span class="sxs-lookup"><span data-stu-id="d2d8e-136">Name Element of SelectionSet (Format)</span></span>](./name-element-for-selectionset-format.md)

[<span data-ttu-id="d2d8e-137">SelectionSets-element (format)</span><span class="sxs-lookup"><span data-stu-id="d2d8e-137">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="d2d8e-138">Typ element (format)</span><span class="sxs-lookup"><span data-stu-id="d2d8e-138">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="d2d8e-139">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="d2d8e-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
