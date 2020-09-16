---
title: Ram element för CustomItem för kontroll av konfiguration (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: fa435b8d6b868d2d7c94b7926321d94edc2ec290
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781485"
---
# <a name="frame-element-for-customitem-for-controls-for-configuration-format"></a><span data-ttu-id="5e01d-102">Frame-element för CustomItem för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="5e01d-102">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

<span data-ttu-id="5e01d-103">Definierar hur data visas, till exempel att flytta data till vänster eller höger.</span><span class="sxs-lookup"><span data-stu-id="5e01d-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="5e01d-104">Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.</span><span class="sxs-lookup"><span data-stu-id="5e01d-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="5e01d-105">Konfigurations element (format) styr element i konfigurations-(format)-kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för Configuration (format) CustomEntry-element för CustomControl för Controls (format) CustomItem-element för CustomEntry för Controls (format) för konfigurations ram element för CustomItem.</span><span class="sxs-lookup"><span data-stu-id="5e01d-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5e01d-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="5e01d-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5e01d-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="5e01d-107">Attributes and Elements</span></span>

<span data-ttu-id="5e01d-108">I följande avsnitt beskrivs attribut, underordnade element och `Frame` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="5e01d-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5e01d-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="5e01d-109">Attributes</span></span>

<span data-ttu-id="5e01d-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="5e01d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5e01d-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="5e01d-111">Child Elements</span></span>

|<span data-ttu-id="5e01d-112">Element</span><span class="sxs-lookup"><span data-stu-id="5e01d-112">Element</span></span>|<span data-ttu-id="5e01d-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5e01d-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="5e01d-114">Nödvändigt element</span><span class="sxs-lookup"><span data-stu-id="5e01d-114">Required Element</span></span>|
|[<span data-ttu-id="5e01d-115">FirstLineHanging-element för Frame för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="5e01d-115">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="5e01d-116">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="5e01d-116">Optional element.</span></span><br /><br /> <span data-ttu-id="5e01d-117">Anger hur många tecken den första raden med data flyttas till vänster.</span><span class="sxs-lookup"><span data-stu-id="5e01d-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="5e01d-118">FirstLineIndent-element för Frame för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="5e01d-118">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="5e01d-119">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="5e01d-119">Optional element.</span></span><br /><br /> <span data-ttu-id="5e01d-120">Anger hur många tecken den första raden med data flyttas till höger.</span><span class="sxs-lookup"><span data-stu-id="5e01d-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="5e01d-121">LeftIndent-element för Frame för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="5e01d-121">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="5e01d-122">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="5e01d-122">Optional element.</span></span><br /><br /> <span data-ttu-id="5e01d-123">Anger hur många tecken data flyttas bort från vänstermarginalen.</span><span class="sxs-lookup"><span data-stu-id="5e01d-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="5e01d-124">RightIndent-element för Frame för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="5e01d-124">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="5e01d-125">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="5e01d-125">Optional element.</span></span><br /><br /> <span data-ttu-id="5e01d-126">Anger hur många tecken data flyttas bort från högermarginalen.</span><span class="sxs-lookup"><span data-stu-id="5e01d-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5e01d-127">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="5e01d-127">Parent Elements</span></span>

|<span data-ttu-id="5e01d-128">Element</span><span class="sxs-lookup"><span data-stu-id="5e01d-128">Element</span></span>|<span data-ttu-id="5e01d-129">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5e01d-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5e01d-130">CustomItem-element för CustomEntry för kontroller för konfiguration</span><span class="sxs-lookup"><span data-stu-id="5e01d-130">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="5e01d-131">Definierar vilka data som visas av kontrollen och hur de visas.</span><span class="sxs-lookup"><span data-stu-id="5e01d-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5e01d-132">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="5e01d-132">Remarks</span></span>

<span data-ttu-id="5e01d-133">Du kan inte ange [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) och [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) -elementen i samma `Frame` element.</span><span class="sxs-lookup"><span data-stu-id="5e01d-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="5e01d-134">Se även</span><span class="sxs-lookup"><span data-stu-id="5e01d-134">See Also</span></span>

[<span data-ttu-id="5e01d-135">FirstLineHanging-element för Frame för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="5e01d-135">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="5e01d-136">FirstLineIndent-element för Frame för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="5e01d-136">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="5e01d-137">LeftIndent-element för Frame för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="5e01d-137">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="5e01d-138">RightIndent-element för Frame för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="5e01d-138">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="5e01d-139">CustomItem-element för CustomEntry för kontroller för konfiguration</span><span class="sxs-lookup"><span data-stu-id="5e01d-139">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="5e01d-140">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="5e01d-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
