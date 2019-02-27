---
title: Kontrollera Element för kontroller för Configuration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bddf7ffa-04d3-4354-90b9-5e714e096260
caps.latest.revision: 13
ms.openlocfilehash: 26fe417c9ca60dda22bdc23d9d339d40135a0c9b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848834"
---
# <a name="control-element-for-controls-for-configuration-format"></a><span data-ttu-id="b5932-102">Control-element för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="b5932-102">Control Element for Controls for Configuration (Format)</span></span>

<span data-ttu-id="b5932-103">Definierar en gemensam kontroll som kan användas av alla vyer av filen formatering och det namn som används för att referera till kontrollen.</span><span class="sxs-lookup"><span data-stu-id="b5932-103">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>

<span data-ttu-id="b5932-104">Konfigurationselementet Element (Format) kontroller av (Format) kontroll konfigurationselement för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="b5932-104">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b5932-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="b5932-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b5932-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="b5932-106">Attributes and Elements</span></span>

<span data-ttu-id="b5932-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för den `Control` element.</span><span class="sxs-lookup"><span data-stu-id="b5932-107">The following sections describe the attributes, child elements, and the parent element for the `Control` element.</span></span> <span data-ttu-id="b5932-108">Du måste ange endast en av varje underordnat element.</span><span class="sxs-lookup"><span data-stu-id="b5932-108">You must specify only one of each child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b5932-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="b5932-109">Attributes</span></span>

<span data-ttu-id="b5932-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="b5932-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b5932-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="b5932-111">Child Elements</span></span>

|<span data-ttu-id="b5932-112">Element</span><span class="sxs-lookup"><span data-stu-id="b5932-112">Element</span></span>|<span data-ttu-id="b5932-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b5932-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b5932-114">Anpassad kontroll Element för kontroll för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="b5932-114">CustomControl Element for Control for Controls for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="b5932-115">Element som krävs.</span><span class="sxs-lookup"><span data-stu-id="b5932-115">Required element.</span></span><br /><br /> <span data-ttu-id="b5932-116">Definierar kontrollen.</span><span class="sxs-lookup"><span data-stu-id="b5932-116">Defines the control.</span></span>|
|[<span data-ttu-id="b5932-117">Namnelement för kontroll för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="b5932-117">Name Element for Control for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="b5932-118">Element som krävs.</span><span class="sxs-lookup"><span data-stu-id="b5932-118">Required element.</span></span><br /><br /> <span data-ttu-id="b5932-119">Anger namnet som refererar till kontrollen.</span><span class="sxs-lookup"><span data-stu-id="b5932-119">Specifies the name used to reference the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b5932-120">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="b5932-120">Parent Elements</span></span>

|<span data-ttu-id="b5932-121">Element</span><span class="sxs-lookup"><span data-stu-id="b5932-121">Element</span></span>|<span data-ttu-id="b5932-122">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b5932-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b5932-123">Kontroller Element av konfigurationen (Format)</span><span class="sxs-lookup"><span data-stu-id="b5932-123">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="b5932-124">Definierar de vanliga kontroller som kan användas av alla vyer i filen formatering eller av andra kontroller.</span><span class="sxs-lookup"><span data-stu-id="b5932-124">Defines the common controls that can be used by all views of the formatting file or by other controls.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b5932-125">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="b5932-125">Remarks</span></span>

<span data-ttu-id="b5932-126">Namnet på den här kontrollen kan refereras i följande element:</span><span class="sxs-lookup"><span data-stu-id="b5932-126">The name given to this control can be referenced in the following elements:</span></span>

- [<span data-ttu-id="b5932-127">ExpressionBinding Element för CustomItem (Format)</span><span class="sxs-lookup"><span data-stu-id="b5932-127">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [<span data-ttu-id="b5932-128">GroupBy-Element för View(Format)</span><span class="sxs-lookup"><span data-stu-id="b5932-128">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="b5932-129">Se även</span><span class="sxs-lookup"><span data-stu-id="b5932-129">See Also</span></span>

[<span data-ttu-id="b5932-130">Kontroller Element av konfigurationen (Format)</span><span class="sxs-lookup"><span data-stu-id="b5932-130">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="b5932-131">Anpassad kontroll element för kontroll för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="b5932-131">CustomControl element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="b5932-132">ExpressionBinding Element för CustomItem (Format)</span><span class="sxs-lookup"><span data-stu-id="b5932-132">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="b5932-133">GroupBy-Element för View(Format)</span><span class="sxs-lookup"><span data-stu-id="b5932-133">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="b5932-134">Namnelement för kontroll för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="b5932-134">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="b5932-135">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="b5932-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
