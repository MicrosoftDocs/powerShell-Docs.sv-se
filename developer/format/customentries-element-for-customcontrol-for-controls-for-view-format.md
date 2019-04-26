---
title: CustomEntries Element för anpassad kontroll för kontroller för att visa (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3485958a-ba87-4932-907c-a8f140c4abdb
caps.latest.revision: 8
ms.openlocfilehash: 4856aee930285781a101868bd6cb67824585bce1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066591"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-view-format"></a><span data-ttu-id="d1331-102">CustomEntries-element för CustomControl för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="d1331-102">CustomEntries Element for CustomControl for Controls for View (Format)</span></span>

<span data-ttu-id="d1331-103">Innehåller definitioner för kontrollen.</span><span class="sxs-lookup"><span data-stu-id="d1331-103">Provides the definitions for the control.</span></span> <span data-ttu-id="d1331-104">Det här elementet används när du definierar kontroller som kan användas av en vy.</span><span class="sxs-lookup"><span data-stu-id="d1331-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="d1331-105">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) kontroller Element (Format) kontroll konfigurationselement för kontroller för att visa (Format) anpassad kontroll Element för kontroll för kontroller för att visa (Format) CustomEntries Element för Anpassad kontroll för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="d1331-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d1331-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="d1331-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d1331-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="d1331-107">Attributes and Elements</span></span>

<span data-ttu-id="d1331-108">I följande avsnitt beskrivs attribut, underordnade element och överordnade element i den `CustomEntries` element.</span><span class="sxs-lookup"><span data-stu-id="d1331-108">The following sections describe attributes, child elements, and parent elements of the `CustomEntries` element.</span></span> <span data-ttu-id="d1331-109">Det finns ingen högsta gräns för antalet underordnade element som kan anges.</span><span class="sxs-lookup"><span data-stu-id="d1331-109">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="d1331-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="d1331-110">Attributes</span></span>

<span data-ttu-id="d1331-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="d1331-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d1331-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="d1331-112">Child Elements</span></span>

|<span data-ttu-id="d1331-113">Element</span><span class="sxs-lookup"><span data-stu-id="d1331-113">Element</span></span>|<span data-ttu-id="d1331-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d1331-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d1331-115">CustomEntry Element för CustomEntries för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="d1331-115">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="d1331-116">Element som krävs.</span><span class="sxs-lookup"><span data-stu-id="d1331-116">Required element.</span></span><br /><br /> <span data-ttu-id="d1331-117">Innehåller en definition av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="d1331-117">Provides a definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d1331-118">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="d1331-118">Parent Elements</span></span>

|<span data-ttu-id="d1331-119">Element</span><span class="sxs-lookup"><span data-stu-id="d1331-119">Element</span></span>|<span data-ttu-id="d1331-120">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d1331-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d1331-121">Anpassad kontroll Element för kontroll för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="d1331-121">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="d1331-122">Definierar den kontroll som används av vyn.</span><span class="sxs-lookup"><span data-stu-id="d1331-122">Defines the control used by the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d1331-123">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="d1331-123">Remarks</span></span>

<span data-ttu-id="d1331-124">I de flesta fall en kontroll har endast en definition som anges i en enda `CustomEntry` element.</span><span class="sxs-lookup"><span data-stu-id="d1331-124">In most cases, a control has only one definition, which is specified in a single `CustomEntry` element.</span></span> <span data-ttu-id="d1331-125">Det är dock möjligt att ange flera definitioner om du vill använda samma kontroll för att visa olika .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="d1331-125">However, it is possible to provide multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="d1331-126">I sådana fall kan du definiera en `CustomEntry` element för varje objekt eller en uppsättning objekt.</span><span class="sxs-lookup"><span data-stu-id="d1331-126">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="d1331-127">Se även</span><span class="sxs-lookup"><span data-stu-id="d1331-127">See Also</span></span>

[<span data-ttu-id="d1331-128">CustomEntry Element för CustomEntries för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="d1331-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="d1331-129">Anpassad kontroll Element för kontroll för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="d1331-129">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="d1331-130">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="d1331-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
