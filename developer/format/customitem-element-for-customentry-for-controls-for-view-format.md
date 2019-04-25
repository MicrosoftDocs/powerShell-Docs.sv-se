---
title: CustomItem Element för CustomEntry för kontroller för att visa (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33cb5350-73ef-4b79-a879-0edf051869e4
caps.latest.revision: 7
ms.openlocfilehash: 174ba6a14819f823ec39f72e49a626e781221d8c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066389"
---
# <a name="customitem-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="88542-102">CustomItem-element för CustomEntry för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="88542-102">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="88542-103">Definierar vilka data som visas av kontrollen och hur de visas.</span><span class="sxs-lookup"><span data-stu-id="88542-103">Defines what data is displayed by the control and how it is displayed.</span></span> <span data-ttu-id="88542-104">Det här elementet används när du definierar kontroller som kan användas av en vy.</span><span class="sxs-lookup"><span data-stu-id="88542-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="88542-105">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) kontroller Element (Format) kontroll konfigurationselement för kontroller för att visa (Format) anpassad kontroll Element för kontroll för kontroller för att visa (Format) CustomEntries Element för Anpassad kontroll för Visa (Format) CustomEntry elementet för CustomEntries för kontroller för att visa (Format) CustomItem Element för CustomEntry för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="88542-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="88542-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="88542-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...<Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="88542-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="88542-107">Attributes and Elements</span></span>

<span data-ttu-id="88542-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `CustomItem` element.</span><span class="sxs-lookup"><span data-stu-id="88542-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span> <span data-ttu-id="88542-109">Mer information finns i kommentarer.</span><span class="sxs-lookup"><span data-stu-id="88542-109">For more information, see Remarks.</span></span>

### <a name="attributes"></a><span data-ttu-id="88542-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="88542-110">Attributes</span></span>

<span data-ttu-id="88542-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="88542-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="88542-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="88542-112">Child Elements</span></span>

|<span data-ttu-id="88542-113">Element</span><span class="sxs-lookup"><span data-stu-id="88542-113">Element</span></span>|<span data-ttu-id="88542-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="88542-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="88542-115">ExpressionBinding Element för CustomItem för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="88542-115">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="88542-116">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="88542-116">Optional element.</span></span><br /><br /> <span data-ttu-id="88542-117">Definierar de data som visas i kontrollen.</span><span class="sxs-lookup"><span data-stu-id="88542-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="88542-118">Ramens Element för CustomItem för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="88542-118">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="88542-119">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="88542-119">Optional element.</span></span><br /><br /> <span data-ttu-id="88542-120">Definierar hur data visas, till exempel ändra datatypen till vänster eller höger.</span><span class="sxs-lookup"><span data-stu-id="88542-120">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|
|[<span data-ttu-id="88542-121">Ny rad-Element för CustomItem för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="88542-121">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="88542-122">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="88542-122">Optional element.</span></span><br /><br /> <span data-ttu-id="88542-123">Lägger till en tom rad visningen av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="88542-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="88542-124">Textelement för CustomItem för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="88542-124">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="88542-125">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="88542-125">Optional element.</span></span><br /><br /> <span data-ttu-id="88542-126">Lägger till text, till exempel parenteser eller hakparenteser, visning av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="88542-126">Adds text, such as parentheses or brackets, to the display of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="88542-127">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="88542-127">Parent Elements</span></span>

|<span data-ttu-id="88542-128">Element</span><span class="sxs-lookup"><span data-stu-id="88542-128">Element</span></span>|<span data-ttu-id="88542-129">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="88542-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="88542-130">CustomEntry Element för CustomEntries för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="88542-130">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="88542-131">Innehåller en definition av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="88542-131">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="88542-132">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="88542-132">Remarks</span></span>

<span data-ttu-id="88542-133">När du anger de underordnade elementen i den `CustomItem` element, Tänk på följande:</span><span class="sxs-lookup"><span data-stu-id="88542-133">When specifying the child elements of the `CustomItem` element, keep the following in mind:</span></span>

- <span data-ttu-id="88542-134">De underordnade elementen måste läggas till i följande ordning: `ExpressionBinding`, `NewLine`, `Text`, och `Frame`.</span><span class="sxs-lookup"><span data-stu-id="88542-134">The child elements must be added in the following sequence: `ExpressionBinding`, `NewLine`, `Text`, and `Frame`.</span></span>

- <span data-ttu-id="88542-135">Det finns ingen högsta gräns för antalet sekvenser som du kan ange.</span><span class="sxs-lookup"><span data-stu-id="88542-135">There is no maximum limit to the number of sequences that you can specify.</span></span>

- <span data-ttu-id="88542-136">Det finns ingen högsta gräns för antalet i varje sekvens `ExpressionBinding` element som du kan använda.</span><span class="sxs-lookup"><span data-stu-id="88542-136">In each sequence, there is no maximum limit to the number of `ExpressionBinding` elements that you can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="88542-137">Se även</span><span class="sxs-lookup"><span data-stu-id="88542-137">See Also</span></span>

[<span data-ttu-id="88542-138">ExpressionBinding Element för CustomItem för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="88542-138">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="88542-139">Ramens Element för CustomItem för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="88542-139">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="88542-140">Ny rad-Element för CustomItem för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="88542-140">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="88542-141">Textelement för CustomItem för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="88542-141">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="88542-142">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="88542-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
