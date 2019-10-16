---
title: ExpressionBinding-element för CustomItem för kontroll av konfiguration (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6649d07-4762-4602-9b4b-d9e2e9e63312
caps.latest.revision: 13
ms.openlocfilehash: 531ff447f8407a737131a38351d7e4c6e7da90fb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354658"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-configuration-format"></a><span data-ttu-id="50d8e-102">ExpressionBinding-element för CustomItem för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="50d8e-102">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>

<span data-ttu-id="50d8e-103">Definierar de data som visas av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="50d8e-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="50d8e-104">Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.</span><span class="sxs-lookup"><span data-stu-id="50d8e-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="50d8e-105">Konfigurations element (format) styr element i konfigurations-(format) kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för konfiguration ( Format) CustomEntry-element för CustomControl for Controls for Configuration (format) CustomItem element for CustomEntry for Controls for Configuration ExpressionBinding element for CustomItem for Controls for Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="50d8e-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="50d8e-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="50d8e-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="50d8e-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="50d8e-107">Attributes and Elements</span></span>

<span data-ttu-id="50d8e-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för elementet `ExpressionBinding`.</span><span class="sxs-lookup"><span data-stu-id="50d8e-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="50d8e-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="50d8e-109">Attributes</span></span>

<span data-ttu-id="50d8e-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="50d8e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="50d8e-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="50d8e-111">Child Elements</span></span>

|<span data-ttu-id="50d8e-112">Element</span><span class="sxs-lookup"><span data-stu-id="50d8e-112">Element</span></span>|<span data-ttu-id="50d8e-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="50d8e-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="50d8e-114">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="50d8e-114">Optional element.</span></span><br /><br /> <span data-ttu-id="50d8e-115">Definierar en kontroll som används av den här kontrollen.</span><span class="sxs-lookup"><span data-stu-id="50d8e-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="50d8e-116">CustomControlName-element för ExpressionBinding för kontroller för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="50d8e-116">CustomControlName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="50d8e-117">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="50d8e-117">Optional element.</span></span><br /><br /> <span data-ttu-id="50d8e-118">Anger namnet på en gemensam kontroll eller en visnings kontroll.</span><span class="sxs-lookup"><span data-stu-id="50d8e-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="50d8e-119">EnumerateCollection-element för ExpressionBinding för kontroller för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="50d8e-119">EnumerateCollection Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="50d8e-120">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="50d8e-120">Optional element.</span></span><br /><br /> <span data-ttu-id="50d8e-121">Anger att elementen i samlingar visas av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="50d8e-121">Specified that the elements of collections are displayed by the control.</span></span>|
|[<span data-ttu-id="50d8e-122">ItemSelectionCondition-element för ExpressionBinding för kontroller för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="50d8e-122">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="50d8e-123">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="50d8e-123">Optional element.</span></span><br /><br /> <span data-ttu-id="50d8e-124">Definierar det villkor som måste finnas för att den här gemensamma kontrollen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="50d8e-124">Defines the condition that must exist for this common control to be used.</span></span>|
|[<span data-ttu-id="50d8e-125">PropertyName-element för ExpressionBinding för kontroll av konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="50d8e-125">PropertyName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="50d8e-126">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="50d8e-126">Optional element.</span></span><br /><br /> <span data-ttu-id="50d8e-127">Anger .NET-egenskapen vars värde visas av den gemensamma kontrollen.</span><span class="sxs-lookup"><span data-stu-id="50d8e-127">Specifies the .NET property whose value is displayed by the common control.</span></span>|
|[<span data-ttu-id="50d8e-128">Script block-element för ExpressionBinding för kontroller för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="50d8e-128">ScriptBlock Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="50d8e-129">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="50d8e-129">Optional element.</span></span><br /><br /> <span data-ttu-id="50d8e-130">Anger det skript vars värde visas av den gemensamma kontrollen.</span><span class="sxs-lookup"><span data-stu-id="50d8e-130">Specifies the script whose value is displayed by the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="50d8e-131">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="50d8e-131">Parent Elements</span></span>

|<span data-ttu-id="50d8e-132">Element</span><span class="sxs-lookup"><span data-stu-id="50d8e-132">Element</span></span>|<span data-ttu-id="50d8e-133">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="50d8e-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="50d8e-134">CustomItem-element för CustomEntry för kontroller för konfiguration</span><span class="sxs-lookup"><span data-stu-id="50d8e-134">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="50d8e-135">Definierar vilka data som visas i vyn anpassad kontroll och hur den visas.</span><span class="sxs-lookup"><span data-stu-id="50d8e-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="50d8e-136">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="50d8e-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="50d8e-137">Se även</span><span class="sxs-lookup"><span data-stu-id="50d8e-137">See Also</span></span>

[<span data-ttu-id="50d8e-138">CustomItem-element för CustomEntry för kontroller för konfiguration</span><span class="sxs-lookup"><span data-stu-id="50d8e-138">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="50d8e-139">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="50d8e-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
