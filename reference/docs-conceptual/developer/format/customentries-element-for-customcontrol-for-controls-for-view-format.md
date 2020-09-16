---
title: CustomEntries-element för CustomControl för kontroller för vy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: a52bd2368044c34a0b73da331785d55597e30260
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783712"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-view-format"></a><span data-ttu-id="b5caf-102">CustomEntries-element för CustomControl för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="b5caf-102">CustomEntries Element for CustomControl for Controls for View (Format)</span></span>

<span data-ttu-id="b5caf-103">Innehåller definitionerna för kontrollen.</span><span class="sxs-lookup"><span data-stu-id="b5caf-103">Provides the definitions for the control.</span></span> <span data-ttu-id="b5caf-104">Det här elementet används när du definierar kontroller som kan användas av en vy.</span><span class="sxs-lookup"><span data-stu-id="b5caf-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="b5caf-105">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) styr element (format) kontroll element (format) styr element (format) kontroll element för Controls för View (format) CustomControl-element för kontroll för kontroller för View (format) CustomEntries-element för CustomControl för kontroller (format)</span><span class="sxs-lookup"><span data-stu-id="b5caf-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b5caf-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="b5caf-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b5caf-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="b5caf-107">Attributes and Elements</span></span>

<span data-ttu-id="b5caf-108">I följande avsnitt beskrivs attribut, underordnade element och `CustomEntries` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="b5caf-108">The following sections describe attributes, child elements, and parent elements of the `CustomEntries` element.</span></span> <span data-ttu-id="b5caf-109">Det finns ingen övre gräns för antalet underordnade element som kan anges.</span><span class="sxs-lookup"><span data-stu-id="b5caf-109">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="b5caf-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="b5caf-110">Attributes</span></span>

<span data-ttu-id="b5caf-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="b5caf-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b5caf-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="b5caf-112">Child Elements</span></span>

|<span data-ttu-id="b5caf-113">Element</span><span class="sxs-lookup"><span data-stu-id="b5caf-113">Element</span></span>|<span data-ttu-id="b5caf-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b5caf-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b5caf-115">CustomEntry-element för CustomEntries för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="b5caf-115">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="b5caf-116">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="b5caf-116">Required element.</span></span><br /><br /> <span data-ttu-id="b5caf-117">Ger en definition av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="b5caf-117">Provides a definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b5caf-118">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="b5caf-118">Parent Elements</span></span>

|<span data-ttu-id="b5caf-119">Element</span><span class="sxs-lookup"><span data-stu-id="b5caf-119">Element</span></span>|<span data-ttu-id="b5caf-120">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b5caf-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b5caf-121">CustomControl-element för Control för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="b5caf-121">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="b5caf-122">Definierar den kontroll som används i vyn.</span><span class="sxs-lookup"><span data-stu-id="b5caf-122">Defines the control used by the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b5caf-123">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="b5caf-123">Remarks</span></span>

<span data-ttu-id="b5caf-124">I de flesta fall har en kontroll bara en definition som anges i ett enda `CustomEntry` element.</span><span class="sxs-lookup"><span data-stu-id="b5caf-124">In most cases, a control has only one definition, which is specified in a single `CustomEntry` element.</span></span> <span data-ttu-id="b5caf-125">Det är dock möjligt att tillhandahålla flera definitioner om du vill använda samma kontroll för att visa olika .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="b5caf-125">However, it is possible to provide multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="b5caf-126">I dessa fall kan du definiera ett- `CustomEntry` element för varje objekt eller uppsättning objekt.</span><span class="sxs-lookup"><span data-stu-id="b5caf-126">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="b5caf-127">Se även</span><span class="sxs-lookup"><span data-stu-id="b5caf-127">See Also</span></span>

[<span data-ttu-id="b5caf-128">CustomEntry-element för CustomEntries för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="b5caf-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="b5caf-129">CustomControl-element för Control för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="b5caf-129">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="b5caf-130">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="b5caf-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
