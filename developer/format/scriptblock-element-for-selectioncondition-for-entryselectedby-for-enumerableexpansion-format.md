---
title: ScriptBlock Element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4126b799-c43d-4175-8513-6d761c65437e
caps.latest.revision: 9
ms.openlocfilehash: a51d8d22fa8b0c7f303a5e8f37edcc5e57724063
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064381"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="f8a4b-102">ScriptBlock-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="f8a4b-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="f8a4b-103">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="f8a4b-103">Specifies the script that triggers the condition.</span></span>

<span data-ttu-id="f8a4b-104">Elementet (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy konfigurationselement för EnumerableExpansion (Format) SelectionCondition elementet för EntrySelectedBy för EnumerableExpansion (Format) ScriptBlock Element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="f8a4b-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f8a4b-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="f8a4b-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f8a4b-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="f8a4b-106">Attributes and Elements</span></span>

<span data-ttu-id="f8a4b-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `ScriptBlock` element.</span><span class="sxs-lookup"><span data-stu-id="f8a4b-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f8a4b-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="f8a4b-108">Attributes</span></span>

<span data-ttu-id="f8a4b-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="f8a4b-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f8a4b-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="f8a4b-110">Child Elements</span></span>

<span data-ttu-id="f8a4b-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="f8a4b-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f8a4b-112">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="f8a4b-112">Parent Elements</span></span>

|<span data-ttu-id="f8a4b-113">Element</span><span class="sxs-lookup"><span data-stu-id="f8a4b-113">Element</span></span>|<span data-ttu-id="f8a4b-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f8a4b-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f8a4b-115">SelectionCondition Element för EntrySelectedBy för EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="f8a4b-115">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="f8a4b-116">Definierar de villkor som måste finnas för att expandera samlingen objekt av den här definitionen.</span><span class="sxs-lookup"><span data-stu-id="f8a4b-116">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f8a4b-117">Textvärde</span><span class="sxs-lookup"><span data-stu-id="f8a4b-117">Text Value</span></span>

<span data-ttu-id="f8a4b-118">Ange det skript som ska utvärderas.</span><span class="sxs-lookup"><span data-stu-id="f8a4b-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="f8a4b-119">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="f8a4b-119">Remarks</span></span>

<span data-ttu-id="f8a4b-120">Urvalsvillkoret måste ange minst ett skript eller egenskapen namn för att utvärdera, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="f8a4b-120">The selection condition must specify at least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="f8a4b-121">Läs mer om hur du använder villkor för val av [definiera villkor för när Data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="f8a4b-121">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f8a4b-122">Se även</span><span class="sxs-lookup"><span data-stu-id="f8a4b-122">See Also</span></span>

[<span data-ttu-id="f8a4b-123">Definiera villkor för när Data visas</span><span class="sxs-lookup"><span data-stu-id="f8a4b-123">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="f8a4b-124">PropertyName-Element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="f8a4b-124">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="f8a4b-125">SelectionCondition Element för EntrySelectedBy för EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="f8a4b-125">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="f8a4b-126">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="f8a4b-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
