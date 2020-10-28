---
ms.date: 09/13/2016
ms.topic: reference
title: EntrySelectedBy-element för CustomEntry för CustomControl för View (format)
description: EntrySelectedBy-element för CustomEntry för CustomControl för View (format)
ms.openlocfilehash: 4821f22560f35034f90d018e5a109004f331441f
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92655354"
---
# <a name="entryselectedby-element-for-customentry-for-customcontrol-for-view-format"></a><span data-ttu-id="0d7a3-103">EntrySelectedBy-element för CustomEntry för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="0d7a3-103">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>

<span data-ttu-id="0d7a3-104">Definierar de .NET-typer som använder den här anpassade posten eller det villkor som måste finnas för att den här posten ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="0d7a3-104">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>

<span data-ttu-id="0d7a3-105">Konfigurations element (format) ViewDefinitions element (format) View element (format) CustomControl element (format) CustomEntries-element för CustomControl för View (format) CustomEntry-element för CustomEntries för View (format) EntrySelectedBy-element för CustomEntry för View (format)</span><span class="sxs-lookup"><span data-stu-id="0d7a3-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0d7a3-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="0d7a3-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0d7a3-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="0d7a3-107">Attributes and Elements</span></span>

<span data-ttu-id="0d7a3-108">I följande avsnitt beskrivs attribut, underordnade element och `EntrySelectedBy` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="0d7a3-108">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0d7a3-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="0d7a3-109">Attributes</span></span>

<span data-ttu-id="0d7a3-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="0d7a3-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0d7a3-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="0d7a3-111">Child Elements</span></span>

|<span data-ttu-id="0d7a3-112">Element</span><span class="sxs-lookup"><span data-stu-id="0d7a3-112">Element</span></span>|<span data-ttu-id="0d7a3-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0d7a3-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0d7a3-114">SelectionCondition-element för EntrySelectedBy för CustomEntry (format)</span><span class="sxs-lookup"><span data-stu-id="0d7a3-114">SelectionCondition Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="0d7a3-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="0d7a3-115">Optional element.</span></span><br /><br /> <span data-ttu-id="0d7a3-116">Definierar det villkor som måste finnas för att den här definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="0d7a3-116">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="0d7a3-117">SelectionSetName-element för EntrySelectedBy för CustomEntry (format)</span><span class="sxs-lookup"><span data-stu-id="0d7a3-117">SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)|<span data-ttu-id="0d7a3-118">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="0d7a3-118">Optional element.</span></span><br /><br /> <span data-ttu-id="0d7a3-119">Anger en uppsättning av .NET-typer som använder den här definitionen av kontrollen View.</span><span class="sxs-lookup"><span data-stu-id="0d7a3-119">Specifies a set of .NET types that use this definition of the control view.</span></span>|
|[<span data-ttu-id="0d7a3-120">Elementet TypeName för EntrySelectedBy för CustomEntry (format)</span><span class="sxs-lookup"><span data-stu-id="0d7a3-120">TypeName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="0d7a3-121">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="0d7a3-121">Optional element.</span></span><br /><br /> <span data-ttu-id="0d7a3-122">Anger en .NET-typ som använder den här definitionen av kontroll visningen.</span><span class="sxs-lookup"><span data-stu-id="0d7a3-122">Specifies a .NET type that uses this definition of the control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0d7a3-123">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="0d7a3-123">Parent Elements</span></span>

|<span data-ttu-id="0d7a3-124">Element</span><span class="sxs-lookup"><span data-stu-id="0d7a3-124">Element</span></span>|<span data-ttu-id="0d7a3-125">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0d7a3-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0d7a3-126">CustomEntry-element för CustomEntries för vy (format)</span><span class="sxs-lookup"><span data-stu-id="0d7a3-126">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="0d7a3-127">Definierar de kontroller som används av vissa .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="0d7a3-127">Defines the controls used by specific .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0d7a3-128">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="0d7a3-128">Remarks</span></span>

<span data-ttu-id="0d7a3-129">Du måste ange minst en typ, markerings uppsättning eller ett markerings villkor för en post.</span><span class="sxs-lookup"><span data-stu-id="0d7a3-129">You must specify at least one type, selection set, or selection condition for an entry.</span></span> <span data-ttu-id="0d7a3-130">Det finns ingen övre gräns för antalet underordnade element som du kan använda.</span><span class="sxs-lookup"><span data-stu-id="0d7a3-130">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="0d7a3-131">Urvals villkor används för att definiera ett villkor som måste finnas för att posten ska kunna användas, till exempel när ett objekt har en speciell egenskap eller när ett angivet egenskaps värde eller skript utvärderas till `true` .</span><span class="sxs-lookup"><span data-stu-id="0d7a3-131">Selection conditions are used to define a condition that must exist for the entry to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="0d7a3-132">Mer information om urvals villkor finns i [definiera villkor för när en visnings post eller ett objekt används](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="0d7a3-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="0d7a3-133">Mer information om komponenterna i en anpassad kontroll visas i [vyn anpassad kontroll](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="0d7a3-133">For more information about the components of a custom control view, see [Custom Control View](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0d7a3-134">Se även</span><span class="sxs-lookup"><span data-stu-id="0d7a3-134">See Also</span></span>

[<span data-ttu-id="0d7a3-135">SelectionCondition-element för EntrySelectedBy för CustomEntry (format)</span><span class="sxs-lookup"><span data-stu-id="0d7a3-135">SelectionCondition Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="0d7a3-136">SelectionSetName-element för EntrySelectedBy för CustomEntry (format)</span><span class="sxs-lookup"><span data-stu-id="0d7a3-136">SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

[<span data-ttu-id="0d7a3-137">Elementet TypeName för EntrySelectedBy för CustomEntry (format)</span><span class="sxs-lookup"><span data-stu-id="0d7a3-137">TypeName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="0d7a3-138">CustomEntry-element för CustomEntries för vy (format)</span><span class="sxs-lookup"><span data-stu-id="0d7a3-138">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="0d7a3-139">Vy för anpassad kontroll</span><span class="sxs-lookup"><span data-stu-id="0d7a3-139">Custom Control View</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="0d7a3-140">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="0d7a3-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
