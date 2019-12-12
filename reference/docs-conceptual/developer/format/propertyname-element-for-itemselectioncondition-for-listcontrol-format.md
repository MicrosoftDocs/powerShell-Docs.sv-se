---
title: PropertyName-element för ItemSelectionCondition för ListControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5e707ae-3c84-4ceb-ba31-56b3ffde6d6c
caps.latest.revision: 7
ms.openlocfilehash: b15e26e18126f69eee7c3a857f9a461d4bdf5848
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354098"
---
# <a name="propertyname-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="bbc29-102">PropertyName-element för ItemSelectionCondition för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="bbc29-102">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="bbc29-103">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="bbc29-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="bbc29-104">När den här egenskapen finns eller när den utvärderas till `true`, uppfylls villkoret och vyn används.</span><span class="sxs-lookup"><span data-stu-id="bbc29-104">When this property is present or when it evaluates to `true`, the condition is met, and the view is used.</span></span> <span data-ttu-id="bbc29-105">Det här elementet används när du definierar en listvy.</span><span class="sxs-lookup"><span data-stu-id="bbc29-105">This element is used when defining a list view.</span></span>

<span data-ttu-id="bbc29-106">Konfigurations element (format) ViewDefinitions element (format) View-element (format) ListControl-element (format) element för ListEntries (format) ListEntry-element för ListControl (format) ListItems-element för ListEntry (format) ListControl Element för ListItems för ListControl (format) ItemSelectionCondition-element för ListItem för ListControls PropertyName-element för ItemSelectionCondition för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="bbc29-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControls PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bbc29-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="bbc29-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bbc29-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="bbc29-108">Attributes and Elements</span></span>

<span data-ttu-id="bbc29-109">I följande avsnitt beskrivs attribut, underordnade element och de överordnade elementen i `PropertyName`-elementet.</span><span class="sxs-lookup"><span data-stu-id="bbc29-109">The following sections describe attributes, child elements, and the parent elements of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="bbc29-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="bbc29-110">Attributes</span></span>

<span data-ttu-id="bbc29-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="bbc29-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bbc29-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="bbc29-112">Child Elements</span></span>

<span data-ttu-id="bbc29-113">Ingen.</span><span class="sxs-lookup"><span data-stu-id="bbc29-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="bbc29-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="bbc29-114">Parent Elements</span></span>

|<span data-ttu-id="bbc29-115">Element</span><span class="sxs-lookup"><span data-stu-id="bbc29-115">Element</span></span>|<span data-ttu-id="bbc29-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="bbc29-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bbc29-117">ItemSelectionCondition-element för ListItem för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="bbc29-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)||

## <a name="text-value"></a><span data-ttu-id="bbc29-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="bbc29-118">Text Value</span></span>

<span data-ttu-id="bbc29-119">Ange namnet på den egenskap vars värde visas.</span><span class="sxs-lookup"><span data-stu-id="bbc29-119">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="bbc29-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="bbc29-120">Remarks</span></span>

<span data-ttu-id="bbc29-121">Om det här elementet används kan du inte ange [script block](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) -elementet när du definierar urvals villkoret.</span><span class="sxs-lookup"><span data-stu-id="bbc29-121">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="bbc29-122">Se även</span><span class="sxs-lookup"><span data-stu-id="bbc29-122">See Also</span></span>

[<span data-ttu-id="bbc29-123">Script block-element för ItemSelectionCondition för ListIControl (format)</span><span class="sxs-lookup"><span data-stu-id="bbc29-123">ScriptBlock Element for ItemSelectionCondition for ListIControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="bbc29-124">ItemSelectionCondition-element för ListItem för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="bbc29-124">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="bbc29-125">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="bbc29-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
