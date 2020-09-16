---
title: SelectionSetName-element för SelectionCondition för EntrySelectedBy för ListEntry (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 3666888f149f176126d9a19bdbad62469ca9f064
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787486"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format"></a><span data-ttu-id="869b0-102">SelectionSetName-element för SelectionCondition för EntrySelectedBy för ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="869b0-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

<span data-ttu-id="869b0-103">Anger den uppsättning av .NET-typer som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="869b0-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="869b0-104">När någon av typerna i den här uppsättningen finns, uppfylls villkoret och objektet visas med hjälp av den här definitionen av listvyn.</span><span class="sxs-lookup"><span data-stu-id="869b0-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the list view.</span></span>

<span data-ttu-id="869b0-105">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) ListControl-element (format) ListEntries-element (format) ListEntry-element (format) EntrySelectedBy-element för ListEntry (format) SelectionCondition element for EntrySelectedBy for ListEntry (format) SelectionSetName-element för SelectionCondition för EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="869b0-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="869b0-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="869b0-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="869b0-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="869b0-107">Attributes and Elements</span></span>

<span data-ttu-id="869b0-108">I följande avsnitt beskrivs attribut, underordnade element och `SelectionSetName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="869b0-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="869b0-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="869b0-109">Attributes</span></span>

<span data-ttu-id="869b0-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="869b0-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="869b0-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="869b0-111">Child Elements</span></span>

<span data-ttu-id="869b0-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="869b0-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="869b0-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="869b0-113">Parent Elements</span></span>

|<span data-ttu-id="869b0-114">Element</span><span class="sxs-lookup"><span data-stu-id="869b0-114">Element</span></span>|<span data-ttu-id="869b0-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="869b0-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="869b0-116">SelectionCondition-element för EntrySelectedBy för ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="869b0-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="869b0-117">Definierar det villkor som måste finnas för att använda den här definitionen av listvyn.</span><span class="sxs-lookup"><span data-stu-id="869b0-117">Defines the condition that must exist to use this definition of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="869b0-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="869b0-118">Text Value</span></span>

<span data-ttu-id="869b0-119">Ange namnet på urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="869b0-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="869b0-120">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="869b0-120">Remarks</span></span>

<span data-ttu-id="869b0-121">Urvals villkoret kan ange en urvals uppsättning eller en .NET-typ, men det går inte att ange båda.</span><span class="sxs-lookup"><span data-stu-id="869b0-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="869b0-122">Mer information om hur du använder urvals villkor finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="869b0-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="869b0-123">Urvals uppsättningar är vanliga grupper av .NET-objekt som kan användas av alla vyer som format filen definierar.</span><span class="sxs-lookup"><span data-stu-id="869b0-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="869b0-124">Mer information om hur du skapar och refererar till urvals uppsättningar finns i [definiera uppsättningar av objekt](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="869b0-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="869b0-125">Mer information om andra komponenter i en listvy finns i [skapa en listvy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="869b0-125">For more information about other components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="869b0-126">Se även</span><span class="sxs-lookup"><span data-stu-id="869b0-126">See Also</span></span>

[<span data-ttu-id="869b0-127">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="869b0-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="869b0-128">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="869b0-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="869b0-129">SelectionCondition-element för EntrySelectedBy för ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="869b0-129">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="869b0-130">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="869b0-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
