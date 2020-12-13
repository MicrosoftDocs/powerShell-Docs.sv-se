---
ms.date: 09/13/2016
ms.topic: reference
title: EntrySelectedBy-element för CustomEntry för CustomControl för View (format)
description: EntrySelectedBy-element för CustomEntry för CustomControl för View (format)
ms.openlocfilehash: 4821f22560f35034f90d018e5a109004f331441f
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655354"
---
# <a name="entryselectedby-element-for-customentry-for-customcontrol-for-view-format"></a><span data-ttu-id="022d5-103">EntrySelectedBy-element för CustomEntry för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="022d5-103">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>

<span data-ttu-id="022d5-104">Definierar de .NET-typer som använder den här anpassade posten eller det villkor som måste finnas för att den här posten ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="022d5-104">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>

<span data-ttu-id="022d5-105">Konfigurations element (format) ViewDefinitions element (format) View element (format) CustomControl element (format) CustomEntries-element för CustomControl för View (format) CustomEntry-element för CustomEntries för View (format) EntrySelectedBy-element för CustomEntry för View (format)</span><span class="sxs-lookup"><span data-stu-id="022d5-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="022d5-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="022d5-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="022d5-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="022d5-107">Attributes and Elements</span></span>

<span data-ttu-id="022d5-108">I följande avsnitt beskrivs attribut, underordnade element och `EntrySelectedBy` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="022d5-108">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="022d5-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="022d5-109">Attributes</span></span>

<span data-ttu-id="022d5-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="022d5-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="022d5-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="022d5-111">Child Elements</span></span>

|<span data-ttu-id="022d5-112">Element</span><span class="sxs-lookup"><span data-stu-id="022d5-112">Element</span></span>|<span data-ttu-id="022d5-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="022d5-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="022d5-114">SelectionCondition-element för EntrySelectedBy för CustomEntry (format)</span><span class="sxs-lookup"><span data-stu-id="022d5-114">SelectionCondition Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="022d5-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="022d5-115">Optional element.</span></span><br /><br /> <span data-ttu-id="022d5-116">Definierar det villkor som måste finnas för att den här definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="022d5-116">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="022d5-117">SelectionSetName-element för EntrySelectedBy för CustomEntry (format)</span><span class="sxs-lookup"><span data-stu-id="022d5-117">SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)|<span data-ttu-id="022d5-118">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="022d5-118">Optional element.</span></span><br /><br /> <span data-ttu-id="022d5-119">Anger en uppsättning av .NET-typer som använder den här definitionen av kontrollen View.</span><span class="sxs-lookup"><span data-stu-id="022d5-119">Specifies a set of .NET types that use this definition of the control view.</span></span>|
|[<span data-ttu-id="022d5-120">Elementet TypeName för EntrySelectedBy för CustomEntry (format)</span><span class="sxs-lookup"><span data-stu-id="022d5-120">TypeName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="022d5-121">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="022d5-121">Optional element.</span></span><br /><br /> <span data-ttu-id="022d5-122">Anger en .NET-typ som använder den här definitionen av kontroll visningen.</span><span class="sxs-lookup"><span data-stu-id="022d5-122">Specifies a .NET type that uses this definition of the control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="022d5-123">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="022d5-123">Parent Elements</span></span>

|<span data-ttu-id="022d5-124">Element</span><span class="sxs-lookup"><span data-stu-id="022d5-124">Element</span></span>|<span data-ttu-id="022d5-125">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="022d5-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="022d5-126">CustomEntry-element för CustomEntries för vy (format)</span><span class="sxs-lookup"><span data-stu-id="022d5-126">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="022d5-127">Definierar de kontroller som används av vissa .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="022d5-127">Defines the controls used by specific .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="022d5-128">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="022d5-128">Remarks</span></span>

<span data-ttu-id="022d5-129">Du måste ange minst en typ, markerings uppsättning eller ett markerings villkor för en post.</span><span class="sxs-lookup"><span data-stu-id="022d5-129">You must specify at least one type, selection set, or selection condition for an entry.</span></span> <span data-ttu-id="022d5-130">Det finns ingen övre gräns för antalet underordnade element som du kan använda.</span><span class="sxs-lookup"><span data-stu-id="022d5-130">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="022d5-131">Urvals villkor används för att definiera ett villkor som måste finnas för att posten ska kunna användas, till exempel när ett objekt har en speciell egenskap eller när ett angivet egenskaps värde eller skript utvärderas till `true` .</span><span class="sxs-lookup"><span data-stu-id="022d5-131">Selection conditions are used to define a condition that must exist for the entry to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="022d5-132">Mer information om urvals villkor finns i [definiera villkor för när en visnings post eller ett objekt används](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="022d5-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="022d5-133">Mer information om komponenterna i en anpassad kontroll visas i [vyn anpassad kontroll](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="022d5-133">For more information about the components of a custom control view, see [Custom Control View](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="022d5-134">Se även</span><span class="sxs-lookup"><span data-stu-id="022d5-134">See Also</span></span>

[<span data-ttu-id="022d5-135">SelectionCondition-element för EntrySelectedBy för CustomEntry (format)</span><span class="sxs-lookup"><span data-stu-id="022d5-135">SelectionCondition Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="022d5-136">SelectionSetName-element för EntrySelectedBy för CustomEntry (format)</span><span class="sxs-lookup"><span data-stu-id="022d5-136">SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

[<span data-ttu-id="022d5-137">Elementet TypeName för EntrySelectedBy för CustomEntry (format)</span><span class="sxs-lookup"><span data-stu-id="022d5-137">TypeName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="022d5-138">CustomEntry-element för CustomEntries för vy (format)</span><span class="sxs-lookup"><span data-stu-id="022d5-138">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="022d5-139">Vy för anpassad kontroll</span><span class="sxs-lookup"><span data-stu-id="022d5-139">Custom Control View</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="022d5-140">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="022d5-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
