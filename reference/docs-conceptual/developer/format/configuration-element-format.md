---
title: Konfigurations element (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d46df0cb-50b7-4b81-82ba-37186a7b7a7f
caps.latest.revision: 28
ms.openlocfilehash: 296c63d0c774a0bf56e90dbaa32f2c221d4c3dbd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354875"
---
# <a name="configuration-element-format"></a><span data-ttu-id="c7907-102">Configuration-element (format)</span><span class="sxs-lookup"><span data-stu-id="c7907-102">Configuration Element (Format)</span></span>

<span data-ttu-id="c7907-103">Representerar det översta elementet i en textfil.</span><span class="sxs-lookup"><span data-stu-id="c7907-103">Represents the top-level element of a formatting file.</span></span>

<span data-ttu-id="c7907-104">Konfigurations element</span><span class="sxs-lookup"><span data-stu-id="c7907-104">Configuration Element</span></span>

## <a name="syntax"></a><span data-ttu-id="c7907-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="c7907-105">Syntax</span></span>

```xml
<Configuration>
  <DefaultSettings>...</DefaultSettings>
  <SelectionSets>...</SelectionSets>
  <Controls>...</Controls>
  <ViewDefinitions>...</ViewDefinitions>
</Configuration>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="c7907-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="c7907-106">Attributes and Elements</span></span>

<span data-ttu-id="c7907-107">I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet för elementet `Configuration`.</span><span class="sxs-lookup"><span data-stu-id="c7907-107">The following sections describe the attributes, child elements, and the parent element of the `Configuration` element.</span></span> <span data-ttu-id="c7907-108">Det här elementet måste vara rot elementet för varje fil format och det här elementet måste innehålla minst ett underordnat element.</span><span class="sxs-lookup"><span data-stu-id="c7907-108">This element must be the root element for each formatting file, and this element must contain at least one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c7907-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="c7907-109">Attributes</span></span>

<span data-ttu-id="c7907-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="c7907-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c7907-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="c7907-111">Child Elements</span></span>

|<span data-ttu-id="c7907-112">Element</span><span class="sxs-lookup"><span data-stu-id="c7907-112">Element</span></span>|<span data-ttu-id="c7907-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c7907-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c7907-114">Styr element för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="c7907-114">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="c7907-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="c7907-115">Optional element.</span></span><br /><br /> <span data-ttu-id="c7907-116">Definierar de gemensamma kontroller som kan användas av alla vyer i formaterings filen.</span><span class="sxs-lookup"><span data-stu-id="c7907-116">Defines the common controls that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="c7907-117">DefaultSettings-element (format)</span><span class="sxs-lookup"><span data-stu-id="c7907-117">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="c7907-118">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="c7907-118">Optional element.</span></span><br /><br /> <span data-ttu-id="c7907-119">Definierar vanliga inställningar som gäller för alla vyer i formaterings filen.</span><span class="sxs-lookup"><span data-stu-id="c7907-119">Defines common settings that apply to all the views of the formatting file.</span></span>|
|[<span data-ttu-id="c7907-120">SelectionSets element format</span><span class="sxs-lookup"><span data-stu-id="c7907-120">SelectionSets Element Format</span></span>](./selectionsets-element-format.md)|<span data-ttu-id="c7907-121">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="c7907-121">Optional element.</span></span><br /><br /> <span data-ttu-id="c7907-122">Definierar de gemensamma uppsättningar av .NET-objekt som kan användas av alla vyer i format filen.</span><span class="sxs-lookup"><span data-stu-id="c7907-122">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="c7907-123">ViewDefinitions-element (format)</span><span class="sxs-lookup"><span data-stu-id="c7907-123">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="c7907-124">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="c7907-124">Optional element.</span></span><br /><br /> <span data-ttu-id="c7907-125">Definierar de vyer som används för att visa objekt.</span><span class="sxs-lookup"><span data-stu-id="c7907-125">Defines the views used to display objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c7907-126">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="c7907-126">Parent Elements</span></span>

<span data-ttu-id="c7907-127">Ingen.</span><span class="sxs-lookup"><span data-stu-id="c7907-127">None.</span></span>

## <a name="remarks"></a><span data-ttu-id="c7907-128">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="c7907-128">Remarks</span></span>

<span data-ttu-id="c7907-129">Formatering av filer definierar hur objekt visas.</span><span class="sxs-lookup"><span data-stu-id="c7907-129">Formatting files define how objects are displayed.</span></span> <span data-ttu-id="c7907-130">I de flesta fall innehåller det här rot elementet ett [ViewDefinitions](./viewdefinitions-element-format.md) -element som definierar tabell, lista och bred vy av format filen.</span><span class="sxs-lookup"><span data-stu-id="c7907-130">In most cases, this root element contains a [ViewDefinitions](./viewdefinitions-element-format.md) element that defines the table, list, and wide views of the formatting file.</span></span> <span data-ttu-id="c7907-131">Förutom visnings definitionerna kan format filen definiera vanliga uppsättningar, inställningar och kontroller som dessa vyer kan använda.</span><span class="sxs-lookup"><span data-stu-id="c7907-131">In addition to the view definitions, the formatting file can define common selection sets, settings, and controls that those views can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="c7907-132">Se även</span><span class="sxs-lookup"><span data-stu-id="c7907-132">See Also</span></span>

[<span data-ttu-id="c7907-133">Styr element för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="c7907-133">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="c7907-134">DefaultSettings-element (format)</span><span class="sxs-lookup"><span data-stu-id="c7907-134">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="c7907-135">SelectionSets-element (format)</span><span class="sxs-lookup"><span data-stu-id="c7907-135">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="c7907-136">ViewDefinitions-element (format)</span><span class="sxs-lookup"><span data-stu-id="c7907-136">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="c7907-137">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="c7907-137">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
