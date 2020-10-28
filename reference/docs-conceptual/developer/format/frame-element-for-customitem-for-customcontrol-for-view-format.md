---
ms.date: 09/13/2016
ms.topic: reference
title: Frame-element för CustomItem för CustomControl för View (format)
description: Frame-element för CustomItem för CustomControl för View (format)
ms.openlocfilehash: 1ffe071bb6c4f590e4c79803a3faff2108c7b636
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92652185"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="22bdb-103">Frame-element för CustomItem för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="22bdb-103">Frame Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="22bdb-104">Definierar hur data visas, till exempel att flytta data till vänster eller höger.</span><span class="sxs-lookup"><span data-stu-id="22bdb-104">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="22bdb-105">Det här elementet används när du definierar en anpassad kontrol vy.</span><span class="sxs-lookup"><span data-stu-id="22bdb-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="22bdb-106">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) CustomControl element (format) CustomEntries-element för CustomControl för View (format) CustomEntry-element för CustomEntries för View (format) CustomItem-element för CustomEntry för CustomControlView (format) för CustomItem för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="22bdb-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CustomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="22bdb-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="22bdb-107">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="22bdb-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="22bdb-108">Attributes and Elements</span></span>

<span data-ttu-id="22bdb-109">I följande avsnitt beskrivs attribut, underordnade element och `Frame` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="22bdb-109">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="22bdb-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="22bdb-110">Attributes</span></span>

<span data-ttu-id="22bdb-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="22bdb-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="22bdb-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="22bdb-112">Child Elements</span></span>

|<span data-ttu-id="22bdb-113">Element</span><span class="sxs-lookup"><span data-stu-id="22bdb-113">Element</span></span>|<span data-ttu-id="22bdb-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="22bdb-114">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="22bdb-115">Nödvändigt element</span><span class="sxs-lookup"><span data-stu-id="22bdb-115">Required Element</span></span>|
|[<span data-ttu-id="22bdb-116">FirstLineHanging-element</span><span class="sxs-lookup"><span data-stu-id="22bdb-116">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="22bdb-117">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="22bdb-117">Optional element.</span></span><br /><br /> <span data-ttu-id="22bdb-118">Anger hur många tecken den första raden med data flyttas till vänster.</span><span class="sxs-lookup"><span data-stu-id="22bdb-118">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="22bdb-119">FirstLineIndent-element</span><span class="sxs-lookup"><span data-stu-id="22bdb-119">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="22bdb-120">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="22bdb-120">Optional element.</span></span><br /><br /> <span data-ttu-id="22bdb-121">Anger hur många tecken den första raden med data flyttas till höger.</span><span class="sxs-lookup"><span data-stu-id="22bdb-121">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="22bdb-122">LeftIndent-element</span><span class="sxs-lookup"><span data-stu-id="22bdb-122">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="22bdb-123">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="22bdb-123">Optional element.</span></span><br /><br /> <span data-ttu-id="22bdb-124">Anger hur många tecken data flyttas bort från vänstermarginalen.</span><span class="sxs-lookup"><span data-stu-id="22bdb-124">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="22bdb-125">RightIndent-element</span><span class="sxs-lookup"><span data-stu-id="22bdb-125">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="22bdb-126">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="22bdb-126">Optional element.</span></span><br /><br /> <span data-ttu-id="22bdb-127">Anger hur många tecken data flyttas bort från högermarginalen.</span><span class="sxs-lookup"><span data-stu-id="22bdb-127">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="22bdb-128">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="22bdb-128">Parent Elements</span></span>

|<span data-ttu-id="22bdb-129">Element</span><span class="sxs-lookup"><span data-stu-id="22bdb-129">Element</span></span>|<span data-ttu-id="22bdb-130">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="22bdb-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="22bdb-131">CustomItem-element för CustomEntry för vy (format)</span><span class="sxs-lookup"><span data-stu-id="22bdb-131">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="22bdb-132">Definierar vilka data som visas av kontrollen och hur de visas.</span><span class="sxs-lookup"><span data-stu-id="22bdb-132">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="22bdb-133">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="22bdb-133">Remarks</span></span>

<span data-ttu-id="22bdb-134">Du kan inte ange [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) och [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) -elementen i samma `Frame` element.</span><span class="sxs-lookup"><span data-stu-id="22bdb-134">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="22bdb-135">Se även</span><span class="sxs-lookup"><span data-stu-id="22bdb-135">See Also</span></span>

[<span data-ttu-id="22bdb-136">FirstLineHanging-element</span><span class="sxs-lookup"><span data-stu-id="22bdb-136">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="22bdb-137">FirstLineIndent-element</span><span class="sxs-lookup"><span data-stu-id="22bdb-137">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="22bdb-138">LeftIndent-element</span><span class="sxs-lookup"><span data-stu-id="22bdb-138">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="22bdb-139">RightIndent-element</span><span class="sxs-lookup"><span data-stu-id="22bdb-139">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="22bdb-140">CustomItem-element för CustomEntry för vy (format)</span><span class="sxs-lookup"><span data-stu-id="22bdb-140">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="22bdb-141">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="22bdb-141">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
