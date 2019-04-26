---
title: TypeName-Element för SelectionCondition för EntrySelectedBy för ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bd025a3a-3780-40db-a068-873e7df38015
caps.latest.revision: 9
ms.openlocfilehash: 2b76b040b39088cc9c3b9d6890c38df3c533b39f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083866"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="74119-102">TypeName-element för SelectionCondition för EntrySelectedBy för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="74119-102">TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="74119-103">Anger ett .NET-typ som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="74119-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="74119-104">Om den här typen finns används posten.</span><span class="sxs-lookup"><span data-stu-id="74119-104">When this type is present, the list entry is used.</span></span>

<span data-ttu-id="74119-105">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) ListControl Element (Format) ListEntries konfigurationselement för ListControl (Format) ListEntry elementet för ListEntries för ListControl (Format) EntrySelectedBy elementet för ListEntry för ListControl (Format) SelectionCondition elementet för EntrySelectedBy för ListControl (Format) TypeName-elementet för SelectionCondition för EntrySelectedBy för ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="74119-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) EntrySelectedBy Element for ListEntry for ListControl (Format) SelectionCondition Element for EntrySelectedBy for ListControl (Format) TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="74119-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="74119-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="74119-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="74119-107">Attributes and Elements</span></span>

<span data-ttu-id="74119-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `TypeName` element.</span><span class="sxs-lookup"><span data-stu-id="74119-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="74119-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="74119-109">Attributes</span></span>

<span data-ttu-id="74119-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="74119-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="74119-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="74119-111">Child Elements</span></span>

<span data-ttu-id="74119-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="74119-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="74119-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="74119-113">Parent Elements</span></span>

|<span data-ttu-id="74119-114">Element</span><span class="sxs-lookup"><span data-stu-id="74119-114">Element</span></span>|<span data-ttu-id="74119-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="74119-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="74119-116">SelectionCondition Element för EntrySelectedBy för ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="74119-116">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="74119-117">Definierar de villkor som måste finnas för den här posten som ska användas.</span><span class="sxs-lookup"><span data-stu-id="74119-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="74119-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="74119-118">Text Value</span></span>

<span data-ttu-id="74119-119">Ange det fullständigt kvalificerade namnet för .NET-typ, till exempel `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="74119-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="74119-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="74119-120">Remarks</span></span>

<span data-ttu-id="74119-121">Urvalsvillkoret kan ange valfritt antal typer i .NET eller val av anger, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="74119-121">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span> <span data-ttu-id="74119-122">Läs mer om hur du använder villkor för val av [definiera villkor för när Data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="74119-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="74119-123">Läs mer om andra komponenter i en listvy i [skapar en listvy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="74119-123">For more information about other the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="74119-124">Se även</span><span class="sxs-lookup"><span data-stu-id="74119-124">See Also</span></span>

[<span data-ttu-id="74119-125">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="74119-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="74119-126">Definiera villkor för när Data visas</span><span class="sxs-lookup"><span data-stu-id="74119-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="74119-127">SelectionCondition Element för EntrySelectedBy för ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="74119-127">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="74119-128">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="74119-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
