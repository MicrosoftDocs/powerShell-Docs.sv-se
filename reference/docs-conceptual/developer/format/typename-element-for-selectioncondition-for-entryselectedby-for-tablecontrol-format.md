---
title: Elementet TypeName för SelectionCondition för EntrySelectedBy för TableControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: b9367f0ea659b9dce8fe200a5a08873d53bc03a8
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772594"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="f47b5-102">TypeName-element för SelectionCondition för EntrySelectedBy för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="f47b5-102">TypeName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="f47b5-103">Anger en .NET-typ som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="f47b5-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="f47b5-104">När den här typen är närvarande uppfylls villkoret och tabell raden används.</span><span class="sxs-lookup"><span data-stu-id="f47b5-104">When this type is present, the condition is met, and the table row is used.</span></span>

<span data-ttu-id="f47b5-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) TableControl-element (format) TableRowEntries-element (format) TableRowEntry-element (format) EntrySelectedBy-element för TableRowEntry (format) SelectionCondition-element för EntrySelectedBy för TableRowEntry (format) element för SelectionCondition (format)</span><span class="sxs-lookup"><span data-stu-id="f47b5-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f47b5-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="f47b5-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f47b5-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="f47b5-107">Attributes and Elements</span></span>

<span data-ttu-id="f47b5-108">I följande avsnitt beskrivs attribut, underordnade element och `TypeName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="f47b5-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f47b5-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="f47b5-109">Attributes</span></span>

<span data-ttu-id="f47b5-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="f47b5-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f47b5-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="f47b5-111">Child Elements</span></span>

<span data-ttu-id="f47b5-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="f47b5-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f47b5-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="f47b5-113">Parent Elements</span></span>

|<span data-ttu-id="f47b5-114">Element</span><span class="sxs-lookup"><span data-stu-id="f47b5-114">Element</span></span>|<span data-ttu-id="f47b5-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f47b5-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f47b5-116">SelectionCondition-element för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="f47b5-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="f47b5-117">Definierar det villkor som måste finnas för att den här tabell raden ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="f47b5-117">Defines the condition that must exist for this table row to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f47b5-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="f47b5-118">Text Value</span></span>

<span data-ttu-id="f47b5-119">Ange det fullständigt kvalificerade namnet för .NET-typen, t `System.IO.DirectoryInfo` . ex..</span><span class="sxs-lookup"><span data-stu-id="f47b5-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="f47b5-120">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="f47b5-120">Remarks</span></span>

<span data-ttu-id="f47b5-121">Urvals villkoret kan ange valfritt antal .NET-typer eller markerings uppsättningar, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="f47b5-121">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span> <span data-ttu-id="f47b5-122">Mer information om hur du använder urvals villkor finns i [definiera villkor för när en visnings post eller ett objekt används](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="f47b5-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="f47b5-123">Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="f47b5-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f47b5-124">Se även</span><span class="sxs-lookup"><span data-stu-id="f47b5-124">See Also</span></span>

[<span data-ttu-id="f47b5-125">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="f47b5-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="f47b5-126">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="f47b5-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="f47b5-127">SelectionCondition-element för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="f47b5-127">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="f47b5-128">SelectionSetName-element för SelectionCondition för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="f47b5-128">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="f47b5-129">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="f47b5-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
