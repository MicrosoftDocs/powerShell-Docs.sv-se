---
title: SelectionSetName Element för EntrySelectedBy för TableControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5dd0bd5d-f206-4cc6-a0f8-70700ee2c4b7
caps.latest.revision: 8
ms.openlocfilehash: 819906127e81355c45103ede85ef3608e1c1cfeb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063929"
---
# <a name="selectionsetname-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="17c3f-102">SelectionSetName-element för EntrySelectedBy för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="17c3f-102">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="17c3f-103">Anger en uppsättning .NET skriver att använda den här posten i tabellvyn.</span><span class="sxs-lookup"><span data-stu-id="17c3f-103">Specifies a set of .NET types the use this entry of the table view.</span></span> <span data-ttu-id="17c3f-104">Det finns ingen gräns för hur många uppsättningar för val av som kan anges för en post.</span><span class="sxs-lookup"><span data-stu-id="17c3f-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="17c3f-105">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format) SelectionSetName konfigurationselement för EntrySelectedBy för TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="17c3f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format) SelectionSetName Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="17c3f-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="17c3f-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="17c3f-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="17c3f-107">Attributes and Elements</span></span>

<span data-ttu-id="17c3f-108">I följande avsnitt beskrivs attribut, element i underordnade och överordnade element.</span><span class="sxs-lookup"><span data-stu-id="17c3f-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="17c3f-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="17c3f-109">Attributes</span></span>

<span data-ttu-id="17c3f-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="17c3f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="17c3f-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="17c3f-111">Child Elements</span></span>

<span data-ttu-id="17c3f-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="17c3f-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="17c3f-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="17c3f-113">Parent Elements</span></span>

|<span data-ttu-id="17c3f-114">Element</span><span class="sxs-lookup"><span data-stu-id="17c3f-114">Element</span></span>|<span data-ttu-id="17c3f-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="17c3f-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="17c3f-116">EntrySelectedBy Element (Format)</span><span class="sxs-lookup"><span data-stu-id="17c3f-116">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="17c3f-117">Definierar vilka typer av .NET som använder den här posten eller villkor som måste finnas för den här posten som ska användas.</span><span class="sxs-lookup"><span data-stu-id="17c3f-117">Defines the .NET types that use this entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="17c3f-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="17c3f-118">Text Value</span></span>

<span data-ttu-id="17c3f-119">Ange namnet på val av uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="17c3f-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="17c3f-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="17c3f-120">Remarks</span></span>

<span data-ttu-id="17c3f-121">Inställningarna används vanligtvis när du vill definiera en grupp med objekt som används i flera vyer.</span><span class="sxs-lookup"><span data-stu-id="17c3f-121">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="17c3f-122">Du kanske vill skapa en tabell och en listvy för samma uppsättning objekt.</span><span class="sxs-lookup"><span data-stu-id="17c3f-122">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="17c3f-123">Mer information om hur du definierar inställningarna finns i [definiera anger av objekt som en vy](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="17c3f-123">For more information about defining selection sets, see [Defining Sets of objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="17c3f-124">Om du anger ett urval som angetts för en post, kan du inte ange ett namn.</span><span class="sxs-lookup"><span data-stu-id="17c3f-124">If you specify a selection set for an entry, you cannot specify a type name.</span></span> <span data-ttu-id="17c3f-125">Läs mer om hur du anger en .NET-typ, [TypeName-Element för EntrySelectedBy för TableRowEntry (Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md).</span><span class="sxs-lookup"><span data-stu-id="17c3f-125">For more information about how to specify a .NET type, see [TypeName Element for EntrySelectedBy for TableRowEntry (Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md).</span></span>

<span data-ttu-id="17c3f-126">Läs mer om komponenterna i en tabellvy, [skapar en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="17c3f-126">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="17c3f-127">Se även</span><span class="sxs-lookup"><span data-stu-id="17c3f-127">See Also</span></span>

[<span data-ttu-id="17c3f-128">EntrySelectedBy Element (Format)</span><span class="sxs-lookup"><span data-stu-id="17c3f-128">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="17c3f-129">Definiera uppsättningar med objekt för en vy</span><span class="sxs-lookup"><span data-stu-id="17c3f-129">Defining Sets of objects for a View</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="17c3f-130">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="17c3f-130">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="17c3f-131">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="17c3f-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
