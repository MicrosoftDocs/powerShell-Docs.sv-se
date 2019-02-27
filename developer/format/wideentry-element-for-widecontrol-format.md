---
title: WideEntry Element för WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 014763cb-7716-4931-899c-8375b5d7a3dd
caps.latest.revision: 15
ms.openlocfilehash: d1d13b5c3436871053353814293d9163ea13c7fb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847182"
---
# <a name="wideentry-element-for-widecontrol-format"></a><span data-ttu-id="0d131-102">WideEntry-element för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="0d131-102">WideEntry Element for WideControl (Format)</span></span>

<span data-ttu-id="0d131-103">Innehåller en definition av bred vy.</span><span class="sxs-lookup"><span data-stu-id="0d131-103">Provides a definition of the wide view.</span></span>

<span data-ttu-id="0d131-104">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry konfigurationselement (Format)</span><span class="sxs-lookup"><span data-stu-id="0d131-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0d131-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="0d131-105">Syntax</span></span>

```xml
<WideEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <WideItem>...</WideItem>
</WideEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0d131-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="0d131-106">Attributes and Elements</span></span>

<span data-ttu-id="0d131-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `WideEntry` element.</span><span class="sxs-lookup"><span data-stu-id="0d131-107">The following sections describe the attributes, child elements, and the parent element of the `WideEntry` element.</span></span> <span data-ttu-id="0d131-108">Du måste ange en enda `WideItem` underordnat element.</span><span class="sxs-lookup"><span data-stu-id="0d131-108">You must specify a single `WideItem` child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0d131-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="0d131-109">Attributes</span></span>

<span data-ttu-id="0d131-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="0d131-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0d131-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="0d131-111">Child Elements</span></span>

|<span data-ttu-id="0d131-112">Element</span><span class="sxs-lookup"><span data-stu-id="0d131-112">Element</span></span>|<span data-ttu-id="0d131-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0d131-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0d131-114">EntrySelectedBy Element för WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="0d131-114">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="0d131-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="0d131-115">Optional element.</span></span><br /><br /> <span data-ttu-id="0d131-116">Definierar vilka typer av .NET som använder den här definitionen för bred posten eller villkor som måste finnas för den här definitionen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="0d131-116">Defines the .NET types that use this wide entry definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="0d131-117">WideItem Element (Format)</span><span class="sxs-lookup"><span data-stu-id="0d131-117">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="0d131-118">Element som krävs.</span><span class="sxs-lookup"><span data-stu-id="0d131-118">Required element.</span></span><br /><br /> <span data-ttu-id="0d131-119">Definierar egenskapen eller skript som vars värde visas.</span><span class="sxs-lookup"><span data-stu-id="0d131-119">Defines the property or script whose value is displayed.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0d131-120">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="0d131-120">Parent Elements</span></span>

|<span data-ttu-id="0d131-121">Element</span><span class="sxs-lookup"><span data-stu-id="0d131-121">Element</span></span>|<span data-ttu-id="0d131-122">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0d131-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0d131-123">WideEntries Element (Format)</span><span class="sxs-lookup"><span data-stu-id="0d131-123">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)|<span data-ttu-id="0d131-124">Innehåller definitioner av bred vy.</span><span class="sxs-lookup"><span data-stu-id="0d131-124">Provides the definitions of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0d131-125">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="0d131-125">Remarks</span></span>

<span data-ttu-id="0d131-126">En bred vy är ett listformat som visar en enda egenskapsvärdet eller skriptvärde för varje objekt.</span><span class="sxs-lookup"><span data-stu-id="0d131-126">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="0d131-127">Till skillnad från andra typer av vyer kan ange du endast ett angivet objekt-element för varje vydefinitionen.</span><span class="sxs-lookup"><span data-stu-id="0d131-127">Unlike other types of views, you can specify only one item element for each view definition.</span></span> <span data-ttu-id="0d131-128">Mer information om de andra komponenterna för en bred vy finns i [skapar en bred vy](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="0d131-128">For more information about the other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="0d131-129">Exempel</span><span class="sxs-lookup"><span data-stu-id="0d131-129">Example</span></span>

<span data-ttu-id="0d131-130">I följande exempel visas en `WideEntry` -element som definierar en enda `WideItem` element.</span><span class="sxs-lookup"><span data-stu-id="0d131-130">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="0d131-131">Den `WideItem` elementet definierar egenskapen vars värde visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="0d131-131">The `WideItem` element defines the property whose value is displayed in the view.</span></span>

```xml
<WideEntries>
  <WideEntry>
    <WideItem>
      <PropertyName>ProcessName</PropertyName>
    </WideItem>
  </WideEntry>
</WideEntries>

```

<span data-ttu-id="0d131-132">Exempel på en bred vy, se [bred vy (grundläggande)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="0d131-132">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0d131-133">Se även</span><span class="sxs-lookup"><span data-stu-id="0d131-133">See Also</span></span>

[<span data-ttu-id="0d131-134">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="0d131-134">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="0d131-135">SelectionCondition Element för WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="0d131-135">SelectionCondition Element for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="0d131-136">SelectionSetName Element för WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="0d131-136">SelectionSetName Element for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="0d131-137">TypeName-Element för WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="0d131-137">TypeName Element for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="0d131-138">WideEntries Element (Format)</span><span class="sxs-lookup"><span data-stu-id="0d131-138">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)

[<span data-ttu-id="0d131-139">WideItem Element (Format)</span><span class="sxs-lookup"><span data-stu-id="0d131-139">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="0d131-140">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="0d131-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
