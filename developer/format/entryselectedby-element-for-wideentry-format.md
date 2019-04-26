---
title: EntrySelectedBy Element för WideEntry (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e0c98933-b7a5-4205-b811-06c0b0bf8988
caps.latest.revision: 9
ms.openlocfilehash: 54c7c261a23075721cd7bce75e530150dc0e0212
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066183"
---
# <a name="entryselectedby-element-for-wideentry-format"></a><span data-ttu-id="6d6fa-102">EntrySelectedBy-element för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="6d6fa-102">EntrySelectedBy Element for WideEntry (Format)</span></span>

<span data-ttu-id="6d6fa-103">Definierar vilka typer av .NET som använder den här definitionen av bred vy eller ett villkor som måste finnas för den här definitionen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="6d6fa-103">Defines the .NET types that use this definition of the wide view or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="6d6fa-104">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy konfigurationselement för WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="6d6fa-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6d6fa-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="6d6fa-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6d6fa-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="6d6fa-106">Attributes and Elements</span></span>

<span data-ttu-id="6d6fa-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `EntrySelectedBy` element.</span><span class="sxs-lookup"><span data-stu-id="6d6fa-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6d6fa-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="6d6fa-108">Attributes</span></span>

<span data-ttu-id="6d6fa-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="6d6fa-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6d6fa-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="6d6fa-110">Child Elements</span></span>

|<span data-ttu-id="6d6fa-111">Element</span><span class="sxs-lookup"><span data-stu-id="6d6fa-111">Element</span></span>|<span data-ttu-id="6d6fa-112">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="6d6fa-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6d6fa-113">SelectionCondition Element för EntrySelectedBy för WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="6d6fa-113">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="6d6fa-114">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="6d6fa-114">Optional element.</span></span><br /><br /> <span data-ttu-id="6d6fa-115">Definierar de villkor som måste finnas för den här definitionen för bred vy som ska användas.</span><span class="sxs-lookup"><span data-stu-id="6d6fa-115">Defines the condition that must exist for this wide view definition to be used.</span></span>|
|[<span data-ttu-id="6d6fa-116">SelectionSetName Element för EntrySelectedBy för WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="6d6fa-116">SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="6d6fa-117">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="6d6fa-117">Optional element.</span></span><br /><br /> <span data-ttu-id="6d6fa-118">Anger en uppsättning med .NET-typer som använder den här definitionen för bred vy.</span><span class="sxs-lookup"><span data-stu-id="6d6fa-118">Specifies a set of .NET types that use this wide view definition.</span></span>|
|[<span data-ttu-id="6d6fa-119">TypeName-Element för EntrySelectedBy för WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="6d6fa-119">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="6d6fa-120">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="6d6fa-120">Optional element.</span></span><br /><br /> <span data-ttu-id="6d6fa-121">Anger ett .NET-typ som använder den här definitionen för bred vy.</span><span class="sxs-lookup"><span data-stu-id="6d6fa-121">Specifies a .NET type that uses this wide view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6d6fa-122">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="6d6fa-122">Parent Elements</span></span>

|<span data-ttu-id="6d6fa-123">Element</span><span class="sxs-lookup"><span data-stu-id="6d6fa-123">Element</span></span>|<span data-ttu-id="6d6fa-124">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="6d6fa-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6d6fa-125">WideEntry Element (Format)</span><span class="sxs-lookup"><span data-stu-id="6d6fa-125">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="6d6fa-126">Innehåller en definition av bred vy.</span><span class="sxs-lookup"><span data-stu-id="6d6fa-126">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6d6fa-127">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="6d6fa-127">Remarks</span></span>

<span data-ttu-id="6d6fa-128">Du måste ange minst en typ, val av set eller urvalsvillkoret för en bred vy-definition.</span><span class="sxs-lookup"><span data-stu-id="6d6fa-128">You must specify at least one type, selection set, or selection condition for a wide view definition.</span></span> <span data-ttu-id="6d6fa-129">Det finns ingen högsta gräns för antalet underordnade element som du kan använda.</span><span class="sxs-lookup"><span data-stu-id="6d6fa-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="6d6fa-130">Val av villkor används för att definiera ett villkor som måste finnas för definitionen som ska användas, till exempel när ett objekt har en specifik egenskap eller som en specifik egenskapsvärdet eller skriptvärdet utvärderas till `true`.</span><span class="sxs-lookup"><span data-stu-id="6d6fa-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script value evaluates to `true`.</span></span> <span data-ttu-id="6d6fa-131">Mer information om val av villkor finns i [definiera villkor för att visa Data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="6d6fa-131">For more information about selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="6d6fa-132">Mer information om andra komponenter för en bred vy finns i [skapar en bred vy](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="6d6fa-132">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6d6fa-133">Se även</span><span class="sxs-lookup"><span data-stu-id="6d6fa-133">See Also</span></span>

[<span data-ttu-id="6d6fa-134">WideEntry Element (Format)</span><span class="sxs-lookup"><span data-stu-id="6d6fa-134">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="6d6fa-135">SelectionCondition Element för EntrySelectedBy för WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="6d6fa-135">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="6d6fa-136">SelectionSetName Element för EntrySelectedBy för WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="6d6fa-136">SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="6d6fa-137">TypeName-Element för EntrySelectedBy för WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="6d6fa-137">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="6d6fa-138">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="6d6fa-138">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="6d6fa-139">Definiera villkor för att visa Data</span><span class="sxs-lookup"><span data-stu-id="6d6fa-139">Defining Conditions for Displaying Data</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="6d6fa-140">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="6d6fa-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
