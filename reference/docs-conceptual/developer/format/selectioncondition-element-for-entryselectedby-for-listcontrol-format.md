---
title: SelectionCondition-element för EntrySelectedBy för ListControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7649d5d0-2b56-49b5-a670-dde46caca343
caps.latest.revision: 11
ms.openlocfilehash: 7150b29ad84dfb587215ee3e64c356adbd5a6305
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417538"
---
# <a name="selectioncondition-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="fdfc9-102">SelectionCondition-element för EntrySelectedBy för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="fdfc9-102">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="fdfc9-103">Definierar det villkor som måste finnas för att använda den här definitionen av listvyn.</span><span class="sxs-lookup"><span data-stu-id="fdfc9-103">Defines the condition that must exist to use this definition of the list view.</span></span> <span data-ttu-id="fdfc9-104">Det finns ingen gräns för antalet urvals villkor som kan anges för en List definition.</span><span class="sxs-lookup"><span data-stu-id="fdfc9-104">There is no limit to the number of selection conditions that can be specified for a list definition.</span></span>

<span data-ttu-id="fdfc9-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) ListControl-element (format) ListEntries-element (format) ListEntry element (format) EntrySelectedBy-element för ListEntry (format) SelectionCondition-element för EntrySelectedBy för ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="fdfc9-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fdfc9-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="fdfc9-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fdfc9-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="fdfc9-107">Attributes and Elements</span></span>

<span data-ttu-id="fdfc9-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `SelectionCondition`-elementet.</span><span class="sxs-lookup"><span data-stu-id="fdfc9-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fdfc9-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="fdfc9-109">Attributes</span></span>

<span data-ttu-id="fdfc9-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="fdfc9-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fdfc9-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="fdfc9-111">Child Elements</span></span>

|<span data-ttu-id="fdfc9-112">Element</span><span class="sxs-lookup"><span data-stu-id="fdfc9-112">Element</span></span>|<span data-ttu-id="fdfc9-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="fdfc9-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fdfc9-114">PropertyName-element för SelectionCondition för EntrySelectedBy för ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="fdfc9-114">PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="fdfc9-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="fdfc9-115">Optional element.</span></span><br /><br /> <span data-ttu-id="fdfc9-116">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="fdfc9-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="fdfc9-117">Script block-element för SelectionCondition för EntrySelectedBy för ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="fdfc9-117">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="fdfc9-118">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="fdfc9-118">Optional element.</span></span><br /><br /> <span data-ttu-id="fdfc9-119">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="fdfc9-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="fdfc9-120">SelectionSetName-element för SelectionCondition för EntrySelectedBy för ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="fdfc9-120">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)|<span data-ttu-id="fdfc9-121">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="fdfc9-121">Optional element.</span></span><br /><br /> <span data-ttu-id="fdfc9-122">Anger den uppsättning av .NET-typer som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="fdfc9-122">Specifies the set of .NET types that trigger the condition.</span></span>|
|[<span data-ttu-id="fdfc9-123">Elementet TypeName för SelectionCondition för EntrySelectedBy för ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="fdfc9-123">TypeName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="fdfc9-124">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="fdfc9-124">Optional element.</span></span><br /><br /> <span data-ttu-id="fdfc9-125">Anger en .NET-typ som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="fdfc9-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="fdfc9-126">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="fdfc9-126">Parent Elements</span></span>

|<span data-ttu-id="fdfc9-127">Element</span><span class="sxs-lookup"><span data-stu-id="fdfc9-127">Element</span></span>|<span data-ttu-id="fdfc9-128">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="fdfc9-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fdfc9-129">EntrySelectedBy-element för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="fdfc9-129">EntrySelectedBy Element for TableRowEntry (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="fdfc9-130">Definierar de .NET-typer som använder den här tabell posten eller det villkor som måste finnas för att den här posten ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="fdfc9-130">Defines the .NET types that use this table entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="fdfc9-131">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="fdfc9-131">Remarks</span></span>

<span data-ttu-id="fdfc9-132">lWhen du definierar ett urvals villkor gäller följande krav:</span><span class="sxs-lookup"><span data-stu-id="fdfc9-132">lWhen you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="fdfc9-133">Markerings villkoret måste ange minst ett egenskaps namn eller ett skript block, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="fdfc9-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="fdfc9-134">Urvals villkoret kan ange valfritt antal .NET-typer eller markerings uppsättningar, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="fdfc9-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="fdfc9-135">Mer information om hur du använder urvals villkor finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="fdfc9-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="fdfc9-136">Mer information om andra komponenter i en listvy finns i [skapa en listvy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="fdfc9-136">For more information about other components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fdfc9-137">Se även</span><span class="sxs-lookup"><span data-stu-id="fdfc9-137">See Also</span></span>

[<span data-ttu-id="fdfc9-138">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="fdfc9-138">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="fdfc9-139">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="fdfc9-139">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="fdfc9-140">ListEntry-element (format)</span><span class="sxs-lookup"><span data-stu-id="fdfc9-140">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="fdfc9-141">SelectionSetName-element för EntrySelectedBy för ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="fdfc9-141">SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="fdfc9-142">Elementet TypeName för EntrySelectedBy för ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="fdfc9-142">TypeName Element for EntrySelectedBy for ListEntry (Format)</span></span>](/powershell/scripting/developer/format/typename-element-for-entryselectedby-for-listcontrol-format)

[<span data-ttu-id="fdfc9-143">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="fdfc9-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
