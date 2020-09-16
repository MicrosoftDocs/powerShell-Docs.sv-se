---
title: Script block-element för ItemSelectionCondition för ListControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 38dc952bfadd6aed24bae8cbef05adcd22e61dd4
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787639"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="1a026-102">ScriptBlock-element för ItemSelectionCondition för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="1a026-102">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="1a026-103">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="1a026-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="1a026-104">När det här skriptet utvärderas `true` , uppfylls villkoret och listobjektet används.</span><span class="sxs-lookup"><span data-stu-id="1a026-104">When this script is evaluated to `true`, the condition is met, and the list item is used.</span></span> <span data-ttu-id="1a026-105">Det här elementet används när du definierar en listvy.</span><span class="sxs-lookup"><span data-stu-id="1a026-105">This element is used when defining a list view.</span></span>

<span data-ttu-id="1a026-106">Konfigurations element (format) ViewDefinitions element (format) View-element (format) ListControl-element (format) ListEntries-element för ListControl (format) ListEntry-element för ListEntries för ListControl (format) ListItems-element för ListEntry för ListControl (format) ListItem-element för ListItems (format) ItemSelectionCondition-element för ListItem (format) ListControl-element för script block (format)</span><span class="sxs-lookup"><span data-stu-id="1a026-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for List Control (Format) ItemSelectionCondition Element for ListItem for ListControl (Format) ScriptBlock Element for ItemSelectionCondition for ListControl  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1a026-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="1a026-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1a026-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="1a026-108">Attributes and Elements</span></span>

<span data-ttu-id="1a026-109">I följande avsnitt beskrivs attribut, underordnade element och `ScriptBlock` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="1a026-109">The following sections describe attributes, child elements, and the parent elements of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1a026-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="1a026-110">Attributes</span></span>

<span data-ttu-id="1a026-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="1a026-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1a026-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="1a026-112">Child Elements</span></span>

<span data-ttu-id="1a026-113">Inga.</span><span class="sxs-lookup"><span data-stu-id="1a026-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1a026-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="1a026-114">Parent Elements</span></span>

|<span data-ttu-id="1a026-115">Element</span><span class="sxs-lookup"><span data-stu-id="1a026-115">Element</span></span>|<span data-ttu-id="1a026-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="1a026-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1a026-117">ItemSelectionCondition-element för ListItem för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="1a026-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="1a026-118">Definierar det villkor som måste finnas för att listobjektet ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="1a026-118">Defines the condition that must exist for this list item to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1a026-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="1a026-119">Text Value</span></span>

<span data-ttu-id="1a026-120">Ange det skript som utvärderas.</span><span class="sxs-lookup"><span data-stu-id="1a026-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="1a026-121">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="1a026-121">Remarks</span></span>

<span data-ttu-id="1a026-122">Om det här elementet används kan du inte ange `PropertyName` elementet när du definierar urvals villkoret.</span><span class="sxs-lookup"><span data-stu-id="1a026-122">If this element is used, you cannot specify the `PropertyName` element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="1a026-123">Se även</span><span class="sxs-lookup"><span data-stu-id="1a026-123">See Also</span></span>

[<span data-ttu-id="1a026-124">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="1a026-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
