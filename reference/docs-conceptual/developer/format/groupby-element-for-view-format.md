---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy-element för View (format)
description: GroupBy-element för View (format)
ms.openlocfilehash: d8ca93a3b2c1490928885579919c07f5eb274cd8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652099"
---
# <a name="groupby-element-for-view-format"></a><span data-ttu-id="a63af-103">GroupBy-element för View (format)</span><span class="sxs-lookup"><span data-stu-id="a63af-103">GroupBy Element for View (Format)</span></span>

<span data-ttu-id="a63af-104">Definierar hur en ny grupp av objekt visas.</span><span class="sxs-lookup"><span data-stu-id="a63af-104">Defines how a new group of objects is displayed.</span></span> <span data-ttu-id="a63af-105">Det här elementet används när du definierar en tabell, en lista, en bred eller en anpassad vy.</span><span class="sxs-lookup"><span data-stu-id="a63af-105">This element is used when defining a table, list, wide, or custom control view.</span></span>

<span data-ttu-id="a63af-106">Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för vy (format)</span><span class="sxs-lookup"><span data-stu-id="a63af-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a63af-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="a63af-107">Syntax</span></span>

```xml
<GroupBy>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  <Label>TextToDisplay</Label>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameOfControl</CustomControlName>
</GroupBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a63af-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="a63af-108">Attributes and Elements</span></span>

<span data-ttu-id="a63af-109">I följande avsnitt beskrivs attribut, underordnade element och överordnade element.</span><span class="sxs-lookup"><span data-stu-id="a63af-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="a63af-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="a63af-110">Attributes</span></span>

<span data-ttu-id="a63af-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="a63af-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a63af-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="a63af-112">Child Elements</span></span>

|<span data-ttu-id="a63af-113">Element</span><span class="sxs-lookup"><span data-stu-id="a63af-113">Element</span></span>|<span data-ttu-id="a63af-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a63af-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a63af-115">CustomControl-element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="a63af-115">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="a63af-116">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="a63af-116">Optional element.</span></span><br /><br /> <span data-ttu-id="a63af-117">Definierar den anpassade kontrollen som visar nya grupper.</span><span class="sxs-lookup"><span data-stu-id="a63af-117">Defines the custom control that display new groups.</span></span>|
|[<span data-ttu-id="a63af-118">CustomControlName-element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="a63af-118">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)|<span data-ttu-id="a63af-119">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="a63af-119">Optional element.</span></span><br /><br /> <span data-ttu-id="a63af-120">Anger namnet på en kontroll som används för att visa den nya gruppen.</span><span class="sxs-lookup"><span data-stu-id="a63af-120">Specifies the name of a control that is used to display the new group.</span></span>|
|[<span data-ttu-id="a63af-121">Label-element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="a63af-121">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)|<span data-ttu-id="a63af-122">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="a63af-122">Optional element.</span></span><br /><br /> <span data-ttu-id="a63af-123">Anger en etikett som visas när en ny grupp påträffas.</span><span class="sxs-lookup"><span data-stu-id="a63af-123">Specifies a label that is displayed when a new group is encountered.</span></span>|
|[<span data-ttu-id="a63af-124">PropertyName-element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="a63af-124">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)|<span data-ttu-id="a63af-125">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="a63af-125">Optional element.</span></span><br /><br /> <span data-ttu-id="a63af-126">Anger .NET-egenskapen som startar en ny grupp när dess värde ändras.</span><span class="sxs-lookup"><span data-stu-id="a63af-126">Specifies the .NET property the starts a new group whenever its value changes.</span></span>|
|[<span data-ttu-id="a63af-127">ScriptBlock-element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="a63af-127">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)|<span data-ttu-id="a63af-128">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="a63af-128">Optional element.</span></span><br /><br /> <span data-ttu-id="a63af-129">Anger det skript som startar en ny grupp när dess värde ändras.</span><span class="sxs-lookup"><span data-stu-id="a63af-129">Specifies the script that starts a new group whenever its value changes.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a63af-130">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="a63af-130">Parent Elements</span></span>

|<span data-ttu-id="a63af-131">Element</span><span class="sxs-lookup"><span data-stu-id="a63af-131">Element</span></span>|<span data-ttu-id="a63af-132">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a63af-132">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a63af-133">View-element (format)</span><span class="sxs-lookup"><span data-stu-id="a63af-133">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="a63af-134">Definierar en vy som visar ett eller flera .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="a63af-134">Defines a view that displays one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a63af-135">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="a63af-135">Remarks</span></span>

<span data-ttu-id="a63af-136">När du definierar hur en ny grupp av objekt visas måste du ange den egenskap eller det skript som ska starta den nya gruppen. Du kan dock inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="a63af-136">When defining how a new group of objects is displayed, you must specify the property or script that will start the new group; however, you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="a63af-137">Se även</span><span class="sxs-lookup"><span data-stu-id="a63af-137">See Also</span></span>

[<span data-ttu-id="a63af-138">CustomControlName-element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="a63af-138">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

[<span data-ttu-id="a63af-139">Label-element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="a63af-139">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)

[<span data-ttu-id="a63af-140">PropertyName-element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="a63af-140">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)

[<span data-ttu-id="a63af-141">ScriptBlock-element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="a63af-141">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="a63af-142">View-element (format)</span><span class="sxs-lookup"><span data-stu-id="a63af-142">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="a63af-143">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="a63af-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
