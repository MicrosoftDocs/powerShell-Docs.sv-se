---
title: Namn element för SelectionSet (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 1fc33eeb87a6912ed6793629ab1969cd65b5f0c5
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773308"
---
# <a name="name-element-for-selectionset-format"></a><span data-ttu-id="1aba8-102">Name-element för SelectionSet (format)</span><span class="sxs-lookup"><span data-stu-id="1aba8-102">Name Element for SelectionSet (Format)</span></span>

<span data-ttu-id="1aba8-103">Anger namnet som används för att referera till urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="1aba8-103">Specifies the name used to reference the selection set.</span></span>

<span data-ttu-id="1aba8-104">Konfigurations element (format) SelectionSets-element (format) SelectionSet element (format), element för SelectionSet (format)</span><span class="sxs-lookup"><span data-stu-id="1aba8-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Name Element of SelectionSet (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1aba8-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="1aba8-105">Syntax</span></span>

```xml
<Name>Name of selection set</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1aba8-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="1aba8-106">Attributes and Elements</span></span>

<span data-ttu-id="1aba8-107">I följande avsnitt beskrivs attributen, underordnade element och `Name` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="1aba8-107">The following sections describe the attributes, child elements, and parent element of the `Name` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1aba8-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="1aba8-108">Attributes</span></span>

<span data-ttu-id="1aba8-109">Inga.</span><span class="sxs-lookup"><span data-stu-id="1aba8-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1aba8-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="1aba8-110">Child Elements</span></span>

<span data-ttu-id="1aba8-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="1aba8-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1aba8-112">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="1aba8-112">Parent Elements</span></span>

|<span data-ttu-id="1aba8-113">Element</span><span class="sxs-lookup"><span data-stu-id="1aba8-113">Element</span></span>|<span data-ttu-id="1aba8-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="1aba8-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1aba8-115">SelectionSet-element (format)</span><span class="sxs-lookup"><span data-stu-id="1aba8-115">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="1aba8-116">Definierar en enda uppsättning .NET-objekt som kan refereras till i uppsättningens namn.</span><span class="sxs-lookup"><span data-stu-id="1aba8-116">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1aba8-117">Textvärde</span><span class="sxs-lookup"><span data-stu-id="1aba8-117">Text Value</span></span>

<span data-ttu-id="1aba8-118">Ange det namn som ska referera till urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="1aba8-118">Specify the name to reference the selection set.</span></span> <span data-ttu-id="1aba8-119">Det finns inga begränsningar för vilka tecken som kan användas.</span><span class="sxs-lookup"><span data-stu-id="1aba8-119">There are no restrictions as to what characters can be used.</span></span>

## <a name="remarks"></a><span data-ttu-id="1aba8-120">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="1aba8-120">Remarks</span></span>

<span data-ttu-id="1aba8-121">Namnet som anges här används i- `SelectionSetName` elementet.</span><span class="sxs-lookup"><span data-stu-id="1aba8-121">The name specified here is used in the `SelectionSetName` element.</span></span> <span data-ttu-id="1aba8-122">Den urvals uppsättning som kan användas av en vy, genom en definition av en vy (vyer kan ha flera definitioner) eller när du anger ett urvals villkor.</span><span class="sxs-lookup"><span data-stu-id="1aba8-122">The selection set that can be used by a view, by a definition of a view (views can have multiple definitions), or when specifying a selection condition.</span></span> <span data-ttu-id="1aba8-123">Mer information om urvals uppsättningar finns i [definiera uppsättningar av objekt](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="1aba8-123">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="1aba8-124">Exempel</span><span class="sxs-lookup"><span data-stu-id="1aba8-124">Example</span></span>

<span data-ttu-id="1aba8-125">Det här exemplet visar ett- `SelectionSet` element som definierar fyra .net-typer.</span><span class="sxs-lookup"><span data-stu-id="1aba8-125">This example shows a `SelectionSet` element that defines four .NET types.</span></span> <span data-ttu-id="1aba8-126">Namnet på urvals uppsättningen är "FileSystemTypes".</span><span class="sxs-lookup"><span data-stu-id="1aba8-126">The name of the selection set is "FileSystemTypes".</span></span>

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

## <a name="see-also"></a><span data-ttu-id="1aba8-127">Se även</span><span class="sxs-lookup"><span data-stu-id="1aba8-127">See Also</span></span>

[<span data-ttu-id="1aba8-128">Definiera valuppsättningar</span><span class="sxs-lookup"><span data-stu-id="1aba8-128">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="1aba8-129">SelectionSet-element (format)</span><span class="sxs-lookup"><span data-stu-id="1aba8-129">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="1aba8-130">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="1aba8-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
