---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSetName-element för SelectionCondition för CustomControl för View (format)
description: SelectionSetName-element för SelectionCondition för CustomControl för View (format)
ms.openlocfilehash: 839032048739e529057d7066fb3bc6aa2fbc5037
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651605"
---
# <a name="selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="34045-103">SelectionSetName-element för SelectionCondition för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="34045-103">SelectionSetName Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="34045-104">Anger den uppsättning av .NET-typer som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="34045-104">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="34045-105">När någon av typerna i den här uppsättningen finns, uppfylls villkoret och objektet visas med den här kontrollen.</span><span class="sxs-lookup"><span data-stu-id="34045-105">When any of the types in this set are present, the condition is met and the object is displayed using this control.</span></span> <span data-ttu-id="34045-106">Det här elementet används när du definierar en anpassad kontrol vy.</span><span class="sxs-lookup"><span data-stu-id="34045-106">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="34045-107">Konfigurations element (format) ViewDefinitions element (format) View element (format) CustomControl element (format) CustomEntries-element för CustomControl för View (format) CustomEntry-element för CustomEntries för View (format) EntrySelectedBy-element för CustomEntry för View (format)</span><span class="sxs-lookup"><span data-stu-id="34045-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="34045-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="34045-108">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="34045-109">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="34045-109">Attributes and Elements</span></span>

<span data-ttu-id="34045-110">I följande avsnitt beskrivs attribut, underordnade element och `SelectionSetName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="34045-110">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="34045-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="34045-111">Attributes</span></span>

<span data-ttu-id="34045-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="34045-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="34045-113">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="34045-113">Child Elements</span></span>

<span data-ttu-id="34045-114">Inga.</span><span class="sxs-lookup"><span data-stu-id="34045-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="34045-115">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="34045-115">Parent Elements</span></span>

|<span data-ttu-id="34045-116">Element</span><span class="sxs-lookup"><span data-stu-id="34045-116">Element</span></span>|<span data-ttu-id="34045-117">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="34045-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="34045-118">SelectionCondition-element för EntrySelectedBy för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="34045-118">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="34045-119">Definierar ett villkor som måste finnas för att den kontroll definition som ska användas.</span><span class="sxs-lookup"><span data-stu-id="34045-119">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="34045-120">Textvärde</span><span class="sxs-lookup"><span data-stu-id="34045-120">Text Value</span></span>

<span data-ttu-id="34045-121">Ange namnet på urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="34045-121">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="34045-122">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="34045-122">Remarks</span></span>

<span data-ttu-id="34045-123">Urvals uppsättningar är vanliga grupper av .NET-objekt som kan användas av alla vyer som format filen definierar.</span><span class="sxs-lookup"><span data-stu-id="34045-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="34045-124">Mer information om hur du skapar och refererar till urvals uppsättningar finns i [definiera uppsättningar av objekt](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="34045-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="34045-125">Urvals villkoret kan ange en urvals uppsättning eller en .NET-typ, men det går inte att ange båda.</span><span class="sxs-lookup"><span data-stu-id="34045-125">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="34045-126">Mer information om hur du använder urvals villkor finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="34045-126">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="34045-127">Se även</span><span class="sxs-lookup"><span data-stu-id="34045-127">See Also</span></span>

[<span data-ttu-id="34045-128">SelectionCondition-element för EntrySelectedBy för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="34045-128">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="34045-129">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="34045-129">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="34045-130">Definiera valuppsättningar</span><span class="sxs-lookup"><span data-stu-id="34045-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="34045-131">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="34045-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
