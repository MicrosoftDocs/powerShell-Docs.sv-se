---
title: Elementet TypeName för SelectionCondition för EntrySelectedBy för ListControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bd025a3a-3780-40db-a068-873e7df38015
caps.latest.revision: 9
ms.openlocfilehash: 2b76b040b39088cc9c3b9d6890c38df3c533b39f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353517"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="57a8b-102">TypeName-element för SelectionCondition för EntrySelectedBy för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="57a8b-102">TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="57a8b-103">Anger en .NET-typ som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="57a8b-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="57a8b-104">När den här typen finns används List posten.</span><span class="sxs-lookup"><span data-stu-id="57a8b-104">When this type is present, the list entry is used.</span></span>

<span data-ttu-id="57a8b-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) ListControl element (format) ListEntries-element för ListControl (format) ListEntry-element för ListEntries för ListControl (format) EntrySelectedBy-element för ListEntry för ListControl (format) SelectionCondition-element för EntrySelectedBy för ListControl (format) TypeName-element för SelectionCondition för EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="57a8b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) EntrySelectedBy Element for ListEntry for ListControl (Format) SelectionCondition Element for EntrySelectedBy for ListControl (Format) TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="57a8b-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="57a8b-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="57a8b-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="57a8b-107">Attributes and Elements</span></span>

<span data-ttu-id="57a8b-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för elementet `TypeName`.</span><span class="sxs-lookup"><span data-stu-id="57a8b-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="57a8b-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="57a8b-109">Attributes</span></span>

<span data-ttu-id="57a8b-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="57a8b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="57a8b-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="57a8b-111">Child Elements</span></span>

<span data-ttu-id="57a8b-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="57a8b-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="57a8b-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="57a8b-113">Parent Elements</span></span>

|<span data-ttu-id="57a8b-114">Element</span><span class="sxs-lookup"><span data-stu-id="57a8b-114">Element</span></span>|<span data-ttu-id="57a8b-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="57a8b-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="57a8b-116">SelectionCondition-element för EntrySelectedBy för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="57a8b-116">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="57a8b-117">Definierar det villkor som måste finnas för att den här List posten ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="57a8b-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="57a8b-118">Text värde</span><span class="sxs-lookup"><span data-stu-id="57a8b-118">Text Value</span></span>

<span data-ttu-id="57a8b-119">Ange det fullständigt kvalificerade namnet för .NET-typen, t. ex. `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="57a8b-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="57a8b-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="57a8b-120">Remarks</span></span>

<span data-ttu-id="57a8b-121">Urvals villkoret kan ange valfritt antal .NET-typer eller markerings uppsättningar, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="57a8b-121">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span> <span data-ttu-id="57a8b-122">Mer information om hur du använder urvals villkor finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="57a8b-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="57a8b-123">Mer information om andra komponenter i en listvy finns i [skapa en listvy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="57a8b-123">For more information about other the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="57a8b-124">Se även</span><span class="sxs-lookup"><span data-stu-id="57a8b-124">See Also</span></span>

[<span data-ttu-id="57a8b-125">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="57a8b-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="57a8b-126">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="57a8b-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="57a8b-127">SelectionCondition-element för EntrySelectedBy för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="57a8b-127">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="57a8b-128">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="57a8b-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
