---
title: Typ element för SelectionSet (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4606fec0-ff31-4d36-af68-227405335ec3
caps.latest.revision: 15
ms.openlocfilehash: 0427367efa2c8a7e352d718706d1341a0c8e3621
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72358744"
---
# <a name="types-element-for-selectionset-format"></a><span data-ttu-id="1d757-102">Types-element för SelectionSet (format)</span><span class="sxs-lookup"><span data-stu-id="1d757-102">Types Element for SelectionSet (Format)</span></span>

<span data-ttu-id="1d757-103">Definierar de .NET-objekt som finns i urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="1d757-103">Defines the .NET objects that are in the selection set.</span></span>

<span data-ttu-id="1d757-104">Konfigurations element (format) SelectionSets-element (format) SelectionSet element (format) element (format)</span><span class="sxs-lookup"><span data-stu-id="1d757-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Types Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1d757-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="1d757-105">Syntax</span></span>

```xml
<Types>
  <TypeName>Nameof.NetType</TypeName>
</Types>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="1d757-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="1d757-106">Attributes and Elements</span></span>

<span data-ttu-id="1d757-107">I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet i `Types`-elementet.</span><span class="sxs-lookup"><span data-stu-id="1d757-107">The following sections describe the attributes, child elements, and the parent element of the `Types` element.</span></span> <span data-ttu-id="1d757-108">Det måste finnas minst ett underordnat element, men det finns ingen övre gräns för antalet underordnade element som kan läggas till.</span><span class="sxs-lookup"><span data-stu-id="1d757-108">There must be at least one child element, but there is no maximum limit to the number of child elements that can be added.</span></span>

### <a name="attributes"></a><span data-ttu-id="1d757-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="1d757-109">Attributes</span></span>

<span data-ttu-id="1d757-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="1d757-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1d757-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="1d757-111">Child Elements</span></span>

|<span data-ttu-id="1d757-112">Element</span><span class="sxs-lookup"><span data-stu-id="1d757-112">Element</span></span>|<span data-ttu-id="1d757-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="1d757-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1d757-114">Element av typen TypeName (format)</span><span class="sxs-lookup"><span data-stu-id="1d757-114">TypeName Element of Types (Format)</span></span>](./typename-element-for-types-format.md)|<span data-ttu-id="1d757-115">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="1d757-115">Required element.</span></span><br /><br /> <span data-ttu-id="1d757-116">Anger det .NET-objekt som tillhör urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="1d757-116">Specifies the .NET object that belongs to the selection set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="1d757-117">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="1d757-117">Parent Elements</span></span>

|<span data-ttu-id="1d757-118">Element</span><span class="sxs-lookup"><span data-stu-id="1d757-118">Element</span></span>|<span data-ttu-id="1d757-119">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="1d757-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1d757-120">SelectionSet-element (format)</span><span class="sxs-lookup"><span data-stu-id="1d757-120">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="1d757-121">Definierar en uppsättning .NET-objekt som kan refereras till i uppsättningens namn.</span><span class="sxs-lookup"><span data-stu-id="1d757-121">Defines a set of .NET objects that can be referenced by the name of the set.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1d757-122">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="1d757-122">Remarks</span></span>

<span data-ttu-id="1d757-123">De objekt som definieras av det här elementet utgör en urvals uppsättning som kan användas av en vy, i en definition av en vy (vyer kan ha flera definitioner) eller när du anger ett urvals villkor.</span><span class="sxs-lookup"><span data-stu-id="1d757-123">The objects defined by this element make up a selection set that can be used by a view, by a definition of a view (views can have multiple definitions), or when specifying a selection condition.</span></span>  <span data-ttu-id="1d757-124">Mer information om urvals uppsättningar finns i [definiera uppsättningar av objekt](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="1d757-124">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="1d757-125">Exempel</span><span class="sxs-lookup"><span data-stu-id="1d757-125">Example</span></span>

<span data-ttu-id="1d757-126">I det här exemplet visas ett `SelectionSet`-element som definierar fyra .NET-typer.</span><span class="sxs-lookup"><span data-stu-id="1d757-126">This example shows a `SelectionSet` element that defines four .NET types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="1d757-127">Se även</span><span class="sxs-lookup"><span data-stu-id="1d757-127">See Also</span></span>

[<span data-ttu-id="1d757-128">Definiera uppsättningar av objekt</span><span class="sxs-lookup"><span data-stu-id="1d757-128">Defining Sets of Objects</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="1d757-129">SelectionSet-element (format)</span><span class="sxs-lookup"><span data-stu-id="1d757-129">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="1d757-130">Element av typen TypeName (format)</span><span class="sxs-lookup"><span data-stu-id="1d757-130">TypeName Element of Types (Format)</span></span>](./typename-element-for-types-format.md)

[<span data-ttu-id="1d757-131">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="1d757-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
