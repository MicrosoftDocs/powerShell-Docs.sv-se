---
title: EntrySelectedBy-element för CustomEntry för kontroller för vy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b3d80a7d-3797-4c46-ae74-ae5cda79b24f
caps.latest.revision: 8
ms.openlocfilehash: efb20c3f2077547e6eb3cb28240512b444f9c481
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355148"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="54961-102">EntrySelectedBy-element för CustomEntry för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="54961-102">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="54961-103">Definierar de .NET-typer som använder den här kontroll definitionen eller det villkor som måste finnas för att den här definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="54961-103">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="54961-104">Det här elementet används när du definierar kontroller som kan användas av en vy.</span><span class="sxs-lookup"><span data-stu-id="54961-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="54961-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) styr element (format) styr element (format) styr element för Controls (format) CustomControl-element för kontroll för Control for View (format) CustomEntries-element för CustomControl for Controls for View (format) CustomEntry-elementet för CustomEntries for Controls for View (format) EntrySelectedBy element for CustomEntry for Controls for View (format)</span><span class="sxs-lookup"><span data-stu-id="54961-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="54961-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="54961-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="54961-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="54961-107">Attributes and Elements</span></span>

<span data-ttu-id="54961-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `EntrySelectedBy`-elementet.</span><span class="sxs-lookup"><span data-stu-id="54961-108">The following sections describe attributes, child elements, and parent element of the `EntrySelectedBy` element.</span></span> <span data-ttu-id="54961-109">Du måste ange minst en typ, markerings uppsättning eller ett markerings villkor för en definition.</span><span class="sxs-lookup"><span data-stu-id="54961-109">You must specify at least one type, selection set, or selection condition for a definition.</span></span> <span data-ttu-id="54961-110">Det finns ingen övre gräns för antalet underordnade element som du kan använda.</span><span class="sxs-lookup"><span data-stu-id="54961-110">There is no maximum limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="54961-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="54961-111">Attributes</span></span>

<span data-ttu-id="54961-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="54961-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="54961-113">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="54961-113">Child Elements</span></span>

|<span data-ttu-id="54961-114">Element</span><span class="sxs-lookup"><span data-stu-id="54961-114">Element</span></span>|<span data-ttu-id="54961-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="54961-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="54961-116">SelectionCondition-element för EntrySelectedBy för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="54961-116">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="54961-117">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="54961-117">Optional element.</span></span><br /><br /> <span data-ttu-id="54961-118">Definierar det villkor som måste finnas för att den här definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="54961-118">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="54961-119">SelectionSetName-element för EntrySelectedBy för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="54961-119">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="54961-120">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="54961-120">Optional element.</span></span><br /><br /> <span data-ttu-id="54961-121">Anger en uppsättning av .NET-typer som använder den här definitionen av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="54961-121">Specifies a set of .NET types that use this definition of the control.</span></span>|
|[<span data-ttu-id="54961-122">Elementet TypeName för EntrySelectedBy för kontroller för vyn (format)</span><span class="sxs-lookup"><span data-stu-id="54961-122">TypeName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./typename-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="54961-123">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="54961-123">Optional element.</span></span><br /><br /> <span data-ttu-id="54961-124">Anger en .NET-typ som använder den här definitionen av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="54961-124">Specifies a .NET type that uses this definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="54961-125">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="54961-125">Parent Elements</span></span>

|<span data-ttu-id="54961-126">Element</span><span class="sxs-lookup"><span data-stu-id="54961-126">Element</span></span>|<span data-ttu-id="54961-127">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="54961-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="54961-128">CustomEntry-element för CustomEntries för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="54961-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="54961-129">Ger en definition av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="54961-129">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="54961-130">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="54961-130">Remarks</span></span>

<span data-ttu-id="54961-131">Urvals villkor används för att definiera ett villkor som måste finnas för att definitionen ska kunna användas, till exempel när ett objekt har en speciell egenskap eller när ett angivet egenskaps värde eller skript utvärderar till `true`.</span><span class="sxs-lookup"><span data-stu-id="54961-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="54961-132">Mer information om urvals villkor finns i [definiera villkor för när en visnings post eller ett objekt används](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="54961-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="54961-133">Se även</span><span class="sxs-lookup"><span data-stu-id="54961-133">See Also</span></span>

[<span data-ttu-id="54961-134">CustomEntry-element för CustomEntries för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="54961-134">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="54961-135">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="54961-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
