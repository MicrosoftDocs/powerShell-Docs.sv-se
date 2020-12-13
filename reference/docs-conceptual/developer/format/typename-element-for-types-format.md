---
ms.date: 09/13/2016
ms.topic: reference
title: TypeName-element för Types (format)
description: TypeName-element för Types (format)
ms.openlocfilehash: c656b8e7e5877b72ff2164e5b417857273cada61
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664619"
---
# <a name="typename-element-for-types-format"></a><span data-ttu-id="8fd44-103">TypeName-element för Types (format)</span><span class="sxs-lookup"><span data-stu-id="8fd44-103">TypeName Element for Types (Format)</span></span>

<span data-ttu-id="8fd44-104">Anger .NET-typen för ett objekt som tillhör urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="8fd44-104">Specifies the .NET type of an object that belongs to the selection set.</span></span>

<span data-ttu-id="8fd44-105">Konfigurations element (format) SelectionSets-element (format) SelectionSet-element (format) Type-element (format) element (format) element typ (format)</span><span class="sxs-lookup"><span data-stu-id="8fd44-105">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Types Element (Format) TypeName Element of Types (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8fd44-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="8fd44-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8fd44-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="8fd44-107">Attributes and Elements</span></span>

<span data-ttu-id="8fd44-108">I följande avsnitt beskrivs attributen, underordnade element och `TypeName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="8fd44-108">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span> <span data-ttu-id="8fd44-109">Minst ett `TypeName` element måste ingå i urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="8fd44-109">At least one `TypeName` element must be included in the selection set.</span></span>

### <a name="attributes"></a><span data-ttu-id="8fd44-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="8fd44-110">Attributes</span></span>

<span data-ttu-id="8fd44-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="8fd44-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8fd44-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="8fd44-112">Child Elements</span></span>

<span data-ttu-id="8fd44-113">Inga.</span><span class="sxs-lookup"><span data-stu-id="8fd44-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8fd44-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="8fd44-114">Parent Elements</span></span>

|<span data-ttu-id="8fd44-115">Element</span><span class="sxs-lookup"><span data-stu-id="8fd44-115">Element</span></span>|<span data-ttu-id="8fd44-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8fd44-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8fd44-117">Typ element (format)</span><span class="sxs-lookup"><span data-stu-id="8fd44-117">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)|<span data-ttu-id="8fd44-118">Definierar de .NET-objekt som finns i urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="8fd44-118">Defines the .NET objects that are in the selection set.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8fd44-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="8fd44-119">Text Value</span></span>

<span data-ttu-id="8fd44-120">Ange det fullständigt kvalificerade namnet för .NET-typen.</span><span class="sxs-lookup"><span data-stu-id="8fd44-120">Specify the fully qualified name for the .NET type.</span></span>

## <a name="remarks"></a><span data-ttu-id="8fd44-121">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="8fd44-121">Remarks</span></span>

<span data-ttu-id="8fd44-122">Du kan använda urvals uppsättningar när du har en uppsättning relaterade objekt som du vill referera till genom att använda ett enda namn, till exempel en uppsättning objekt som är relaterade till arv.</span><span class="sxs-lookup"><span data-stu-id="8fd44-122">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="8fd44-123">När du definierar dina vyer kan du ange en uppsättning objekt genom att använda namnet på urvals uppsättningen i stället för att visa alla objekt i varje vy.</span><span class="sxs-lookup"><span data-stu-id="8fd44-123">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="8fd44-124">Vanliga urvals uppsättningar anges med deras namn när du definierar vyerna för format filen.</span><span class="sxs-lookup"><span data-stu-id="8fd44-124">Common selection sets are specified by their name when defining the views of the formatting file.</span></span> <span data-ttu-id="8fd44-125">I dessa fall anger det `SelectionSetName` underordnade elementet för `ViewSelectedBy` vyns element uppsättning.</span><span class="sxs-lookup"><span data-stu-id="8fd44-125">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` element for the view specifies the set.</span></span> <span data-ttu-id="8fd44-126">Olika poster i en vy kan dock också ange en markerings uppsättning som endast gäller för posten i vyn.</span><span class="sxs-lookup"><span data-stu-id="8fd44-126">However, different entries of a view can also specify a selection set that applies to only that entry of the view.</span></span> <span data-ttu-id="8fd44-127">Mer information om urvals uppsättningar finns i [definiera uppsättningar av objekt](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="8fd44-127">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="8fd44-128">Exempel</span><span class="sxs-lookup"><span data-stu-id="8fd44-128">Example</span></span>

<span data-ttu-id="8fd44-129">I följande exempel visas ett- `SelectionSet` element som definierar fyra .net-typer.</span><span class="sxs-lookup"><span data-stu-id="8fd44-129">The following example shows a `SelectionSet` element that defines four .NET types.</span></span>

```
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

## <a name="see-also"></a><span data-ttu-id="8fd44-130">Se även</span><span class="sxs-lookup"><span data-stu-id="8fd44-130">See Also</span></span>

[<span data-ttu-id="8fd44-131">Definiera valuppsättningar</span><span class="sxs-lookup"><span data-stu-id="8fd44-131">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="8fd44-132">SelectionSet-element (format)</span><span class="sxs-lookup"><span data-stu-id="8fd44-132">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="8fd44-133">SelectionSets-element (format)</span><span class="sxs-lookup"><span data-stu-id="8fd44-133">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="8fd44-134">Typ element (format)</span><span class="sxs-lookup"><span data-stu-id="8fd44-134">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="8fd44-135">Skriva en Windows PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="8fd44-135">Writing a Windows PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
