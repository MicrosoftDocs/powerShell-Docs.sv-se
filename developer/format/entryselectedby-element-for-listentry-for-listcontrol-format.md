---
title: EntrySelectedBy Element för ListEntry för ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f7a74e9-764d-46ce-ab8e-8b9314ce1659
caps.latest.revision: 12
ms.openlocfilehash: 723619e67612b859d0acbab37eecd82141adf923
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846076"
---
# <a name="entryselectedby-element-for-listentry-for-listcontrol-format"></a><span data-ttu-id="89822-102">EntrySelectedBy-element för ListEntry för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="89822-102">EntrySelectedBy Element for ListEntry for ListControl (Format)</span></span>

<span data-ttu-id="89822-103">Definierar vilka typer av .NET som använder den här listan vydefinitionen eller villkor som måste finnas för den här definitionen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="89822-103">Defines the .NET types that use this list view definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="89822-104">I de flesta fall behövs bara en definition för en listvy.</span><span class="sxs-lookup"><span data-stu-id="89822-104">In most cases only one definition is needed for a list view.</span></span> <span data-ttu-id="89822-105">Du kan ange flera definitioner för listvyn om du vill använda samma listvyn för att visa olika data för olika objekt.</span><span class="sxs-lookup"><span data-stu-id="89822-105">However, you can provide multiple definitions for the list view if you want to use the same list view to display different data for different objects.</span></span>

<span data-ttu-id="89822-106">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) ListControl Element (Format) ListEntries konfigurationselement för ListControl (Format) ListEntry elementet för ListEntry för ListControl (Format) EntrySelectedBy elementet för ListEntry för ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="89822-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntry for ListControl (Format) EntrySelectedBy Element for ListEntry for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="89822-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="89822-107">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="89822-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="89822-108">Attributes and Elements</span></span>

<span data-ttu-id="89822-109">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `EntrySelectedBy` element.</span><span class="sxs-lookup"><span data-stu-id="89822-109">The following sections describe the attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="89822-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="89822-110">Attributes</span></span>

<span data-ttu-id="89822-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="89822-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="89822-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="89822-112">Child Elements</span></span>

|<span data-ttu-id="89822-113">Element</span><span class="sxs-lookup"><span data-stu-id="89822-113">Element</span></span>|<span data-ttu-id="89822-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="89822-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="89822-115">SelectionCondition Element för EntrySelectedBy för ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="89822-115">SelectionCondition Element for EntrySelectedBy for ListControl  (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="89822-116">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="89822-116">Optional element.</span></span><br /><br /> <span data-ttu-id="89822-117">Definierar de villkor som måste finnas för den här listan vydefinitionen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="89822-117">Defines the condition that must exist for this list view definition to be used.</span></span>|
|[<span data-ttu-id="89822-118">SelectionSetName Element för EnrtySelectedBy för ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="89822-118">SelectionSetName Element for EnrtySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="89822-119">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="89822-119">Optional element.</span></span><br /><br /> <span data-ttu-id="89822-120">Anger en uppsättning med .NET-typer som använder den här listan vydefinitionen.</span><span class="sxs-lookup"><span data-stu-id="89822-120">Specifies a set of .NET types that use this list view definition.</span></span>|
|[<span data-ttu-id="89822-121">TypeName-Element för EntrySelectedBy för ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="89822-121">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>](./typename-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="89822-122">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="89822-122">Optional element.</span></span><br /><br /> <span data-ttu-id="89822-123">Anger ett .NET-typ som använder den här listan vydefinitionen.</span><span class="sxs-lookup"><span data-stu-id="89822-123">Specifies a .NET type that uses this list view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="89822-124">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="89822-124">Parent Elements</span></span>

|<span data-ttu-id="89822-125">Element</span><span class="sxs-lookup"><span data-stu-id="89822-125">Element</span></span>|<span data-ttu-id="89822-126">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="89822-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="89822-127">ListEntry Element för ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="89822-127">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="89822-128">Definierar hur raderna i listan visas.</span><span class="sxs-lookup"><span data-stu-id="89822-128">Defines how the rows of the list are displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="89822-129">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="89822-129">Remarks</span></span>

<span data-ttu-id="89822-130">Du måste ange minst en typ, val av set eller urvalsvillkoret för en lista över vydefinitionen.</span><span class="sxs-lookup"><span data-stu-id="89822-130">You must specify at least one type, selection set, or selection condition for a list view definition.</span></span> <span data-ttu-id="89822-131">Det finns ingen högsta gräns för antalet underordnade element som du kan använda.</span><span class="sxs-lookup"><span data-stu-id="89822-131">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="89822-132">Val av villkor används för att definiera ett villkor som måste finnas för definitionen som ska användas, till exempel när ett objekt har en specifik egenskap eller som en specifik egenskapsvärde eller ett skript som utvärderas till `true`.</span><span class="sxs-lookup"><span data-stu-id="89822-132">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="89822-133">Mer information om val av villkor finns i [definiera villkor för när Data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="89822-133">For more information about selection conditions, see [Defining Conditions for when Data is displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="89822-134">Läs mer om komponenterna i en listvy, [skapar en listvy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="89822-134">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="89822-135">Exempel</span><span class="sxs-lookup"><span data-stu-id="89822-135">Example</span></span>

<span data-ttu-id="89822-136">I följande exempel visas hur du definierar objekt för en listvy med hjälp av sina .NET-typnamn.</span><span class="sxs-lookup"><span data-stu-id="89822-136">The following example shows how to define the objects for a list view using their .NET type name.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>NameofDotNetType</TypeName>>
  </EntrySelectedBy>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="89822-137">Se även</span><span class="sxs-lookup"><span data-stu-id="89822-137">See Also</span></span>

[<span data-ttu-id="89822-138">ListEntry Element för ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="89822-138">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="89822-139">SelectionCondition Element för EntrySelectedBy för ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="89822-139">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="89822-140">SelectionSetName Element för EnrtySelectedBy för ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="89822-140">SelectionSetName Element for EnrtySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="89822-141">TypeName-Element för EntrySelectedBy för ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="89822-141">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>](./typename-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="89822-142">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="89822-142">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="89822-143">Definiera villkor för när Data visas</span><span class="sxs-lookup"><span data-stu-id="89822-143">Defining Conditions for when Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="89822-144">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="89822-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
