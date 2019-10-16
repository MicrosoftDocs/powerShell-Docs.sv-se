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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72358751"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="c82ad-102">TypeName-element för SelectionCondition för EntrySelectedBy för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="c82ad-102">TypeName Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="c82ad-103">Anger en .NET-typ som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="c82ad-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="c82ad-104">När den här typen finns används definitionen.</span><span class="sxs-lookup"><span data-stu-id="c82ad-104">When this type is present, the definition is used.</span></span>

<span data-ttu-id="c82ad-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) WideControl-element (format) WideEntries-element (format) WideEntry element (format) EntrySelectedBy-element för WideEntry (format) SelectionCondition-element för EntrySelectedBy för WideEntry (format) elementet TypeName för SelectionCondition för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="c82ad-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c82ad-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="c82ad-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c82ad-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="c82ad-107">Attributes and Elements</span></span>

<span data-ttu-id="c82ad-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för elementet `TypeName`.</span><span class="sxs-lookup"><span data-stu-id="c82ad-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c82ad-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="c82ad-109">Attributes</span></span>

<span data-ttu-id="c82ad-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="c82ad-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c82ad-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="c82ad-111">Child Elements</span></span>

<span data-ttu-id="c82ad-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="c82ad-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c82ad-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="c82ad-113">Parent Elements</span></span>

|<span data-ttu-id="c82ad-114">Element</span><span class="sxs-lookup"><span data-stu-id="c82ad-114">Element</span></span>|<span data-ttu-id="c82ad-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c82ad-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c82ad-116">SelectionCondition-element för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="c82ad-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="c82ad-117">Definierar det villkor som måste finnas för att den här breda posten ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="c82ad-117">Defines the condition that must exist for this wide entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c82ad-118">Text värde</span><span class="sxs-lookup"><span data-stu-id="c82ad-118">Text Value</span></span>

<span data-ttu-id="c82ad-119">Ange det fullständigt kvalificerade namnet för .NET-typen, t. ex. `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="c82ad-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="c82ad-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="c82ad-120">Remarks</span></span>

<span data-ttu-id="c82ad-121">Urvals villkoret kan ange en .NET-typ eller en urvals uppsättning, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="c82ad-121">The selection condition can specify a .NET type or a selection set, but cannot specify both.</span></span> <span data-ttu-id="c82ad-122">Mer information om hur du använder urvals villkor finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="c82ad-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="c82ad-123">Mer information om andra komponenter i en bred vy finns i [skapa en bred vy](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="c82ad-123">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c82ad-124">Se även</span><span class="sxs-lookup"><span data-stu-id="c82ad-124">See Also</span></span>

[<span data-ttu-id="c82ad-125">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="c82ad-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="c82ad-126">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="c82ad-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="c82ad-127">SelectionCondition-element för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="c82ad-127">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="c82ad-128">SelectionSetName-element för SelectionCondition för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="c82ad-128">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="c82ad-129">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="c82ad-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
