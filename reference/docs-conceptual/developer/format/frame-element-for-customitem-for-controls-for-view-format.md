---
title: Ram element för CustomItem för kontroller för vy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a5729091-78a9-4bc1-abac-210bc20c6dbe
caps.latest.revision: 7
ms.openlocfilehash: f93dc20a9c5f87c14605578062b1e60f5a3d25cf
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354980"
---
# <a name="frame-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="28cd3-102">Frame-element för CustomItem för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="28cd3-102">Frame Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="28cd3-103">Definierar hur data visas, till exempel att flytta data till vänster eller höger.</span><span class="sxs-lookup"><span data-stu-id="28cd3-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="28cd3-104">Det här elementet används när du definierar kontroller som kan användas av en vy.</span><span class="sxs-lookup"><span data-stu-id="28cd3-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="28cd3-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) styr element (format) styr element (format) styr element för Controls (format) CustomControl-element för kontroll för Control for View (format) CustomEntries-element för CustomControl för visnings-(format) CustomEntry-element för CustomEntries för Controls for View (format) CustomItem-elementet for CustomEntry for Controls for View (format) Frame element for CustomItem for Controls for View (format)</span><span class="sxs-lookup"><span data-stu-id="28cd3-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) Frame Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="28cd3-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="28cd3-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="28cd3-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="28cd3-107">Attributes and Elements</span></span>

<span data-ttu-id="28cd3-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för elementet `Frame`.</span><span class="sxs-lookup"><span data-stu-id="28cd3-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="28cd3-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="28cd3-109">Attributes</span></span>

<span data-ttu-id="28cd3-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="28cd3-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="28cd3-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="28cd3-111">Child Elements</span></span>

|<span data-ttu-id="28cd3-112">Element</span><span class="sxs-lookup"><span data-stu-id="28cd3-112">Element</span></span>|<span data-ttu-id="28cd3-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="28cd3-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="28cd3-114">Nödvändigt element</span><span class="sxs-lookup"><span data-stu-id="28cd3-114">Required Element</span></span>|
|[<span data-ttu-id="28cd3-115">FirstLineHanging-element för kontroll bild av vyer (format)</span><span class="sxs-lookup"><span data-stu-id="28cd3-115">FirstLineHanging Element of Frame of Controls of View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="28cd3-116">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="28cd3-116">Optional element.</span></span><br /><br /> <span data-ttu-id="28cd3-117">Anger hur många tecken den första raden flyttas till vänster.</span><span class="sxs-lookup"><span data-stu-id="28cd3-117">Specifies how many characters the first line is shifted to the left.</span></span>|
|[<span data-ttu-id="28cd3-118">FirstLineIndent-element för kontroll bild av vyer (format)</span><span class="sxs-lookup"><span data-stu-id="28cd3-118">FirstLineIndent Element of Frame of Controls of View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="28cd3-119">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="28cd3-119">Optional element.</span></span><br /><br /> <span data-ttu-id="28cd3-120">Anger hur många tecken den första raden flyttas till höger.</span><span class="sxs-lookup"><span data-stu-id="28cd3-120">Specifies how many characters the first line is shifted to the right.</span></span>|
|[<span data-ttu-id="28cd3-121">LeftIndent-element för kontroll bild av vyer (format)</span><span class="sxs-lookup"><span data-stu-id="28cd3-121">LeftIndent Element of Frame of Controls of View (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="28cd3-122">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="28cd3-122">Optional element.</span></span><br /><br /> <span data-ttu-id="28cd3-123">Anger hur många tecken data flyttas bort från vänstermarginalen.</span><span class="sxs-lookup"><span data-stu-id="28cd3-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="28cd3-124">RightIndent-element för kontroll bild av vyer (format)</span><span class="sxs-lookup"><span data-stu-id="28cd3-124">RightIndent Element of Frame of Controls of View (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="28cd3-125">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="28cd3-125">Optional element.</span></span><br /><br /> <span data-ttu-id="28cd3-126">Anger hur många tecken data flyttas bort från högermarginalen.</span><span class="sxs-lookup"><span data-stu-id="28cd3-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="28cd3-127">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="28cd3-127">Parent Elements</span></span>

|<span data-ttu-id="28cd3-128">Element</span><span class="sxs-lookup"><span data-stu-id="28cd3-128">Element</span></span>|<span data-ttu-id="28cd3-129">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="28cd3-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="28cd3-130">CustomItem-element för CustomEntry för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="28cd3-130">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="28cd3-131">Definierar vilka data som visas av kontrollen och hur de visas.</span><span class="sxs-lookup"><span data-stu-id="28cd3-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="28cd3-132">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="28cd3-132">Remarks</span></span>

<span data-ttu-id="28cd3-133">Du kan inte ange [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) och [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) -elementen i samma `Frame`-element.</span><span class="sxs-lookup"><span data-stu-id="28cd3-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="28cd3-134">Se även</span><span class="sxs-lookup"><span data-stu-id="28cd3-134">See Also</span></span>

[<span data-ttu-id="28cd3-135">FirstLineHanging-element för kontroll bild av vyer (format)</span><span class="sxs-lookup"><span data-stu-id="28cd3-135">FirstLineHanging Element of Frame of Controls of View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="28cd3-136">FirstLineIndent-element för kontroll bild av vyer (format)</span><span class="sxs-lookup"><span data-stu-id="28cd3-136">FirstLineIndent Element of Frame of Controls of View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="28cd3-137">LeftIndent-element för kontroll bild av vyer (format)</span><span class="sxs-lookup"><span data-stu-id="28cd3-137">LeftIndent Element of Frame of Controls of View (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="28cd3-138">RightIndent-element för kontroll bild av vyer (format)</span><span class="sxs-lookup"><span data-stu-id="28cd3-138">RightIndent Element of Frame of Controls of View (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="28cd3-139">CustomItem-element för CustomEntry för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="28cd3-139">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="28cd3-140">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="28cd3-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
