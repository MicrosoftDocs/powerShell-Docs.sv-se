---
title: Script block-element för SelectionCondition för EntrySelectedBy för TableControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: a23d3515749393e9f5a2053634a44d1a817ebf38
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783457"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="813d0-102">ScriptBlock-element för SelectionCondition för EntrySelectedBy för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="813d0-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="813d0-103">Anger det skript block som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="813d0-103">Specifies the script block that triggers the condition.</span></span> <span data-ttu-id="813d0-104">När det här skriptet utvärderas `true` , uppfylls villkoret och tabell posten används.</span><span class="sxs-lookup"><span data-stu-id="813d0-104">When this script is evaluated to `true`, the condition is met, and the table entry is used.</span></span>

<span data-ttu-id="813d0-105">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) TableControl-element (format) TableRowEntries-element (format) TableRowEntry-element (format) EntrySelectedBy-element för TableRowEntry (format) SelectionCondition element for EntrySelectedBy for TableRowEntry (format) script block-element för SelectionCondition för EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="813d0-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="813d0-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="813d0-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="813d0-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="813d0-107">Attributes and Elements</span></span>

<span data-ttu-id="813d0-108">I följande avsnitt beskrivs attribut, underordnade element och `ScriptBlock` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="813d0-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="813d0-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="813d0-109">Attributes</span></span>

<span data-ttu-id="813d0-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="813d0-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="813d0-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="813d0-111">Child Elements</span></span>

<span data-ttu-id="813d0-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="813d0-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="813d0-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="813d0-113">Parent Elements</span></span>

|<span data-ttu-id="813d0-114">Element</span><span class="sxs-lookup"><span data-stu-id="813d0-114">Element</span></span>|<span data-ttu-id="813d0-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="813d0-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="813d0-116">SelectionCondition-element för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="813d0-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="813d0-117">Definierar det villkor som måste finnas för att den här tabell posten ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="813d0-117">Defines the condition that must exist for this table entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="813d0-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="813d0-118">Text Value</span></span>

<span data-ttu-id="813d0-119">Ange det skript som utvärderas.</span><span class="sxs-lookup"><span data-stu-id="813d0-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="813d0-120">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="813d0-120">Remarks</span></span>

<span data-ttu-id="813d0-121">Markerings villkoret måste innehålla minst ett skript block eller egenskaps namn, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="813d0-121">The selection condition must specify at least one script block or property name, but cannot specify both.</span></span> <span data-ttu-id="813d0-122">Mer information om hur du använder urvals villkor finns i [definiera villkor för när en visnings post eller ett objekt används](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="813d0-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="813d0-123">Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="813d0-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="813d0-124">Se även</span><span class="sxs-lookup"><span data-stu-id="813d0-124">See Also</span></span>

[<span data-ttu-id="813d0-125">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="813d0-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="813d0-126">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="813d0-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="813d0-127">PropertyName-element för SelectionCondition för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="813d0-127">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[<span data-ttu-id="813d0-128">SelectionCondition-element för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="813d0-128">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="813d0-129">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="813d0-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
