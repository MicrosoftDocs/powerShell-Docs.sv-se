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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849485"
---
# <a name="frame-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="95c3b-102">Frame-element för CustomItem för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="95c3b-102">Frame Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="95c3b-103">Definierar hur data visas, till exempel ändra datatypen till vänster eller höger.</span><span class="sxs-lookup"><span data-stu-id="95c3b-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="95c3b-104">Det här elementet används när du definierar kontroller som kan användas av en vy.</span><span class="sxs-lookup"><span data-stu-id="95c3b-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="95c3b-105">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) kontroller Element (Format) kontroll konfigurationselement för kontroller för att visa (Format) anpassad kontroll Element för kontroll för kontroller för att visa (Format) CustomEntries Element för Anpassad kontroll för Visa (Format) CustomEntry elementet för CustomEntries för kontroller för att visa (Format) CustomItem Element för CustomEntry för kontroller för att visa (Format) RAM-Element för CustomItem för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="95c3b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) Frame Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="95c3b-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="95c3b-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="95c3b-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="95c3b-107">Attributes and Elements</span></span>

<span data-ttu-id="95c3b-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `Frame` element.</span><span class="sxs-lookup"><span data-stu-id="95c3b-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="95c3b-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="95c3b-109">Attributes</span></span>

<span data-ttu-id="95c3b-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="95c3b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="95c3b-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="95c3b-111">Child Elements</span></span>

|<span data-ttu-id="95c3b-112">Element</span><span class="sxs-lookup"><span data-stu-id="95c3b-112">Element</span></span>|<span data-ttu-id="95c3b-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="95c3b-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="95c3b-114">Element som krävs</span><span class="sxs-lookup"><span data-stu-id="95c3b-114">Required Element</span></span>|
|[<span data-ttu-id="95c3b-115">FirstLineHanging Element av bildruta från kontrollerna för Visa (Format)</span><span class="sxs-lookup"><span data-stu-id="95c3b-115">FirstLineHanging Element of Frame of Controls of View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="95c3b-116">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="95c3b-116">Optional element.</span></span><br /><br /> <span data-ttu-id="95c3b-117">Anger hur många tecken som den första raden ska flyttas till vänster.</span><span class="sxs-lookup"><span data-stu-id="95c3b-117">Specifies how many characters the first line is shifted to the left.</span></span>|
|[<span data-ttu-id="95c3b-118">FirstLineIndent Element av bildruta från kontrollerna för Visa (Format)</span><span class="sxs-lookup"><span data-stu-id="95c3b-118">FirstLineIndent Element of Frame of Controls of View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="95c3b-119">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="95c3b-119">Optional element.</span></span><br /><br /> <span data-ttu-id="95c3b-120">Anger hur många tecken som den första raden ska flyttas till höger.</span><span class="sxs-lookup"><span data-stu-id="95c3b-120">Specifies how many characters the first line is shifted to the right.</span></span>|
|[<span data-ttu-id="95c3b-121">LeftIndent Element av bildruta från kontrollerna för Visa (Format)</span><span class="sxs-lookup"><span data-stu-id="95c3b-121">LeftIndent Element of Frame of Controls of View (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="95c3b-122">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="95c3b-122">Optional element.</span></span><br /><br /> <span data-ttu-id="95c3b-123">Anger hur många tecken som data ska flyttas från vänster marginal.</span><span class="sxs-lookup"><span data-stu-id="95c3b-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="95c3b-124">RightIndent Element av bildruta från kontrollerna för Visa (Format)</span><span class="sxs-lookup"><span data-stu-id="95c3b-124">RightIndent Element of Frame of Controls of View (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="95c3b-125">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="95c3b-125">Optional element.</span></span><br /><br /> <span data-ttu-id="95c3b-126">Anger hur många tecken som data ska flyttas från höger marginal.</span><span class="sxs-lookup"><span data-stu-id="95c3b-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="95c3b-127">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="95c3b-127">Parent Elements</span></span>

|<span data-ttu-id="95c3b-128">Element</span><span class="sxs-lookup"><span data-stu-id="95c3b-128">Element</span></span>|<span data-ttu-id="95c3b-129">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="95c3b-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="95c3b-130">CustomItem Element för CustomEntry för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="95c3b-130">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="95c3b-131">Definierar vilka data som visas av kontrollen och hur de visas.</span><span class="sxs-lookup"><span data-stu-id="95c3b-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="95c3b-132">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="95c3b-132">Remarks</span></span>

<span data-ttu-id="95c3b-133">Du kan inte ange den [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) och [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) element i samma `Frame` element.</span><span class="sxs-lookup"><span data-stu-id="95c3b-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="95c3b-134">Se även</span><span class="sxs-lookup"><span data-stu-id="95c3b-134">See Also</span></span>

[<span data-ttu-id="95c3b-135">FirstLineHanging Element av bildruta från kontrollerna för Visa (Format)</span><span class="sxs-lookup"><span data-stu-id="95c3b-135">FirstLineHanging Element of Frame of Controls of View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="95c3b-136">FirstLineIndent Element av bildruta från kontrollerna för Visa (Format)</span><span class="sxs-lookup"><span data-stu-id="95c3b-136">FirstLineIndent Element of Frame of Controls of View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="95c3b-137">LeftIndent Element av bildruta från kontrollerna för Visa (Format)</span><span class="sxs-lookup"><span data-stu-id="95c3b-137">LeftIndent Element of Frame of Controls of View (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="95c3b-138">RightIndent Element av bildruta från kontrollerna för Visa (Format)</span><span class="sxs-lookup"><span data-stu-id="95c3b-138">RightIndent Element of Frame of Controls of View (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="95c3b-139">CustomItem Element för CustomEntry för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="95c3b-139">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="95c3b-140">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="95c3b-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
