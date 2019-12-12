---
title: Script block-element för SelectionCondition för EntrySelectedBy för WideControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec68309-7826-4643-a521-e29c996663fb
caps.latest.revision: 11
ms.openlocfilehash: 649a978e21e9421a3f3e953261e1d309e23c3f9c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72358910"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="15da0-102">ScriptBlock-element för SelectionCondition för EntrySelectedBy för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="15da0-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="15da0-103">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="15da0-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="15da0-104">När det här skriptet utvärderas till `true`, uppfylls villkoret och den breda post definitionen används.</span><span class="sxs-lookup"><span data-stu-id="15da0-104">When this script is evaluated to `true`, the condition is met, and the wide entry definition is used.</span></span>

<span data-ttu-id="15da0-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) WideControl-element (format) WideEntries-element (format) WideEntry element (format) EntrySelectedBy-element för WideEntry (format) SelectionCondition-element för EntrySelectedBy för WideEntry (format) script block-element för SelectionCondition för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="15da0-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="15da0-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="15da0-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="15da0-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="15da0-107">Attributes and Elements</span></span>

<span data-ttu-id="15da0-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `ScriptBlock`-elementet.</span><span class="sxs-lookup"><span data-stu-id="15da0-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="15da0-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="15da0-109">Attributes</span></span>

<span data-ttu-id="15da0-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="15da0-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="15da0-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="15da0-111">Child Elements</span></span>

<span data-ttu-id="15da0-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="15da0-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="15da0-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="15da0-113">Parent Elements</span></span>

|<span data-ttu-id="15da0-114">Element</span><span class="sxs-lookup"><span data-stu-id="15da0-114">Element</span></span>|<span data-ttu-id="15da0-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="15da0-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="15da0-116">SelectionCondition-element för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="15da0-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="15da0-117">Definierar det villkor som måste finnas för att den här definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="15da0-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="15da0-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="15da0-118">Text Value</span></span>

<span data-ttu-id="15da0-119">Ange det skript som utvärderas.</span><span class="sxs-lookup"><span data-stu-id="15da0-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="15da0-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="15da0-120">Remarks</span></span>

<span data-ttu-id="15da0-121">Urvals villkoret måste innehålla minst ett skript eller egenskaps namn som ska utvärderas, men det går inte att ange båda.</span><span class="sxs-lookup"><span data-stu-id="15da0-121">The selection condition must specify at least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="15da0-122">Mer information om hur du använder urvals villkor finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="15da0-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="15da0-123">Mer information om andra komponenter i en bred vy finns i [wide View](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="15da0-123">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="15da0-124">Se även</span><span class="sxs-lookup"><span data-stu-id="15da0-124">See Also</span></span>

[<span data-ttu-id="15da0-125">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="15da0-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="15da0-126">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="15da0-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="15da0-127">PropertyName-element för SelectionCondition för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="15da0-127">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="15da0-128">SelectionCondition-element för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="15da0-128">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="15da0-129">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="15da0-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
