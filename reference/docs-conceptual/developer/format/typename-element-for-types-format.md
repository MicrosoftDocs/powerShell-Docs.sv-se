---
title: Elementet TypeName för typer (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0595b99e-b438-4240-b47b-555cf0316f33
caps.latest.revision: 15
ms.openlocfilehash: bd5baa03c2050b2c3bbe1d7697c253d923175d39
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72358738"
---
# <a name="typename-element-for-types-format"></a><span data-ttu-id="3543c-102">TypeName-element för Types (format)</span><span class="sxs-lookup"><span data-stu-id="3543c-102">TypeName Element for Types (Format)</span></span>

<span data-ttu-id="3543c-103">Anger .NET-typen för ett objekt som tillhör urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="3543c-103">Specifies the .NET type of an object that belongs to the selection set.</span></span>

<span data-ttu-id="3543c-104">Konfigurations element (format) SelectionSets-element (format) SelectionSet-element (format) Type-element (format) element (format) element typ (format)</span><span class="sxs-lookup"><span data-stu-id="3543c-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Types Element (Format) TypeName Element of Types (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3543c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="3543c-105">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3543c-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="3543c-106">Attributes and Elements</span></span>

<span data-ttu-id="3543c-107">I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet i `TypeName`-elementet.</span><span class="sxs-lookup"><span data-stu-id="3543c-107">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span> <span data-ttu-id="3543c-108">Minst ett `TypeName`-element måste ingå i urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="3543c-108">At least one `TypeName` element must be included in the selection set.</span></span>

### <a name="attributes"></a><span data-ttu-id="3543c-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="3543c-109">Attributes</span></span>

<span data-ttu-id="3543c-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="3543c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3543c-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="3543c-111">Child Elements</span></span>

<span data-ttu-id="3543c-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="3543c-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3543c-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="3543c-113">Parent Elements</span></span>

|<span data-ttu-id="3543c-114">Element</span><span class="sxs-lookup"><span data-stu-id="3543c-114">Element</span></span>|<span data-ttu-id="3543c-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="3543c-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3543c-116">Typ element (format)</span><span class="sxs-lookup"><span data-stu-id="3543c-116">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)|<span data-ttu-id="3543c-117">Definierar de .NET-objekt som finns i urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="3543c-117">Defines the .NET objects that are in the selection set.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3543c-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="3543c-118">Text Value</span></span>

<span data-ttu-id="3543c-119">Ange det fullständigt kvalificerade namnet för .NET-typen.</span><span class="sxs-lookup"><span data-stu-id="3543c-119">Specify the fully qualified name for the .NET type.</span></span>

## <a name="remarks"></a><span data-ttu-id="3543c-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="3543c-120">Remarks</span></span>

<span data-ttu-id="3543c-121">Du kan använda urvals uppsättningar när du har en uppsättning relaterade objekt som du vill referera till genom att använda ett enda namn, till exempel en uppsättning objekt som är relaterade till arv.</span><span class="sxs-lookup"><span data-stu-id="3543c-121">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="3543c-122">När du definierar dina vyer kan du ange en uppsättning objekt genom att använda namnet på urvals uppsättningen i stället för att visa alla objekt i varje vy.</span><span class="sxs-lookup"><span data-stu-id="3543c-122">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="3543c-123">Vanliga urvals uppsättningar anges med deras namn när du definierar vyerna för format filen.</span><span class="sxs-lookup"><span data-stu-id="3543c-123">Common selection sets are specified by their name when defining the views of the formatting file.</span></span> <span data-ttu-id="3543c-124">I dessa fall anger `SelectionSetName` underordnat element i `ViewSelectedBy`-elementet för vyn mängden.</span><span class="sxs-lookup"><span data-stu-id="3543c-124">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` element for the view specifies the set.</span></span> <span data-ttu-id="3543c-125">Olika poster i en vy kan dock också ange en markerings uppsättning som endast gäller för posten i vyn.</span><span class="sxs-lookup"><span data-stu-id="3543c-125">However, different entries of a view can also specify a selection set that applies to only that entry of the view.</span></span> <span data-ttu-id="3543c-126">Mer information om urvals uppsättningar finns i [definiera uppsättningar av objekt](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="3543c-126">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="3543c-127">Exempel</span><span class="sxs-lookup"><span data-stu-id="3543c-127">Example</span></span>

<span data-ttu-id="3543c-128">I följande exempel visas ett `SelectionSet`-element som definierar fyra .NET-typer.</span><span class="sxs-lookup"><span data-stu-id="3543c-128">The following example shows a `SelectionSet` element that defines four .NET types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="3543c-129">Se även</span><span class="sxs-lookup"><span data-stu-id="3543c-129">See Also</span></span>

[<span data-ttu-id="3543c-130">Definiera urvals uppsättningar</span><span class="sxs-lookup"><span data-stu-id="3543c-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="3543c-131">SelectionSet-element (format)</span><span class="sxs-lookup"><span data-stu-id="3543c-131">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="3543c-132">SelectionSets-element (format)</span><span class="sxs-lookup"><span data-stu-id="3543c-132">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="3543c-133">Typ element (format)</span><span class="sxs-lookup"><span data-stu-id="3543c-133">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="3543c-134">Skriva en Windows PowerShell-textfil</span><span class="sxs-lookup"><span data-stu-id="3543c-134">Writing a Windows PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
