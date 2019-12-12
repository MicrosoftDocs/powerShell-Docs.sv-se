---
title: SelectionSets-element (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebbac73a-1c99-4388-9f47-703cd024dc6d
caps.latest.revision: 18
ms.openlocfilehash: a9356635d60d5f8c5d4dec4ec8b7d0aea2b037dd
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353734"
---
# <a name="selectionsets-element-format"></a><span data-ttu-id="2cc1f-102">SelectionSets-element (format)</span><span class="sxs-lookup"><span data-stu-id="2cc1f-102">SelectionSets Element (Format)</span></span>

<span data-ttu-id="2cc1f-103">Definierar de gemensamma uppsättningar av .NET-objekt som kan användas av alla vyer i format filen.</span><span class="sxs-lookup"><span data-stu-id="2cc1f-103">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span> <span data-ttu-id="2cc1f-104">Vyer och kontroller i format filen kan referera till en fullständig uppsättning objekt genom att bara använda namnet på uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="2cc1f-104">The views and controls of the formatting file can reference the complete set of objects by using only the name of the selection set.</span></span>

<span data-ttu-id="2cc1f-105">SelectionSets element format för konfigurations element</span><span class="sxs-lookup"><span data-stu-id="2cc1f-105">Configuration Element SelectionSets Element Format</span></span>

## <a name="syntax"></a><span data-ttu-id="2cc1f-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="2cc1f-106">Syntax</span></span>

```xml
<SelectionSets>
  <SelectionSet>...</SelectionSet>
</SelectionSets>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2cc1f-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="2cc1f-107">Attributes and Elements</span></span>

<span data-ttu-id="2cc1f-108">I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet i `SelectionSets`-elementet.</span><span class="sxs-lookup"><span data-stu-id="2cc1f-108">The following sections describe the attributes, child elements, and parent element of the `SelectionSets` element.</span></span> <span data-ttu-id="2cc1f-109">Varje underordnat element definierar en uppsättning objekt som kan refereras till av uppsättningens namn.</span><span class="sxs-lookup"><span data-stu-id="2cc1f-109">Each child element defines a set of objects that can be referenced by the name of the set.</span></span> <span data-ttu-id="2cc1f-110">Ordningen på de underordnade elementen är inte signifikant.</span><span class="sxs-lookup"><span data-stu-id="2cc1f-110">The order of the child elements is not significant.</span></span>

### <a name="attributes"></a><span data-ttu-id="2cc1f-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="2cc1f-111">Attributes</span></span>

<span data-ttu-id="2cc1f-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="2cc1f-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2cc1f-113">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="2cc1f-113">Child Elements</span></span>

|<span data-ttu-id="2cc1f-114">Element</span><span class="sxs-lookup"><span data-stu-id="2cc1f-114">Element</span></span>|<span data-ttu-id="2cc1f-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="2cc1f-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2cc1f-116">SelectionSet-element (format)</span><span class="sxs-lookup"><span data-stu-id="2cc1f-116">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="2cc1f-117">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="2cc1f-117">Required element.</span></span><br /><br /> <span data-ttu-id="2cc1f-118">Definierar en enda uppsättning .NET-objekt som kan refereras till i uppsättningens namn.</span><span class="sxs-lookup"><span data-stu-id="2cc1f-118">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2cc1f-119">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="2cc1f-119">Parent Elements</span></span>

|<span data-ttu-id="2cc1f-120">Element</span><span class="sxs-lookup"><span data-stu-id="2cc1f-120">Element</span></span>|<span data-ttu-id="2cc1f-121">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="2cc1f-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2cc1f-122">Konfigurations element</span><span class="sxs-lookup"><span data-stu-id="2cc1f-122">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="2cc1f-123">Representerar det översta elementet i en textfil.</span><span class="sxs-lookup"><span data-stu-id="2cc1f-123">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2cc1f-124">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="2cc1f-124">Remarks</span></span>

<span data-ttu-id="2cc1f-125">Du kan använda urvals uppsättningar när du har en uppsättning relaterade objekt som du vill referera till genom att använda ett enda namn, till exempel en uppsättning objekt som är relaterade till arv.</span><span class="sxs-lookup"><span data-stu-id="2cc1f-125">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="2cc1f-126">När du definierar dina vyer kan du ange en uppsättning objekt genom att använda namnet på urvals uppsättningen i stället för att visa alla objekt i varje vy.</span><span class="sxs-lookup"><span data-stu-id="2cc1f-126">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="2cc1f-127">Vanliga urvals uppsättningar anges med deras namn när du definierar vyerna för format filen eller definitionerna för vyerna.</span><span class="sxs-lookup"><span data-stu-id="2cc1f-127">Common selection sets are specified by their name when defining the views of the formatting file or the definitions of the views.</span></span> <span data-ttu-id="2cc1f-128">I dessa fall anger `SelectionSetName` underordnat element i `ViewSelectedBy` och `EntrySelectedBy` elementen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="2cc1f-128">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` and `EntrySelectedBy` elements specifies the set to be used.</span></span> <span data-ttu-id="2cc1f-129">Mer information om urvals uppsättningar finns i [definiera uppsättningar av objekt](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="2cc1f-129">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2cc1f-130">Se även</span><span class="sxs-lookup"><span data-stu-id="2cc1f-130">See Also</span></span>

[<span data-ttu-id="2cc1f-131">Konfigurations element</span><span class="sxs-lookup"><span data-stu-id="2cc1f-131">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="2cc1f-132">Definiera urvals uppsättningar</span><span class="sxs-lookup"><span data-stu-id="2cc1f-132">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="2cc1f-133">SelectionSet-element (format)</span><span class="sxs-lookup"><span data-stu-id="2cc1f-133">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="2cc1f-134">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="2cc1f-134">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
