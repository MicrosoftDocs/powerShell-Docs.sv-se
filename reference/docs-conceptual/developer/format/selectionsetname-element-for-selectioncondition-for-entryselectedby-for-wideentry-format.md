---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSetName-element för SelectionCondition för EntrySelectedBy för WideEntry (format)
description: SelectionSetName-element för SelectionCondition för EntrySelectedBy för WideEntry (format)
ms.openlocfilehash: c6466e3ac6e1f194df9172468d26448f9630da6a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655003"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="d362c-103">SelectionSetName-element för SelectionCondition för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="d362c-103">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="d362c-104">Anger den uppsättning av .NET-typer som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="d362c-104">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="d362c-105">När någon av typerna i den här uppsättningen finns, uppfylls villkoret och objektet visas genom att använda den här definitionen av wide View.</span><span class="sxs-lookup"><span data-stu-id="d362c-105">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the wide view.</span></span>

<span data-ttu-id="d362c-106">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) WideControl-element (format) WideEntries-element (format) WideEntry-element (format) EntrySelectedBy-element för WideEntry (format) SelectionCondition element for EntrySelectedBy for WideEntry (format) SelectionSetName-element för SelectionCondition för EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="d362c-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d362c-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="d362c-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d362c-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="d362c-108">Attributes and Elements</span></span>

<span data-ttu-id="d362c-109">I följande avsnitt beskrivs attribut, underordnade element och `SelectionSetName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="d362c-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d362c-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="d362c-110">Attributes</span></span>

<span data-ttu-id="d362c-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="d362c-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d362c-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="d362c-112">Child Elements</span></span>

<span data-ttu-id="d362c-113">Inga.</span><span class="sxs-lookup"><span data-stu-id="d362c-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d362c-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="d362c-114">Parent Elements</span></span>

|<span data-ttu-id="d362c-115">Element</span><span class="sxs-lookup"><span data-stu-id="d362c-115">Element</span></span>|<span data-ttu-id="d362c-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d362c-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d362c-117">SelectionCondition-element för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="d362c-117">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="d362c-118">Definierar det villkor som måste finnas för att den här definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="d362c-118">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d362c-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="d362c-119">Text Value</span></span>

<span data-ttu-id="d362c-120">Ange namnet på urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="d362c-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="d362c-121">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="d362c-121">Remarks</span></span>

<span data-ttu-id="d362c-122">Urvals villkoret kan ange en urvals uppsättning eller en .NET-typ, men det går inte att ange båda.</span><span class="sxs-lookup"><span data-stu-id="d362c-122">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="d362c-123">Mer information om hur du använder urvals villkor finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="d362c-123">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="d362c-124">Urvals uppsättningar är vanliga grupper av .NET-objekt som kan användas av alla vyer som format filen definierar.</span><span class="sxs-lookup"><span data-stu-id="d362c-124">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="d362c-125">Mer information om hur du skapar och refererar till urvals uppsättningar finns i [definiera uppsättningar av objekt](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="d362c-125">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="d362c-126">Mer information om andra komponenter i en bred vy finns i [skapa en bred vy](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="d362c-126">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d362c-127">Se även</span><span class="sxs-lookup"><span data-stu-id="d362c-127">See Also</span></span>

[<span data-ttu-id="d362c-128">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="d362c-128">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="d362c-129">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="d362c-129">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="d362c-130">Definiera valuppsättningar</span><span class="sxs-lookup"><span data-stu-id="d362c-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="d362c-131">SelectionCondition-element för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="d362c-131">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="d362c-132">Elementet TypeName för SelectionCondition för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="d362c-132">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="d362c-133">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="d362c-133">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
