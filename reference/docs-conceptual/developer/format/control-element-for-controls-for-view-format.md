---
title: Kontroll element för kontroller för vy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1fd53f55-698d-4df5-bb9a-fe28dc3193e1
caps.latest.revision: 11
ms.openlocfilehash: df568ccb36a2646b983622cdf95718dd5cac62c3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354854"
---
# <a name="control-element-for-controls-for-view--format"></a><span data-ttu-id="cb4ac-102">Control-element för Controls för View  (format)</span><span class="sxs-lookup"><span data-stu-id="cb4ac-102">Control Element for Controls for View  (Format)</span></span>

<span data-ttu-id="cb4ac-103">Definierar en kontroll som kan användas av vyn och det namn som används för att referera till kontrollen.</span><span class="sxs-lookup"><span data-stu-id="cb4ac-103">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>

<span data-ttu-id="cb4ac-104">Konfigurations element (format) ViewDefinitions element (format) View-element (format) styr element (format) styr element (format) kontroll element för vyer (format)</span><span class="sxs-lookup"><span data-stu-id="cb4ac-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cb4ac-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="cb4ac-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cb4ac-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="cb4ac-106">Attributes and Elements</span></span>

<span data-ttu-id="cb4ac-107">I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet i `Control`-elementet.</span><span class="sxs-lookup"><span data-stu-id="cb4ac-107">The following sections describe the attributes, child elements, and the parent element of the `Control` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="cb4ac-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="cb4ac-108">Attributes</span></span>

<span data-ttu-id="cb4ac-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="cb4ac-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cb4ac-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="cb4ac-110">Child Elements</span></span>

|<span data-ttu-id="cb4ac-111">Element</span><span class="sxs-lookup"><span data-stu-id="cb4ac-111">Element</span></span>|<span data-ttu-id="cb4ac-112">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="cb4ac-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cb4ac-113">Namn element för kontroll för vy (format)</span><span class="sxs-lookup"><span data-stu-id="cb4ac-113">Name Element for Control for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="cb4ac-114">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="cb4ac-114">Required element.</span></span><br /><br /> <span data-ttu-id="cb4ac-115">Anger kontrollens namn.</span><span class="sxs-lookup"><span data-stu-id="cb4ac-115">Specifies the name of the control.</span></span>|
|[<span data-ttu-id="cb4ac-116">CustomControl-element för kontroll för vy (format)</span><span class="sxs-lookup"><span data-stu-id="cb4ac-116">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="cb4ac-117">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="cb4ac-117">Required element.</span></span><br /><br /> <span data-ttu-id="cb4ac-118">Definierar den kontroll som används i den här vyn.</span><span class="sxs-lookup"><span data-stu-id="cb4ac-118">Defines the control used by this view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="cb4ac-119">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="cb4ac-119">Parent Elements</span></span>

|<span data-ttu-id="cb4ac-120">Element</span><span class="sxs-lookup"><span data-stu-id="cb4ac-120">Element</span></span>|<span data-ttu-id="cb4ac-121">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="cb4ac-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cb4ac-122">Kontrollerar element (format)</span><span class="sxs-lookup"><span data-stu-id="cb4ac-122">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="cb4ac-123">Definierar de visnings kontroller som kan användas av en speciell vy.</span><span class="sxs-lookup"><span data-stu-id="cb4ac-123">Defines the view controls that can be used by a specific view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="cb4ac-124">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="cb4ac-124">Remarks</span></span>

<span data-ttu-id="cb4ac-125">Den här kontrollen kan anges med följande element:</span><span class="sxs-lookup"><span data-stu-id="cb4ac-125">This control can be specified by the following elements:</span></span>

- [<span data-ttu-id="cb4ac-126">CustomControlName-element för ExpressionBinding för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="cb4ac-126">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [<span data-ttu-id="cb4ac-127">CustomControlName-element för ExpressionBinding för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="cb4ac-127">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [<span data-ttu-id="cb4ac-128">CustomControlName-element för ExpressionBinding för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="cb4ac-128">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [<span data-ttu-id="cb4ac-129">CustomControlName-element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="cb4ac-129">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="cb4ac-130">Se även</span><span class="sxs-lookup"><span data-stu-id="cb4ac-130">See Also</span></span>

[<span data-ttu-id="cb4ac-131">CustomControl-element för kontroll för vy (format)</span><span class="sxs-lookup"><span data-stu-id="cb4ac-131">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="cb4ac-132">CustomControlName-element för ExpressionBinding för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="cb4ac-132">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="cb4ac-133">CustomControlName-element för ExpressionBinding för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="cb4ac-133">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="cb4ac-134">CustomControlName-element för ExpressionBinding för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="cb4ac-134">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="cb4ac-135">CustomControlName-element för ExpressionBinding för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="cb4ac-135">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="cb4ac-136">Kontrollerar element (format)</span><span class="sxs-lookup"><span data-stu-id="cb4ac-136">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="cb4ac-137">Namn element för kontroll för vy (format)</span><span class="sxs-lookup"><span data-stu-id="cb4ac-137">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="cb4ac-138">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="cb4ac-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
