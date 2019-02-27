---
title: ItemSelectionCondition Element för ListItem för ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2668aea-37e9-4753-a4e9-7980ae5ec2eb
caps.latest.revision: 10
ms.openlocfilehash: 6bc0ccbcc5bd62429f63ed220da66dc66f44f7ca
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850920"
---
# <a name="itemselectioncondition-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="b1b81-102">ItemSelectionCondition-element för ListItem för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="b1b81-102">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="b1b81-103">Definierar de villkor som måste finnas för det här objektet i listan som ska användas.</span><span class="sxs-lookup"><span data-stu-id="b1b81-103">Defines the condition that must exist for this list item to be used.</span></span>

<span data-ttu-id="b1b81-104">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) ListControl Element (Format) ListEntries konfigurationselement för ListControl (Format) ListEntry elementet för ListEntries för ListControl (Format) ListItems som finns elementet för ListEntry för ListControl (Format) ListItem elementet för ListItems som finns för ListControl (Format) ItemSelectionCondition elementet för ListItem för ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="b1b81-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b1b81-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="b1b81-105">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b1b81-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="b1b81-106">Attributes and Elements</span></span>

<span data-ttu-id="b1b81-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `ItemSelectionCondition` element.</span><span class="sxs-lookup"><span data-stu-id="b1b81-107">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b1b81-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="b1b81-108">Attributes</span></span>

<span data-ttu-id="b1b81-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="b1b81-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b1b81-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="b1b81-110">Child Elements</span></span>

|<span data-ttu-id="b1b81-111">Element</span><span class="sxs-lookup"><span data-stu-id="b1b81-111">Element</span></span>|<span data-ttu-id="b1b81-112">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b1b81-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b1b81-113">PropertyName-Element för ItemSelectionCondition för ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="b1b81-113">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="b1b81-114">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="b1b81-114">Optional element.</span></span><br /><br /> <span data-ttu-id="b1b81-115">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="b1b81-115">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="b1b81-116">ScriptBlock Element för ItemSelectionCondition för ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="b1b81-116">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="b1b81-117">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="b1b81-117">Optional element.</span></span><br /><br /> <span data-ttu-id="b1b81-118">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="b1b81-118">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b1b81-119">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="b1b81-119">Parent Elements</span></span>

|<span data-ttu-id="b1b81-120">Element</span><span class="sxs-lookup"><span data-stu-id="b1b81-120">Element</span></span>|<span data-ttu-id="b1b81-121">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b1b81-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b1b81-122">ListItem Element för ListItems som finns för ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="b1b81-122">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="b1b81-123">Definierar egenskapen eller skript som vars värde visas i en rad i listvyn.</span><span class="sxs-lookup"><span data-stu-id="b1b81-123">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b1b81-124">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="b1b81-124">Remarks</span></span>

<span data-ttu-id="b1b81-125">Du kan ange ett egenskapsnamn eller ett skript för det här villkoret men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="b1b81-125">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="b1b81-126">Se även</span><span class="sxs-lookup"><span data-stu-id="b1b81-126">See Also</span></span>

[<span data-ttu-id="b1b81-127">ListItem Element för ListItems som finns för ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="b1b81-127">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="b1b81-128">PropertyName-Element för ItemSelectionCondition för ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="b1b81-128">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="b1b81-129">ScriptBlock Element för ItemSelectionCondition för ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="b1b81-129">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="b1b81-130">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="b1b81-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
