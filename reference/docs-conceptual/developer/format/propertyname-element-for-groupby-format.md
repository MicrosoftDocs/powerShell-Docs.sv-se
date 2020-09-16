---
title: PropertyName-element för GroupBy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e83ebd49e4f3087c817b3cc8772889dbe85113aa
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785616"
---
# <a name="propertyname-element-for-groupby-format"></a><span data-ttu-id="94e5f-102">PropertyName-element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="94e5f-102">PropertyName Element for GroupBy (Format)</span></span>

<span data-ttu-id="94e5f-103">Anger den .NET-egenskap som startar en ny grupp när dess värde ändras.</span><span class="sxs-lookup"><span data-stu-id="94e5f-103">Specifies the .NET property that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="94e5f-104">Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) PropertyName-element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="94e5f-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) PropertyName Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="94e5f-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="94e5f-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="94e5f-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="94e5f-106">Attributes and Elements</span></span>

<span data-ttu-id="94e5f-107">I följande avsnitt beskrivs attribut, underordnade element och `PropertyName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="94e5f-107">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="94e5f-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="94e5f-108">Attributes</span></span>

<span data-ttu-id="94e5f-109">Inga.</span><span class="sxs-lookup"><span data-stu-id="94e5f-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="94e5f-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="94e5f-110">Child Elements</span></span>

<span data-ttu-id="94e5f-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="94e5f-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="94e5f-112">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="94e5f-112">Parent Elements</span></span>

|<span data-ttu-id="94e5f-113">Element</span><span class="sxs-lookup"><span data-stu-id="94e5f-113">Element</span></span>|<span data-ttu-id="94e5f-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="94e5f-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="94e5f-115">GroupBy-element för View (format)</span><span class="sxs-lookup"><span data-stu-id="94e5f-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="94e5f-116">Definierar hur en grupp med .NET-objekt visas.</span><span class="sxs-lookup"><span data-stu-id="94e5f-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="94e5f-117">Textvärde</span><span class="sxs-lookup"><span data-stu-id="94e5f-117">Text Value</span></span>

<span data-ttu-id="94e5f-118">Ange .NET-egenskaps namnet.</span><span class="sxs-lookup"><span data-stu-id="94e5f-118">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="94e5f-119">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="94e5f-119">Remarks</span></span>

<span data-ttu-id="94e5f-120">Windows PowerShell startar en ny grupp när värdet för den här egenskapen ändras.</span><span class="sxs-lookup"><span data-stu-id="94e5f-120">Windows PowerShell starts a new group whenever the value of this property changes.</span></span>

<span data-ttu-id="94e5f-121">När det här elementet har angetts kan du inte ange [script block](./scriptblock-element-for-groupby-format.md) -elementet för att starta en ny grupp.</span><span class="sxs-lookup"><span data-stu-id="94e5f-121">When this element is specified, you cannot specify the [ScriptBlock](./scriptblock-element-for-groupby-format.md) element to start a new group.</span></span>

## <a name="example"></a><span data-ttu-id="94e5f-122">Exempel</span><span class="sxs-lookup"><span data-stu-id="94e5f-122">Example</span></span>

<span data-ttu-id="94e5f-123">I följande exempel visas hur du startar en ny grupp när värdet för en egenskap ändras.</span><span class="sxs-lookup"><span data-stu-id="94e5f-123">The following example shows how to start a new group when the value of a property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="94e5f-124">Ett exempel på en hel format fil som innehåller det här elementet finns i [wide View (groupby)](./wide-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="94e5f-124">For an example of a complete formatting file that includes this element, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="94e5f-125">Se även</span><span class="sxs-lookup"><span data-stu-id="94e5f-125">See Also</span></span>

[<span data-ttu-id="94e5f-126">GroupBy-element för View (format)</span><span class="sxs-lookup"><span data-stu-id="94e5f-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="94e5f-127">ScriptBlock-element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="94e5f-127">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="94e5f-128">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="94e5f-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
