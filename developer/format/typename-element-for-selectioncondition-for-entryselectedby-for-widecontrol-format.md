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
ms.openlocfilehash: 6142350e3843a5feddcb5cee8901bbfa607d8d4c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083815"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="6d2ba-102">TypeName-element för SelectionCondition för EntrySelectedBy för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="6d2ba-102">TypeName Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="6d2ba-103">Anger ett .NET-typ som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="6d2ba-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="6d2ba-104">Om den här typen finns används definitionen.</span><span class="sxs-lookup"><span data-stu-id="6d2ba-104">When this type is present, the definition is used.</span></span>

<span data-ttu-id="6d2ba-105">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy konfigurationselement för WideEntry (Format) SelectionCondition elementet för EntrySelectedBy för WideEntry (Format) TypeName-elementet för SelectionCondition för EntrySelectedBy för WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="6d2ba-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6d2ba-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="6d2ba-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6d2ba-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="6d2ba-107">Attributes and Elements</span></span>

<span data-ttu-id="6d2ba-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `TypeName` element.</span><span class="sxs-lookup"><span data-stu-id="6d2ba-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6d2ba-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="6d2ba-109">Attributes</span></span>

<span data-ttu-id="6d2ba-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="6d2ba-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6d2ba-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="6d2ba-111">Child Elements</span></span>

<span data-ttu-id="6d2ba-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="6d2ba-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6d2ba-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="6d2ba-113">Parent Elements</span></span>

|<span data-ttu-id="6d2ba-114">Element</span><span class="sxs-lookup"><span data-stu-id="6d2ba-114">Element</span></span>|<span data-ttu-id="6d2ba-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="6d2ba-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6d2ba-116">SelectionCondition Element för EntrySelectedBy för WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="6d2ba-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="6d2ba-117">Definierar de villkor som måste finnas för den här wide posten som ska användas.</span><span class="sxs-lookup"><span data-stu-id="6d2ba-117">Defines the condition that must exist for this wide entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="6d2ba-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="6d2ba-118">Text Value</span></span>

<span data-ttu-id="6d2ba-119">Ange det fullständigt kvalificerade namnet för .NET-typ, till exempel `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="6d2ba-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="6d2ba-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="6d2ba-120">Remarks</span></span>

<span data-ttu-id="6d2ba-121">Urvalsvillkoret kan ange en .NET-typ eller ett urval anger, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="6d2ba-121">The selection condition can specify a .NET type or a selection set, but cannot specify both.</span></span> <span data-ttu-id="6d2ba-122">Läs mer om hur du använder villkor för val av [definiera villkor för när Data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="6d2ba-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="6d2ba-123">Mer information om andra komponenter för en bred vy finns i [skapar en bred vy](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="6d2ba-123">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6d2ba-124">Se även</span><span class="sxs-lookup"><span data-stu-id="6d2ba-124">See Also</span></span>

[<span data-ttu-id="6d2ba-125">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="6d2ba-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="6d2ba-126">Definiera villkor för när Data visas</span><span class="sxs-lookup"><span data-stu-id="6d2ba-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="6d2ba-127">SelectionCondition Element för EntrySelectedBy för WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="6d2ba-127">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="6d2ba-128">SelectionSetName Element för SelectionCondition för EntrySelectedBy för WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="6d2ba-128">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="6d2ba-129">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="6d2ba-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
