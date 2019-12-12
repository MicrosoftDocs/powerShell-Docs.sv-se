---
title: PropertyName-element för SelectionCondition för EntrySelectedBy för ListControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71c3f1f6-6fe2-42f1-8260-6974d3871748
caps.latest.revision: 11
ms.openlocfilehash: 7d526372cf80327b3fb9b79b6e83429c57780183
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354028"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="f5e9d-102">PropertyName-element för SelectionCondition för EntrySelectedBy för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="f5e9d-102">PropertyName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="f5e9d-103">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="f5e9d-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="f5e9d-104">När den här egenskapen finns eller när den utvärderas till `true`, uppfylls villkoret och list posten används.</span><span class="sxs-lookup"><span data-stu-id="f5e9d-104">When this property is present or when it evaluates to `true`, the condition is met, and the list entry is used.</span></span>

<span data-ttu-id="f5e9d-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) ListControl-element (format) ListEntries-element (format) ListEntry element (format) EntrySelectedBy-element för ListEntry (format) SelectionCondition-element för EntrySelectedBy för ListEntry (format) PropertyName-element för SelectionCondition för EntrySelectedBy för ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="f5e9d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f5e9d-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="f5e9d-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f5e9d-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="f5e9d-107">Attributes and Elements</span></span>

<span data-ttu-id="f5e9d-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `PropertyName`-elementet.</span><span class="sxs-lookup"><span data-stu-id="f5e9d-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f5e9d-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="f5e9d-109">Attributes</span></span>

<span data-ttu-id="f5e9d-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="f5e9d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f5e9d-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="f5e9d-111">Child Elements</span></span>

<span data-ttu-id="f5e9d-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="f5e9d-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f5e9d-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="f5e9d-113">Parent Elements</span></span>

|<span data-ttu-id="f5e9d-114">Element</span><span class="sxs-lookup"><span data-stu-id="f5e9d-114">Element</span></span>|<span data-ttu-id="f5e9d-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f5e9d-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f5e9d-116">SelectionCondition-element för EntrySelectedBy för ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="f5e9d-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="f5e9d-117">Definierar det villkor som måste finnas för att den här List posten ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="f5e9d-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f5e9d-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="f5e9d-118">Text Value</span></span>

<span data-ttu-id="f5e9d-119">Ange .NET-egenskaps namnet.</span><span class="sxs-lookup"><span data-stu-id="f5e9d-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="f5e9d-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="f5e9d-120">Remarks</span></span>

<span data-ttu-id="f5e9d-121">Urvals villkoret måste innehålla minst ett egenskaps namn eller ett skript block, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="f5e9d-121">The selection condition must specify at least one property name or a script block, but cannot specify both.</span></span> <span data-ttu-id="f5e9d-122">Mer information om hur du använder urvals villkor finns i [definiera villkor för när en visnings post eller ett objekt används](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="f5e9d-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="f5e9d-123">Mer information om andra komponenter i en listvy finns i [skapa listvyn](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="f5e9d-123">For more information about other components of a list view, see [Creating List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f5e9d-124">Se även</span><span class="sxs-lookup"><span data-stu-id="f5e9d-124">See Also</span></span>

[<span data-ttu-id="f5e9d-125">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="f5e9d-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="f5e9d-126">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="f5e9d-126">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="f5e9d-127">ListEntry-element (format)</span><span class="sxs-lookup"><span data-stu-id="f5e9d-127">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="f5e9d-128">Script block-element för SelectionCondition för EntrySelectedBy för ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="f5e9d-128">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="f5e9d-129">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="f5e9d-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
