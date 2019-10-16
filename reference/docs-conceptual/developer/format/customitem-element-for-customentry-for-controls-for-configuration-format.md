---
title: CustomItem-element för CustomEntry för kontroll av konfiguration (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73fb11ee-0ebd-477a-ac36-acdfbb32e70d
caps.latest.revision: 7
ms.openlocfilehash: bd0cb69770817ec215ddb1862a43a838baddefcf
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355246"
---
# <a name="customitem-element-for-customentry-for-controls-for-configuration-format"></a><span data-ttu-id="27321-102">CustomItem-element för CustomEntry för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="27321-102">CustomItem Element for CustomEntry for Controls for Configuration (Format)</span></span>

<span data-ttu-id="27321-103">Definierar vilka data som visas av kontrollen och hur de visas.</span><span class="sxs-lookup"><span data-stu-id="27321-103">Defines what data is displayed by the control and how it is displayed.</span></span> <span data-ttu-id="27321-104">Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.</span><span class="sxs-lookup"><span data-stu-id="27321-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="27321-105">Konfigurations element (format) styr element i konfigurations-(format) kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för konfiguration ( Format) CustomEntry-element för CustomControl for Controls for Configuration (format) CustomItem-element för CustomEntry för kontroller för konfiguration</span><span class="sxs-lookup"><span data-stu-id="27321-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration</span></span>

## <a name="syntax"></a><span data-ttu-id="27321-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="27321-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...</Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="27321-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="27321-107">Attributes and Elements</span></span>

<span data-ttu-id="27321-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för elementet `CustomItem`.</span><span class="sxs-lookup"><span data-stu-id="27321-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span> <span data-ttu-id="27321-109">Mer information finns i kommentarer.</span><span class="sxs-lookup"><span data-stu-id="27321-109">For more information, see Remarks.</span></span>

### <a name="attributes"></a><span data-ttu-id="27321-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="27321-110">Attributes</span></span>

<span data-ttu-id="27321-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="27321-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="27321-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="27321-112">Child Elements</span></span>

|<span data-ttu-id="27321-113">Element</span><span class="sxs-lookup"><span data-stu-id="27321-113">Element</span></span>|<span data-ttu-id="27321-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="27321-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="27321-115">ExpressionBinding-element för CustomItem för kontroller för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="27321-115">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="27321-116">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="27321-116">Optional element.</span></span><br /><br /> <span data-ttu-id="27321-117">Definierar de data som visas av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="27321-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="27321-118">Ram element för CustomItem för kontroll av konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="27321-118">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="27321-119">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="27321-119">Optional element.</span></span><br /><br /> <span data-ttu-id="27321-120">Definierar hur data visas, till exempel att flytta data till vänster eller höger.</span><span class="sxs-lookup"><span data-stu-id="27321-120">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|
|[<span data-ttu-id="27321-121">Rad matnings element för CustomItem för kontroll av konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="27321-121">NewLine Element for CustomItem for Controls for Configuration (Format)</span></span>](./newline-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="27321-122">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="27321-122">Optional element.</span></span><br /><br /> <span data-ttu-id="27321-123">Lägger till en tom rad i visningen av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="27321-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="27321-124">Text element för CustomItem för konfigurations kontroller (format)</span><span class="sxs-lookup"><span data-stu-id="27321-124">Text Element for CustomItem for Controls for Configuration (Format)</span></span>](./text-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="27321-125">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="27321-125">Optional element.</span></span><br /><br /> <span data-ttu-id="27321-126">Lägger till text, till exempel parenteser eller hakparenteser, för att Visa kontrollen.</span><span class="sxs-lookup"><span data-stu-id="27321-126">Adds text, such as parentheses or brackets, to the display of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="27321-127">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="27321-127">Parent Elements</span></span>

|<span data-ttu-id="27321-128">Element</span><span class="sxs-lookup"><span data-stu-id="27321-128">Element</span></span>|<span data-ttu-id="27321-129">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="27321-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="27321-130">CustomEntry-element för CustomControl för kontroller för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="27321-130">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="27321-131">Ger en definition av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="27321-131">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="27321-132">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="27321-132">Remarks</span></span>

<span data-ttu-id="27321-133">Tänk på följande när du anger underordnade element i `CustomItem`-elementet:</span><span class="sxs-lookup"><span data-stu-id="27321-133">When specifying the child elements of the `CustomItem` element, keep the following in mind:</span></span>

- <span data-ttu-id="27321-134">De underordnade elementen måste läggas till i följande ordning: `ExpressionBinding`, `NewLine`, `Text` och `Frame`.</span><span class="sxs-lookup"><span data-stu-id="27321-134">The child elements must be added in the following sequence: `ExpressionBinding`, `NewLine`, `Text`, and `Frame`.</span></span>

- <span data-ttu-id="27321-135">Det finns ingen övre gräns för antalet sekvenser som du kan ange.</span><span class="sxs-lookup"><span data-stu-id="27321-135">There is no maximum limit to the number of sequences that you can specify.</span></span>

- <span data-ttu-id="27321-136">I varje sekvens finns det ingen övre gräns för antalet `ExpressionBinding`-element som du kan använda.</span><span class="sxs-lookup"><span data-stu-id="27321-136">In each sequence, there is no maximum limit to the number of `ExpressionBinding` elements that you can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="27321-137">Se även</span><span class="sxs-lookup"><span data-stu-id="27321-137">See Also</span></span>

[<span data-ttu-id="27321-138">ExpressionBinding-element för CustomItem för kontroller för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="27321-138">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="27321-139">Ram element för CustomItem för kontroll av konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="27321-139">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="27321-140">Rad matnings element för CustomItem för kontroll av konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="27321-140">NewLine Element for CustomItem for Controls for Configuration (Format)</span></span>](./newline-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="27321-141">Text element för CustomItem för konfigurations kontroller (format)</span><span class="sxs-lookup"><span data-stu-id="27321-141">Text Element for CustomItem for Controls for Configuration (Format)</span></span>](./text-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="27321-142">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="27321-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
