---
title: EntrySelectedBy Element för EnumerableExpansion (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3af6aff8-4c2d-4f08-9bb1-e1f3ed3e583e
caps.latest.revision: 11
ms.openlocfilehash: 6a371bdbb85d07730c32931a4a79ee40856ce298
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846524"
---
# <a name="entryselectedby-element-for-enumerableexpansion-format"></a><span data-ttu-id="eef6c-102">EntrySelectedBy-element för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="eef6c-102">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="eef6c-103">Definierar vilka typer av .NET som använder den här definitionen eller villkor som måste finnas för den här definitionen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="eef6c-103">Defines the .NET types that use this definition or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="eef6c-104">Elementet (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy konfigurationselement för EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="eef6c-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="eef6c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="eef6c-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="eef6c-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="eef6c-106">Attributes and Elements</span></span>

<span data-ttu-id="eef6c-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `EntrySelectedBy` element.</span><span class="sxs-lookup"><span data-stu-id="eef6c-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="eef6c-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="eef6c-108">Attributes</span></span>

<span data-ttu-id="eef6c-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="eef6c-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="eef6c-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="eef6c-110">Child Elements</span></span>

|<span data-ttu-id="eef6c-111">Element</span><span class="sxs-lookup"><span data-stu-id="eef6c-111">Element</span></span>|<span data-ttu-id="eef6c-112">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eef6c-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="eef6c-113">SelectionCondition Element för EntrySelectedBy för EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="eef6c-113">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="eef6c-114">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="eef6c-114">Optional element.</span></span><br /><br /> <span data-ttu-id="eef6c-115">Definierar de villkor som måste finnas för att expandera samlingen objekt av den här definitionen.</span><span class="sxs-lookup"><span data-stu-id="eef6c-115">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|
|[<span data-ttu-id="eef6c-116">SelectionSetName Element för EntrySelectedBy för EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="eef6c-116">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="eef6c-117">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="eef6c-117">Optional element.</span></span><br /><br /> <span data-ttu-id="eef6c-118">Anger en uppsättning med .NET-typer som använder den här definitionen av hur mängdobjekt har expanderats.</span><span class="sxs-lookup"><span data-stu-id="eef6c-118">Specifies a set of .NET types that use this definition of how collection objects are expanded.</span></span>|
|[<span data-ttu-id="eef6c-119">TypeName-Element för EntrySelectedBy för EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="eef6c-119">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="eef6c-120">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="eef6c-120">Optional element.</span></span><br /><br /> <span data-ttu-id="eef6c-121">Anger ett .NET-typ som använder den här definitionen av hur mängdobjekt har expanderats.</span><span class="sxs-lookup"><span data-stu-id="eef6c-121">Specifies a .NET type that uses this definition of how collection objects are expanded.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="eef6c-122">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="eef6c-122">Parent Elements</span></span>

|<span data-ttu-id="eef6c-123">Element</span><span class="sxs-lookup"><span data-stu-id="eef6c-123">Element</span></span>|<span data-ttu-id="eef6c-124">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eef6c-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="eef6c-125">EnumerableExpansion Element (Format)</span><span class="sxs-lookup"><span data-stu-id="eef6c-125">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="eef6c-126">Definierar hur specifik .NET samling objekt visas när de visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="eef6c-126">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="eef6c-127">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="eef6c-127">Remarks</span></span>

<span data-ttu-id="eef6c-128">Du måste ange minst en typ, val av set eller urvalsvillkoret för en definition av posten.</span><span class="sxs-lookup"><span data-stu-id="eef6c-128">You must specify at least one type, selection set, or selection condition for a definition entry.</span></span> <span data-ttu-id="eef6c-129">Det finns ingen högsta gräns för antalet underordnade element som du kan använda.</span><span class="sxs-lookup"><span data-stu-id="eef6c-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="eef6c-130">Val av villkor används för att definiera ett villkor som måste finnas för definitionen som ska användas, till exempel när ett objekt har en specifik egenskap eller som en specifik egenskapsvärde eller ett skript som utvärderas till `true`.</span><span class="sxs-lookup"><span data-stu-id="eef6c-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="eef6c-131">Mer information om val av villkor finns i [definiera villkor för att visa Data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="eef6c-131">For more information about selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="eef6c-132">Se även</span><span class="sxs-lookup"><span data-stu-id="eef6c-132">See Also</span></span>

[<span data-ttu-id="eef6c-133">Definiera villkor för att visa Data</span><span class="sxs-lookup"><span data-stu-id="eef6c-133">Defining Conditions for Displaying Data</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="eef6c-134">EnumerableExpansion Element (Format)</span><span class="sxs-lookup"><span data-stu-id="eef6c-134">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)

[<span data-ttu-id="eef6c-135">SelectionCondition Element för EntrySelectedBy för EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="eef6c-135">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="eef6c-136">SelectionSetName Element för EntrySelectedBy för EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="eef6c-136">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="eef6c-137">TypeName-Element för EntrySelectedBy för EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="eef6c-137">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="eef6c-138">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="eef6c-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
