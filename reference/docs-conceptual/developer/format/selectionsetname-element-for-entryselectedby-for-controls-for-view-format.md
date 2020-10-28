---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSetName-element för EntrySelectedBy för Controls för View (format)
description: SelectionSetName-element för EntrySelectedBy för Controls för View (format)
ms.openlocfilehash: 3211b7cacd7e57770b48b03f4aade33da506f180
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92664741"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-view-format"></a><span data-ttu-id="19308-103">SelectionSetName-element för EntrySelectedBy för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="19308-103">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>

<span data-ttu-id="19308-104">Anger en uppsättning av .NET-typer som använder den här definitionen av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="19308-104">Specifies a set of .NET types that use this definition of the control.</span></span> <span data-ttu-id="19308-105">Det här elementet används när du definierar kontroller som kan användas av en vy.</span><span class="sxs-lookup"><span data-stu-id="19308-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="19308-106">Konfigurations element (format) ViewDefinitions element (format) View-element (format) styr element (format) styr element (format) styr element för Controls (format) CustomControl-element för kontroll för Control for View (format) CustomEntries-element för CustomControl for Controls for View (format) CustomEntry-elementet för CustomEntries for Controls for View (format) EntrySelectedBy-elementet for CustomEntry for Controls for View (format) SelectionSetName element for EntrySelectedBy for Controls for View (format)</span><span class="sxs-lookup"><span data-stu-id="19308-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="19308-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="19308-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="19308-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="19308-108">Attributes and Elements</span></span>

<span data-ttu-id="19308-109">I följande avsnitt beskrivs attribut, underordnade element och `SelectionSetName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="19308-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="19308-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="19308-110">Attributes</span></span>

<span data-ttu-id="19308-111">Inget</span><span class="sxs-lookup"><span data-stu-id="19308-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="19308-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="19308-112">Child Elements</span></span>

<span data-ttu-id="19308-113">Inga.</span><span class="sxs-lookup"><span data-stu-id="19308-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="19308-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="19308-114">Parent Elements</span></span>

|<span data-ttu-id="19308-115">Element</span><span class="sxs-lookup"><span data-stu-id="19308-115">Element</span></span>|<span data-ttu-id="19308-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="19308-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="19308-117">EntrySelectedBy-element för CustomEntry för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="19308-117">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="19308-118">Definierar de .NET-typer som använder den här kontroll definitionen eller det villkor som måste finnas för att den här definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="19308-118">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="19308-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="19308-119">Text Value</span></span>

<span data-ttu-id="19308-120">Ange namnet på urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="19308-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="19308-121">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="19308-121">Remarks</span></span>

<span data-ttu-id="19308-122">Varje kontroll definition måste ha minst ett typ namn, en markerings uppsättning eller ett urvals villkor definierat.</span><span class="sxs-lookup"><span data-stu-id="19308-122">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="19308-123">Urvals uppsättningar används vanligt vis när du vill definiera en grupp objekt som används i flera vyer.</span><span class="sxs-lookup"><span data-stu-id="19308-123">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="19308-124">Mer information om hur du definierar urvals uppsättningar finns i [definiera urvals uppsättningar](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="19308-124">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="19308-125">Se även</span><span class="sxs-lookup"><span data-stu-id="19308-125">See Also</span></span>

[<span data-ttu-id="19308-126">EntrySelectedBy-element för CustomEntry för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="19308-126">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="19308-127">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="19308-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
