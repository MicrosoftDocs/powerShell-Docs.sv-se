---
ms.date: 09/13/2016
ms.topic: reference
title: EntrySelectedBy-element för CustomEntry för Controls för View (format)
description: EntrySelectedBy-element för CustomEntry för Controls för View (format)
ms.openlocfilehash: 29b0574a95d81962fb3f72a526f89273baeea647
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660256"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="4db4c-103">EntrySelectedBy-element för CustomEntry för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="4db4c-103">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="4db4c-104">Definierar de .NET-typer som använder den här kontroll definitionen eller det villkor som måste finnas för att den här definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="4db4c-104">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="4db4c-105">Det här elementet används när du definierar kontroller som kan användas av en vy.</span><span class="sxs-lookup"><span data-stu-id="4db4c-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="4db4c-106">Konfigurations element (format) ViewDefinitions element (format) visar element (format) styr element (format) styr element (format) styr element (format) kontroll element för Controls for View (format) CustomControl-elementet för Control for View (format) CustomEntries-element för CustomControl for Controls for View (format) CustomEntry-elementet for CustomEntries for Controls for View (format) EntrySelectedBy element for</span><span class="sxs-lookup"><span data-stu-id="4db4c-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4db4c-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="4db4c-107">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4db4c-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="4db4c-108">Attributes and Elements</span></span>

<span data-ttu-id="4db4c-109">I följande avsnitt beskrivs attribut, underordnade element och `EntrySelectedBy` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="4db4c-109">The following sections describe attributes, child elements, and parent element of the `EntrySelectedBy` element.</span></span> <span data-ttu-id="4db4c-110">Du måste ange minst en typ, markerings uppsättning eller ett markerings villkor för en definition.</span><span class="sxs-lookup"><span data-stu-id="4db4c-110">You must specify at least one type, selection set, or selection condition for a definition.</span></span> <span data-ttu-id="4db4c-111">Det finns ingen övre gräns för antalet underordnade element som du kan använda.</span><span class="sxs-lookup"><span data-stu-id="4db4c-111">There is no maximum limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="4db4c-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="4db4c-112">Attributes</span></span>

<span data-ttu-id="4db4c-113">Inga.</span><span class="sxs-lookup"><span data-stu-id="4db4c-113">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4db4c-114">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="4db4c-114">Child Elements</span></span>

|<span data-ttu-id="4db4c-115">Element</span><span class="sxs-lookup"><span data-stu-id="4db4c-115">Element</span></span>|<span data-ttu-id="4db4c-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="4db4c-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4db4c-117">SelectionCondition-element för EntrySelectedBy för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="4db4c-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="4db4c-118">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="4db4c-118">Optional element.</span></span><br /><br /> <span data-ttu-id="4db4c-119">Definierar det villkor som måste finnas för att den här definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="4db4c-119">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="4db4c-120">SelectionSetName-element för EntrySelectedBy för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="4db4c-120">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="4db4c-121">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="4db4c-121">Optional element.</span></span><br /><br /> <span data-ttu-id="4db4c-122">Anger en uppsättning av .NET-typer som använder den här definitionen av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="4db4c-122">Specifies a set of .NET types that use this definition of the control.</span></span>|
|[<span data-ttu-id="4db4c-123">TypeName-element för EntrySelectedBy för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="4db4c-123">TypeName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./typename-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="4db4c-124">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="4db4c-124">Optional element.</span></span><br /><br /> <span data-ttu-id="4db4c-125">Anger en .NET-typ som använder den här definitionen av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="4db4c-125">Specifies a .NET type that uses this definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4db4c-126">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="4db4c-126">Parent Elements</span></span>

|<span data-ttu-id="4db4c-127">Element</span><span class="sxs-lookup"><span data-stu-id="4db4c-127">Element</span></span>|<span data-ttu-id="4db4c-128">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="4db4c-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4db4c-129">CustomEntry-element för CustomEntries för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="4db4c-129">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="4db4c-130">Ger en definition av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="4db4c-130">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4db4c-131">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="4db4c-131">Remarks</span></span>

<span data-ttu-id="4db4c-132">Urvals villkor används för att definiera ett villkor som måste finnas för att definitionen ska kunna användas, till exempel när ett objekt har en speciell egenskap eller när ett angivet egenskaps värde eller skript utvärderas till `true` .</span><span class="sxs-lookup"><span data-stu-id="4db4c-132">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="4db4c-133">Mer information om urvals villkor finns i [definiera villkor för när en visnings post eller ett objekt används](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="4db4c-133">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4db4c-134">Se även</span><span class="sxs-lookup"><span data-stu-id="4db4c-134">See Also</span></span>

[<span data-ttu-id="4db4c-135">CustomEntry-element för CustomEntries för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="4db4c-135">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="4db4c-136">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="4db4c-136">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
