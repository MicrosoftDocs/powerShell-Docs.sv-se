---
title: Kontrollera Element för kontrollerna för Visa (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1fd53f55-698d-4df5-bb9a-fe28dc3193e1
caps.latest.revision: 11
ms.openlocfilehash: df568ccb36a2646b983622cdf95718dd5cac62c3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066778"
---
# <a name="control-element-for-controls-for-view--format"></a><span data-ttu-id="09d0a-102">Control-element för Controls för View  (format)</span><span class="sxs-lookup"><span data-stu-id="09d0a-102">Control Element for Controls for View  (Format)</span></span>

<span data-ttu-id="09d0a-103">Definierar en kontroll som kan användas av vyn och det namn som används för att referera till kontrollen.</span><span class="sxs-lookup"><span data-stu-id="09d0a-103">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>

<span data-ttu-id="09d0a-104">Elementet (Format) ViewDefinitions Element (Format) visa konfigurationselement (Format) styr Element (Format) kontroll Element för kontroller för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="09d0a-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="09d0a-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="09d0a-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="09d0a-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="09d0a-106">Attributes and Elements</span></span>

<span data-ttu-id="09d0a-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `Control` element.</span><span class="sxs-lookup"><span data-stu-id="09d0a-107">The following sections describe the attributes, child elements, and the parent element of the `Control` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="09d0a-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="09d0a-108">Attributes</span></span>

<span data-ttu-id="09d0a-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="09d0a-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="09d0a-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="09d0a-110">Child Elements</span></span>

|<span data-ttu-id="09d0a-111">Element</span><span class="sxs-lookup"><span data-stu-id="09d0a-111">Element</span></span>|<span data-ttu-id="09d0a-112">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="09d0a-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="09d0a-113">Namnelement för kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="09d0a-113">Name Element for Control for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="09d0a-114">Element som krävs.</span><span class="sxs-lookup"><span data-stu-id="09d0a-114">Required element.</span></span><br /><br /> <span data-ttu-id="09d0a-115">Anger namnet på kontrollen.</span><span class="sxs-lookup"><span data-stu-id="09d0a-115">Specifies the name of the control.</span></span>|
|[<span data-ttu-id="09d0a-116">Anpassad kontroll Element för kontroll för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="09d0a-116">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="09d0a-117">Element som krävs.</span><span class="sxs-lookup"><span data-stu-id="09d0a-117">Required element.</span></span><br /><br /> <span data-ttu-id="09d0a-118">Definierar den kontroll som används av den här vyn.</span><span class="sxs-lookup"><span data-stu-id="09d0a-118">Defines the control used by this view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="09d0a-119">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="09d0a-119">Parent Elements</span></span>

|<span data-ttu-id="09d0a-120">Element</span><span class="sxs-lookup"><span data-stu-id="09d0a-120">Element</span></span>|<span data-ttu-id="09d0a-121">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="09d0a-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="09d0a-122">Kontroller Element (Format)</span><span class="sxs-lookup"><span data-stu-id="09d0a-122">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="09d0a-123">Definierar vyn kontroller som kan användas av en specifik vy.</span><span class="sxs-lookup"><span data-stu-id="09d0a-123">Defines the view controls that can be used by a specific view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="09d0a-124">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="09d0a-124">Remarks</span></span>

<span data-ttu-id="09d0a-125">Den här kontrollen kan anges med följande element:</span><span class="sxs-lookup"><span data-stu-id="09d0a-125">This control can be specified by the following elements:</span></span>

- [<span data-ttu-id="09d0a-126">CustomControlName Element för ExpressionBinding för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="09d0a-126">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [<span data-ttu-id="09d0a-127">CustomControlName Element för ExpressionBinding för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="09d0a-127">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [<span data-ttu-id="09d0a-128">CustomControlName Element för ExpressionBinding för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="09d0a-128">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [<span data-ttu-id="09d0a-129">CustomControlName Element för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="09d0a-129">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="09d0a-130">Se även</span><span class="sxs-lookup"><span data-stu-id="09d0a-130">See Also</span></span>

[<span data-ttu-id="09d0a-131">Anpassad kontroll Element för kontroll för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="09d0a-131">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="09d0a-132">CustomControlName Element för ExpressionBinding för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="09d0a-132">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="09d0a-133">CustomControlName Element för ExpressionBinding för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="09d0a-133">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="09d0a-134">CustomControlName Element för ExpressionBinding för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="09d0a-134">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="09d0a-135">CustomControlName Element för ExpressionBinding för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="09d0a-135">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="09d0a-136">Kontroller Element (Format)</span><span class="sxs-lookup"><span data-stu-id="09d0a-136">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="09d0a-137">Namnelement för kontroll för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="09d0a-137">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="09d0a-138">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="09d0a-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
