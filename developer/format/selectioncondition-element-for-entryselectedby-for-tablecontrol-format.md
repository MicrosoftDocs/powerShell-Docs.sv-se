---
title: SelectionCondition Element för EntrySelectedBy för TableControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 912f3e63-e4d5-41ce-8710-6dfd8c885dc2
caps.latest.revision: 12
ms.openlocfilehash: 2faca6021dc26878869bdd2d35bc4ffc64d0fe7b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075672"
---
# <a name="selectioncondition-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="023e8-102">SelectionCondition-element för EntrySelectedBy för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="023e8-102">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="023e8-103">Definierar de villkor som måste finnas för att använda för den här definitionen av tabellvyn.</span><span class="sxs-lookup"><span data-stu-id="023e8-103">Defines the condition that must exist to use for this definition of the table view.</span></span> <span data-ttu-id="023e8-104">Det finns ingen gräns för hur många val av villkor som kan anges för en tabelldefinition.</span><span class="sxs-lookup"><span data-stu-id="023e8-104">There is no limit to the number of selection conditions that can be specified for a table definition.</span></span>

<span data-ttu-id="023e8-105">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy konfigurationselement för TableRowEntry (Format) SelectionCondition Element för EntrySelectedBy för TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="023e8-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="023e8-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="023e8-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="023e8-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="023e8-107">Attributes and Elements</span></span>

<span data-ttu-id="023e8-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i elementet SelectionCondition.</span><span class="sxs-lookup"><span data-stu-id="023e8-108">The following sections describe attributes, child elements, and the parent element of the SelectionCondition element.</span></span>

### <a name="attributes"></a><span data-ttu-id="023e8-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="023e8-109">Attributes</span></span>

<span data-ttu-id="023e8-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="023e8-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="023e8-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="023e8-111">Child Elements</span></span>

|<span data-ttu-id="023e8-112">Element</span><span class="sxs-lookup"><span data-stu-id="023e8-112">Element</span></span>|<span data-ttu-id="023e8-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="023e8-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="023e8-114">PropertyName-Element för SelectionCondition för EntrySelectedBy för TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="023e8-114">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)|<span data-ttu-id="023e8-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="023e8-115">Optional element.</span></span><br /><br /> <span data-ttu-id="023e8-116">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="023e8-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="023e8-117">ScriptBlock Element för SelectionCondition för EntrySelectedBy för TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="023e8-117">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="023e8-118">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="023e8-118">Optional element.</span></span><br /><br /> <span data-ttu-id="023e8-119">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="023e8-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="023e8-120">SelectionSetName Element för SelectionCondition för EntrySelectedBy för TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="023e8-120">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="023e8-121">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="023e8-121">Optional element.</span></span><br /><br /> <span data-ttu-id="023e8-122">Anger uppsättningen med .NET-typer som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="023e8-122">Specifies the set of .NET types that trigger the condition.</span></span>|
|[<span data-ttu-id="023e8-123">TypeName-Element för SelectionCondition för EntrySelectedBy för TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="023e8-123">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="023e8-124">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="023e8-124">Optional element.</span></span><br /><br /> <span data-ttu-id="023e8-125">Anger ett .NET-typ som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="023e8-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="023e8-126">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="023e8-126">Parent Elements</span></span>

|<span data-ttu-id="023e8-127">Element</span><span class="sxs-lookup"><span data-stu-id="023e8-127">Element</span></span>|<span data-ttu-id="023e8-128">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="023e8-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="023e8-129">EntrySelectedBy Element för TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="023e8-129">EntrySelectedBy Element for TableRowEntry (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="023e8-130">Definierar vilka typer av .NET som använder den här tabellposten eller villkor som måste finnas för den här posten som ska användas.</span><span class="sxs-lookup"><span data-stu-id="023e8-130">Defines the .NET types that use this table entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="023e8-131">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="023e8-131">Remarks</span></span>

<span data-ttu-id="023e8-132">Varje listpost måste ha minst ett namn, val av set eller Urvalsvillkoret som definierats.</span><span class="sxs-lookup"><span data-stu-id="023e8-132">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="023e8-133">När du definierar en urvalsvillkoret, gäller följande krav:</span><span class="sxs-lookup"><span data-stu-id="023e8-133">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="023e8-134">Urvalsvillkoret måste ange ett namn med minst en egenskap eller ett skriptblock, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="023e8-134">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="023e8-135">Urvalsvillkoret kan ange valfritt antal typer i .NET eller val av anger, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="023e8-135">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="023e8-136">Läs mer om hur du använder villkor för val av [definiera villkor för när en post i vyn eller objektet används](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="023e8-136">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="023e8-137">Läs mer om komponenterna i en tabellvy, [skapar en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="023e8-137">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="023e8-138">Se även</span><span class="sxs-lookup"><span data-stu-id="023e8-138">See Also</span></span>

[<span data-ttu-id="023e8-139">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="023e8-139">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="023e8-140">Definiera villkor för när Data visas</span><span class="sxs-lookup"><span data-stu-id="023e8-140">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="023e8-141">EntrySelectedBy Element (Format)</span><span class="sxs-lookup"><span data-stu-id="023e8-141">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="023e8-142">PropertyName-Element för SelectionCondition för EntrySelectedBy för TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="023e8-142">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[<span data-ttu-id="023e8-143">ScriptBlock Element för SelectionCondition för EntrySelectedBy för TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="023e8-143">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="023e8-144">SelectionSetName Element för SelectionCondition för EntrySelectedBy för TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="023e8-144">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="023e8-145">TypeName-Element för SelectionCondition för EntrySelectedBy för TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="023e8-145">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="023e8-146">Skriva ett Windows PowerShell formatering och skriver fil</span><span class="sxs-lookup"><span data-stu-id="023e8-146">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
