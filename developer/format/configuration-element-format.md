---
title: Konfigurationselementet (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d46df0cb-50b7-4b81-82ba-37186a7b7a7f
caps.latest.revision: 28
ms.openlocfilehash: 296c63d0c774a0bf56e90dbaa32f2c221d4c3dbd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847042"
---
# <a name="configuration-element-format"></a><span data-ttu-id="1893c-102">Configuration-element (format)</span><span class="sxs-lookup"><span data-stu-id="1893c-102">Configuration Element (Format)</span></span>

<span data-ttu-id="1893c-103">Representerar det översta elementet i en formatering fil.</span><span class="sxs-lookup"><span data-stu-id="1893c-103">Represents the top-level element of a formatting file.</span></span>

<span data-ttu-id="1893c-104">Konfigurationselement</span><span class="sxs-lookup"><span data-stu-id="1893c-104">Configuration Element</span></span>

## <a name="syntax"></a><span data-ttu-id="1893c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="1893c-105">Syntax</span></span>

```xml
<Configuration>
  <DefaultSettings>...</DefaultSettings>
  <SelectionSets>...</SelectionSets>
  <Controls>...</Controls>
  <ViewDefinitions>...</ViewDefinitions>
</Configuration>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="1893c-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="1893c-106">Attributes and Elements</span></span>

<span data-ttu-id="1893c-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `Configuration` element.</span><span class="sxs-lookup"><span data-stu-id="1893c-107">The following sections describe the attributes, child elements, and the parent element of the `Configuration` element.</span></span> <span data-ttu-id="1893c-108">Det här elementet måste vara rotelementet för varje formatering fil och det här elementet måste innehålla minst ett underordnat element.</span><span class="sxs-lookup"><span data-stu-id="1893c-108">This element must be the root element for each formatting file, and this element must contain at least one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1893c-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="1893c-109">Attributes</span></span>

<span data-ttu-id="1893c-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="1893c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1893c-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="1893c-111">Child Elements</span></span>

|<span data-ttu-id="1893c-112">Element</span><span class="sxs-lookup"><span data-stu-id="1893c-112">Element</span></span>|<span data-ttu-id="1893c-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="1893c-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1893c-114">Kontroller Element för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="1893c-114">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="1893c-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="1893c-115">Optional element.</span></span><br /><br /> <span data-ttu-id="1893c-116">Definierar de vanliga kontroller som kan användas av alla vyer i filen formatering.</span><span class="sxs-lookup"><span data-stu-id="1893c-116">Defines the common controls that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="1893c-117">DefaultSettings Element (Format)</span><span class="sxs-lookup"><span data-stu-id="1893c-117">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="1893c-118">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="1893c-118">Optional element.</span></span><br /><br /> <span data-ttu-id="1893c-119">Definierar gemensamma inställningar som gäller för alla vyer i filen formatering.</span><span class="sxs-lookup"><span data-stu-id="1893c-119">Defines common settings that apply to all the views of the formatting file.</span></span>|
|[<span data-ttu-id="1893c-120">SelectionSets Element Format</span><span class="sxs-lookup"><span data-stu-id="1893c-120">SelectionSets Element Format</span></span>](./selectionsets-element-format.md)|<span data-ttu-id="1893c-121">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="1893c-121">Optional element.</span></span><br /><br /> <span data-ttu-id="1893c-122">Definierar gemensamma uppsättningar med .NET-objekt som kan användas av alla vyer i filen formatering.</span><span class="sxs-lookup"><span data-stu-id="1893c-122">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="1893c-123">ViewDefinitions Element (Format)</span><span class="sxs-lookup"><span data-stu-id="1893c-123">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="1893c-124">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="1893c-124">Optional element.</span></span><br /><br /> <span data-ttu-id="1893c-125">Definierar de vyer som används för att visa objekt.</span><span class="sxs-lookup"><span data-stu-id="1893c-125">Defines the views used to display objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="1893c-126">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="1893c-126">Parent Elements</span></span>

<span data-ttu-id="1893c-127">Ingen.</span><span class="sxs-lookup"><span data-stu-id="1893c-127">None.</span></span>

## <a name="remarks"></a><span data-ttu-id="1893c-128">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="1893c-128">Remarks</span></span>

<span data-ttu-id="1893c-129">Formateras definierar hur objekt visas.</span><span class="sxs-lookup"><span data-stu-id="1893c-129">Formatting files define how objects are displayed.</span></span> <span data-ttu-id="1893c-130">I de flesta fall är detta rotelement innehåller en [ViewDefinitions](./viewdefinitions-element-format.md) -element som definierar den tabell, lista och många vyer i filen formatering.</span><span class="sxs-lookup"><span data-stu-id="1893c-130">In most cases, this root element contains a [ViewDefinitions](./viewdefinitions-element-format.md) element that defines the table, list, and wide views of the formatting file.</span></span> <span data-ttu-id="1893c-131">Förutom att visa-definitioner kan filen formatering definiera vanliga val av uppsättningar, inställningar och kontroller som kan använda för dessa vyer.</span><span class="sxs-lookup"><span data-stu-id="1893c-131">In addition to the view definitions, the formatting file can define common selection sets, settings, and controls that those views can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="1893c-132">Se även</span><span class="sxs-lookup"><span data-stu-id="1893c-132">See Also</span></span>

[<span data-ttu-id="1893c-133">Kontroller Element för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="1893c-133">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="1893c-134">DefaultSettings Element (Format)</span><span class="sxs-lookup"><span data-stu-id="1893c-134">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="1893c-135">SelectionSets Element (Format)</span><span class="sxs-lookup"><span data-stu-id="1893c-135">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="1893c-136">ViewDefinitions Element (Format)</span><span class="sxs-lookup"><span data-stu-id="1893c-136">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="1893c-137">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="1893c-137">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
