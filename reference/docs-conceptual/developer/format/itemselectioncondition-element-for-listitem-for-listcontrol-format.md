---
title: ItemSelectionCondition-element för ListItem för ListControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2668aea-37e9-4753-a4e9-7980ae5ec2eb
caps.latest.revision: 10
ms.openlocfilehash: 6bc0ccbcc5bd62429f63ed220da66dc66f44f7ca
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72356058"
---
# <a name="itemselectioncondition-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="77314-102">ItemSelectionCondition-element för ListItem för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="77314-102">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="77314-103">Definierar det villkor som måste finnas för att listobjektet ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="77314-103">Defines the condition that must exist for this list item to be used.</span></span>

<span data-ttu-id="77314-104">Konfigurations element (format) ViewDefinitions element (format) View-element (format) ListControl element (format) ListEntries-element för ListControl (format) ListEntry-element för ListEntries för ListControl (format) ListItems-element för ListEntry för ListControl (format) ListItem-elementet för ListItems för ListControl (format) ItemSelectionCondition-elementet för ListItem för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="77314-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="77314-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="77314-105">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="77314-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="77314-106">Attributes and Elements</span></span>

<span data-ttu-id="77314-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `ItemSelectionCondition`-elementet.</span><span class="sxs-lookup"><span data-stu-id="77314-107">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="77314-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="77314-108">Attributes</span></span>

<span data-ttu-id="77314-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="77314-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="77314-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="77314-110">Child Elements</span></span>

|<span data-ttu-id="77314-111">Element</span><span class="sxs-lookup"><span data-stu-id="77314-111">Element</span></span>|<span data-ttu-id="77314-112">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="77314-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="77314-113">PropertyName-element för ItemSelectionCondition för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="77314-113">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="77314-114">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="77314-114">Optional element.</span></span><br /><br /> <span data-ttu-id="77314-115">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="77314-115">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="77314-116">Script block-element för ItemSelectionCondition för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="77314-116">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="77314-117">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="77314-117">Optional element.</span></span><br /><br /> <span data-ttu-id="77314-118">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="77314-118">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="77314-119">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="77314-119">Parent Elements</span></span>

|<span data-ttu-id="77314-120">Element</span><span class="sxs-lookup"><span data-stu-id="77314-120">Element</span></span>|<span data-ttu-id="77314-121">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="77314-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="77314-122">ListItem-element för ListItems för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="77314-122">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="77314-123">Definierar egenskapen eller skriptet vars värde visas i en rad i list visningen.</span><span class="sxs-lookup"><span data-stu-id="77314-123">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="77314-124">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="77314-124">Remarks</span></span>

<span data-ttu-id="77314-125">Du kan ange ett egenskaps namn eller ett skript för villkoret, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="77314-125">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="77314-126">Se även</span><span class="sxs-lookup"><span data-stu-id="77314-126">See Also</span></span>

[<span data-ttu-id="77314-127">ListItem-element för ListItems för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="77314-127">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="77314-128">PropertyName-element för ItemSelectionCondition för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="77314-128">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="77314-129">Script block-element för ItemSelectionCondition för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="77314-129">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="77314-130">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="77314-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
