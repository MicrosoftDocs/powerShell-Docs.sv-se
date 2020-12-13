---
ms.date: 09/13/2016
ms.topic: reference
title: EntrySelectedBy-element för CustomEntry för Controls för Configuration (format)
description: EntrySelectedBy-element för CustomEntry för Controls för Configuration (format)
ms.openlocfilehash: fadcdb69ac71269ba2f2f80baf139bb363d4acba
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666679"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-configuration-format"></a><span data-ttu-id="5518e-103">EntrySelectedBy-element för CustomEntry för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="5518e-103">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>

<span data-ttu-id="5518e-104">Definierar de .NET-typer som använder definitionen av den gemensamma kontrollen eller villkoret som måste finnas för att den här kontrollen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="5518e-104">Defines the .NET types that use the definition of the common control or the condition that must exist for this control to be used.</span></span> <span data-ttu-id="5518e-105">Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.</span><span class="sxs-lookup"><span data-stu-id="5518e-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="5518e-106">Konfigurations element (format) styr element i konfigurations-(format)-kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för Configuration (format) CustomEntry-element för CustomControl för Controls (format) EntrySelectedBy-element för CustomEntry för kontroll av konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="5518e-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5518e-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="5518e-107">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5518e-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="5518e-108">Attributes and Elements</span></span>

<span data-ttu-id="5518e-109">I följande avsnitt beskrivs attribut, underordnade element och `EntrySelectedBy` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="5518e-109">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5518e-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="5518e-110">Attributes</span></span>

<span data-ttu-id="5518e-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="5518e-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5518e-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="5518e-112">Child Elements</span></span>

|<span data-ttu-id="5518e-113">Element</span><span class="sxs-lookup"><span data-stu-id="5518e-113">Element</span></span>|<span data-ttu-id="5518e-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5518e-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5518e-115">SelectionCondition-element för EntrySelectedBy för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="5518e-115">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="5518e-116">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="5518e-116">Optional element.</span></span><br /><br /> <span data-ttu-id="5518e-117">Definierar det villkor som måste finnas för att den gemensamma kontroll definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="5518e-117">Defines the condition that must exist for the common control definition to be used.</span></span>|
|[<span data-ttu-id="5518e-118">SelectionSetName-element för EntrySelectedBy för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="5518e-118">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="5518e-119">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="5518e-119">Optional element.</span></span><br /><br /> <span data-ttu-id="5518e-120">Anger en uppsättning av .NET-typer som använder den här definitionen av den gemensamma kontrollen.</span><span class="sxs-lookup"><span data-stu-id="5518e-120">Specifies a set of .NET types that use this definition of the common control.</span></span>|
|[<span data-ttu-id="5518e-121">TypeName-element för EntrySelectedBy för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="5518e-121">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="5518e-122">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="5518e-122">Optional element.</span></span><br /><br /> <span data-ttu-id="5518e-123">Anger en .NET-typ som använder den här definitionen av den gemensamma kontrollen.</span><span class="sxs-lookup"><span data-stu-id="5518e-123">Specifies a .NET type that uses this definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5518e-124">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="5518e-124">Parent Elements</span></span>

|<span data-ttu-id="5518e-125">Element</span><span class="sxs-lookup"><span data-stu-id="5518e-125">Element</span></span>|<span data-ttu-id="5518e-126">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5518e-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5518e-127">CustomEntry-element för CustomControl för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="5518e-127">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="5518e-128">Ger en definition av den gemensamma kontrollen.</span><span class="sxs-lookup"><span data-stu-id="5518e-128">Provides a definition of the common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5518e-129">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="5518e-129">Remarks</span></span>

<span data-ttu-id="5518e-130">Varje definition måste minst ha minst en .NET-typ, markerings uppsättning eller ett urvals villkor angivet.</span><span class="sxs-lookup"><span data-stu-id="5518e-130">At a minimum, each definition must have at least one .NET type, selection set, or selection condition specified.</span></span> <span data-ttu-id="5518e-131">Det finns ingen övre gräns för antalet typer, markerings uppsättningar eller markerings villkor som du kan ange.</span><span class="sxs-lookup"><span data-stu-id="5518e-131">There is no maximum limit to the number of types, selection sets, or selection conditions that you can specify.</span></span>

## <a name="see-also"></a><span data-ttu-id="5518e-132">Se även</span><span class="sxs-lookup"><span data-stu-id="5518e-132">See Also</span></span>

[<span data-ttu-id="5518e-133">SelectionCondition-element för EntrySelectedBy för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="5518e-133">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="5518e-134">SelectionSetName-element för EntrySelectedBy för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="5518e-134">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="5518e-135">CustomEntry-element för CustomControl för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="5518e-135">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="5518e-136">TypeName-element för EntrySelectedBy för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="5518e-136">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="5518e-137">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="5518e-137">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
