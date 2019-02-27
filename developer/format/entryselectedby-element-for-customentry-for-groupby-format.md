---
title: EntrySelectedBy Element för CustomEntry för GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a317d482-73cc-4c98-a002-1357fa879cd7
caps.latest.revision: 7
ms.openlocfilehash: cf1a80e845c38d97d71f26eba63c38a550958b79
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851585"
---
# <a name="entryselectedby-element-for-customentry-for-groupby-format"></a><span data-ttu-id="cc1cb-102">EntrySelectedBy-element för CustomEntry för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="cc1cb-102">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="cc1cb-103">Definierar vilka typer av .NET som använder den här kontrollen definitionen eller villkor som måste finnas för den här definitionen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="cc1cb-103">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="cc1cb-104">Det här elementet används när du definierar hur en ny grupp med objekt visas.</span><span class="sxs-lookup"><span data-stu-id="cc1cb-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="cc1cb-105">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) GroupBy konfigurationselement för Visa (Format) anpassad kontroll elementet för GroupBy (Format) CustomEntries Element för anpassad kontroll för GroupBy (Format) CustomEntry elementet för Anpassad kontroll för GroupBy (Format) EntrySelectedBy elementet för CustomEntry för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="cc1cb-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cc1cb-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="cc1cb-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cc1cb-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="cc1cb-107">Attributes and Elements</span></span>

<span data-ttu-id="cc1cb-108">I följande avsnitt beskrivs attribut, underordnade element och överordnade elementet i den `EntrySelectedBy` element.</span><span class="sxs-lookup"><span data-stu-id="cc1cb-108">The following sections describe attributes, child elements, and parent element of the `EntrySelectedBy` element.</span></span> <span data-ttu-id="cc1cb-109">Du måste ange minst en typ, val av set eller urvalsvillkoret definieras.</span><span class="sxs-lookup"><span data-stu-id="cc1cb-109">You must specify at least one type, selection set, or selection condition for a definition.</span></span> <span data-ttu-id="cc1cb-110">Det finns ingen högsta gräns för antalet underordnade element som du kan använda.</span><span class="sxs-lookup"><span data-stu-id="cc1cb-110">There is no maximum limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="cc1cb-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="cc1cb-111">Attributes</span></span>

<span data-ttu-id="cc1cb-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="cc1cb-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cc1cb-113">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="cc1cb-113">Child Elements</span></span>

|<span data-ttu-id="cc1cb-114">Element</span><span class="sxs-lookup"><span data-stu-id="cc1cb-114">Element</span></span>|<span data-ttu-id="cc1cb-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="cc1cb-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cc1cb-116">SelectionCondition Element för EntrySelectedBy för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="cc1cb-116">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="cc1cb-117">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="cc1cb-117">Optional element.</span></span><br /><br /> <span data-ttu-id="cc1cb-118">Definierar de villkor som måste finnas för den här definitionen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="cc1cb-118">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="cc1cb-119">SelectionSetName Element för EntrySelectedBy för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="cc1cb-119">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="cc1cb-120">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="cc1cb-120">Optional element.</span></span><br /><br /> <span data-ttu-id="cc1cb-121">Anger en uppsättning med .NET-typer som använder den här definitionen för kontrollen.</span><span class="sxs-lookup"><span data-stu-id="cc1cb-121">Specifies a set of .NET types that use this definition of the control.</span></span>|
|[<span data-ttu-id="cc1cb-122">TypeName-Element för EntrySelectedBy för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="cc1cb-122">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./typename-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="cc1cb-123">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="cc1cb-123">Optional element.</span></span><br /><br /> <span data-ttu-id="cc1cb-124">Anger ett .NET-typ som använder den här definitionen för kontrollen.</span><span class="sxs-lookup"><span data-stu-id="cc1cb-124">Specifies a .NET type that uses this definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="cc1cb-125">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="cc1cb-125">Parent Elements</span></span>

|<span data-ttu-id="cc1cb-126">Element</span><span class="sxs-lookup"><span data-stu-id="cc1cb-126">Element</span></span>|<span data-ttu-id="cc1cb-127">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="cc1cb-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cc1cb-128">CustomEntry Element för anpassad kontroll för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="cc1cb-128">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="cc1cb-129">Innehåller en definition av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="cc1cb-129">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="cc1cb-130">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="cc1cb-130">Remarks</span></span>

<span data-ttu-id="cc1cb-131">Val av villkor används för att definiera ett villkor som måste finnas för definitionen som ska användas, till exempel när ett objekt har en specifik egenskap eller när en specifik egenskapsvärdet eller skript som utvärderas till `true`.</span><span class="sxs-lookup"><span data-stu-id="cc1cb-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="cc1cb-132">Mer information om val av villkor finns i [definiera villkor för när en post i vyn eller objektet används](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="cc1cb-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cc1cb-133">Se även</span><span class="sxs-lookup"><span data-stu-id="cc1cb-133">See Also</span></span>

[<span data-ttu-id="cc1cb-134">SelectionCondition Element för EntrySelectedBy för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="cc1cb-134">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="cc1cb-135">SelectionSetName Element för EntrySelectedBy för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="cc1cb-135">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="cc1cb-136">TypeName-Element för EntrySelectedBy för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="cc1cb-136">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./typename-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="cc1cb-137">CustomEntry Element för CustomEntries för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="cc1cb-137">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="cc1cb-138">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="cc1cb-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
