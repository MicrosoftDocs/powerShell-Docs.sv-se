---
title: TypeName-Element för SelectionCondition för EntrySelectedBy för WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d6d43fa-c900-4e2f-952d-deccd584236f
caps.latest.revision: 11
ms.openlocfilehash: 0d7bbfd8be3bf2bd1af75a45ca4db016dfb6bff6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848183"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="043a3-102">TypeName-element för SelectionCondition för EntrySelectedBy för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="043a3-102">TypeName Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="043a3-103">Anger ett .NET-typ som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="043a3-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="043a3-104">Om den här typen finns används definitionen.</span><span class="sxs-lookup"><span data-stu-id="043a3-104">When this type is present, the definition is used.</span></span>

<span data-ttu-id="043a3-105">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy konfigurationselement för WideEntry (Format) SelectionCondition elementet för EntrySelectedBy för WideEntry (Format) TypeName-elementet för SelectionCondition för EntrySelectedBy för WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="043a3-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="043a3-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="043a3-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="043a3-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="043a3-107">Attributes and Elements</span></span>

<span data-ttu-id="043a3-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `TypeName` element.</span><span class="sxs-lookup"><span data-stu-id="043a3-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="043a3-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="043a3-109">Attributes</span></span>

<span data-ttu-id="043a3-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="043a3-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="043a3-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="043a3-111">Child Elements</span></span>

<span data-ttu-id="043a3-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="043a3-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="043a3-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="043a3-113">Parent Elements</span></span>

|<span data-ttu-id="043a3-114">Element</span><span class="sxs-lookup"><span data-stu-id="043a3-114">Element</span></span>|<span data-ttu-id="043a3-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="043a3-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="043a3-116">SelectionCondition Element för EntrySelectedBy för WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="043a3-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="043a3-117">Definierar de villkor som måste finnas för den här wide posten som ska användas.</span><span class="sxs-lookup"><span data-stu-id="043a3-117">Defines the condition that must exist for this wide entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="043a3-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="043a3-118">Text Value</span></span>

<span data-ttu-id="043a3-119">Ange det fullständigt kvalificerade namnet för .NET-typ, till exempel `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="043a3-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="043a3-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="043a3-120">Remarks</span></span>

<span data-ttu-id="043a3-121">Urvalsvillkoret kan ange en .NET-typ eller ett urval anger, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="043a3-121">The selection condition can specify a .NET type or a selection set, but cannot specify both.</span></span> <span data-ttu-id="043a3-122">Läs mer om hur du använder villkor för val av [definiera villkor för när Data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="043a3-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="043a3-123">Mer information om andra komponenter för en bred vy finns i [skapar en bred vy](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="043a3-123">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="043a3-124">Se även</span><span class="sxs-lookup"><span data-stu-id="043a3-124">See Also</span></span>

[<span data-ttu-id="043a3-125">Genererades en bred vy</span><span class="sxs-lookup"><span data-stu-id="043a3-125">Creatng a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="043a3-126">Definiera villkor för när Data visas</span><span class="sxs-lookup"><span data-stu-id="043a3-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="043a3-127">SelectionCondition Element för EntrySelectedBy för WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="043a3-127">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="043a3-128">SelectionSetName Element för SelectionCondition för EntrySelectedBy för WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="043a3-128">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="043a3-129">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="043a3-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
