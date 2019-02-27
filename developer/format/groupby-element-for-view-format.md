---
title: GroupBy-Element för Visa (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 67a2b061-2a4a-4ad1-84f9-cdbefb64aaab
caps.latest.revision: 8
ms.openlocfilehash: abb8b91626128b3deaa2db24a9fd8b34a6563410
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849282"
---
# <a name="groupby-element-for-view-format"></a><span data-ttu-id="389c9-102">GroupBy-element för View (format)</span><span class="sxs-lookup"><span data-stu-id="389c9-102">GroupBy Element for View (Format)</span></span>

<span data-ttu-id="389c9-103">Definierar hur en ny grupp med objekt visas.</span><span class="sxs-lookup"><span data-stu-id="389c9-103">Defines how a new group of objects is displayed.</span></span> <span data-ttu-id="389c9-104">Det här elementet används när du definierar en tabell, lista, brett eller anpassad vy.</span><span class="sxs-lookup"><span data-stu-id="389c9-104">This element is used when defining a table, list, wide, or custom control view.</span></span>

<span data-ttu-id="389c9-105">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) GroupBy konfigurationselement för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="389c9-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="389c9-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="389c9-106">Syntax</span></span>

```xml
<GroupBy>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  <Label>TextToDisplay</Label>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameOfControl</CustomControlName>
</GroupBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="389c9-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="389c9-107">Attributes and Elements</span></span>

<span data-ttu-id="389c9-108">I följande avsnitt beskrivs attribut, element i underordnade och överordnade element.</span><span class="sxs-lookup"><span data-stu-id="389c9-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="389c9-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="389c9-109">Attributes</span></span>

<span data-ttu-id="389c9-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="389c9-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="389c9-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="389c9-111">Child Elements</span></span>

|<span data-ttu-id="389c9-112">Element</span><span class="sxs-lookup"><span data-stu-id="389c9-112">Element</span></span>|<span data-ttu-id="389c9-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="389c9-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="389c9-114">Anpassad kontroll Element för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="389c9-114">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="389c9-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="389c9-115">Optional element.</span></span><br /><br /> <span data-ttu-id="389c9-116">Definierar den anpassade kontrollen som visar nya grupper.</span><span class="sxs-lookup"><span data-stu-id="389c9-116">Defines the custom control that display new groups.</span></span>|
|[<span data-ttu-id="389c9-117">CustomControlName Element för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="389c9-117">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)|<span data-ttu-id="389c9-118">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="389c9-118">Optional element.</span></span><br /><br /> <span data-ttu-id="389c9-119">Anger namnet på en kontroll som används för att visa den nya gruppen.</span><span class="sxs-lookup"><span data-stu-id="389c9-119">Specifies the name of a control that is used to display the new group.</span></span>|
|[<span data-ttu-id="389c9-120">Etikettelement för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="389c9-120">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)|<span data-ttu-id="389c9-121">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="389c9-121">Optional element.</span></span><br /><br /> <span data-ttu-id="389c9-122">Anger en etikett som visas när en ny grupp har påträffats.</span><span class="sxs-lookup"><span data-stu-id="389c9-122">Specifies a label that is displayed when a new group is encountered.</span></span>|
|[<span data-ttu-id="389c9-123">PropertyName-Element för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="389c9-123">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)|<span data-ttu-id="389c9-124">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="389c9-124">Optional element.</span></span><br /><br /> <span data-ttu-id="389c9-125">Anger egenskapen .NET startar en ny grupp när dess värde ändras.</span><span class="sxs-lookup"><span data-stu-id="389c9-125">Specifies the .NET property the starts a new group whenever its value changes.</span></span>|
|[<span data-ttu-id="389c9-126">ScriptBlock Element för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="389c9-126">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)|<span data-ttu-id="389c9-127">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="389c9-127">Optional element.</span></span><br /><br /> <span data-ttu-id="389c9-128">Anger det skript som startar en ny grupp när dess värde ändras.</span><span class="sxs-lookup"><span data-stu-id="389c9-128">Specifies the script that starts a new group whenever its value changes.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="389c9-129">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="389c9-129">Parent Elements</span></span>

|<span data-ttu-id="389c9-130">Element</span><span class="sxs-lookup"><span data-stu-id="389c9-130">Element</span></span>|<span data-ttu-id="389c9-131">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="389c9-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="389c9-132">Visa Element (Format)</span><span class="sxs-lookup"><span data-stu-id="389c9-132">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="389c9-133">Definierar en vy som visar en eller flera .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="389c9-133">Defines a view that displays one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="389c9-134">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="389c9-134">Remarks</span></span>

<span data-ttu-id="389c9-135">När du definierar hur en ny grupp med objekt visas, måste du ange egenskapen eller skript som startar den nya gruppen; Du kan dock ange båda.</span><span class="sxs-lookup"><span data-stu-id="389c9-135">When defining how a new group of objects is displayed, you must specify the property or script that will start the new group; however, you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="389c9-136">Se även</span><span class="sxs-lookup"><span data-stu-id="389c9-136">See Also</span></span>

[<span data-ttu-id="389c9-137">CustomControlName Element för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="389c9-137">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

[<span data-ttu-id="389c9-138">Etikettelement för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="389c9-138">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)

[<span data-ttu-id="389c9-139">PropertyName-Element för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="389c9-139">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)

[<span data-ttu-id="389c9-140">ScriptBlock Element för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="389c9-140">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="389c9-141">Visa Element (Format)</span><span class="sxs-lookup"><span data-stu-id="389c9-141">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="389c9-142">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="389c9-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
