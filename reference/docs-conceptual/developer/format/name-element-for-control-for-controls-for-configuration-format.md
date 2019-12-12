---
title: Namn element för kontroll för konfiguration (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4371d45-49a4-4303-8384-5b54105bd0d6
caps.latest.revision: 8
ms.openlocfilehash: 2704a530e0ae269efb772ac10e531bcbb12f6eff
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354322"
---
# <a name="name-element-for-control-for-controls-for-configuration-format"></a><span data-ttu-id="6cfca-102">Name-element för Control för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="6cfca-102">Name Element for Control for Controls for Configuration (Format)</span></span>

<span data-ttu-id="6cfca-103">Anger kontrollens namn.</span><span class="sxs-lookup"><span data-stu-id="6cfca-103">Specifies the name of the control.</span></span> <span data-ttu-id="6cfca-104">Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.</span><span class="sxs-lookup"><span data-stu-id="6cfca-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="6cfca-105">Konfigurations element (format) styr element i konfigurations element (format) kontroll element för kontroll av namn element för konfiguration (format) för kontroll för konfiguration av kontroller (format)</span><span class="sxs-lookup"><span data-stu-id="6cfca-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) Name Element for Control for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6cfca-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="6cfca-106">Syntax</span></span>

```xml
<Name>NameOfControl</Name>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="6cfca-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="6cfca-107">Attributes and Elements</span></span>

<span data-ttu-id="6cfca-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `Name`-elementet.</span><span class="sxs-lookup"><span data-stu-id="6cfca-108">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6cfca-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="6cfca-109">Attributes</span></span>

<span data-ttu-id="6cfca-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="6cfca-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6cfca-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="6cfca-111">Child Elements</span></span>

<span data-ttu-id="6cfca-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="6cfca-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6cfca-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="6cfca-113">Parent Elements</span></span>

|<span data-ttu-id="6cfca-114">Element</span><span class="sxs-lookup"><span data-stu-id="6cfca-114">Element</span></span>|<span data-ttu-id="6cfca-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="6cfca-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6cfca-116">Kontroll element för konfigurations kontroll (format)</span><span class="sxs-lookup"><span data-stu-id="6cfca-116">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)|<span data-ttu-id="6cfca-117">Definierar en gemensam kontroll som kan användas av alla vyer i format filen och det namn som används för att referera till kontrollen.</span><span class="sxs-lookup"><span data-stu-id="6cfca-117">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="6cfca-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="6cfca-118">Text Value</span></span>

<span data-ttu-id="6cfca-119">Ange det namn som ska användas för att referera till den här kontrollen.</span><span class="sxs-lookup"><span data-stu-id="6cfca-119">Specify the name that is used to reference this control.</span></span>

## <a name="remarks"></a><span data-ttu-id="6cfca-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="6cfca-120">Remarks</span></span>

<span data-ttu-id="6cfca-121">Namnet som anges här kan användas i följande element för att referera till den här kontrollen.</span><span class="sxs-lookup"><span data-stu-id="6cfca-121">The name specified here can be used in the following elements to reference this control.</span></span>

- <span data-ttu-id="6cfca-122">När du skapar en tabell, lista, bred eller anpassad flikkontroll, kan kontrollen anges med följande element: [groupby-element för vy (format)](./groupby-element-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="6cfca-122">When creating a table, list, wide or custom control view, the control can be specified by the following element: [GroupBy Element for View (Format)](./groupby-element-for-view-format.md)</span></span>

- <span data-ttu-id="6cfca-123">När du skapar en annan gemensam kontroll, kan den här kontrollen anges av följande element: [ExpressionBinding-element för CustomItem för kontroller för konfiguration (format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)</span><span class="sxs-lookup"><span data-stu-id="6cfca-123">When creating another common control, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for Configuration (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)</span></span>

- <span data-ttu-id="6cfca-124">När du skapar en kontroll som kan användas av en vy, kan den här kontrollen anges med följande element: [ExpressionBinding-element för CustomItem för kontroller för vy (format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="6cfca-124">When creating a control that can be used by a view, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="6cfca-125">Se även</span><span class="sxs-lookup"><span data-stu-id="6cfca-125">See Also</span></span>

[<span data-ttu-id="6cfca-126">Kontroll element för konfigurations kontroll (format)</span><span class="sxs-lookup"><span data-stu-id="6cfca-126">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)

[<span data-ttu-id="6cfca-127">ExpressionBinding-element för CustomItem för kontroller för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="6cfca-127">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="6cfca-128">ExpressionBinding-element för CustomItem för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="6cfca-128">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="6cfca-129">GroupBy-element för vy (format)</span><span class="sxs-lookup"><span data-stu-id="6cfca-129">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="6cfca-130">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="6cfca-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
