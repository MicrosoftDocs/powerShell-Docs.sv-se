---
ms.date: 09/13/2016
ms.topic: reference
title: CustomEntries-element för CustomControl för GroupBy (format)
description: CustomEntries-element för CustomControl för GroupBy (format)
ms.openlocfilehash: cde59d38b83930cb64a3a0040891783e4ab96723
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92666798"
---
# <a name="customentries-element-for-customcontrol-for-groupby-format"></a><span data-ttu-id="470dd-103">CustomEntries-element för CustomControl för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="470dd-103">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

<span data-ttu-id="470dd-104">Innehåller definitionerna för kontrollen.</span><span class="sxs-lookup"><span data-stu-id="470dd-104">Provides the definitions for the control.</span></span> <span data-ttu-id="470dd-105">Det här elementet används när du definierar hur en ny grupp av objekt visas.</span><span class="sxs-lookup"><span data-stu-id="470dd-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="470dd-106">Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="470dd-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="470dd-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="470dd-107">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="470dd-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="470dd-108">Attributes and Elements</span></span>

<span data-ttu-id="470dd-109">I följande avsnitt beskrivs attribut, underordnade element och `CustomEntries` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="470dd-109">The following sections describe attributes, child elements, and parent elements of the `CustomEntries` element.</span></span> <span data-ttu-id="470dd-110">Det finns ingen övre gräns för antalet underordnade element som kan anges.</span><span class="sxs-lookup"><span data-stu-id="470dd-110">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="470dd-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="470dd-111">Attributes</span></span>

<span data-ttu-id="470dd-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="470dd-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="470dd-113">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="470dd-113">Child Elements</span></span>

|<span data-ttu-id="470dd-114">Element</span><span class="sxs-lookup"><span data-stu-id="470dd-114">Element</span></span>|<span data-ttu-id="470dd-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="470dd-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="470dd-116">CustomEntry-element för CustomControl för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="470dd-116">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="470dd-117">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="470dd-117">Required element.</span></span><br /><br /> <span data-ttu-id="470dd-118">Ger en definition av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="470dd-118">Provides a definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="470dd-119">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="470dd-119">Parent Elements</span></span>

|<span data-ttu-id="470dd-120">Element</span><span class="sxs-lookup"><span data-stu-id="470dd-120">Element</span></span>|<span data-ttu-id="470dd-121">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="470dd-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="470dd-122">CustomControl-element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="470dd-122">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="470dd-123">Definierar den anpassade kontrollen som visar den nya gruppen.</span><span class="sxs-lookup"><span data-stu-id="470dd-123">Defines the custom control that displays the new group.</span></span>|

## <a name="remarks"></a><span data-ttu-id="470dd-124">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="470dd-124">Remarks</span></span>

<span data-ttu-id="470dd-125">I de flesta fall har en kontroll bara en definition som anges i ett enda `CustomEntry` element.</span><span class="sxs-lookup"><span data-stu-id="470dd-125">In most cases, a control has only one definition, which is specified in a single `CustomEntry` element.</span></span> <span data-ttu-id="470dd-126">Det är dock möjligt att tillhandahålla flera definitioner om du vill använda samma kontroll för att visa olika grupper.</span><span class="sxs-lookup"><span data-stu-id="470dd-126">However, it is possible to provide multiple definitions if you want to use the same control to display different groups.</span></span> <span data-ttu-id="470dd-127">I dessa fall kan du definiera ett- `CustomEntry` element för en grupp.</span><span class="sxs-lookup"><span data-stu-id="470dd-127">In those cases, you can define a `CustomEntry` element for a group.</span></span>

## <a name="see-also"></a><span data-ttu-id="470dd-128">Se även</span><span class="sxs-lookup"><span data-stu-id="470dd-128">See Also</span></span>

[<span data-ttu-id="470dd-129">CustomEntry-element för CustomEntries för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="470dd-129">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="470dd-130">CustomControl-element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="470dd-130">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="470dd-131">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="470dd-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
