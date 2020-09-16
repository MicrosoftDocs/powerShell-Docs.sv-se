---
title: CustomEntries-element för CustomControl för vy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c89eb25f6922a92e2c18298d0128c4c2ca93df3d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785973"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a><span data-ttu-id="ca2a0-102">CustomEntries-element för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="ca2a0-102">CustomEntries Element for CustomControl for View (Format)</span></span>

<span data-ttu-id="ca2a0-103">Innehåller definitionerna för vyn anpassad kontroll.</span><span class="sxs-lookup"><span data-stu-id="ca2a0-103">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="ca2a0-104">Vyn anpassad kontroll måste ange en eller flera definitioner.</span><span class="sxs-lookup"><span data-stu-id="ca2a0-104">The custom control view must specify one or more definitions.</span></span>

<span data-ttu-id="ca2a0-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) CustomControl-element (format) element (format) CustomEntries-element för CustomControl för vy (format)</span><span class="sxs-lookup"><span data-stu-id="ca2a0-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ca2a0-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="ca2a0-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ca2a0-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="ca2a0-107">Attributes and Elements</span></span>

<span data-ttu-id="ca2a0-108">I följande avsnitt beskrivs attribut, underordnade element och `CustomControlEntries` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="ca2a0-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlEntries` element.</span></span> <span data-ttu-id="ca2a0-109">Du måste ange ett eller flera underordnade element.</span><span class="sxs-lookup"><span data-stu-id="ca2a0-109">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="ca2a0-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="ca2a0-110">Attributes</span></span>

<span data-ttu-id="ca2a0-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="ca2a0-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ca2a0-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="ca2a0-112">Child Elements</span></span>

|<span data-ttu-id="ca2a0-113">Element</span><span class="sxs-lookup"><span data-stu-id="ca2a0-113">Element</span></span>|<span data-ttu-id="ca2a0-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ca2a0-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ca2a0-115">CustomEntry-element för CustomEntries för vy (format)</span><span class="sxs-lookup"><span data-stu-id="ca2a0-115">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="ca2a0-116">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="ca2a0-116">Required element.</span></span><br /><br /> <span data-ttu-id="ca2a0-117">Innehåller en definition av den anpassade kontrollen.</span><span class="sxs-lookup"><span data-stu-id="ca2a0-117">Provides a definition of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ca2a0-118">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="ca2a0-118">Parent Elements</span></span>

|<span data-ttu-id="ca2a0-119">Element</span><span class="sxs-lookup"><span data-stu-id="ca2a0-119">Element</span></span>|<span data-ttu-id="ca2a0-120">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ca2a0-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ca2a0-121">CustomControl-element för View (format)</span><span class="sxs-lookup"><span data-stu-id="ca2a0-121">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)|<span data-ttu-id="ca2a0-122">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="ca2a0-122">Required element.</span></span><br /><br /> <span data-ttu-id="ca2a0-123">Definierar ett anpassat kontroll format för vyn.</span><span class="sxs-lookup"><span data-stu-id="ca2a0-123">Defines a custom control format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ca2a0-124">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="ca2a0-124">Remarks</span></span>

<span data-ttu-id="ca2a0-125">I de flesta fall har en kontroll bara en definition som definieras i ett enda `CustomEntry` element.</span><span class="sxs-lookup"><span data-stu-id="ca2a0-125">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="ca2a0-126">Det är dock möjligt att ha flera definitioner om du vill använda samma kontroll för att visa olika .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="ca2a0-126">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="ca2a0-127">I dessa fall kan du definiera ett- `CustomEntry` element för varje objekt eller uppsättning objekt.</span><span class="sxs-lookup"><span data-stu-id="ca2a0-127">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="ca2a0-128">Se även</span><span class="sxs-lookup"><span data-stu-id="ca2a0-128">See Also</span></span>

[<span data-ttu-id="ca2a0-129">CustomControl-element för View (format)</span><span class="sxs-lookup"><span data-stu-id="ca2a0-129">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="ca2a0-130">CustomEntry-element för CustomEntries för vy (format)</span><span class="sxs-lookup"><span data-stu-id="ca2a0-130">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="ca2a0-131">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="ca2a0-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
