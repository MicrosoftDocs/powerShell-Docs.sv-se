---
title: EntrySelectedBy-element för CustomEntry för kontroller för vy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 5c82e02d23b1694d05f7a32578ccc5d33686f13f
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774260"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="5311f-102">EntrySelectedBy-element för CustomEntry för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="5311f-102">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="5311f-103">Definierar de .NET-typer som använder den här kontroll definitionen eller det villkor som måste finnas för att den här definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="5311f-103">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="5311f-104">Det här elementet används när du definierar kontroller som kan användas av en vy.</span><span class="sxs-lookup"><span data-stu-id="5311f-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="5311f-105">Konfigurations element (format) ViewDefinitions element (format) visar element (format) styr element (format) styr element (format) styr element (format) kontroll element för Controls for View (format) CustomControl-elementet för Control for View (format) CustomEntries-element för CustomControl for Controls for View (format) CustomEntry-elementet for CustomEntries for Controls for View (format) EntrySelectedBy element for</span><span class="sxs-lookup"><span data-stu-id="5311f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5311f-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="5311f-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5311f-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="5311f-107">Attributes and Elements</span></span>

<span data-ttu-id="5311f-108">I följande avsnitt beskrivs attribut, underordnade element och `EntrySelectedBy` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="5311f-108">The following sections describe attributes, child elements, and parent element of the `EntrySelectedBy` element.</span></span> <span data-ttu-id="5311f-109">Du måste ange minst en typ, markerings uppsättning eller ett markerings villkor för en definition.</span><span class="sxs-lookup"><span data-stu-id="5311f-109">You must specify at least one type, selection set, or selection condition for a definition.</span></span> <span data-ttu-id="5311f-110">Det finns ingen övre gräns för antalet underordnade element som du kan använda.</span><span class="sxs-lookup"><span data-stu-id="5311f-110">There is no maximum limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="5311f-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="5311f-111">Attributes</span></span>

<span data-ttu-id="5311f-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="5311f-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5311f-113">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="5311f-113">Child Elements</span></span>

|<span data-ttu-id="5311f-114">Element</span><span class="sxs-lookup"><span data-stu-id="5311f-114">Element</span></span>|<span data-ttu-id="5311f-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5311f-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5311f-116">SelectionCondition-element för EntrySelectedBy för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="5311f-116">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="5311f-117">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="5311f-117">Optional element.</span></span><br /><br /> <span data-ttu-id="5311f-118">Definierar det villkor som måste finnas för att den här definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="5311f-118">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="5311f-119">SelectionSetName-element för EntrySelectedBy för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="5311f-119">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="5311f-120">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="5311f-120">Optional element.</span></span><br /><br /> <span data-ttu-id="5311f-121">Anger en uppsättning av .NET-typer som använder den här definitionen av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="5311f-121">Specifies a set of .NET types that use this definition of the control.</span></span>|
|[<span data-ttu-id="5311f-122">TypeName-element för EntrySelectedBy för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="5311f-122">TypeName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./typename-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="5311f-123">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="5311f-123">Optional element.</span></span><br /><br /> <span data-ttu-id="5311f-124">Anger en .NET-typ som använder den här definitionen av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="5311f-124">Specifies a .NET type that uses this definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5311f-125">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="5311f-125">Parent Elements</span></span>

|<span data-ttu-id="5311f-126">Element</span><span class="sxs-lookup"><span data-stu-id="5311f-126">Element</span></span>|<span data-ttu-id="5311f-127">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5311f-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5311f-128">CustomEntry-element för CustomEntries för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="5311f-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="5311f-129">Ger en definition av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="5311f-129">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5311f-130">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="5311f-130">Remarks</span></span>

<span data-ttu-id="5311f-131">Urvals villkor används för att definiera ett villkor som måste finnas för att definitionen ska kunna användas, till exempel när ett objekt har en speciell egenskap eller när ett angivet egenskaps värde eller skript utvärderas till `true` .</span><span class="sxs-lookup"><span data-stu-id="5311f-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="5311f-132">Mer information om urvals villkor finns i [definiera villkor för när en visnings post eller ett objekt används](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="5311f-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5311f-133">Se även</span><span class="sxs-lookup"><span data-stu-id="5311f-133">See Also</span></span>

[<span data-ttu-id="5311f-134">CustomEntry-element för CustomEntries för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="5311f-134">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="5311f-135">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="5311f-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
