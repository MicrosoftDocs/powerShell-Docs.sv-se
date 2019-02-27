---
title: SelectionSets Element (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebbac73a-1c99-4388-9f47-703cd024dc6d
caps.latest.revision: 18
ms.openlocfilehash: a9356635d60d5f8c5d4dec4ec8b7d0aea2b037dd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845110"
---
# <a name="selectionsets-element-format"></a><span data-ttu-id="5b9f5-102">SelectionSets-element (format)</span><span class="sxs-lookup"><span data-stu-id="5b9f5-102">SelectionSets Element (Format)</span></span>

<span data-ttu-id="5b9f5-103">Definierar gemensamma uppsättningar med .NET-objekt som kan användas av alla vyer i filen formatering.</span><span class="sxs-lookup"><span data-stu-id="5b9f5-103">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span> <span data-ttu-id="5b9f5-104">Vyer och kontroller av filen formatering kan referera till en fullständig uppsättning med objekt med hjälp av endast namnet på val av uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="5b9f5-104">The views and controls of the formatting file can reference the complete set of objects by using only the name of the selection set.</span></span>

<span data-ttu-id="5b9f5-105">Konfiguration av elementet SelectionSets elementet Format</span><span class="sxs-lookup"><span data-stu-id="5b9f5-105">Configuration Element SelectionSets Element Format</span></span>

## <a name="syntax"></a><span data-ttu-id="5b9f5-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="5b9f5-106">Syntax</span></span>

```xml
<SelectionSets>
  <SelectionSet>...</SelectionSet>
</SelectionSets>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5b9f5-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="5b9f5-107">Attributes and Elements</span></span>

<span data-ttu-id="5b9f5-108">I följande avsnitt beskrivs de attribut och underordnade element överordnade elementet i den `SelectionSets` element.</span><span class="sxs-lookup"><span data-stu-id="5b9f5-108">The following sections describe the attributes, child elements, and parent element of the `SelectionSets` element.</span></span> <span data-ttu-id="5b9f5-109">Varje underordnat element definierar en uppsättning objekt som kan refereras av namnet på uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="5b9f5-109">Each child element defines a set of objects that can be referenced by the name of the set.</span></span> <span data-ttu-id="5b9f5-110">Ordningen på de underordnade elementen är inte viktig.</span><span class="sxs-lookup"><span data-stu-id="5b9f5-110">The order of the child elements is not significant.</span></span>

### <a name="attributes"></a><span data-ttu-id="5b9f5-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="5b9f5-111">Attributes</span></span>

<span data-ttu-id="5b9f5-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="5b9f5-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5b9f5-113">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="5b9f5-113">Child Elements</span></span>

|<span data-ttu-id="5b9f5-114">Element</span><span class="sxs-lookup"><span data-stu-id="5b9f5-114">Element</span></span>|<span data-ttu-id="5b9f5-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b9f5-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5b9f5-116">SelectionSet Element (Format)</span><span class="sxs-lookup"><span data-stu-id="5b9f5-116">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="5b9f5-117">Element som krävs.</span><span class="sxs-lookup"><span data-stu-id="5b9f5-117">Required element.</span></span><br /><br /> <span data-ttu-id="5b9f5-118">Definierar en uppsättning med .NET-objekt som kan refereras av namnet på uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="5b9f5-118">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5b9f5-119">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="5b9f5-119">Parent Elements</span></span>

|<span data-ttu-id="5b9f5-120">Element</span><span class="sxs-lookup"><span data-stu-id="5b9f5-120">Element</span></span>|<span data-ttu-id="5b9f5-121">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b9f5-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5b9f5-122">Konfigurationselement</span><span class="sxs-lookup"><span data-stu-id="5b9f5-122">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="5b9f5-123">Representerar det översta elementet i en formatering fil.</span><span class="sxs-lookup"><span data-stu-id="5b9f5-123">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5b9f5-124">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="5b9f5-124">Remarks</span></span>

<span data-ttu-id="5b9f5-125">Du kan använda inställningarna när du har en uppsättning relaterade objekt som du vill referera till med hjälp av ett enda namn, till exempel en uppsättning objekt som är relaterade genom arv.</span><span class="sxs-lookup"><span data-stu-id="5b9f5-125">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="5b9f5-126">När du definierar dina vyer kan du ange en uppsättning objekt med hjälp av namnet på den val av i stället för att visa en lista över alla objekt i varje vy.</span><span class="sxs-lookup"><span data-stu-id="5b9f5-126">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="5b9f5-127">Vanliga val av uppsättningar anges efter deras namn när du definierar vyer i filen formatering eller definitioner av vyerna.</span><span class="sxs-lookup"><span data-stu-id="5b9f5-127">Common selection sets are specified by their name when defining the views of the formatting file or the definitions of the views.</span></span> <span data-ttu-id="5b9f5-128">I dessa fall kan den `SelectionSetName` underordnat element av den `ViewSelectedBy` och `EntrySelectedBy` anger de element som ska användas.</span><span class="sxs-lookup"><span data-stu-id="5b9f5-128">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` and `EntrySelectedBy` elements specifies the set to be used.</span></span> <span data-ttu-id="5b9f5-129">Mer information om inställningarna finns i [definiera anger av objekt](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="5b9f5-129">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5b9f5-130">Se även</span><span class="sxs-lookup"><span data-stu-id="5b9f5-130">See Also</span></span>

[<span data-ttu-id="5b9f5-131">Konfigurationselement</span><span class="sxs-lookup"><span data-stu-id="5b9f5-131">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="5b9f5-132">Definiera inställningarna</span><span class="sxs-lookup"><span data-stu-id="5b9f5-132">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="5b9f5-133">SelectionSet Element (Format)</span><span class="sxs-lookup"><span data-stu-id="5b9f5-133">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="5b9f5-134">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="5b9f5-134">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
