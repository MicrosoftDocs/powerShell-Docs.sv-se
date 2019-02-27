---
title: EntrySelectedBy Element för CustomEntry för kontroller för att visa (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b3d80a7d-3797-4c46-ae74-ae5cda79b24f
caps.latest.revision: 8
ms.openlocfilehash: efb20c3f2077547e6eb3cb28240512b444f9c481
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849289"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="20f73-102">EntrySelectedBy-element för CustomEntry för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="20f73-102">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="20f73-103">Definierar vilka typer av .NET som använder den här kontrollen definitionen eller villkor som måste finnas för den här definitionen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="20f73-103">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="20f73-104">Det här elementet används när du definierar kontroller som kan användas av en vy.</span><span class="sxs-lookup"><span data-stu-id="20f73-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="20f73-105">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) kontroller Element (Format) kontroll konfigurationselement för kontroller för att visa (Format) anpassad kontroll Element för kontroll för kontroller för att visa (Format) CustomEntries Element för Anpassad kontroll för kontroller för att visa (Format) CustomEntry Element för CustomEntries för kontroller för att visa (Format) EntrySelectedBy Element för CustomEntry för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="20f73-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="20f73-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="20f73-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="20f73-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="20f73-107">Attributes and Elements</span></span>

<span data-ttu-id="20f73-108">I följande avsnitt beskrivs attribut, underordnade element och överordnade elementet i den `EntrySelectedBy` element.</span><span class="sxs-lookup"><span data-stu-id="20f73-108">The following sections describe attributes, child elements, and parent element of the `EntrySelectedBy` element.</span></span> <span data-ttu-id="20f73-109">Du måste ange minst en typ, val av set eller urvalsvillkoret definieras.</span><span class="sxs-lookup"><span data-stu-id="20f73-109">You must specify at least one type, selection set, or selection condition for a definition.</span></span> <span data-ttu-id="20f73-110">Det finns ingen högsta gräns för antalet underordnade element som du kan använda.</span><span class="sxs-lookup"><span data-stu-id="20f73-110">There is no maximum limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="20f73-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="20f73-111">Attributes</span></span>

<span data-ttu-id="20f73-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="20f73-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="20f73-113">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="20f73-113">Child Elements</span></span>

|<span data-ttu-id="20f73-114">Element</span><span class="sxs-lookup"><span data-stu-id="20f73-114">Element</span></span>|<span data-ttu-id="20f73-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="20f73-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="20f73-116">SelectionCondition Element för EntrySelectedBy för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="20f73-116">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="20f73-117">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="20f73-117">Optional element.</span></span><br /><br /> <span data-ttu-id="20f73-118">Definierar de villkor som måste finnas för den här definitionen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="20f73-118">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="20f73-119">SelectionSetName Element för EntrySelectedBy för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="20f73-119">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="20f73-120">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="20f73-120">Optional element.</span></span><br /><br /> <span data-ttu-id="20f73-121">Anger en uppsättning med .NET-typer som använder den här definitionen för kontrollen.</span><span class="sxs-lookup"><span data-stu-id="20f73-121">Specifies a set of .NET types that use this definition of the control.</span></span>|
|[<span data-ttu-id="20f73-122">TypeName-Element för EntrySelectedBy för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="20f73-122">TypeName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./typename-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="20f73-123">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="20f73-123">Optional element.</span></span><br /><br /> <span data-ttu-id="20f73-124">Anger ett .NET-typ som använder den här definitionen för kontrollen.</span><span class="sxs-lookup"><span data-stu-id="20f73-124">Specifies a .NET type that uses this definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="20f73-125">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="20f73-125">Parent Elements</span></span>

|<span data-ttu-id="20f73-126">Element</span><span class="sxs-lookup"><span data-stu-id="20f73-126">Element</span></span>|<span data-ttu-id="20f73-127">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="20f73-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="20f73-128">CustomEntry Element för CustomEntries för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="20f73-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="20f73-129">Innehåller en definition av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="20f73-129">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="20f73-130">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="20f73-130">Remarks</span></span>

<span data-ttu-id="20f73-131">Val av villkor används för att definiera ett villkor som måste finnas för definitionen som ska användas, till exempel när ett objekt har en specifik egenskap eller när en specifik egenskapsvärdet eller skript som utvärderas till `true`.</span><span class="sxs-lookup"><span data-stu-id="20f73-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="20f73-132">Mer information om val av villkor finns i [definiera villkor för när en post i vyn eller objektet används](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="20f73-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="20f73-133">Se även</span><span class="sxs-lookup"><span data-stu-id="20f73-133">See Also</span></span>

[<span data-ttu-id="20f73-134">CustomEntry Element för CustomEntries för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="20f73-134">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="20f73-135">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="20f73-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
