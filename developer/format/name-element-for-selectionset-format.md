---
title: Namn på Element för SelectionSet (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 914917f7-0efc-4d1f-88bd-de714bedd98f
caps.latest.revision: 15
ms.openlocfilehash: 29dbdbd335511e4ca2706a625541554825838f23
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848330"
---
# <a name="name-element-for-selectionset-format"></a><span data-ttu-id="b5ab1-102">Name-element för SelectionSet (format)</span><span class="sxs-lookup"><span data-stu-id="b5ab1-102">Name Element for SelectionSet (Format)</span></span>

<span data-ttu-id="b5ab1-103">Anger namnet som refererar till uppsättningen val.</span><span class="sxs-lookup"><span data-stu-id="b5ab1-103">Specifies the name used to reference the selection set.</span></span>

<span data-ttu-id="b5ab1-104">Elementet (Format) SelectionSets Element (Format) SelectionSet Element (Format) namn konfigurationselement för SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="b5ab1-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Name Element of SelectionSet (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b5ab1-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="b5ab1-105">Syntax</span></span>

```xml
<Name>Name of selection set</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b5ab1-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="b5ab1-106">Attributes and Elements</span></span>

<span data-ttu-id="b5ab1-107">I följande avsnitt beskrivs de attribut och underordnade element överordnade elementet i den `Name` Element.</span><span class="sxs-lookup"><span data-stu-id="b5ab1-107">The following sections describe the attributes, child elements, and parent element of the `Name` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b5ab1-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="b5ab1-108">Attributes</span></span>

<span data-ttu-id="b5ab1-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="b5ab1-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b5ab1-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="b5ab1-110">Child Elements</span></span>

<span data-ttu-id="b5ab1-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="b5ab1-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b5ab1-112">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="b5ab1-112">Parent Elements</span></span>

|<span data-ttu-id="b5ab1-113">Element</span><span class="sxs-lookup"><span data-stu-id="b5ab1-113">Element</span></span>|<span data-ttu-id="b5ab1-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b5ab1-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b5ab1-115">SelectionSet Element (Format)</span><span class="sxs-lookup"><span data-stu-id="b5ab1-115">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="b5ab1-116">Definierar en uppsättning med .NET-objekt som kan refereras av namnet på uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="b5ab1-116">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b5ab1-117">Textvärde</span><span class="sxs-lookup"><span data-stu-id="b5ab1-117">Text Value</span></span>

<span data-ttu-id="b5ab1-118">Ange ett namn för att referera till val av uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="b5ab1-118">Specify the name to reference the selection set.</span></span> <span data-ttu-id="b5ab1-119">Det finns inga begränsningar vad gäller vilka tecken som kan användas.</span><span class="sxs-lookup"><span data-stu-id="b5ab1-119">There are no restrictions as to what characters can be used.</span></span>

## <a name="remarks"></a><span data-ttu-id="b5ab1-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="b5ab1-120">Remarks</span></span>

<span data-ttu-id="b5ab1-121">Namnet som anges här används i den `SelectionSetName` element.</span><span class="sxs-lookup"><span data-stu-id="b5ab1-121">The name specified here is used in the `SelectionSetName` element.</span></span> <span data-ttu-id="b5ab1-122">Val av uppsättningen som kan användas av en vy av en definition av en vy (vyer kan ha flera definitioner), eller när du anger ett val av villkor.</span><span class="sxs-lookup"><span data-stu-id="b5ab1-122">The selection set that can be used by a view, by a definition of a view (views can have multiple definitions), or when specifying a selection condition.</span></span> <span data-ttu-id="b5ab1-123">Mer information om inställningarna finns i [definiera anger av objekt](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="b5ab1-123">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="b5ab1-124">Exempel</span><span class="sxs-lookup"><span data-stu-id="b5ab1-124">Example</span></span>

<span data-ttu-id="b5ab1-125">Det här exemplet visar en `SelectionSet` -element som definierar fyra typer av .NET.</span><span class="sxs-lookup"><span data-stu-id="b5ab1-125">This example shows a `SelectionSet` element that defines four .NET types.</span></span> <span data-ttu-id="b5ab1-126">Val av uppsättningen heter ”FileSystemTypes”.</span><span class="sxs-lookup"><span data-stu-id="b5ab1-126">The name of the selection set is "FileSystemTypes".</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b5ab1-127">Se även</span><span class="sxs-lookup"><span data-stu-id="b5ab1-127">See Also</span></span>

[<span data-ttu-id="b5ab1-128">Definiera inställningarna</span><span class="sxs-lookup"><span data-stu-id="b5ab1-128">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="b5ab1-129">SelectionSet Element (Format)</span><span class="sxs-lookup"><span data-stu-id="b5ab1-129">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="b5ab1-130">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="b5ab1-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
