---
title: CustomItem-element för CustomEntry for GroupBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7c517aa-24f5-41ae-b82d-cb0fac81a245
caps.latest.revision: 7
ms.openlocfilehash: 2d821f5e3bc8d0f81ef8a8a040c6f9bcb1658bee
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355141"
---
# <a name="customitem-element-for-customentry-for-groupby-format"></a><span data-ttu-id="38386-102">CustomItem-element för CustomEntry för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="38386-102">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="38386-103">Definierar vilka data som visas i vyn anpassad kontroll och hur den visas.</span><span class="sxs-lookup"><span data-stu-id="38386-103">Defines what data is displayed by the custom control view and how it is displayed.</span></span> <span data-ttu-id="38386-104">Det här elementet används när du definierar hur en ny grupp av objekt visas.</span><span class="sxs-lookup"><span data-stu-id="38386-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="38386-105">Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for GroupBy (format) CustomItem-element för CustomEntry för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="38386-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="38386-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="38386-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="38386-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="38386-107">Attributes and Elements</span></span>

<span data-ttu-id="38386-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `CustomItem`-elementet.</span><span class="sxs-lookup"><span data-stu-id="38386-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="38386-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="38386-109">Attributes</span></span>

<span data-ttu-id="38386-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="38386-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="38386-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="38386-111">Child Elements</span></span>

|<span data-ttu-id="38386-112">Element</span><span class="sxs-lookup"><span data-stu-id="38386-112">Element</span></span>|<span data-ttu-id="38386-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="38386-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="38386-114">ExpressionBinding-element för CustomItem för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="38386-114">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="38386-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="38386-115">Optional element.</span></span><br /><br /> <span data-ttu-id="38386-116">Definierar de data som visas av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="38386-116">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="38386-117">Ram element för CustomItem för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="38386-117">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="38386-118">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="38386-118">Optional element.</span></span><br /><br /> <span data-ttu-id="38386-119">Definierar vilka data som visas i vyn anpassad kontroll och hur den visas.</span><span class="sxs-lookup"><span data-stu-id="38386-119">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|
|[<span data-ttu-id="38386-120">Rad matnings element för CustomItem för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="38386-120">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="38386-121">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="38386-121">Optional element.</span></span><br /><br /> <span data-ttu-id="38386-122">Lägger till en tom rad i visningen av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="38386-122">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="38386-123">Text element för CustomItem för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="38386-123">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="38386-124">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="38386-124">Optional element.</span></span><br /><br /> <span data-ttu-id="38386-125">Anger ytterligare text för de data som visas i kontrollen.</span><span class="sxs-lookup"><span data-stu-id="38386-125">Specifies additional text to the data displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="38386-126">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="38386-126">Parent Elements</span></span>

|<span data-ttu-id="38386-127">Element</span><span class="sxs-lookup"><span data-stu-id="38386-127">Element</span></span>|<span data-ttu-id="38386-128">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="38386-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="38386-129">CustomEntry-element för CustomControl för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="38386-129">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="38386-130">Innehåller en definition av den anpassade kontrollen.</span><span class="sxs-lookup"><span data-stu-id="38386-130">Provides a definition of the custom control view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="38386-131">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="38386-131">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="38386-132">Se även</span><span class="sxs-lookup"><span data-stu-id="38386-132">See Also</span></span>

[<span data-ttu-id="38386-133">CustomEntry-element för CustomControl för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="38386-133">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="38386-134">ExpressionBinding-element för CustomItem för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="38386-134">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="38386-135">Ram element för CustomItem för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="38386-135">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="38386-136">Rad matnings element för CustomItem för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="38386-136">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="38386-137">Text element för CustomItem för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="38386-137">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="38386-138">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="38386-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
