---
ms.date: 09/13/2016
ms.topic: reference
title: Frame-element för CustomItem för GroupBy (format)
description: Frame-element för CustomItem för GroupBy (format)
ms.openlocfilehash: 86b51766974ebfcae06583ade237a77c6db92866
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652178"
---
# <a name="frame-element-for-customitem-for-groupby-format"></a><span data-ttu-id="a0933-103">Frame-element för CustomItem för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="a0933-103">Frame Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="a0933-104">Definierar hur data visas, till exempel att flytta data till vänster eller höger.</span><span class="sxs-lookup"><span data-stu-id="a0933-104">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="a0933-105">Det här elementet används när du definierar hur en ny grupp av objekt visas.</span><span class="sxs-lookup"><span data-stu-id="a0933-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="a0933-106">Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för visnings-(format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for GroupBy (format) CustomEntry element for CustomControl for groupby (format) CustomItem-element för CustomEntry</span><span class="sxs-lookup"><span data-stu-id="a0933-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) Frame Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a0933-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="a0933-107">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a0933-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="a0933-108">Attributes and Elements</span></span>

<span data-ttu-id="a0933-109">I följande avsnitt beskrivs attribut, underordnade element och `Frame` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="a0933-109">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a0933-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="a0933-110">Attributes</span></span>

<span data-ttu-id="a0933-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="a0933-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a0933-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="a0933-112">Child Elements</span></span>

|<span data-ttu-id="a0933-113">Element</span><span class="sxs-lookup"><span data-stu-id="a0933-113">Element</span></span>|<span data-ttu-id="a0933-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a0933-114">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="a0933-115">Nödvändigt element</span><span class="sxs-lookup"><span data-stu-id="a0933-115">Required Element</span></span>|
|[<span data-ttu-id="a0933-116">FirstLineHanging-element för Frame för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="a0933-116">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)|<span data-ttu-id="a0933-117">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="a0933-117">Optional element.</span></span><br /><br /> <span data-ttu-id="a0933-118">Anger hur många tecken den första raden med data flyttas till vänster.</span><span class="sxs-lookup"><span data-stu-id="a0933-118">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="a0933-119">FirstLineIndent-element för Frame för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="a0933-119">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="a0933-120">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="a0933-120">Optional element.</span></span><br /><br /> <span data-ttu-id="a0933-121">Anger hur många tecken den första raden med data flyttas till höger.</span><span class="sxs-lookup"><span data-stu-id="a0933-121">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="a0933-122">LeftIndent-element för Frame för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="a0933-122">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="a0933-123">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="a0933-123">Optional element.</span></span><br /><br /> <span data-ttu-id="a0933-124">Anger hur många tecken data flyttas bort från vänstermarginalen.</span><span class="sxs-lookup"><span data-stu-id="a0933-124">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|<span data-ttu-id="a0933-125">[RightIndent-element för inramad groupby (format)](./rightindent-element-for-frame-for-groupby-format.md) RightIndent-element</span><span class="sxs-lookup"><span data-stu-id="a0933-125">[RightIndent Element for Frame for GroupBy (Format)](./rightindent-element-for-frame-for-groupby-format.md)RightIndent Element</span></span>|<span data-ttu-id="a0933-126">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="a0933-126">Optional element.</span></span><br /><br /> <span data-ttu-id="a0933-127">Anger hur många tecken data flyttas bort från högermarginalen.</span><span class="sxs-lookup"><span data-stu-id="a0933-127">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a0933-128">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="a0933-128">Parent Elements</span></span>

|<span data-ttu-id="a0933-129">Element</span><span class="sxs-lookup"><span data-stu-id="a0933-129">Element</span></span>|<span data-ttu-id="a0933-130">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a0933-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a0933-131">CustomItem-element för CustomEntry för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="a0933-131">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="a0933-132">Definierar vilka data som visas av kontrollen och hur de visas.</span><span class="sxs-lookup"><span data-stu-id="a0933-132">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a0933-133">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="a0933-133">Remarks</span></span>

<span data-ttu-id="a0933-134">Du kan inte ange [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) och [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) -elementen i samma `Frame` element.</span><span class="sxs-lookup"><span data-stu-id="a0933-134">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="a0933-135">Se även</span><span class="sxs-lookup"><span data-stu-id="a0933-135">See Also</span></span>

[<span data-ttu-id="a0933-136">FirstLineHanging-element för Frame för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="a0933-136">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="a0933-137">FirstLineIndent-element för Frame för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="a0933-137">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="a0933-138">LeftIndent-element för Frame för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="a0933-138">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="a0933-139">RightIndent-element för Frame för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="a0933-139">RightIndent Element for Frame for GroupBy (Format)</span></span>](./rightindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="a0933-140">CustomItem-element för CustomEntry för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="a0933-140">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="a0933-141">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="a0933-141">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
