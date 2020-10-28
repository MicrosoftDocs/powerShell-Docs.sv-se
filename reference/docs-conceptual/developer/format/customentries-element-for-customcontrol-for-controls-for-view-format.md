---
ms.date: 09/13/2016
ms.topic: reference
title: CustomEntries-element för CustomControl för Controls för View (format)
description: CustomEntries-element för CustomControl för Controls för View (format)
ms.openlocfilehash: 43187294a407d08f765f8c42aba25d13dba6d901
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92652375"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-view-format"></a><span data-ttu-id="64f9a-103">CustomEntries-element för CustomControl för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="64f9a-103">CustomEntries Element for CustomControl for Controls for View (Format)</span></span>

<span data-ttu-id="64f9a-104">Innehåller definitionerna för kontrollen.</span><span class="sxs-lookup"><span data-stu-id="64f9a-104">Provides the definitions for the control.</span></span> <span data-ttu-id="64f9a-105">Det här elementet används när du definierar kontroller som kan användas av en vy.</span><span class="sxs-lookup"><span data-stu-id="64f9a-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="64f9a-106">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) styr element (format) kontroll element (format) styr element (format) kontroll element för Controls för View (format) CustomControl-element för kontroll för kontroller för View (format) CustomEntries-element för CustomControl för kontroller (format)</span><span class="sxs-lookup"><span data-stu-id="64f9a-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="64f9a-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="64f9a-107">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="64f9a-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="64f9a-108">Attributes and Elements</span></span>

<span data-ttu-id="64f9a-109">I följande avsnitt beskrivs attribut, underordnade element och `CustomEntries` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="64f9a-109">The following sections describe attributes, child elements, and parent elements of the `CustomEntries` element.</span></span> <span data-ttu-id="64f9a-110">Det finns ingen övre gräns för antalet underordnade element som kan anges.</span><span class="sxs-lookup"><span data-stu-id="64f9a-110">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="64f9a-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="64f9a-111">Attributes</span></span>

<span data-ttu-id="64f9a-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="64f9a-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="64f9a-113">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="64f9a-113">Child Elements</span></span>

|<span data-ttu-id="64f9a-114">Element</span><span class="sxs-lookup"><span data-stu-id="64f9a-114">Element</span></span>|<span data-ttu-id="64f9a-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="64f9a-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="64f9a-116">CustomEntry-element för CustomEntries för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="64f9a-116">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="64f9a-117">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="64f9a-117">Required element.</span></span><br /><br /> <span data-ttu-id="64f9a-118">Ger en definition av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="64f9a-118">Provides a definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="64f9a-119">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="64f9a-119">Parent Elements</span></span>

|<span data-ttu-id="64f9a-120">Element</span><span class="sxs-lookup"><span data-stu-id="64f9a-120">Element</span></span>|<span data-ttu-id="64f9a-121">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="64f9a-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="64f9a-122">CustomControl-element för Control för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="64f9a-122">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="64f9a-123">Definierar den kontroll som används i vyn.</span><span class="sxs-lookup"><span data-stu-id="64f9a-123">Defines the control used by the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="64f9a-124">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="64f9a-124">Remarks</span></span>

<span data-ttu-id="64f9a-125">I de flesta fall har en kontroll bara en definition som anges i ett enda `CustomEntry` element.</span><span class="sxs-lookup"><span data-stu-id="64f9a-125">In most cases, a control has only one definition, which is specified in a single `CustomEntry` element.</span></span> <span data-ttu-id="64f9a-126">Det är dock möjligt att tillhandahålla flera definitioner om du vill använda samma kontroll för att visa olika .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="64f9a-126">However, it is possible to provide multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="64f9a-127">I dessa fall kan du definiera ett- `CustomEntry` element för varje objekt eller uppsättning objekt.</span><span class="sxs-lookup"><span data-stu-id="64f9a-127">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="64f9a-128">Se även</span><span class="sxs-lookup"><span data-stu-id="64f9a-128">See Also</span></span>

[<span data-ttu-id="64f9a-129">CustomEntry-element för CustomEntries för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="64f9a-129">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="64f9a-130">CustomControl-element för Control för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="64f9a-130">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="64f9a-131">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="64f9a-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
