---
ms.date: 09/13/2016
ms.topic: reference
title: Name-element för Control för Controls för View (format)
description: Name-element för Control för Controls för View (format)
ms.openlocfilehash: 52b7170777a35596767c34f2d58106dfa6479567
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92666492"
---
# <a name="name-element-for-control-for-controls-for-view-format"></a><span data-ttu-id="c1b8b-103">Name-element för Control för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="c1b8b-103">Name Element for Control for Controls for View (Format)</span></span>

<span data-ttu-id="c1b8b-104">Anger kontrollens namn.</span><span class="sxs-lookup"><span data-stu-id="c1b8b-104">Specifies the name of the control.</span></span>

<span data-ttu-id="c1b8b-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) styr element (format) styr element (format) styr element för att visa (format)-elementet för kontroll av visnings namn (format)</span><span class="sxs-lookup"><span data-stu-id="c1b8b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) Name Element for Control for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c1b8b-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="c1b8b-106">Syntax</span></span>

```xml
<Name>ControlName</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c1b8b-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="c1b8b-107">Attributes and Elements</span></span>

<span data-ttu-id="c1b8b-108">I följande avsnitt beskrivs attribut, underordnade element och `Name` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="c1b8b-108">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c1b8b-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="c1b8b-109">Attributes</span></span>

<span data-ttu-id="c1b8b-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="c1b8b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c1b8b-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="c1b8b-111">Child Elements</span></span>

<span data-ttu-id="c1b8b-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="c1b8b-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c1b8b-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="c1b8b-113">Parent Elements</span></span>

|<span data-ttu-id="c1b8b-114">Element</span><span class="sxs-lookup"><span data-stu-id="c1b8b-114">Element</span></span>|<span data-ttu-id="c1b8b-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c1b8b-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c1b8b-116">Kontroll element för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="c1b8b-116">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)|<span data-ttu-id="c1b8b-117">Definierar en kontroll som kan användas av vyn och det namn som används för att referera till kontrollen.</span><span class="sxs-lookup"><span data-stu-id="c1b8b-117">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c1b8b-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="c1b8b-118">Text Value</span></span>

<span data-ttu-id="c1b8b-119">Ange det namn som ska användas för att referera till kontrollen.</span><span class="sxs-lookup"><span data-stu-id="c1b8b-119">Specify the name that is used to reference the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="c1b8b-120">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="c1b8b-120">Remarks</span></span>

<span data-ttu-id="c1b8b-121">Namnet som anges här kan användas i följande element för att referera till den här kontrollen.</span><span class="sxs-lookup"><span data-stu-id="c1b8b-121">The name specified here can be used in the following elements to reference this control.</span></span>

- <span data-ttu-id="c1b8b-122">När du skapar en tabell, lista, bred eller anpassad flikkontroll, kan kontrollen anges med följande element: [groupby-element för vy (format)](./groupby-element-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="c1b8b-122">When creating a table, list, wide or custom control view, the control can be specified by the following element: [GroupBy Element for View (Format)](./groupby-element-for-view-format.md)</span></span>

- <span data-ttu-id="c1b8b-123">När du skapar en annan kontroll som kan användas av en vy, kan den här kontrollen anges av följande element: [ExpressionBinding-element för CustomItem för kontroller för visning (format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="c1b8b-123">When creating another control that can be used by a view, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="c1b8b-124">Se även</span><span class="sxs-lookup"><span data-stu-id="c1b8b-124">See Also</span></span>

[<span data-ttu-id="c1b8b-125">GroupBy-element för View (format)</span><span class="sxs-lookup"><span data-stu-id="c1b8b-125">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="c1b8b-126">ExpressionBinding-element för CustomItem för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="c1b8b-126">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="c1b8b-127">Kontroll element för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="c1b8b-127">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)

[<span data-ttu-id="c1b8b-128">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="c1b8b-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
