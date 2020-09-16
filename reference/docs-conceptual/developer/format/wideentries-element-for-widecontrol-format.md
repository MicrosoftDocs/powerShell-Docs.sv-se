---
title: WideEntries-element för WideControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 74383b288c945008c1d7b5119363a166c04802ae
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785055"
---
# <a name="wideentries-element-for-widecontrol-format"></a><span data-ttu-id="86597-102">WideEntries-element för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="86597-102">WideEntries Element for WideControl (Format)</span></span>

<span data-ttu-id="86597-103">Innehåller definitionerna för den breda vyn.</span><span class="sxs-lookup"><span data-stu-id="86597-103">Provides the definitions of the wide view.</span></span> <span data-ttu-id="86597-104">Wide View måste ange en eller flera definitioner.</span><span class="sxs-lookup"><span data-stu-id="86597-104">The wide view must specify one or more definitions.</span></span>

<span data-ttu-id="86597-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) WideControl-element (format) element för WideEntries (format)</span><span class="sxs-lookup"><span data-stu-id="86597-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="86597-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="86597-106">Syntax</span></span>

```xml
<WideEntries>
  <WideEntry>...</WideEntry>
</WideEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="86597-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="86597-107">Attributes and Elements</span></span>

<span data-ttu-id="86597-108">I följande avsnitt beskrivs attributen, underordnade element och `WideEntries` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="86597-108">The following sections describe the attributes, child elements, and parent element of the `WideEntries` element.</span></span> <span data-ttu-id="86597-109">Minst ett underordnat element måste anges.</span><span class="sxs-lookup"><span data-stu-id="86597-109">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="86597-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="86597-110">Attributes</span></span>

<span data-ttu-id="86597-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="86597-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="86597-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="86597-112">Child Elements</span></span>

|<span data-ttu-id="86597-113">Element</span><span class="sxs-lookup"><span data-stu-id="86597-113">Element</span></span>|<span data-ttu-id="86597-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="86597-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="86597-115">WideEntry-element (format)</span><span class="sxs-lookup"><span data-stu-id="86597-115">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="86597-116">Ger en definition av den breda vyn.</span><span class="sxs-lookup"><span data-stu-id="86597-116">Provides a definition of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="86597-117">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="86597-117">Parent Elements</span></span>

|<span data-ttu-id="86597-118">Element</span><span class="sxs-lookup"><span data-stu-id="86597-118">Element</span></span>|<span data-ttu-id="86597-119">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="86597-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="86597-120">WideControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="86597-120">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="86597-121">Definierar ett brett List format (enskilt värde) för vyn.</span><span class="sxs-lookup"><span data-stu-id="86597-121">Defines a wide (single value) list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="86597-122">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="86597-122">Remarks</span></span>

<span data-ttu-id="86597-123">En bred vy är ett List format som visar ett enda egenskaps värde eller skript värde för varje objekt.</span><span class="sxs-lookup"><span data-stu-id="86597-123">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="86597-124">Mer information om komponenterna i en bred vy finns i [wide View-komponenter](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="86597-124">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="86597-125">Exempel</span><span class="sxs-lookup"><span data-stu-id="86597-125">Example</span></span>

<span data-ttu-id="86597-126">I följande exempel visas ett `WideEntries` element som definierar ett enda `WideEntry` element.</span><span class="sxs-lookup"><span data-stu-id="86597-126">The following example shows a `WideEntries` element that defines a single `WideEntry` element.</span></span> <span data-ttu-id="86597-127">`WideEntry`Elementet innehåller ett enda `WideItem` element som definierar vilken egenskap eller vilket skript värde som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="86597-127">The `WideEntry` element contains a single `WideItem` element that defines what property or script value is displayed in the view.</span></span>

```xml
<WideControl>
  <WideEntries>
    <WideEntry>
      <WideItem>...</WideItem>
    <WideEntry>
  </WideEntries>
</WideControl>
```

<span data-ttu-id="86597-128">Ett fullständigt exempel på en bred vy finns i [wide View (grundläggande)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="86597-128">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="86597-129">Se även</span><span class="sxs-lookup"><span data-stu-id="86597-129">See Also</span></span>

[<span data-ttu-id="86597-130">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="86597-130">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="86597-131">WideControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="86597-131">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="86597-132">WideEntry-element (format)</span><span class="sxs-lookup"><span data-stu-id="86597-132">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="86597-133">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="86597-133">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
