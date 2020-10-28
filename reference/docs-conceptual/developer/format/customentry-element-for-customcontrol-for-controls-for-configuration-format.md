---
ms.date: 09/13/2016
ms.topic: reference
title: CustomEntry-element för CustomControl för Controls för Configuration (format)
description: CustomEntry-element för CustomControl för Controls för Configuration (format)
ms.openlocfilehash: 3967be86a1d6c12c7215ef19d50bac9fafd5ad6d
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92648288"
---
# <a name="customentry-element-for-customcontrol-for-controls-for-configuration-format"></a><span data-ttu-id="cfabd-103">CustomEntry-element för CustomControl för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="cfabd-103">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>

<span data-ttu-id="cfabd-104">Ger en definition av den gemensamma kontrollen.</span><span class="sxs-lookup"><span data-stu-id="cfabd-104">Provides a definition of the common control.</span></span> <span data-ttu-id="cfabd-105">Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.</span><span class="sxs-lookup"><span data-stu-id="cfabd-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="cfabd-106">Konfigurations element (format) styr element i konfigurations-(format)-kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för Configuration (format) CustomEntry-element för CustomControl för kontroll av konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="cfabd-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cfabd-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="cfabd-107">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="cfabd-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="cfabd-108">Attributes and Elements</span></span>

<span data-ttu-id="cfabd-109">I följande avsnitt beskrivs attribut, underordnade element och `CustomEntry` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="cfabd-109">The following sections describe attributes, child elements, and the parent element of the `CustomEntry` element.</span></span> <span data-ttu-id="cfabd-110">Du måste ange de objekt som ska visas av definitionen.</span><span class="sxs-lookup"><span data-stu-id="cfabd-110">You must specify the items displayed by the definition.</span></span>

### <a name="attributes"></a><span data-ttu-id="cfabd-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="cfabd-111">Attributes</span></span>

<span data-ttu-id="cfabd-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="cfabd-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cfabd-113">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="cfabd-113">Child Elements</span></span>

|<span data-ttu-id="cfabd-114">Element</span><span class="sxs-lookup"><span data-stu-id="cfabd-114">Element</span></span>|<span data-ttu-id="cfabd-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="cfabd-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cfabd-116">EntrySelectedBy-element för CustomEntry för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="cfabd-116">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="cfabd-117">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="cfabd-117">Optional element.</span></span><br /><br /> <span data-ttu-id="cfabd-118">Definierar de .NET-typer som använder definitionen av den gemensamma kontrollen eller villkoret som måste finnas för att den här kontrollen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="cfabd-118">Defines the .NET types that use the definition of the common control or the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="cfabd-119">CustomItem-element för CustomEntry för kontroller för konfiguration</span><span class="sxs-lookup"><span data-stu-id="cfabd-119">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="cfabd-120">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="cfabd-120">Required element.</span></span><br /><br /> <span data-ttu-id="cfabd-121">Definierar vilka data som visas av kontrollen och hur de visas.</span><span class="sxs-lookup"><span data-stu-id="cfabd-121">Defines what data is displayed by the control and how it is displayed.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="cfabd-122">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="cfabd-122">Parent Elements</span></span>

|<span data-ttu-id="cfabd-123">Element</span><span class="sxs-lookup"><span data-stu-id="cfabd-123">Element</span></span>|<span data-ttu-id="cfabd-124">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="cfabd-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cfabd-125">CustomEntries-element för CustomControl för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="cfabd-125">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="cfabd-126">Innehåller definitionerna för den gemensamma kontrollen.</span><span class="sxs-lookup"><span data-stu-id="cfabd-126">Provides the definitions of the common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="cfabd-127">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="cfabd-127">Remarks</span></span>

<span data-ttu-id="cfabd-128">I de flesta fall krävs bara en definition för varje gemensam anpassad kontroll, men det är möjligt att ha flera definitioner om du vill använda samma kontroll för att visa olika .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="cfabd-128">In most cases, only one definition is required for each common custom control, but it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="cfabd-129">I dessa fall kan du ange en separat definition för varje objekt eller uppsättning objekt.</span><span class="sxs-lookup"><span data-stu-id="cfabd-129">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="cfabd-130">Se även</span><span class="sxs-lookup"><span data-stu-id="cfabd-130">See Also</span></span>

[<span data-ttu-id="cfabd-131">CustomEntries-element för CustomControl för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="cfabd-131">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="cfabd-132">CustomItem-element för CustomEntry för kontroller för konfiguration</span><span class="sxs-lookup"><span data-stu-id="cfabd-132">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="cfabd-133">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="cfabd-133">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
