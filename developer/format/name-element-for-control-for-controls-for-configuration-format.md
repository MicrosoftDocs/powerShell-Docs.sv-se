---
title: Namnge Element för kontroll för kontroller för konfiguration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4371d45-49a4-4303-8384-5b54105bd0d6
caps.latest.revision: 8
ms.openlocfilehash: 2704a530e0ae269efb772ac10e531bcbb12f6eff
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849674"
---
# <a name="name-element-for-control-for-controls-for-configuration-format"></a><span data-ttu-id="2259f-102">Name-element för Control för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="2259f-102">Name Element for Control for Controls for Configuration (Format)</span></span>

<span data-ttu-id="2259f-103">Anger namnet på kontrollen.</span><span class="sxs-lookup"><span data-stu-id="2259f-103">Specifies the name of the control.</span></span> <span data-ttu-id="2259f-104">Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.</span><span class="sxs-lookup"><span data-stu-id="2259f-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="2259f-105">Konfigurationselementet Element (Format) kontroller av (Format) kontroll konfigurationselement för kontroller för Configuration (Format) namnelement för kontroll för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="2259f-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) Name Element for Control for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2259f-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="2259f-106">Syntax</span></span>

```xml
<Name>NameOfControl</Name>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="2259f-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="2259f-107">Attributes and Elements</span></span>

<span data-ttu-id="2259f-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `Name` element.</span><span class="sxs-lookup"><span data-stu-id="2259f-108">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2259f-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="2259f-109">Attributes</span></span>

<span data-ttu-id="2259f-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="2259f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2259f-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="2259f-111">Child Elements</span></span>

<span data-ttu-id="2259f-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="2259f-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2259f-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="2259f-113">Parent Elements</span></span>

|<span data-ttu-id="2259f-114">Element</span><span class="sxs-lookup"><span data-stu-id="2259f-114">Element</span></span>|<span data-ttu-id="2259f-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="2259f-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2259f-116">Control-Element för kontroller för Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="2259f-116">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)|<span data-ttu-id="2259f-117">Definierar en gemensam kontroll som kan användas av alla vyer av filen formatering och det namn som används för att referera till kontrollen.</span><span class="sxs-lookup"><span data-stu-id="2259f-117">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2259f-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="2259f-118">Text Value</span></span>

<span data-ttu-id="2259f-119">Ange ett namn som används för att referera till den här kontrollen.</span><span class="sxs-lookup"><span data-stu-id="2259f-119">Specify the name that is used to reference this control.</span></span>

## <a name="remarks"></a><span data-ttu-id="2259f-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="2259f-120">Remarks</span></span>

<span data-ttu-id="2259f-121">Namnet som anges här kan användas i följande element för att referera till den här kontrollen.</span><span class="sxs-lookup"><span data-stu-id="2259f-121">The name specified here can be used in the following elements to reference this control.</span></span>

- <span data-ttu-id="2259f-122">När du skapar en tabell, lista, brett eller anpassade vy, kan kontrollen anges med följande element: [GroupBy-Element för Visa (Format)](./groupby-element-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="2259f-122">When creating a table, list, wide or custom control view, the control can be specified by the following element: [GroupBy Element for View (Format)](./groupby-element-for-view-format.md)</span></span>

- <span data-ttu-id="2259f-123">När du skapar en annan vanliga kontroll, kan den här kontrollen anges med följande element: [ExpressionBinding Element för CustomItem för kontroller för konfiguration (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)</span><span class="sxs-lookup"><span data-stu-id="2259f-123">When creating another common control, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for Configuration (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)</span></span>

- <span data-ttu-id="2259f-124">När du skapar en kontroll som kan användas av en vy, kan den här kontrollen anges med följande element: [ExpressionBinding Element för CustomItem för kontroller för att visa (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="2259f-124">When creating a control that can be used by a view, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="2259f-125">Se även</span><span class="sxs-lookup"><span data-stu-id="2259f-125">See Also</span></span>

[<span data-ttu-id="2259f-126">Control-Element för kontroller för Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="2259f-126">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)

[<span data-ttu-id="2259f-127">ExpressionBinding Element för CustomItem för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="2259f-127">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="2259f-128">ExpressionBinding Element för CustomItem för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="2259f-128">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="2259f-129">GroupBy-Element för Visa (Format)</span><span class="sxs-lookup"><span data-stu-id="2259f-129">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="2259f-130">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="2259f-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
