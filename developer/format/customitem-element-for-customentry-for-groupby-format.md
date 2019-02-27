---
title: CustomItem Element för CustomEntry för GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7c517aa-24f5-41ae-b82d-cb0fac81a245
caps.latest.revision: 7
ms.openlocfilehash: 2d821f5e3bc8d0f81ef8a8a040c6f9bcb1658bee
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847462"
---
# <a name="customitem-element-for-customentry-for-groupby-format"></a><span data-ttu-id="f956f-102">CustomItem-element för CustomEntry för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="f956f-102">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="f956f-103">Definierar vilka data som visas i vyn anpassad kontroll och hur de visas.</span><span class="sxs-lookup"><span data-stu-id="f956f-103">Defines what data is displayed by the custom control view and how it is displayed.</span></span> <span data-ttu-id="f956f-104">Det här elementet används när du definierar hur en ny grupp med objekt visas.</span><span class="sxs-lookup"><span data-stu-id="f956f-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="f956f-105">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) GroupBy konfigurationselement för Visa (Format) anpassad kontroll elementet för GroupBy (Format) CustomEntries Element för anpassad kontroll för GroupBy (Format) CustomItem elementet för CustomEntry för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="f956f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f956f-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="f956f-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f956f-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="f956f-107">Attributes and Elements</span></span>

<span data-ttu-id="f956f-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `CustomItem` element.</span><span class="sxs-lookup"><span data-stu-id="f956f-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f956f-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="f956f-109">Attributes</span></span>

<span data-ttu-id="f956f-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="f956f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f956f-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="f956f-111">Child Elements</span></span>

|<span data-ttu-id="f956f-112">Element</span><span class="sxs-lookup"><span data-stu-id="f956f-112">Element</span></span>|<span data-ttu-id="f956f-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f956f-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f956f-114">ExpressionBinding Element för CustomItem för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="f956f-114">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="f956f-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="f956f-115">Optional element.</span></span><br /><br /> <span data-ttu-id="f956f-116">Definierar de data som visas i kontrollen.</span><span class="sxs-lookup"><span data-stu-id="f956f-116">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="f956f-117">Ramens Element för CustomItem för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="f956f-117">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="f956f-118">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="f956f-118">Optional element.</span></span><br /><br /> <span data-ttu-id="f956f-119">Definierar vilka data som visas i vyn anpassad kontroll och hur de visas.</span><span class="sxs-lookup"><span data-stu-id="f956f-119">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|
|[<span data-ttu-id="f956f-120">Ny rad-Element för CustomItem för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="f956f-120">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="f956f-121">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="f956f-121">Optional element.</span></span><br /><br /> <span data-ttu-id="f956f-122">Lägger till en tom rad visningen av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="f956f-122">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="f956f-123">Textelement för CustomItem för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="f956f-123">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="f956f-124">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="f956f-124">Optional element.</span></span><br /><br /> <span data-ttu-id="f956f-125">Anger ytterligare text till data som visas i kontrollen.</span><span class="sxs-lookup"><span data-stu-id="f956f-125">Specifies additional text to the data displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f956f-126">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="f956f-126">Parent Elements</span></span>

|<span data-ttu-id="f956f-127">Element</span><span class="sxs-lookup"><span data-stu-id="f956f-127">Element</span></span>|<span data-ttu-id="f956f-128">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f956f-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f956f-129">CustomEntry Element för anpassad kontroll för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="f956f-129">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="f956f-130">Innehåller en definition av vyn anpassad kontroll.</span><span class="sxs-lookup"><span data-stu-id="f956f-130">Provides a definition of the custom control view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f956f-131">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="f956f-131">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="f956f-132">Se även</span><span class="sxs-lookup"><span data-stu-id="f956f-132">See Also</span></span>

[<span data-ttu-id="f956f-133">CustomEntry Element för anpassad kontroll för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="f956f-133">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="f956f-134">ExpressionBinding Element för CustomItem för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="f956f-134">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="f956f-135">Ramens Element för CustomItem för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="f956f-135">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="f956f-136">Ny rad-Element för CustomItem för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="f956f-136">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="f956f-137">Textelement för CustomItem för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="f956f-137">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="f956f-138">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="f956f-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
