---
ms.date: 09/13/2016
ms.topic: reference
title: Name-element för Control för Controls för Configuration (format)
description: Name-element för Control för Controls för Configuration (format)
ms.openlocfilehash: 0c1c83f827482886ca742f2c0174e8383f87fb52
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92666509"
---
# <a name="name-element-for-control-for-controls-for-configuration-format"></a><span data-ttu-id="ac8bf-103">Name-element för Control för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="ac8bf-103">Name Element for Control for Controls for Configuration (Format)</span></span>

<span data-ttu-id="ac8bf-104">Anger kontrollens namn.</span><span class="sxs-lookup"><span data-stu-id="ac8bf-104">Specifies the name of the control.</span></span> <span data-ttu-id="ac8bf-105">Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.</span><span class="sxs-lookup"><span data-stu-id="ac8bf-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="ac8bf-106">Konfigurations element (format) styr element i konfigurations element (format) kontroll element för kontroll av namn element för konfiguration (format) för kontroll för konfiguration av kontroller (format)</span><span class="sxs-lookup"><span data-stu-id="ac8bf-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) Name Element for Control for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ac8bf-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="ac8bf-107">Syntax</span></span>

```xml
<Name>NameOfControl</Name>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="ac8bf-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="ac8bf-108">Attributes and Elements</span></span>

<span data-ttu-id="ac8bf-109">I följande avsnitt beskrivs attribut, underordnade element och `Name` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="ac8bf-109">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ac8bf-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="ac8bf-110">Attributes</span></span>

<span data-ttu-id="ac8bf-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="ac8bf-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ac8bf-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="ac8bf-112">Child Elements</span></span>

<span data-ttu-id="ac8bf-113">Inga.</span><span class="sxs-lookup"><span data-stu-id="ac8bf-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ac8bf-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="ac8bf-114">Parent Elements</span></span>

|<span data-ttu-id="ac8bf-115">Element</span><span class="sxs-lookup"><span data-stu-id="ac8bf-115">Element</span></span>|<span data-ttu-id="ac8bf-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ac8bf-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ac8bf-117">Control-element för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="ac8bf-117">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)|<span data-ttu-id="ac8bf-118">Definierar en gemensam kontroll som kan användas av alla vyer i format filen och det namn som används för att referera till kontrollen.</span><span class="sxs-lookup"><span data-stu-id="ac8bf-118">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ac8bf-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="ac8bf-119">Text Value</span></span>

<span data-ttu-id="ac8bf-120">Ange det namn som ska användas för att referera till den här kontrollen.</span><span class="sxs-lookup"><span data-stu-id="ac8bf-120">Specify the name that is used to reference this control.</span></span>

## <a name="remarks"></a><span data-ttu-id="ac8bf-121">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="ac8bf-121">Remarks</span></span>

<span data-ttu-id="ac8bf-122">Namnet som anges här kan användas i följande element för att referera till den här kontrollen.</span><span class="sxs-lookup"><span data-stu-id="ac8bf-122">The name specified here can be used in the following elements to reference this control.</span></span>

- <span data-ttu-id="ac8bf-123">När du skapar en tabell, lista, bred eller anpassad flikkontroll, kan kontrollen anges med följande element: [groupby-element för vy (format)](./groupby-element-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="ac8bf-123">When creating a table, list, wide or custom control view, the control can be specified by the following element: [GroupBy Element for View (Format)](./groupby-element-for-view-format.md)</span></span>

- <span data-ttu-id="ac8bf-124">När du skapar en annan gemensam kontroll, kan den här kontrollen anges av följande element: [ExpressionBinding-element för CustomItem för kontroller för konfiguration (format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)</span><span class="sxs-lookup"><span data-stu-id="ac8bf-124">When creating another common control, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for Configuration (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)</span></span>

- <span data-ttu-id="ac8bf-125">När du skapar en kontroll som kan användas av en vy, kan den här kontrollen anges med följande element: [ExpressionBinding-element för CustomItem för kontroller för vy (format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="ac8bf-125">When creating a control that can be used by a view, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="ac8bf-126">Se även</span><span class="sxs-lookup"><span data-stu-id="ac8bf-126">See Also</span></span>

[<span data-ttu-id="ac8bf-127">Control-element för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="ac8bf-127">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)

[<span data-ttu-id="ac8bf-128">ExpressionBinding-element för CustomItem för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="ac8bf-128">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="ac8bf-129">ExpressionBinding-element för CustomItem för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="ac8bf-129">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="ac8bf-130">GroupBy-element för View (format)</span><span class="sxs-lookup"><span data-stu-id="ac8bf-130">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="ac8bf-131">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="ac8bf-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
