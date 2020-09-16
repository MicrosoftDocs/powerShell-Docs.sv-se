---
title: SelectionSets-element (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 718b08e02220f285ef215fdca727492fd4407466
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785208"
---
# <a name="selectionsets-element-format"></a><span data-ttu-id="f3ad7-102">SelectionSets-element (format)</span><span class="sxs-lookup"><span data-stu-id="f3ad7-102">SelectionSets Element (Format)</span></span>

<span data-ttu-id="f3ad7-103">Definierar de gemensamma uppsättningar av .NET-objekt som kan användas av alla vyer i format filen.</span><span class="sxs-lookup"><span data-stu-id="f3ad7-103">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span> <span data-ttu-id="f3ad7-104">Vyer och kontroller i format filen kan referera till en fullständig uppsättning objekt genom att bara använda namnet på uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="f3ad7-104">The views and controls of the formatting file can reference the complete set of objects by using only the name of the selection set.</span></span>

<span data-ttu-id="f3ad7-105">SelectionSets element format för konfigurations element</span><span class="sxs-lookup"><span data-stu-id="f3ad7-105">Configuration Element SelectionSets Element Format</span></span>

## <a name="syntax"></a><span data-ttu-id="f3ad7-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="f3ad7-106">Syntax</span></span>

```xml
<SelectionSets>
  <SelectionSet>...</SelectionSet>
</SelectionSets>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f3ad7-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="f3ad7-107">Attributes and Elements</span></span>

<span data-ttu-id="f3ad7-108">I följande avsnitt beskrivs attributen, underordnade element och `SelectionSets` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="f3ad7-108">The following sections describe the attributes, child elements, and parent element of the `SelectionSets` element.</span></span> <span data-ttu-id="f3ad7-109">Varje underordnat element definierar en uppsättning objekt som kan refereras till av uppsättningens namn.</span><span class="sxs-lookup"><span data-stu-id="f3ad7-109">Each child element defines a set of objects that can be referenced by the name of the set.</span></span> <span data-ttu-id="f3ad7-110">Ordningen på de underordnade elementen är inte signifikant.</span><span class="sxs-lookup"><span data-stu-id="f3ad7-110">The order of the child elements is not significant.</span></span>

### <a name="attributes"></a><span data-ttu-id="f3ad7-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="f3ad7-111">Attributes</span></span>

<span data-ttu-id="f3ad7-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="f3ad7-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f3ad7-113">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="f3ad7-113">Child Elements</span></span>

|<span data-ttu-id="f3ad7-114">Element</span><span class="sxs-lookup"><span data-stu-id="f3ad7-114">Element</span></span>|<span data-ttu-id="f3ad7-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f3ad7-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f3ad7-116">SelectionSet-element (format)</span><span class="sxs-lookup"><span data-stu-id="f3ad7-116">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="f3ad7-117">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="f3ad7-117">Required element.</span></span><br /><br /> <span data-ttu-id="f3ad7-118">Definierar en enda uppsättning .NET-objekt som kan refereras till i uppsättningens namn.</span><span class="sxs-lookup"><span data-stu-id="f3ad7-118">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f3ad7-119">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="f3ad7-119">Parent Elements</span></span>

|<span data-ttu-id="f3ad7-120">Element</span><span class="sxs-lookup"><span data-stu-id="f3ad7-120">Element</span></span>|<span data-ttu-id="f3ad7-121">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f3ad7-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f3ad7-122">Konfigurations element</span><span class="sxs-lookup"><span data-stu-id="f3ad7-122">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="f3ad7-123">Representerar det översta elementet i en textfil.</span><span class="sxs-lookup"><span data-stu-id="f3ad7-123">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f3ad7-124">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="f3ad7-124">Remarks</span></span>

<span data-ttu-id="f3ad7-125">Du kan använda urvals uppsättningar när du har en uppsättning relaterade objekt som du vill referera till genom att använda ett enda namn, till exempel en uppsättning objekt som är relaterade till arv.</span><span class="sxs-lookup"><span data-stu-id="f3ad7-125">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="f3ad7-126">När du definierar dina vyer kan du ange en uppsättning objekt genom att använda namnet på urvals uppsättningen i stället för att visa alla objekt i varje vy.</span><span class="sxs-lookup"><span data-stu-id="f3ad7-126">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="f3ad7-127">Vanliga urvals uppsättningar anges med deras namn när du definierar vyerna för format filen eller definitionerna för vyerna.</span><span class="sxs-lookup"><span data-stu-id="f3ad7-127">Common selection sets are specified by their name when defining the views of the formatting file or the definitions of the views.</span></span> <span data-ttu-id="f3ad7-128">I dessa fall anger det `SelectionSetName` underordnade elementet i `ViewSelectedBy` `EntrySelectedBy` elementen och den uppsättning som ska användas.</span><span class="sxs-lookup"><span data-stu-id="f3ad7-128">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` and `EntrySelectedBy` elements specifies the set to be used.</span></span> <span data-ttu-id="f3ad7-129">Mer information om urvals uppsättningar finns i [definiera uppsättningar av objekt](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="f3ad7-129">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f3ad7-130">Se även</span><span class="sxs-lookup"><span data-stu-id="f3ad7-130">See Also</span></span>

[<span data-ttu-id="f3ad7-131">Konfigurations element</span><span class="sxs-lookup"><span data-stu-id="f3ad7-131">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="f3ad7-132">Definiera valuppsättningar</span><span class="sxs-lookup"><span data-stu-id="f3ad7-132">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="f3ad7-133">SelectionSet-element (format)</span><span class="sxs-lookup"><span data-stu-id="f3ad7-133">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="f3ad7-134">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="f3ad7-134">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
