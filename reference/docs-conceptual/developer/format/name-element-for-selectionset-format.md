---
ms.date: 09/13/2016
ms.topic: reference
title: Name-element för SelectionSet (format)
description: Name-element för SelectionSet (format)
ms.openlocfilehash: 98c13be6ea352055231fbdb3a60f0eb508f661b8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666474"
---
# <a name="name-element-for-selectionset-format"></a><span data-ttu-id="0f647-103">Name-element för SelectionSet (format)</span><span class="sxs-lookup"><span data-stu-id="0f647-103">Name Element for SelectionSet (Format)</span></span>

<span data-ttu-id="0f647-104">Anger namnet som används för att referera till urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="0f647-104">Specifies the name used to reference the selection set.</span></span>

<span data-ttu-id="0f647-105">Konfigurations element (format) SelectionSets-element (format) SelectionSet element (format), element för SelectionSet (format)</span><span class="sxs-lookup"><span data-stu-id="0f647-105">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Name Element of SelectionSet (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0f647-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="0f647-106">Syntax</span></span>

```xml
<Name>Name of selection set</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0f647-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="0f647-107">Attributes and Elements</span></span>

<span data-ttu-id="0f647-108">I följande avsnitt beskrivs attributen, underordnade element och `Name` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="0f647-108">The following sections describe the attributes, child elements, and parent element of the `Name` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0f647-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="0f647-109">Attributes</span></span>

<span data-ttu-id="0f647-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="0f647-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0f647-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="0f647-111">Child Elements</span></span>

<span data-ttu-id="0f647-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="0f647-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0f647-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="0f647-113">Parent Elements</span></span>

|<span data-ttu-id="0f647-114">Element</span><span class="sxs-lookup"><span data-stu-id="0f647-114">Element</span></span>|<span data-ttu-id="0f647-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0f647-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0f647-116">SelectionSet-element (format)</span><span class="sxs-lookup"><span data-stu-id="0f647-116">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="0f647-117">Definierar en enda uppsättning .NET-objekt som kan refereras till i uppsättningens namn.</span><span class="sxs-lookup"><span data-stu-id="0f647-117">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0f647-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="0f647-118">Text Value</span></span>

<span data-ttu-id="0f647-119">Ange det namn som ska referera till urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="0f647-119">Specify the name to reference the selection set.</span></span> <span data-ttu-id="0f647-120">Det finns inga begränsningar för vilka tecken som kan användas.</span><span class="sxs-lookup"><span data-stu-id="0f647-120">There are no restrictions as to what characters can be used.</span></span>

## <a name="remarks"></a><span data-ttu-id="0f647-121">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="0f647-121">Remarks</span></span>

<span data-ttu-id="0f647-122">Namnet som anges här används i- `SelectionSetName` elementet.</span><span class="sxs-lookup"><span data-stu-id="0f647-122">The name specified here is used in the `SelectionSetName` element.</span></span> <span data-ttu-id="0f647-123">Den urvals uppsättning som kan användas av en vy, genom en definition av en vy (vyer kan ha flera definitioner) eller när du anger ett urvals villkor.</span><span class="sxs-lookup"><span data-stu-id="0f647-123">The selection set that can be used by a view, by a definition of a view (views can have multiple definitions), or when specifying a selection condition.</span></span> <span data-ttu-id="0f647-124">Mer information om urvals uppsättningar finns i [definiera uppsättningar av objekt](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="0f647-124">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="0f647-125">Exempel</span><span class="sxs-lookup"><span data-stu-id="0f647-125">Example</span></span>

<span data-ttu-id="0f647-126">Det här exemplet visar ett- `SelectionSet` element som definierar fyra .net-typer.</span><span class="sxs-lookup"><span data-stu-id="0f647-126">This example shows a `SelectionSet` element that defines four .NET types.</span></span> <span data-ttu-id="0f647-127">Namnet på urvals uppsättningen är "FileSystemTypes".</span><span class="sxs-lookup"><span data-stu-id="0f647-127">The name of the selection set is "FileSystemTypes".</span></span>

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

## <a name="see-also"></a><span data-ttu-id="0f647-128">Se även</span><span class="sxs-lookup"><span data-stu-id="0f647-128">See Also</span></span>

[<span data-ttu-id="0f647-129">Definiera valuppsättningar</span><span class="sxs-lookup"><span data-stu-id="0f647-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="0f647-130">SelectionSet-element (format)</span><span class="sxs-lookup"><span data-stu-id="0f647-130">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="0f647-131">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="0f647-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
