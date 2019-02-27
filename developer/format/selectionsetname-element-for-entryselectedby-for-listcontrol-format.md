---
title: SelectionSetName Element för EntrySelectedBy för ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cff7763c-5ce0-49c1-a480-1249c9f57a13
caps.latest.revision: 11
ms.openlocfilehash: 7fd431b4b1ddecd3a7358c2bf97f299b97162b34
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849723"
---
# <a name="selectionsetname-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="c92e8-102">SelectionSetName-element för EntrySelectedBy för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="c92e8-102">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="c92e8-103">Anger en uppsättning med .NET-objekt för posten.</span><span class="sxs-lookup"><span data-stu-id="c92e8-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="c92e8-104">Det finns ingen gräns för hur många uppsättningar för val av som kan anges för en post.</span><span class="sxs-lookup"><span data-stu-id="c92e8-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="c92e8-105">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy konfigurationselement för ListEntry (Format) SelectionSetName elementet för EntrySelectedBy för ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="c92e8-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c92e8-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="c92e8-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c92e8-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="c92e8-107">Attributes and Elements</span></span>

<span data-ttu-id="c92e8-108">I följande avsnitt beskrivs attribut, underordnade element och överordnade elementet i den `SelectionSetName` element.</span><span class="sxs-lookup"><span data-stu-id="c92e8-108">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c92e8-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="c92e8-109">Attributes</span></span>

<span data-ttu-id="c92e8-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="c92e8-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c92e8-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="c92e8-111">Child Elements</span></span>

<span data-ttu-id="c92e8-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="c92e8-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c92e8-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="c92e8-113">Parent Elements</span></span>

|<span data-ttu-id="c92e8-114">Element</span><span class="sxs-lookup"><span data-stu-id="c92e8-114">Element</span></span>|<span data-ttu-id="c92e8-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c92e8-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c92e8-116">EntrySelectedBy Element för ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="c92e8-116">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="c92e8-117">Definierar vilka typer av .NET som använder den här posten eller villkor som måste finnas för den här posten som ska användas.</span><span class="sxs-lookup"><span data-stu-id="c92e8-117">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c92e8-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="c92e8-118">Text Value</span></span>

<span data-ttu-id="c92e8-119">Ange namnet på val av uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="c92e8-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="c92e8-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="c92e8-120">Remarks</span></span>

<span data-ttu-id="c92e8-121">Varje listpost måste ha minst ett namn, val av set eller Urvalsvillkoret som definierats.</span><span class="sxs-lookup"><span data-stu-id="c92e8-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="c92e8-122">Inställningarna används vanligtvis när du vill definiera en grupp med objekt som används i flera vyer.</span><span class="sxs-lookup"><span data-stu-id="c92e8-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="c92e8-123">Du kanske vill skapa en tabell och en listvy för samma uppsättning objekt.</span><span class="sxs-lookup"><span data-stu-id="c92e8-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="c92e8-124">Mer information om hur du definierar inställningarna finns i [definiera anger av objekt som en vy](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="c92e8-124">For more information about defining selection sets, see [Defining Sets of objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="c92e8-125">Läs mer om komponenterna i en listvy, [skapar en listvy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="c92e8-125">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="c92e8-126">Exempel</span><span class="sxs-lookup"><span data-stu-id="c92e8-126">Example</span></span>

<span data-ttu-id="c92e8-127">I följande exempel visas hur du anger ett urval som angetts för en post av en listvy.</span><span class="sxs-lookup"><span data-stu-id="c92e8-127">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="c92e8-128">Se även</span><span class="sxs-lookup"><span data-stu-id="c92e8-128">See Also</span></span>

[<span data-ttu-id="c92e8-129">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="c92e8-129">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="c92e8-130">EntrySelectedBy Element för ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="c92e8-130">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="c92e8-131">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="c92e8-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
