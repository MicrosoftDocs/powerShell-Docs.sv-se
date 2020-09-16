---
title: EntrySelectedBy-element för WideEntry (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: ba0a776839c39d753d12859335388c5326639fd4
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774090"
---
# <a name="entryselectedby-element-for-wideentry-format"></a><span data-ttu-id="afdf5-102">EntrySelectedBy-element för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="afdf5-102">EntrySelectedBy Element for WideEntry (Format)</span></span>

<span data-ttu-id="afdf5-103">Definierar de .NET-typer som använder den här definitionen för wide View eller det villkor som måste finnas för att den här definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="afdf5-103">Defines the .NET types that use this definition of the wide view or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="afdf5-104">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) WideControl-element (format) WideEntries-element (format) WideEntry element (format) EntrySelectedBy-element för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="afdf5-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="afdf5-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="afdf5-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="afdf5-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="afdf5-106">Attributes and Elements</span></span>

<span data-ttu-id="afdf5-107">I följande avsnitt beskrivs attribut, underordnade element och `EntrySelectedBy` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="afdf5-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="afdf5-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="afdf5-108">Attributes</span></span>

<span data-ttu-id="afdf5-109">Inga.</span><span class="sxs-lookup"><span data-stu-id="afdf5-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="afdf5-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="afdf5-110">Child Elements</span></span>

|<span data-ttu-id="afdf5-111">Element</span><span class="sxs-lookup"><span data-stu-id="afdf5-111">Element</span></span>|<span data-ttu-id="afdf5-112">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="afdf5-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="afdf5-113">SelectionCondition-element för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="afdf5-113">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="afdf5-114">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="afdf5-114">Optional element.</span></span><br /><br /> <span data-ttu-id="afdf5-115">Definierar det villkor som måste finnas för att denna wide View-definition ska användas.</span><span class="sxs-lookup"><span data-stu-id="afdf5-115">Defines the condition that must exist for this wide view definition to be used.</span></span>|
|[<span data-ttu-id="afdf5-116">SelectionSetName-element för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="afdf5-116">SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="afdf5-117">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="afdf5-117">Optional element.</span></span><br /><br /> <span data-ttu-id="afdf5-118">Anger en uppsättning av .NET-typer som använder denna wide View-definition.</span><span class="sxs-lookup"><span data-stu-id="afdf5-118">Specifies a set of .NET types that use this wide view definition.</span></span>|
|[<span data-ttu-id="afdf5-119">TypeName-element för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="afdf5-119">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="afdf5-120">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="afdf5-120">Optional element.</span></span><br /><br /> <span data-ttu-id="afdf5-121">Anger en .NET-typ som använder denna wide View-definition.</span><span class="sxs-lookup"><span data-stu-id="afdf5-121">Specifies a .NET type that uses this wide view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="afdf5-122">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="afdf5-122">Parent Elements</span></span>

|<span data-ttu-id="afdf5-123">Element</span><span class="sxs-lookup"><span data-stu-id="afdf5-123">Element</span></span>|<span data-ttu-id="afdf5-124">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="afdf5-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="afdf5-125">WideEntry-element (format)</span><span class="sxs-lookup"><span data-stu-id="afdf5-125">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="afdf5-126">Ger en definition av den breda vyn.</span><span class="sxs-lookup"><span data-stu-id="afdf5-126">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="afdf5-127">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="afdf5-127">Remarks</span></span>

<span data-ttu-id="afdf5-128">Du måste ange minst en typ, markerings uppsättning eller ett markerings villkor för en wide View-definition.</span><span class="sxs-lookup"><span data-stu-id="afdf5-128">You must specify at least one type, selection set, or selection condition for a wide view definition.</span></span> <span data-ttu-id="afdf5-129">Det finns ingen övre gräns för antalet underordnade element som du kan använda.</span><span class="sxs-lookup"><span data-stu-id="afdf5-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="afdf5-130">Urvals villkor används för att definiera ett villkor som måste finnas för att definitionen ska kunna användas, till exempel när ett objekt har en speciell egenskap eller ett angivet egenskaps värde eller skript värde utvärderas till `true` .</span><span class="sxs-lookup"><span data-stu-id="afdf5-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script value evaluates to `true`.</span></span> <span data-ttu-id="afdf5-131">Mer information om urvals villkor finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="afdf5-131">For more information about selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="afdf5-132">Mer information om andra komponenter i en bred vy finns i [skapa en bred vy](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="afdf5-132">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="afdf5-133">Se även</span><span class="sxs-lookup"><span data-stu-id="afdf5-133">See Also</span></span>

[<span data-ttu-id="afdf5-134">WideEntry-element (format)</span><span class="sxs-lookup"><span data-stu-id="afdf5-134">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="afdf5-135">SelectionCondition-element för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="afdf5-135">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="afdf5-136">SelectionSetName-element för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="afdf5-136">SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="afdf5-137">TypeName-element för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="afdf5-137">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="afdf5-138">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="afdf5-138">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="afdf5-139">Definiera villkor för datavisning</span><span class="sxs-lookup"><span data-stu-id="afdf5-139">Defining Conditions for Displaying Data</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="afdf5-140">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="afdf5-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
