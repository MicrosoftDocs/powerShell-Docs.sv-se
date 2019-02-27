---
title: RAM-Element för CustomItem för GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab2a5379-299d-4c97-86a2-b639ea890fae
caps.latest.revision: 6
ms.openlocfilehash: 7f9066c0fe0954fadff9dc8f0c35a62c6710f516
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846006"
---
# <a name="frame-element-for-customitem-for-groupby-format"></a><span data-ttu-id="15bd8-102">Frame-element för CustomItem för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="15bd8-102">Frame Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="15bd8-103">Definierar hur data visas, till exempel ändra datatypen till vänster eller höger.</span><span class="sxs-lookup"><span data-stu-id="15bd8-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="15bd8-104">Det här elementet används när du definierar hur en ny grupp med objekt visas.</span><span class="sxs-lookup"><span data-stu-id="15bd8-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="15bd8-105">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) GroupBy konfigurationselement för Visa (Format) anpassad kontroll elementet för GroupBy (Format) CustomEntries Element för anpassad kontroll för GroupBy (Format) CustomEntry elementet för Anpassad kontroll för GroupBy (Format) CustomItem elementet för CustomEntry för GroupBy (Format) RAM-elementet för CustomItem för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="15bd8-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) Frame Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="15bd8-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="15bd8-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="15bd8-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="15bd8-107">Attributes and Elements</span></span>

<span data-ttu-id="15bd8-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `Frame` element.</span><span class="sxs-lookup"><span data-stu-id="15bd8-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="15bd8-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="15bd8-109">Attributes</span></span>

<span data-ttu-id="15bd8-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="15bd8-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="15bd8-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="15bd8-111">Child Elements</span></span>

|<span data-ttu-id="15bd8-112">Element</span><span class="sxs-lookup"><span data-stu-id="15bd8-112">Element</span></span>|<span data-ttu-id="15bd8-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="15bd8-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="15bd8-114">Element som krävs</span><span class="sxs-lookup"><span data-stu-id="15bd8-114">Required Element</span></span>|
|[<span data-ttu-id="15bd8-115">FirstLineHanging Element för ramens för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="15bd8-115">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)|<span data-ttu-id="15bd8-116">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="15bd8-116">Optional element.</span></span><br /><br /> <span data-ttu-id="15bd8-117">Anger hur många tecken som den första raden av data ska flyttas till vänster.</span><span class="sxs-lookup"><span data-stu-id="15bd8-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="15bd8-118">FirstLineIndent Element för ramens för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="15bd8-118">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="15bd8-119">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="15bd8-119">Optional element.</span></span><br /><br /> <span data-ttu-id="15bd8-120">Anger hur många tecken som den första raden av data ska flyttas till höger.</span><span class="sxs-lookup"><span data-stu-id="15bd8-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="15bd8-121">LeftIndent Element för ramens för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="15bd8-121">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="15bd8-122">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="15bd8-122">Optional element.</span></span><br /><br /> <span data-ttu-id="15bd8-123">Anger hur många tecken som data ska flyttas från vänster marginal.</span><span class="sxs-lookup"><span data-stu-id="15bd8-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|<span data-ttu-id="15bd8-124">[RightIndent Element för ramens för GroupBy (Format)](./rightindent-element-for-frame-for-groupby-format.md)RightIndent Element</span><span class="sxs-lookup"><span data-stu-id="15bd8-124">[RightIndent Element for Frame for GroupBy (Format)](./rightindent-element-for-frame-for-groupby-format.md)RightIndent Element</span></span>|<span data-ttu-id="15bd8-125">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="15bd8-125">Optional element.</span></span><br /><br /> <span data-ttu-id="15bd8-126">Anger hur många tecken som data ska flyttas från höger marginal.</span><span class="sxs-lookup"><span data-stu-id="15bd8-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="15bd8-127">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="15bd8-127">Parent Elements</span></span>

|<span data-ttu-id="15bd8-128">Element</span><span class="sxs-lookup"><span data-stu-id="15bd8-128">Element</span></span>|<span data-ttu-id="15bd8-129">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="15bd8-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="15bd8-130">CustomItem Element för CustomEntry för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="15bd8-130">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="15bd8-131">Definierar vilka data som visas av kontrollen och hur de visas.</span><span class="sxs-lookup"><span data-stu-id="15bd8-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="15bd8-132">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="15bd8-132">Remarks</span></span>

<span data-ttu-id="15bd8-133">Du kan inte ange den [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) och [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) element i samma `Frame` element.</span><span class="sxs-lookup"><span data-stu-id="15bd8-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="15bd8-134">Se även</span><span class="sxs-lookup"><span data-stu-id="15bd8-134">See Also</span></span>

[<span data-ttu-id="15bd8-135">FirstLineHanging Element för ramens för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="15bd8-135">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="15bd8-136">FirstLineIndent Element för ramens för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="15bd8-136">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="15bd8-137">LeftIndent Element för ramens för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="15bd8-137">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="15bd8-138">RightIndent Element för ramens för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="15bd8-138">RightIndent Element for Frame for GroupBy (Format)</span></span>](./rightindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="15bd8-139">CustomItem Element för CustomEntry för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="15bd8-139">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="15bd8-140">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="15bd8-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
