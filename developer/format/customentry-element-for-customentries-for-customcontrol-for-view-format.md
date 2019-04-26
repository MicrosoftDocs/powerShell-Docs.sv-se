---
title: CustomEntry Element för CustomEntries för anpassad kontroll för vy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac3c0a25-f2ca-4e28-b3dc-9cb06a76d92a
caps.latest.revision: 11
ms.openlocfilehash: 7804155bffeb1f0df8339f797bf59f8def56a3fc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066455"
---
# <a name="customentry-element-for-customentries-for-customcontrol-for-view-format"></a><span data-ttu-id="98ad4-102">CustomEntry-element för CustomEntries för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="98ad4-102">CustomEntry Element for CustomEntries for CustomControl for View (Format)</span></span>

<span data-ttu-id="98ad4-103">Innehåller en definition av vyn anpassad kontroll.</span><span class="sxs-lookup"><span data-stu-id="98ad4-103">Provides a definition of the custom control view.</span></span>

<span data-ttu-id="98ad4-104">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) anpassad kontroll Element (Format) CustomEntries konfigurationselement för anpassad kontroll för Visa (Format) CustomEntry elementet för CustomEntries för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="98ad4-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="98ad4-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="98ad4-105">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="98ad4-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="98ad4-106">Attributes and Elements</span></span>

<span data-ttu-id="98ad4-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `CustomEntry` element.</span><span class="sxs-lookup"><span data-stu-id="98ad4-107">The following sections describe attributes, child elements, and the parent element of the `CustomEntry` element.</span></span> <span data-ttu-id="98ad4-108">Du måste ange objekt som visas av definitionen.</span><span class="sxs-lookup"><span data-stu-id="98ad4-108">You must specify the items displayed by the definition.</span></span>

### <a name="attributes"></a><span data-ttu-id="98ad4-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="98ad4-109">Attributes</span></span>

<span data-ttu-id="98ad4-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="98ad4-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="98ad4-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="98ad4-111">Child Elements</span></span>

|<span data-ttu-id="98ad4-112">Element</span><span class="sxs-lookup"><span data-stu-id="98ad4-112">Element</span></span>|<span data-ttu-id="98ad4-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="98ad4-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="98ad4-114">EntrySelectedBy Element för CustomEntry för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="98ad4-114">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="98ad4-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="98ad4-115">Optional element.</span></span><br /><br /> <span data-ttu-id="98ad4-116">Definierar vilka typer av .NET som använder definitionen av den anpassade kontroll vyn eller ett villkor som måste finnas för den här definitionen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="98ad4-116">Defines the .NET types that use the definition of the custom control view or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="98ad4-117">CustomItem Element för CustomEntry för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="98ad4-117">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="98ad4-118">Definierar en kontroll för den anpassade kontroll-definitionen.</span><span class="sxs-lookup"><span data-stu-id="98ad4-118">Defines a control for the custom control definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="98ad4-119">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="98ad4-119">Parent Elements</span></span>

|<span data-ttu-id="98ad4-120">Element</span><span class="sxs-lookup"><span data-stu-id="98ad4-120">Element</span></span>|<span data-ttu-id="98ad4-121">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="98ad4-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="98ad4-122">CustomEntries Element för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="98ad4-122">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="98ad4-123">Innehåller definitioner av vyn anpassad kontroll.</span><span class="sxs-lookup"><span data-stu-id="98ad4-123">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="98ad4-124">Den anpassade kontroll vyn måste ange en eller flera definitioner.</span><span class="sxs-lookup"><span data-stu-id="98ad4-124">The custom control view must specify one or more definitions.</span></span>|

## <a name="remarks"></a><span data-ttu-id="98ad4-125">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="98ad4-125">Remarks</span></span>

<span data-ttu-id="98ad4-126">Endast en definition som krävs för varje anpassad kontroll vy i de flesta fall, men det är möjligt att ha flera definitioner om du vill använda samma vy för att visa olika .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="98ad4-126">In most cases, only one definition is required for each custom control view, but it is possible to have multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="98ad4-127">I sådana fall kan ange du en definition av separat för varje objekt eller en uppsättning objekt.</span><span class="sxs-lookup"><span data-stu-id="98ad4-127">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="98ad4-128">Se även</span><span class="sxs-lookup"><span data-stu-id="98ad4-128">See Also</span></span>

[<span data-ttu-id="98ad4-129">Anpassad kontroll Element för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="98ad4-129">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="98ad4-130">CustomItem Element för CustomEntry för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="98ad4-130">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="98ad4-131">EntrySelectedBy Element för CustomEntry för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="98ad4-131">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="98ad4-132">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="98ad4-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
