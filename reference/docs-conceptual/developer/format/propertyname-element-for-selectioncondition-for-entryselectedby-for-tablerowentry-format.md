---
title: PropertyName-element för SelectionCondition för EntrySelectedBy för TableRowEntry (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: bec8377fb13b8f288196a809e7aa4e7f46c66e31
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785548"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format"></a><span data-ttu-id="b8c0c-102">PropertyName-element för SelectionCondition för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="b8c0c-102">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

<span data-ttu-id="b8c0c-103">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="b8c0c-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="b8c0c-104">När den här egenskapen finns eller när den utvärderas `true` , uppfylls villkoret och tabell posten används.</span><span class="sxs-lookup"><span data-stu-id="b8c0c-104">When this property is present or when it evaluates to `true`, the condition is met, and the table entry is used.</span></span>

<span data-ttu-id="b8c0c-105">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) TableControl-element (format) TableRowEntries-element (format) TableRowEntry-element (format) EntrySelectedBy-element för TableRowEntry (format) SelectionCondition element for EntrySelectedBy för TableRowEntry (format) PropertyName-element för SelectionCondition för EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="b8c0c-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b8c0c-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="b8c0c-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b8c0c-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="b8c0c-107">Attributes and Elements</span></span>

<span data-ttu-id="b8c0c-108">I följande avsnitt beskrivs attribut, underordnade element och `PropertyName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="b8c0c-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b8c0c-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="b8c0c-109">Attributes</span></span>

<span data-ttu-id="b8c0c-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="b8c0c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b8c0c-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="b8c0c-111">Child Elements</span></span>

<span data-ttu-id="b8c0c-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="b8c0c-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b8c0c-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="b8c0c-113">Parent Elements</span></span>

|<span data-ttu-id="b8c0c-114">Element</span><span class="sxs-lookup"><span data-stu-id="b8c0c-114">Element</span></span>|<span data-ttu-id="b8c0c-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b8c0c-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b8c0c-116">SelectionCondition-element för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="b8c0c-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="b8c0c-117">Definierar det villkor som måste finnas för att den här tabell posten ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="b8c0c-117">Defines the condition that must exist for this table entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b8c0c-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="b8c0c-118">Text Value</span></span>

<span data-ttu-id="b8c0c-119">Ange .NET-egenskaps namnet.</span><span class="sxs-lookup"><span data-stu-id="b8c0c-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="b8c0c-120">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="b8c0c-120">Remarks</span></span>

<span data-ttu-id="b8c0c-121">Urvals villkoret måste innehålla minst ett egenskaps namn eller ett skript block, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="b8c0c-121">The selection condition must specify at least one property name or a script block, but cannot specify both.</span></span> <span data-ttu-id="b8c0c-122">Mer information om hur urvals villkor kan användas finns i [definiera villkor för när en visnings post eller ett objekt används](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="b8c0c-122">For more information about how selection conditions can be used, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="b8c0c-123">Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="b8c0c-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b8c0c-124">Se även</span><span class="sxs-lookup"><span data-stu-id="b8c0c-124">See Also</span></span>

[<span data-ttu-id="b8c0c-125">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="b8c0c-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="b8c0c-126">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="b8c0c-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="b8c0c-127">Script block-element för SelectionCondition för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="b8c0c-127">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="b8c0c-128">SelectionCondition-element för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="b8c0c-128">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="b8c0c-129">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="b8c0c-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
