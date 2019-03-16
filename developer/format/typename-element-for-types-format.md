---
title: TypeName-Element för typer (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0595b99e-b438-4240-b47b-555cf0316f33
caps.latest.revision: 15
ms.openlocfilehash: bd5baa03c2050b2c3bbe1d7697c253d923175d39
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057934"
---
# <a name="typename-element-for-types-format"></a><span data-ttu-id="cbde8-102">TypeName-element för Types (format)</span><span class="sxs-lookup"><span data-stu-id="cbde8-102">TypeName Element for Types (Format)</span></span>

<span data-ttu-id="cbde8-103">Anger .NET-typ för ett objekt som hör till val av uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="cbde8-103">Specifies the .NET type of an object that belongs to the selection set.</span></span>

<span data-ttu-id="cbde8-104">Elementet (Format) SelectionSets Element (Format) SelectionSet konfigurationselement (Format) datatyper Element (Format) TypeName Element av typer (Format)</span><span class="sxs-lookup"><span data-stu-id="cbde8-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Types Element (Format) TypeName Element of Types (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cbde8-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="cbde8-105">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cbde8-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="cbde8-106">Attributes and Elements</span></span>

<span data-ttu-id="cbde8-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `TypeName` element.</span><span class="sxs-lookup"><span data-stu-id="cbde8-107">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span> <span data-ttu-id="cbde8-108">Minst en `TypeName` elementet måste finnas med i val av uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="cbde8-108">At least one `TypeName` element must be included in the selection set.</span></span>

### <a name="attributes"></a><span data-ttu-id="cbde8-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="cbde8-109">Attributes</span></span>

<span data-ttu-id="cbde8-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="cbde8-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cbde8-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="cbde8-111">Child Elements</span></span>

<span data-ttu-id="cbde8-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="cbde8-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="cbde8-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="cbde8-113">Parent Elements</span></span>

|<span data-ttu-id="cbde8-114">Element</span><span class="sxs-lookup"><span data-stu-id="cbde8-114">Element</span></span>|<span data-ttu-id="cbde8-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="cbde8-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cbde8-116">Typer av Element (Format)</span><span class="sxs-lookup"><span data-stu-id="cbde8-116">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)|<span data-ttu-id="cbde8-117">Definierar de .NET-objekt som är i urvalet inställda.</span><span class="sxs-lookup"><span data-stu-id="cbde8-117">Defines the .NET objects that are in the selection set.</span></span>|

## <a name="text-value"></a><span data-ttu-id="cbde8-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="cbde8-118">Text Value</span></span>

<span data-ttu-id="cbde8-119">Ange det fullständigt kvalificerade namnet för .NET-typen.</span><span class="sxs-lookup"><span data-stu-id="cbde8-119">Specify the fully qualified name for the .NET type.</span></span>

## <a name="remarks"></a><span data-ttu-id="cbde8-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="cbde8-120">Remarks</span></span>

<span data-ttu-id="cbde8-121">Du kan använda inställningarna när du har en uppsättning relaterade objekt som du vill referera till med hjälp av ett enda namn, till exempel en uppsättning objekt som är relaterade genom arv.</span><span class="sxs-lookup"><span data-stu-id="cbde8-121">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="cbde8-122">När du definierar dina vyer kan du ange en uppsättning objekt med hjälp av namnet på den val av i stället för att visa en lista över alla objekt i varje vy.</span><span class="sxs-lookup"><span data-stu-id="cbde8-122">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="cbde8-123">Vanliga val av uppsättningar anges efter deras namn när du definierar vyer i filen formatering.</span><span class="sxs-lookup"><span data-stu-id="cbde8-123">Common selection sets are specified by their name when defining the views of the formatting file.</span></span> <span data-ttu-id="cbde8-124">I dessa fall kan den `SelectionSetName` underordnat element av den `ViewSelectedBy` element för vyn anger.</span><span class="sxs-lookup"><span data-stu-id="cbde8-124">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` element for the view specifies the set.</span></span> <span data-ttu-id="cbde8-125">Olika poster i en vy kan även ange en uppsättning för val av som gäller för den aktuella posten för vyn.</span><span class="sxs-lookup"><span data-stu-id="cbde8-125">However, different entries of a view can also specify a selection set that applies to only that entry of the view.</span></span> <span data-ttu-id="cbde8-126">Mer information om inställningarna finns i [definiera anger av objekt](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="cbde8-126">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="cbde8-127">Exempel</span><span class="sxs-lookup"><span data-stu-id="cbde8-127">Example</span></span>

<span data-ttu-id="cbde8-128">I följande exempel visas en `SelectionSet` -element som definierar fyra typer av .NET.</span><span class="sxs-lookup"><span data-stu-id="cbde8-128">The following example shows a `SelectionSet` element that defines four .NET types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="cbde8-129">Se även</span><span class="sxs-lookup"><span data-stu-id="cbde8-129">See Also</span></span>

[<span data-ttu-id="cbde8-130">Definiera inställningarna</span><span class="sxs-lookup"><span data-stu-id="cbde8-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="cbde8-131">SelectionSet Element (Format)</span><span class="sxs-lookup"><span data-stu-id="cbde8-131">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="cbde8-132">SelectionSets Element (Format)</span><span class="sxs-lookup"><span data-stu-id="cbde8-132">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="cbde8-133">Typer av Element (Format)</span><span class="sxs-lookup"><span data-stu-id="cbde8-133">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="cbde8-134">Skriva ett Windows PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="cbde8-134">Writing a Windows PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
