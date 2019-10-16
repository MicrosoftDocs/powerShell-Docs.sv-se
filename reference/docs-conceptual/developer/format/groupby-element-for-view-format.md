---
title: GroupBy-element för vy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 67a2b061-2a4a-4ad1-84f9-cdbefb64aaab
caps.latest.revision: 8
ms.openlocfilehash: abb8b91626128b3deaa2db24a9fd8b34a6563410
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354966"
---
# <a name="groupby-element-for-view-format"></a><span data-ttu-id="18841-102">GroupBy-element för View (format)</span><span class="sxs-lookup"><span data-stu-id="18841-102">GroupBy Element for View (Format)</span></span>

<span data-ttu-id="18841-103">Definierar hur en ny grupp av objekt visas.</span><span class="sxs-lookup"><span data-stu-id="18841-103">Defines how a new group of objects is displayed.</span></span> <span data-ttu-id="18841-104">Det här elementet används när du definierar en tabell, en lista, en bred eller en anpassad vy.</span><span class="sxs-lookup"><span data-stu-id="18841-104">This element is used when defining a table, list, wide, or custom control view.</span></span>

<span data-ttu-id="18841-105">Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för vy (format)</span><span class="sxs-lookup"><span data-stu-id="18841-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="18841-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="18841-106">Syntax</span></span>

```xml
<GroupBy>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  <Label>TextToDisplay</Label>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameOfControl</CustomControlName>
</GroupBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="18841-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="18841-107">Attributes and Elements</span></span>

<span data-ttu-id="18841-108">I följande avsnitt beskrivs attribut, underordnade element och överordnade element.</span><span class="sxs-lookup"><span data-stu-id="18841-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="18841-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="18841-109">Attributes</span></span>

<span data-ttu-id="18841-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="18841-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="18841-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="18841-111">Child Elements</span></span>

|<span data-ttu-id="18841-112">Element</span><span class="sxs-lookup"><span data-stu-id="18841-112">Element</span></span>|<span data-ttu-id="18841-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="18841-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="18841-114">CustomControl-element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="18841-114">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="18841-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="18841-115">Optional element.</span></span><br /><br /> <span data-ttu-id="18841-116">Definierar den anpassade kontrollen som visar nya grupper.</span><span class="sxs-lookup"><span data-stu-id="18841-116">Defines the custom control that display new groups.</span></span>|
|[<span data-ttu-id="18841-117">CustomControlName-element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="18841-117">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)|<span data-ttu-id="18841-118">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="18841-118">Optional element.</span></span><br /><br /> <span data-ttu-id="18841-119">Anger namnet på en kontroll som används för att visa den nya gruppen.</span><span class="sxs-lookup"><span data-stu-id="18841-119">Specifies the name of a control that is used to display the new group.</span></span>|
|[<span data-ttu-id="18841-120">Etikett element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="18841-120">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)|<span data-ttu-id="18841-121">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="18841-121">Optional element.</span></span><br /><br /> <span data-ttu-id="18841-122">Anger en etikett som visas när en ny grupp påträffas.</span><span class="sxs-lookup"><span data-stu-id="18841-122">Specifies a label that is displayed when a new group is encountered.</span></span>|
|[<span data-ttu-id="18841-123">PropertyName-element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="18841-123">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)|<span data-ttu-id="18841-124">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="18841-124">Optional element.</span></span><br /><br /> <span data-ttu-id="18841-125">Anger .NET-egenskapen som startar en ny grupp när dess värde ändras.</span><span class="sxs-lookup"><span data-stu-id="18841-125">Specifies the .NET property the starts a new group whenever its value changes.</span></span>|
|[<span data-ttu-id="18841-126">Script block-element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="18841-126">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)|<span data-ttu-id="18841-127">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="18841-127">Optional element.</span></span><br /><br /> <span data-ttu-id="18841-128">Anger det skript som startar en ny grupp när dess värde ändras.</span><span class="sxs-lookup"><span data-stu-id="18841-128">Specifies the script that starts a new group whenever its value changes.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="18841-129">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="18841-129">Parent Elements</span></span>

|<span data-ttu-id="18841-130">Element</span><span class="sxs-lookup"><span data-stu-id="18841-130">Element</span></span>|<span data-ttu-id="18841-131">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="18841-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="18841-132">Visa element (format)</span><span class="sxs-lookup"><span data-stu-id="18841-132">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="18841-133">Definierar en vy som visar ett eller flera .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="18841-133">Defines a view that displays one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="18841-134">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="18841-134">Remarks</span></span>

<span data-ttu-id="18841-135">När du definierar hur en ny grupp av objekt visas måste du ange den egenskap eller det skript som ska starta den nya gruppen. Du kan dock inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="18841-135">When defining how a new group of objects is displayed, you must specify the property or script that will start the new group; however, you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="18841-136">Se även</span><span class="sxs-lookup"><span data-stu-id="18841-136">See Also</span></span>

[<span data-ttu-id="18841-137">CustomControlName-element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="18841-137">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

[<span data-ttu-id="18841-138">Etikett element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="18841-138">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)

[<span data-ttu-id="18841-139">PropertyName-element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="18841-139">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)

[<span data-ttu-id="18841-140">Script block-element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="18841-140">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="18841-141">Visa element (format)</span><span class="sxs-lookup"><span data-stu-id="18841-141">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="18841-142">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="18841-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
