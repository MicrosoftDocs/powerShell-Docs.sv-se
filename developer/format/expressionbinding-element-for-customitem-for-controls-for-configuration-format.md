---
title: ExpressionBinding Element för CustomItem för kontroller för konfiguration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6649d07-4762-4602-9b4b-d9e2e9e63312
caps.latest.revision: 13
ms.openlocfilehash: 531ff447f8407a737131a38351d7e4c6e7da90fb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846209"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-configuration-format"></a><span data-ttu-id="5da54-102">ExpressionBinding-element för CustomItem för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="5da54-102">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>

<span data-ttu-id="5da54-103">Definierar de data som visas i kontrollen.</span><span class="sxs-lookup"><span data-stu-id="5da54-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="5da54-104">Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.</span><span class="sxs-lookup"><span data-stu-id="5da54-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="5da54-105">Konfigurationselementet Element (Format) kontroller av (Format) kontroll konfigurationselement för kontroller för (Format) anpassad kontroll konfigurationselement för kontroll för (Format) CustomEntries konfigurationselement för anpassad kontroll för konfiguration ( Format) CustomEntry Element för anpassad kontroll för kontroller för (Format) CustomItem konfigurationselement för CustomEntry för kontroller för ExpressionBinding konfigurationselement för CustomItem för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="5da54-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5da54-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="5da54-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="5da54-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="5da54-107">Attributes and Elements</span></span>

<span data-ttu-id="5da54-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `ExpressionBinding` element.</span><span class="sxs-lookup"><span data-stu-id="5da54-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5da54-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="5da54-109">Attributes</span></span>

<span data-ttu-id="5da54-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="5da54-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5da54-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="5da54-111">Child Elements</span></span>

|<span data-ttu-id="5da54-112">Element</span><span class="sxs-lookup"><span data-stu-id="5da54-112">Element</span></span>|<span data-ttu-id="5da54-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5da54-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="5da54-114">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="5da54-114">Optional element.</span></span><br /><br /> <span data-ttu-id="5da54-115">Definierar en kontroll som används av den här kontrollen.</span><span class="sxs-lookup"><span data-stu-id="5da54-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="5da54-116">CustomControlName Element för ExpressionBinding för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="5da54-116">CustomControlName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="5da54-117">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="5da54-117">Optional element.</span></span><br /><br /> <span data-ttu-id="5da54-118">Anger namnet på en gemensam kontroll eller en kontroll.</span><span class="sxs-lookup"><span data-stu-id="5da54-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="5da54-119">EnumerateCollection Element för ExpressionBinding för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="5da54-119">EnumerateCollection Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="5da54-120">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="5da54-120">Optional element.</span></span><br /><br /> <span data-ttu-id="5da54-121">Ange att elementen i samlingar visas i kontrollen.</span><span class="sxs-lookup"><span data-stu-id="5da54-121">Specified that the elements of collections are displayed by the control.</span></span>|
|[<span data-ttu-id="5da54-122">ItemSelectionCondition Element för ExpressionBinding för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="5da54-122">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="5da54-123">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="5da54-123">Optional element.</span></span><br /><br /> <span data-ttu-id="5da54-124">Definierar de villkor som måste finnas för den här vanliga kontrollen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="5da54-124">Defines the condition that must exist for this common control to be used.</span></span>|
|[<span data-ttu-id="5da54-125">PropertyName-Element för ExpressionBinding för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="5da54-125">PropertyName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="5da54-126">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="5da54-126">Optional element.</span></span><br /><br /> <span data-ttu-id="5da54-127">Anger egenskapen .NET vars värde visas som vanliga kontrollen.</span><span class="sxs-lookup"><span data-stu-id="5da54-127">Specifies the .NET property whose value is displayed by the common control.</span></span>|
|[<span data-ttu-id="5da54-128">ScriptBlock Element för ExpressionBinding för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="5da54-128">ScriptBlock Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="5da54-129">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="5da54-129">Optional element.</span></span><br /><br /> <span data-ttu-id="5da54-130">Anger skriptet vars värde visas som vanliga kontrollen.</span><span class="sxs-lookup"><span data-stu-id="5da54-130">Specifies the script whose value is displayed by the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5da54-131">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="5da54-131">Parent Elements</span></span>

|<span data-ttu-id="5da54-132">Element</span><span class="sxs-lookup"><span data-stu-id="5da54-132">Element</span></span>|<span data-ttu-id="5da54-133">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5da54-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5da54-134">CustomItem Element för CustomEntry för kontroller för konfiguration</span><span class="sxs-lookup"><span data-stu-id="5da54-134">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="5da54-135">Definierar vilka data som visas i vyn anpassad kontroll och hur de visas.</span><span class="sxs-lookup"><span data-stu-id="5da54-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5da54-136">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="5da54-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="5da54-137">Se även</span><span class="sxs-lookup"><span data-stu-id="5da54-137">See Also</span></span>

[<span data-ttu-id="5da54-138">CustomItem Element för CustomEntry för kontroller för konfiguration</span><span class="sxs-lookup"><span data-stu-id="5da54-138">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="5da54-139">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="5da54-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
