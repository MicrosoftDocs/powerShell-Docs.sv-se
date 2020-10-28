---
ms.date: 09/13/2016
ms.topic: reference
title: Control-element för Controls för View  (format)
description: Control-element för Controls för View  (format)
ms.openlocfilehash: c48b8b7ecaebfde5e6ed2123b837d92561551766
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92668090"
---
# <a name="control-element-for-controls-for-view--format"></a><span data-ttu-id="41132-103">Control-element för Controls för View  (format)</span><span class="sxs-lookup"><span data-stu-id="41132-103">Control Element for Controls for View  (Format)</span></span>

<span data-ttu-id="41132-104">Definierar en kontroll som kan användas av vyn och det namn som används för att referera till kontrollen.</span><span class="sxs-lookup"><span data-stu-id="41132-104">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>

<span data-ttu-id="41132-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) styr element (format) styr element (format) kontroll element för vyer (format)</span><span class="sxs-lookup"><span data-stu-id="41132-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="41132-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="41132-106">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="41132-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="41132-107">Attributes and Elements</span></span>

<span data-ttu-id="41132-108">I följande avsnitt beskrivs attributen, underordnade element och `Control` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="41132-108">The following sections describe the attributes, child elements, and the parent element of the `Control` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="41132-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="41132-109">Attributes</span></span>

<span data-ttu-id="41132-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="41132-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="41132-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="41132-111">Child Elements</span></span>

|<span data-ttu-id="41132-112">Element</span><span class="sxs-lookup"><span data-stu-id="41132-112">Element</span></span>|<span data-ttu-id="41132-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="41132-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="41132-114">Namn element för kontroll för vy (format)</span><span class="sxs-lookup"><span data-stu-id="41132-114">Name Element for Control for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="41132-115">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="41132-115">Required element.</span></span><br /><br /> <span data-ttu-id="41132-116">Anger kontrollens namn.</span><span class="sxs-lookup"><span data-stu-id="41132-116">Specifies the name of the control.</span></span>|
|[<span data-ttu-id="41132-117">CustomControl-element för Control för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="41132-117">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="41132-118">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="41132-118">Required element.</span></span><br /><br /> <span data-ttu-id="41132-119">Definierar den kontroll som används i den här vyn.</span><span class="sxs-lookup"><span data-stu-id="41132-119">Defines the control used by this view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="41132-120">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="41132-120">Parent Elements</span></span>

|<span data-ttu-id="41132-121">Element</span><span class="sxs-lookup"><span data-stu-id="41132-121">Element</span></span>|<span data-ttu-id="41132-122">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="41132-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="41132-123">Kontrollerar element (format)</span><span class="sxs-lookup"><span data-stu-id="41132-123">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="41132-124">Definierar de visnings kontroller som kan användas av en speciell vy.</span><span class="sxs-lookup"><span data-stu-id="41132-124">Defines the view controls that can be used by a specific view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="41132-125">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="41132-125">Remarks</span></span>

<span data-ttu-id="41132-126">Den här kontrollen kan anges med följande element:</span><span class="sxs-lookup"><span data-stu-id="41132-126">This control can be specified by the following elements:</span></span>

- [<span data-ttu-id="41132-127">CustomControlName-element för ExpressionBinding för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="41132-127">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [<span data-ttu-id="41132-128">CustomControlName-element för ExpressionBinding för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="41132-128">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [<span data-ttu-id="41132-129">CustomControlName-element för ExpressionBinding för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="41132-129">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [<span data-ttu-id="41132-130">CustomControlName-element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="41132-130">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="41132-131">Se även</span><span class="sxs-lookup"><span data-stu-id="41132-131">See Also</span></span>

[<span data-ttu-id="41132-132">CustomControl-element för Control för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="41132-132">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="41132-133">CustomControlName-element för ExpressionBinding för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="41132-133">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="41132-134">CustomControlName-element för ExpressionBinding för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="41132-134">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="41132-135">CustomControlName-element för ExpressionBinding för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="41132-135">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="41132-136">CustomControlName-element för ExpressionBinding för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="41132-136">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="41132-137">Kontrollerar element (format)</span><span class="sxs-lookup"><span data-stu-id="41132-137">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="41132-138">Name-element för Control för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="41132-138">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="41132-139">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="41132-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
