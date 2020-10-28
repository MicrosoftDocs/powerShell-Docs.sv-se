---
ms.date: 09/13/2016
ms.topic: reference
title: PropertyName-element för GroupBy (format)
description: PropertyName-element för GroupBy (format)
ms.openlocfilehash: 44351c46ff2386f967644fef4f423b3858dc1619
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92666152"
---
# <a name="propertyname-element-for-groupby-format"></a><span data-ttu-id="62ec8-103">PropertyName-element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="62ec8-103">PropertyName Element for GroupBy (Format)</span></span>

<span data-ttu-id="62ec8-104">Anger den .NET-egenskap som startar en ny grupp när dess värde ändras.</span><span class="sxs-lookup"><span data-stu-id="62ec8-104">Specifies the .NET property that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="62ec8-105">Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) PropertyName-element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="62ec8-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) PropertyName Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="62ec8-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="62ec8-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="62ec8-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="62ec8-107">Attributes and Elements</span></span>

<span data-ttu-id="62ec8-108">I följande avsnitt beskrivs attribut, underordnade element och `PropertyName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="62ec8-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="62ec8-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="62ec8-109">Attributes</span></span>

<span data-ttu-id="62ec8-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="62ec8-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="62ec8-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="62ec8-111">Child Elements</span></span>

<span data-ttu-id="62ec8-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="62ec8-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="62ec8-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="62ec8-113">Parent Elements</span></span>

|<span data-ttu-id="62ec8-114">Element</span><span class="sxs-lookup"><span data-stu-id="62ec8-114">Element</span></span>|<span data-ttu-id="62ec8-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="62ec8-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="62ec8-116">GroupBy-element för View (format)</span><span class="sxs-lookup"><span data-stu-id="62ec8-116">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="62ec8-117">Definierar hur en grupp med .NET-objekt visas.</span><span class="sxs-lookup"><span data-stu-id="62ec8-117">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="62ec8-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="62ec8-118">Text Value</span></span>

<span data-ttu-id="62ec8-119">Ange .NET-egenskaps namnet.</span><span class="sxs-lookup"><span data-stu-id="62ec8-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="62ec8-120">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="62ec8-120">Remarks</span></span>

<span data-ttu-id="62ec8-121">Windows PowerShell startar en ny grupp när värdet för den här egenskapen ändras.</span><span class="sxs-lookup"><span data-stu-id="62ec8-121">Windows PowerShell starts a new group whenever the value of this property changes.</span></span>

<span data-ttu-id="62ec8-122">När det här elementet har angetts kan du inte ange [script block](./scriptblock-element-for-groupby-format.md) -elementet för att starta en ny grupp.</span><span class="sxs-lookup"><span data-stu-id="62ec8-122">When this element is specified, you cannot specify the [ScriptBlock](./scriptblock-element-for-groupby-format.md) element to start a new group.</span></span>

## <a name="example"></a><span data-ttu-id="62ec8-123">Exempel</span><span class="sxs-lookup"><span data-stu-id="62ec8-123">Example</span></span>

<span data-ttu-id="62ec8-124">I följande exempel visas hur du startar en ny grupp när värdet för en egenskap ändras.</span><span class="sxs-lookup"><span data-stu-id="62ec8-124">The following example shows how to start a new group when the value of a property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="62ec8-125">Ett exempel på en hel format fil som innehåller det här elementet finns i [wide View (groupby)](./wide-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="62ec8-125">For an example of a complete formatting file that includes this element, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="62ec8-126">Se även</span><span class="sxs-lookup"><span data-stu-id="62ec8-126">See Also</span></span>

[<span data-ttu-id="62ec8-127">GroupBy-element för View (format)</span><span class="sxs-lookup"><span data-stu-id="62ec8-127">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="62ec8-128">ScriptBlock-element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="62ec8-128">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="62ec8-129">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="62ec8-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
