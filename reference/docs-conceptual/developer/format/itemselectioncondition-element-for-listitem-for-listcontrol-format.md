---
title: ItemSelectionCondition-element för ListItem för ListControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: f5c388928668e03b96923130fb5849f637548f12
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783627"
---
# <a name="itemselectioncondition-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="55e07-102">ItemSelectionCondition-element för ListItem för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="55e07-102">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="55e07-103">Definierar det villkor som måste finnas för att listobjektet ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="55e07-103">Defines the condition that must exist for this list item to be used.</span></span>

<span data-ttu-id="55e07-104">Konfigurations element (format) ViewDefinitions element (format) View-element (format) ListControl-element (format) ListEntries-element för ListControl (format) ListEntry-element för ListEntries för ListControl (format) ListItems element for ListEntry for ListControl (format) ListItem element for ListItems for ListControl (format) ItemSelectionCondition element for ListItem for ListControl for (format)</span><span class="sxs-lookup"><span data-stu-id="55e07-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="55e07-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="55e07-105">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="55e07-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="55e07-106">Attributes and Elements</span></span>

<span data-ttu-id="55e07-107">I följande avsnitt beskrivs attribut, underordnade element och `ItemSelectionCondition` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="55e07-107">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="55e07-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="55e07-108">Attributes</span></span>

<span data-ttu-id="55e07-109">Inga.</span><span class="sxs-lookup"><span data-stu-id="55e07-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="55e07-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="55e07-110">Child Elements</span></span>

|<span data-ttu-id="55e07-111">Element</span><span class="sxs-lookup"><span data-stu-id="55e07-111">Element</span></span>|<span data-ttu-id="55e07-112">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="55e07-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="55e07-113">PropertyName-element för ItemSelectionCondition för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="55e07-113">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="55e07-114">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="55e07-114">Optional element.</span></span><br /><br /> <span data-ttu-id="55e07-115">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="55e07-115">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="55e07-116">ScriptBlock-element för ItemSelectionCondition för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="55e07-116">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="55e07-117">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="55e07-117">Optional element.</span></span><br /><br /> <span data-ttu-id="55e07-118">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="55e07-118">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="55e07-119">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="55e07-119">Parent Elements</span></span>

|<span data-ttu-id="55e07-120">Element</span><span class="sxs-lookup"><span data-stu-id="55e07-120">Element</span></span>|<span data-ttu-id="55e07-121">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="55e07-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="55e07-122">ListItem-element för ListItems för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="55e07-122">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="55e07-123">Definierar egenskapen eller skriptet vars värde visas i en rad i list visningen.</span><span class="sxs-lookup"><span data-stu-id="55e07-123">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="55e07-124">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="55e07-124">Remarks</span></span>

<span data-ttu-id="55e07-125">Du kan ange ett egenskaps namn eller ett skript för villkoret, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="55e07-125">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="55e07-126">Se även</span><span class="sxs-lookup"><span data-stu-id="55e07-126">See Also</span></span>

[<span data-ttu-id="55e07-127">ListItem-element för ListItems för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="55e07-127">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="55e07-128">PropertyName-element för ItemSelectionCondition för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="55e07-128">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="55e07-129">ScriptBlock-element för ItemSelectionCondition för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="55e07-129">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="55e07-130">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="55e07-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
