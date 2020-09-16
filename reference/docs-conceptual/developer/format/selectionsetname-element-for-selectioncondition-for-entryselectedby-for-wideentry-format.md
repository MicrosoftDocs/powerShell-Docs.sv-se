---
title: SelectionSetName-element för SelectionCondition för EntrySelectedBy för WideEntry (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 44c88ce75ae485e1c48ceb08bfd12f739a632996
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787452"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="fd50a-102">SelectionSetName-element för SelectionCondition för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="fd50a-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="fd50a-103">Anger den uppsättning av .NET-typer som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="fd50a-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="fd50a-104">När någon av typerna i den här uppsättningen finns, uppfylls villkoret och objektet visas genom att använda den här definitionen av wide View.</span><span class="sxs-lookup"><span data-stu-id="fd50a-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the wide view.</span></span>

<span data-ttu-id="fd50a-105">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) WideControl-element (format) WideEntries-element (format) WideEntry-element (format) EntrySelectedBy-element för WideEntry (format) SelectionCondition element for EntrySelectedBy for WideEntry (format) SelectionSetName-element för SelectionCondition för EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="fd50a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fd50a-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="fd50a-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fd50a-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="fd50a-107">Attributes and Elements</span></span>

<span data-ttu-id="fd50a-108">I följande avsnitt beskrivs attribut, underordnade element och `SelectionSetName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="fd50a-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fd50a-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="fd50a-109">Attributes</span></span>

<span data-ttu-id="fd50a-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="fd50a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fd50a-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="fd50a-111">Child Elements</span></span>

<span data-ttu-id="fd50a-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="fd50a-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fd50a-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="fd50a-113">Parent Elements</span></span>

|<span data-ttu-id="fd50a-114">Element</span><span class="sxs-lookup"><span data-stu-id="fd50a-114">Element</span></span>|<span data-ttu-id="fd50a-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="fd50a-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fd50a-116">SelectionCondition-element för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="fd50a-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="fd50a-117">Definierar det villkor som måste finnas för att den här definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="fd50a-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="fd50a-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="fd50a-118">Text Value</span></span>

<span data-ttu-id="fd50a-119">Ange namnet på urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="fd50a-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="fd50a-120">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="fd50a-120">Remarks</span></span>

<span data-ttu-id="fd50a-121">Urvals villkoret kan ange en urvals uppsättning eller en .NET-typ, men det går inte att ange båda.</span><span class="sxs-lookup"><span data-stu-id="fd50a-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="fd50a-122">Mer information om hur du använder urvals villkor finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="fd50a-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="fd50a-123">Urvals uppsättningar är vanliga grupper av .NET-objekt som kan användas av alla vyer som format filen definierar.</span><span class="sxs-lookup"><span data-stu-id="fd50a-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="fd50a-124">Mer information om hur du skapar och refererar till urvals uppsättningar finns i [definiera uppsättningar av objekt](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="fd50a-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="fd50a-125">Mer information om andra komponenter i en bred vy finns i [skapa en bred vy](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="fd50a-125">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fd50a-126">Se även</span><span class="sxs-lookup"><span data-stu-id="fd50a-126">See Also</span></span>

[<span data-ttu-id="fd50a-127">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="fd50a-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="fd50a-128">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="fd50a-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="fd50a-129">Definiera valuppsättningar</span><span class="sxs-lookup"><span data-stu-id="fd50a-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="fd50a-130">SelectionCondition-element för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="fd50a-130">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="fd50a-131">Elementet TypeName för SelectionCondition för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="fd50a-131">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="fd50a-132">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="fd50a-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
