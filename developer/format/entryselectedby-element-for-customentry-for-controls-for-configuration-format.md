---
title: EntrySelectedBy Element för CustomEntry för kontroller för konfiguration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30abae8f-c7f7-479d-ad85-19e07ddef204
caps.latest.revision: 10
ms.openlocfilehash: e930e4422afd203feda6a389655ff8a355e3bec0
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848680"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-configuration-format"></a><span data-ttu-id="0c796-102">EntrySelectedBy-element för CustomEntry för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="0c796-102">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>

<span data-ttu-id="0c796-103">Definierar vilka typer av .NET som använder definitionen av den vanliga kontrollen eller villkor som måste finnas för den här kontrollen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="0c796-103">Defines the .NET types that use the definition of the common control or the condition that must exist for this control to be used.</span></span> <span data-ttu-id="0c796-104">Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.</span><span class="sxs-lookup"><span data-stu-id="0c796-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="0c796-105">Konfigurationselementet Element (Format) kontroller av (Format) kontroll konfigurationselement för kontroller för (Format) anpassad kontroll konfigurationselement för kontroll för (Format) CustomEntries konfigurationselement för anpassad kontroll för konfiguration ( Format) CustomEntry Element för anpassad kontroll för kontroller för (Format) EntrySelectedBy konfigurationselement för CustomEntry för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="0c796-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0c796-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="0c796-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0c796-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="0c796-107">Attributes and Elements</span></span>

<span data-ttu-id="0c796-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `EntrySelectedBy` element.</span><span class="sxs-lookup"><span data-stu-id="0c796-108">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0c796-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="0c796-109">Attributes</span></span>

<span data-ttu-id="0c796-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="0c796-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0c796-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="0c796-111">Child Elements</span></span>

|<span data-ttu-id="0c796-112">Element</span><span class="sxs-lookup"><span data-stu-id="0c796-112">Element</span></span>|<span data-ttu-id="0c796-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0c796-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0c796-114">SelectionCondition Element för EntrySelectedBy för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="0c796-114">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="0c796-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="0c796-115">Optional element.</span></span><br /><br /> <span data-ttu-id="0c796-116">Definierar de villkor som måste finnas för de gemensamma definitionerna för kontrollen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="0c796-116">Defines the condition that must exist for the common control definition to be used.</span></span>|
|[<span data-ttu-id="0c796-117">SelectionSetName Element för EntrySelectedBy för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="0c796-117">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="0c796-118">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="0c796-118">Optional element.</span></span><br /><br /> <span data-ttu-id="0c796-119">Anger en uppsättning med .NET-typer som använder den här definitionen för vanliga kontrollen.</span><span class="sxs-lookup"><span data-stu-id="0c796-119">Specifies a set of .NET types that use this definition of the common control.</span></span>|
|[<span data-ttu-id="0c796-120">TypeName-Element för EntrySelectedBy för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="0c796-120">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="0c796-121">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="0c796-121">Optional element.</span></span><br /><br /> <span data-ttu-id="0c796-122">Anger ett .NET-typ som använder den här definitionen för vanliga kontrollen.</span><span class="sxs-lookup"><span data-stu-id="0c796-122">Specifies a .NET type that uses this definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0c796-123">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="0c796-123">Parent Elements</span></span>

|<span data-ttu-id="0c796-124">Element</span><span class="sxs-lookup"><span data-stu-id="0c796-124">Element</span></span>|<span data-ttu-id="0c796-125">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0c796-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0c796-126">CustomEntry Element för anpassad kontroll för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="0c796-126">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="0c796-127">Innehåller en definition av vanliga kontrollen.</span><span class="sxs-lookup"><span data-stu-id="0c796-127">Provides a definition of the common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0c796-128">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="0c796-128">Remarks</span></span>

<span data-ttu-id="0c796-129">Varje definition måste minst ha minst en .NET-typ, val av set eller val av villkoret.</span><span class="sxs-lookup"><span data-stu-id="0c796-129">At a minimum, each definition must have at least one .NET type, selection set, or selection condition specified.</span></span> <span data-ttu-id="0c796-130">Det finns ingen högsta gräns för hur många typer, val av uppsättningar eller val av villkor som du kan ange.</span><span class="sxs-lookup"><span data-stu-id="0c796-130">There is no maximum limit to the number of types, selection sets, or selection conditions that you can specify.</span></span>

## <a name="see-also"></a><span data-ttu-id="0c796-131">Se även</span><span class="sxs-lookup"><span data-stu-id="0c796-131">See Also</span></span>

[<span data-ttu-id="0c796-132">SelectionCondition Element för EntrySelectedBy för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="0c796-132">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="0c796-133">SelectionSetName Element för EntrySelectedBy för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="0c796-133">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="0c796-134">CustomEntry Element för anpassad kontroll för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="0c796-134">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="0c796-135">TypeName-Element för EntrySelectdBy för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="0c796-135">TypeName Element for EntrySelectdBy for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="0c796-136">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="0c796-136">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
