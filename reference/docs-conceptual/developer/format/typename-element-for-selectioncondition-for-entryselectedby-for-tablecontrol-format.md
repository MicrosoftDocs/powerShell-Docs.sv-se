---
title: Elementet TypeName för SelectionCondition för EntrySelectedBy för TableControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e97d56fb-4e35-447a-9282-26f10d0a4609
caps.latest.revision: 11
ms.openlocfilehash: fe65ac95cead7df0069ffdae666fb34b7309fbb6
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353454"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="efb29-102">TypeName-element för SelectionCondition för EntrySelectedBy för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="efb29-102">TypeName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="efb29-103">Anger en .NET-typ som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="efb29-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="efb29-104">När den här typen är närvarande uppfylls villkoret och tabell raden används.</span><span class="sxs-lookup"><span data-stu-id="efb29-104">When this type is present, the condition is met, and the table row is used.</span></span>

<span data-ttu-id="efb29-105">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) TableControl-element (format) TableRowEntries-element (format) TableRowEntry element (format) EntrySelectedBy-element för TableRowEntry (format) SelectionCondition-element för EntrySelectedBy för TableRowEntry (format) elementet TypeName för SelectionCondition för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="efb29-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="efb29-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="efb29-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="efb29-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="efb29-107">Attributes and Elements</span></span>

<span data-ttu-id="efb29-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för elementet `TypeName`.</span><span class="sxs-lookup"><span data-stu-id="efb29-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="efb29-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="efb29-109">Attributes</span></span>

<span data-ttu-id="efb29-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="efb29-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="efb29-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="efb29-111">Child Elements</span></span>

<span data-ttu-id="efb29-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="efb29-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="efb29-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="efb29-113">Parent Elements</span></span>

|<span data-ttu-id="efb29-114">Element</span><span class="sxs-lookup"><span data-stu-id="efb29-114">Element</span></span>|<span data-ttu-id="efb29-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="efb29-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="efb29-116">SelectionCondition-element för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="efb29-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="efb29-117">Definierar det villkor som måste finnas för att den här tabell raden ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="efb29-117">Defines the condition that must exist for this table row to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="efb29-118">Text värde</span><span class="sxs-lookup"><span data-stu-id="efb29-118">Text Value</span></span>

<span data-ttu-id="efb29-119">Ange det fullständigt kvalificerade namnet för .NET-typen, t. ex. `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="efb29-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="efb29-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="efb29-120">Remarks</span></span>

<span data-ttu-id="efb29-121">Urvals villkoret kan ange valfritt antal .NET-typer eller markerings uppsättningar, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="efb29-121">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span> <span data-ttu-id="efb29-122">Mer information om hur du använder urvals villkor finns i [definiera villkor för när en visnings post eller ett objekt används](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="efb29-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="efb29-123">Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="efb29-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="efb29-124">Se även</span><span class="sxs-lookup"><span data-stu-id="efb29-124">See Also</span></span>

[<span data-ttu-id="efb29-125">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="efb29-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="efb29-126">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="efb29-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="efb29-127">SelectionCondition-element för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="efb29-127">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="efb29-128">SelectionSetName-element för SelectionCondition för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="efb29-128">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="efb29-129">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="efb29-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
