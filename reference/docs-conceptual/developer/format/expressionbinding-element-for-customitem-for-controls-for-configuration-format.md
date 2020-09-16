---
title: ExpressionBinding-element för CustomItem för kontroll av konfiguration (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 1ad83fa9d915822eaefb490658f8a219defdddf2
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773920"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-configuration-format"></a><span data-ttu-id="e910d-102">ExpressionBinding-element för CustomItem för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="e910d-102">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>

<span data-ttu-id="e910d-103">Definierar de data som visas av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="e910d-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="e910d-104">Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.</span><span class="sxs-lookup"><span data-stu-id="e910d-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="e910d-105">Konfigurations element (format) styr element i konfigurations-(format)-kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för Configuration (format) CustomEntry-element för CustomControl för Controls (format) CustomItem-element för CustomEntry för Controls för Configuration ExpressionBinding-element för CustomItem för Controls (format)</span><span class="sxs-lookup"><span data-stu-id="e910d-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e910d-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="e910d-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="e910d-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="e910d-107">Attributes and Elements</span></span>

<span data-ttu-id="e910d-108">I följande avsnitt beskrivs attribut, underordnade element och `ExpressionBinding` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="e910d-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e910d-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="e910d-109">Attributes</span></span>

<span data-ttu-id="e910d-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="e910d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e910d-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="e910d-111">Child Elements</span></span>

|<span data-ttu-id="e910d-112">Element</span><span class="sxs-lookup"><span data-stu-id="e910d-112">Element</span></span>|<span data-ttu-id="e910d-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e910d-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="e910d-114">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="e910d-114">Optional element.</span></span><br /><br /> <span data-ttu-id="e910d-115">Definierar en kontroll som används av den här kontrollen.</span><span class="sxs-lookup"><span data-stu-id="e910d-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="e910d-116">CustomControlName-element för ExpressionBinding för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="e910d-116">CustomControlName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="e910d-117">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="e910d-117">Optional element.</span></span><br /><br /> <span data-ttu-id="e910d-118">Anger namnet på en gemensam kontroll eller en visnings kontroll.</span><span class="sxs-lookup"><span data-stu-id="e910d-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="e910d-119">EnumerateCollection-element för ExpressionBinding för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="e910d-119">EnumerateCollection Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="e910d-120">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="e910d-120">Optional element.</span></span><br /><br /> <span data-ttu-id="e910d-121">Anger att elementen i samlingar visas av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="e910d-121">Specified that the elements of collections are displayed by the control.</span></span>|
|[<span data-ttu-id="e910d-122">ItemSelectionCondition-element för ExpressionBinding för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="e910d-122">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="e910d-123">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="e910d-123">Optional element.</span></span><br /><br /> <span data-ttu-id="e910d-124">Definierar det villkor som måste finnas för att den här gemensamma kontrollen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="e910d-124">Defines the condition that must exist for this common control to be used.</span></span>|
|[<span data-ttu-id="e910d-125">PropertyName-element för ExpressionBinding för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="e910d-125">PropertyName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="e910d-126">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="e910d-126">Optional element.</span></span><br /><br /> <span data-ttu-id="e910d-127">Anger .NET-egenskapen vars värde visas av den gemensamma kontrollen.</span><span class="sxs-lookup"><span data-stu-id="e910d-127">Specifies the .NET property whose value is displayed by the common control.</span></span>|
|[<span data-ttu-id="e910d-128">ScriptBlock-element för ExpressionBinding för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="e910d-128">ScriptBlock Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="e910d-129">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="e910d-129">Optional element.</span></span><br /><br /> <span data-ttu-id="e910d-130">Anger det skript vars värde visas av den gemensamma kontrollen.</span><span class="sxs-lookup"><span data-stu-id="e910d-130">Specifies the script whose value is displayed by the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e910d-131">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="e910d-131">Parent Elements</span></span>

|<span data-ttu-id="e910d-132">Element</span><span class="sxs-lookup"><span data-stu-id="e910d-132">Element</span></span>|<span data-ttu-id="e910d-133">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e910d-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e910d-134">CustomItem-element för CustomEntry för kontroller för konfiguration</span><span class="sxs-lookup"><span data-stu-id="e910d-134">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="e910d-135">Definierar vilka data som visas i vyn anpassad kontroll och hur den visas.</span><span class="sxs-lookup"><span data-stu-id="e910d-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e910d-136">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="e910d-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="e910d-137">Se även</span><span class="sxs-lookup"><span data-stu-id="e910d-137">See Also</span></span>

[<span data-ttu-id="e910d-138">CustomItem-element för CustomEntry för kontroller för konfiguration</span><span class="sxs-lookup"><span data-stu-id="e910d-138">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="e910d-139">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="e910d-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
