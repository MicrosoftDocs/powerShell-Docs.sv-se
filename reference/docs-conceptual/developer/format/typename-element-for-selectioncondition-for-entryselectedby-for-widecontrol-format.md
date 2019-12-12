---
title: Elementet TypeName för SelectionCondition för EntrySelectedBy för WideControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d6d43fa-c900-4e2f-952d-deccd584236f
caps.latest.revision: 11
ms.openlocfilehash: 6142350e3843a5feddcb5cee8901bbfa607d8d4c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72358751"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="51036-102">TypeName-element för SelectionCondition för EntrySelectedBy för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="51036-102">TypeName Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="51036-103">Anger en .NET-typ som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="51036-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="51036-104">När den här typen finns används definitionen.</span><span class="sxs-lookup"><span data-stu-id="51036-104">When this type is present, the definition is used.</span></span>

<span data-ttu-id="51036-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) WideControl-element (format) WideEntries-element (format) WideEntry element (format) EntrySelectedBy-element för WideEntry (format) SelectionCondition-element för EntrySelectedBy för WideEntry (format) elementet TypeName för SelectionCondition för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="51036-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="51036-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="51036-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="51036-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="51036-107">Attributes and Elements</span></span>

<span data-ttu-id="51036-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `TypeName`-elementet.</span><span class="sxs-lookup"><span data-stu-id="51036-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="51036-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="51036-109">Attributes</span></span>

<span data-ttu-id="51036-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="51036-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="51036-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="51036-111">Child Elements</span></span>

<span data-ttu-id="51036-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="51036-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="51036-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="51036-113">Parent Elements</span></span>

|<span data-ttu-id="51036-114">Element</span><span class="sxs-lookup"><span data-stu-id="51036-114">Element</span></span>|<span data-ttu-id="51036-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="51036-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="51036-116">SelectionCondition-element för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="51036-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="51036-117">Definierar det villkor som måste finnas för att den här breda posten ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="51036-117">Defines the condition that must exist for this wide entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="51036-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="51036-118">Text Value</span></span>

<span data-ttu-id="51036-119">Ange det fullständigt kvalificerade namnet för .NET-typen, t. ex. `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="51036-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="51036-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="51036-120">Remarks</span></span>

<span data-ttu-id="51036-121">Urvals villkoret kan ange en .NET-typ eller en urvals uppsättning, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="51036-121">The selection condition can specify a .NET type or a selection set, but cannot specify both.</span></span> <span data-ttu-id="51036-122">Mer information om hur du använder urvals villkor finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="51036-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="51036-123">Mer information om andra komponenter i en bred vy finns i [skapa en bred vy](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="51036-123">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="51036-124">Se även</span><span class="sxs-lookup"><span data-stu-id="51036-124">See Also</span></span>

[<span data-ttu-id="51036-125">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="51036-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="51036-126">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="51036-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="51036-127">SelectionCondition-element för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="51036-127">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="51036-128">SelectionSetName-element för SelectionCondition för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="51036-128">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="51036-129">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="51036-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
