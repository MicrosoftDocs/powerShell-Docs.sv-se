---
title: Frame-element för CustomItem för CustomControl för vy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e1a13100-41a4-4847-9f07-458c85783505
caps.latest.revision: 6
ms.openlocfilehash: 925ef86e61801f5a66f89dd25e0756f00dd35155
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354973"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="d3309-102">Frame-element för CustomItem för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="d3309-102">Frame Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="d3309-103">Definierar hur data visas, till exempel att flytta data till vänster eller höger.</span><span class="sxs-lookup"><span data-stu-id="d3309-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="d3309-104">Det här elementet används när du definierar en anpassad kontrol vy.</span><span class="sxs-lookup"><span data-stu-id="d3309-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="d3309-105">Konfigurations element (format) ViewDefinitions element (format) View element (format) CustomControl element (format) CustomEntries-element för CustomControl för View (format) CustomEntry-element för CustomEntries för View (format) CustomItem-element för CustomEntry för CustomControlView (format) för CustomItem för CustomControl för vy (format)</span><span class="sxs-lookup"><span data-stu-id="d3309-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CustomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d3309-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="d3309-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d3309-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="d3309-107">Attributes and Elements</span></span>

<span data-ttu-id="d3309-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `Frame`-elementet.</span><span class="sxs-lookup"><span data-stu-id="d3309-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d3309-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="d3309-109">Attributes</span></span>

<span data-ttu-id="d3309-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="d3309-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d3309-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="d3309-111">Child Elements</span></span>

|<span data-ttu-id="d3309-112">Element</span><span class="sxs-lookup"><span data-stu-id="d3309-112">Element</span></span>|<span data-ttu-id="d3309-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d3309-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="d3309-114">Nödvändigt element</span><span class="sxs-lookup"><span data-stu-id="d3309-114">Required Element</span></span>|
|[<span data-ttu-id="d3309-115">FirstLineHanging-element</span><span class="sxs-lookup"><span data-stu-id="d3309-115">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="d3309-116">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="d3309-116">Optional element.</span></span><br /><br /> <span data-ttu-id="d3309-117">Anger hur många tecken den första raden med data flyttas till vänster.</span><span class="sxs-lookup"><span data-stu-id="d3309-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="d3309-118">FirstLineIndent-element</span><span class="sxs-lookup"><span data-stu-id="d3309-118">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="d3309-119">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="d3309-119">Optional element.</span></span><br /><br /> <span data-ttu-id="d3309-120">Anger hur många tecken den första raden med data flyttas till höger.</span><span class="sxs-lookup"><span data-stu-id="d3309-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="d3309-121">LeftIndent-element</span><span class="sxs-lookup"><span data-stu-id="d3309-121">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="d3309-122">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="d3309-122">Optional element.</span></span><br /><br /> <span data-ttu-id="d3309-123">Anger hur många tecken data flyttas bort från vänstermarginalen.</span><span class="sxs-lookup"><span data-stu-id="d3309-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="d3309-124">RightIndent-element</span><span class="sxs-lookup"><span data-stu-id="d3309-124">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="d3309-125">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="d3309-125">Optional element.</span></span><br /><br /> <span data-ttu-id="d3309-126">Anger hur många tecken data flyttas bort från högermarginalen.</span><span class="sxs-lookup"><span data-stu-id="d3309-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d3309-127">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="d3309-127">Parent Elements</span></span>

|<span data-ttu-id="d3309-128">Element</span><span class="sxs-lookup"><span data-stu-id="d3309-128">Element</span></span>|<span data-ttu-id="d3309-129">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d3309-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d3309-130">CustomItem-element för CustomEntry för vy (format)</span><span class="sxs-lookup"><span data-stu-id="d3309-130">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="d3309-131">Definierar vilka data som visas av kontrollen och hur de visas.</span><span class="sxs-lookup"><span data-stu-id="d3309-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d3309-132">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="d3309-132">Remarks</span></span>

<span data-ttu-id="d3309-133">Du kan inte ange [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) och [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) -elementen i samma `Frame`-element.</span><span class="sxs-lookup"><span data-stu-id="d3309-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="d3309-134">Se även</span><span class="sxs-lookup"><span data-stu-id="d3309-134">See Also</span></span>

[<span data-ttu-id="d3309-135">FirstLineHanging-element</span><span class="sxs-lookup"><span data-stu-id="d3309-135">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="d3309-136">FirstLineIndent-element</span><span class="sxs-lookup"><span data-stu-id="d3309-136">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="d3309-137">LeftIndent-element</span><span class="sxs-lookup"><span data-stu-id="d3309-137">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="d3309-138">RightIndent-element</span><span class="sxs-lookup"><span data-stu-id="d3309-138">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="d3309-139">CustomItem-element för CustomEntry för vy (format)</span><span class="sxs-lookup"><span data-stu-id="d3309-139">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="d3309-140">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="d3309-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
