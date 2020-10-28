---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSetName-element för SelectionCondition för Controls för Configuration (format)
description: SelectionSetName-element för SelectionCondition för Controls för Configuration (format)
ms.openlocfilehash: 4177aace5a6a9374900e7339167c69b531c1e2e7
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92651655"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="99600-103">SelectionSetName-element för SelectionCondition för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="99600-103">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="99600-104">Anger den uppsättning av .NET-typer som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="99600-104">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="99600-105">När någon av typerna i den här uppsättningen finns, uppfylls villkoret och objektet visas med hjälp av den här kontrollen.</span><span class="sxs-lookup"><span data-stu-id="99600-105">When any of the types in this set are present, the condition is met, and the object is displayed by using this control.</span></span> <span data-ttu-id="99600-106">Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.</span><span class="sxs-lookup"><span data-stu-id="99600-106">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="99600-107">Konfigurations element (format) styr element i konfigurations-(format)-kontroll element för kontroll för CustomControl-element (format) för Control för Configuration (format) CustomEntries-element för CustomControl för Controls (format) CustomEntry-element för CustomControl for Controls for Configuration (format) EntrySelectedBy-elementet för CustomEntry for Controls for Configuration (format) SelectionCondition element for EntrySelectedBy for Controls for Configuration (format) SelectionSetName element for SelectionCondition for Controls for Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="99600-107">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format) SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="99600-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="99600-108">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="99600-109">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="99600-109">Attributes and Elements</span></span>

<span data-ttu-id="99600-110">I följande avsnitt beskrivs attribut, underordnade element och `SelectionSetName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="99600-110">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="99600-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="99600-111">Attributes</span></span>

<span data-ttu-id="99600-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="99600-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="99600-113">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="99600-113">Child Elements</span></span>

<span data-ttu-id="99600-114">Inga.</span><span class="sxs-lookup"><span data-stu-id="99600-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="99600-115">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="99600-115">Parent Elements</span></span>

|<span data-ttu-id="99600-116">Element</span><span class="sxs-lookup"><span data-stu-id="99600-116">Element</span></span>|<span data-ttu-id="99600-117">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="99600-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="99600-118">SelectionCondition-element för EntrySelectedBy för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="99600-118">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="99600-119">Definierar ett villkor som måste finnas för att den kontroll definition som ska användas.</span><span class="sxs-lookup"><span data-stu-id="99600-119">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="99600-120">Textvärde</span><span class="sxs-lookup"><span data-stu-id="99600-120">Text Value</span></span>

<span data-ttu-id="99600-121">Ange namnet på urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="99600-121">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="99600-122">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="99600-122">Remarks</span></span>

<span data-ttu-id="99600-123">Urvals uppsättningar är vanliga grupper av .NET-objekt som kan användas av alla vyer som format filen definierar.</span><span class="sxs-lookup"><span data-stu-id="99600-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="99600-124">Mer information om hur du skapar och refererar till urvals uppsättningar finns i [definiera uppsättningar av objekt](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="99600-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="99600-125">Urvals villkoret kan ange en urvals uppsättning eller en .NET-typ, men det går inte att ange båda.</span><span class="sxs-lookup"><span data-stu-id="99600-125">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="99600-126">Mer information om hur du använder urvals villkor finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="99600-126">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="99600-127">Se även</span><span class="sxs-lookup"><span data-stu-id="99600-127">See Also</span></span>

[<span data-ttu-id="99600-128">SelectionCondition-element för EntrySelectedBy för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="99600-128">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="99600-129">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="99600-129">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="99600-130">Definiera valuppsättningar</span><span class="sxs-lookup"><span data-stu-id="99600-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="99600-131">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="99600-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
