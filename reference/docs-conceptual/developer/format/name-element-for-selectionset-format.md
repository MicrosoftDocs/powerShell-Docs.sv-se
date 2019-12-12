---
title: Namn element för SelectionSet (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 914917f7-0efc-4d1f-88bd-de714bedd98f
caps.latest.revision: 15
ms.openlocfilehash: 29dbdbd335511e4ca2706a625541554825838f23
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354294"
---
# <a name="name-element-for-selectionset-format"></a><span data-ttu-id="77570-102">Name-element för SelectionSet (format)</span><span class="sxs-lookup"><span data-stu-id="77570-102">Name Element for SelectionSet (Format)</span></span>

<span data-ttu-id="77570-103">Anger namnet som används för att referera till urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="77570-103">Specifies the name used to reference the selection set.</span></span>

<span data-ttu-id="77570-104">Konfigurations element (format) SelectionSets-element (format) SelectionSet element (format), element för SelectionSet (format)</span><span class="sxs-lookup"><span data-stu-id="77570-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Name Element of SelectionSet (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="77570-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="77570-105">Syntax</span></span>

```xml
<Name>Name of selection set</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="77570-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="77570-106">Attributes and Elements</span></span>

<span data-ttu-id="77570-107">I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet i `Name`-elementet.</span><span class="sxs-lookup"><span data-stu-id="77570-107">The following sections describe the attributes, child elements, and parent element of the `Name` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="77570-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="77570-108">Attributes</span></span>

<span data-ttu-id="77570-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="77570-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="77570-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="77570-110">Child Elements</span></span>

<span data-ttu-id="77570-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="77570-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="77570-112">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="77570-112">Parent Elements</span></span>

|<span data-ttu-id="77570-113">Element</span><span class="sxs-lookup"><span data-stu-id="77570-113">Element</span></span>|<span data-ttu-id="77570-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="77570-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="77570-115">SelectionSet-element (format)</span><span class="sxs-lookup"><span data-stu-id="77570-115">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="77570-116">Definierar en enda uppsättning .NET-objekt som kan refereras till i uppsättningens namn.</span><span class="sxs-lookup"><span data-stu-id="77570-116">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

## <a name="text-value"></a><span data-ttu-id="77570-117">Textvärde</span><span class="sxs-lookup"><span data-stu-id="77570-117">Text Value</span></span>

<span data-ttu-id="77570-118">Ange det namn som ska referera till urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="77570-118">Specify the name to reference the selection set.</span></span> <span data-ttu-id="77570-119">Det finns inga begränsningar för vilka tecken som kan användas.</span><span class="sxs-lookup"><span data-stu-id="77570-119">There are no restrictions as to what characters can be used.</span></span>

## <a name="remarks"></a><span data-ttu-id="77570-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="77570-120">Remarks</span></span>

<span data-ttu-id="77570-121">Namnet som anges här används i `SelectionSetName`-elementet.</span><span class="sxs-lookup"><span data-stu-id="77570-121">The name specified here is used in the `SelectionSetName` element.</span></span> <span data-ttu-id="77570-122">Den urvals uppsättning som kan användas av en vy, genom en definition av en vy (vyer kan ha flera definitioner) eller när du anger ett urvals villkor.</span><span class="sxs-lookup"><span data-stu-id="77570-122">The selection set that can be used by a view, by a definition of a view (views can have multiple definitions), or when specifying a selection condition.</span></span> <span data-ttu-id="77570-123">Mer information om urvals uppsättningar finns i [definiera uppsättningar av objekt](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="77570-123">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="77570-124">Exempel</span><span class="sxs-lookup"><span data-stu-id="77570-124">Example</span></span>

<span data-ttu-id="77570-125">I det här exemplet visas ett `SelectionSet`-element som definierar fyra .NET-typer.</span><span class="sxs-lookup"><span data-stu-id="77570-125">This example shows a `SelectionSet` element that defines four .NET types.</span></span> <span data-ttu-id="77570-126">Namnet på urvals uppsättningen är "FileSystemTypes".</span><span class="sxs-lookup"><span data-stu-id="77570-126">The name of the selection set is "FileSystemTypes".</span></span>

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

## <a name="see-also"></a><span data-ttu-id="77570-127">Se även</span><span class="sxs-lookup"><span data-stu-id="77570-127">See Also</span></span>

[<span data-ttu-id="77570-128">Definiera urvals uppsättningar</span><span class="sxs-lookup"><span data-stu-id="77570-128">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="77570-129">SelectionSet-element (format)</span><span class="sxs-lookup"><span data-stu-id="77570-129">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="77570-130">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="77570-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
