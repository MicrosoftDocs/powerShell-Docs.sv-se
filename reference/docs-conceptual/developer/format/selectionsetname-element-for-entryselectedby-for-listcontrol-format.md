---
title: SelectionSetName-element för EntrySelectedBy för ListControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cff7763c-5ce0-49c1-a480-1249c9f57a13
caps.latest.revision: 11
ms.openlocfilehash: 7fd431b4b1ddecd3a7358c2bf97f299b97162b34
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353825"
---
# <a name="selectionsetname-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="aaf67-102">SelectionSetName-element för EntrySelectedBy för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="aaf67-102">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="aaf67-103">Anger en uppsättning .NET-objekt för List posten.</span><span class="sxs-lookup"><span data-stu-id="aaf67-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="aaf67-104">Det finns ingen gräns för antalet markerings uppsättningar som kan anges för en post.</span><span class="sxs-lookup"><span data-stu-id="aaf67-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="aaf67-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) ListControl-element (format) ListEntries-element (format) ListEntry element (format) EntrySelectedBy-element för ListEntry (format) SelectionSetName-element för EntrySelectedBy för ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="aaf67-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="aaf67-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="aaf67-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="aaf67-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="aaf67-107">Attributes and Elements</span></span>

<span data-ttu-id="aaf67-108">I följande avsnitt beskrivs attribut, underordnade element och ett överordnat element för elementet `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="aaf67-108">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="aaf67-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="aaf67-109">Attributes</span></span>

<span data-ttu-id="aaf67-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="aaf67-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="aaf67-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="aaf67-111">Child Elements</span></span>

<span data-ttu-id="aaf67-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="aaf67-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="aaf67-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="aaf67-113">Parent Elements</span></span>

|<span data-ttu-id="aaf67-114">Element</span><span class="sxs-lookup"><span data-stu-id="aaf67-114">Element</span></span>|<span data-ttu-id="aaf67-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="aaf67-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="aaf67-116">EntrySelectedBy-element för ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="aaf67-116">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="aaf67-117">Definierar de .NET-typer som använder den här List posten eller det villkor som måste finnas för att den här posten ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="aaf67-117">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="aaf67-118">Text värde</span><span class="sxs-lookup"><span data-stu-id="aaf67-118">Text Value</span></span>

<span data-ttu-id="aaf67-119">Ange namnet på urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="aaf67-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="aaf67-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="aaf67-120">Remarks</span></span>

<span data-ttu-id="aaf67-121">Varje List post måste ha minst ett typ namn, en urvals uppsättning eller ett urvals villkor definierat.</span><span class="sxs-lookup"><span data-stu-id="aaf67-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="aaf67-122">Urvals uppsättningar används vanligt vis när du vill definiera en grupp objekt som används i flera vyer.</span><span class="sxs-lookup"><span data-stu-id="aaf67-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="aaf67-123">Du kanske till exempel vill skapa en tabellvy och en listvy för samma uppsättning objekt.</span><span class="sxs-lookup"><span data-stu-id="aaf67-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="aaf67-124">Mer information om hur du definierar urvals uppsättningar finns i [definiera uppsättningar av objekt för en vy](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="aaf67-124">For more information about defining selection sets, see [Defining Sets of objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="aaf67-125">Mer information om komponenterna i en listvy finns i [skapa en listvy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="aaf67-125">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="aaf67-126">Exempel</span><span class="sxs-lookup"><span data-stu-id="aaf67-126">Example</span></span>

<span data-ttu-id="aaf67-127">I följande exempel visas hur du anger en markerings uppsättning för en post i en listvy.</span><span class="sxs-lookup"><span data-stu-id="aaf67-127">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="aaf67-128">Se även</span><span class="sxs-lookup"><span data-stu-id="aaf67-128">See Also</span></span>

[<span data-ttu-id="aaf67-129">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="aaf67-129">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="aaf67-130">EntrySelectedBy-element för ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="aaf67-130">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="aaf67-131">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="aaf67-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
