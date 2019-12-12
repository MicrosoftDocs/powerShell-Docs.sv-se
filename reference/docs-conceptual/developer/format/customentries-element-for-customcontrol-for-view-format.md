---
title: CustomEntries-element för CustomControl för vy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb412831-94f7-4054-b19e-32c1b14c66dd
caps.latest.revision: 11
ms.openlocfilehash: 827baacd22ef258dd9b0c8a383a23fce7d975f7f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355281"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a><span data-ttu-id="c30ae-102">CustomEntries-element för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="c30ae-102">CustomEntries Element for CustomControl for View (Format)</span></span>

<span data-ttu-id="c30ae-103">Innehåller definitionerna för vyn anpassad kontroll.</span><span class="sxs-lookup"><span data-stu-id="c30ae-103">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="c30ae-104">Vyn anpassad kontroll måste ange en eller flera definitioner.</span><span class="sxs-lookup"><span data-stu-id="c30ae-104">The custom control view must specify one or more definitions.</span></span>

<span data-ttu-id="c30ae-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) CustomControl-element (format) element (format) CustomEntries-element för CustomControl för vy (format)</span><span class="sxs-lookup"><span data-stu-id="c30ae-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c30ae-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="c30ae-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c30ae-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="c30ae-107">Attributes and Elements</span></span>

<span data-ttu-id="c30ae-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `CustomControlEntries`-elementet.</span><span class="sxs-lookup"><span data-stu-id="c30ae-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlEntries` element.</span></span> <span data-ttu-id="c30ae-109">Du måste ange ett eller flera underordnade element.</span><span class="sxs-lookup"><span data-stu-id="c30ae-109">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="c30ae-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="c30ae-110">Attributes</span></span>

<span data-ttu-id="c30ae-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="c30ae-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c30ae-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="c30ae-112">Child Elements</span></span>

|<span data-ttu-id="c30ae-113">Element</span><span class="sxs-lookup"><span data-stu-id="c30ae-113">Element</span></span>|<span data-ttu-id="c30ae-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c30ae-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c30ae-115">CustomEntry-element för CustomEntries för vy (format)</span><span class="sxs-lookup"><span data-stu-id="c30ae-115">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="c30ae-116">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="c30ae-116">Required element.</span></span><br /><br /> <span data-ttu-id="c30ae-117">Innehåller en definition av den anpassade kontrollen.</span><span class="sxs-lookup"><span data-stu-id="c30ae-117">Provides a definition of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c30ae-118">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="c30ae-118">Parent Elements</span></span>

|<span data-ttu-id="c30ae-119">Element</span><span class="sxs-lookup"><span data-stu-id="c30ae-119">Element</span></span>|<span data-ttu-id="c30ae-120">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c30ae-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c30ae-121">CustomControl-element för vy (format)</span><span class="sxs-lookup"><span data-stu-id="c30ae-121">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)|<span data-ttu-id="c30ae-122">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="c30ae-122">Required element.</span></span><br /><br /> <span data-ttu-id="c30ae-123">Definierar ett anpassat kontroll format för vyn.</span><span class="sxs-lookup"><span data-stu-id="c30ae-123">Defines a custom control format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c30ae-124">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="c30ae-124">Remarks</span></span>

<span data-ttu-id="c30ae-125">I de flesta fall har en kontroll bara en definition som definieras i ett enda `CustomEntry`-element.</span><span class="sxs-lookup"><span data-stu-id="c30ae-125">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="c30ae-126">Det är dock möjligt att ha flera definitioner om du vill använda samma kontroll för att visa olika .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="c30ae-126">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="c30ae-127">I dessa fall kan du definiera ett `CustomEntry`-element för varje objekt eller uppsättning objekt.</span><span class="sxs-lookup"><span data-stu-id="c30ae-127">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="c30ae-128">Se även</span><span class="sxs-lookup"><span data-stu-id="c30ae-128">See Also</span></span>

[<span data-ttu-id="c30ae-129">CustomControl-element för vy (format)</span><span class="sxs-lookup"><span data-stu-id="c30ae-129">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="c30ae-130">CustomEntry-element för CustomEntries för vy (format)</span><span class="sxs-lookup"><span data-stu-id="c30ae-130">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="c30ae-131">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="c30ae-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
