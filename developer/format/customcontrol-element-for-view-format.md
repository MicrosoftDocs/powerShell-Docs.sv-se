---
title: Anpassad kontroll Element för vy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2edac16c-0b30-4985-ac84-0821aa9a9f6d
caps.latest.revision: 12
ms.openlocfilehash: bd0f7ca4de8dede97d1553cd62884ea45876e0c7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850493"
---
# <a name="customcontrol-element-for-view-format"></a><span data-ttu-id="c8530-102">CustomControl-element för View (format)</span><span class="sxs-lookup"><span data-stu-id="c8530-102">CustomControl Element for View (Format)</span></span>

<span data-ttu-id="c8530-103">Definierar en anpassad kontroll format för vyn.</span><span class="sxs-lookup"><span data-stu-id="c8530-103">Defines a custom control format for the view.</span></span>

<span data-ttu-id="c8530-104">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) anpassad kontroll konfigurationselement (Format)</span><span class="sxs-lookup"><span data-stu-id="c8530-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c8530-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="c8530-105">Syntax</span></span>

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c8530-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="c8530-106">Attributes and Elements</span></span>

<span data-ttu-id="c8530-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `CustomControl` element.</span><span class="sxs-lookup"><span data-stu-id="c8530-107">The following sections describe attributes, child elements, and the parent element of the `CustomControl` element.</span></span> <span data-ttu-id="c8530-108">Du måste ange ett underordnat element.</span><span class="sxs-lookup"><span data-stu-id="c8530-108">You must specify one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c8530-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="c8530-109">Attributes</span></span>

<span data-ttu-id="c8530-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="c8530-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c8530-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="c8530-111">Child Elements</span></span>

|<span data-ttu-id="c8530-112">Element</span><span class="sxs-lookup"><span data-stu-id="c8530-112">Element</span></span>|<span data-ttu-id="c8530-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c8530-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c8530-114">CustomEntries Element för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="c8530-114">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="c8530-115">Element som krävs.</span><span class="sxs-lookup"><span data-stu-id="c8530-115">Required element.</span></span><br /><br /> <span data-ttu-id="c8530-116">Innehåller definitioner av vyn anpassad kontroll.</span><span class="sxs-lookup"><span data-stu-id="c8530-116">Provides the definitions of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c8530-117">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="c8530-117">Parent Elements</span></span>

|<span data-ttu-id="c8530-118">Element</span><span class="sxs-lookup"><span data-stu-id="c8530-118">Element</span></span>|<span data-ttu-id="c8530-119">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c8530-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c8530-120">Visa Element (Format)</span><span class="sxs-lookup"><span data-stu-id="c8530-120">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="c8530-121">Definierar en vy som används för att visa en eller flera .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="c8530-121">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c8530-122">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="c8530-122">Remarks</span></span>

<span data-ttu-id="c8530-123">Endast en definition som krävs för varje kontroll vy i de flesta fall, men det är möjligt att ange flera definitioner om du vill använda samma vy för att visa olika .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="c8530-123">In most cases, only one definition is required for each control view, but it is possible to provide multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="c8530-124">I sådana fall kan ange du en definition av separat för varje objekt eller en uppsättning objekt.</span><span class="sxs-lookup"><span data-stu-id="c8530-124">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="c8530-125">Se även</span><span class="sxs-lookup"><span data-stu-id="c8530-125">See Also</span></span>

[<span data-ttu-id="c8530-126">CustomEntries Element för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="c8530-126">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)

[<span data-ttu-id="c8530-127">Visa Element (Format)</span><span class="sxs-lookup"><span data-stu-id="c8530-127">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="c8530-128">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="c8530-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
