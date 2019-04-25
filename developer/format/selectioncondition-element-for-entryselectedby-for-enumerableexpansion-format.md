---
title: SelectionCondition Element för EntrySelectedBy för EnumerableExpansion (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c012115-9241-4851-9015-841eb508faf3
caps.latest.revision: 10
ms.openlocfilehash: d6adf2fa62384d671fd6a07dd185a941daa44cec
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064143"
---
# <a name="selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="1c982-102">SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="1c982-102">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="1c982-103">Definierar de villkor som måste finnas för att expandera samlingen objekt av den här definitionen.</span><span class="sxs-lookup"><span data-stu-id="1c982-103">Defines the condition that must exist to expand the collection objects of this definition.</span></span>

<span data-ttu-id="1c982-104">Elementet (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy konfigurationselement för EnumerableExpansion (Format) SelectionCondition elementet för EntrySelectedBy för EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="1c982-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1c982-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="1c982-105">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1c982-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="1c982-106">Attributes and Elements</span></span>

<span data-ttu-id="1c982-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `SelectionCondition` element.</span><span class="sxs-lookup"><span data-stu-id="1c982-107">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="1c982-108">Du måste ange en enda `PropertyName` eller `ScriptBlock` element.</span><span class="sxs-lookup"><span data-stu-id="1c982-108">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="1c982-109">Den `SelectionSetName` och `TypeName` element är valfria.</span><span class="sxs-lookup"><span data-stu-id="1c982-109">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="1c982-110">Du kan ange en av antingen element.</span><span class="sxs-lookup"><span data-stu-id="1c982-110">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1c982-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="1c982-111">Attributes</span></span>

<span data-ttu-id="1c982-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="1c982-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1c982-113">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="1c982-113">Child Elements</span></span>

|<span data-ttu-id="1c982-114">Element</span><span class="sxs-lookup"><span data-stu-id="1c982-114">Element</span></span>|<span data-ttu-id="1c982-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="1c982-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1c982-116">PropertyName-Element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="1c982-116">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="1c982-117">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="1c982-117">Optional element.</span></span><br /><br /> <span data-ttu-id="1c982-118">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="1c982-118">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="1c982-119">ScriptBlock Element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="1c982-119">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="1c982-120">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="1c982-120">Optional element.</span></span><br /><br /> <span data-ttu-id="1c982-121">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="1c982-121">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="1c982-122">SelectionSetName Element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="1c982-122">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="1c982-123">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="1c982-123">Optional element.</span></span><br /><br /> <span data-ttu-id="1c982-124">Anger den uppsättning med .NET-typer som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="1c982-124">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="1c982-125">TypeName-Element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="1c982-125">TypeName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="1c982-126">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="1c982-126">Optional element.</span></span><br /><br /> <span data-ttu-id="1c982-127">Anger ett .NET-typ som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="1c982-127">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="1c982-128">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="1c982-128">Parent Elements</span></span>

|<span data-ttu-id="1c982-129">Element</span><span class="sxs-lookup"><span data-stu-id="1c982-129">Element</span></span>|<span data-ttu-id="1c982-130">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="1c982-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1c982-131">EntrySelectedBy Element för EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="1c982-131">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="1c982-132">Definierar vilka .NET samling objekt byggs med den här definitionen.</span><span class="sxs-lookup"><span data-stu-id="1c982-132">Defines which .NET collection objects are expanded by this definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1c982-133">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="1c982-133">Remarks</span></span>

<span data-ttu-id="1c982-134">Varje definition måste ha minst ett namn, val av set eller Urvalsvillkoret som definierats.</span><span class="sxs-lookup"><span data-stu-id="1c982-134">Each definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="1c982-135">När du definierar en urvalsvillkoret, gäller följande krav:</span><span class="sxs-lookup"><span data-stu-id="1c982-135">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="1c982-136">Urvalsvillkoret måste ange ett namn med minst en egenskap eller ett skriptblock, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="1c982-136">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="1c982-137">Urvalsvillkoret kan ange valfritt antal typer i .NET eller val av anger, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="1c982-137">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="1c982-138">Läs mer om hur du använder villkor för val av [definiera villkor för Diplaying Data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="1c982-138">For more information about how to use selection conditions, see [Defining Conditions for Diplaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="1c982-139">Mer information om andra komponenter för en bred vy finns i [bred vy](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="1c982-139">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1c982-140">Se även</span><span class="sxs-lookup"><span data-stu-id="1c982-140">See Also</span></span>

[<span data-ttu-id="1c982-141">Definiera villkor för när Data visas</span><span class="sxs-lookup"><span data-stu-id="1c982-141">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="1c982-142">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="1c982-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
