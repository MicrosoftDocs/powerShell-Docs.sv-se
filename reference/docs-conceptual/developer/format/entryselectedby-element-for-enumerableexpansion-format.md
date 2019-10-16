---
title: EntrySelectedBy-element för EnumerableExpansion (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3af6aff8-4c2d-4f08-9bb1-e1f3ed3e583e
caps.latest.revision: 11
ms.openlocfilehash: 6a371bdbb85d07730c32931a4a79ee40856ce298
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72358987"
---
# <a name="entryselectedby-element-for-enumerableexpansion-format"></a><span data-ttu-id="a57ae-102">EntrySelectedBy-element för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="a57ae-102">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="a57ae-103">Definierar de .NET-typer som använder den här definitionen eller det villkor som måste finnas för att den här definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="a57ae-103">Defines the .NET types that use this definition or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="a57ae-104">Konfigurations element (format) DefaultSettings-element (format) EnumerableExpansions-element (format) EnumerableExpansion-element (format) EntrySelectedBy-element för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="a57ae-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a57ae-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="a57ae-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a57ae-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="a57ae-106">Attributes and Elements</span></span>

<span data-ttu-id="a57ae-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för elementet `EntrySelectedBy`.</span><span class="sxs-lookup"><span data-stu-id="a57ae-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a57ae-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="a57ae-108">Attributes</span></span>

<span data-ttu-id="a57ae-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="a57ae-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a57ae-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="a57ae-110">Child Elements</span></span>

|<span data-ttu-id="a57ae-111">Element</span><span class="sxs-lookup"><span data-stu-id="a57ae-111">Element</span></span>|<span data-ttu-id="a57ae-112">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a57ae-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a57ae-113">SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="a57ae-113">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="a57ae-114">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="a57ae-114">Optional element.</span></span><br /><br /> <span data-ttu-id="a57ae-115">Definierar det villkor som måste finnas för att expandera samlings objekt i den här definitionen.</span><span class="sxs-lookup"><span data-stu-id="a57ae-115">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|
|[<span data-ttu-id="a57ae-116">SelectionSetName-element för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="a57ae-116">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="a57ae-117">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="a57ae-117">Optional element.</span></span><br /><br /> <span data-ttu-id="a57ae-118">Anger en uppsättning .NET-typer som använder den här definitionen av hur samlings objekt expanderas.</span><span class="sxs-lookup"><span data-stu-id="a57ae-118">Specifies a set of .NET types that use this definition of how collection objects are expanded.</span></span>|
|[<span data-ttu-id="a57ae-119">Elementet TypeName för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="a57ae-119">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="a57ae-120">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="a57ae-120">Optional element.</span></span><br /><br /> <span data-ttu-id="a57ae-121">Anger en .NET-typ som använder den här definitionen av hur samlings objekt expanderas.</span><span class="sxs-lookup"><span data-stu-id="a57ae-121">Specifies a .NET type that uses this definition of how collection objects are expanded.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a57ae-122">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="a57ae-122">Parent Elements</span></span>

|<span data-ttu-id="a57ae-123">Element</span><span class="sxs-lookup"><span data-stu-id="a57ae-123">Element</span></span>|<span data-ttu-id="a57ae-124">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a57ae-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a57ae-125">EnumerableExpansion-element (format)</span><span class="sxs-lookup"><span data-stu-id="a57ae-125">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="a57ae-126">Definierar hur vissa .NET Collection-objekt expanderas när de visas i en vy.</span><span class="sxs-lookup"><span data-stu-id="a57ae-126">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a57ae-127">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="a57ae-127">Remarks</span></span>

<span data-ttu-id="a57ae-128">Du måste ange minst en typ, markerings uppsättning eller ett markerings villkor för en definitions post.</span><span class="sxs-lookup"><span data-stu-id="a57ae-128">You must specify at least one type, selection set, or selection condition for a definition entry.</span></span> <span data-ttu-id="a57ae-129">Det finns ingen övre gräns för antalet underordnade element som du kan använda.</span><span class="sxs-lookup"><span data-stu-id="a57ae-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="a57ae-130">Urvals villkor används för att definiera ett villkor som måste finnas för att definitionen ska kunna användas, till exempel när ett objekt har en speciell egenskap eller ett angivet egenskaps värde eller skript utvärderar till `true`.</span><span class="sxs-lookup"><span data-stu-id="a57ae-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="a57ae-131">Mer information om urvals villkor finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="a57ae-131">For more information about selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a57ae-132">Se även</span><span class="sxs-lookup"><span data-stu-id="a57ae-132">See Also</span></span>

[<span data-ttu-id="a57ae-133">Definiera villkor för visning av data</span><span class="sxs-lookup"><span data-stu-id="a57ae-133">Defining Conditions for Displaying Data</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="a57ae-134">EnumerableExpansion-element (format)</span><span class="sxs-lookup"><span data-stu-id="a57ae-134">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)

[<span data-ttu-id="a57ae-135">SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="a57ae-135">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="a57ae-136">SelectionSetName-element för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="a57ae-136">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="a57ae-137">Elementet TypeName för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="a57ae-137">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="a57ae-138">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="a57ae-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
