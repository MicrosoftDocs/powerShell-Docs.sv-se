---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSetName-element för SelectionCondition för GroupBy (format)
description: SelectionSetName-element för SelectionCondition för GroupBy (format)
ms.openlocfilehash: a4f28c1caba3790718b99f63659cb0cbed8def16
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654988"
---
# <a name="selectionsetname-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="65318-103">SelectionSetName-element för SelectionCondition för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="65318-103">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="65318-104">Anger den uppsättning av .NET-typer som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="65318-104">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="65318-105">När någon av typerna i den här uppsättningen finns, uppfylls villkoret och objektet visas med hjälp av den här kontrollen.</span><span class="sxs-lookup"><span data-stu-id="65318-105">When any of the types in this set are present, the condition is met, and the object is displayed by using this control.</span></span> <span data-ttu-id="65318-106">Det här elementet används när du definierar hur en ny grupp av objekt visas.</span><span class="sxs-lookup"><span data-stu-id="65318-106">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="65318-107">Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for GroupBy (format) CustomEntry-element for CustomControl for groupby (format) EntrySelectedBy-element för CustomEntry (format) SelectionCondition element for EntrySelectedBy för groupby (format) SelectionSetName element for SelectionCondition</span><span class="sxs-lookup"><span data-stu-id="65318-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="65318-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="65318-108">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="65318-109">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="65318-109">Attributes and Elements</span></span>

<span data-ttu-id="65318-110">I följande avsnitt beskrivs attribut, underordnade element och `SelectionSetName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="65318-110">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="65318-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="65318-111">Attributes</span></span>

<span data-ttu-id="65318-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="65318-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="65318-113">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="65318-113">Child Elements</span></span>

<span data-ttu-id="65318-114">Inga.</span><span class="sxs-lookup"><span data-stu-id="65318-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="65318-115">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="65318-115">Parent Elements</span></span>

|<span data-ttu-id="65318-116">Element</span><span class="sxs-lookup"><span data-stu-id="65318-116">Element</span></span>|<span data-ttu-id="65318-117">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="65318-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="65318-118">SelectionCondition-element för EntrySelectedBy för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="65318-118">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="65318-119">Definierar ett villkor som måste finnas för att den kontroll definition som ska användas.</span><span class="sxs-lookup"><span data-stu-id="65318-119">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="65318-120">Textvärde</span><span class="sxs-lookup"><span data-stu-id="65318-120">Text Value</span></span>

<span data-ttu-id="65318-121">Ange namnet på urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="65318-121">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="65318-122">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="65318-122">Remarks</span></span>

<span data-ttu-id="65318-123">Urvals uppsättningar är vanliga grupper av .NET-objekt som kan användas av alla vyer som format filen definierar.</span><span class="sxs-lookup"><span data-stu-id="65318-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="65318-124">Mer information om hur du skapar och refererar till urvals uppsättningar finns i [definiera urvals uppsättningar](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="65318-124">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="65318-125">När det här elementet har angetts kan du inte ange elementet [TypeName](./typename-element-for-selectioncondition-for-groupby-format.md) .</span><span class="sxs-lookup"><span data-stu-id="65318-125">When this element is specified, you cannot specify the [TypeName](./typename-element-for-selectioncondition-for-groupby-format.md) element.</span></span> <span data-ttu-id="65318-126">Mer information om hur du definierar urvals villkor finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="65318-126">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="65318-127">Se även</span><span class="sxs-lookup"><span data-stu-id="65318-127">See Also</span></span>

[<span data-ttu-id="65318-128">TypeName-element för SelectionCondition för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="65318-128">TypeName Element for SelectionCondition for GroupBy (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)

[<span data-ttu-id="65318-129">SelectionCondition-element för EntrySelectedBy för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="65318-129">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="65318-130">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="65318-130">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="65318-131">Definiera valuppsättningar</span><span class="sxs-lookup"><span data-stu-id="65318-131">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="65318-132">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="65318-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
