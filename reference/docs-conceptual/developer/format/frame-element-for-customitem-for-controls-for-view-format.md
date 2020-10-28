---
ms.date: 09/13/2016
ms.topic: reference
title: Frame-element för CustomItem för Controls för View (format)
description: Frame-element för CustomItem för Controls för View (format)
ms.openlocfilehash: 6f26e19a6894ac213b924108a56cb80f9ffd1143
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92652204"
---
# <a name="frame-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="5ab9d-103">Frame-element för CustomItem för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="5ab9d-103">Frame Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="5ab9d-104">Definierar hur data visas, till exempel att flytta data till vänster eller höger.</span><span class="sxs-lookup"><span data-stu-id="5ab9d-104">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="5ab9d-105">Det här elementet används när du definierar kontroller som kan användas av en vy.</span><span class="sxs-lookup"><span data-stu-id="5ab9d-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="5ab9d-106">Konfigurations element (format) ViewDefinitions element (format) View-element (format) styr element (format) kontroll element (format) styr element (format) för kontroll element för View (format) CustomControl-element för kontroll för Control for View (format) CustomEntries element för CustomControl for View (format) CustomEntry-elementet för CustomEntries for Controls for View (format) CustomItem-elementet for CustomEntry for Controls for View (format) Frame element for CustomItem for Controls for View (format)</span><span class="sxs-lookup"><span data-stu-id="5ab9d-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) Frame Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5ab9d-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="5ab9d-107">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5ab9d-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="5ab9d-108">Attributes and Elements</span></span>

<span data-ttu-id="5ab9d-109">I följande avsnitt beskrivs attribut, underordnade element och `Frame` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="5ab9d-109">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5ab9d-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="5ab9d-110">Attributes</span></span>

<span data-ttu-id="5ab9d-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="5ab9d-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5ab9d-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="5ab9d-112">Child Elements</span></span>

|<span data-ttu-id="5ab9d-113">Element</span><span class="sxs-lookup"><span data-stu-id="5ab9d-113">Element</span></span>|<span data-ttu-id="5ab9d-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5ab9d-114">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="5ab9d-115">Nödvändigt element</span><span class="sxs-lookup"><span data-stu-id="5ab9d-115">Required Element</span></span>|
|[<span data-ttu-id="5ab9d-116">FirstLineHanging-element för kontroll bild av vyer (format)</span><span class="sxs-lookup"><span data-stu-id="5ab9d-116">FirstLineHanging Element of Frame of Controls of View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="5ab9d-117">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="5ab9d-117">Optional element.</span></span><br /><br /> <span data-ttu-id="5ab9d-118">Anger hur många tecken den första raden flyttas till vänster.</span><span class="sxs-lookup"><span data-stu-id="5ab9d-118">Specifies how many characters the first line is shifted to the left.</span></span>|
|[<span data-ttu-id="5ab9d-119">FirstLineIndent-element för kontroll bild av vyer (format)</span><span class="sxs-lookup"><span data-stu-id="5ab9d-119">FirstLineIndent Element of Frame of Controls of View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="5ab9d-120">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="5ab9d-120">Optional element.</span></span><br /><br /> <span data-ttu-id="5ab9d-121">Anger hur många tecken den första raden flyttas till höger.</span><span class="sxs-lookup"><span data-stu-id="5ab9d-121">Specifies how many characters the first line is shifted to the right.</span></span>|
|[<span data-ttu-id="5ab9d-122">LeftIndent-element för kontroll bild av vyer (format)</span><span class="sxs-lookup"><span data-stu-id="5ab9d-122">LeftIndent Element of Frame of Controls of View (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="5ab9d-123">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="5ab9d-123">Optional element.</span></span><br /><br /> <span data-ttu-id="5ab9d-124">Anger hur många tecken data flyttas bort från vänstermarginalen.</span><span class="sxs-lookup"><span data-stu-id="5ab9d-124">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="5ab9d-125">RightIndent-element för kontroll bild av vyer (format)</span><span class="sxs-lookup"><span data-stu-id="5ab9d-125">RightIndent Element of Frame of Controls of View (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="5ab9d-126">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="5ab9d-126">Optional element.</span></span><br /><br /> <span data-ttu-id="5ab9d-127">Anger hur många tecken data flyttas bort från högermarginalen.</span><span class="sxs-lookup"><span data-stu-id="5ab9d-127">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5ab9d-128">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="5ab9d-128">Parent Elements</span></span>

|<span data-ttu-id="5ab9d-129">Element</span><span class="sxs-lookup"><span data-stu-id="5ab9d-129">Element</span></span>|<span data-ttu-id="5ab9d-130">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5ab9d-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5ab9d-131">CustomItem-element för CustomEntry för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="5ab9d-131">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="5ab9d-132">Definierar vilka data som visas av kontrollen och hur de visas.</span><span class="sxs-lookup"><span data-stu-id="5ab9d-132">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5ab9d-133">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="5ab9d-133">Remarks</span></span>

<span data-ttu-id="5ab9d-134">Du kan inte ange [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) och [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) -elementen i samma `Frame` element.</span><span class="sxs-lookup"><span data-stu-id="5ab9d-134">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="5ab9d-135">Se även</span><span class="sxs-lookup"><span data-stu-id="5ab9d-135">See Also</span></span>

[<span data-ttu-id="5ab9d-136">FirstLineHanging-element för kontroll bild av vyer (format)</span><span class="sxs-lookup"><span data-stu-id="5ab9d-136">FirstLineHanging Element of Frame of Controls of View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="5ab9d-137">FirstLineIndent-element för kontroll bild av vyer (format)</span><span class="sxs-lookup"><span data-stu-id="5ab9d-137">FirstLineIndent Element of Frame of Controls of View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="5ab9d-138">LeftIndent-element för kontroll bild av vyer (format)</span><span class="sxs-lookup"><span data-stu-id="5ab9d-138">LeftIndent Element of Frame of Controls of View (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="5ab9d-139">RightIndent-element för kontroll bild av vyer (format)</span><span class="sxs-lookup"><span data-stu-id="5ab9d-139">RightIndent Element of Frame of Controls of View (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="5ab9d-140">CustomItem-element för CustomEntry för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="5ab9d-140">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="5ab9d-141">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="5ab9d-141">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
