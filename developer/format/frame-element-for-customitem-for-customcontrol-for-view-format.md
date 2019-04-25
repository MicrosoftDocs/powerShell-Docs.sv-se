---
title: RAM-Element för CustomItem för anpassad kontroll för vy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e1a13100-41a4-4847-9f07-458c85783505
caps.latest.revision: 6
ms.openlocfilehash: 925ef86e61801f5a66f89dd25e0756f00dd35155
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065588"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="e6110-102">Frame-element för CustomItem för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="e6110-102">Frame Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="e6110-103">Definierar hur data visas, till exempel ändra datatypen till vänster eller höger.</span><span class="sxs-lookup"><span data-stu-id="e6110-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="e6110-104">Det här elementet används när du definierar en anpassad kontroll vy.</span><span class="sxs-lookup"><span data-stu-id="e6110-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="e6110-105">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) anpassad kontroll Element (Format) CustomEntries konfigurationselement för anpassad kontroll för Visa (Format) CustomEntry elementet för CustomEntries för vyn (Format) CustomItem elementet för CustomEntry för CustomControlView (Format) RAM-elementet för CustomItem för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="e6110-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CustomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e6110-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="e6110-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e6110-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="e6110-107">Attributes and Elements</span></span>

<span data-ttu-id="e6110-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `Frame` element.</span><span class="sxs-lookup"><span data-stu-id="e6110-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e6110-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="e6110-109">Attributes</span></span>

<span data-ttu-id="e6110-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="e6110-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e6110-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="e6110-111">Child Elements</span></span>

|<span data-ttu-id="e6110-112">Element</span><span class="sxs-lookup"><span data-stu-id="e6110-112">Element</span></span>|<span data-ttu-id="e6110-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e6110-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="e6110-114">Element som krävs</span><span class="sxs-lookup"><span data-stu-id="e6110-114">Required Element</span></span>|
|[<span data-ttu-id="e6110-115">FirstLineHanging Element</span><span class="sxs-lookup"><span data-stu-id="e6110-115">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="e6110-116">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="e6110-116">Optional element.</span></span><br /><br /> <span data-ttu-id="e6110-117">Anger hur många tecken som den första raden av data ska flyttas till vänster.</span><span class="sxs-lookup"><span data-stu-id="e6110-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="e6110-118">FirstLineIndent Element</span><span class="sxs-lookup"><span data-stu-id="e6110-118">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="e6110-119">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="e6110-119">Optional element.</span></span><br /><br /> <span data-ttu-id="e6110-120">Anger hur många tecken som den första raden av data ska flyttas till höger.</span><span class="sxs-lookup"><span data-stu-id="e6110-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="e6110-121">LeftIndent Element</span><span class="sxs-lookup"><span data-stu-id="e6110-121">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="e6110-122">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="e6110-122">Optional element.</span></span><br /><br /> <span data-ttu-id="e6110-123">Anger hur många tecken som data ska flyttas från vänster marginal.</span><span class="sxs-lookup"><span data-stu-id="e6110-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="e6110-124">RightIndent Element</span><span class="sxs-lookup"><span data-stu-id="e6110-124">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="e6110-125">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="e6110-125">Optional element.</span></span><br /><br /> <span data-ttu-id="e6110-126">Anger hur många tecken som data ska flyttas från höger marginal.</span><span class="sxs-lookup"><span data-stu-id="e6110-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e6110-127">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="e6110-127">Parent Elements</span></span>

|<span data-ttu-id="e6110-128">Element</span><span class="sxs-lookup"><span data-stu-id="e6110-128">Element</span></span>|<span data-ttu-id="e6110-129">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e6110-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e6110-130">CustomItem Element för CustomEntry för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="e6110-130">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="e6110-131">Definierar vilka data som visas av kontrollen och hur de visas.</span><span class="sxs-lookup"><span data-stu-id="e6110-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e6110-132">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="e6110-132">Remarks</span></span>

<span data-ttu-id="e6110-133">Du kan inte ange den [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) och [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) element i samma `Frame` element.</span><span class="sxs-lookup"><span data-stu-id="e6110-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="e6110-134">Se även</span><span class="sxs-lookup"><span data-stu-id="e6110-134">See Also</span></span>

[<span data-ttu-id="e6110-135">FirstLineHanging Element</span><span class="sxs-lookup"><span data-stu-id="e6110-135">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="e6110-136">FirstLineIndent Element</span><span class="sxs-lookup"><span data-stu-id="e6110-136">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="e6110-137">LeftIndent Element</span><span class="sxs-lookup"><span data-stu-id="e6110-137">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="e6110-138">RightIndent Element</span><span class="sxs-lookup"><span data-stu-id="e6110-138">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="e6110-139">CustomItem Element för CustomEntry för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="e6110-139">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="e6110-140">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="e6110-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
