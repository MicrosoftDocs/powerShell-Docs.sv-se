---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSets-element (format)
description: SelectionSets-element (format)
ms.openlocfilehash: e5c928dfb82bc6963b4a87aef9ec06d34cacfdcb
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92654928"
---
# <a name="selectionsets-element-format"></a><span data-ttu-id="f02ae-103">SelectionSets-element (format)</span><span class="sxs-lookup"><span data-stu-id="f02ae-103">SelectionSets Element (Format)</span></span>

<span data-ttu-id="f02ae-104">Definierar de gemensamma uppsättningar av .NET-objekt som kan användas av alla vyer i format filen.</span><span class="sxs-lookup"><span data-stu-id="f02ae-104">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span> <span data-ttu-id="f02ae-105">Vyer och kontroller i format filen kan referera till en fullständig uppsättning objekt genom att bara använda namnet på uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="f02ae-105">The views and controls of the formatting file can reference the complete set of objects by using only the name of the selection set.</span></span>

<span data-ttu-id="f02ae-106">SelectionSets element format för konfigurations element</span><span class="sxs-lookup"><span data-stu-id="f02ae-106">Configuration Element SelectionSets Element Format</span></span>

## <a name="syntax"></a><span data-ttu-id="f02ae-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="f02ae-107">Syntax</span></span>

```xml
<SelectionSets>
  <SelectionSet>...</SelectionSet>
</SelectionSets>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f02ae-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="f02ae-108">Attributes and Elements</span></span>

<span data-ttu-id="f02ae-109">I följande avsnitt beskrivs attributen, underordnade element och `SelectionSets` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="f02ae-109">The following sections describe the attributes, child elements, and parent element of the `SelectionSets` element.</span></span> <span data-ttu-id="f02ae-110">Varje underordnat element definierar en uppsättning objekt som kan refereras till av uppsättningens namn.</span><span class="sxs-lookup"><span data-stu-id="f02ae-110">Each child element defines a set of objects that can be referenced by the name of the set.</span></span> <span data-ttu-id="f02ae-111">Ordningen på de underordnade elementen är inte signifikant.</span><span class="sxs-lookup"><span data-stu-id="f02ae-111">The order of the child elements is not significant.</span></span>

### <a name="attributes"></a><span data-ttu-id="f02ae-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="f02ae-112">Attributes</span></span>

<span data-ttu-id="f02ae-113">Inga.</span><span class="sxs-lookup"><span data-stu-id="f02ae-113">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f02ae-114">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="f02ae-114">Child Elements</span></span>

|<span data-ttu-id="f02ae-115">Element</span><span class="sxs-lookup"><span data-stu-id="f02ae-115">Element</span></span>|<span data-ttu-id="f02ae-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f02ae-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f02ae-117">SelectionSet-element (format)</span><span class="sxs-lookup"><span data-stu-id="f02ae-117">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="f02ae-118">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="f02ae-118">Required element.</span></span><br /><br /> <span data-ttu-id="f02ae-119">Definierar en enda uppsättning .NET-objekt som kan refereras till i uppsättningens namn.</span><span class="sxs-lookup"><span data-stu-id="f02ae-119">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f02ae-120">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="f02ae-120">Parent Elements</span></span>

|<span data-ttu-id="f02ae-121">Element</span><span class="sxs-lookup"><span data-stu-id="f02ae-121">Element</span></span>|<span data-ttu-id="f02ae-122">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f02ae-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f02ae-123">Konfigurations element</span><span class="sxs-lookup"><span data-stu-id="f02ae-123">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="f02ae-124">Representerar det översta elementet i en textfil.</span><span class="sxs-lookup"><span data-stu-id="f02ae-124">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f02ae-125">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="f02ae-125">Remarks</span></span>

<span data-ttu-id="f02ae-126">Du kan använda urvals uppsättningar när du har en uppsättning relaterade objekt som du vill referera till genom att använda ett enda namn, till exempel en uppsättning objekt som är relaterade till arv.</span><span class="sxs-lookup"><span data-stu-id="f02ae-126">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="f02ae-127">När du definierar dina vyer kan du ange en uppsättning objekt genom att använda namnet på urvals uppsättningen i stället för att visa alla objekt i varje vy.</span><span class="sxs-lookup"><span data-stu-id="f02ae-127">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="f02ae-128">Vanliga urvals uppsättningar anges med deras namn när du definierar vyerna för format filen eller definitionerna för vyerna.</span><span class="sxs-lookup"><span data-stu-id="f02ae-128">Common selection sets are specified by their name when defining the views of the formatting file or the definitions of the views.</span></span> <span data-ttu-id="f02ae-129">I dessa fall anger det `SelectionSetName` underordnade elementet i `ViewSelectedBy` `EntrySelectedBy` elementen och den uppsättning som ska användas.</span><span class="sxs-lookup"><span data-stu-id="f02ae-129">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` and `EntrySelectedBy` elements specifies the set to be used.</span></span> <span data-ttu-id="f02ae-130">Mer information om urvals uppsättningar finns i [definiera uppsättningar av objekt](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="f02ae-130">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f02ae-131">Se även</span><span class="sxs-lookup"><span data-stu-id="f02ae-131">See Also</span></span>

[<span data-ttu-id="f02ae-132">Konfigurations element</span><span class="sxs-lookup"><span data-stu-id="f02ae-132">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="f02ae-133">Definiera valuppsättningar</span><span class="sxs-lookup"><span data-stu-id="f02ae-133">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="f02ae-134">SelectionSet-element (format)</span><span class="sxs-lookup"><span data-stu-id="f02ae-134">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="f02ae-135">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="f02ae-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
