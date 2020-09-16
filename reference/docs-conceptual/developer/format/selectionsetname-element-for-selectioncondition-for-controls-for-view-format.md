---
title: SelectionSetName-element för SelectionCondition för kontroller för vy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 0feb23f860487952344680f75ee674e9e0e6dcc6
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787537"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="e04cd-102">SelectionSetName-element för SelectionCondition för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="e04cd-102">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="e04cd-103">Anger den uppsättning av .NET-typer som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="e04cd-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="e04cd-104">När någon av typerna i den här uppsättningen finns, uppfylls villkoret och objektet visas med den här kontrollen.</span><span class="sxs-lookup"><span data-stu-id="e04cd-104">When any of the types in this set are present, the condition is met and the object is displayed using this control.</span></span> <span data-ttu-id="e04cd-105">Det här elementet används när du definierar kontroller som kan användas av en vy.</span><span class="sxs-lookup"><span data-stu-id="e04cd-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="e04cd-106">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) styr element (format) styr element (format) styr element (format) kontroll element för Controls for View (format) CustomControl-element för kontroll för kontroller för View (format) CustomEntries-element för CustomControl för kontroller (format) CustomEntry-element för CustomEntries for Controls for View (format) EntrySelectedBy-element för CustomEntry for Controls for View (format) SelectionCondition-elementet for EntrySelectedBy for Controls for View (format) SelectionSetName element for SelectionCondition for Controls for View (format)</span><span class="sxs-lookup"><span data-stu-id="e04cd-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e04cd-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="e04cd-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e04cd-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="e04cd-108">Attributes and Elements</span></span>

<span data-ttu-id="e04cd-109">I följande avsnitt beskrivs attribut, underordnade element och `SelectionSetName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="e04cd-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e04cd-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="e04cd-110">Attributes</span></span>

<span data-ttu-id="e04cd-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="e04cd-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e04cd-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="e04cd-112">Child Elements</span></span>

<span data-ttu-id="e04cd-113">Inga.</span><span class="sxs-lookup"><span data-stu-id="e04cd-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e04cd-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="e04cd-114">Parent Elements</span></span>

|<span data-ttu-id="e04cd-115">Element</span><span class="sxs-lookup"><span data-stu-id="e04cd-115">Element</span></span>|<span data-ttu-id="e04cd-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e04cd-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e04cd-117">SelectionCondition-element för EntrySelectedBy för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="e04cd-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="e04cd-118">Definierar ett villkor som måste finnas för att den kontroll definition som ska användas.</span><span class="sxs-lookup"><span data-stu-id="e04cd-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e04cd-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="e04cd-119">Text Value</span></span>

<span data-ttu-id="e04cd-120">Ange namnet på urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="e04cd-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="e04cd-121">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="e04cd-121">Remarks</span></span>

<span data-ttu-id="e04cd-122">Urvals uppsättningar är vanliga grupper av .NET-objekt som kan användas av alla vyer som format filen definierar.</span><span class="sxs-lookup"><span data-stu-id="e04cd-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="e04cd-123">Mer information om hur du skapar och refererar till urvals uppsättningar finns i [definiera urvals uppsättningar](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="e04cd-123">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="e04cd-124">Urvals villkoret kan ange en urvals uppsättning eller en .NET-typ, men det går inte att ange båda.</span><span class="sxs-lookup"><span data-stu-id="e04cd-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="e04cd-125">Mer information om hur du använder urvals villkor finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="e04cd-125">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e04cd-126">Se även</span><span class="sxs-lookup"><span data-stu-id="e04cd-126">See Also</span></span>

[<span data-ttu-id="e04cd-127">SelectionCondition-element för EntrySelectedBy för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="e04cd-127">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="e04cd-128">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="e04cd-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="e04cd-129">Definiera valuppsättningar</span><span class="sxs-lookup"><span data-stu-id="e04cd-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="e04cd-130">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="e04cd-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
