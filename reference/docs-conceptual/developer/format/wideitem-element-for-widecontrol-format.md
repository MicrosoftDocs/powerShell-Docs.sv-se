---
ms.date: 09/13/2016
ms.topic: reference
title: WideItem-element för WideControl (format)
description: WideItem-element för WideControl (format)
ms.openlocfilehash: b9c416bbe3befcd689b8a2c0b72a8ff1301b9659
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92647799"
---
# <a name="wideitem-element-for-widecontrol-format"></a><span data-ttu-id="b4f44-103">WideItem-element för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="b4f44-103">WideItem Element for WideControl (Format)</span></span>

<span data-ttu-id="b4f44-104">Definierar egenskapen eller skriptet vars värde visas.</span><span class="sxs-lookup"><span data-stu-id="b4f44-104">Defines the property or script whose value is displayed.</span></span>

<span data-ttu-id="b4f44-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) WideControl-element (format) WideEntries-element (format) WideEntry-element (format) WideItem-element (format)</span><span class="sxs-lookup"><span data-stu-id="b4f44-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b4f44-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="b4f44-106">Syntax</span></span>

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b4f44-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="b4f44-107">Attributes and Elements</span></span>

<span data-ttu-id="b4f44-108">I följande avsnitt beskrivs attributen, underordnade element och `WideItem` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="b4f44-108">The following sections describe the attributes, child elements, and the parent element of the `WideItem` element.</span></span> <span data-ttu-id="b4f44-109">`FormatString`Elementet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="b4f44-109">The `FormatString` element is optional.</span></span> <span data-ttu-id="b4f44-110">Du måste dock ange ett `PropertyName` eller `ScriptBlock` -element, men du kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="b4f44-110">However, you must specify a `PropertyName` or `ScriptBlock` element, but you cannot specify both.</span></span>

### <a name="attributes"></a><span data-ttu-id="b4f44-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="b4f44-111">Attributes</span></span>

<span data-ttu-id="b4f44-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="b4f44-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b4f44-113">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="b4f44-113">Child Elements</span></span>

|<span data-ttu-id="b4f44-114">Element</span><span class="sxs-lookup"><span data-stu-id="b4f44-114">Element</span></span>|<span data-ttu-id="b4f44-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b4f44-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b4f44-116">FormatString-element för WideItem för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="b4f44-116">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="b4f44-117">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="b4f44-117">Optional element.</span></span><br /><br /> <span data-ttu-id="b4f44-118">Anger ett format mönster som definierar hur egenskapen eller skriptets värde visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="b4f44-118">Specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>|
|[<span data-ttu-id="b4f44-119">PropertyName-element för WideItem (format)</span><span class="sxs-lookup"><span data-stu-id="b4f44-119">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="b4f44-120">Anger egenskapen för det objekt vars värde visas i den bred vyn.</span><span class="sxs-lookup"><span data-stu-id="b4f44-120">Specifies the property of the object whose value is displayed in the wide view.</span></span>|
|[<span data-ttu-id="b4f44-121">Script block-element för WideItem (format)</span><span class="sxs-lookup"><span data-stu-id="b4f44-121">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="b4f44-122">Anger det skript vars värde visas i den breda vyn.</span><span class="sxs-lookup"><span data-stu-id="b4f44-122">Specifies the script whose value is displayed in the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b4f44-123">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="b4f44-123">Parent Elements</span></span>

|<span data-ttu-id="b4f44-124">Element</span><span class="sxs-lookup"><span data-stu-id="b4f44-124">Element</span></span>|<span data-ttu-id="b4f44-125">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b4f44-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b4f44-126">WideEntry-element (format)</span><span class="sxs-lookup"><span data-stu-id="b4f44-126">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="b4f44-127">Ger en definition av den breda vyn.</span><span class="sxs-lookup"><span data-stu-id="b4f44-127">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b4f44-128">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="b4f44-128">Remarks</span></span>

<span data-ttu-id="b4f44-129">Mer information om komponenterna i en bred vy finns i [wide View](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="b4f44-129">For more information about the components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="b4f44-130">Exempel</span><span class="sxs-lookup"><span data-stu-id="b4f44-130">Example</span></span>

<span data-ttu-id="b4f44-131">I följande exempel visas ett `WideEntry` element som definierar ett enda `WideItem` element.</span><span class="sxs-lookup"><span data-stu-id="b4f44-131">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="b4f44-132">`WideItem`Elementet definierar egenskapen eller skriptet vars värde visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="b4f44-132">The `WideItem` element defines the property or script whose value is displayed in the view.</span></span>

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

<span data-ttu-id="b4f44-133">Ett fullständigt exempel på en bred vy finns i [wide View (grundläggande)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="b4f44-133">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b4f44-134">Se även</span><span class="sxs-lookup"><span data-stu-id="b4f44-134">See Also</span></span>

[<span data-ttu-id="b4f44-135">FormatString-element för WideItem för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="b4f44-135">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="b4f44-136">PropertyName-element för WideItem (format)</span><span class="sxs-lookup"><span data-stu-id="b4f44-136">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="b4f44-137">Script block-element för WideItem (format)</span><span class="sxs-lookup"><span data-stu-id="b4f44-137">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="b4f44-138">WideEntry-element (format)</span><span class="sxs-lookup"><span data-stu-id="b4f44-138">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="b4f44-139">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="b4f44-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
