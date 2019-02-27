---
title: CustomItem Element för CustomEntry för kontroller för konfiguration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73fb11ee-0ebd-477a-ac36-acdfbb32e70d
caps.latest.revision: 7
ms.openlocfilehash: bd0cb69770817ec215ddb1862a43a838baddefcf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851669"
---
# <a name="customitem-element-for-customentry-for-controls-for-configuration-format"></a><span data-ttu-id="3967f-102">CustomItem-element för CustomEntry för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="3967f-102">CustomItem Element for CustomEntry for Controls for Configuration (Format)</span></span>

<span data-ttu-id="3967f-103">Definierar vilka data som visas av kontrollen och hur de visas.</span><span class="sxs-lookup"><span data-stu-id="3967f-103">Defines what data is displayed by the control and how it is displayed.</span></span> <span data-ttu-id="3967f-104">Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.</span><span class="sxs-lookup"><span data-stu-id="3967f-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="3967f-105">Konfigurationselementet Element (Format) kontroller av (Format) kontroll konfigurationselement för kontroller för (Format) anpassad kontroll konfigurationselement för kontroll för (Format) CustomEntries konfigurationselement för anpassad kontroll för konfiguration ( Format) CustomEntry Element för anpassad kontroll för kontroller för (Format) CustomItem konfigurationselement för CustomEntry för kontroller för konfiguration</span><span class="sxs-lookup"><span data-stu-id="3967f-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration</span></span>

## <a name="syntax"></a><span data-ttu-id="3967f-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="3967f-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...</Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3967f-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="3967f-107">Attributes and Elements</span></span>

<span data-ttu-id="3967f-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `CustomItem` element.</span><span class="sxs-lookup"><span data-stu-id="3967f-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span> <span data-ttu-id="3967f-109">Mer information finns i kommentarer.</span><span class="sxs-lookup"><span data-stu-id="3967f-109">For more information, see Remarks.</span></span>

### <a name="attributes"></a><span data-ttu-id="3967f-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="3967f-110">Attributes</span></span>

<span data-ttu-id="3967f-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="3967f-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3967f-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="3967f-112">Child Elements</span></span>

|<span data-ttu-id="3967f-113">Element</span><span class="sxs-lookup"><span data-stu-id="3967f-113">Element</span></span>|<span data-ttu-id="3967f-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="3967f-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3967f-115">ExpressionBinding Element för CustomItem för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="3967f-115">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="3967f-116">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="3967f-116">Optional element.</span></span><br /><br /> <span data-ttu-id="3967f-117">Definierar de data som visas i kontrollen.</span><span class="sxs-lookup"><span data-stu-id="3967f-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="3967f-118">Ramens Element för CustomItem för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="3967f-118">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="3967f-119">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="3967f-119">Optional element.</span></span><br /><br /> <span data-ttu-id="3967f-120">Definierar hur data visas, till exempel ändra datatypen till vänster eller höger.</span><span class="sxs-lookup"><span data-stu-id="3967f-120">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|
|[<span data-ttu-id="3967f-121">Ny rad-Element för CustomItem för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="3967f-121">NewLine Element for CustomItem for Controls for Configuration (Format)</span></span>](./newline-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="3967f-122">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="3967f-122">Optional element.</span></span><br /><br /> <span data-ttu-id="3967f-123">Lägger till en tom rad visningen av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="3967f-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="3967f-124">Textelement för CustomItem för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="3967f-124">Text Element for CustomItem for Controls for Configuration (Format)</span></span>](./text-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="3967f-125">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="3967f-125">Optional element.</span></span><br /><br /> <span data-ttu-id="3967f-126">Lägger till text, till exempel parenteser eller hakparenteser, visning av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="3967f-126">Adds text, such as parentheses or brackets, to the display of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3967f-127">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="3967f-127">Parent Elements</span></span>

|<span data-ttu-id="3967f-128">Element</span><span class="sxs-lookup"><span data-stu-id="3967f-128">Element</span></span>|<span data-ttu-id="3967f-129">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="3967f-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3967f-130">CustomEntry Element för anpassad kontroll för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="3967f-130">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="3967f-131">Innehåller en definition av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="3967f-131">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3967f-132">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="3967f-132">Remarks</span></span>

<span data-ttu-id="3967f-133">När du anger de underordnade elementen i den `CustomItem` element, Tänk på följande:</span><span class="sxs-lookup"><span data-stu-id="3967f-133">When specifying the child elements of the `CustomItem` element, keep the following in mind:</span></span>

- <span data-ttu-id="3967f-134">De underordnade elementen måste läggas till i följande ordning: `ExpressionBinding`, `NewLine`, `Text`, och `Frame`.</span><span class="sxs-lookup"><span data-stu-id="3967f-134">The child elements must be added in the following sequence: `ExpressionBinding`, `NewLine`, `Text`, and `Frame`.</span></span>

- <span data-ttu-id="3967f-135">Det finns ingen högsta gräns för antalet sekvenser som du kan ange.</span><span class="sxs-lookup"><span data-stu-id="3967f-135">There is no maximum limit to the number of sequences that you can specify.</span></span>

- <span data-ttu-id="3967f-136">Det finns ingen högsta gräns för antalet i varje sekvens `ExpressionBinding` element som du kan använda.</span><span class="sxs-lookup"><span data-stu-id="3967f-136">In each sequence, there is no maximum limit to the number of `ExpressionBinding` elements that you can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="3967f-137">Se även</span><span class="sxs-lookup"><span data-stu-id="3967f-137">See Also</span></span>

[<span data-ttu-id="3967f-138">ExpressionBinding Element för CustomItem för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="3967f-138">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="3967f-139">Ramens Element för CustomItem för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="3967f-139">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="3967f-140">Ny rad-Element för CustomItem för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="3967f-140">NewLine Element for CustomItem for Controls for Configuration (Format)</span></span>](./newline-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="3967f-141">Textelement för CustomItem för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="3967f-141">Text Element for CustomItem for Controls for Configuration (Format)</span></span>](./text-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="3967f-142">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="3967f-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
