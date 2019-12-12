---
title: WideEntries-element för WideControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c4bff45-0960-4b3a-95e7-47f2cee03ac5
caps.latest.revision: 12
ms.openlocfilehash: 083f3c8df8136858e32778ed231943ef983e47aa
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353426"
---
# <a name="wideentries-element-for-widecontrol-format"></a><span data-ttu-id="6a6d7-102">WideEntries-element för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="6a6d7-102">WideEntries Element for WideControl (Format)</span></span>

<span data-ttu-id="6a6d7-103">Innehåller definitionerna för den breda vyn.</span><span class="sxs-lookup"><span data-stu-id="6a6d7-103">Provides the definitions of the wide view.</span></span> <span data-ttu-id="6a6d7-104">Wide View måste ange en eller flera definitioner.</span><span class="sxs-lookup"><span data-stu-id="6a6d7-104">The wide view must specify one or more definitions.</span></span>

<span data-ttu-id="6a6d7-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) WideControl-element (format) element för WideEntries (format)</span><span class="sxs-lookup"><span data-stu-id="6a6d7-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6a6d7-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="6a6d7-106">Syntax</span></span>

```xml
<WideEntries>
  <WideEntry>...</WideEntry>
</WideEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="6a6d7-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="6a6d7-107">Attributes and Elements</span></span>

<span data-ttu-id="6a6d7-108">I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet i `WideEntries`-elementet.</span><span class="sxs-lookup"><span data-stu-id="6a6d7-108">The following sections describe the attributes, child elements, and parent element of the `WideEntries` element.</span></span> <span data-ttu-id="6a6d7-109">Minst ett underordnat element måste anges.</span><span class="sxs-lookup"><span data-stu-id="6a6d7-109">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="6a6d7-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="6a6d7-110">Attributes</span></span>

<span data-ttu-id="6a6d7-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="6a6d7-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6a6d7-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="6a6d7-112">Child Elements</span></span>

|<span data-ttu-id="6a6d7-113">Element</span><span class="sxs-lookup"><span data-stu-id="6a6d7-113">Element</span></span>|<span data-ttu-id="6a6d7-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="6a6d7-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6a6d7-115">WideEntry-element (format)</span><span class="sxs-lookup"><span data-stu-id="6a6d7-115">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="6a6d7-116">Ger en definition av den breda vyn.</span><span class="sxs-lookup"><span data-stu-id="6a6d7-116">Provides a definition of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6a6d7-117">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="6a6d7-117">Parent Elements</span></span>

|<span data-ttu-id="6a6d7-118">Element</span><span class="sxs-lookup"><span data-stu-id="6a6d7-118">Element</span></span>|<span data-ttu-id="6a6d7-119">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="6a6d7-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6a6d7-120">WideControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="6a6d7-120">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="6a6d7-121">Definierar ett brett List format (enskilt värde) för vyn.</span><span class="sxs-lookup"><span data-stu-id="6a6d7-121">Defines a wide (single value) list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6a6d7-122">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="6a6d7-122">Remarks</span></span>

<span data-ttu-id="6a6d7-123">En bred vy är ett List format som visar ett enda egenskaps värde eller skript värde för varje objekt.</span><span class="sxs-lookup"><span data-stu-id="6a6d7-123">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="6a6d7-124">Mer information om komponenterna i en bred vy finns i [wide View-komponenter](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="6a6d7-124">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="6a6d7-125">Exempel</span><span class="sxs-lookup"><span data-stu-id="6a6d7-125">Example</span></span>

<span data-ttu-id="6a6d7-126">I följande exempel visas ett `WideEntries`-element som definierar ett enskilt `WideEntry`-element.</span><span class="sxs-lookup"><span data-stu-id="6a6d7-126">The following example shows a `WideEntries` element that defines a single `WideEntry` element.</span></span> <span data-ttu-id="6a6d7-127">`WideEntry`-elementet innehåller ett enda `WideItem`-element som definierar vilken egenskap eller vilket skript värde som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="6a6d7-127">The `WideEntry` element contains a single `WideItem` element that defines what property or script value is displayed in the view.</span></span>

```xml
<WideControl>
  <WideEntries>
    <WideEntry>
      <WideItem>...</WideItem>
    <WideEntry>
  </WideEntries>
</WideControl>
```

<span data-ttu-id="6a6d7-128">Ett fullständigt exempel på en bred vy finns i [wide View (grundläggande)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="6a6d7-128">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6a6d7-129">Se även</span><span class="sxs-lookup"><span data-stu-id="6a6d7-129">See Also</span></span>

[<span data-ttu-id="6a6d7-130">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="6a6d7-130">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="6a6d7-131">WideControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="6a6d7-131">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="6a6d7-132">WideEntry-element (format)</span><span class="sxs-lookup"><span data-stu-id="6a6d7-132">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="6a6d7-133">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="6a6d7-133">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
