---
title: CustomItem-element för CustomEntry för kontroller för vy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33cb5350-73ef-4b79-a879-0edf051869e4
caps.latest.revision: 7
ms.openlocfilehash: 174ba6a14819f823ec39f72e49a626e781221d8c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355183"
---
# <a name="customitem-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="2bd3b-102">CustomItem-element för CustomEntry för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="2bd3b-102">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="2bd3b-103">Definierar vilka data som visas av kontrollen och hur de visas.</span><span class="sxs-lookup"><span data-stu-id="2bd3b-103">Defines what data is displayed by the control and how it is displayed.</span></span> <span data-ttu-id="2bd3b-104">Det här elementet används när du definierar kontroller som kan användas av en vy.</span><span class="sxs-lookup"><span data-stu-id="2bd3b-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="2bd3b-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) styr element (format) styr element (format) styr element för Controls (format) CustomControl-element för kontroll för Control for View (format) CustomEntries-element för CustomControl för visnings-(format) CustomEntry-element för CustomEntries för Controls för View (format) CustomItem-elementet för CustomEntry för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="2bd3b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2bd3b-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="2bd3b-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...<Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2bd3b-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="2bd3b-107">Attributes and Elements</span></span>

<span data-ttu-id="2bd3b-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `CustomItem`-elementet.</span><span class="sxs-lookup"><span data-stu-id="2bd3b-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span> <span data-ttu-id="2bd3b-109">Mer information finns i kommentarer.</span><span class="sxs-lookup"><span data-stu-id="2bd3b-109">For more information, see Remarks.</span></span>

### <a name="attributes"></a><span data-ttu-id="2bd3b-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="2bd3b-110">Attributes</span></span>

<span data-ttu-id="2bd3b-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="2bd3b-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2bd3b-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="2bd3b-112">Child Elements</span></span>

|<span data-ttu-id="2bd3b-113">Element</span><span class="sxs-lookup"><span data-stu-id="2bd3b-113">Element</span></span>|<span data-ttu-id="2bd3b-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="2bd3b-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2bd3b-115">ExpressionBinding-element för CustomItem för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="2bd3b-115">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="2bd3b-116">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="2bd3b-116">Optional element.</span></span><br /><br /> <span data-ttu-id="2bd3b-117">Definierar de data som visas av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="2bd3b-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="2bd3b-118">Ram element för CustomItem för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="2bd3b-118">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="2bd3b-119">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="2bd3b-119">Optional element.</span></span><br /><br /> <span data-ttu-id="2bd3b-120">Definierar hur data visas, till exempel att flytta data till vänster eller höger.</span><span class="sxs-lookup"><span data-stu-id="2bd3b-120">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|
|[<span data-ttu-id="2bd3b-121">Rad matnings element för CustomItem för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="2bd3b-121">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="2bd3b-122">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="2bd3b-122">Optional element.</span></span><br /><br /> <span data-ttu-id="2bd3b-123">Lägger till en tom rad i visningen av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="2bd3b-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="2bd3b-124">Text element för CustomItem för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="2bd3b-124">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="2bd3b-125">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="2bd3b-125">Optional element.</span></span><br /><br /> <span data-ttu-id="2bd3b-126">Lägger till text, till exempel parenteser eller hakparenteser, för att Visa kontrollen.</span><span class="sxs-lookup"><span data-stu-id="2bd3b-126">Adds text, such as parentheses or brackets, to the display of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2bd3b-127">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="2bd3b-127">Parent Elements</span></span>

|<span data-ttu-id="2bd3b-128">Element</span><span class="sxs-lookup"><span data-stu-id="2bd3b-128">Element</span></span>|<span data-ttu-id="2bd3b-129">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="2bd3b-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2bd3b-130">CustomEntry-element för CustomEntries för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="2bd3b-130">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="2bd3b-131">Ger en definition av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="2bd3b-131">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2bd3b-132">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="2bd3b-132">Remarks</span></span>

<span data-ttu-id="2bd3b-133">Tänk på följande när du anger underordnade element för `CustomItem`-elementet:</span><span class="sxs-lookup"><span data-stu-id="2bd3b-133">When specifying the child elements of the `CustomItem` element, keep the following in mind:</span></span>

- <span data-ttu-id="2bd3b-134">De underordnade elementen måste läggas till i följande ordning: `ExpressionBinding`, `NewLine`, `Text`och `Frame`.</span><span class="sxs-lookup"><span data-stu-id="2bd3b-134">The child elements must be added in the following sequence: `ExpressionBinding`, `NewLine`, `Text`, and `Frame`.</span></span>

- <span data-ttu-id="2bd3b-135">Det finns ingen övre gräns för antalet sekvenser som du kan ange.</span><span class="sxs-lookup"><span data-stu-id="2bd3b-135">There is no maximum limit to the number of sequences that you can specify.</span></span>

- <span data-ttu-id="2bd3b-136">I varje sekvens finns det ingen övre gräns för antalet `ExpressionBinding`-element som du kan använda.</span><span class="sxs-lookup"><span data-stu-id="2bd3b-136">In each sequence, there is no maximum limit to the number of `ExpressionBinding` elements that you can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="2bd3b-137">Se även</span><span class="sxs-lookup"><span data-stu-id="2bd3b-137">See Also</span></span>

[<span data-ttu-id="2bd3b-138">ExpressionBinding-element för CustomItem för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="2bd3b-138">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="2bd3b-139">Ram element för CustomItem för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="2bd3b-139">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="2bd3b-140">Rad matnings element för CustomItem för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="2bd3b-140">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="2bd3b-141">Text element för CustomItem för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="2bd3b-141">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="2bd3b-142">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="2bd3b-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
