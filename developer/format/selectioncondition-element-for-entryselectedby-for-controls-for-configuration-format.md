---
title: SelectionCondition Element för EntrySelectedBy för kontroller för konfiguration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f23ef405-0f1e-4607-b3f4-4017b7ead106
caps.latest.revision: 7
ms.openlocfilehash: a5098da55d0a63272a121b973cb05e26dc47e3e1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845516"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="e05ce-102">SelectionCondition-element för EntrySelectedBy för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="e05ce-102">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="e05ce-103">Definierar ett villkor som måste finnas för en gemensam kontrolldefinition som ska användas.</span><span class="sxs-lookup"><span data-stu-id="e05ce-103">Defines a condition that must exist for a common control definition to be used.</span></span> <span data-ttu-id="e05ce-104">Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.</span><span class="sxs-lookup"><span data-stu-id="e05ce-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="e05ce-105">Konfigurationselementet Element (Format) kontroller av (Format) kontroll konfigurationselement för kontroller för (Format) anpassad kontroll konfigurationselement för kontroll för (Format) CustomEntries konfigurationselement för anpassad kontroll för kontroller för (Format) CustomEntry konfigurationselement för anpassad kontroll för kontroller för (Format) EntrySelectedBy konfigurationselement för CustomEntry för kontroller för (Format) SelectionCondition konfigurationselement för EntrySelectedBy för CustomEntry för Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="e05ce-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e05ce-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="e05ce-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e05ce-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="e05ce-107">Attributes and Elements</span></span>

<span data-ttu-id="e05ce-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `SelectionCondition` element.</span><span class="sxs-lookup"><span data-stu-id="e05ce-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e05ce-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="e05ce-109">Attributes</span></span>

<span data-ttu-id="e05ce-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="e05ce-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e05ce-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="e05ce-111">Child Elements</span></span>

|<span data-ttu-id="e05ce-112">Element</span><span class="sxs-lookup"><span data-stu-id="e05ce-112">Element</span></span>|<span data-ttu-id="e05ce-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e05ce-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e05ce-114">PropertyName-Element för SelectionCondition för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="e05ce-114">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="e05ce-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="e05ce-115">Optional element.</span></span><br /><br /> <span data-ttu-id="e05ce-116">Anger en .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="e05ce-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="e05ce-117">ScriptBlock Element för SelectionCondition för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="e05ce-117">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="e05ce-118">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="e05ce-118">Optional element.</span></span><br /><br /> <span data-ttu-id="e05ce-119">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="e05ce-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="e05ce-120">SelectionSetName Element för SelectionCondition för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="e05ce-120">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="e05ce-121">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="e05ce-121">Optional element.</span></span><br /><br /> <span data-ttu-id="e05ce-122">Anger den uppsättning med .NET-typer som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="e05ce-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="e05ce-123">TypeName-Element för SelectionCondition för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="e05ce-123">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="e05ce-124">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="e05ce-124">Optional element.</span></span><br /><br /> <span data-ttu-id="e05ce-125">Anger ett .NET-typ som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="e05ce-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e05ce-126">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="e05ce-126">Parent Elements</span></span>

|<span data-ttu-id="e05ce-127">Element</span><span class="sxs-lookup"><span data-stu-id="e05ce-127">Element</span></span>|<span data-ttu-id="e05ce-128">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e05ce-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e05ce-129">EntrySelectedBy Element för CustomEntry för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="e05ce-129">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="e05ce-130">Definierar vilka typer av .NET som använder den här posten gemensam kontroll definition.</span><span class="sxs-lookup"><span data-stu-id="e05ce-130">Defines the .NET types that use this entry of the common control definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e05ce-131">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="e05ce-131">Remarks</span></span>

<span data-ttu-id="e05ce-132">Måste följa följande riktlinjer när du definierar ett val av villkor:</span><span class="sxs-lookup"><span data-stu-id="e05ce-132">The following guidelines must be followed when defining a selection condition:</span></span>

- <span data-ttu-id="e05ce-133">Urvalsvillkoret måste ange ett namn med minst en egenskap eller ett skriptblock, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="e05ce-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="e05ce-134">Urvalsvillkoret kan ange valfritt antal typer i .NET eller val av anger, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="e05ce-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="e05ce-135">Läs mer om hur du kan använda villkor för val av [definiera villkor för när Data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="e05ce-135">For more information about how selection conditions can be used, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e05ce-136">Se även</span><span class="sxs-lookup"><span data-stu-id="e05ce-136">See Also</span></span>

[<span data-ttu-id="e05ce-137">PropertyName-Element för SelectionCondition för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="e05ce-137">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="e05ce-138">ScriptBlock Element för SelectionCondition för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="e05ce-138">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="e05ce-139">SelectionSetName Element för SelectionCondition för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="e05ce-139">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="e05ce-140">TypeName-Element för SelectionCondition för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="e05ce-140">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="e05ce-141">EntrySelectedBy Element för CustomEntry för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="e05ce-141">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="e05ce-142">Skriva ett Windows PowerShell formatering och skriver fil</span><span class="sxs-lookup"><span data-stu-id="e05ce-142">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
