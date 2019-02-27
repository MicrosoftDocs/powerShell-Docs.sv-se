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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846097"
---
# <a name="entryselectedby-element-for-wideentry-format"></a><span data-ttu-id="a0cd2-102">EntrySelectedBy-element för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="a0cd2-102">EntrySelectedBy Element for WideEntry (Format)</span></span>

<span data-ttu-id="a0cd2-103">Definierar vilka typer av .NET som använder den här definitionen av bred vy eller ett villkor som måste finnas för den här definitionen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="a0cd2-103">Defines the .NET types that use this definition of the wide view or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="a0cd2-104">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy konfigurationselement för WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="a0cd2-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a0cd2-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="a0cd2-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a0cd2-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="a0cd2-106">Attributes and Elements</span></span>

<span data-ttu-id="a0cd2-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `EntrySelectedBy` element.</span><span class="sxs-lookup"><span data-stu-id="a0cd2-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a0cd2-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="a0cd2-108">Attributes</span></span>

<span data-ttu-id="a0cd2-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="a0cd2-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a0cd2-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="a0cd2-110">Child Elements</span></span>

|<span data-ttu-id="a0cd2-111">Element</span><span class="sxs-lookup"><span data-stu-id="a0cd2-111">Element</span></span>|<span data-ttu-id="a0cd2-112">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a0cd2-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a0cd2-113">SelectionCondition Element för EntrySelectedBy för WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="a0cd2-113">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="a0cd2-114">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="a0cd2-114">Optional element.</span></span><br /><br /> <span data-ttu-id="a0cd2-115">Definierar de villkor som måste finnas för den här definitionen för bred vy som ska användas.</span><span class="sxs-lookup"><span data-stu-id="a0cd2-115">Defines the condition that must exist for this wide view definition to be used.</span></span>|
|[<span data-ttu-id="a0cd2-116">SelectionSetName Element för EntrySelectedBy för WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="a0cd2-116">SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="a0cd2-117">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="a0cd2-117">Optional element.</span></span><br /><br /> <span data-ttu-id="a0cd2-118">Anger en uppsättning med .NET-typer som använder den här definitionen för bred vy.</span><span class="sxs-lookup"><span data-stu-id="a0cd2-118">Specifies a set of .NET types that use this wide view definition.</span></span>|
|[<span data-ttu-id="a0cd2-119">TypeName-Element för EntrySelectedBy för WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="a0cd2-119">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="a0cd2-120">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="a0cd2-120">Optional element.</span></span><br /><br /> <span data-ttu-id="a0cd2-121">Anger ett .NET-typ som använder den här definitionen för bred vy.</span><span class="sxs-lookup"><span data-stu-id="a0cd2-121">Specifies a .NET type that uses this wide view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a0cd2-122">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="a0cd2-122">Parent Elements</span></span>

|<span data-ttu-id="a0cd2-123">Element</span><span class="sxs-lookup"><span data-stu-id="a0cd2-123">Element</span></span>|<span data-ttu-id="a0cd2-124">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a0cd2-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a0cd2-125">WideEntry Element (Format)</span><span class="sxs-lookup"><span data-stu-id="a0cd2-125">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="a0cd2-126">Innehåller en definition av bred vy.</span><span class="sxs-lookup"><span data-stu-id="a0cd2-126">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a0cd2-127">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="a0cd2-127">Remarks</span></span>

<span data-ttu-id="a0cd2-128">Du måste ange minst en typ, val av set eller urvalsvillkoret för en bred vy-definition.</span><span class="sxs-lookup"><span data-stu-id="a0cd2-128">You must specify at least one type, selection set, or selection condition for a wide view definition.</span></span> <span data-ttu-id="a0cd2-129">Det finns ingen högsta gräns för antalet underordnade element som du kan använda.</span><span class="sxs-lookup"><span data-stu-id="a0cd2-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="a0cd2-130">Val av villkor används för att definiera ett villkor som måste finnas för definitionen som ska användas, till exempel när ett objekt har en specifik egenskap eller som en specifik egenskapsvärdet eller skriptvärdet utvärderas till `true`.</span><span class="sxs-lookup"><span data-stu-id="a0cd2-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script value evaluates to `true`.</span></span> <span data-ttu-id="a0cd2-131">Mer information om val av villkor finns i [definiera villkor för att visa Data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="a0cd2-131">For more information about selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="a0cd2-132">Mer information om andra komponenter för en bred vy finns i [skapar en bred vy](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="a0cd2-132">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a0cd2-133">Se även</span><span class="sxs-lookup"><span data-stu-id="a0cd2-133">See Also</span></span>

[<span data-ttu-id="a0cd2-134">WideEntry Element (Format)</span><span class="sxs-lookup"><span data-stu-id="a0cd2-134">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="a0cd2-135">SelectionCondition Element för EntrySelectedBy för WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="a0cd2-135">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="a0cd2-136">SelectionSetName Element för EntrySelectedBy för WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="a0cd2-136">SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="a0cd2-137">TypeName-Element för EntrySelectedBy för WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="a0cd2-137">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="a0cd2-138">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="a0cd2-138">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="a0cd2-139">Definiera villkor för att visa Data</span><span class="sxs-lookup"><span data-stu-id="a0cd2-139">Defining Conditions for Displaying Data</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="a0cd2-140">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="a0cd2-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
