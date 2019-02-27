---
title: SelectionCondition Element för EntrySelectedBy för ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7649d5d0-2b56-49b5-a670-dde46caca343
caps.latest.revision: 11
ms.openlocfilehash: ec75945c5517c02fa001f0a38573c045ffcdbfd3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847854"
---
# <a name="selectioncondition-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="a08b0-102">SelectionCondition-element för EntrySelectedBy för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="a08b0-102">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="a08b0-103">Definierar de villkor som måste finnas för att använda den här definitionen i listvyn.</span><span class="sxs-lookup"><span data-stu-id="a08b0-103">Defines the condition that must exist to use this definition of the list view.</span></span> <span data-ttu-id="a08b0-104">Det finns ingen gräns för hur många val av villkor som kan anges för en definition av listan.</span><span class="sxs-lookup"><span data-stu-id="a08b0-104">There is no limit to the number of selection conditions that can be specified for a list definition.</span></span>

<span data-ttu-id="a08b0-105">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy konfigurationselement för ListEntry (Format) SelectionCondition elementet för EntrySelectedBy för ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="a08b0-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a08b0-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="a08b0-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a08b0-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="a08b0-107">Attributes and Elements</span></span>

<span data-ttu-id="a08b0-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `SelectionCondition` element.</span><span class="sxs-lookup"><span data-stu-id="a08b0-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a08b0-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="a08b0-109">Attributes</span></span>

<span data-ttu-id="a08b0-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="a08b0-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a08b0-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="a08b0-111">Child Elements</span></span>

|<span data-ttu-id="a08b0-112">Element</span><span class="sxs-lookup"><span data-stu-id="a08b0-112">Element</span></span>|<span data-ttu-id="a08b0-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a08b0-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a08b0-114">PropertyName-Element för SelectionCondition för EmtrySelectedBy för ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="a08b0-114">PropertyName Element for SelectionCondition for EmtrySelectedBy for ListEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="a08b0-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="a08b0-115">Optional element.</span></span><br /><br /> <span data-ttu-id="a08b0-116">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="a08b0-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="a08b0-117">ScriptBlock Element för SelectionCondition för EntrySelectedBy för ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="a08b0-117">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="a08b0-118">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="a08b0-118">Optional element.</span></span><br /><br /> <span data-ttu-id="a08b0-119">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="a08b0-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="a08b0-120">SelectionSetName Element för SelectionCondition för EntrySelectedBy för ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="a08b0-120">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)|<span data-ttu-id="a08b0-121">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="a08b0-121">Optional element.</span></span><br /><br /> <span data-ttu-id="a08b0-122">Anger uppsättningen med .NET-typer som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="a08b0-122">Specifies the set of .NET types that trigger the condition.</span></span>|
|[<span data-ttu-id="a08b0-123">TypeName-Element för SelectionCondition för EntrySelectedBy för ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="a08b0-123">TypeName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="a08b0-124">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="a08b0-124">Optional element.</span></span><br /><br /> <span data-ttu-id="a08b0-125">Anger ett .NET-typ som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="a08b0-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a08b0-126">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="a08b0-126">Parent Elements</span></span>

|<span data-ttu-id="a08b0-127">Element</span><span class="sxs-lookup"><span data-stu-id="a08b0-127">Element</span></span>|<span data-ttu-id="a08b0-128">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a08b0-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a08b0-129">EntrySelectedBy Element för TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="a08b0-129">EntrySelectedBy Element for TableRowEntry (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="a08b0-130">Definierar vilka typer av .NET som använder den här tabellposten eller villkor som måste finnas för den här posten som ska användas.</span><span class="sxs-lookup"><span data-stu-id="a08b0-130">Defines the .NET types that use this table entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a08b0-131">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="a08b0-131">Remarks</span></span>

<span data-ttu-id="a08b0-132">lWhen som du definierar ett villkor för val av följande krav gäller:</span><span class="sxs-lookup"><span data-stu-id="a08b0-132">lWhen you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="a08b0-133">Urvalsvillkoret måste ange ett namn med minst en egenskap eller ett skriptblock, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="a08b0-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="a08b0-134">Urvalsvillkoret kan ange valfritt antal typer i .NET eller val av anger, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="a08b0-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="a08b0-135">Läs mer om hur du använder villkor för val av [definiera villkor för när Data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="a08b0-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="a08b0-136">Läs mer om andra komponenter i en listvy, [skapar en listvy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="a08b0-136">For more information about other components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a08b0-137">Se även</span><span class="sxs-lookup"><span data-stu-id="a08b0-137">See Also</span></span>

[<span data-ttu-id="a08b0-138">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="a08b0-138">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="a08b0-139">Definiera villkor för när Data visas</span><span class="sxs-lookup"><span data-stu-id="a08b0-139">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="a08b0-140">ListEntry Element (Format)</span><span class="sxs-lookup"><span data-stu-id="a08b0-140">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="a08b0-141">SelectionSetName Element för EnrtySelectedBy för ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="a08b0-141">SelectionSetName Element for EnrtySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="a08b0-142">TypeName-Element för EntrySelectedBy för ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="a08b0-142">TypeName Element for EntrySelectedBy for ListEntry (Format)</span></span>](http://msdn.microsoft.com/en-us/fcd4daa6-f3fd-43f7-a468-03c582d34533)

[<span data-ttu-id="a08b0-143">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="a08b0-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
