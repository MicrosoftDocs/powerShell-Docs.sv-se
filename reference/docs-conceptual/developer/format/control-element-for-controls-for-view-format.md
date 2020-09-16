---
title: Kontroll element för kontroller för vy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 13ea2f09aec7fea8e5460197f133b5f5219cd369
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783814"
---
# <a name="control-element-for-controls-for-view--format"></a><span data-ttu-id="acdb3-102">Control-element för Controls för View  (format)</span><span class="sxs-lookup"><span data-stu-id="acdb3-102">Control Element for Controls for View  (Format)</span></span>

<span data-ttu-id="acdb3-103">Definierar en kontroll som kan användas av vyn och det namn som används för att referera till kontrollen.</span><span class="sxs-lookup"><span data-stu-id="acdb3-103">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>

<span data-ttu-id="acdb3-104">Konfigurations element (format) ViewDefinitions element (format) View-element (format) styr element (format) styr element (format) kontroll element för vyer (format)</span><span class="sxs-lookup"><span data-stu-id="acdb3-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="acdb3-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="acdb3-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="acdb3-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="acdb3-106">Attributes and Elements</span></span>

<span data-ttu-id="acdb3-107">I följande avsnitt beskrivs attributen, underordnade element och `Control` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="acdb3-107">The following sections describe the attributes, child elements, and the parent element of the `Control` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="acdb3-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="acdb3-108">Attributes</span></span>

<span data-ttu-id="acdb3-109">Inga.</span><span class="sxs-lookup"><span data-stu-id="acdb3-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="acdb3-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="acdb3-110">Child Elements</span></span>

|<span data-ttu-id="acdb3-111">Element</span><span class="sxs-lookup"><span data-stu-id="acdb3-111">Element</span></span>|<span data-ttu-id="acdb3-112">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="acdb3-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="acdb3-113">Namn element för kontroll för vy (format)</span><span class="sxs-lookup"><span data-stu-id="acdb3-113">Name Element for Control for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="acdb3-114">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="acdb3-114">Required element.</span></span><br /><br /> <span data-ttu-id="acdb3-115">Anger kontrollens namn.</span><span class="sxs-lookup"><span data-stu-id="acdb3-115">Specifies the name of the control.</span></span>|
|[<span data-ttu-id="acdb3-116">CustomControl-element för Control för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="acdb3-116">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="acdb3-117">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="acdb3-117">Required element.</span></span><br /><br /> <span data-ttu-id="acdb3-118">Definierar den kontroll som används i den här vyn.</span><span class="sxs-lookup"><span data-stu-id="acdb3-118">Defines the control used by this view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="acdb3-119">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="acdb3-119">Parent Elements</span></span>

|<span data-ttu-id="acdb3-120">Element</span><span class="sxs-lookup"><span data-stu-id="acdb3-120">Element</span></span>|<span data-ttu-id="acdb3-121">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="acdb3-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="acdb3-122">Kontrollerar element (format)</span><span class="sxs-lookup"><span data-stu-id="acdb3-122">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="acdb3-123">Definierar de visnings kontroller som kan användas av en speciell vy.</span><span class="sxs-lookup"><span data-stu-id="acdb3-123">Defines the view controls that can be used by a specific view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="acdb3-124">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="acdb3-124">Remarks</span></span>

<span data-ttu-id="acdb3-125">Den här kontrollen kan anges med följande element:</span><span class="sxs-lookup"><span data-stu-id="acdb3-125">This control can be specified by the following elements:</span></span>

- [<span data-ttu-id="acdb3-126">CustomControlName-element för ExpressionBinding för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="acdb3-126">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [<span data-ttu-id="acdb3-127">CustomControlName-element för ExpressionBinding för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="acdb3-127">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [<span data-ttu-id="acdb3-128">CustomControlName-element för ExpressionBinding för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="acdb3-128">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [<span data-ttu-id="acdb3-129">CustomControlName-element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="acdb3-129">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="acdb3-130">Se även</span><span class="sxs-lookup"><span data-stu-id="acdb3-130">See Also</span></span>

[<span data-ttu-id="acdb3-131">CustomControl-element för Control för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="acdb3-131">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="acdb3-132">CustomControlName-element för ExpressionBinding för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="acdb3-132">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="acdb3-133">CustomControlName-element för ExpressionBinding för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="acdb3-133">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="acdb3-134">CustomControlName-element för ExpressionBinding för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="acdb3-134">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="acdb3-135">CustomControlName-element för ExpressionBinding för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="acdb3-135">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="acdb3-136">Kontrollerar element (format)</span><span class="sxs-lookup"><span data-stu-id="acdb3-136">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="acdb3-137">Name-element för Control för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="acdb3-137">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="acdb3-138">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="acdb3-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
