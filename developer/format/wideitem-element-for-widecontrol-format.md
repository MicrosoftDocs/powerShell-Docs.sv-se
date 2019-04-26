---
title: WideItem Element för WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17352fc4-ba83-4f04-86bc-f591765d85a8
caps.latest.revision: 18
ms.openlocfilehash: fa9eda3ea1028c27dbfb3eb04747af3b817c1a81
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083645"
---
# <a name="wideitem-element-for-widecontrol-format"></a><span data-ttu-id="792e1-102">WideItem-element för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="792e1-102">WideItem Element for WideControl (Format)</span></span>

<span data-ttu-id="792e1-103">Definierar egenskapen eller skript som vars värde visas.</span><span class="sxs-lookup"><span data-stu-id="792e1-103">Defines the property or script whose value is displayed.</span></span>

<span data-ttu-id="792e1-104">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem konfigurationselement (Format)</span><span class="sxs-lookup"><span data-stu-id="792e1-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="792e1-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="792e1-105">Syntax</span></span>

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="792e1-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="792e1-106">Attributes and Elements</span></span>

<span data-ttu-id="792e1-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `WideItem` element.</span><span class="sxs-lookup"><span data-stu-id="792e1-107">The following sections describe the attributes, child elements, and the parent element of the `WideItem` element.</span></span> <span data-ttu-id="792e1-108">Den `FormatString` element är valfria.</span><span class="sxs-lookup"><span data-stu-id="792e1-108">The `FormatString` element is optional.</span></span> <span data-ttu-id="792e1-109">Du måste dock ange en `PropertyName` eller `ScriptBlock` element, men du kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="792e1-109">However, you must specify a `PropertyName` or `ScriptBlock` element, but you cannot specify both.</span></span>

### <a name="attributes"></a><span data-ttu-id="792e1-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="792e1-110">Attributes</span></span>

<span data-ttu-id="792e1-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="792e1-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="792e1-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="792e1-112">Child Elements</span></span>

|<span data-ttu-id="792e1-113">Element</span><span class="sxs-lookup"><span data-stu-id="792e1-113">Element</span></span>|<span data-ttu-id="792e1-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="792e1-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="792e1-115">FormatString-Element för WideItem för WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="792e1-115">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="792e1-116">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="792e1-116">Optional element.</span></span><br /><br /> <span data-ttu-id="792e1-117">Anger ett formatmönster som definierar hur värdet för egenskapen eller skript visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="792e1-117">Specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>|
|[<span data-ttu-id="792e1-118">PropertyName-Element för WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="792e1-118">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="792e1-119">Anger egenskapen för objektet vars värde visas i bred vy.</span><span class="sxs-lookup"><span data-stu-id="792e1-119">Specifies the property of the object whose value is displayed in the wide view.</span></span>|
|[<span data-ttu-id="792e1-120">ScriptBlock Element för WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="792e1-120">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="792e1-121">Anger skriptet vars värde visas i bred vy.</span><span class="sxs-lookup"><span data-stu-id="792e1-121">Specifies the script whose value is displayed in the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="792e1-122">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="792e1-122">Parent Elements</span></span>

|<span data-ttu-id="792e1-123">Element</span><span class="sxs-lookup"><span data-stu-id="792e1-123">Element</span></span>|<span data-ttu-id="792e1-124">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="792e1-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="792e1-125">WideEntry Element (Format)</span><span class="sxs-lookup"><span data-stu-id="792e1-125">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="792e1-126">Innehåller en definition av bred vy.</span><span class="sxs-lookup"><span data-stu-id="792e1-126">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="792e1-127">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="792e1-127">Remarks</span></span>

<span data-ttu-id="792e1-128">Mer information om komponenter för en bred vy finns i [bred vy](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="792e1-128">For more information about the components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="792e1-129">Exempel</span><span class="sxs-lookup"><span data-stu-id="792e1-129">Example</span></span>

<span data-ttu-id="792e1-130">I följande exempel visas en `WideEntry` -element som definierar en enda `WideItem` element.</span><span class="sxs-lookup"><span data-stu-id="792e1-130">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="792e1-131">Den `WideItem` elementet definierar egenskapen eller skript som vars värde visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="792e1-131">The `WideItem` element defines the property or script whose value is displayed in the view.</span></span>

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

<span data-ttu-id="792e1-132">Exempel på en bred vy, se [bred vy (grundläggande)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="792e1-132">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="792e1-133">Se även</span><span class="sxs-lookup"><span data-stu-id="792e1-133">See Also</span></span>

[<span data-ttu-id="792e1-134">FormatString-Element för WideItem för WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="792e1-134">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="792e1-135">PropertyName-Element för WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="792e1-135">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="792e1-136">ScriptBlock Element för WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="792e1-136">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="792e1-137">WideEntry Element (Format)</span><span class="sxs-lookup"><span data-stu-id="792e1-137">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="792e1-138">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="792e1-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
