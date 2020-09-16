---
title: WideItem-element för WideControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 6b2f7c97978c20350caeec894589c5995ae7ccc4
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779904"
---
# <a name="wideitem-element-for-widecontrol-format"></a><span data-ttu-id="4e2ff-102">WideItem-element för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="4e2ff-102">WideItem Element for WideControl (Format)</span></span>

<span data-ttu-id="4e2ff-103">Definierar egenskapen eller skriptet vars värde visas.</span><span class="sxs-lookup"><span data-stu-id="4e2ff-103">Defines the property or script whose value is displayed.</span></span>

<span data-ttu-id="4e2ff-104">Konfigurations element (format) ViewDefinitions element (format) View-element (format) WideControl-element (format) WideEntries-element (format) WideEntry-element (format) WideItem-element (format)</span><span class="sxs-lookup"><span data-stu-id="4e2ff-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4e2ff-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="4e2ff-105">Syntax</span></span>

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4e2ff-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="4e2ff-106">Attributes and Elements</span></span>

<span data-ttu-id="4e2ff-107">I följande avsnitt beskrivs attributen, underordnade element och `WideItem` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="4e2ff-107">The following sections describe the attributes, child elements, and the parent element of the `WideItem` element.</span></span> <span data-ttu-id="4e2ff-108">`FormatString`Elementet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="4e2ff-108">The `FormatString` element is optional.</span></span> <span data-ttu-id="4e2ff-109">Du måste dock ange ett `PropertyName` eller `ScriptBlock` -element, men du kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="4e2ff-109">However, you must specify a `PropertyName` or `ScriptBlock` element, but you cannot specify both.</span></span>

### <a name="attributes"></a><span data-ttu-id="4e2ff-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="4e2ff-110">Attributes</span></span>

<span data-ttu-id="4e2ff-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="4e2ff-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4e2ff-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="4e2ff-112">Child Elements</span></span>

|<span data-ttu-id="4e2ff-113">Element</span><span class="sxs-lookup"><span data-stu-id="4e2ff-113">Element</span></span>|<span data-ttu-id="4e2ff-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="4e2ff-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4e2ff-115">FormatString-element för WideItem för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="4e2ff-115">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="4e2ff-116">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="4e2ff-116">Optional element.</span></span><br /><br /> <span data-ttu-id="4e2ff-117">Anger ett format mönster som definierar hur egenskapen eller skriptets värde visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="4e2ff-117">Specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>|
|[<span data-ttu-id="4e2ff-118">PropertyName-element för WideItem (format)</span><span class="sxs-lookup"><span data-stu-id="4e2ff-118">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="4e2ff-119">Anger egenskapen för det objekt vars värde visas i den bred vyn.</span><span class="sxs-lookup"><span data-stu-id="4e2ff-119">Specifies the property of the object whose value is displayed in the wide view.</span></span>|
|[<span data-ttu-id="4e2ff-120">Script block-element för WideItem (format)</span><span class="sxs-lookup"><span data-stu-id="4e2ff-120">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="4e2ff-121">Anger det skript vars värde visas i den breda vyn.</span><span class="sxs-lookup"><span data-stu-id="4e2ff-121">Specifies the script whose value is displayed in the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4e2ff-122">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="4e2ff-122">Parent Elements</span></span>

|<span data-ttu-id="4e2ff-123">Element</span><span class="sxs-lookup"><span data-stu-id="4e2ff-123">Element</span></span>|<span data-ttu-id="4e2ff-124">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="4e2ff-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4e2ff-125">WideEntry-element (format)</span><span class="sxs-lookup"><span data-stu-id="4e2ff-125">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="4e2ff-126">Ger en definition av den breda vyn.</span><span class="sxs-lookup"><span data-stu-id="4e2ff-126">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4e2ff-127">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="4e2ff-127">Remarks</span></span>

<span data-ttu-id="4e2ff-128">Mer information om komponenterna i en bred vy finns i [wide View](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="4e2ff-128">For more information about the components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="4e2ff-129">Exempel</span><span class="sxs-lookup"><span data-stu-id="4e2ff-129">Example</span></span>

<span data-ttu-id="4e2ff-130">I följande exempel visas ett `WideEntry` element som definierar ett enda `WideItem` element.</span><span class="sxs-lookup"><span data-stu-id="4e2ff-130">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="4e2ff-131">`WideItem`Elementet definierar egenskapen eller skriptet vars värde visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="4e2ff-131">The `WideItem` element defines the property or script whose value is displayed in the view.</span></span>

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

<span data-ttu-id="4e2ff-132">Ett fullständigt exempel på en bred vy finns i [wide View (grundläggande)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="4e2ff-132">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4e2ff-133">Se även</span><span class="sxs-lookup"><span data-stu-id="4e2ff-133">See Also</span></span>

[<span data-ttu-id="4e2ff-134">FormatString-element för WideItem för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="4e2ff-134">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="4e2ff-135">PropertyName-element för WideItem (format)</span><span class="sxs-lookup"><span data-stu-id="4e2ff-135">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="4e2ff-136">Script block-element för WideItem (format)</span><span class="sxs-lookup"><span data-stu-id="4e2ff-136">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="4e2ff-137">WideEntry-element (format)</span><span class="sxs-lookup"><span data-stu-id="4e2ff-137">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="4e2ff-138">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="4e2ff-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
