---
title: EntrySelectedBy-element för CustomEntry for GroupBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a317d482-73cc-4c98-a002-1357fa879cd7
caps.latest.revision: 7
ms.openlocfilehash: cf1a80e845c38d97d71f26eba63c38a550958b79
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355127"
---
# <a name="entryselectedby-element-for-customentry-for-groupby-format"></a><span data-ttu-id="bb3a1-102">EntrySelectedBy-element för CustomEntry för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="bb3a1-102">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="bb3a1-103">Definierar de .NET-typer som använder den här kontroll definitionen eller det villkor som måste finnas för att den här definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="bb3a1-103">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="bb3a1-104">Det här elementet används när du definierar hur en ny grupp av objekt visas.</span><span class="sxs-lookup"><span data-stu-id="bb3a1-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="bb3a1-105">Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for GroupBy (format) CustomEntry-element för CustomControl för GroupBy (format) EntrySelectedBy-element för CustomEntry för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="bb3a1-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bb3a1-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="bb3a1-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bb3a1-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="bb3a1-107">Attributes and Elements</span></span>

<span data-ttu-id="bb3a1-108">I följande avsnitt beskrivs attribut, underordnade element och ett överordnat element för elementet `EntrySelectedBy`.</span><span class="sxs-lookup"><span data-stu-id="bb3a1-108">The following sections describe attributes, child elements, and parent element of the `EntrySelectedBy` element.</span></span> <span data-ttu-id="bb3a1-109">Du måste ange minst en typ, markerings uppsättning eller ett markerings villkor för en definition.</span><span class="sxs-lookup"><span data-stu-id="bb3a1-109">You must specify at least one type, selection set, or selection condition for a definition.</span></span> <span data-ttu-id="bb3a1-110">Det finns ingen övre gräns för antalet underordnade element som du kan använda.</span><span class="sxs-lookup"><span data-stu-id="bb3a1-110">There is no maximum limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="bb3a1-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="bb3a1-111">Attributes</span></span>

<span data-ttu-id="bb3a1-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="bb3a1-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bb3a1-113">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="bb3a1-113">Child Elements</span></span>

|<span data-ttu-id="bb3a1-114">Element</span><span class="sxs-lookup"><span data-stu-id="bb3a1-114">Element</span></span>|<span data-ttu-id="bb3a1-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="bb3a1-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bb3a1-116">SelectionCondition-element för EntrySelectedBy för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="bb3a1-116">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="bb3a1-117">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="bb3a1-117">Optional element.</span></span><br /><br /> <span data-ttu-id="bb3a1-118">Definierar det villkor som måste finnas för att den här definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="bb3a1-118">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="bb3a1-119">SelectionSetName-element för EntrySelectedBy för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="bb3a1-119">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="bb3a1-120">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="bb3a1-120">Optional element.</span></span><br /><br /> <span data-ttu-id="bb3a1-121">Anger en uppsättning av .NET-typer som använder den här definitionen av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="bb3a1-121">Specifies a set of .NET types that use this definition of the control.</span></span>|
|[<span data-ttu-id="bb3a1-122">Elementet TypeName för EntrySelectedBy för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="bb3a1-122">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./typename-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="bb3a1-123">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="bb3a1-123">Optional element.</span></span><br /><br /> <span data-ttu-id="bb3a1-124">Anger en .NET-typ som använder den här definitionen av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="bb3a1-124">Specifies a .NET type that uses this definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="bb3a1-125">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="bb3a1-125">Parent Elements</span></span>

|<span data-ttu-id="bb3a1-126">Element</span><span class="sxs-lookup"><span data-stu-id="bb3a1-126">Element</span></span>|<span data-ttu-id="bb3a1-127">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="bb3a1-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bb3a1-128">CustomEntry-element för CustomControl för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="bb3a1-128">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="bb3a1-129">Ger en definition av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="bb3a1-129">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="bb3a1-130">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="bb3a1-130">Remarks</span></span>

<span data-ttu-id="bb3a1-131">Urvals villkor används för att definiera ett villkor som måste finnas för att definitionen ska kunna användas, till exempel när ett objekt har en speciell egenskap eller när ett angivet egenskaps värde eller skript utvärderar till `true`.</span><span class="sxs-lookup"><span data-stu-id="bb3a1-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="bb3a1-132">Mer information om urvals villkor finns i [definiera villkor för när en visnings post eller ett objekt används](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="bb3a1-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bb3a1-133">Se även</span><span class="sxs-lookup"><span data-stu-id="bb3a1-133">See Also</span></span>

[<span data-ttu-id="bb3a1-134">SelectionCondition-element för EntrySelectedBy för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="bb3a1-134">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="bb3a1-135">SelectionSetName-element för EntrySelectedBy för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="bb3a1-135">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="bb3a1-136">Elementet TypeName för EntrySelectedBy för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="bb3a1-136">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./typename-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="bb3a1-137">CustomEntry-element för CustomEntries för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="bb3a1-137">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="bb3a1-138">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="bb3a1-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
