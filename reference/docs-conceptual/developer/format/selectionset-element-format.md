---
title: SelectionSet-element (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 848e7acd-d578-4fd1-a575-c0c3b9b5e68a
caps.latest.revision: 17
ms.openlocfilehash: c809aa6c3a40d16cfd2fd99065a846d265ec0f61
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72358869"
---
# <a name="selectionset-element-format"></a><span data-ttu-id="6dfd9-102">SelectionSet-element (format)</span><span class="sxs-lookup"><span data-stu-id="6dfd9-102">SelectionSet Element (Format)</span></span>

<span data-ttu-id="6dfd9-103">Definierar en uppsättning .NET-objekt som kan refereras till i uppsättningens namn.</span><span class="sxs-lookup"><span data-stu-id="6dfd9-103">Defines a set of .NET objects that can be referenced by the name of the set.</span></span>

<span data-ttu-id="6dfd9-104">Konfigurations element (format) SelectionSets-element (format) SelectionSet-element (format)</span><span class="sxs-lookup"><span data-stu-id="6dfd9-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6dfd9-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="6dfd9-105">Syntax</span></span>

```xml
<SelectionSet>
  <Name>SelectionSetName</Name>
  <Types>...</Types>
</SelectionSet>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6dfd9-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="6dfd9-106">Attributes and Elements</span></span>

<span data-ttu-id="6dfd9-107">I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet för elementet `SelectionSet`.</span><span class="sxs-lookup"><span data-stu-id="6dfd9-107">The following sections describe the attributes, child elements, and the parent element of the `SelectionSet` element.</span></span> <span data-ttu-id="6dfd9-108">Varje urvals uppsättning måste ha ett namn och måste ange .NET-objekten för uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="6dfd9-108">Each selection set must have a name, and it must specify the .NET objects of the set.</span></span>

### <a name="attributes"></a><span data-ttu-id="6dfd9-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="6dfd9-109">Attributes</span></span>

<span data-ttu-id="6dfd9-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="6dfd9-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6dfd9-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="6dfd9-111">Child Elements</span></span>

|<span data-ttu-id="6dfd9-112">Element</span><span class="sxs-lookup"><span data-stu-id="6dfd9-112">Element</span></span>|<span data-ttu-id="6dfd9-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="6dfd9-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6dfd9-114">Namn element för SelectionSet (format)</span><span class="sxs-lookup"><span data-stu-id="6dfd9-114">Name Element for SelectionSet (Format)</span></span>](./name-element-for-selectionset-format.md)|<span data-ttu-id="6dfd9-115">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="6dfd9-115">Required element.</span></span><br /><br /> <span data-ttu-id="6dfd9-116">Anger namnet som används för att referera till urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="6dfd9-116">Specifies the name used to reference the selection set.</span></span>|
|[<span data-ttu-id="6dfd9-117">Typ element (format)</span><span class="sxs-lookup"><span data-stu-id="6dfd9-117">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)|<span data-ttu-id="6dfd9-118">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="6dfd9-118">Required element.</span></span><br /><br /> <span data-ttu-id="6dfd9-119">Definierar de .NET-objekt som finns i urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="6dfd9-119">Defines the .NET objects that are in the selection set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6dfd9-120">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="6dfd9-120">Parent Elements</span></span>

|<span data-ttu-id="6dfd9-121">Element</span><span class="sxs-lookup"><span data-stu-id="6dfd9-121">Element</span></span>|<span data-ttu-id="6dfd9-122">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="6dfd9-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6dfd9-123">SelectionSets element format</span><span class="sxs-lookup"><span data-stu-id="6dfd9-123">SelectionSets Element Format</span></span>](./selectionsets-element-format.md)|<span data-ttu-id="6dfd9-124">Definierar de gemensamma uppsättningar av .NET-objekt som kan användas av alla vyer i format filen.</span><span class="sxs-lookup"><span data-stu-id="6dfd9-124">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6dfd9-125">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="6dfd9-125">Remarks</span></span>

<span data-ttu-id="6dfd9-126">Du kan använda urvals uppsättningar när du har en uppsättning relaterade objekt som du vill referera till genom att använda ett enda namn, till exempel en uppsättning objekt som är relaterade till arv.</span><span class="sxs-lookup"><span data-stu-id="6dfd9-126">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="6dfd9-127">När du definierar dina vyer kan du ange en uppsättning objekt genom att använda namnet på urvals uppsättningen i stället för att visa alla objekt i varje vy.</span><span class="sxs-lookup"><span data-stu-id="6dfd9-127">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="6dfd9-128">Vanliga urvals uppsättningar anges med deras namn när du definierar vyerna för format filen eller definitionerna för vyerna.</span><span class="sxs-lookup"><span data-stu-id="6dfd9-128">Common selection sets are specified by their name when defining the views of the formatting file or the definitions of the views.</span></span> <span data-ttu-id="6dfd9-129">I dessa fall anger det underordnade elementet `SelectionSetName` för elementen `ViewSelectedBy` och `EntrySelectedBy` den uppsättning som ska användas.</span><span class="sxs-lookup"><span data-stu-id="6dfd9-129">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` and `EntrySelectedBy` elements specifies the set to be used.</span></span> <span data-ttu-id="6dfd9-130">Mer information om urvals uppsättningar finns i [definiera uppsättningar av objekt](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="6dfd9-130">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="6dfd9-131">Exempel</span><span class="sxs-lookup"><span data-stu-id="6dfd9-131">Example</span></span>

<span data-ttu-id="6dfd9-132">I följande exempel visas ett `SelectionSet`-element som definierar fyra .NET-typer.</span><span class="sxs-lookup"><span data-stu-id="6dfd9-132">The following example shows a `SelectionSet` element that defines four .NET types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="6dfd9-133">Se även</span><span class="sxs-lookup"><span data-stu-id="6dfd9-133">See Also</span></span>

[<span data-ttu-id="6dfd9-134">Definiera urvals uppsättningar</span><span class="sxs-lookup"><span data-stu-id="6dfd9-134">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="6dfd9-135">Namn element i SelectionSet (format)</span><span class="sxs-lookup"><span data-stu-id="6dfd9-135">Name Element of SelectionSet (Format)</span></span>](./name-element-for-selectionset-format.md)

[<span data-ttu-id="6dfd9-136">SelectionSets-element (format)</span><span class="sxs-lookup"><span data-stu-id="6dfd9-136">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="6dfd9-137">Typ element (format)</span><span class="sxs-lookup"><span data-stu-id="6dfd9-137">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="6dfd9-138">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="6dfd9-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
