---
title: PropertyName-element för SelectionCondition för EntrySelectedBy för WideEntry (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 340abb12-6df1-42f4-bdae-b0509c90952c
caps.latest.revision: 11
ms.openlocfilehash: 196877b97db9ed0592e357486c1318dc1e7efd31
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353993"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="8738c-102">PropertyName-element för SelectionCondition för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="8738c-102">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="8738c-103">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="8738c-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="8738c-104">När den här egenskapen finns eller när den utvärderas till `true`, uppfylls villkoret och definitionen används.</span><span class="sxs-lookup"><span data-stu-id="8738c-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="8738c-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) WideControl-element (format) WideEntries-element (format) WideEntry element (format) EntrySelectedBy-element för WideEntry (format) SelectionCondition-element för EntrySelectedBy för WideEntry (format) PropertyName-element för SelectionCondition för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="8738c-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8738c-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="8738c-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

```csharp

```

## <a name="attributes-and-elements"></a><span data-ttu-id="8738c-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="8738c-107">Attributes and Elements</span></span>

<span data-ttu-id="8738c-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `PropertyName`-elementet.</span><span class="sxs-lookup"><span data-stu-id="8738c-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8738c-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="8738c-109">Attributes</span></span>

<span data-ttu-id="8738c-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="8738c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8738c-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="8738c-111">Child Elements</span></span>

<span data-ttu-id="8738c-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="8738c-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8738c-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="8738c-113">Parent Elements</span></span>

|<span data-ttu-id="8738c-114">Element</span><span class="sxs-lookup"><span data-stu-id="8738c-114">Element</span></span>|<span data-ttu-id="8738c-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8738c-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8738c-116">SelectionCondition-element för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="8738c-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="8738c-117">Definierar det villkor som måste finnas för att den här definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="8738c-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8738c-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="8738c-118">Text Value</span></span>

<span data-ttu-id="8738c-119">Ange .NET-egenskaps namnet.</span><span class="sxs-lookup"><span data-stu-id="8738c-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="8738c-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="8738c-120">Remarks</span></span>

<span data-ttu-id="8738c-121">Urvals villkoret måste innehålla minst ett egenskaps namn eller ett skript som ska utvärderas, men det går inte att ange båda.</span><span class="sxs-lookup"><span data-stu-id="8738c-121">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="8738c-122">Mer information om hur du använder urvals villkor finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="8738c-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="8738c-123">Mer information om andra komponenter i en bred vy finns i [wide View](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="8738c-123">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8738c-124">Se även</span><span class="sxs-lookup"><span data-stu-id="8738c-124">See Also</span></span>

[<span data-ttu-id="8738c-125">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="8738c-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="8738c-126">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="8738c-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="8738c-127">Script block-element för SelectionCondition för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="8738c-127">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="8738c-128">SelectionCondition-element för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="8738c-128">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="8738c-129">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="8738c-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
