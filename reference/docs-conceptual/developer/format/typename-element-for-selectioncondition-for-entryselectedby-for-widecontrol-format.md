---
title: Elementet TypeName för SelectionCondition för EntrySelectedBy för WideControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 5021f665b994581f9ff982e13af922d7940ebf2b
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783321"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="564d1-102">TypeName-element för SelectionCondition för EntrySelectedBy för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="564d1-102">TypeName Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="564d1-103">Anger en .NET-typ som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="564d1-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="564d1-104">När den här typen finns används definitionen.</span><span class="sxs-lookup"><span data-stu-id="564d1-104">When this type is present, the definition is used.</span></span>

<span data-ttu-id="564d1-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) WideControl-element (format) WideEntries-element (format) WideEntry-element (format) EntrySelectedBy-element för WideEntry (format) SelectionCondition-element för EntrySelectedBy för WideEntry (format) element för SelectionCondition (format)</span><span class="sxs-lookup"><span data-stu-id="564d1-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="564d1-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="564d1-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="564d1-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="564d1-107">Attributes and Elements</span></span>

<span data-ttu-id="564d1-108">I följande avsnitt beskrivs attribut, underordnade element och `TypeName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="564d1-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="564d1-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="564d1-109">Attributes</span></span>

<span data-ttu-id="564d1-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="564d1-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="564d1-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="564d1-111">Child Elements</span></span>

<span data-ttu-id="564d1-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="564d1-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="564d1-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="564d1-113">Parent Elements</span></span>

|<span data-ttu-id="564d1-114">Element</span><span class="sxs-lookup"><span data-stu-id="564d1-114">Element</span></span>|<span data-ttu-id="564d1-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="564d1-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="564d1-116">SelectionCondition-element för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="564d1-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="564d1-117">Definierar det villkor som måste finnas för att den här breda posten ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="564d1-117">Defines the condition that must exist for this wide entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="564d1-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="564d1-118">Text Value</span></span>

<span data-ttu-id="564d1-119">Ange det fullständigt kvalificerade namnet för .NET-typen, t `System.IO.DirectoryInfo` . ex..</span><span class="sxs-lookup"><span data-stu-id="564d1-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="564d1-120">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="564d1-120">Remarks</span></span>

<span data-ttu-id="564d1-121">Urvals villkoret kan ange en .NET-typ eller en urvals uppsättning, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="564d1-121">The selection condition can specify a .NET type or a selection set, but cannot specify both.</span></span> <span data-ttu-id="564d1-122">Mer information om hur du använder urvals villkor finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="564d1-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="564d1-123">Mer information om andra komponenter i en bred vy finns i [skapa en bred vy](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="564d1-123">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="564d1-124">Se även</span><span class="sxs-lookup"><span data-stu-id="564d1-124">See Also</span></span>

[<span data-ttu-id="564d1-125">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="564d1-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="564d1-126">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="564d1-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="564d1-127">SelectionCondition-element för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="564d1-127">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="564d1-128">SelectionSetName-element för SelectionCondition för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="564d1-128">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="564d1-129">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="564d1-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
