---
title: SelectionSetName-element för EntrySelectedBy för CustomControl för View (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859d2335-7fcd-4efd-b1cc-3d171e334c6b
caps.latest.revision: 7
ms.openlocfilehash: f4bf820be88919af43eeaf043b3ed8b9c06e1bf2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355750"
---
# <a name="selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format"></a><span data-ttu-id="437f0-102">SelectionSetName-element för EntrySelectedBy för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="437f0-102">SelectionSetName Element for EntrySelectedBy for CustomControl for View (Format)</span></span>

<span data-ttu-id="437f0-103">Anger en uppsättning .NET-objekt för List posten.</span><span class="sxs-lookup"><span data-stu-id="437f0-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="437f0-104">Det finns ingen gräns för antalet markerings uppsättningar som kan anges för en post.</span><span class="sxs-lookup"><span data-stu-id="437f0-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="437f0-105">Konfigurations element (format) ViewDefinitions element (format) View element (format) CustomControl element (format) CustomEntries-element för CustomControl för View (format) CustomEntry-element för CustomEntries för View (format) EntrySelectedBy Element för CustomEntry för View (format) SelectionSetName-element för EntrySelectedBy för CustomEntry (format)</span><span class="sxs-lookup"><span data-stu-id="437f0-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="437f0-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="437f0-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="437f0-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="437f0-107">Attributes and Elements</span></span>

<span data-ttu-id="437f0-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `SelectionSetName`-elementet.</span><span class="sxs-lookup"><span data-stu-id="437f0-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="437f0-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="437f0-109">Attributes</span></span>

<span data-ttu-id="437f0-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="437f0-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="437f0-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="437f0-111">Child Elements</span></span>

<span data-ttu-id="437f0-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="437f0-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="437f0-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="437f0-113">Parent Elements</span></span>

|<span data-ttu-id="437f0-114">Element</span><span class="sxs-lookup"><span data-stu-id="437f0-114">Element</span></span>|<span data-ttu-id="437f0-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="437f0-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="437f0-116">EntrySelectedBy-element för CustomEntry för vy (format)</span><span class="sxs-lookup"><span data-stu-id="437f0-116">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="437f0-117">Definierar de .NET-typer som använder den här anpassade posten eller det villkor som måste finnas för att den här posten ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="437f0-117">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="437f0-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="437f0-118">Text Value</span></span>

<span data-ttu-id="437f0-119">Ange namnet på urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="437f0-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="437f0-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="437f0-120">Remarks</span></span>

<span data-ttu-id="437f0-121">Varje anpassad kontroll post måste ha minst ett typ namn, en urvals uppsättning eller ett urvals villkor definierat.</span><span class="sxs-lookup"><span data-stu-id="437f0-121">Each custom control entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="437f0-122">Urvals uppsättningar används vanligt vis när du vill definiera en grupp objekt som används i flera vyer.</span><span class="sxs-lookup"><span data-stu-id="437f0-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="437f0-123">Du kanske till exempel vill skapa en tabellvy och en listvy för samma uppsättning objekt.</span><span class="sxs-lookup"><span data-stu-id="437f0-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="437f0-124">Mer information om hur du definierar urvals uppsättningar finns i [definiera urvals uppsättningar](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="437f0-124">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="437f0-125">Mer information om komponenterna i en anpassad kontroll vy finns i [skapa anpassade kontroller](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="437f0-125">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="437f0-126">Se även</span><span class="sxs-lookup"><span data-stu-id="437f0-126">See Also</span></span>

[<span data-ttu-id="437f0-127">EntrySelectedBy-element för CustomEntry för vy (format)</span><span class="sxs-lookup"><span data-stu-id="437f0-127">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="437f0-128">Vy för anpassad kontroll</span><span class="sxs-lookup"><span data-stu-id="437f0-128">Custom Control View</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="437f0-129">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="437f0-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
