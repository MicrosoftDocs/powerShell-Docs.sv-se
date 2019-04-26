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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066676"
---
# <a name="customcontrol-element-for-view-format"></a><span data-ttu-id="09cd8-102">CustomControl-element för View (format)</span><span class="sxs-lookup"><span data-stu-id="09cd8-102">CustomControl Element for View (Format)</span></span>

<span data-ttu-id="09cd8-103">Definierar en anpassad kontroll format för vyn.</span><span class="sxs-lookup"><span data-stu-id="09cd8-103">Defines a custom control format for the view.</span></span>

<span data-ttu-id="09cd8-104">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) anpassad kontroll konfigurationselement (Format)</span><span class="sxs-lookup"><span data-stu-id="09cd8-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="09cd8-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="09cd8-105">Syntax</span></span>

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="09cd8-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="09cd8-106">Attributes and Elements</span></span>

<span data-ttu-id="09cd8-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `CustomControl` element.</span><span class="sxs-lookup"><span data-stu-id="09cd8-107">The following sections describe attributes, child elements, and the parent element of the `CustomControl` element.</span></span> <span data-ttu-id="09cd8-108">Du måste ange ett underordnat element.</span><span class="sxs-lookup"><span data-stu-id="09cd8-108">You must specify one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="09cd8-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="09cd8-109">Attributes</span></span>

<span data-ttu-id="09cd8-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="09cd8-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="09cd8-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="09cd8-111">Child Elements</span></span>

|<span data-ttu-id="09cd8-112">Element</span><span class="sxs-lookup"><span data-stu-id="09cd8-112">Element</span></span>|<span data-ttu-id="09cd8-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="09cd8-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="09cd8-114">CustomEntries Element för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="09cd8-114">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="09cd8-115">Element som krävs.</span><span class="sxs-lookup"><span data-stu-id="09cd8-115">Required element.</span></span><br /><br /> <span data-ttu-id="09cd8-116">Innehåller definitioner av vyn anpassad kontroll.</span><span class="sxs-lookup"><span data-stu-id="09cd8-116">Provides the definitions of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="09cd8-117">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="09cd8-117">Parent Elements</span></span>

|<span data-ttu-id="09cd8-118">Element</span><span class="sxs-lookup"><span data-stu-id="09cd8-118">Element</span></span>|<span data-ttu-id="09cd8-119">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="09cd8-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="09cd8-120">Visa Element (Format)</span><span class="sxs-lookup"><span data-stu-id="09cd8-120">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="09cd8-121">Definierar en vy som används för att visa en eller flera .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="09cd8-121">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="09cd8-122">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="09cd8-122">Remarks</span></span>

<span data-ttu-id="09cd8-123">Endast en definition som krävs för varje kontroll vy i de flesta fall, men det är möjligt att ange flera definitioner om du vill använda samma vy för att visa olika .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="09cd8-123">In most cases, only one definition is required for each control view, but it is possible to provide multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="09cd8-124">I sådana fall kan ange du en definition av separat för varje objekt eller en uppsättning objekt.</span><span class="sxs-lookup"><span data-stu-id="09cd8-124">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="09cd8-125">Se även</span><span class="sxs-lookup"><span data-stu-id="09cd8-125">See Also</span></span>

[<span data-ttu-id="09cd8-126">CustomEntries Element för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="09cd8-126">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)

[<span data-ttu-id="09cd8-127">Visa Element (Format)</span><span class="sxs-lookup"><span data-stu-id="09cd8-127">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="09cd8-128">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="09cd8-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
