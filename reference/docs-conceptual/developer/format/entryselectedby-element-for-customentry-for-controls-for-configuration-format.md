---
title: EntrySelectedBy-element för CustomEntry för kontroll av konfiguration (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e9467c8c2d80e46c0a47c31569efbddbabe25bb1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774277"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-configuration-format"></a><span data-ttu-id="57a46-102">EntrySelectedBy-element för CustomEntry för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="57a46-102">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>

<span data-ttu-id="57a46-103">Definierar de .NET-typer som använder definitionen av den gemensamma kontrollen eller villkoret som måste finnas för att den här kontrollen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="57a46-103">Defines the .NET types that use the definition of the common control or the condition that must exist for this control to be used.</span></span> <span data-ttu-id="57a46-104">Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.</span><span class="sxs-lookup"><span data-stu-id="57a46-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="57a46-105">Konfigurations element (format) styr element i konfigurations-(format)-kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för Configuration (format) CustomEntry-element för CustomControl för Controls (format) EntrySelectedBy-element för CustomEntry för kontroll av konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="57a46-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="57a46-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="57a46-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="57a46-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="57a46-107">Attributes and Elements</span></span>

<span data-ttu-id="57a46-108">I följande avsnitt beskrivs attribut, underordnade element och `EntrySelectedBy` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="57a46-108">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="57a46-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="57a46-109">Attributes</span></span>

<span data-ttu-id="57a46-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="57a46-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="57a46-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="57a46-111">Child Elements</span></span>

|<span data-ttu-id="57a46-112">Element</span><span class="sxs-lookup"><span data-stu-id="57a46-112">Element</span></span>|<span data-ttu-id="57a46-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="57a46-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="57a46-114">SelectionCondition-element för EntrySelectedBy för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="57a46-114">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="57a46-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="57a46-115">Optional element.</span></span><br /><br /> <span data-ttu-id="57a46-116">Definierar det villkor som måste finnas för att den gemensamma kontroll definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="57a46-116">Defines the condition that must exist for the common control definition to be used.</span></span>|
|[<span data-ttu-id="57a46-117">SelectionSetName-element för EntrySelectedBy för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="57a46-117">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="57a46-118">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="57a46-118">Optional element.</span></span><br /><br /> <span data-ttu-id="57a46-119">Anger en uppsättning av .NET-typer som använder den här definitionen av den gemensamma kontrollen.</span><span class="sxs-lookup"><span data-stu-id="57a46-119">Specifies a set of .NET types that use this definition of the common control.</span></span>|
|[<span data-ttu-id="57a46-120">TypeName-element för EntrySelectedBy för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="57a46-120">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="57a46-121">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="57a46-121">Optional element.</span></span><br /><br /> <span data-ttu-id="57a46-122">Anger en .NET-typ som använder den här definitionen av den gemensamma kontrollen.</span><span class="sxs-lookup"><span data-stu-id="57a46-122">Specifies a .NET type that uses this definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="57a46-123">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="57a46-123">Parent Elements</span></span>

|<span data-ttu-id="57a46-124">Element</span><span class="sxs-lookup"><span data-stu-id="57a46-124">Element</span></span>|<span data-ttu-id="57a46-125">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="57a46-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="57a46-126">CustomEntry-element för CustomControl för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="57a46-126">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="57a46-127">Ger en definition av den gemensamma kontrollen.</span><span class="sxs-lookup"><span data-stu-id="57a46-127">Provides a definition of the common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="57a46-128">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="57a46-128">Remarks</span></span>

<span data-ttu-id="57a46-129">Varje definition måste minst ha minst en .NET-typ, markerings uppsättning eller ett urvals villkor angivet.</span><span class="sxs-lookup"><span data-stu-id="57a46-129">At a minimum, each definition must have at least one .NET type, selection set, or selection condition specified.</span></span> <span data-ttu-id="57a46-130">Det finns ingen övre gräns för antalet typer, markerings uppsättningar eller markerings villkor som du kan ange.</span><span class="sxs-lookup"><span data-stu-id="57a46-130">There is no maximum limit to the number of types, selection sets, or selection conditions that you can specify.</span></span>

## <a name="see-also"></a><span data-ttu-id="57a46-131">Se även</span><span class="sxs-lookup"><span data-stu-id="57a46-131">See Also</span></span>

[<span data-ttu-id="57a46-132">SelectionCondition-element för EntrySelectedBy för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="57a46-132">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="57a46-133">SelectionSetName-element för EntrySelectedBy för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="57a46-133">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="57a46-134">CustomEntry-element för CustomControl för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="57a46-134">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="57a46-135">TypeName-element för EntrySelectedBy för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="57a46-135">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="57a46-136">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="57a46-136">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
