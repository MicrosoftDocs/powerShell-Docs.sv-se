---
title: RAM-Element för CustomItem för kontroller för vy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a5729091-78a9-4bc1-abac-210bc20c6dbe
caps.latest.revision: 7
ms.openlocfilehash: f93dc20a9c5f87c14605578062b1e60f5a3d25cf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065724"
---
# <a name="frame-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="09f35-102">Frame-element för CustomItem för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="09f35-102">Frame Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="09f35-103">Definierar hur data visas, till exempel ändra datatypen till vänster eller höger.</span><span class="sxs-lookup"><span data-stu-id="09f35-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="09f35-104">Det här elementet används när du definierar kontroller som kan användas av en vy.</span><span class="sxs-lookup"><span data-stu-id="09f35-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="09f35-105">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) kontroller Element (Format) kontroll konfigurationselement för kontroller för att visa (Format) anpassad kontroll Element för kontroll för kontroller för att visa (Format) CustomEntries Element för Anpassad kontroll för Visa (Format) CustomEntry elementet för CustomEntries för kontroller för att visa (Format) CustomItem Element för CustomEntry för kontroller för att visa (Format) RAM-Element för CustomItem för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="09f35-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) Frame Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="09f35-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="09f35-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="09f35-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="09f35-107">Attributes and Elements</span></span>

<span data-ttu-id="09f35-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `Frame` element.</span><span class="sxs-lookup"><span data-stu-id="09f35-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="09f35-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="09f35-109">Attributes</span></span>

<span data-ttu-id="09f35-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="09f35-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="09f35-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="09f35-111">Child Elements</span></span>

|<span data-ttu-id="09f35-112">Element</span><span class="sxs-lookup"><span data-stu-id="09f35-112">Element</span></span>|<span data-ttu-id="09f35-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="09f35-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="09f35-114">Element som krävs</span><span class="sxs-lookup"><span data-stu-id="09f35-114">Required Element</span></span>|
|[<span data-ttu-id="09f35-115">FirstLineHanging Element av bildruta från kontrollerna för Visa (Format)</span><span class="sxs-lookup"><span data-stu-id="09f35-115">FirstLineHanging Element of Frame of Controls of View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="09f35-116">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="09f35-116">Optional element.</span></span><br /><br /> <span data-ttu-id="09f35-117">Anger hur många tecken som den första raden ska flyttas till vänster.</span><span class="sxs-lookup"><span data-stu-id="09f35-117">Specifies how many characters the first line is shifted to the left.</span></span>|
|[<span data-ttu-id="09f35-118">FirstLineIndent Element av bildruta från kontrollerna för Visa (Format)</span><span class="sxs-lookup"><span data-stu-id="09f35-118">FirstLineIndent Element of Frame of Controls of View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="09f35-119">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="09f35-119">Optional element.</span></span><br /><br /> <span data-ttu-id="09f35-120">Anger hur många tecken som den första raden ska flyttas till höger.</span><span class="sxs-lookup"><span data-stu-id="09f35-120">Specifies how many characters the first line is shifted to the right.</span></span>|
|[<span data-ttu-id="09f35-121">LeftIndent Element av bildruta från kontrollerna för Visa (Format)</span><span class="sxs-lookup"><span data-stu-id="09f35-121">LeftIndent Element of Frame of Controls of View (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="09f35-122">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="09f35-122">Optional element.</span></span><br /><br /> <span data-ttu-id="09f35-123">Anger hur många tecken som data ska flyttas från vänster marginal.</span><span class="sxs-lookup"><span data-stu-id="09f35-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="09f35-124">RightIndent Element av bildruta från kontrollerna för Visa (Format)</span><span class="sxs-lookup"><span data-stu-id="09f35-124">RightIndent Element of Frame of Controls of View (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="09f35-125">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="09f35-125">Optional element.</span></span><br /><br /> <span data-ttu-id="09f35-126">Anger hur många tecken som data ska flyttas från höger marginal.</span><span class="sxs-lookup"><span data-stu-id="09f35-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="09f35-127">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="09f35-127">Parent Elements</span></span>

|<span data-ttu-id="09f35-128">Element</span><span class="sxs-lookup"><span data-stu-id="09f35-128">Element</span></span>|<span data-ttu-id="09f35-129">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="09f35-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="09f35-130">CustomItem Element för CustomEntry för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="09f35-130">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="09f35-131">Definierar vilka data som visas av kontrollen och hur de visas.</span><span class="sxs-lookup"><span data-stu-id="09f35-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="09f35-132">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="09f35-132">Remarks</span></span>

<span data-ttu-id="09f35-133">Du kan inte ange den [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) och [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) element i samma `Frame` element.</span><span class="sxs-lookup"><span data-stu-id="09f35-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="09f35-134">Se även</span><span class="sxs-lookup"><span data-stu-id="09f35-134">See Also</span></span>

[<span data-ttu-id="09f35-135">FirstLineHanging Element av bildruta från kontrollerna för Visa (Format)</span><span class="sxs-lookup"><span data-stu-id="09f35-135">FirstLineHanging Element of Frame of Controls of View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="09f35-136">FirstLineIndent Element av bildruta från kontrollerna för Visa (Format)</span><span class="sxs-lookup"><span data-stu-id="09f35-136">FirstLineIndent Element of Frame of Controls of View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="09f35-137">LeftIndent Element av bildruta från kontrollerna för Visa (Format)</span><span class="sxs-lookup"><span data-stu-id="09f35-137">LeftIndent Element of Frame of Controls of View (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="09f35-138">RightIndent Element av bildruta från kontrollerna för Visa (Format)</span><span class="sxs-lookup"><span data-stu-id="09f35-138">RightIndent Element of Frame of Controls of View (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="09f35-139">CustomItem Element för CustomEntry för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="09f35-139">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="09f35-140">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="09f35-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
