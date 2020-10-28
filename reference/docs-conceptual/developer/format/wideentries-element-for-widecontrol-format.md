---
ms.date: 09/13/2016
ms.topic: reference
title: WideEntries-element för WideControl (format)
description: WideEntries-element för WideControl (format)
ms.openlocfilehash: 567b8acdd0d2e8d5daaef2c31b4fe4ce38c23a47
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92651238"
---
# <a name="wideentries-element-for-widecontrol-format"></a><span data-ttu-id="33bd6-103">WideEntries-element för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="33bd6-103">WideEntries Element for WideControl (Format)</span></span>

<span data-ttu-id="33bd6-104">Innehåller definitionerna för den breda vyn.</span><span class="sxs-lookup"><span data-stu-id="33bd6-104">Provides the definitions of the wide view.</span></span> <span data-ttu-id="33bd6-105">Wide View måste ange en eller flera definitioner.</span><span class="sxs-lookup"><span data-stu-id="33bd6-105">The wide view must specify one or more definitions.</span></span>

<span data-ttu-id="33bd6-106">Konfigurations element (format) ViewDefinitions element (format) View-element (format) WideControl-element (format) element för WideEntries (format)</span><span class="sxs-lookup"><span data-stu-id="33bd6-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="33bd6-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="33bd6-107">Syntax</span></span>

```xml
<WideEntries>
  <WideEntry>...</WideEntry>
</WideEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="33bd6-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="33bd6-108">Attributes and Elements</span></span>

<span data-ttu-id="33bd6-109">I följande avsnitt beskrivs attributen, underordnade element och `WideEntries` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="33bd6-109">The following sections describe the attributes, child elements, and parent element of the `WideEntries` element.</span></span> <span data-ttu-id="33bd6-110">Minst ett underordnat element måste anges.</span><span class="sxs-lookup"><span data-stu-id="33bd6-110">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="33bd6-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="33bd6-111">Attributes</span></span>

<span data-ttu-id="33bd6-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="33bd6-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="33bd6-113">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="33bd6-113">Child Elements</span></span>

|<span data-ttu-id="33bd6-114">Element</span><span class="sxs-lookup"><span data-stu-id="33bd6-114">Element</span></span>|<span data-ttu-id="33bd6-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33bd6-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="33bd6-116">WideEntry-element (format)</span><span class="sxs-lookup"><span data-stu-id="33bd6-116">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="33bd6-117">Ger en definition av den breda vyn.</span><span class="sxs-lookup"><span data-stu-id="33bd6-117">Provides a definition of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="33bd6-118">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="33bd6-118">Parent Elements</span></span>

|<span data-ttu-id="33bd6-119">Element</span><span class="sxs-lookup"><span data-stu-id="33bd6-119">Element</span></span>|<span data-ttu-id="33bd6-120">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33bd6-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="33bd6-121">WideControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="33bd6-121">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="33bd6-122">Definierar ett brett List format (enskilt värde) för vyn.</span><span class="sxs-lookup"><span data-stu-id="33bd6-122">Defines a wide (single value) list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="33bd6-123">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="33bd6-123">Remarks</span></span>

<span data-ttu-id="33bd6-124">En bred vy är ett List format som visar ett enda egenskaps värde eller skript värde för varje objekt.</span><span class="sxs-lookup"><span data-stu-id="33bd6-124">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="33bd6-125">Mer information om komponenterna i en bred vy finns i [wide View-komponenter](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="33bd6-125">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="33bd6-126">Exempel</span><span class="sxs-lookup"><span data-stu-id="33bd6-126">Example</span></span>

<span data-ttu-id="33bd6-127">I följande exempel visas ett `WideEntries` element som definierar ett enda `WideEntry` element.</span><span class="sxs-lookup"><span data-stu-id="33bd6-127">The following example shows a `WideEntries` element that defines a single `WideEntry` element.</span></span> <span data-ttu-id="33bd6-128">`WideEntry`Elementet innehåller ett enda `WideItem` element som definierar vilken egenskap eller vilket skript värde som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="33bd6-128">The `WideEntry` element contains a single `WideItem` element that defines what property or script value is displayed in the view.</span></span>

```xml
<WideControl>
  <WideEntries>
    <WideEntry>
      <WideItem>...</WideItem>
    <WideEntry>
  </WideEntries>
</WideControl>
```

<span data-ttu-id="33bd6-129">Ett fullständigt exempel på en bred vy finns i [wide View (grundläggande)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="33bd6-129">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="33bd6-130">Se även</span><span class="sxs-lookup"><span data-stu-id="33bd6-130">See Also</span></span>

[<span data-ttu-id="33bd6-131">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="33bd6-131">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="33bd6-132">WideControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="33bd6-132">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="33bd6-133">WideEntry-element (format)</span><span class="sxs-lookup"><span data-stu-id="33bd6-133">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="33bd6-134">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="33bd6-134">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
