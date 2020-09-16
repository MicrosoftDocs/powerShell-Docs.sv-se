---
title: SelectionSetName-element för EntrySelectedBy for GroupBy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 362f7844c09a52494387a62e329adfb309767427
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785293"
---
# <a name="selectionsetname-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="99075-102">SelectionSetName-element för EntrySelectedBy för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="99075-102">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="99075-103">Anger en uppsättning .NET-objekt för List posten.</span><span class="sxs-lookup"><span data-stu-id="99075-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="99075-104">Det finns ingen gräns för antalet markerings uppsättningar som kan anges för en post.</span><span class="sxs-lookup"><span data-stu-id="99075-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span> <span data-ttu-id="99075-105">Det här elementet används när du definierar hur en ny grupp av objekt visas.</span><span class="sxs-lookup"><span data-stu-id="99075-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="99075-106">Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for GroupBy (format) CustomEntry-element for CustomControl for groupby (format) EntrySelectedBy-element för CustomEntry (format)</span><span class="sxs-lookup"><span data-stu-id="99075-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="99075-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="99075-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="99075-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="99075-108">Attributes and Elements</span></span>

<span data-ttu-id="99075-109">I följande avsnitt beskrivs attribut, underordnade element och `SelectionSetName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="99075-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="99075-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="99075-110">Attributes</span></span>

<span data-ttu-id="99075-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="99075-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="99075-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="99075-112">Child Elements</span></span>

<span data-ttu-id="99075-113">Inga.</span><span class="sxs-lookup"><span data-stu-id="99075-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="99075-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="99075-114">Parent Elements</span></span>

|<span data-ttu-id="99075-115">Element</span><span class="sxs-lookup"><span data-stu-id="99075-115">Element</span></span>|<span data-ttu-id="99075-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="99075-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="99075-117">EntrySelectedBy-element för CustomEntry för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="99075-117">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="99075-118">Definierar de .NET-typer som använder den här anpassade posten eller det villkor som måste finnas för att den här posten ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="99075-118">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="99075-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="99075-119">Text Value</span></span>

<span data-ttu-id="99075-120">Ange namnet på urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="99075-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="99075-121">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="99075-121">Remarks</span></span>

<span data-ttu-id="99075-122">Varje definition av anpassad kontroll måste ha minst ett typ namn, en urvals uppsättning eller ett urvals villkor definierat.</span><span class="sxs-lookup"><span data-stu-id="99075-122">Each custom control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="99075-123">Urvals uppsättningar används vanligt vis när du vill definiera en grupp objekt som används i flera vyer.</span><span class="sxs-lookup"><span data-stu-id="99075-123">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="99075-124">Du kanske till exempel vill skapa en tabellvy och en listvy för samma uppsättning objekt.</span><span class="sxs-lookup"><span data-stu-id="99075-124">For example, you may want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="99075-125">Mer information om hur du definierar urvals uppsättningar finns i [definiera urvals uppsättningar](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="99075-125">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="99075-126">Mer information om komponenterna i en anpassad kontroll vy finns i [skapa anpassade kontroller](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="99075-126">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="99075-127">Se även</span><span class="sxs-lookup"><span data-stu-id="99075-127">See Also</span></span>

[<span data-ttu-id="99075-128">EntrySelectedBy-element för CustomEntry för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="99075-128">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="99075-129">Skapa anpassade kontroller</span><span class="sxs-lookup"><span data-stu-id="99075-129">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="99075-130">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="99075-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
