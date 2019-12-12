---
title: Kontroll element för konfigurations kontroll (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bddf7ffa-04d3-4354-90b9-5e714e096260
caps.latest.revision: 13
ms.openlocfilehash: 26fe417c9ca60dda22bdc23d9d339d40135a0c9b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359085"
---
# <a name="control-element-for-controls-for-configuration-format"></a><span data-ttu-id="208ca-102">Control-element för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="208ca-102">Control Element for Controls for Configuration (Format)</span></span>

<span data-ttu-id="208ca-103">Definierar en gemensam kontroll som kan användas av alla vyer i format filen och det namn som används för att referera till kontrollen.</span><span class="sxs-lookup"><span data-stu-id="208ca-103">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>

<span data-ttu-id="208ca-104">Konfigurations element (format) styr element i konfigurations-(format) kontroll element för konfigurations inställningar (format)</span><span class="sxs-lookup"><span data-stu-id="208ca-104">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="208ca-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="208ca-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="208ca-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="208ca-106">Attributes and Elements</span></span>

<span data-ttu-id="208ca-107">I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet för `Control`-elementet.</span><span class="sxs-lookup"><span data-stu-id="208ca-107">The following sections describe the attributes, child elements, and the parent element for the `Control` element.</span></span> <span data-ttu-id="208ca-108">Du måste ange ett av varje underordnat element.</span><span class="sxs-lookup"><span data-stu-id="208ca-108">You must specify only one of each child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="208ca-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="208ca-109">Attributes</span></span>

<span data-ttu-id="208ca-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="208ca-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="208ca-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="208ca-111">Child Elements</span></span>

|<span data-ttu-id="208ca-112">Element</span><span class="sxs-lookup"><span data-stu-id="208ca-112">Element</span></span>|<span data-ttu-id="208ca-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="208ca-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="208ca-114">CustomControl-element för kontroll av konfigurations inställningar (format)</span><span class="sxs-lookup"><span data-stu-id="208ca-114">CustomControl Element for Control for Controls for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="208ca-115">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="208ca-115">Required element.</span></span><br /><br /> <span data-ttu-id="208ca-116">Definierar kontrollen.</span><span class="sxs-lookup"><span data-stu-id="208ca-116">Defines the control.</span></span>|
|[<span data-ttu-id="208ca-117">Namn element för kontroll av konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="208ca-117">Name Element for Control for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="208ca-118">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="208ca-118">Required element.</span></span><br /><br /> <span data-ttu-id="208ca-119">Anger det namn som ska användas för att referera till kontrollen.</span><span class="sxs-lookup"><span data-stu-id="208ca-119">Specifies the name used to reference the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="208ca-120">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="208ca-120">Parent Elements</span></span>

|<span data-ttu-id="208ca-121">Element</span><span class="sxs-lookup"><span data-stu-id="208ca-121">Element</span></span>|<span data-ttu-id="208ca-122">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="208ca-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="208ca-123">Kontrollerar konfigurations element (format)</span><span class="sxs-lookup"><span data-stu-id="208ca-123">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="208ca-124">Definierar de vanliga kontroller som kan användas av alla vyer i formaterings filen eller av andra kontroller.</span><span class="sxs-lookup"><span data-stu-id="208ca-124">Defines the common controls that can be used by all views of the formatting file or by other controls.</span></span>|

## <a name="remarks"></a><span data-ttu-id="208ca-125">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="208ca-125">Remarks</span></span>

<span data-ttu-id="208ca-126">Det namn som ges till den här kontrollen kan refereras till i följande element:</span><span class="sxs-lookup"><span data-stu-id="208ca-126">The name given to this control can be referenced in the following elements:</span></span>

- [<span data-ttu-id="208ca-127">ExpressionBinding-element för CustomItem (format)</span><span class="sxs-lookup"><span data-stu-id="208ca-127">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [<span data-ttu-id="208ca-128">GroupBy-element för vy (format)</span><span class="sxs-lookup"><span data-stu-id="208ca-128">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="208ca-129">Se även</span><span class="sxs-lookup"><span data-stu-id="208ca-129">See Also</span></span>

[<span data-ttu-id="208ca-130">Kontrollerar konfigurations element (format)</span><span class="sxs-lookup"><span data-stu-id="208ca-130">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="208ca-131">CustomControl-element för kontroll av konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="208ca-131">CustomControl element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="208ca-132">ExpressionBinding-element för CustomItem (format)</span><span class="sxs-lookup"><span data-stu-id="208ca-132">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="208ca-133">GroupBy-element för vy (format)</span><span class="sxs-lookup"><span data-stu-id="208ca-133">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="208ca-134">Namn element för kontroll för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="208ca-134">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="208ca-135">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="208ca-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
