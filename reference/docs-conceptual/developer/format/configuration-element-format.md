---
ms.date: 09/13/2016
ms.topic: reference
title: Configuration-element (format)
description: Configuration-element (format)
ms.openlocfilehash: 0524736d40dd7a7acb0b6fb61d1438b75672c240
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92655697"
---
# <a name="configuration-element-format"></a><span data-ttu-id="d4e00-103">Configuration-element (format)</span><span class="sxs-lookup"><span data-stu-id="d4e00-103">Configuration Element (Format)</span></span>

<span data-ttu-id="d4e00-104">Representerar det översta elementet i en textfil.</span><span class="sxs-lookup"><span data-stu-id="d4e00-104">Represents the top-level element of a formatting file.</span></span>

<span data-ttu-id="d4e00-105">Konfigurations element</span><span class="sxs-lookup"><span data-stu-id="d4e00-105">Configuration Element</span></span>

## <a name="syntax"></a><span data-ttu-id="d4e00-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="d4e00-106">Syntax</span></span>

```xml
<Configuration>
  <DefaultSettings>...</DefaultSettings>
  <SelectionSets>...</SelectionSets>
  <Controls>...</Controls>
  <ViewDefinitions>...</ViewDefinitions>
</Configuration>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="d4e00-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="d4e00-107">Attributes and Elements</span></span>

<span data-ttu-id="d4e00-108">I följande avsnitt beskrivs attributen, underordnade element och `Configuration` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="d4e00-108">The following sections describe the attributes, child elements, and the parent element of the `Configuration` element.</span></span> <span data-ttu-id="d4e00-109">Det här elementet måste vara rot elementet för varje fil format och det här elementet måste innehålla minst ett underordnat element.</span><span class="sxs-lookup"><span data-stu-id="d4e00-109">This element must be the root element for each formatting file, and this element must contain at least one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d4e00-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="d4e00-110">Attributes</span></span>

<span data-ttu-id="d4e00-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="d4e00-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d4e00-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="d4e00-112">Child Elements</span></span>

|<span data-ttu-id="d4e00-113">Element</span><span class="sxs-lookup"><span data-stu-id="d4e00-113">Element</span></span>|<span data-ttu-id="d4e00-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d4e00-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d4e00-115">Controls-element för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="d4e00-115">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="d4e00-116">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="d4e00-116">Optional element.</span></span><br /><br /> <span data-ttu-id="d4e00-117">Definierar de gemensamma kontroller som kan användas av alla vyer i formaterings filen.</span><span class="sxs-lookup"><span data-stu-id="d4e00-117">Defines the common controls that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="d4e00-118">DefaultSettings-element (format)</span><span class="sxs-lookup"><span data-stu-id="d4e00-118">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="d4e00-119">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="d4e00-119">Optional element.</span></span><br /><br /> <span data-ttu-id="d4e00-120">Definierar vanliga inställningar som gäller för alla vyer i formaterings filen.</span><span class="sxs-lookup"><span data-stu-id="d4e00-120">Defines common settings that apply to all the views of the formatting file.</span></span>|
|[<span data-ttu-id="d4e00-121">SelectionSets element format</span><span class="sxs-lookup"><span data-stu-id="d4e00-121">SelectionSets Element Format</span></span>](./selectionsets-element-format.md)|<span data-ttu-id="d4e00-122">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="d4e00-122">Optional element.</span></span><br /><br /> <span data-ttu-id="d4e00-123">Definierar de gemensamma uppsättningar av .NET-objekt som kan användas av alla vyer i format filen.</span><span class="sxs-lookup"><span data-stu-id="d4e00-123">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="d4e00-124">ViewDefinitions-element (format)</span><span class="sxs-lookup"><span data-stu-id="d4e00-124">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="d4e00-125">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="d4e00-125">Optional element.</span></span><br /><br /> <span data-ttu-id="d4e00-126">Definierar de vyer som används för att visa objekt.</span><span class="sxs-lookup"><span data-stu-id="d4e00-126">Defines the views used to display objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d4e00-127">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="d4e00-127">Parent Elements</span></span>

<span data-ttu-id="d4e00-128">Inga.</span><span class="sxs-lookup"><span data-stu-id="d4e00-128">None.</span></span>

## <a name="remarks"></a><span data-ttu-id="d4e00-129">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="d4e00-129">Remarks</span></span>

<span data-ttu-id="d4e00-130">Formatering av filer definierar hur objekt visas.</span><span class="sxs-lookup"><span data-stu-id="d4e00-130">Formatting files define how objects are displayed.</span></span> <span data-ttu-id="d4e00-131">I de flesta fall innehåller det här rot elementet ett [ViewDefinitions](./viewdefinitions-element-format.md) -element som definierar tabell, lista och bred vy av format filen.</span><span class="sxs-lookup"><span data-stu-id="d4e00-131">In most cases, this root element contains a [ViewDefinitions](./viewdefinitions-element-format.md) element that defines the table, list, and wide views of the formatting file.</span></span> <span data-ttu-id="d4e00-132">Förutom visnings definitionerna kan format filen definiera vanliga uppsättningar, inställningar och kontroller som dessa vyer kan använda.</span><span class="sxs-lookup"><span data-stu-id="d4e00-132">In addition to the view definitions, the formatting file can define common selection sets, settings, and controls that those views can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="d4e00-133">Se även</span><span class="sxs-lookup"><span data-stu-id="d4e00-133">See Also</span></span>

[<span data-ttu-id="d4e00-134">Controls-element för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="d4e00-134">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="d4e00-135">DefaultSettings-element (format)</span><span class="sxs-lookup"><span data-stu-id="d4e00-135">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="d4e00-136">SelectionSets-element (format)</span><span class="sxs-lookup"><span data-stu-id="d4e00-136">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="d4e00-137">ViewDefinitions-element (format)</span><span class="sxs-lookup"><span data-stu-id="d4e00-137">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="d4e00-138">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="d4e00-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
