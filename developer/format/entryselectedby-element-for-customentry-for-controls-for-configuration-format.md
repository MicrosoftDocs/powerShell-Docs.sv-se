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
ms.openlocfilehash: 81eca4f66f0057074612f2d60482b45adc36357b
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059226"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-configuration-format"></a><span data-ttu-id="443ba-102">EntrySelectedBy-element för CustomEntry för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="443ba-102">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>

<span data-ttu-id="443ba-103">Definierar vilka typer av .NET som använder definitionen av den vanliga kontrollen eller villkor som måste finnas för den här kontrollen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="443ba-103">Defines the .NET types that use the definition of the common control or the condition that must exist for this control to be used.</span></span> <span data-ttu-id="443ba-104">Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.</span><span class="sxs-lookup"><span data-stu-id="443ba-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="443ba-105">Konfigurationselementet Element (Format) kontroller av (Format) kontroll konfigurationselement för kontroller för (Format) anpassad kontroll konfigurationselement för kontroll för (Format) CustomEntries konfigurationselement för anpassad kontroll för konfiguration ( Format) CustomEntry Element för anpassad kontroll för kontroller för (Format) EntrySelectedBy konfigurationselement för CustomEntry för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="443ba-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="443ba-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="443ba-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="443ba-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="443ba-107">Attributes and Elements</span></span>

<span data-ttu-id="443ba-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `EntrySelectedBy` element.</span><span class="sxs-lookup"><span data-stu-id="443ba-108">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="443ba-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="443ba-109">Attributes</span></span>

<span data-ttu-id="443ba-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="443ba-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="443ba-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="443ba-111">Child Elements</span></span>

|<span data-ttu-id="443ba-112">Element</span><span class="sxs-lookup"><span data-stu-id="443ba-112">Element</span></span>|<span data-ttu-id="443ba-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="443ba-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="443ba-114">SelectionCondition Element för EntrySelectedBy för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="443ba-114">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="443ba-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="443ba-115">Optional element.</span></span><br /><br /> <span data-ttu-id="443ba-116">Definierar de villkor som måste finnas för de gemensamma definitionerna för kontrollen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="443ba-116">Defines the condition that must exist for the common control definition to be used.</span></span>|
|[<span data-ttu-id="443ba-117">SelectionSetName Element för EntrySelectedBy för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="443ba-117">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="443ba-118">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="443ba-118">Optional element.</span></span><br /><br /> <span data-ttu-id="443ba-119">Anger en uppsättning med .NET-typer som använder den här definitionen för vanliga kontrollen.</span><span class="sxs-lookup"><span data-stu-id="443ba-119">Specifies a set of .NET types that use this definition of the common control.</span></span>|
|[<span data-ttu-id="443ba-120">TypeName-Element för EntrySelectedBy för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="443ba-120">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="443ba-121">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="443ba-121">Optional element.</span></span><br /><br /> <span data-ttu-id="443ba-122">Anger ett .NET-typ som använder den här definitionen för vanliga kontrollen.</span><span class="sxs-lookup"><span data-stu-id="443ba-122">Specifies a .NET type that uses this definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="443ba-123">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="443ba-123">Parent Elements</span></span>

|<span data-ttu-id="443ba-124">Element</span><span class="sxs-lookup"><span data-stu-id="443ba-124">Element</span></span>|<span data-ttu-id="443ba-125">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="443ba-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="443ba-126">CustomEntry Element för anpassad kontroll för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="443ba-126">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="443ba-127">Innehåller en definition av vanliga kontrollen.</span><span class="sxs-lookup"><span data-stu-id="443ba-127">Provides a definition of the common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="443ba-128">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="443ba-128">Remarks</span></span>

<span data-ttu-id="443ba-129">Varje definition måste minst ha minst en .NET-typ, val av set eller val av villkoret.</span><span class="sxs-lookup"><span data-stu-id="443ba-129">At a minimum, each definition must have at least one .NET type, selection set, or selection condition specified.</span></span> <span data-ttu-id="443ba-130">Det finns ingen högsta gräns för hur många typer, val av uppsättningar eller val av villkor som du kan ange.</span><span class="sxs-lookup"><span data-stu-id="443ba-130">There is no maximum limit to the number of types, selection sets, or selection conditions that you can specify.</span></span>

## <a name="see-also"></a><span data-ttu-id="443ba-131">Se även</span><span class="sxs-lookup"><span data-stu-id="443ba-131">See Also</span></span>

[<span data-ttu-id="443ba-132">SelectionCondition Element för EntrySelectedBy för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="443ba-132">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="443ba-133">SelectionSetName Element för EntrySelectedBy för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="443ba-133">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="443ba-134">CustomEntry Element för anpassad kontroll för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="443ba-134">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="443ba-135">TypeName-Element för EntrySelectedBy för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="443ba-135">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="443ba-136">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="443ba-136">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
