---
title: SelectionSet Element (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 848e7acd-d578-4fd1-a575-c0c3b9b5e68a
caps.latest.revision: 17
ms.openlocfilehash: c809aa6c3a40d16cfd2fd99065a846d265ec0f61
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850423"
---
# <a name="selectionset-element-format"></a><span data-ttu-id="74260-102">SelectionSet-element (format)</span><span class="sxs-lookup"><span data-stu-id="74260-102">SelectionSet Element (Format)</span></span>

<span data-ttu-id="74260-103">Definierar en uppsättning av .NET-objekt som kan refereras av namnet på uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="74260-103">Defines a set of .NET objects that can be referenced by the name of the set.</span></span>

<span data-ttu-id="74260-104">Elementet (Format) SelectionSets Element (Format) SelectionSet konfigurationselement (Format)</span><span class="sxs-lookup"><span data-stu-id="74260-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="74260-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="74260-105">Syntax</span></span>

```xml
<SelectionSet>
  <Name>SelectionSetName</Name>
  <Types>...</Types>
</SelectionSet>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="74260-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="74260-106">Attributes and Elements</span></span>

<span data-ttu-id="74260-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `SelectionSet` element.</span><span class="sxs-lookup"><span data-stu-id="74260-107">The following sections describe the attributes, child elements, and the parent element of the `SelectionSet` element.</span></span> <span data-ttu-id="74260-108">Varje uppsättning val måste ha ett namn och det måste ange .NET-objekt i uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="74260-108">Each selection set must have a name, and it must specify the .NET objects of the set.</span></span>

### <a name="attributes"></a><span data-ttu-id="74260-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="74260-109">Attributes</span></span>

<span data-ttu-id="74260-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="74260-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="74260-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="74260-111">Child Elements</span></span>

|<span data-ttu-id="74260-112">Element</span><span class="sxs-lookup"><span data-stu-id="74260-112">Element</span></span>|<span data-ttu-id="74260-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="74260-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="74260-114">Namnelement för SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="74260-114">Name Element for SelectionSet (Format)</span></span>](./name-element-for-selectionset-format.md)|<span data-ttu-id="74260-115">Element som krävs.</span><span class="sxs-lookup"><span data-stu-id="74260-115">Required element.</span></span><br /><br /> <span data-ttu-id="74260-116">Anger namnet som refererar till uppsättningen val.</span><span class="sxs-lookup"><span data-stu-id="74260-116">Specifies the name used to reference the selection set.</span></span>|
|[<span data-ttu-id="74260-117">Typer av Element (Format)</span><span class="sxs-lookup"><span data-stu-id="74260-117">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)|<span data-ttu-id="74260-118">Element som krävs.</span><span class="sxs-lookup"><span data-stu-id="74260-118">Required element.</span></span><br /><br /> <span data-ttu-id="74260-119">Definierar de .NET-objekt som är i urvalet inställda.</span><span class="sxs-lookup"><span data-stu-id="74260-119">Defines the .NET objects that are in the selection set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="74260-120">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="74260-120">Parent Elements</span></span>

|<span data-ttu-id="74260-121">Element</span><span class="sxs-lookup"><span data-stu-id="74260-121">Element</span></span>|<span data-ttu-id="74260-122">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="74260-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="74260-123">SelectionSets Element Format</span><span class="sxs-lookup"><span data-stu-id="74260-123">SelectionSets Element Format</span></span>](./selectionsets-element-format.md)|<span data-ttu-id="74260-124">Definierar gemensamma uppsättningar med .NET-objekt som kan användas av alla vyer i filen formatering.</span><span class="sxs-lookup"><span data-stu-id="74260-124">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="74260-125">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="74260-125">Remarks</span></span>

<span data-ttu-id="74260-126">Du kan använda inställningarna när du har en uppsättning relaterade objekt som du vill referera till med hjälp av ett enda namn, till exempel en uppsättning objekt som är relaterade genom arv.</span><span class="sxs-lookup"><span data-stu-id="74260-126">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="74260-127">När du definierar dina vyer kan du ange en uppsättning objekt med hjälp av namnet på den val av i stället för att visa en lista över alla objekt i varje vy.</span><span class="sxs-lookup"><span data-stu-id="74260-127">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="74260-128">Vanliga val av uppsättningar anges efter deras namn när du definierar vyer i filen formatering eller definitioner av vyerna.</span><span class="sxs-lookup"><span data-stu-id="74260-128">Common selection sets are specified by their name when defining the views of the formatting file or the definitions of the views.</span></span> <span data-ttu-id="74260-129">I dessa fall kan den `SelectionSetName` underordnat element av den `ViewSelectedBy` och `EntrySelectedBy` anger de element som ska användas.</span><span class="sxs-lookup"><span data-stu-id="74260-129">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` and `EntrySelectedBy` elements specifies the set to be used.</span></span> <span data-ttu-id="74260-130">Mer information om inställningarna finns i [definiera anger av objekt](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="74260-130">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="74260-131">Exempel</span><span class="sxs-lookup"><span data-stu-id="74260-131">Example</span></span>

<span data-ttu-id="74260-132">I följande exempel visas en `SelectionSet` -element som definierar fyra typer av .NET.</span><span class="sxs-lookup"><span data-stu-id="74260-132">The following example shows a `SelectionSet` element that defines four .NET types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="74260-133">Se även</span><span class="sxs-lookup"><span data-stu-id="74260-133">See Also</span></span>

[<span data-ttu-id="74260-134">Definiera inställningarna</span><span class="sxs-lookup"><span data-stu-id="74260-134">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="74260-135">Namnelement av SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="74260-135">Name Element of SelectionSet (Format)</span></span>](./name-element-for-selectionset-format.md)

[<span data-ttu-id="74260-136">SelectionSets Element (Format)</span><span class="sxs-lookup"><span data-stu-id="74260-136">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="74260-137">Typer av Element (Format)</span><span class="sxs-lookup"><span data-stu-id="74260-137">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="74260-138">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="74260-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
