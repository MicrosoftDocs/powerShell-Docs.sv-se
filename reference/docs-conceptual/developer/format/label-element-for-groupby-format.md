---
title: Etikett element för GroupBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3351d237-e8c2-4ec5-9500-4eceadb407c2
caps.latest.revision: 11
ms.openlocfilehash: e7158711c60d13c745bbdfab9b1b9fc7d98b34e2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72356065"
---
# <a name="label-element-for-groupby-format"></a><span data-ttu-id="e85d2-102">Label-element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="e85d2-102">Label Element for GroupBy (Format)</span></span>

<span data-ttu-id="e85d2-103">Anger en etikett som visas när en ny grupp påträffas.</span><span class="sxs-lookup"><span data-stu-id="e85d2-103">Specifies a label that is displayed when a new group is encountered.</span></span>

<span data-ttu-id="e85d2-104">Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för visnings-(format) etikett element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="e85d2-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) Label Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e85d2-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="e85d2-105">Syntax</span></span>

```xml
<Label>DisplayedLabel</Label>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e85d2-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="e85d2-106">Attributes and Elements</span></span>

<span data-ttu-id="e85d2-107">I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet i `Label`-elementet.</span><span class="sxs-lookup"><span data-stu-id="e85d2-107">The following sections describe the attributes, child elements, and parent element of the `Label` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e85d2-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="e85d2-108">Attributes</span></span>

<span data-ttu-id="e85d2-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="e85d2-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e85d2-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="e85d2-110">Child Elements</span></span>

<span data-ttu-id="e85d2-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="e85d2-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e85d2-112">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="e85d2-112">Parent Elements</span></span>

|<span data-ttu-id="e85d2-113">Element</span><span class="sxs-lookup"><span data-stu-id="e85d2-113">Element</span></span>|<span data-ttu-id="e85d2-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e85d2-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e85d2-115">GroupBy-element för vy (format)</span><span class="sxs-lookup"><span data-stu-id="e85d2-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="e85d2-116">Definierar hur en ny grupp av objekt visas.</span><span class="sxs-lookup"><span data-stu-id="e85d2-116">Defines how a new group of objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e85d2-117">Textvärde</span><span class="sxs-lookup"><span data-stu-id="e85d2-117">Text Value</span></span>

<span data-ttu-id="e85d2-118">Ange texten som visas när Windows PowerShell påträffar en ny egenskap eller ett nytt skript värde.</span><span class="sxs-lookup"><span data-stu-id="e85d2-118">Specify the text that is displayed whenever Windows PowerShell encounters a new property or script value.</span></span>

## <a name="remarks"></a><span data-ttu-id="e85d2-119">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="e85d2-119">Remarks</span></span>

<span data-ttu-id="e85d2-120">Utöver den text som anges av det här elementet visar Windows PowerShell det nya värdet som startar gruppen och lägger till en tom rad före och efter gruppen.</span><span class="sxs-lookup"><span data-stu-id="e85d2-120">In addition to the text specified by this element, Windows PowerShell displays the new value that starts the group, and adds a blank line before and after the group.</span></span>

## <a name="example"></a><span data-ttu-id="e85d2-121">Exempel</span><span class="sxs-lookup"><span data-stu-id="e85d2-121">Example</span></span>

<span data-ttu-id="e85d2-122">I följande exempel visas etiketten för en ny grupp.</span><span class="sxs-lookup"><span data-stu-id="e85d2-122">The following example shows the label for a new group.</span></span> <span data-ttu-id="e85d2-123">Etiketten som visas ser ut ungefär så här: `Service Type: NewValueofProperty`</span><span class="sxs-lookup"><span data-stu-id="e85d2-123">The displayed label would look similar to this: `Service Type: NewValueofProperty`</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="e85d2-124">Ett exempel på en hel format fil som innehåller det här elementet finns i [wide View (groupby)](./wide-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="e85d2-124">For an example of a complete formatting file that includes this element, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e85d2-125">Se även</span><span class="sxs-lookup"><span data-stu-id="e85d2-125">See Also</span></span>

[<span data-ttu-id="e85d2-126">GroupBy-element för vy (format)</span><span class="sxs-lookup"><span data-stu-id="e85d2-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="e85d2-127">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="e85d2-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
