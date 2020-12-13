---
ms.date: 09/13/2016
ms.topic: reference
title: TypeName-element för EntrySelectedBy för CustomEntry för View (format)
description: TypeName-element för EntrySelectedBy för CustomEntry för View (format)
ms.openlocfilehash: 72bb88bccc2bbd62f7ed160b820cf9169cb69341
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645740"
---
# <a name="typename-element-for-entryselectedby-for-customentry-for-view-format"></a><span data-ttu-id="6e794-103">TypeName-element för EntrySelectedBy för CustomEntry för View (format)</span><span class="sxs-lookup"><span data-stu-id="6e794-103">TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

<span data-ttu-id="6e794-104">Anger en .NET-typ som använder den här definitionen för den anpassade kontrollen.</span><span class="sxs-lookup"><span data-stu-id="6e794-104">Specifies a .NET type that uses this definition of the custom control view.</span></span> <span data-ttu-id="6e794-105">Det finns ingen gräns för antalet typer som kan anges för en definition.</span><span class="sxs-lookup"><span data-stu-id="6e794-105">There is no limit to the number of types that can be specified for a definition.</span></span>

<span data-ttu-id="6e794-106">Konfigurations element (format) ViewDefinitions element (format) View element (format) CustomControl element (format) CustomEntries-element för CustomControl för View (format) CustomEntry-element för CustomEntries för View (format) EntrySelectedBy-element för CustomEntry för View (format) elementet TypeName for EntrySelectedBy för View (format)</span><span class="sxs-lookup"><span data-stu-id="6e794-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6e794-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="6e794-107">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6e794-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="6e794-108">Attributes and Elements</span></span>

<span data-ttu-id="6e794-109">I följande avsnitt beskrivs attribut, underordnade element och `TypeName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="6e794-109">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6e794-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="6e794-110">Attributes</span></span>

<span data-ttu-id="6e794-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="6e794-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6e794-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="6e794-112">Child Elements</span></span>

<span data-ttu-id="6e794-113">Inga.</span><span class="sxs-lookup"><span data-stu-id="6e794-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6e794-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="6e794-114">Parent Elements</span></span>

|<span data-ttu-id="6e794-115">Element</span><span class="sxs-lookup"><span data-stu-id="6e794-115">Element</span></span>|<span data-ttu-id="6e794-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="6e794-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6e794-117">EntrySelectedBy-element för CustomEntry för vy (format)</span><span class="sxs-lookup"><span data-stu-id="6e794-117">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="6e794-118">Definierar de .NET-typer som använder den här anpassade kontroll definitionen eller det villkor som måste finnas för att den här definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="6e794-118">Defines the .NET types that use this custom control view definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="6e794-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="6e794-119">Text Value</span></span>

<span data-ttu-id="6e794-120">Ange det fullständigt kvalificerade namnet för .NET-typen, t `System.IO.DirectoryInfo` . ex..</span><span class="sxs-lookup"><span data-stu-id="6e794-120">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="6e794-121">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="6e794-121">Remarks</span></span>

<span data-ttu-id="6e794-122">Varje definition av anpassad kontroll måste ha minst ett typ namn, en urvals uppsättning eller ett urvals villkor definierat.</span><span class="sxs-lookup"><span data-stu-id="6e794-122">Each custom control view definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="6e794-123">Mer information om komponenterna i en anpassad kontroll vy finns i [skapa anpassade kontroller](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="6e794-123">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6e794-124">Se även</span><span class="sxs-lookup"><span data-stu-id="6e794-124">See Also</span></span>

[<span data-ttu-id="6e794-125">Skapa anpassade kontroller</span><span class="sxs-lookup"><span data-stu-id="6e794-125">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="6e794-126">EntrySelectedBy-element för CustomEntry för vy (format)</span><span class="sxs-lookup"><span data-stu-id="6e794-126">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="6e794-127">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="6e794-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
