---
title: EntrySelectedBy Element för CustomEntry för anpassad kontroll för vy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7828b45b-eabf-4432-b127-131b4ef0c800
caps.latest.revision: 8
ms.openlocfilehash: e7176f9f6ef67116ea7c07a46797fb0ba84f915d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849324"
---
# <a name="entryselectedby-element-for-customentry-for-customcontrol-for-view-format"></a><span data-ttu-id="24fe9-102">EntrySelectedBy-element för CustomEntry för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="24fe9-102">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>

<span data-ttu-id="24fe9-103">Definierar vilka typer av .NET som använder den här anpassade posten eller villkor som måste finnas för den här posten som ska användas.</span><span class="sxs-lookup"><span data-stu-id="24fe9-103">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>

<span data-ttu-id="24fe9-104">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) anpassad kontroll Element (Format) CustomEntries konfigurationselement för anpassad kontroll för Visa (Format) CustomEntry elementet för CustomEntries för EntrySelectedBy vy (Format) Element för CustomEntry för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="24fe9-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="24fe9-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="24fe9-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="24fe9-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="24fe9-106">Attributes and Elements</span></span>

<span data-ttu-id="24fe9-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `EntrySelectedBy` element.</span><span class="sxs-lookup"><span data-stu-id="24fe9-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="24fe9-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="24fe9-108">Attributes</span></span>

<span data-ttu-id="24fe9-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="24fe9-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="24fe9-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="24fe9-110">Child Elements</span></span>

|<span data-ttu-id="24fe9-111">Element</span><span class="sxs-lookup"><span data-stu-id="24fe9-111">Element</span></span>|<span data-ttu-id="24fe9-112">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="24fe9-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="24fe9-113">SelectionCondition Element för EntrySelectedBy för CustomEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="24fe9-113">SelectionCondition Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="24fe9-114">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="24fe9-114">Optional element.</span></span><br /><br /> <span data-ttu-id="24fe9-115">Definierar de villkor som måste finnas för den här definitionen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="24fe9-115">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="24fe9-116">SelectionSetName Element för EntrySelectedBy för CustomEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="24fe9-116">SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)|<span data-ttu-id="24fe9-117">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="24fe9-117">Optional element.</span></span><br /><br /> <span data-ttu-id="24fe9-118">Anger en uppsättning med .NET-typer som använder den här definitionen av vyn kontroll.</span><span class="sxs-lookup"><span data-stu-id="24fe9-118">Specifies a set of .NET types that use this definition of the control view.</span></span>|
|[<span data-ttu-id="24fe9-119">TypeName-Element för EntrySelectedBy för CustomEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="24fe9-119">TypeName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="24fe9-120">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="24fe9-120">Optional element.</span></span><br /><br /> <span data-ttu-id="24fe9-121">Anger ett .NET-typ som använder den här definitionen av vyn kontroll.</span><span class="sxs-lookup"><span data-stu-id="24fe9-121">Specifies a .NET type that uses this definition of the control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="24fe9-122">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="24fe9-122">Parent Elements</span></span>

|<span data-ttu-id="24fe9-123">Element</span><span class="sxs-lookup"><span data-stu-id="24fe9-123">Element</span></span>|<span data-ttu-id="24fe9-124">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="24fe9-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="24fe9-125">CustomEntry Element för CustomEntries för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="24fe9-125">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="24fe9-126">Definierar de kontroller som används av specifika .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="24fe9-126">Defines the controls used by specific .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="24fe9-127">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="24fe9-127">Remarks</span></span>

<span data-ttu-id="24fe9-128">Du måste ange minst en typ, val av set eller urvalsvillkoret efter en post.</span><span class="sxs-lookup"><span data-stu-id="24fe9-128">You must specify at least one type, selection set, or selection condition for an entry.</span></span> <span data-ttu-id="24fe9-129">Det finns ingen högsta gräns för antalet underordnade element som du kan använda.</span><span class="sxs-lookup"><span data-stu-id="24fe9-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="24fe9-130">Val av villkor används för att definiera ett villkor som måste finnas för posten som ska användas, till exempel när ett objekt har en specifik egenskap eller när en specifik egenskapsvärdet eller skript som utvärderas till `true`.</span><span class="sxs-lookup"><span data-stu-id="24fe9-130">Selection conditions are used to define a condition that must exist for the entry to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="24fe9-131">Mer information om val av villkor finns i [definiera villkor för när en post i vyn eller objektet används](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="24fe9-131">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="24fe9-132">Mer information om komponenter för en anpassad kontroll vy finns i [anpassad kontroll vy](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="24fe9-132">For more information about the components of a custom control view, see [Custom Control View](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="24fe9-133">Se även</span><span class="sxs-lookup"><span data-stu-id="24fe9-133">See Also</span></span>

[<span data-ttu-id="24fe9-134">SelectionCondition Element för EntrySelectedBy för CustomEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="24fe9-134">SelectionCondition Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="24fe9-135">SelectionSetName Element för EntrySelectedBy för CustomEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="24fe9-135">SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

[<span data-ttu-id="24fe9-136">TypeName-Element för EntrySelectedBy för CustomEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="24fe9-136">TypeName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="24fe9-137">CustomEntry Element för CustomEntries för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="24fe9-137">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="24fe9-138">Visa anpassad kontroll</span><span class="sxs-lookup"><span data-stu-id="24fe9-138">Custom Control View</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="24fe9-139">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="24fe9-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
