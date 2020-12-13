---
ms.date: 09/13/2016
ms.topic: reference
title: ScriptBlock-element för SelectionCondition för EntrySelectedBy för TableControl (format)
description: ScriptBlock-element för SelectionCondition för EntrySelectedBy för TableControl (format)
ms.openlocfilehash: a984bda6b8fba3a5cb9485576ffd847f0d366d3e
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659888"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="caf9a-103">ScriptBlock-element för SelectionCondition för EntrySelectedBy för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="caf9a-103">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="caf9a-104">Anger det skript block som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="caf9a-104">Specifies the script block that triggers the condition.</span></span> <span data-ttu-id="caf9a-105">När det här skriptet utvärderas `true` , uppfylls villkoret och tabell posten används.</span><span class="sxs-lookup"><span data-stu-id="caf9a-105">When this script is evaluated to `true`, the condition is met, and the table entry is used.</span></span>

<span data-ttu-id="caf9a-106">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) TableControl-element (format) TableRowEntries-element (format) TableRowEntry-element (format) EntrySelectedBy-element för TableRowEntry (format) SelectionCondition element for EntrySelectedBy for TableRowEntry (format) script block-element för SelectionCondition för EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="caf9a-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="caf9a-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="caf9a-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="caf9a-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="caf9a-108">Attributes and Elements</span></span>

<span data-ttu-id="caf9a-109">I följande avsnitt beskrivs attribut, underordnade element och `ScriptBlock` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="caf9a-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="caf9a-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="caf9a-110">Attributes</span></span>

<span data-ttu-id="caf9a-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="caf9a-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="caf9a-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="caf9a-112">Child Elements</span></span>

<span data-ttu-id="caf9a-113">Inga.</span><span class="sxs-lookup"><span data-stu-id="caf9a-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="caf9a-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="caf9a-114">Parent Elements</span></span>

|<span data-ttu-id="caf9a-115">Element</span><span class="sxs-lookup"><span data-stu-id="caf9a-115">Element</span></span>|<span data-ttu-id="caf9a-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="caf9a-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="caf9a-117">SelectionCondition-element för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="caf9a-117">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="caf9a-118">Definierar det villkor som måste finnas för att den här tabell posten ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="caf9a-118">Defines the condition that must exist for this table entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="caf9a-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="caf9a-119">Text Value</span></span>

<span data-ttu-id="caf9a-120">Ange det skript som utvärderas.</span><span class="sxs-lookup"><span data-stu-id="caf9a-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="caf9a-121">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="caf9a-121">Remarks</span></span>

<span data-ttu-id="caf9a-122">Markerings villkoret måste innehålla minst ett skript block eller egenskaps namn, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="caf9a-122">The selection condition must specify at least one script block or property name, but cannot specify both.</span></span> <span data-ttu-id="caf9a-123">Mer information om hur du använder urvals villkor finns i [definiera villkor för när en visnings post eller ett objekt används](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="caf9a-123">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="caf9a-124">Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="caf9a-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="caf9a-125">Se även</span><span class="sxs-lookup"><span data-stu-id="caf9a-125">See Also</span></span>

[<span data-ttu-id="caf9a-126">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="caf9a-126">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="caf9a-127">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="caf9a-127">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="caf9a-128">PropertyName-element för SelectionCondition för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="caf9a-128">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[<span data-ttu-id="caf9a-129">SelectionCondition-element för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="caf9a-129">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="caf9a-130">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="caf9a-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
