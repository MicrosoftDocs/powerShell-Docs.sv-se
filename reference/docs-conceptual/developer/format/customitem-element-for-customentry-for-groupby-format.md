---
title: CustomItem-element för CustomEntry for GroupBy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e8086c5330b6644f83316ad4ae33c33ba40d9eee
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783729"
---
# <a name="customitem-element-for-customentry-for-groupby-format"></a><span data-ttu-id="b5ab4-102">CustomItem-element för CustomEntry för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="b5ab4-102">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="b5ab4-103">Definierar vilka data som visas i vyn anpassad kontroll och hur den visas.</span><span class="sxs-lookup"><span data-stu-id="b5ab4-103">Defines what data is displayed by the custom control view and how it is displayed.</span></span> <span data-ttu-id="b5ab4-104">Det här elementet används när du definierar hur en ny grupp av objekt visas.</span><span class="sxs-lookup"><span data-stu-id="b5ab4-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="b5ab4-105">Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for groupby (format) CustomItem-element för CustomEntry för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="b5ab4-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b5ab4-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="b5ab4-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b5ab4-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="b5ab4-107">Attributes and Elements</span></span>

<span data-ttu-id="b5ab4-108">I följande avsnitt beskrivs attribut, underordnade element och `CustomItem` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="b5ab4-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b5ab4-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="b5ab4-109">Attributes</span></span>

<span data-ttu-id="b5ab4-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="b5ab4-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b5ab4-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="b5ab4-111">Child Elements</span></span>

|<span data-ttu-id="b5ab4-112">Element</span><span class="sxs-lookup"><span data-stu-id="b5ab4-112">Element</span></span>|<span data-ttu-id="b5ab4-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b5ab4-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b5ab4-114">ExpressionBinding-element för CustomItem för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="b5ab4-114">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="b5ab4-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="b5ab4-115">Optional element.</span></span><br /><br /> <span data-ttu-id="b5ab4-116">Definierar de data som visas av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="b5ab4-116">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="b5ab4-117">Frame-element för CustomItem för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="b5ab4-117">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="b5ab4-118">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="b5ab4-118">Optional element.</span></span><br /><br /> <span data-ttu-id="b5ab4-119">Definierar vilka data som visas i vyn anpassad kontroll och hur den visas.</span><span class="sxs-lookup"><span data-stu-id="b5ab4-119">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|
|[<span data-ttu-id="b5ab4-120">NewLine-element för CustomItem för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="b5ab4-120">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="b5ab4-121">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="b5ab4-121">Optional element.</span></span><br /><br /> <span data-ttu-id="b5ab4-122">Lägger till en tom rad i visningen av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="b5ab4-122">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="b5ab4-123">Text-element för CustomItem för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="b5ab4-123">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="b5ab4-124">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="b5ab4-124">Optional element.</span></span><br /><br /> <span data-ttu-id="b5ab4-125">Anger ytterligare text för de data som visas i kontrollen.</span><span class="sxs-lookup"><span data-stu-id="b5ab4-125">Specifies additional text to the data displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b5ab4-126">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="b5ab4-126">Parent Elements</span></span>

|<span data-ttu-id="b5ab4-127">Element</span><span class="sxs-lookup"><span data-stu-id="b5ab4-127">Element</span></span>|<span data-ttu-id="b5ab4-128">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b5ab4-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b5ab4-129">CustomEntry-element för CustomControl för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="b5ab4-129">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="b5ab4-130">Innehåller en definition av den anpassade kontrollen.</span><span class="sxs-lookup"><span data-stu-id="b5ab4-130">Provides a definition of the custom control view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b5ab4-131">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="b5ab4-131">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="b5ab4-132">Se även</span><span class="sxs-lookup"><span data-stu-id="b5ab4-132">See Also</span></span>

[<span data-ttu-id="b5ab4-133">CustomEntry-element för CustomControl för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="b5ab4-133">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="b5ab4-134">ExpressionBinding-element för CustomItem för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="b5ab4-134">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="b5ab4-135">Frame-element för CustomItem för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="b5ab4-135">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="b5ab4-136">NewLine-element för CustomItem för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="b5ab4-136">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="b5ab4-137">Text-element för CustomItem för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="b5ab4-137">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="b5ab4-138">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="b5ab4-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
