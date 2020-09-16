---
title: Frame-element för CustomItem för CustomControl för vy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4864ea1a865f77c9de6e495d7e8296e81c19b366
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781451"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="1c88e-102">Frame-element för CustomItem för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="1c88e-102">Frame Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="1c88e-103">Definierar hur data visas, till exempel att flytta data till vänster eller höger.</span><span class="sxs-lookup"><span data-stu-id="1c88e-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="1c88e-104">Det här elementet används när du definierar en anpassad kontrol vy.</span><span class="sxs-lookup"><span data-stu-id="1c88e-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="1c88e-105">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) CustomControl element (format) CustomEntries-element för CustomControl för View (format) CustomEntry-element för CustomEntries för View (format) CustomItem-element för CustomEntry för CustomControlView (format) för CustomItem för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="1c88e-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CustomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1c88e-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="1c88e-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1c88e-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="1c88e-107">Attributes and Elements</span></span>

<span data-ttu-id="1c88e-108">I följande avsnitt beskrivs attribut, underordnade element och `Frame` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="1c88e-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1c88e-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="1c88e-109">Attributes</span></span>

<span data-ttu-id="1c88e-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="1c88e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1c88e-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="1c88e-111">Child Elements</span></span>

|<span data-ttu-id="1c88e-112">Element</span><span class="sxs-lookup"><span data-stu-id="1c88e-112">Element</span></span>|<span data-ttu-id="1c88e-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="1c88e-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="1c88e-114">Nödvändigt element</span><span class="sxs-lookup"><span data-stu-id="1c88e-114">Required Element</span></span>|
|[<span data-ttu-id="1c88e-115">FirstLineHanging-element</span><span class="sxs-lookup"><span data-stu-id="1c88e-115">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="1c88e-116">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="1c88e-116">Optional element.</span></span><br /><br /> <span data-ttu-id="1c88e-117">Anger hur många tecken den första raden med data flyttas till vänster.</span><span class="sxs-lookup"><span data-stu-id="1c88e-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="1c88e-118">FirstLineIndent-element</span><span class="sxs-lookup"><span data-stu-id="1c88e-118">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="1c88e-119">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="1c88e-119">Optional element.</span></span><br /><br /> <span data-ttu-id="1c88e-120">Anger hur många tecken den första raden med data flyttas till höger.</span><span class="sxs-lookup"><span data-stu-id="1c88e-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="1c88e-121">LeftIndent-element</span><span class="sxs-lookup"><span data-stu-id="1c88e-121">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="1c88e-122">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="1c88e-122">Optional element.</span></span><br /><br /> <span data-ttu-id="1c88e-123">Anger hur många tecken data flyttas bort från vänstermarginalen.</span><span class="sxs-lookup"><span data-stu-id="1c88e-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="1c88e-124">RightIndent-element</span><span class="sxs-lookup"><span data-stu-id="1c88e-124">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="1c88e-125">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="1c88e-125">Optional element.</span></span><br /><br /> <span data-ttu-id="1c88e-126">Anger hur många tecken data flyttas bort från högermarginalen.</span><span class="sxs-lookup"><span data-stu-id="1c88e-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="1c88e-127">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="1c88e-127">Parent Elements</span></span>

|<span data-ttu-id="1c88e-128">Element</span><span class="sxs-lookup"><span data-stu-id="1c88e-128">Element</span></span>|<span data-ttu-id="1c88e-129">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="1c88e-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1c88e-130">CustomItem-element för CustomEntry för vy (format)</span><span class="sxs-lookup"><span data-stu-id="1c88e-130">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="1c88e-131">Definierar vilka data som visas av kontrollen och hur de visas.</span><span class="sxs-lookup"><span data-stu-id="1c88e-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1c88e-132">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="1c88e-132">Remarks</span></span>

<span data-ttu-id="1c88e-133">Du kan inte ange [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) och [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) -elementen i samma `Frame` element.</span><span class="sxs-lookup"><span data-stu-id="1c88e-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="1c88e-134">Se även</span><span class="sxs-lookup"><span data-stu-id="1c88e-134">See Also</span></span>

[<span data-ttu-id="1c88e-135">FirstLineHanging-element</span><span class="sxs-lookup"><span data-stu-id="1c88e-135">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="1c88e-136">FirstLineIndent-element</span><span class="sxs-lookup"><span data-stu-id="1c88e-136">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="1c88e-137">LeftIndent-element</span><span class="sxs-lookup"><span data-stu-id="1c88e-137">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="1c88e-138">RightIndent-element</span><span class="sxs-lookup"><span data-stu-id="1c88e-138">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="1c88e-139">CustomItem-element för CustomEntry för vy (format)</span><span class="sxs-lookup"><span data-stu-id="1c88e-139">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="1c88e-140">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="1c88e-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
