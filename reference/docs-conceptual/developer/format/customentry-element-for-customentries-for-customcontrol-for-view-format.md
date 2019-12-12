---
title: CustomEntry-element för CustomEntries för CustomControl för View (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac3c0a25-f2ca-4e28-b3dc-9cb06a76d92a
caps.latest.revision: 11
ms.openlocfilehash: 7804155bffeb1f0df8339f797bf59f8def56a3fc
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355239"
---
# <a name="customentry-element-for-customentries-for-customcontrol-for-view-format"></a><span data-ttu-id="3633d-102">CustomEntry-element för CustomEntries för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="3633d-102">CustomEntry Element for CustomEntries for CustomControl for View (Format)</span></span>

<span data-ttu-id="3633d-103">Innehåller en definition av den anpassade kontrollen.</span><span class="sxs-lookup"><span data-stu-id="3633d-103">Provides a definition of the custom control view.</span></span>

<span data-ttu-id="3633d-104">Konfigurations element (format) ViewDefinitions element (format) View element (format) CustomControl element (format) CustomEntries-element för CustomControl för View (format) CustomEntry-element för CustomEntries för vy (format)</span><span class="sxs-lookup"><span data-stu-id="3633d-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3633d-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="3633d-105">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3633d-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="3633d-106">Attributes and Elements</span></span>

<span data-ttu-id="3633d-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `CustomEntry`-elementet.</span><span class="sxs-lookup"><span data-stu-id="3633d-107">The following sections describe attributes, child elements, and the parent element of the `CustomEntry` element.</span></span> <span data-ttu-id="3633d-108">Du måste ange de objekt som ska visas av definitionen.</span><span class="sxs-lookup"><span data-stu-id="3633d-108">You must specify the items displayed by the definition.</span></span>

### <a name="attributes"></a><span data-ttu-id="3633d-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="3633d-109">Attributes</span></span>

<span data-ttu-id="3633d-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="3633d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3633d-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="3633d-111">Child Elements</span></span>

|<span data-ttu-id="3633d-112">Element</span><span class="sxs-lookup"><span data-stu-id="3633d-112">Element</span></span>|<span data-ttu-id="3633d-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="3633d-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3633d-114">EntrySelectedBy-element för CustomEntry för vy (format)</span><span class="sxs-lookup"><span data-stu-id="3633d-114">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="3633d-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="3633d-115">Optional element.</span></span><br /><br /> <span data-ttu-id="3633d-116">Definierar de .NET-typer som använder definitionen av den anpassade kontrollen eller det villkor som måste finnas för att den här definitionen ska användas.</span><span class="sxs-lookup"><span data-stu-id="3633d-116">Defines the .NET types that use the definition of the custom control view or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="3633d-117">CustomItem-element för CustomEntry för vy (format)</span><span class="sxs-lookup"><span data-stu-id="3633d-117">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="3633d-118">Definierar en kontroll för definitionen av den anpassade kontrollen.</span><span class="sxs-lookup"><span data-stu-id="3633d-118">Defines a control for the custom control definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3633d-119">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="3633d-119">Parent Elements</span></span>

|<span data-ttu-id="3633d-120">Element</span><span class="sxs-lookup"><span data-stu-id="3633d-120">Element</span></span>|<span data-ttu-id="3633d-121">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="3633d-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3633d-122">CustomEntries-element för CustomControl för vy (format)</span><span class="sxs-lookup"><span data-stu-id="3633d-122">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="3633d-123">Innehåller definitionerna för vyn anpassad kontroll.</span><span class="sxs-lookup"><span data-stu-id="3633d-123">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="3633d-124">Vyn anpassad kontroll måste ange en eller flera definitioner.</span><span class="sxs-lookup"><span data-stu-id="3633d-124">The custom control view must specify one or more definitions.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3633d-125">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="3633d-125">Remarks</span></span>

<span data-ttu-id="3633d-126">I de flesta fall krävs bara en definition för varje anpassad kontroll, men det är möjligt att ha flera definitioner om du vill använda samma vy för att visa olika .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="3633d-126">In most cases, only one definition is required for each custom control view, but it is possible to have multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="3633d-127">I dessa fall kan du ange en separat definition för varje objekt eller uppsättning objekt.</span><span class="sxs-lookup"><span data-stu-id="3633d-127">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="3633d-128">Se även</span><span class="sxs-lookup"><span data-stu-id="3633d-128">See Also</span></span>

[<span data-ttu-id="3633d-129">CustomControl-element för vy (format)</span><span class="sxs-lookup"><span data-stu-id="3633d-129">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="3633d-130">CustomItem-element för CustomEntry för vy (format)</span><span class="sxs-lookup"><span data-stu-id="3633d-130">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="3633d-131">EntrySelectedBy-element för CustomEntry för vy (format)</span><span class="sxs-lookup"><span data-stu-id="3633d-131">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="3633d-132">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="3633d-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
