---
ms.date: 09/13/2016
ms.topic: reference
title: TypeName-element för EntrySelectedBy för GroupBy (format)
description: TypeName-element för EntrySelectedBy för GroupBy (format)
ms.openlocfilehash: 07cc92e9c501aa0eb2d219e416851be0fcd80f47
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92645711"
---
# <a name="typename-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="e3e86-103">TypeName-element för EntrySelectedBy för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="e3e86-103">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="e3e86-104">Anger en .NET-typ som använder den här definitionen av den anpassade kontrollen.</span><span class="sxs-lookup"><span data-stu-id="e3e86-104">Specifies a .NET type that uses this definition of the custom control.</span></span> <span data-ttu-id="e3e86-105">Det här elementet används när du definierar hur en ny grupp av objekt visas.</span><span class="sxs-lookup"><span data-stu-id="e3e86-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="e3e86-106">Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för visnings-(format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for GroupBy (format) CustomEntry element for CustomControl for groupby (format) EntrySelectedBy-element för CustomEntry</span><span class="sxs-lookup"><span data-stu-id="e3e86-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e3e86-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="e3e86-107">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e3e86-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="e3e86-108">Attributes and Elements</span></span>

<span data-ttu-id="e3e86-109">I följande avsnitt beskrivs attribut, underordnade element och `TypeName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="e3e86-109">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e3e86-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="e3e86-110">Attributes</span></span>

<span data-ttu-id="e3e86-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="e3e86-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e3e86-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="e3e86-112">Child Elements</span></span>

<span data-ttu-id="e3e86-113">Inga.</span><span class="sxs-lookup"><span data-stu-id="e3e86-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e3e86-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="e3e86-114">Parent Elements</span></span>

|<span data-ttu-id="e3e86-115">Element</span><span class="sxs-lookup"><span data-stu-id="e3e86-115">Element</span></span>|<span data-ttu-id="e3e86-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e3e86-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e3e86-117">EntrySelectedBy-element för CustomEntry för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="e3e86-117">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="e3e86-118">Definierar de .NET-typer som använder den här kontroll definitionen eller det villkor som måste finnas för att den här definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="e3e86-118">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e3e86-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="e3e86-119">Text Value</span></span>

<span data-ttu-id="e3e86-120">Ange det fullständigt kvalificerade namnet för .NET-typen, t `System.IO.DirectoryInfo` . ex..</span><span class="sxs-lookup"><span data-stu-id="e3e86-120">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="e3e86-121">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="e3e86-121">Remarks</span></span>

<span data-ttu-id="e3e86-122">Varje kontroll definition måste ha minst ett typ namn, en markerings uppsättning eller ett urvals villkor definierat.</span><span class="sxs-lookup"><span data-stu-id="e3e86-122">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="e3e86-123">Mer information om komponenterna i en anpassad kontroll vy finns i [skapa anpassade kontroller](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="e3e86-123">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e3e86-124">Se även</span><span class="sxs-lookup"><span data-stu-id="e3e86-124">See Also</span></span>

[<span data-ttu-id="e3e86-125">Skapa anpassade kontroller</span><span class="sxs-lookup"><span data-stu-id="e3e86-125">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="e3e86-126">EntrySelectedBy-element för CustomEntry för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="e3e86-126">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="e3e86-127">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="e3e86-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
