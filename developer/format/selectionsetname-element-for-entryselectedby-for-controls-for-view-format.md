---
title: SelectionSetName Element för EntrySelectedBy för kontroller för att visa (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b594a064-746f-4900-99e4-7be7bf5aa5a2
caps.latest.revision: 7
ms.openlocfilehash: d540c99707f4e0796b2d408f2161a9208257ab32
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075655"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-view-format"></a><span data-ttu-id="e89e7-102">SelectionSetName-element för EntrySelectedBy för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="e89e7-102">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>

<span data-ttu-id="e89e7-103">Anger en uppsättning med .NET-typer som använder den här definitionen för kontrollen.</span><span class="sxs-lookup"><span data-stu-id="e89e7-103">Specifies a set of .NET types that use this definition of the control.</span></span> <span data-ttu-id="e89e7-104">Det här elementet används när du definierar kontroller som kan användas av en vy.</span><span class="sxs-lookup"><span data-stu-id="e89e7-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="e89e7-105">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) kontroller Element (Format) kontroll konfigurationselement för kontroller för att visa (Format) anpassad kontroll Element för kontroll för kontroller för att visa (Format) CustomEntries Element för Anpassad kontroll för kontroller för att visa (Format) CustomEntry Element för CustomEntries för kontroller för att visa (Format) EntrySelectedBy Element för CustomEntry för kontroller för att visa (Format) SelectionSetName Element för EntrySelectedBy för kontroller för att visa ( Format)</span><span class="sxs-lookup"><span data-stu-id="e89e7-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e89e7-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="e89e7-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="e89e7-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="e89e7-107">Attributes and Elements</span></span>

<span data-ttu-id="e89e7-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `SelectionSetName` element.</span><span class="sxs-lookup"><span data-stu-id="e89e7-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e89e7-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="e89e7-109">Attributes</span></span>

<span data-ttu-id="e89e7-110">Inga</span><span class="sxs-lookup"><span data-stu-id="e89e7-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="e89e7-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="e89e7-111">Child Elements</span></span>

<span data-ttu-id="e89e7-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="e89e7-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e89e7-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="e89e7-113">Parent Elements</span></span>

|<span data-ttu-id="e89e7-114">Element</span><span class="sxs-lookup"><span data-stu-id="e89e7-114">Element</span></span>|<span data-ttu-id="e89e7-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e89e7-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e89e7-116">EntrySelectedBy Element för CustomEntry för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="e89e7-116">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="e89e7-117">Definierar vilka typer av .NET som använder den här kontrollen definitionen eller villkor som måste finnas för den här definitionen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="e89e7-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e89e7-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="e89e7-118">Text Value</span></span>

<span data-ttu-id="e89e7-119">Ange namnet på val av uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="e89e7-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="e89e7-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="e89e7-120">Remarks</span></span>

<span data-ttu-id="e89e7-121">Varje kontrolldefinition måste ha minst ett namn, val av set eller Urvalsvillkoret som definierats.</span><span class="sxs-lookup"><span data-stu-id="e89e7-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="e89e7-122">Inställningarna används vanligtvis när du vill definiera en grupp med objekt som används i flera vyer.</span><span class="sxs-lookup"><span data-stu-id="e89e7-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="e89e7-123">Mer information om hur du definierar inställningarna finns i [definiera val av anger](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="e89e7-123">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e89e7-124">Se även</span><span class="sxs-lookup"><span data-stu-id="e89e7-124">See Also</span></span>

[<span data-ttu-id="e89e7-125">EntrySelectedBy Element för CustomEntry för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="e89e7-125">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="e89e7-126">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="e89e7-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
