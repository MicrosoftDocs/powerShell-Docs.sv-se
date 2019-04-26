---
title: CustomEntries Element för anpassad kontroll för vy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb412831-94f7-4054-b19e-32c1b14c66dd
caps.latest.revision: 11
ms.openlocfilehash: 827baacd22ef258dd9b0c8a383a23fce7d975f7f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066523"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a><span data-ttu-id="7d272-102">CustomEntries-element för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="7d272-102">CustomEntries Element for CustomControl for View (Format)</span></span>

<span data-ttu-id="7d272-103">Innehåller definitioner av vyn anpassad kontroll.</span><span class="sxs-lookup"><span data-stu-id="7d272-103">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="7d272-104">Den anpassade kontroll vyn måste ange en eller flera definitioner.</span><span class="sxs-lookup"><span data-stu-id="7d272-104">The custom control view must specify one or more definitions.</span></span>

<span data-ttu-id="7d272-105">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) anpassad kontroll Element (Format) CustomEntries konfigurationselement för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="7d272-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7d272-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="7d272-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7d272-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="7d272-107">Attributes and Elements</span></span>

<span data-ttu-id="7d272-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `CustomControlEntries` element.</span><span class="sxs-lookup"><span data-stu-id="7d272-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlEntries` element.</span></span> <span data-ttu-id="7d272-109">Du måste ange en eller flera underordnade element.</span><span class="sxs-lookup"><span data-stu-id="7d272-109">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="7d272-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="7d272-110">Attributes</span></span>

<span data-ttu-id="7d272-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="7d272-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7d272-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="7d272-112">Child Elements</span></span>

|<span data-ttu-id="7d272-113">Element</span><span class="sxs-lookup"><span data-stu-id="7d272-113">Element</span></span>|<span data-ttu-id="7d272-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d272-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7d272-115">CustomEntry Element för CustomEntries för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="7d272-115">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="7d272-116">Element som krävs.</span><span class="sxs-lookup"><span data-stu-id="7d272-116">Required element.</span></span><br /><br /> <span data-ttu-id="7d272-117">Innehåller en definition av vyn anpassad kontroll.</span><span class="sxs-lookup"><span data-stu-id="7d272-117">Provides a definition of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7d272-118">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="7d272-118">Parent Elements</span></span>

|<span data-ttu-id="7d272-119">Element</span><span class="sxs-lookup"><span data-stu-id="7d272-119">Element</span></span>|<span data-ttu-id="7d272-120">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d272-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7d272-121">Anpassad kontroll Element för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="7d272-121">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)|<span data-ttu-id="7d272-122">Element som krävs.</span><span class="sxs-lookup"><span data-stu-id="7d272-122">Required element.</span></span><br /><br /> <span data-ttu-id="7d272-123">Definierar en anpassad kontroll format för vyn.</span><span class="sxs-lookup"><span data-stu-id="7d272-123">Defines a custom control format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7d272-124">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="7d272-124">Remarks</span></span>

<span data-ttu-id="7d272-125">I de flesta fall en kontroll har endast en definition som definieras i en enda `CustomEntry` element.</span><span class="sxs-lookup"><span data-stu-id="7d272-125">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="7d272-126">Det är dock möjligt att ha flera definitioner om du vill använda samma kontroll för att visa olika .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="7d272-126">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="7d272-127">I sådana fall kan du definiera en `CustomEntry` element för varje objekt eller en uppsättning objekt.</span><span class="sxs-lookup"><span data-stu-id="7d272-127">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="7d272-128">Se även</span><span class="sxs-lookup"><span data-stu-id="7d272-128">See Also</span></span>

[<span data-ttu-id="7d272-129">Anpassad kontroll Element för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="7d272-129">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="7d272-130">CustomEntry Element för CustomEntries för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="7d272-130">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="7d272-131">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="7d272-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
