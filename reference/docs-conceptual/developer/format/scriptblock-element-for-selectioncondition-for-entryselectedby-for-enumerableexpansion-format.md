---
title: Script block-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4126b799-c43d-4175-8513-6d761c65437e
caps.latest.revision: 9
ms.openlocfilehash: a51d8d22fa8b0c7f303a5e8f37edcc5e57724063
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72358938"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="9d498-102">ScriptBlock-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="9d498-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="9d498-103">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="9d498-103">Specifies the script that triggers the condition.</span></span>

<span data-ttu-id="9d498-104">Konfigurations element (format) DefaultSettings-element (format) EnumerableExpansions-element (format) EnumerableExpansion-element (format) EntrySelectedBy-element för EnumerableExpansion (format) SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format) script block-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="9d498-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9d498-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="9d498-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9d498-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="9d498-106">Attributes and Elements</span></span>

<span data-ttu-id="9d498-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `ScriptBlock`-elementet.</span><span class="sxs-lookup"><span data-stu-id="9d498-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9d498-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="9d498-108">Attributes</span></span>

<span data-ttu-id="9d498-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="9d498-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9d498-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="9d498-110">Child Elements</span></span>

<span data-ttu-id="9d498-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="9d498-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9d498-112">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="9d498-112">Parent Elements</span></span>

|<span data-ttu-id="9d498-113">Element</span><span class="sxs-lookup"><span data-stu-id="9d498-113">Element</span></span>|<span data-ttu-id="9d498-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="9d498-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9d498-115">SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="9d498-115">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="9d498-116">Definierar det villkor som måste finnas för att expandera samlings objekt i den här definitionen.</span><span class="sxs-lookup"><span data-stu-id="9d498-116">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9d498-117">Textvärde</span><span class="sxs-lookup"><span data-stu-id="9d498-117">Text Value</span></span>

<span data-ttu-id="9d498-118">Ange det skript som utvärderas.</span><span class="sxs-lookup"><span data-stu-id="9d498-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="9d498-119">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="9d498-119">Remarks</span></span>

<span data-ttu-id="9d498-120">Urvals villkoret måste innehålla minst ett skript eller egenskaps namn som ska utvärderas, men det går inte att ange båda.</span><span class="sxs-lookup"><span data-stu-id="9d498-120">The selection condition must specify at least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="9d498-121">Mer information om hur du använder urvals villkor finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="9d498-121">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9d498-122">Se även</span><span class="sxs-lookup"><span data-stu-id="9d498-122">See Also</span></span>

[<span data-ttu-id="9d498-123">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="9d498-123">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="9d498-124">PropertyName-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="9d498-124">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="9d498-125">SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="9d498-125">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="9d498-126">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="9d498-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
