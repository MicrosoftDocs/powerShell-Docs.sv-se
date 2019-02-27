---
title: Etikettera Element för GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3351d237-e8c2-4ec5-9500-4eceadb407c2
caps.latest.revision: 11
ms.openlocfilehash: e7158711c60d13c745bbdfab9b1b9fc7d98b34e2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851291"
---
# <a name="label-element-for-groupby-format"></a><span data-ttu-id="8453c-102">Label-element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="8453c-102">Label Element for GroupBy (Format)</span></span>

<span data-ttu-id="8453c-103">Anger en etikett som visas när en ny grupp har påträffats.</span><span class="sxs-lookup"><span data-stu-id="8453c-103">Specifies a label that is displayed when a new group is encountered.</span></span>

<span data-ttu-id="8453c-104">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) GroupBy konfigurationselement för Visa (Format) etikett elementet för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="8453c-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) Label Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8453c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="8453c-105">Syntax</span></span>

```xml
<Label>DisplayedLabel</Label>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8453c-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="8453c-106">Attributes and Elements</span></span>

<span data-ttu-id="8453c-107">I följande avsnitt beskrivs de attribut och underordnade element överordnade elementet i den `Label` element.</span><span class="sxs-lookup"><span data-stu-id="8453c-107">The following sections describe the attributes, child elements, and parent element of the `Label` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8453c-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="8453c-108">Attributes</span></span>

<span data-ttu-id="8453c-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="8453c-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8453c-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="8453c-110">Child Elements</span></span>

<span data-ttu-id="8453c-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="8453c-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8453c-112">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="8453c-112">Parent Elements</span></span>

|<span data-ttu-id="8453c-113">Element</span><span class="sxs-lookup"><span data-stu-id="8453c-113">Element</span></span>|<span data-ttu-id="8453c-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8453c-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8453c-115">GroupBy-Element för Visa (Format)</span><span class="sxs-lookup"><span data-stu-id="8453c-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="8453c-116">Definierar hur en ny grupp med objekt visas.</span><span class="sxs-lookup"><span data-stu-id="8453c-116">Defines how a new group of objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8453c-117">Textvärde</span><span class="sxs-lookup"><span data-stu-id="8453c-117">Text Value</span></span>

<span data-ttu-id="8453c-118">Ange vilken text som visas när en ny egenskap eller skriptvärdet uppstår med hjälp av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8453c-118">Specify the text that is displayed whenever Windows PowerShell encounters a new property or script value.</span></span>

## <a name="remarks"></a><span data-ttu-id="8453c-119">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="8453c-119">Remarks</span></span>

<span data-ttu-id="8453c-120">Förutom den text som anges av det här elementet, visar det nya värdet som startar gruppen och lägger till en tom rad före och efter gruppen i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8453c-120">In addition to the text specified by this element, Windows PowerShell displays the new value that starts the group, and adds a blank line before and after the group.</span></span>

## <a name="example"></a><span data-ttu-id="8453c-121">Exempel</span><span class="sxs-lookup"><span data-stu-id="8453c-121">Example</span></span>

<span data-ttu-id="8453c-122">I följande exempel visar etiketten för en ny grupp.</span><span class="sxs-lookup"><span data-stu-id="8453c-122">The following example shows the label for a new group.</span></span> <span data-ttu-id="8453c-123">Visas etiketten skulle se ut ungefär så här: `Service Type: NewValueofProperty`</span><span class="sxs-lookup"><span data-stu-id="8453c-123">The displayed label would look similar to this: `Service Type: NewValueofProperty`</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="8453c-124">Ett exempel på en fullständig formatering fil som innehåller det här elementet finns [bred vy (GroupBy)](./wide-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="8453c-124">For an example of a complete formatting file that includes this element, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8453c-125">Se även</span><span class="sxs-lookup"><span data-stu-id="8453c-125">See Also</span></span>

[<span data-ttu-id="8453c-126">GroupBy-Element för Visa (Format)</span><span class="sxs-lookup"><span data-stu-id="8453c-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="8453c-127">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="8453c-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
