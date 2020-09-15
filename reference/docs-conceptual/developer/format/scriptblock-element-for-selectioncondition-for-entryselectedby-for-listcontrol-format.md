---
title: Script block-element för SelectionCondition för EntrySelectedBy för ListControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 56bd04c9af74bdaa7a186a208fc15a67cb08b004
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772866"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="28a47-102">ScriptBlock-element för SelectionCondition för EntrySelectedBy för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="28a47-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="28a47-103">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="28a47-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="28a47-104">När det här skriptet utvärderas `true` , uppfylls villkoret och list posten används.</span><span class="sxs-lookup"><span data-stu-id="28a47-104">When this script is evaluated to `true`, the condition is met, and the list entry is used.</span></span>

<span data-ttu-id="28a47-105">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) ListControl-element (format) ListEntries-element (format) ListEntry-element (format) EntrySelectedBy-element för ListEntry (format) SelectionCondition element for EntrySelectedBy for ListEntry (format) script block-element för SelectionCondition för EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="28a47-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="28a47-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="28a47-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="28a47-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="28a47-107">Attributes and Elements</span></span>

<span data-ttu-id="28a47-108">I följande avsnitt beskrivs attribut, underordnade element och `ScriptBlock` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="28a47-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="28a47-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="28a47-109">Attributes</span></span>

<span data-ttu-id="28a47-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="28a47-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="28a47-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="28a47-111">Child Elements</span></span>

<span data-ttu-id="28a47-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="28a47-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="28a47-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="28a47-113">Parent Elements</span></span>

|<span data-ttu-id="28a47-114">Element</span><span class="sxs-lookup"><span data-stu-id="28a47-114">Element</span></span>|<span data-ttu-id="28a47-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="28a47-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="28a47-116">SelectionCondition-element för EntrySelectedBy för ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="28a47-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="28a47-117">Definierar det villkor som måste finnas för att den här List posten ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="28a47-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="28a47-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="28a47-118">Text Value</span></span>

<span data-ttu-id="28a47-119">Ange det skript som utvärderas.</span><span class="sxs-lookup"><span data-stu-id="28a47-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="28a47-120">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="28a47-120">Remarks</span></span>

<span data-ttu-id="28a47-121">Urvals villkoret måste ange minst ett skript eller egenskaps namn som ska utvärderas, men det går inte att ange båda.</span><span class="sxs-lookup"><span data-stu-id="28a47-121">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="28a47-122">(Mer information om hur urvals villkor kan användas finns i [definiera villkor för när en visnings post eller ett objekt används](./defining-conditions-for-displaying-data.md).)</span><span class="sxs-lookup"><span data-stu-id="28a47-122">(For more information about how selection conditions can be used, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).)</span></span>

<span data-ttu-id="28a47-123">Mer information om de andra komponenterna i en listvy finns i [listvyn](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="28a47-123">For more information about the other components of a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="28a47-124">Se även</span><span class="sxs-lookup"><span data-stu-id="28a47-124">See Also</span></span>

[<span data-ttu-id="28a47-125">ListEntry-element (format)</span><span class="sxs-lookup"><span data-stu-id="28a47-125">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="28a47-126">PropertyName-element för SelectionCondition för EntrySelectedBy för ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="28a47-126">PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="28a47-127">SelectionCondition-element för EntrySelectedBy för ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="28a47-127">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="28a47-128">Listvy</span><span class="sxs-lookup"><span data-stu-id="28a47-128">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="28a47-129">Definiera villkor för när en visnings post eller ett objekt används</span><span class="sxs-lookup"><span data-stu-id="28a47-129">Defining Conditions for when a View Entry or Item is Used</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="28a47-130">Skriva en Windows PowerShell-formatering och en typ fil</span><span class="sxs-lookup"><span data-stu-id="28a47-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
