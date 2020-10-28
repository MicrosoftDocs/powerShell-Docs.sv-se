---
ms.date: 09/13/2016
ms.topic: reference
title: TypeName-element för SelectionCondition för EntrySelectedBy för WideControl (format)
description: TypeName-element för SelectionCondition för EntrySelectedBy för WideControl (format)
ms.openlocfilehash: af6e4782c345b43e16bce59c333bdaaceba0d845
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92645502"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="5640a-103">TypeName-element för SelectionCondition för EntrySelectedBy för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="5640a-103">TypeName Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="5640a-104">Anger en .NET-typ som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="5640a-104">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="5640a-105">När den här typen finns används definitionen.</span><span class="sxs-lookup"><span data-stu-id="5640a-105">When this type is present, the definition is used.</span></span>

<span data-ttu-id="5640a-106">Konfigurations element (format) ViewDefinitions element (format) View-element (format) WideControl-element (format) WideEntries-element (format) WideEntry-element (format) EntrySelectedBy-element för WideEntry (format) SelectionCondition-element för EntrySelectedBy för WideEntry (format) element för SelectionCondition (format)</span><span class="sxs-lookup"><span data-stu-id="5640a-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5640a-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="5640a-107">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5640a-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="5640a-108">Attributes and Elements</span></span>

<span data-ttu-id="5640a-109">I följande avsnitt beskrivs attribut, underordnade element och `TypeName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="5640a-109">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5640a-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="5640a-110">Attributes</span></span>

<span data-ttu-id="5640a-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="5640a-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5640a-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="5640a-112">Child Elements</span></span>

<span data-ttu-id="5640a-113">Inga.</span><span class="sxs-lookup"><span data-stu-id="5640a-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5640a-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="5640a-114">Parent Elements</span></span>

|<span data-ttu-id="5640a-115">Element</span><span class="sxs-lookup"><span data-stu-id="5640a-115">Element</span></span>|<span data-ttu-id="5640a-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5640a-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5640a-117">SelectionCondition-element för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="5640a-117">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="5640a-118">Definierar det villkor som måste finnas för att den här breda posten ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="5640a-118">Defines the condition that must exist for this wide entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5640a-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="5640a-119">Text Value</span></span>

<span data-ttu-id="5640a-120">Ange det fullständigt kvalificerade namnet för .NET-typen, t `System.IO.DirectoryInfo` . ex..</span><span class="sxs-lookup"><span data-stu-id="5640a-120">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="5640a-121">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="5640a-121">Remarks</span></span>

<span data-ttu-id="5640a-122">Urvals villkoret kan ange en .NET-typ eller en urvals uppsättning, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="5640a-122">The selection condition can specify a .NET type or a selection set, but cannot specify both.</span></span> <span data-ttu-id="5640a-123">Mer information om hur du använder urvals villkor finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="5640a-123">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="5640a-124">Mer information om andra komponenter i en bred vy finns i [skapa en bred vy](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="5640a-124">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5640a-125">Se även</span><span class="sxs-lookup"><span data-stu-id="5640a-125">See Also</span></span>

[<span data-ttu-id="5640a-126">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="5640a-126">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="5640a-127">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="5640a-127">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="5640a-128">SelectionCondition-element för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="5640a-128">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="5640a-129">SelectionSetName-element för SelectionCondition för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="5640a-129">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="5640a-130">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="5640a-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
