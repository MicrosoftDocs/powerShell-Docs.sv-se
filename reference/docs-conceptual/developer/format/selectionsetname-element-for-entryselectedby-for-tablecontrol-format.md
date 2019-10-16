---
title: SelectionSetName-element för EntrySelectedBy för TableControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5dd0bd5d-f206-4cc6-a0f8-70700ee2c4b7
caps.latest.revision: 8
ms.openlocfilehash: 819906127e81355c45103ede85ef3608e1c1cfeb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72358846"
---
# <a name="selectionsetname-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="59a78-102">SelectionSetName-element för EntrySelectedBy för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="59a78-102">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="59a78-103">Anger en uppsättning .NET-typer. Använd den här posten i vyn tabell.</span><span class="sxs-lookup"><span data-stu-id="59a78-103">Specifies a set of .NET types the use this entry of the table view.</span></span> <span data-ttu-id="59a78-104">Det finns ingen gräns för antalet markerings uppsättningar som kan anges för en post.</span><span class="sxs-lookup"><span data-stu-id="59a78-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="59a78-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) TableControl-element (format) TableRowEntries-element (format) TableRowEntry element (format) EntrySelectedBy element (format) SelectionSetName-element för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="59a78-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format) SelectionSetName Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="59a78-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="59a78-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="59a78-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="59a78-107">Attributes and Elements</span></span>

<span data-ttu-id="59a78-108">I följande avsnitt beskrivs attribut, underordnade element och överordnade element.</span><span class="sxs-lookup"><span data-stu-id="59a78-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="59a78-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="59a78-109">Attributes</span></span>

<span data-ttu-id="59a78-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="59a78-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="59a78-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="59a78-111">Child Elements</span></span>

<span data-ttu-id="59a78-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="59a78-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="59a78-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="59a78-113">Parent Elements</span></span>

|<span data-ttu-id="59a78-114">Element</span><span class="sxs-lookup"><span data-stu-id="59a78-114">Element</span></span>|<span data-ttu-id="59a78-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="59a78-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="59a78-116">EntrySelectedBy-element (format)</span><span class="sxs-lookup"><span data-stu-id="59a78-116">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="59a78-117">Definierar de .NET-typer som använder den här posten eller det villkor som måste finnas för att den här posten ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="59a78-117">Defines the .NET types that use this entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="59a78-118">Text värde</span><span class="sxs-lookup"><span data-stu-id="59a78-118">Text Value</span></span>

<span data-ttu-id="59a78-119">Ange namnet på urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="59a78-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="59a78-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="59a78-120">Remarks</span></span>

<span data-ttu-id="59a78-121">Urvals uppsättningar används vanligt vis när du vill definiera en grupp objekt som används i flera vyer.</span><span class="sxs-lookup"><span data-stu-id="59a78-121">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="59a78-122">Du kanske till exempel vill skapa en tabellvy och en listvy för samma uppsättning objekt.</span><span class="sxs-lookup"><span data-stu-id="59a78-122">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="59a78-123">Mer information om hur du definierar urvals uppsättningar finns i [definiera uppsättningar av objekt för en vy](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="59a78-123">For more information about defining selection sets, see [Defining Sets of objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="59a78-124">Om du anger en markerings uppsättning för en post kan du inte ange ett typnamn.</span><span class="sxs-lookup"><span data-stu-id="59a78-124">If you specify a selection set for an entry, you cannot specify a type name.</span></span> <span data-ttu-id="59a78-125">Mer information om hur du anger en .NET-typ finns i [elementet TypeName för EntrySelectedBy för TableRowEntry (format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md).</span><span class="sxs-lookup"><span data-stu-id="59a78-125">For more information about how to specify a .NET type, see [TypeName Element for EntrySelectedBy for TableRowEntry (Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md).</span></span>

<span data-ttu-id="59a78-126">Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="59a78-126">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="59a78-127">Se även</span><span class="sxs-lookup"><span data-stu-id="59a78-127">See Also</span></span>

[<span data-ttu-id="59a78-128">EntrySelectedBy-element (format)</span><span class="sxs-lookup"><span data-stu-id="59a78-128">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="59a78-129">Definiera uppsättningar av objekt för en vy</span><span class="sxs-lookup"><span data-stu-id="59a78-129">Defining Sets of objects for a View</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="59a78-130">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="59a78-130">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="59a78-131">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="59a78-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
