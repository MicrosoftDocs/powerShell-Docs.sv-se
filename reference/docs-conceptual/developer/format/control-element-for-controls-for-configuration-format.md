---
ms.date: 09/13/2016
ms.topic: reference
title: Control-element för Controls för Configuration (format)
description: Control-element för Controls för Configuration (format)
ms.openlocfilehash: 43424de025cb89d81533e973abd7c39c09533747
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655660"
---
# <a name="control-element-for-controls-for-configuration-format"></a><span data-ttu-id="577d7-103">Control-element för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="577d7-103">Control Element for Controls for Configuration (Format)</span></span>

<span data-ttu-id="577d7-104">Definierar en gemensam kontroll som kan användas av alla vyer i format filen och det namn som används för att referera till kontrollen.</span><span class="sxs-lookup"><span data-stu-id="577d7-104">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>

<span data-ttu-id="577d7-105">Konfigurations element (format) styr element i konfigurations-(format) kontroll element för konfigurations inställningar (format)</span><span class="sxs-lookup"><span data-stu-id="577d7-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="577d7-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="577d7-106">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="577d7-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="577d7-107">Attributes and Elements</span></span>

<span data-ttu-id="577d7-108">I följande avsnitt beskrivs attributen, underordnade element och `Control` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="577d7-108">The following sections describe the attributes, child elements, and the parent element for the `Control` element.</span></span> <span data-ttu-id="577d7-109">Du måste ange ett av varje underordnat element.</span><span class="sxs-lookup"><span data-stu-id="577d7-109">You must specify only one of each child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="577d7-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="577d7-110">Attributes</span></span>

<span data-ttu-id="577d7-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="577d7-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="577d7-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="577d7-112">Child Elements</span></span>

|<span data-ttu-id="577d7-113">Element</span><span class="sxs-lookup"><span data-stu-id="577d7-113">Element</span></span>|<span data-ttu-id="577d7-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="577d7-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="577d7-115">CustomControl-element för Control för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="577d7-115">CustomControl Element for Control for Controls for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="577d7-116">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="577d7-116">Required element.</span></span><br /><br /> <span data-ttu-id="577d7-117">Definierar kontrollen.</span><span class="sxs-lookup"><span data-stu-id="577d7-117">Defines the control.</span></span>|
|[<span data-ttu-id="577d7-118">Namn element för kontroll av konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="577d7-118">Name Element for Control for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="577d7-119">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="577d7-119">Required element.</span></span><br /><br /> <span data-ttu-id="577d7-120">Anger det namn som ska användas för att referera till kontrollen.</span><span class="sxs-lookup"><span data-stu-id="577d7-120">Specifies the name used to reference the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="577d7-121">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="577d7-121">Parent Elements</span></span>

|<span data-ttu-id="577d7-122">Element</span><span class="sxs-lookup"><span data-stu-id="577d7-122">Element</span></span>|<span data-ttu-id="577d7-123">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="577d7-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="577d7-124">Kontrollerar konfigurations element (format)</span><span class="sxs-lookup"><span data-stu-id="577d7-124">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="577d7-125">Definierar de vanliga kontroller som kan användas av alla vyer i formaterings filen eller av andra kontroller.</span><span class="sxs-lookup"><span data-stu-id="577d7-125">Defines the common controls that can be used by all views of the formatting file or by other controls.</span></span>|

## <a name="remarks"></a><span data-ttu-id="577d7-126">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="577d7-126">Remarks</span></span>

<span data-ttu-id="577d7-127">Det namn som ges till den här kontrollen kan refereras till i följande element:</span><span class="sxs-lookup"><span data-stu-id="577d7-127">The name given to this control can be referenced in the following elements:</span></span>

- [<span data-ttu-id="577d7-128">ExpressionBinding-element för CustomItem (format)</span><span class="sxs-lookup"><span data-stu-id="577d7-128">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [<span data-ttu-id="577d7-129">GroupBy-element för vy (format)</span><span class="sxs-lookup"><span data-stu-id="577d7-129">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="577d7-130">Se även</span><span class="sxs-lookup"><span data-stu-id="577d7-130">See Also</span></span>

[<span data-ttu-id="577d7-131">Kontrollerar konfigurations element (format)</span><span class="sxs-lookup"><span data-stu-id="577d7-131">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="577d7-132">CustomControl-element för kontroll av konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="577d7-132">CustomControl element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="577d7-133">ExpressionBinding-element för CustomItem (format)</span><span class="sxs-lookup"><span data-stu-id="577d7-133">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="577d7-134">GroupBy-element för vy (format)</span><span class="sxs-lookup"><span data-stu-id="577d7-134">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="577d7-135">Name-element för Control för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="577d7-135">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="577d7-136">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="577d7-136">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
