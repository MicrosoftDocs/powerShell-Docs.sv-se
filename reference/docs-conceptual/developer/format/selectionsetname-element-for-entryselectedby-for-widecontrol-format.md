---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSetName-element för EntrySelectedBy för WideControl (format)
description: SelectionSetName-element för EntrySelectedBy för WideControl (format)
ms.openlocfilehash: bf6a44bb733421f36a9140d0ec10e61aedfbda6a
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92651690"
---
# <a name="selectionsetname-element-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="1e3d0-103">SelectionSetName-element för EntrySelectedBy för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="1e3d0-103">SelectionSetName Element for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="1e3d0-104">Anger en uppsättning .NET-objekt för definitionen.</span><span class="sxs-lookup"><span data-stu-id="1e3d0-104">Specifies a set of .NET objects for the definition.</span></span> <span data-ttu-id="1e3d0-105">Definitionen används när något av dessa objekt visas.</span><span class="sxs-lookup"><span data-stu-id="1e3d0-105">The definition is used whenever one of these objects is displayed.</span></span>

<span data-ttu-id="1e3d0-106">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) WideControl-element (format) WideEntries-element (format) WideEntry element (format) EntrySelectedBy-element för WideEntry (format) SelectionSetName-element för EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="1e3d0-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1e3d0-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="1e3d0-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="1e3d0-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="1e3d0-108">Attributes and Elements</span></span>

<span data-ttu-id="1e3d0-109">I följande avsnitt beskrivs attributen, underordnade element och `SelectionSetName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="1e3d0-109">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1e3d0-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="1e3d0-110">Attributes</span></span>

<span data-ttu-id="1e3d0-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="1e3d0-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1e3d0-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="1e3d0-112">Child Elements</span></span>

<span data-ttu-id="1e3d0-113">Inga.</span><span class="sxs-lookup"><span data-stu-id="1e3d0-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1e3d0-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="1e3d0-114">Parent Elements</span></span>

|<span data-ttu-id="1e3d0-115">Element</span><span class="sxs-lookup"><span data-stu-id="1e3d0-115">Element</span></span>|<span data-ttu-id="1e3d0-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="1e3d0-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1e3d0-117">EntrySelectedBy-element för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="1e3d0-117">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="1e3d0-118">Definierar de .NET-typer som använder den här breda posten eller det villkor som måste finnas för att den här posten ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="1e3d0-118">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1e3d0-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="1e3d0-119">Text Value</span></span>

<span data-ttu-id="1e3d0-120">Ange namnet på urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="1e3d0-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="1e3d0-121">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="1e3d0-121">Remarks</span></span>

<span data-ttu-id="1e3d0-122">Varje definition måste ange ett typ namn, en urvals uppsättning eller ett markerings villkor.</span><span class="sxs-lookup"><span data-stu-id="1e3d0-122">Each definition must specify one type name, selection set, or selection condition.</span></span>

<span data-ttu-id="1e3d0-123">Urvals uppsättningar används vanligt vis när du vill definiera en grupp objekt som används i flera vyer.</span><span class="sxs-lookup"><span data-stu-id="1e3d0-123">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="1e3d0-124">Du kanske till exempel vill skapa en tabellvy och en listvy för samma uppsättning objekt.</span><span class="sxs-lookup"><span data-stu-id="1e3d0-124">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="1e3d0-125">Mer information om hur du definierar urvals uppsättningar finns i [definiera uppsättningar av objekt för en vy](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="1e3d0-125">For more information about defining selection sets, see [Defining Sets of Objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="1e3d0-126">Mer information om andra komponenter i en bred vy finns i [skapa en bred vy](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="1e3d0-126">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1e3d0-127">Se även</span><span class="sxs-lookup"><span data-stu-id="1e3d0-127">See Also</span></span>

[<span data-ttu-id="1e3d0-128">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="1e3d0-128">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="1e3d0-129">Definiera valuppsättningar</span><span class="sxs-lookup"><span data-stu-id="1e3d0-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="1e3d0-130">EntrySelectedBy-element för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="1e3d0-130">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="1e3d0-131">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="1e3d0-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
