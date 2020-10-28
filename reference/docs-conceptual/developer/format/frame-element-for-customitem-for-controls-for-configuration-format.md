---
ms.date: 09/13/2016
ms.topic: reference
title: Frame-element för CustomItem för Controls för Configuration (format)
description: Frame-element för CustomItem för Controls för Configuration (format)
ms.openlocfilehash: 85d095b9b0c25b68b2353bce56b85333aff91b98
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92652243"
---
# <a name="frame-element-for-customitem-for-controls-for-configuration-format"></a><span data-ttu-id="b7bbb-103">Frame-element för CustomItem för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="b7bbb-103">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

<span data-ttu-id="b7bbb-104">Definierar hur data visas, till exempel att flytta data till vänster eller höger.</span><span class="sxs-lookup"><span data-stu-id="b7bbb-104">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="b7bbb-105">Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.</span><span class="sxs-lookup"><span data-stu-id="b7bbb-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="b7bbb-106">Konfigurations element (format) styr element i konfigurations-(format)-kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för Configuration (format) CustomEntry-element för CustomControl för Controls (format) CustomItem-element för CustomEntry för Controls (format) för konfigurations ram element för CustomItem.</span><span class="sxs-lookup"><span data-stu-id="b7bbb-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b7bbb-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="b7bbb-107">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b7bbb-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="b7bbb-108">Attributes and Elements</span></span>

<span data-ttu-id="b7bbb-109">I följande avsnitt beskrivs attribut, underordnade element och `Frame` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="b7bbb-109">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b7bbb-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="b7bbb-110">Attributes</span></span>

<span data-ttu-id="b7bbb-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="b7bbb-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b7bbb-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="b7bbb-112">Child Elements</span></span>

|<span data-ttu-id="b7bbb-113">Element</span><span class="sxs-lookup"><span data-stu-id="b7bbb-113">Element</span></span>|<span data-ttu-id="b7bbb-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b7bbb-114">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="b7bbb-115">Nödvändigt element</span><span class="sxs-lookup"><span data-stu-id="b7bbb-115">Required Element</span></span>|
|[<span data-ttu-id="b7bbb-116">FirstLineHanging-element för Frame för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="b7bbb-116">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="b7bbb-117">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="b7bbb-117">Optional element.</span></span><br /><br /> <span data-ttu-id="b7bbb-118">Anger hur många tecken den första raden med data flyttas till vänster.</span><span class="sxs-lookup"><span data-stu-id="b7bbb-118">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="b7bbb-119">FirstLineIndent-element för Frame för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="b7bbb-119">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="b7bbb-120">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="b7bbb-120">Optional element.</span></span><br /><br /> <span data-ttu-id="b7bbb-121">Anger hur många tecken den första raden med data flyttas till höger.</span><span class="sxs-lookup"><span data-stu-id="b7bbb-121">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="b7bbb-122">LeftIndent-element för Frame för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="b7bbb-122">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="b7bbb-123">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="b7bbb-123">Optional element.</span></span><br /><br /> <span data-ttu-id="b7bbb-124">Anger hur många tecken data flyttas bort från vänstermarginalen.</span><span class="sxs-lookup"><span data-stu-id="b7bbb-124">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="b7bbb-125">RightIndent-element för Frame för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="b7bbb-125">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="b7bbb-126">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="b7bbb-126">Optional element.</span></span><br /><br /> <span data-ttu-id="b7bbb-127">Anger hur många tecken data flyttas bort från högermarginalen.</span><span class="sxs-lookup"><span data-stu-id="b7bbb-127">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b7bbb-128">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="b7bbb-128">Parent Elements</span></span>

|<span data-ttu-id="b7bbb-129">Element</span><span class="sxs-lookup"><span data-stu-id="b7bbb-129">Element</span></span>|<span data-ttu-id="b7bbb-130">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b7bbb-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b7bbb-131">CustomItem-element för CustomEntry för kontroller för konfiguration</span><span class="sxs-lookup"><span data-stu-id="b7bbb-131">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="b7bbb-132">Definierar vilka data som visas av kontrollen och hur de visas.</span><span class="sxs-lookup"><span data-stu-id="b7bbb-132">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b7bbb-133">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="b7bbb-133">Remarks</span></span>

<span data-ttu-id="b7bbb-134">Du kan inte ange [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) och [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) -elementen i samma `Frame` element.</span><span class="sxs-lookup"><span data-stu-id="b7bbb-134">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="b7bbb-135">Se även</span><span class="sxs-lookup"><span data-stu-id="b7bbb-135">See Also</span></span>

[<span data-ttu-id="b7bbb-136">FirstLineHanging-element för Frame för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="b7bbb-136">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="b7bbb-137">FirstLineIndent-element för Frame för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="b7bbb-137">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="b7bbb-138">LeftIndent-element för Frame för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="b7bbb-138">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="b7bbb-139">RightIndent-element för Frame för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="b7bbb-139">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="b7bbb-140">CustomItem-element för CustomEntry för kontroller för konfiguration</span><span class="sxs-lookup"><span data-stu-id="b7bbb-140">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="b7bbb-141">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="b7bbb-141">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
