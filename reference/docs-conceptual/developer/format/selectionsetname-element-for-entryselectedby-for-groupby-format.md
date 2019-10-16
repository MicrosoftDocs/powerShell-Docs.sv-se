---
title: SelectionSetName-element för EntrySelectedBy for GroupBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d569c623-2277-49e3-933e-c26262b91cd5
caps.latest.revision: 6
ms.openlocfilehash: 69cd113c444b4e3c5dceabcdfddb439cd1376f6b
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355743"
---
# <a name="selectionsetname-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="6db63-102">SelectionSetName-element för EntrySelectedBy för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="6db63-102">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="6db63-103">Anger en uppsättning .NET-objekt för List posten.</span><span class="sxs-lookup"><span data-stu-id="6db63-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="6db63-104">Det finns ingen gräns för antalet markerings uppsättningar som kan anges för en post.</span><span class="sxs-lookup"><span data-stu-id="6db63-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span> <span data-ttu-id="6db63-105">Det här elementet används när du definierar hur en ny grupp av objekt visas.</span><span class="sxs-lookup"><span data-stu-id="6db63-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="6db63-106">Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for GroupBy (format) CustomEntry-element för CustomControl for GroupBy (format) EntrySelectedBy-element för CustomEntry för GroupBy (format) SelectionSetName-element för EntrySelectedBy för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="6db63-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6db63-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="6db63-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6db63-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="6db63-108">Attributes and Elements</span></span>

<span data-ttu-id="6db63-109">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för elementet `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="6db63-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6db63-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="6db63-110">Attributes</span></span>

<span data-ttu-id="6db63-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="6db63-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6db63-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="6db63-112">Child Elements</span></span>

<span data-ttu-id="6db63-113">Ingen.</span><span class="sxs-lookup"><span data-stu-id="6db63-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6db63-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="6db63-114">Parent Elements</span></span>

|<span data-ttu-id="6db63-115">Element</span><span class="sxs-lookup"><span data-stu-id="6db63-115">Element</span></span>|<span data-ttu-id="6db63-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="6db63-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6db63-117">EntrySelectedBy-element för CustomEntry för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="6db63-117">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="6db63-118">Definierar de .NET-typer som använder den här anpassade posten eller det villkor som måste finnas för att den här posten ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="6db63-118">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="6db63-119">Text värde</span><span class="sxs-lookup"><span data-stu-id="6db63-119">Text Value</span></span>

<span data-ttu-id="6db63-120">Ange namnet på urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="6db63-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="6db63-121">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="6db63-121">Remarks</span></span>

<span data-ttu-id="6db63-122">Varje definition av anpassad kontroll måste ha minst ett typ namn, en urvals uppsättning eller ett urvals villkor definierat.</span><span class="sxs-lookup"><span data-stu-id="6db63-122">Each custom control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="6db63-123">Urvals uppsättningar används vanligt vis när du vill definiera en grupp objekt som används i flera vyer.</span><span class="sxs-lookup"><span data-stu-id="6db63-123">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="6db63-124">Du kanske till exempel vill skapa en tabellvy och en listvy för samma uppsättning objekt.</span><span class="sxs-lookup"><span data-stu-id="6db63-124">For example, you may want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="6db63-125">Mer information om hur du definierar urvals uppsättningar finns i [definiera urvals uppsättningar](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="6db63-125">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="6db63-126">Mer information om komponenterna i en anpassad kontroll vy finns i [skapa anpassade kontroller](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="6db63-126">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6db63-127">Se även</span><span class="sxs-lookup"><span data-stu-id="6db63-127">See Also</span></span>

[<span data-ttu-id="6db63-128">EntrySelectedBy-element för CustomEntry för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="6db63-128">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="6db63-129">Skapa anpassade kontroller</span><span class="sxs-lookup"><span data-stu-id="6db63-129">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="6db63-130">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="6db63-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
