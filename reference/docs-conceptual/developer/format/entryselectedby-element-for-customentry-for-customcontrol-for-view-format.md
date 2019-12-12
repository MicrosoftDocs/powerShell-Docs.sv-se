---
title: EntrySelectedBy-element för CustomEntry för CustomControl för View (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7828b45b-eabf-4432-b127-131b4ef0c800
caps.latest.revision: 8
ms.openlocfilehash: e7176f9f6ef67116ea7c07a46797fb0ba84f915d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72358997"
---
# <a name="entryselectedby-element-for-customentry-for-customcontrol-for-view-format"></a><span data-ttu-id="42913-102">EntrySelectedBy-element för CustomEntry för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="42913-102">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>

<span data-ttu-id="42913-103">Definierar de .NET-typer som använder den här anpassade posten eller det villkor som måste finnas för att den här posten ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="42913-103">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>

<span data-ttu-id="42913-104">Konfigurations element (format) ViewDefinitions element (format) View element (format) CustomControl element (format) CustomEntries-element för CustomControl för View (format) CustomEntry-element för CustomEntries för View (format) EntrySelectedBy Element för CustomEntry för vy (format)</span><span class="sxs-lookup"><span data-stu-id="42913-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="42913-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="42913-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="42913-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="42913-106">Attributes and Elements</span></span>

<span data-ttu-id="42913-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `EntrySelectedBy`-elementet.</span><span class="sxs-lookup"><span data-stu-id="42913-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="42913-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="42913-108">Attributes</span></span>

<span data-ttu-id="42913-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="42913-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="42913-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="42913-110">Child Elements</span></span>

|<span data-ttu-id="42913-111">Element</span><span class="sxs-lookup"><span data-stu-id="42913-111">Element</span></span>|<span data-ttu-id="42913-112">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="42913-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="42913-113">SelectionCondition-element för EntrySelectedBy för CustomEntry (format)</span><span class="sxs-lookup"><span data-stu-id="42913-113">SelectionCondition Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="42913-114">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="42913-114">Optional element.</span></span><br /><br /> <span data-ttu-id="42913-115">Definierar det villkor som måste finnas för att den här definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="42913-115">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="42913-116">SelectionSetName-element för EntrySelectedBy för CustomEntry (format)</span><span class="sxs-lookup"><span data-stu-id="42913-116">SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)|<span data-ttu-id="42913-117">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="42913-117">Optional element.</span></span><br /><br /> <span data-ttu-id="42913-118">Anger en uppsättning av .NET-typer som använder den här definitionen av kontrollen View.</span><span class="sxs-lookup"><span data-stu-id="42913-118">Specifies a set of .NET types that use this definition of the control view.</span></span>|
|[<span data-ttu-id="42913-119">Elementet TypeName för EntrySelectedBy för CustomEntry (format)</span><span class="sxs-lookup"><span data-stu-id="42913-119">TypeName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="42913-120">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="42913-120">Optional element.</span></span><br /><br /> <span data-ttu-id="42913-121">Anger en .NET-typ som använder den här definitionen av kontroll visningen.</span><span class="sxs-lookup"><span data-stu-id="42913-121">Specifies a .NET type that uses this definition of the control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="42913-122">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="42913-122">Parent Elements</span></span>

|<span data-ttu-id="42913-123">Element</span><span class="sxs-lookup"><span data-stu-id="42913-123">Element</span></span>|<span data-ttu-id="42913-124">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="42913-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="42913-125">CustomEntry-element för CustomEntries för vy (format)</span><span class="sxs-lookup"><span data-stu-id="42913-125">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="42913-126">Definierar de kontroller som används av vissa .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="42913-126">Defines the controls used by specific .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="42913-127">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="42913-127">Remarks</span></span>

<span data-ttu-id="42913-128">Du måste ange minst en typ, markerings uppsättning eller ett markerings villkor för en post.</span><span class="sxs-lookup"><span data-stu-id="42913-128">You must specify at least one type, selection set, or selection condition for an entry.</span></span> <span data-ttu-id="42913-129">Det finns ingen övre gräns för antalet underordnade element som du kan använda.</span><span class="sxs-lookup"><span data-stu-id="42913-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="42913-130">Urvals villkor används för att definiera ett villkor som måste finnas för att posten ska kunna användas, till exempel när ett objekt har en speciell egenskap eller när ett angivet egenskaps värde eller skript utvärderar till `true`.</span><span class="sxs-lookup"><span data-stu-id="42913-130">Selection conditions are used to define a condition that must exist for the entry to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="42913-131">Mer information om urvals villkor finns i [definiera villkor för när en visnings post eller ett objekt används](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="42913-131">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="42913-132">Mer information om komponenterna i en anpassad kontroll visas i [vyn anpassad kontroll](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="42913-132">For more information about the components of a custom control view, see [Custom Control View](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="42913-133">Se även</span><span class="sxs-lookup"><span data-stu-id="42913-133">See Also</span></span>

[<span data-ttu-id="42913-134">SelectionCondition-element för EntrySelectedBy för CustomEntry (format)</span><span class="sxs-lookup"><span data-stu-id="42913-134">SelectionCondition Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="42913-135">SelectionSetName-element för EntrySelectedBy för CustomEntry (format)</span><span class="sxs-lookup"><span data-stu-id="42913-135">SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

[<span data-ttu-id="42913-136">Elementet TypeName för EntrySelectedBy för CustomEntry (format)</span><span class="sxs-lookup"><span data-stu-id="42913-136">TypeName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="42913-137">CustomEntry-element för CustomEntries för vy (format)</span><span class="sxs-lookup"><span data-stu-id="42913-137">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="42913-138">Vy för anpassad kontroll</span><span class="sxs-lookup"><span data-stu-id="42913-138">Custom Control View</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="42913-139">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="42913-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
