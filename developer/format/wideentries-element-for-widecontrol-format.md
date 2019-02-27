---
title: WideEntries Element för WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c4bff45-0960-4b3a-95e7-47f2cee03ac5
caps.latest.revision: 12
ms.openlocfilehash: 083f3c8df8136858e32778ed231943ef983e47aa
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56844907"
---
# <a name="wideentries-element-for-widecontrol-format"></a><span data-ttu-id="b9106-102">WideEntries-element för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="b9106-102">WideEntries Element for WideControl (Format)</span></span>

<span data-ttu-id="b9106-103">Innehåller definitioner av bred vy.</span><span class="sxs-lookup"><span data-stu-id="b9106-103">Provides the definitions of the wide view.</span></span> <span data-ttu-id="b9106-104">Bred vy måste ange en eller flera definitioner.</span><span class="sxs-lookup"><span data-stu-id="b9106-104">The wide view must specify one or more definitions.</span></span>

<span data-ttu-id="b9106-105">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) WideControl Element (Format) WideEntries konfigurationselement (Format)</span><span class="sxs-lookup"><span data-stu-id="b9106-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b9106-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="b9106-106">Syntax</span></span>

```xml
<WideEntries>
  <WideEntry>...</WideEntry>
</WideEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="b9106-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="b9106-107">Attributes and Elements</span></span>

<span data-ttu-id="b9106-108">I följande avsnitt beskrivs de attribut och underordnade element överordnade elementet i den `WideEntries` element.</span><span class="sxs-lookup"><span data-stu-id="b9106-108">The following sections describe the attributes, child elements, and parent element of the `WideEntries` element.</span></span> <span data-ttu-id="b9106-109">Du måste ange minst ett underordnat element.</span><span class="sxs-lookup"><span data-stu-id="b9106-109">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="b9106-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="b9106-110">Attributes</span></span>

<span data-ttu-id="b9106-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="b9106-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b9106-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="b9106-112">Child Elements</span></span>

|<span data-ttu-id="b9106-113">Element</span><span class="sxs-lookup"><span data-stu-id="b9106-113">Element</span></span>|<span data-ttu-id="b9106-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b9106-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b9106-115">WideEntry Element (Format)</span><span class="sxs-lookup"><span data-stu-id="b9106-115">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="b9106-116">Innehåller en definition av bred vy.</span><span class="sxs-lookup"><span data-stu-id="b9106-116">Provides a definition of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b9106-117">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="b9106-117">Parent Elements</span></span>

|<span data-ttu-id="b9106-118">Element</span><span class="sxs-lookup"><span data-stu-id="b9106-118">Element</span></span>|<span data-ttu-id="b9106-119">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b9106-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b9106-120">WideControl Element (Format)</span><span class="sxs-lookup"><span data-stu-id="b9106-120">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="b9106-121">Definierar en bred (enstaka värde) listformat för vyn.</span><span class="sxs-lookup"><span data-stu-id="b9106-121">Defines a wide (single value) list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b9106-122">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="b9106-122">Remarks</span></span>

<span data-ttu-id="b9106-123">En bred vy är ett listformat som visar en enda egenskapsvärdet eller skriptvärde för varje objekt.</span><span class="sxs-lookup"><span data-stu-id="b9106-123">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="b9106-124">Mer information om komponenter för en bred vy finns i [bred vy komponenter](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="b9106-124">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="b9106-125">Exempel</span><span class="sxs-lookup"><span data-stu-id="b9106-125">Example</span></span>

<span data-ttu-id="b9106-126">I följande exempel visas en `WideEntries` -element som definierar en enda `WideEntry` element.</span><span class="sxs-lookup"><span data-stu-id="b9106-126">The following example shows a `WideEntries` element that defines a single `WideEntry` element.</span></span> <span data-ttu-id="b9106-127">Den `WideEntry` elementet innehåller en enda `WideItem` element som definierar vilket värde som egenskapen eller skript visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="b9106-127">The `WideEntry` element contains a single `WideItem` element that defines what property or script value is displayed in the view.</span></span>

```xml
<WideControl>
  <WideEntries>
    <WideEntry>
      <WideItem>...</WideItem>
    <WideEntry>
  </WideEntries>
</WideControl>
```

<span data-ttu-id="b9106-128">Exempel på en bred vy, se [bred vy (grundläggande)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="b9106-128">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b9106-129">Se även</span><span class="sxs-lookup"><span data-stu-id="b9106-129">See Also</span></span>

[<span data-ttu-id="b9106-130">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="b9106-130">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="b9106-131">WideControl Element (Format)</span><span class="sxs-lookup"><span data-stu-id="b9106-131">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="b9106-132">WideEntry Element (Format)</span><span class="sxs-lookup"><span data-stu-id="b9106-132">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="b9106-133">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="b9106-133">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
