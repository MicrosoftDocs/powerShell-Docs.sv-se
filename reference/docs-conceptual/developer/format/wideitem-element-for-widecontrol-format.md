---
title: WideItem-element för WideControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17352fc4-ba83-4f04-86bc-f591765d85a8
caps.latest.revision: 18
ms.openlocfilehash: fa9eda3ea1028c27dbfb3eb04747af3b817c1a81
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353405"
---
# <a name="wideitem-element-for-widecontrol-format"></a><span data-ttu-id="ac007-102">WideItem-element för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="ac007-102">WideItem Element for WideControl (Format)</span></span>

<span data-ttu-id="ac007-103">Definierar egenskapen eller skriptet vars värde visas.</span><span class="sxs-lookup"><span data-stu-id="ac007-103">Defines the property or script whose value is displayed.</span></span>

<span data-ttu-id="ac007-104">Konfigurations element (format) ViewDefinitions element (format) View-element (format) WideControl-element (format) WideEntries-element (format) WideEntry-element (format) WideItem-element (format)</span><span class="sxs-lookup"><span data-stu-id="ac007-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ac007-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="ac007-105">Syntax</span></span>

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ac007-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="ac007-106">Attributes and Elements</span></span>

<span data-ttu-id="ac007-107">I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet för elementet `WideItem`.</span><span class="sxs-lookup"><span data-stu-id="ac007-107">The following sections describe the attributes, child elements, and the parent element of the `WideItem` element.</span></span> <span data-ttu-id="ac007-108">Elementet `FormatString` är valfritt.</span><span class="sxs-lookup"><span data-stu-id="ac007-108">The `FormatString` element is optional.</span></span> <span data-ttu-id="ac007-109">Du måste dock ange ett `PropertyName`-eller `ScriptBlock`-element, men du kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="ac007-109">However, you must specify a `PropertyName` or `ScriptBlock` element, but you cannot specify both.</span></span>

### <a name="attributes"></a><span data-ttu-id="ac007-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="ac007-110">Attributes</span></span>

<span data-ttu-id="ac007-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="ac007-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ac007-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="ac007-112">Child Elements</span></span>

|<span data-ttu-id="ac007-113">Element</span><span class="sxs-lookup"><span data-stu-id="ac007-113">Element</span></span>|<span data-ttu-id="ac007-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ac007-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ac007-115">FormatString-element för WideItem för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="ac007-115">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="ac007-116">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="ac007-116">Optional element.</span></span><br /><br /> <span data-ttu-id="ac007-117">Anger ett format mönster som definierar hur egenskapen eller skriptets värde visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="ac007-117">Specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>|
|[<span data-ttu-id="ac007-118">PropertyName-element för WideItem (format)</span><span class="sxs-lookup"><span data-stu-id="ac007-118">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="ac007-119">Anger egenskapen för det objekt vars värde visas i den bred vyn.</span><span class="sxs-lookup"><span data-stu-id="ac007-119">Specifies the property of the object whose value is displayed in the wide view.</span></span>|
|[<span data-ttu-id="ac007-120">Script block-element för WideItem (format)</span><span class="sxs-lookup"><span data-stu-id="ac007-120">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="ac007-121">Anger det skript vars värde visas i den breda vyn.</span><span class="sxs-lookup"><span data-stu-id="ac007-121">Specifies the script whose value is displayed in the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ac007-122">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="ac007-122">Parent Elements</span></span>

|<span data-ttu-id="ac007-123">Element</span><span class="sxs-lookup"><span data-stu-id="ac007-123">Element</span></span>|<span data-ttu-id="ac007-124">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ac007-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ac007-125">WideEntry-element (format)</span><span class="sxs-lookup"><span data-stu-id="ac007-125">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="ac007-126">Ger en definition av den breda vyn.</span><span class="sxs-lookup"><span data-stu-id="ac007-126">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ac007-127">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="ac007-127">Remarks</span></span>

<span data-ttu-id="ac007-128">Mer information om komponenterna i en bred vy finns i [wide View](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="ac007-128">For more information about the components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="ac007-129">Exempel</span><span class="sxs-lookup"><span data-stu-id="ac007-129">Example</span></span>

<span data-ttu-id="ac007-130">I följande exempel visas ett `WideEntry`-element som definierar ett enda `WideItem`-element.</span><span class="sxs-lookup"><span data-stu-id="ac007-130">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="ac007-131">Elementet `WideItem` definierar egenskapen eller skriptet vars värde visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="ac007-131">The `WideItem` element defines the property or script whose value is displayed in the view.</span></span>

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

<span data-ttu-id="ac007-132">Ett fullständigt exempel på en bred vy finns i [wide View (grundläggande)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="ac007-132">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ac007-133">Se även</span><span class="sxs-lookup"><span data-stu-id="ac007-133">See Also</span></span>

[<span data-ttu-id="ac007-134">FormatString-element för WideItem för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="ac007-134">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="ac007-135">PropertyName-element för WideItem (format)</span><span class="sxs-lookup"><span data-stu-id="ac007-135">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="ac007-136">Script block-element för WideItem (format)</span><span class="sxs-lookup"><span data-stu-id="ac007-136">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="ac007-137">WideEntry-element (format)</span><span class="sxs-lookup"><span data-stu-id="ac007-137">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="ac007-138">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="ac007-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
