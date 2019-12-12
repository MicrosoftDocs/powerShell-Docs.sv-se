---
title: SelectionCondition-element för EntrySelectedBy för kontroll av konfiguration (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f23ef405-0f1e-4607-b3f4-4017b7ead106
caps.latest.revision: 7
ms.openlocfilehash: a5098da55d0a63272a121b973cb05e26dc47e3e1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72358900"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="49d59-102">SelectionCondition-element för EntrySelectedBy för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="49d59-102">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="49d59-103">Definierar ett villkor som måste finnas för att en gemensam kontroll definition ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="49d59-103">Defines a condition that must exist for a common control definition to be used.</span></span> <span data-ttu-id="49d59-104">Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.</span><span class="sxs-lookup"><span data-stu-id="49d59-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="49d59-105">Konfigurations element (format) styr element i konfigurations-(format)-kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för kontroller för Konfiguration (format) CustomEntry-element för CustomControl for Controls for Configuration (format) EntrySelectedBy-element för CustomEntry for Controls for Configuration (format) SelectionCondition-element för EntrySelectedBy för CustomEntry för Konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="49d59-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="49d59-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="49d59-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="49d59-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="49d59-107">Attributes and Elements</span></span>

<span data-ttu-id="49d59-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `SelectionCondition`-elementet.</span><span class="sxs-lookup"><span data-stu-id="49d59-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="49d59-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="49d59-109">Attributes</span></span>

<span data-ttu-id="49d59-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="49d59-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="49d59-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="49d59-111">Child Elements</span></span>

|<span data-ttu-id="49d59-112">Element</span><span class="sxs-lookup"><span data-stu-id="49d59-112">Element</span></span>|<span data-ttu-id="49d59-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="49d59-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="49d59-114">PropertyName-element för SelectionCondition för kontroll av konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="49d59-114">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="49d59-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="49d59-115">Optional element.</span></span><br /><br /> <span data-ttu-id="49d59-116">Anger en .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="49d59-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="49d59-117">Script block-element för SelectionCondition för kontroller för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="49d59-117">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="49d59-118">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="49d59-118">Optional element.</span></span><br /><br /> <span data-ttu-id="49d59-119">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="49d59-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="49d59-120">SelectionSetName-element för SelectionCondition för kontroller för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="49d59-120">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="49d59-121">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="49d59-121">Optional element.</span></span><br /><br /> <span data-ttu-id="49d59-122">Anger den uppsättning av .NET-typer som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="49d59-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="49d59-123">Elementet TypeName för SelectionCondition för kontroller för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="49d59-123">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="49d59-124">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="49d59-124">Optional element.</span></span><br /><br /> <span data-ttu-id="49d59-125">Anger en .NET-typ som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="49d59-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="49d59-126">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="49d59-126">Parent Elements</span></span>

|<span data-ttu-id="49d59-127">Element</span><span class="sxs-lookup"><span data-stu-id="49d59-127">Element</span></span>|<span data-ttu-id="49d59-128">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="49d59-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="49d59-129">EntrySelectedBy-element för CustomEntry för kontroller för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="49d59-129">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="49d59-130">Definierar de .NET-typer som använder den här posten i common Control definition.</span><span class="sxs-lookup"><span data-stu-id="49d59-130">Defines the .NET types that use this entry of the common control definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="49d59-131">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="49d59-131">Remarks</span></span>

<span data-ttu-id="49d59-132">Följande rikt linjer måste följas när du definierar ett urvals villkor:</span><span class="sxs-lookup"><span data-stu-id="49d59-132">The following guidelines must be followed when defining a selection condition:</span></span>

- <span data-ttu-id="49d59-133">Markerings villkoret måste ange minst ett egenskaps namn eller ett skript block, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="49d59-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="49d59-134">Urvals villkoret kan ange valfritt antal .NET-typer eller markerings uppsättningar, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="49d59-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="49d59-135">Mer information om hur urvals villkor kan användas finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="49d59-135">For more information about how selection conditions can be used, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="49d59-136">Se även</span><span class="sxs-lookup"><span data-stu-id="49d59-136">See Also</span></span>

[<span data-ttu-id="49d59-137">PropertyName-element för SelectionCondition för kontroll av konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="49d59-137">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="49d59-138">Script block-element för SelectionCondition för kontroller för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="49d59-138">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="49d59-139">SelectionSetName-element för SelectionCondition för kontroller för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="49d59-139">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="49d59-140">Elementet TypeName för SelectionCondition för kontroller för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="49d59-140">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="49d59-141">EntrySelectedBy-element för CustomEntry för kontroller för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="49d59-141">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="49d59-142">Skriva en Windows PowerShell-formatering och en typ fil</span><span class="sxs-lookup"><span data-stu-id="49d59-142">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
