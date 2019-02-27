---
title: SelectionSetName Element för EntrySelectedBy för kontroller för konfiguration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 42143d1e-7cda-4c4a-b568-fa1951bb9417
caps.latest.revision: 6
ms.openlocfilehash: 9060ee54d6f88c7f910b16cf5c9b87f37844b736
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850248"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="7a659-102">SelectionSetName-element för EntrySelectedBy för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="7a659-102">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="7a659-103">Anger en uppsättning med .NET-typer som använder den här definitionen för kontrollen.</span><span class="sxs-lookup"><span data-stu-id="7a659-103">Specifies a set of .NET types that use this definition of the control.</span></span> <span data-ttu-id="7a659-104">Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.</span><span class="sxs-lookup"><span data-stu-id="7a659-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="7a659-105">Konfigurationselementet Element (Format) kontroller av (Format) kontroll konfigurationselement för kontroller för (Format) anpassad kontroll konfigurationselement för kontroll för (Format) CustomEntries konfigurationselement för anpassad kontroll för konfiguration ( Format) CustomEntry Element för anpassad kontroll för kontroller för (Format) EntrySelectedBy konfigurationselement för CustomEntry för kontroller för (Format) SelectionSetName konfigurationselement för EntrySelectedBy för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="7a659-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7a659-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="7a659-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="7a659-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="7a659-107">Attributes and Elements</span></span>

<span data-ttu-id="7a659-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `SelectionSetName` element.</span><span class="sxs-lookup"><span data-stu-id="7a659-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7a659-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="7a659-109">Attributes</span></span>

<span data-ttu-id="7a659-110">Inga</span><span class="sxs-lookup"><span data-stu-id="7a659-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="7a659-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="7a659-111">Child Elements</span></span>

<span data-ttu-id="7a659-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="7a659-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7a659-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="7a659-113">Parent Elements</span></span>

|<span data-ttu-id="7a659-114">Element</span><span class="sxs-lookup"><span data-stu-id="7a659-114">Element</span></span>|<span data-ttu-id="7a659-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7a659-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7a659-116">EntrySelectedBy Element för CustomEntry för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="7a659-116">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="7a659-117">Definierar vilka typer av .NET som använder den här kontrollen definitionen eller villkor som måste finnas för den här definitionen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="7a659-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7a659-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="7a659-118">Text Value</span></span>

<span data-ttu-id="7a659-119">Ange namnet på val av uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="7a659-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="7a659-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="7a659-120">Remarks</span></span>

<span data-ttu-id="7a659-121">Varje kontrolldefinition måste ha minst ett namn, val av set eller Urvalsvillkoret som definierats.</span><span class="sxs-lookup"><span data-stu-id="7a659-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="7a659-122">Inställningarna används vanligtvis när du vill definiera en grupp med objekt som används i flera vyer.</span><span class="sxs-lookup"><span data-stu-id="7a659-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="7a659-123">Mer information om hur du definierar inställningarna finns i [definiera val av anger](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="7a659-123">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7a659-124">Se även</span><span class="sxs-lookup"><span data-stu-id="7a659-124">See Also</span></span>

[<span data-ttu-id="7a659-125">EntrySelectedBy Element för CustomEntry för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="7a659-125">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="7a659-126">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="7a659-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
