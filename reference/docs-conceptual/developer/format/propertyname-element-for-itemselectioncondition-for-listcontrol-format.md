---
title: PropertyName-element för ItemSelectionCondition för ListControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 8bdbb05326f7ff5ccffa46215631a5c954080dc1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780873"
---
# <a name="propertyname-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="9690f-102">PropertyName-element för ItemSelectionCondition för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="9690f-102">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="9690f-103">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="9690f-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="9690f-104">När den här egenskapen finns eller när den utvärderas `true` , uppfylls villkoret och vyn används.</span><span class="sxs-lookup"><span data-stu-id="9690f-104">When this property is present or when it evaluates to `true`, the condition is met, and the view is used.</span></span> <span data-ttu-id="9690f-105">Det här elementet används när du definierar en listvy.</span><span class="sxs-lookup"><span data-stu-id="9690f-105">This element is used when defining a list view.</span></span>

<span data-ttu-id="9690f-106">Konfigurations element (format) ViewDefinitions element (format) View-element (format) ListControl-element (format) ListEntries-element (format) ListEntry-element för ListControl (format) ListItems-element för ListEntry (format) ListControl-element för ListItem (format) ListItems-element för ListControl (format) ItemSelectionCondition-element för ListItem-elementet ListControls (format)</span><span class="sxs-lookup"><span data-stu-id="9690f-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControls PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9690f-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="9690f-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9690f-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="9690f-108">Attributes and Elements</span></span>

<span data-ttu-id="9690f-109">I följande avsnitt beskrivs attribut, underordnade element och `PropertyName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="9690f-109">The following sections describe attributes, child elements, and the parent elements of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9690f-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="9690f-110">Attributes</span></span>

<span data-ttu-id="9690f-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="9690f-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9690f-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="9690f-112">Child Elements</span></span>

<span data-ttu-id="9690f-113">Inga.</span><span class="sxs-lookup"><span data-stu-id="9690f-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9690f-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="9690f-114">Parent Elements</span></span>

|<span data-ttu-id="9690f-115">Element</span><span class="sxs-lookup"><span data-stu-id="9690f-115">Element</span></span>|<span data-ttu-id="9690f-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="9690f-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9690f-117">ItemSelectionCondition-element för ListItem för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="9690f-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)||

## <a name="text-value"></a><span data-ttu-id="9690f-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="9690f-118">Text Value</span></span>

<span data-ttu-id="9690f-119">Ange namnet på den egenskap vars värde visas.</span><span class="sxs-lookup"><span data-stu-id="9690f-119">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="9690f-120">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="9690f-120">Remarks</span></span>

<span data-ttu-id="9690f-121">Om det här elementet används kan du inte ange [script block](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) -elementet när du definierar urvals villkoret.</span><span class="sxs-lookup"><span data-stu-id="9690f-121">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="9690f-122">Se även</span><span class="sxs-lookup"><span data-stu-id="9690f-122">See Also</span></span>

[<span data-ttu-id="9690f-123">Script block-element för ItemSelectionCondition för ListIControl (format)</span><span class="sxs-lookup"><span data-stu-id="9690f-123">ScriptBlock Element for ItemSelectionCondition for ListIControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="9690f-124">ItemSelectionCondition-element för ListItem för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="9690f-124">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="9690f-125">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="9690f-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
