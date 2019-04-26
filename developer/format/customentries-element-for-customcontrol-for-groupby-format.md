---
title: CustomEntries Element för anpassad kontroll för GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af83c0f6-7fdd-4aa0-af12-efc62f632974
caps.latest.revision: 7
ms.openlocfilehash: f073142bf836ae892f161cf8c36ed16c35e311f5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066555"
---
# <a name="customentries-element-for-customcontrol-for-groupby-format"></a><span data-ttu-id="142a8-102">CustomEntries-element för CustomControl för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="142a8-102">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

<span data-ttu-id="142a8-103">Innehåller definitioner för kontrollen.</span><span class="sxs-lookup"><span data-stu-id="142a8-103">Provides the definitions for the control.</span></span> <span data-ttu-id="142a8-104">Det här elementet används när du definierar hur en ny grupp med objekt visas.</span><span class="sxs-lookup"><span data-stu-id="142a8-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="142a8-105">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) GroupBy konfigurationselement för Visa (Format) anpassad kontroll elementet för GroupBy (Format) CustomEntries Element för anpassad kontroll för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="142a8-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="142a8-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="142a8-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="142a8-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="142a8-107">Attributes and Elements</span></span>

<span data-ttu-id="142a8-108">I följande avsnitt beskrivs attribut, underordnade element och överordnade element i den `CustomEntries` element.</span><span class="sxs-lookup"><span data-stu-id="142a8-108">The following sections describe attributes, child elements, and parent elements of the `CustomEntries` element.</span></span> <span data-ttu-id="142a8-109">Det finns ingen högsta gräns för antalet underordnade element som kan anges.</span><span class="sxs-lookup"><span data-stu-id="142a8-109">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="142a8-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="142a8-110">Attributes</span></span>

<span data-ttu-id="142a8-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="142a8-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="142a8-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="142a8-112">Child Elements</span></span>

|<span data-ttu-id="142a8-113">Element</span><span class="sxs-lookup"><span data-stu-id="142a8-113">Element</span></span>|<span data-ttu-id="142a8-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="142a8-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="142a8-115">CustomEntry Element för anpassad kontroll för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="142a8-115">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="142a8-116">Element som krävs.</span><span class="sxs-lookup"><span data-stu-id="142a8-116">Required element.</span></span><br /><br /> <span data-ttu-id="142a8-117">Innehåller en definition av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="142a8-117">Provides a definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="142a8-118">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="142a8-118">Parent Elements</span></span>

|<span data-ttu-id="142a8-119">Element</span><span class="sxs-lookup"><span data-stu-id="142a8-119">Element</span></span>|<span data-ttu-id="142a8-120">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="142a8-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="142a8-121">Anpassad kontroll Element för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="142a8-121">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="142a8-122">Definierar den anpassade kontrollen som visar den nya gruppen.</span><span class="sxs-lookup"><span data-stu-id="142a8-122">Defines the custom control that displays the new group.</span></span>|

## <a name="remarks"></a><span data-ttu-id="142a8-123">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="142a8-123">Remarks</span></span>

<span data-ttu-id="142a8-124">I de flesta fall en kontroll har endast en definition som anges i en enda `CustomEntry` element.</span><span class="sxs-lookup"><span data-stu-id="142a8-124">In most cases, a control has only one definition, which is specified in a single `CustomEntry` element.</span></span> <span data-ttu-id="142a8-125">Det är dock möjligt att ange flera definitioner om du vill använda samma kontroll för att visa olika grupper.</span><span class="sxs-lookup"><span data-stu-id="142a8-125">However, it is possible to provide multiple definitions if you want to use the same control to display different groups.</span></span> <span data-ttu-id="142a8-126">I sådana fall kan du definiera en `CustomEntry` element för en grupp.</span><span class="sxs-lookup"><span data-stu-id="142a8-126">In those cases, you can define a `CustomEntry` element for a group.</span></span>

## <a name="see-also"></a><span data-ttu-id="142a8-127">Se även</span><span class="sxs-lookup"><span data-stu-id="142a8-127">See Also</span></span>

[<span data-ttu-id="142a8-128">CustomEntry Element för CustomEntries för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="142a8-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="142a8-129">Anpassad kontroll Element för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="142a8-129">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="142a8-130">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="142a8-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
