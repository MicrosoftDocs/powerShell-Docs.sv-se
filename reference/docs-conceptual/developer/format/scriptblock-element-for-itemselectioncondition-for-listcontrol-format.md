---
ms.date: 09/13/2016
ms.topic: reference
title: ScriptBlock-element för ItemSelectionCondition för ListControl (format)
description: ScriptBlock-element för ItemSelectionCondition för ListControl (format)
ms.openlocfilehash: 1e518f898e0e1e62ca64f9897b1323cc6dd89ae9
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92665051"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="54750-103">ScriptBlock-element för ItemSelectionCondition för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="54750-103">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="54750-104">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="54750-104">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="54750-105">När det här skriptet utvärderas `true` , uppfylls villkoret och listobjektet används.</span><span class="sxs-lookup"><span data-stu-id="54750-105">When this script is evaluated to `true`, the condition is met, and the list item is used.</span></span> <span data-ttu-id="54750-106">Det här elementet används när du definierar en listvy.</span><span class="sxs-lookup"><span data-stu-id="54750-106">This element is used when defining a list view.</span></span>

<span data-ttu-id="54750-107">Konfigurations element (format) ViewDefinitions element (format) View-element (format) ListControl-element (format) ListEntries-element för ListControl (format) ListEntry-element för ListEntries för ListControl (format) ListItems-element för ListEntry för ListControl (format) ListItem-element för ListItems (format) ItemSelectionCondition-element för ListItem (format) ListControl-element för script block (format)</span><span class="sxs-lookup"><span data-stu-id="54750-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for List Control (Format) ItemSelectionCondition Element for ListItem for ListControl (Format) ScriptBlock Element for ItemSelectionCondition for ListControl  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="54750-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="54750-108">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="54750-109">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="54750-109">Attributes and Elements</span></span>

<span data-ttu-id="54750-110">I följande avsnitt beskrivs attribut, underordnade element och `ScriptBlock` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="54750-110">The following sections describe attributes, child elements, and the parent elements of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="54750-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="54750-111">Attributes</span></span>

<span data-ttu-id="54750-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="54750-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="54750-113">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="54750-113">Child Elements</span></span>

<span data-ttu-id="54750-114">Inga.</span><span class="sxs-lookup"><span data-stu-id="54750-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="54750-115">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="54750-115">Parent Elements</span></span>

|<span data-ttu-id="54750-116">Element</span><span class="sxs-lookup"><span data-stu-id="54750-116">Element</span></span>|<span data-ttu-id="54750-117">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="54750-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="54750-118">ItemSelectionCondition-element för ListItem för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="54750-118">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="54750-119">Definierar det villkor som måste finnas för att listobjektet ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="54750-119">Defines the condition that must exist for this list item to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="54750-120">Textvärde</span><span class="sxs-lookup"><span data-stu-id="54750-120">Text Value</span></span>

<span data-ttu-id="54750-121">Ange det skript som utvärderas.</span><span class="sxs-lookup"><span data-stu-id="54750-121">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="54750-122">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="54750-122">Remarks</span></span>

<span data-ttu-id="54750-123">Om det här elementet används kan du inte ange `PropertyName` elementet när du definierar urvals villkoret.</span><span class="sxs-lookup"><span data-stu-id="54750-123">If this element is used, you cannot specify the `PropertyName` element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="54750-124">Se även</span><span class="sxs-lookup"><span data-stu-id="54750-124">See Also</span></span>

[<span data-ttu-id="54750-125">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="54750-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
