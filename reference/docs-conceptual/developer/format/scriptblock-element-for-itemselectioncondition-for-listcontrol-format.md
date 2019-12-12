---
title: Script block-element för ItemSelectionCondition för ListControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c929a6df-d050-416a-9de0-e913dd5a035c
caps.latest.revision: 8
ms.openlocfilehash: a0768a9c1ac66cd9dcf1848c4b031ccbc722b4c2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353895"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="83575-102">ScriptBlock-element för ItemSelectionCondition för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="83575-102">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="83575-103">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="83575-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="83575-104">När det här skriptet utvärderas till `true`, uppfylls villkoret och listobjektet används.</span><span class="sxs-lookup"><span data-stu-id="83575-104">When this script is evaluated to `true`, the condition is met, and the list item is used.</span></span> <span data-ttu-id="83575-105">Det här elementet används när du definierar en listvy.</span><span class="sxs-lookup"><span data-stu-id="83575-105">This element is used when defining a list view.</span></span>

<span data-ttu-id="83575-106">Konfigurations element (format) ViewDefinitions element (format) View-element (format) ListControl element (format) ListEntries-element för ListControl (format) ListEntry-element för ListEntries för ListControl (format) ListItems-element för ListEntry för ListControl (format) ListItem-element för ListItems för List kontroll (format) ItemSelectionCondition-element för ListItem för ListControl (format) script block-element för ItemSelectionCondition för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="83575-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for List Control (Format) ItemSelectionCondition Element for ListItem for ListControl (Format) ScriptBlock Element for ItemSelectionCondition for ListControl  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="83575-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="83575-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="83575-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="83575-108">Attributes and Elements</span></span>

<span data-ttu-id="83575-109">I följande avsnitt beskrivs attribut, underordnade element och de överordnade elementen i `ScriptBlock`-elementet.</span><span class="sxs-lookup"><span data-stu-id="83575-109">The following sections describe attributes, child elements, and the parent elements of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="83575-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="83575-110">Attributes</span></span>

<span data-ttu-id="83575-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="83575-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="83575-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="83575-112">Child Elements</span></span>

<span data-ttu-id="83575-113">Ingen.</span><span class="sxs-lookup"><span data-stu-id="83575-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="83575-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="83575-114">Parent Elements</span></span>

|<span data-ttu-id="83575-115">Element</span><span class="sxs-lookup"><span data-stu-id="83575-115">Element</span></span>|<span data-ttu-id="83575-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="83575-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="83575-117">ItemSelectionCondition-element för ListItem för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="83575-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="83575-118">Definierar det villkor som måste finnas för att listobjektet ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="83575-118">Defines the condition that must exist for this list item to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="83575-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="83575-119">Text Value</span></span>

<span data-ttu-id="83575-120">Ange det skript som utvärderas.</span><span class="sxs-lookup"><span data-stu-id="83575-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="83575-121">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="83575-121">Remarks</span></span>

<span data-ttu-id="83575-122">Om det här elementet används kan du inte ange `PropertyName`-elementet när du definierar urvals villkoret.</span><span class="sxs-lookup"><span data-stu-id="83575-122">If this element is used, you cannot specify the `PropertyName` element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="83575-123">Se även</span><span class="sxs-lookup"><span data-stu-id="83575-123">See Also</span></span>

[<span data-ttu-id="83575-124">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="83575-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
