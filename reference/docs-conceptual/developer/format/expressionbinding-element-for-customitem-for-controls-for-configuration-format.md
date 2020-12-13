---
ms.date: 09/13/2016
ms.topic: reference
title: ExpressionBinding-element för CustomItem för Controls för Configuration (format)
description: ExpressionBinding-element för CustomItem för Controls för Configuration (format)
ms.openlocfilehash: 1abcf2173e18d45839161b4c7e59f1ad238f81a1
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655333"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-configuration-format"></a><span data-ttu-id="8cb6c-103">ExpressionBinding-element för CustomItem för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="8cb6c-103">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>

<span data-ttu-id="8cb6c-104">Definierar de data som visas av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="8cb6c-104">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="8cb6c-105">Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.</span><span class="sxs-lookup"><span data-stu-id="8cb6c-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="8cb6c-106">Konfigurations element (format) styr element i konfigurations-(format)-kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för Configuration (format) CustomEntry-element för CustomControl för Controls (format) CustomItem-element för CustomEntry för Controls för Configuration ExpressionBinding-element för CustomItem för Controls (format)</span><span class="sxs-lookup"><span data-stu-id="8cb6c-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8cb6c-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="8cb6c-107">Syntax</span></span>

```xml
<ExpressionBinding>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameofCommonCustomControl</CustomControlName>
  <EnumerateCollection/>
  <ItemSelectionCondition>...</ItemSelectionCondition>
  <PropertyName>Nameof.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate></ScriptBlock>
</ExpressionBinding>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8cb6c-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="8cb6c-108">Attributes and Elements</span></span>

<span data-ttu-id="8cb6c-109">I följande avsnitt beskrivs attribut, underordnade element och `ExpressionBinding` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="8cb6c-109">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8cb6c-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="8cb6c-110">Attributes</span></span>

<span data-ttu-id="8cb6c-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="8cb6c-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8cb6c-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="8cb6c-112">Child Elements</span></span>

|<span data-ttu-id="8cb6c-113">Element</span><span class="sxs-lookup"><span data-stu-id="8cb6c-113">Element</span></span>|<span data-ttu-id="8cb6c-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8cb6c-114">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="8cb6c-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="8cb6c-115">Optional element.</span></span><br /><br /> <span data-ttu-id="8cb6c-116">Definierar en kontroll som används av den här kontrollen.</span><span class="sxs-lookup"><span data-stu-id="8cb6c-116">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="8cb6c-117">CustomControlName-element för ExpressionBinding för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="8cb6c-117">CustomControlName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="8cb6c-118">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="8cb6c-118">Optional element.</span></span><br /><br /> <span data-ttu-id="8cb6c-119">Anger namnet på en gemensam kontroll eller en visnings kontroll.</span><span class="sxs-lookup"><span data-stu-id="8cb6c-119">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="8cb6c-120">EnumerateCollection-element för ExpressionBinding för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="8cb6c-120">EnumerateCollection Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="8cb6c-121">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="8cb6c-121">Optional element.</span></span><br /><br /> <span data-ttu-id="8cb6c-122">Anger att elementen i samlingar visas av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="8cb6c-122">Specified that the elements of collections are displayed by the control.</span></span>|
|[<span data-ttu-id="8cb6c-123">ItemSelectionCondition-element för ExpressionBinding för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="8cb6c-123">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="8cb6c-124">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="8cb6c-124">Optional element.</span></span><br /><br /> <span data-ttu-id="8cb6c-125">Definierar det villkor som måste finnas för att den här gemensamma kontrollen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="8cb6c-125">Defines the condition that must exist for this common control to be used.</span></span>|
|[<span data-ttu-id="8cb6c-126">PropertyName-element för ExpressionBinding för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="8cb6c-126">PropertyName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="8cb6c-127">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="8cb6c-127">Optional element.</span></span><br /><br /> <span data-ttu-id="8cb6c-128">Anger .NET-egenskapen vars värde visas av den gemensamma kontrollen.</span><span class="sxs-lookup"><span data-stu-id="8cb6c-128">Specifies the .NET property whose value is displayed by the common control.</span></span>|
|[<span data-ttu-id="8cb6c-129">ScriptBlock-element för ExpressionBinding för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="8cb6c-129">ScriptBlock Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="8cb6c-130">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="8cb6c-130">Optional element.</span></span><br /><br /> <span data-ttu-id="8cb6c-131">Anger det skript vars värde visas av den gemensamma kontrollen.</span><span class="sxs-lookup"><span data-stu-id="8cb6c-131">Specifies the script whose value is displayed by the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="8cb6c-132">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="8cb6c-132">Parent Elements</span></span>

|<span data-ttu-id="8cb6c-133">Element</span><span class="sxs-lookup"><span data-stu-id="8cb6c-133">Element</span></span>|<span data-ttu-id="8cb6c-134">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8cb6c-134">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8cb6c-135">CustomItem-element för CustomEntry för kontroller för konfiguration</span><span class="sxs-lookup"><span data-stu-id="8cb6c-135">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="8cb6c-136">Definierar vilka data som visas i vyn anpassad kontroll och hur den visas.</span><span class="sxs-lookup"><span data-stu-id="8cb6c-136">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8cb6c-137">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="8cb6c-137">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="8cb6c-138">Se även</span><span class="sxs-lookup"><span data-stu-id="8cb6c-138">See Also</span></span>

[<span data-ttu-id="8cb6c-139">CustomItem-element för CustomEntry för kontroller för konfiguration</span><span class="sxs-lookup"><span data-stu-id="8cb6c-139">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="8cb6c-140">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="8cb6c-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
