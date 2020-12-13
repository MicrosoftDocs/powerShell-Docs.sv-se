---
ms.date: 09/13/2016
ms.topic: reference
title: Label-element för GroupBy (format)
description: Label-element för GroupBy (format)
ms.openlocfilehash: ff4b0dec01bb5b472b1813540661791b91568eed
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649791"
---
# <a name="label-element-for-groupby-format"></a><span data-ttu-id="8ff5e-103">Label-element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="8ff5e-103">Label Element for GroupBy (Format)</span></span>

<span data-ttu-id="8ff5e-104">Anger en etikett som visas när en ny grupp påträffas.</span><span class="sxs-lookup"><span data-stu-id="8ff5e-104">Specifies a label that is displayed when a new group is encountered.</span></span>

<span data-ttu-id="8ff5e-105">Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för visnings-(format) etikett element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="8ff5e-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) Label Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8ff5e-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="8ff5e-106">Syntax</span></span>

```xml
<Label>DisplayedLabel</Label>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8ff5e-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="8ff5e-107">Attributes and Elements</span></span>

<span data-ttu-id="8ff5e-108">I följande avsnitt beskrivs attributen, underordnade element och `Label` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="8ff5e-108">The following sections describe the attributes, child elements, and parent element of the `Label` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8ff5e-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="8ff5e-109">Attributes</span></span>

<span data-ttu-id="8ff5e-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="8ff5e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8ff5e-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="8ff5e-111">Child Elements</span></span>

<span data-ttu-id="8ff5e-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="8ff5e-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8ff5e-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="8ff5e-113">Parent Elements</span></span>

|<span data-ttu-id="8ff5e-114">Element</span><span class="sxs-lookup"><span data-stu-id="8ff5e-114">Element</span></span>|<span data-ttu-id="8ff5e-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8ff5e-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8ff5e-116">GroupBy-element för View (format)</span><span class="sxs-lookup"><span data-stu-id="8ff5e-116">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="8ff5e-117">Definierar hur en ny grupp av objekt visas.</span><span class="sxs-lookup"><span data-stu-id="8ff5e-117">Defines how a new group of objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8ff5e-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="8ff5e-118">Text Value</span></span>

<span data-ttu-id="8ff5e-119">Ange texten som visas när Windows PowerShell påträffar en ny egenskap eller ett nytt skript värde.</span><span class="sxs-lookup"><span data-stu-id="8ff5e-119">Specify the text that is displayed whenever Windows PowerShell encounters a new property or script value.</span></span>

## <a name="remarks"></a><span data-ttu-id="8ff5e-120">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="8ff5e-120">Remarks</span></span>

<span data-ttu-id="8ff5e-121">Utöver den text som anges av det här elementet visar Windows PowerShell det nya värdet som startar gruppen och lägger till en tom rad före och efter gruppen.</span><span class="sxs-lookup"><span data-stu-id="8ff5e-121">In addition to the text specified by this element, Windows PowerShell displays the new value that starts the group, and adds a blank line before and after the group.</span></span>

## <a name="example"></a><span data-ttu-id="8ff5e-122">Exempel</span><span class="sxs-lookup"><span data-stu-id="8ff5e-122">Example</span></span>

<span data-ttu-id="8ff5e-123">I följande exempel visas etiketten för en ny grupp.</span><span class="sxs-lookup"><span data-stu-id="8ff5e-123">The following example shows the label for a new group.</span></span> <span data-ttu-id="8ff5e-124">Den visade etiketten ser ut ungefär så här: `Service Type: NewValueofProperty`</span><span class="sxs-lookup"><span data-stu-id="8ff5e-124">The displayed label would look similar to this: `Service Type: NewValueofProperty`</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="8ff5e-125">Ett exempel på en hel format fil som innehåller det här elementet finns i [wide View (groupby)](./wide-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="8ff5e-125">For an example of a complete formatting file that includes this element, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8ff5e-126">Se även</span><span class="sxs-lookup"><span data-stu-id="8ff5e-126">See Also</span></span>

[<span data-ttu-id="8ff5e-127">GroupBy-element för View (format)</span><span class="sxs-lookup"><span data-stu-id="8ff5e-127">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="8ff5e-128">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="8ff5e-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
