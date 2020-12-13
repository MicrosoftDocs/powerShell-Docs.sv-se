---
ms.date: 09/13/2016
ms.topic: reference
title: ScriptBlock-element för WideItem för WideControl (format)
description: ScriptBlock-element för WideItem för WideControl (format)
ms.openlocfilehash: 68e47926e5e6b846c8a0a3dbc16d1f0d59f11dee
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659874"
---
# <a name="scriptblock-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="df6d0-103">ScriptBlock-element för WideItem för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="df6d0-103">ScriptBlock Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="df6d0-104">Anger det skript vars värde visas i den breda vyn.</span><span class="sxs-lookup"><span data-stu-id="df6d0-104">Specifies the script whose value is displayed in the wide view.</span></span>

<span data-ttu-id="df6d0-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) WideControl-element (format) WideEntries-element (format) WideEntry-element (format) WideItem element (format) script block-element för WideItem (format)</span><span class="sxs-lookup"><span data-stu-id="df6d0-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) ScriptBlock Element for WideItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="df6d0-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="df6d0-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToExecute</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="df6d0-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="df6d0-107">Attributes and Elements</span></span>

<span data-ttu-id="df6d0-108">I följande avsnitt beskrivs attributen, underordnade element och `ScriptBlock` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="df6d0-108">The following sections describe the attributes, child elements, and parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="df6d0-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="df6d0-109">Attributes</span></span>

<span data-ttu-id="df6d0-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="df6d0-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="df6d0-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="df6d0-111">Child Elements</span></span>

<span data-ttu-id="df6d0-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="df6d0-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="df6d0-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="df6d0-113">Parent Elements</span></span>

|<span data-ttu-id="df6d0-114">Element</span><span class="sxs-lookup"><span data-stu-id="df6d0-114">Element</span></span>|<span data-ttu-id="df6d0-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="df6d0-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="df6d0-116">WideItem-element (format)</span><span class="sxs-lookup"><span data-stu-id="df6d0-116">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="df6d0-117">Definierar egenskapen eller skript blocket vars värde visas i den breda vyn.</span><span class="sxs-lookup"><span data-stu-id="df6d0-117">Defines the property or script block whose value is displayed in the wide view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="df6d0-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="df6d0-118">Text Value</span></span>

<span data-ttu-id="df6d0-119">Ange det skript vars värde visas.</span><span class="sxs-lookup"><span data-stu-id="df6d0-119">Specify the script whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="df6d0-120">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="df6d0-120">Remarks</span></span>

<span data-ttu-id="df6d0-121">Mer information om komponenterna i en bred vy finns i [skapa en bred vy](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="df6d0-121">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="df6d0-122">Exempel</span><span class="sxs-lookup"><span data-stu-id="df6d0-122">Example</span></span>

<span data-ttu-id="df6d0-123">Det här exemplet visar ett- `WideItem` element som definierar ett skript vars värde visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="df6d0-123">This example shows a `WideItem` element that defines a script whose value is displayed in the view.</span></span>

```xml
<WideItem>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
</WideItem>
```

## <a name="see-also"></a><span data-ttu-id="df6d0-124">Se även</span><span class="sxs-lookup"><span data-stu-id="df6d0-124">See Also</span></span>

[<span data-ttu-id="df6d0-125">WideItem-element (format)</span><span class="sxs-lookup"><span data-stu-id="df6d0-125">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="df6d0-126">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="df6d0-126">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="df6d0-127">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="df6d0-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
