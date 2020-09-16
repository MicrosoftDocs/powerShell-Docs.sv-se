---
title: Namn element för kontroll för konfiguration (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 3d45ba98b909ebee18e01d2b6985a48906ce39d9
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783542"
---
# <a name="name-element-for-control-for-controls-for-configuration-format"></a><span data-ttu-id="3430d-102">Name-element för Control för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="3430d-102">Name Element for Control for Controls for Configuration (Format)</span></span>

<span data-ttu-id="3430d-103">Anger kontrollens namn.</span><span class="sxs-lookup"><span data-stu-id="3430d-103">Specifies the name of the control.</span></span> <span data-ttu-id="3430d-104">Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.</span><span class="sxs-lookup"><span data-stu-id="3430d-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="3430d-105">Konfigurations element (format) styr element i konfigurations element (format) kontroll element för kontroll av namn element för konfiguration (format) för kontroll för konfiguration av kontroller (format)</span><span class="sxs-lookup"><span data-stu-id="3430d-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) Name Element for Control for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3430d-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="3430d-106">Syntax</span></span>

```xml
<Name>NameOfControl</Name>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="3430d-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="3430d-107">Attributes and Elements</span></span>

<span data-ttu-id="3430d-108">I följande avsnitt beskrivs attribut, underordnade element och `Name` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="3430d-108">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3430d-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="3430d-109">Attributes</span></span>

<span data-ttu-id="3430d-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="3430d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3430d-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="3430d-111">Child Elements</span></span>

<span data-ttu-id="3430d-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="3430d-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3430d-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="3430d-113">Parent Elements</span></span>

|<span data-ttu-id="3430d-114">Element</span><span class="sxs-lookup"><span data-stu-id="3430d-114">Element</span></span>|<span data-ttu-id="3430d-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="3430d-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3430d-116">Control-element för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="3430d-116">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)|<span data-ttu-id="3430d-117">Definierar en gemensam kontroll som kan användas av alla vyer i format filen och det namn som används för att referera till kontrollen.</span><span class="sxs-lookup"><span data-stu-id="3430d-117">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3430d-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="3430d-118">Text Value</span></span>

<span data-ttu-id="3430d-119">Ange det namn som ska användas för att referera till den här kontrollen.</span><span class="sxs-lookup"><span data-stu-id="3430d-119">Specify the name that is used to reference this control.</span></span>

## <a name="remarks"></a><span data-ttu-id="3430d-120">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="3430d-120">Remarks</span></span>

<span data-ttu-id="3430d-121">Namnet som anges här kan användas i följande element för att referera till den här kontrollen.</span><span class="sxs-lookup"><span data-stu-id="3430d-121">The name specified here can be used in the following elements to reference this control.</span></span>

- <span data-ttu-id="3430d-122">När du skapar en tabell, lista, bred eller anpassad flikkontroll, kan kontrollen anges med följande element: [groupby-element för vy (format)](./groupby-element-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="3430d-122">When creating a table, list, wide or custom control view, the control can be specified by the following element: [GroupBy Element for View (Format)](./groupby-element-for-view-format.md)</span></span>

- <span data-ttu-id="3430d-123">När du skapar en annan gemensam kontroll, kan den här kontrollen anges av följande element: [ExpressionBinding-element för CustomItem för kontroller för konfiguration (format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)</span><span class="sxs-lookup"><span data-stu-id="3430d-123">When creating another common control, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for Configuration (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)</span></span>

- <span data-ttu-id="3430d-124">När du skapar en kontroll som kan användas av en vy, kan den här kontrollen anges med följande element: [ExpressionBinding-element för CustomItem för kontroller för vy (format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="3430d-124">When creating a control that can be used by a view, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="3430d-125">Se även</span><span class="sxs-lookup"><span data-stu-id="3430d-125">See Also</span></span>

[<span data-ttu-id="3430d-126">Control-element för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="3430d-126">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)

[<span data-ttu-id="3430d-127">ExpressionBinding-element för CustomItem för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="3430d-127">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="3430d-128">ExpressionBinding-element för CustomItem för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="3430d-128">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="3430d-129">GroupBy-element för View (format)</span><span class="sxs-lookup"><span data-stu-id="3430d-129">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="3430d-130">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="3430d-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
