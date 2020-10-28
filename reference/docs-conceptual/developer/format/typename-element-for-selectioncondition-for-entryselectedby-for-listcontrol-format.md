---
ms.date: 09/13/2016
ms.topic: reference
title: TypeName-element för SelectionCondition för EntrySelectedBy för ListControl (format)
description: TypeName-element för SelectionCondition för EntrySelectedBy för ListControl (format)
ms.openlocfilehash: 2e8246e3ef2cba38824d8f8004acfffc3236df13
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92645555"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="da253-103">TypeName-element för SelectionCondition för EntrySelectedBy för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="da253-103">TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="da253-104">Anger en .NET-typ som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="da253-104">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="da253-105">När den här typen finns används List posten.</span><span class="sxs-lookup"><span data-stu-id="da253-105">When this type is present, the list entry is used.</span></span>

<span data-ttu-id="da253-106">Konfigurations element (format) ViewDefinitions element (format) View-element (format) ListControl-element (format) ListEntries-element för ListControl (format) ListEntry-element för ListEntries för ListControl (format) EntrySelectedBy-element för ListEntry för ListControl (format) SelectionCondition-element för EntrySelectedBy (format) ListControl-element för SelectionCondition för EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="da253-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) EntrySelectedBy Element for ListEntry for ListControl (Format) SelectionCondition Element for EntrySelectedBy for ListControl (Format) TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="da253-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="da253-107">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="da253-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="da253-108">Attributes and Elements</span></span>

<span data-ttu-id="da253-109">I följande avsnitt beskrivs attribut, underordnade element och `TypeName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="da253-109">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="da253-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="da253-110">Attributes</span></span>

<span data-ttu-id="da253-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="da253-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="da253-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="da253-112">Child Elements</span></span>

<span data-ttu-id="da253-113">Inga.</span><span class="sxs-lookup"><span data-stu-id="da253-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="da253-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="da253-114">Parent Elements</span></span>

|<span data-ttu-id="da253-115">Element</span><span class="sxs-lookup"><span data-stu-id="da253-115">Element</span></span>|<span data-ttu-id="da253-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="da253-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="da253-117">SelectionCondition-element för EntrySelectedBy för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="da253-117">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="da253-118">Definierar det villkor som måste finnas för att den här List posten ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="da253-118">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="da253-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="da253-119">Text Value</span></span>

<span data-ttu-id="da253-120">Ange det fullständigt kvalificerade namnet för .NET-typen, t `System.IO.DirectoryInfo` . ex..</span><span class="sxs-lookup"><span data-stu-id="da253-120">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="da253-121">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="da253-121">Remarks</span></span>

<span data-ttu-id="da253-122">Urvals villkoret kan ange valfritt antal .NET-typer eller markerings uppsättningar, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="da253-122">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span> <span data-ttu-id="da253-123">Mer information om hur du använder urvals villkor finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="da253-123">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="da253-124">Mer information om andra komponenter i en listvy finns i [skapa en listvy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="da253-124">For more information about other the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="da253-125">Se även</span><span class="sxs-lookup"><span data-stu-id="da253-125">See Also</span></span>

[<span data-ttu-id="da253-126">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="da253-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="da253-127">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="da253-127">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="da253-128">SelectionCondition-element för EntrySelectedBy för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="da253-128">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="da253-129">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="da253-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
