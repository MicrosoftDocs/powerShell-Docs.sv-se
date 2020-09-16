---
title: EntrySelectedBy-element för CustomEntry for GroupBy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 75a0f42e7722b54791a873200a35c8fcbbd665b1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774141"
---
# <a name="entryselectedby-element-for-customentry-for-groupby-format"></a><span data-ttu-id="81339-102">EntrySelectedBy-element för CustomEntry för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="81339-102">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="81339-103">Definierar de .NET-typer som använder den här kontroll definitionen eller det villkor som måste finnas för att den här definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="81339-103">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="81339-104">Det här elementet används när du definierar hur en ny grupp av objekt visas.</span><span class="sxs-lookup"><span data-stu-id="81339-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="81339-105">Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for GroupBy (format) CustomEntry element for CustomControl for GroupBy (format) EntrySelectedBy-element för CustomEntry (format)</span><span class="sxs-lookup"><span data-stu-id="81339-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="81339-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="81339-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="81339-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="81339-107">Attributes and Elements</span></span>

<span data-ttu-id="81339-108">I följande avsnitt beskrivs attribut, underordnade element och `EntrySelectedBy` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="81339-108">The following sections describe attributes, child elements, and parent element of the `EntrySelectedBy` element.</span></span> <span data-ttu-id="81339-109">Du måste ange minst en typ, markerings uppsättning eller ett markerings villkor för en definition.</span><span class="sxs-lookup"><span data-stu-id="81339-109">You must specify at least one type, selection set, or selection condition for a definition.</span></span> <span data-ttu-id="81339-110">Det finns ingen övre gräns för antalet underordnade element som du kan använda.</span><span class="sxs-lookup"><span data-stu-id="81339-110">There is no maximum limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="81339-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="81339-111">Attributes</span></span>

<span data-ttu-id="81339-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="81339-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="81339-113">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="81339-113">Child Elements</span></span>

|<span data-ttu-id="81339-114">Element</span><span class="sxs-lookup"><span data-stu-id="81339-114">Element</span></span>|<span data-ttu-id="81339-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="81339-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="81339-116">SelectionCondition-element för EntrySelectedBy för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="81339-116">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="81339-117">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="81339-117">Optional element.</span></span><br /><br /> <span data-ttu-id="81339-118">Definierar det villkor som måste finnas för att den här definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="81339-118">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="81339-119">SelectionSetName-element för EntrySelectedBy för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="81339-119">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="81339-120">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="81339-120">Optional element.</span></span><br /><br /> <span data-ttu-id="81339-121">Anger en uppsättning av .NET-typer som använder den här definitionen av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="81339-121">Specifies a set of .NET types that use this definition of the control.</span></span>|
|[<span data-ttu-id="81339-122">TypeName-element för EntrySelectedBy för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="81339-122">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./typename-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="81339-123">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="81339-123">Optional element.</span></span><br /><br /> <span data-ttu-id="81339-124">Anger en .NET-typ som använder den här definitionen av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="81339-124">Specifies a .NET type that uses this definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="81339-125">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="81339-125">Parent Elements</span></span>

|<span data-ttu-id="81339-126">Element</span><span class="sxs-lookup"><span data-stu-id="81339-126">Element</span></span>|<span data-ttu-id="81339-127">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="81339-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="81339-128">CustomEntry-element för CustomControl för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="81339-128">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="81339-129">Ger en definition av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="81339-129">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="81339-130">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="81339-130">Remarks</span></span>

<span data-ttu-id="81339-131">Urvals villkor används för att definiera ett villkor som måste finnas för att definitionen ska kunna användas, till exempel när ett objekt har en speciell egenskap eller när ett angivet egenskaps värde eller skript utvärderas till `true` .</span><span class="sxs-lookup"><span data-stu-id="81339-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="81339-132">Mer information om urvals villkor finns i [definiera villkor för när en visnings post eller ett objekt används](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="81339-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="81339-133">Se även</span><span class="sxs-lookup"><span data-stu-id="81339-133">See Also</span></span>

[<span data-ttu-id="81339-134">SelectionCondition-element för EntrySelectedBy för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="81339-134">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="81339-135">SelectionSetName-element för EntrySelectedBy för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="81339-135">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="81339-136">TypeName-element för EntrySelectedBy för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="81339-136">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./typename-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="81339-137">CustomEntry-element för CustomEntries för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="81339-137">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="81339-138">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="81339-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
