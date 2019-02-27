---
title: CustomItem Element för CustomEntry för anpassad kontroll för vy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98708c1d-6f39-4a76-b454-31153a6ade8c
caps.latest.revision: 12
ms.openlocfilehash: 3c110bd5fe3ef2f790ef136556afa7c29d0b5b29
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846944"
---
# <a name="customitem-element-for-customentry-for-customcontrol-for-view-format"></a><span data-ttu-id="36199-102">CustomItem-element för CustomEntry för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="36199-102">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>

<span data-ttu-id="36199-103">Definierar vilka data som visas i vyn anpassad kontroll och hur de visas.</span><span class="sxs-lookup"><span data-stu-id="36199-103">Defines what data is displayed by the custom control view and how it is displayed.</span></span> <span data-ttu-id="36199-104">Det här elementet används när du definierar en anpassad kontroll vy.</span><span class="sxs-lookup"><span data-stu-id="36199-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="36199-105">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) anpassad kontroll Element (Format) CustomEntries konfigurationselement för anpassad kontroll för Visa (Format) CustomEntry elementet för CustomEntries för vyn (Format) CustomItem elementet för CustomEntry för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="36199-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="36199-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="36199-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="36199-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="36199-107">Attributes and Elements</span></span>

<span data-ttu-id="36199-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `CustomItem` element.</span><span class="sxs-lookup"><span data-stu-id="36199-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="36199-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="36199-109">Attributes</span></span>

<span data-ttu-id="36199-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="36199-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="36199-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="36199-111">Child Elements</span></span>

|<span data-ttu-id="36199-112">Element</span><span class="sxs-lookup"><span data-stu-id="36199-112">Element</span></span>|<span data-ttu-id="36199-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="36199-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="36199-114">ExpressionBinding Element för CustomItem för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="36199-114">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="36199-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="36199-115">Optional element.</span></span><br /><br /> <span data-ttu-id="36199-116">Definierar de data som visas i kontrollen.</span><span class="sxs-lookup"><span data-stu-id="36199-116">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="36199-117">Ramens Element för CustomItem för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="36199-117">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="36199-118">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="36199-118">Optional element.</span></span><br /><br /> <span data-ttu-id="36199-119">Definierar vilka data som visas i vyn anpassad kontroll och hur de visas.</span><span class="sxs-lookup"><span data-stu-id="36199-119">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|
|[<span data-ttu-id="36199-120">Ny rad-Element för CustomItem för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="36199-120">NewLine Element for CustomItem for Custom Control for View (Format)</span></span>](./newline-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="36199-121">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="36199-121">Optional element.</span></span><br /><br /> <span data-ttu-id="36199-122">Lägger till en tom rad visningen av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="36199-122">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="36199-123">Textelement för CustomItem för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="36199-123">Text Element for CustomItem for CustomControl for View (Format)</span></span>](./text-element-for-customitem-for-customview-for-view-format.md)|<span data-ttu-id="36199-124">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="36199-124">Optional element.</span></span><br /><br /> <span data-ttu-id="36199-125">Anger ytterligare text till data som visas i kontrollen.</span><span class="sxs-lookup"><span data-stu-id="36199-125">Specifies additional text to the data displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="36199-126">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="36199-126">Parent Elements</span></span>

|<span data-ttu-id="36199-127">Element</span><span class="sxs-lookup"><span data-stu-id="36199-127">Element</span></span>|<span data-ttu-id="36199-128">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="36199-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="36199-129">CustomEntry Element för CustomEntries för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="36199-129">CustomEntry Element for CustomEntries for CustomControl for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="36199-130">Innehåller en definition av vyn anpassad kontroll.</span><span class="sxs-lookup"><span data-stu-id="36199-130">Provides a definition of the custom control view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="36199-131">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="36199-131">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="36199-132">Se även</span><span class="sxs-lookup"><span data-stu-id="36199-132">See Also</span></span>

[<span data-ttu-id="36199-133">CustomEntry Element för CustomEntries för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="36199-133">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="36199-134">ExpressionBinding Element för CustomItem för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="36199-134">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="36199-135">Ramens Element för CustomItem för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="36199-135">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="36199-136">Ny rad-Element för CustomItem för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="36199-136">NewLine Element for CustomItem for CustomControl for View (Format)</span></span>](./newline-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="36199-137">Textelement för CustomItem för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="36199-137">Text Element for CustomItem for CustomControl for View (Format)</span></span>](./text-element-for-customitem-for-customview-for-view-format.md)

[<span data-ttu-id="36199-138">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="36199-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
