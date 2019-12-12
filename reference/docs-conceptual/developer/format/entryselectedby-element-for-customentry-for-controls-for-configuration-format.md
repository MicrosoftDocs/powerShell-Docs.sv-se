---
title: EntrySelectedBy-element för CustomEntry för kontroll av konfiguration (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30abae8f-c7f7-479d-ad85-19e07ddef204
caps.latest.revision: 10
ms.openlocfilehash: 81eca4f66f0057074612f2d60482b45adc36357b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359005"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-configuration-format"></a><span data-ttu-id="e6177-102">EntrySelectedBy-element för CustomEntry för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="e6177-102">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>

<span data-ttu-id="e6177-103">Definierar de .NET-typer som använder definitionen av den gemensamma kontrollen eller villkoret som måste finnas för att den här kontrollen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="e6177-103">Defines the .NET types that use the definition of the common control or the condition that must exist for this control to be used.</span></span> <span data-ttu-id="e6177-104">Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.</span><span class="sxs-lookup"><span data-stu-id="e6177-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="e6177-105">Konfigurations element (format) styr element i konfigurations-(format) kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för konfiguration ( Format) CustomEntry-element för CustomControl for Controls for Configuration (format) EntrySelectedBy-element för CustomEntry för kontroll av konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="e6177-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e6177-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="e6177-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e6177-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="e6177-107">Attributes and Elements</span></span>

<span data-ttu-id="e6177-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `EntrySelectedBy`-elementet.</span><span class="sxs-lookup"><span data-stu-id="e6177-108">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e6177-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="e6177-109">Attributes</span></span>

<span data-ttu-id="e6177-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="e6177-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e6177-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="e6177-111">Child Elements</span></span>

|<span data-ttu-id="e6177-112">Element</span><span class="sxs-lookup"><span data-stu-id="e6177-112">Element</span></span>|<span data-ttu-id="e6177-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e6177-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e6177-114">SelectionCondition-element för EntrySelectedBy för kontroller för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="e6177-114">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="e6177-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="e6177-115">Optional element.</span></span><br /><br /> <span data-ttu-id="e6177-116">Definierar det villkor som måste finnas för att den gemensamma kontroll definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="e6177-116">Defines the condition that must exist for the common control definition to be used.</span></span>|
|[<span data-ttu-id="e6177-117">SelectionSetName-element för EntrySelectedBy för kontroller för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="e6177-117">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="e6177-118">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="e6177-118">Optional element.</span></span><br /><br /> <span data-ttu-id="e6177-119">Anger en uppsättning av .NET-typer som använder den här definitionen av den gemensamma kontrollen.</span><span class="sxs-lookup"><span data-stu-id="e6177-119">Specifies a set of .NET types that use this definition of the common control.</span></span>|
|[<span data-ttu-id="e6177-120">Elementet TypeName för EntrySelectedBy för kontroller för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="e6177-120">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="e6177-121">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="e6177-121">Optional element.</span></span><br /><br /> <span data-ttu-id="e6177-122">Anger en .NET-typ som använder den här definitionen av den gemensamma kontrollen.</span><span class="sxs-lookup"><span data-stu-id="e6177-122">Specifies a .NET type that uses this definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e6177-123">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="e6177-123">Parent Elements</span></span>

|<span data-ttu-id="e6177-124">Element</span><span class="sxs-lookup"><span data-stu-id="e6177-124">Element</span></span>|<span data-ttu-id="e6177-125">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e6177-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e6177-126">CustomEntry-element för CustomControl för kontroller för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="e6177-126">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="e6177-127">Ger en definition av den gemensamma kontrollen.</span><span class="sxs-lookup"><span data-stu-id="e6177-127">Provides a definition of the common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e6177-128">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="e6177-128">Remarks</span></span>

<span data-ttu-id="e6177-129">Varje definition måste minst ha minst en .NET-typ, markerings uppsättning eller ett urvals villkor angivet.</span><span class="sxs-lookup"><span data-stu-id="e6177-129">At a minimum, each definition must have at least one .NET type, selection set, or selection condition specified.</span></span> <span data-ttu-id="e6177-130">Det finns ingen övre gräns för antalet typer, markerings uppsättningar eller markerings villkor som du kan ange.</span><span class="sxs-lookup"><span data-stu-id="e6177-130">There is no maximum limit to the number of types, selection sets, or selection conditions that you can specify.</span></span>

## <a name="see-also"></a><span data-ttu-id="e6177-131">Se även</span><span class="sxs-lookup"><span data-stu-id="e6177-131">See Also</span></span>

[<span data-ttu-id="e6177-132">SelectionCondition-element för EntrySelectedBy för kontroller för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="e6177-132">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="e6177-133">SelectionSetName-element för EntrySelectedBy för kontroller för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="e6177-133">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="e6177-134">CustomEntry-element för CustomControl för kontroller för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="e6177-134">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="e6177-135">Elementet TypeName för EntrySelectedBy för kontroller för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="e6177-135">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="e6177-136">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="e6177-136">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
