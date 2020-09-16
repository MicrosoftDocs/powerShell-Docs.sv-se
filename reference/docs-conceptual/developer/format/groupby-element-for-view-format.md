---
title: GroupBy-element för vy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 2f9071a3ebbc7cc2ccb7721dd518e82723e9cc4e
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781434"
---
# <a name="groupby-element-for-view-format"></a><span data-ttu-id="e670b-102">GroupBy-element för View (format)</span><span class="sxs-lookup"><span data-stu-id="e670b-102">GroupBy Element for View (Format)</span></span>

<span data-ttu-id="e670b-103">Definierar hur en ny grupp av objekt visas.</span><span class="sxs-lookup"><span data-stu-id="e670b-103">Defines how a new group of objects is displayed.</span></span> <span data-ttu-id="e670b-104">Det här elementet används när du definierar en tabell, en lista, en bred eller en anpassad vy.</span><span class="sxs-lookup"><span data-stu-id="e670b-104">This element is used when defining a table, list, wide, or custom control view.</span></span>

<span data-ttu-id="e670b-105">Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för vy (format)</span><span class="sxs-lookup"><span data-stu-id="e670b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e670b-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="e670b-106">Syntax</span></span>

```xml
<GroupBy>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  <Label>TextToDisplay</Label>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameOfControl</CustomControlName>
</GroupBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e670b-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="e670b-107">Attributes and Elements</span></span>

<span data-ttu-id="e670b-108">I följande avsnitt beskrivs attribut, underordnade element och överordnade element.</span><span class="sxs-lookup"><span data-stu-id="e670b-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="e670b-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="e670b-109">Attributes</span></span>

<span data-ttu-id="e670b-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="e670b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e670b-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="e670b-111">Child Elements</span></span>

|<span data-ttu-id="e670b-112">Element</span><span class="sxs-lookup"><span data-stu-id="e670b-112">Element</span></span>|<span data-ttu-id="e670b-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e670b-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e670b-114">CustomControl-element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="e670b-114">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="e670b-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="e670b-115">Optional element.</span></span><br /><br /> <span data-ttu-id="e670b-116">Definierar den anpassade kontrollen som visar nya grupper.</span><span class="sxs-lookup"><span data-stu-id="e670b-116">Defines the custom control that display new groups.</span></span>|
|[<span data-ttu-id="e670b-117">CustomControlName-element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="e670b-117">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)|<span data-ttu-id="e670b-118">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="e670b-118">Optional element.</span></span><br /><br /> <span data-ttu-id="e670b-119">Anger namnet på en kontroll som används för att visa den nya gruppen.</span><span class="sxs-lookup"><span data-stu-id="e670b-119">Specifies the name of a control that is used to display the new group.</span></span>|
|[<span data-ttu-id="e670b-120">Label-element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="e670b-120">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)|<span data-ttu-id="e670b-121">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="e670b-121">Optional element.</span></span><br /><br /> <span data-ttu-id="e670b-122">Anger en etikett som visas när en ny grupp påträffas.</span><span class="sxs-lookup"><span data-stu-id="e670b-122">Specifies a label that is displayed when a new group is encountered.</span></span>|
|[<span data-ttu-id="e670b-123">PropertyName-element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="e670b-123">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)|<span data-ttu-id="e670b-124">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="e670b-124">Optional element.</span></span><br /><br /> <span data-ttu-id="e670b-125">Anger .NET-egenskapen som startar en ny grupp när dess värde ändras.</span><span class="sxs-lookup"><span data-stu-id="e670b-125">Specifies the .NET property the starts a new group whenever its value changes.</span></span>|
|[<span data-ttu-id="e670b-126">ScriptBlock-element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="e670b-126">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)|<span data-ttu-id="e670b-127">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="e670b-127">Optional element.</span></span><br /><br /> <span data-ttu-id="e670b-128">Anger det skript som startar en ny grupp när dess värde ändras.</span><span class="sxs-lookup"><span data-stu-id="e670b-128">Specifies the script that starts a new group whenever its value changes.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e670b-129">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="e670b-129">Parent Elements</span></span>

|<span data-ttu-id="e670b-130">Element</span><span class="sxs-lookup"><span data-stu-id="e670b-130">Element</span></span>|<span data-ttu-id="e670b-131">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e670b-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e670b-132">View-element (format)</span><span class="sxs-lookup"><span data-stu-id="e670b-132">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="e670b-133">Definierar en vy som visar ett eller flera .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="e670b-133">Defines a view that displays one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e670b-134">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="e670b-134">Remarks</span></span>

<span data-ttu-id="e670b-135">När du definierar hur en ny grupp av objekt visas måste du ange den egenskap eller det skript som ska starta den nya gruppen. Du kan dock inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="e670b-135">When defining how a new group of objects is displayed, you must specify the property or script that will start the new group; however, you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="e670b-136">Se även</span><span class="sxs-lookup"><span data-stu-id="e670b-136">See Also</span></span>

[<span data-ttu-id="e670b-137">CustomControlName-element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="e670b-137">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

[<span data-ttu-id="e670b-138">Label-element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="e670b-138">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)

[<span data-ttu-id="e670b-139">PropertyName-element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="e670b-139">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)

[<span data-ttu-id="e670b-140">ScriptBlock-element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="e670b-140">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="e670b-141">View-element (format)</span><span class="sxs-lookup"><span data-stu-id="e670b-141">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="e670b-142">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="e670b-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
