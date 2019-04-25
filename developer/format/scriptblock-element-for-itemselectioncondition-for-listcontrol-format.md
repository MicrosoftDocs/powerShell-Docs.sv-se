---
title: ScriptBlock Element för ItemSelectionCondition för ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c929a6df-d050-416a-9de0-e913dd5a035c
caps.latest.revision: 8
ms.openlocfilehash: a0768a9c1ac66cd9dcf1848c4b031ccbc722b4c2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064415"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="a19b7-102">ScriptBlock-element för ItemSelectionCondition för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="a19b7-102">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="a19b7-103">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="a19b7-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="a19b7-104">När det här skriptet ska utvärderas till `true`villkoret uppfylls och listobjektet används.</span><span class="sxs-lookup"><span data-stu-id="a19b7-104">When this script is evaluated to `true`, the condition is met, and the list item is used.</span></span> <span data-ttu-id="a19b7-105">Det här elementet används när du definierar en listvy.</span><span class="sxs-lookup"><span data-stu-id="a19b7-105">This element is used when defining a list view.</span></span>

<span data-ttu-id="a19b7-106">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) ListControl Element (Format) ListEntries konfigurationselement för ListControl (Format) ListEntry elementet för ListEntries för ListControl (Format) ListItems som finns elementet för ListEntry för ListControl (Format) ListItem elementet för ListItems som finns för listan kontroll (Format) ItemSelectionCondition elementet för ListItem för ListControl (Format) ScriptBlock elementet för ItemSelectionCondition för ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="a19b7-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for List Control (Format) ItemSelectionCondition Element for ListItem for ListControl (Format) ScriptBlock Element for ItemSelectionCondition for ListControl  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a19b7-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="a19b7-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a19b7-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="a19b7-108">Attributes and Elements</span></span>

<span data-ttu-id="a19b7-109">I följande avsnitt beskrivs attribut, underordnade element och de överordnade element i den `ScriptBlock` element.</span><span class="sxs-lookup"><span data-stu-id="a19b7-109">The following sections describe attributes, child elements, and the parent elements of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a19b7-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="a19b7-110">Attributes</span></span>

<span data-ttu-id="a19b7-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="a19b7-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a19b7-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="a19b7-112">Child Elements</span></span>

<span data-ttu-id="a19b7-113">Ingen.</span><span class="sxs-lookup"><span data-stu-id="a19b7-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a19b7-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="a19b7-114">Parent Elements</span></span>

|<span data-ttu-id="a19b7-115">Element</span><span class="sxs-lookup"><span data-stu-id="a19b7-115">Element</span></span>|<span data-ttu-id="a19b7-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a19b7-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a19b7-117">ItemSelectionCondition Element för ListItem för ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="a19b7-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="a19b7-118">Definierar de villkor som måste finnas för det här objektet i listan som ska användas.</span><span class="sxs-lookup"><span data-stu-id="a19b7-118">Defines the condition that must exist for this list item to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a19b7-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="a19b7-119">Text Value</span></span>

<span data-ttu-id="a19b7-120">Ange det skript som ska utvärderas.</span><span class="sxs-lookup"><span data-stu-id="a19b7-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="a19b7-121">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="a19b7-121">Remarks</span></span>

<span data-ttu-id="a19b7-122">Om det här elementet används som du kan inte ange den `PropertyName` element när du definierar urvalsvillkoret.</span><span class="sxs-lookup"><span data-stu-id="a19b7-122">If this element is used, you cannot specify the `PropertyName` element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="a19b7-123">Se även</span><span class="sxs-lookup"><span data-stu-id="a19b7-123">See Also</span></span>

[<span data-ttu-id="a19b7-124">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="a19b7-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
