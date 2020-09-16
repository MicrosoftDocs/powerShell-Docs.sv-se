---
title: Ram element för CustomItem for GroupBy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 1568236ff7b6142f7e41be70a3ae5e28307cf790
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785769"
---
# <a name="frame-element-for-customitem-for-groupby-format"></a><span data-ttu-id="f6385-102">Frame-element för CustomItem för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="f6385-102">Frame Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="f6385-103">Definierar hur data visas, till exempel att flytta data till vänster eller höger.</span><span class="sxs-lookup"><span data-stu-id="f6385-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="f6385-104">Det här elementet används när du definierar hur en ny grupp av objekt visas.</span><span class="sxs-lookup"><span data-stu-id="f6385-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="f6385-105">Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för visnings-(format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for GroupBy (format) CustomEntry element for CustomControl for groupby (format) CustomItem-element för CustomEntry</span><span class="sxs-lookup"><span data-stu-id="f6385-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) Frame Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f6385-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="f6385-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f6385-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="f6385-107">Attributes and Elements</span></span>

<span data-ttu-id="f6385-108">I följande avsnitt beskrivs attribut, underordnade element och `Frame` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="f6385-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f6385-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="f6385-109">Attributes</span></span>

<span data-ttu-id="f6385-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="f6385-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f6385-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="f6385-111">Child Elements</span></span>

|<span data-ttu-id="f6385-112">Element</span><span class="sxs-lookup"><span data-stu-id="f6385-112">Element</span></span>|<span data-ttu-id="f6385-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f6385-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="f6385-114">Nödvändigt element</span><span class="sxs-lookup"><span data-stu-id="f6385-114">Required Element</span></span>|
|[<span data-ttu-id="f6385-115">FirstLineHanging-element för Frame för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="f6385-115">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)|<span data-ttu-id="f6385-116">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="f6385-116">Optional element.</span></span><br /><br /> <span data-ttu-id="f6385-117">Anger hur många tecken den första raden med data flyttas till vänster.</span><span class="sxs-lookup"><span data-stu-id="f6385-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="f6385-118">FirstLineIndent-element för Frame för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="f6385-118">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="f6385-119">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="f6385-119">Optional element.</span></span><br /><br /> <span data-ttu-id="f6385-120">Anger hur många tecken den första raden med data flyttas till höger.</span><span class="sxs-lookup"><span data-stu-id="f6385-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="f6385-121">LeftIndent-element för Frame för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="f6385-121">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="f6385-122">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="f6385-122">Optional element.</span></span><br /><br /> <span data-ttu-id="f6385-123">Anger hur många tecken data flyttas bort från vänstermarginalen.</span><span class="sxs-lookup"><span data-stu-id="f6385-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|<span data-ttu-id="f6385-124">[RightIndent-element för inramad groupby (format)](./rightindent-element-for-frame-for-groupby-format.md) RightIndent-element</span><span class="sxs-lookup"><span data-stu-id="f6385-124">[RightIndent Element for Frame for GroupBy (Format)](./rightindent-element-for-frame-for-groupby-format.md)RightIndent Element</span></span>|<span data-ttu-id="f6385-125">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="f6385-125">Optional element.</span></span><br /><br /> <span data-ttu-id="f6385-126">Anger hur många tecken data flyttas bort från högermarginalen.</span><span class="sxs-lookup"><span data-stu-id="f6385-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f6385-127">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="f6385-127">Parent Elements</span></span>

|<span data-ttu-id="f6385-128">Element</span><span class="sxs-lookup"><span data-stu-id="f6385-128">Element</span></span>|<span data-ttu-id="f6385-129">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f6385-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f6385-130">CustomItem-element för CustomEntry för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="f6385-130">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="f6385-131">Definierar vilka data som visas av kontrollen och hur de visas.</span><span class="sxs-lookup"><span data-stu-id="f6385-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f6385-132">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="f6385-132">Remarks</span></span>

<span data-ttu-id="f6385-133">Du kan inte ange [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) och [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) -elementen i samma `Frame` element.</span><span class="sxs-lookup"><span data-stu-id="f6385-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="f6385-134">Se även</span><span class="sxs-lookup"><span data-stu-id="f6385-134">See Also</span></span>

[<span data-ttu-id="f6385-135">FirstLineHanging-element för Frame för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="f6385-135">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="f6385-136">FirstLineIndent-element för Frame för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="f6385-136">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="f6385-137">LeftIndent-element för Frame för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="f6385-137">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="f6385-138">RightIndent-element för Frame för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="f6385-138">RightIndent Element for Frame for GroupBy (Format)</span></span>](./rightindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="f6385-139">CustomItem-element för CustomEntry för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="f6385-139">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="f6385-140">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="f6385-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
