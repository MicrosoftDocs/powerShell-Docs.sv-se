---
title: CustomEntries-element för CustomControl for GroupBy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 2221d1bb94159697ff10466e4606d6d54e117e30
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785956"
---
# <a name="customentries-element-for-customcontrol-for-groupby-format"></a><span data-ttu-id="d51d7-102">CustomEntries-element för CustomControl för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="d51d7-102">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

<span data-ttu-id="d51d7-103">Innehåller definitionerna för kontrollen.</span><span class="sxs-lookup"><span data-stu-id="d51d7-103">Provides the definitions for the control.</span></span> <span data-ttu-id="d51d7-104">Det här elementet används när du definierar hur en ny grupp av objekt visas.</span><span class="sxs-lookup"><span data-stu-id="d51d7-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="d51d7-105">Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="d51d7-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d51d7-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="d51d7-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d51d7-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="d51d7-107">Attributes and Elements</span></span>

<span data-ttu-id="d51d7-108">I följande avsnitt beskrivs attribut, underordnade element och `CustomEntries` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="d51d7-108">The following sections describe attributes, child elements, and parent elements of the `CustomEntries` element.</span></span> <span data-ttu-id="d51d7-109">Det finns ingen övre gräns för antalet underordnade element som kan anges.</span><span class="sxs-lookup"><span data-stu-id="d51d7-109">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="d51d7-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="d51d7-110">Attributes</span></span>

<span data-ttu-id="d51d7-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="d51d7-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d51d7-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="d51d7-112">Child Elements</span></span>

|<span data-ttu-id="d51d7-113">Element</span><span class="sxs-lookup"><span data-stu-id="d51d7-113">Element</span></span>|<span data-ttu-id="d51d7-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d51d7-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d51d7-115">CustomEntry-element för CustomControl för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="d51d7-115">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="d51d7-116">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="d51d7-116">Required element.</span></span><br /><br /> <span data-ttu-id="d51d7-117">Ger en definition av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="d51d7-117">Provides a definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d51d7-118">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="d51d7-118">Parent Elements</span></span>

|<span data-ttu-id="d51d7-119">Element</span><span class="sxs-lookup"><span data-stu-id="d51d7-119">Element</span></span>|<span data-ttu-id="d51d7-120">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d51d7-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d51d7-121">CustomControl-element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="d51d7-121">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="d51d7-122">Definierar den anpassade kontrollen som visar den nya gruppen.</span><span class="sxs-lookup"><span data-stu-id="d51d7-122">Defines the custom control that displays the new group.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d51d7-123">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="d51d7-123">Remarks</span></span>

<span data-ttu-id="d51d7-124">I de flesta fall har en kontroll bara en definition som anges i ett enda `CustomEntry` element.</span><span class="sxs-lookup"><span data-stu-id="d51d7-124">In most cases, a control has only one definition, which is specified in a single `CustomEntry` element.</span></span> <span data-ttu-id="d51d7-125">Det är dock möjligt att tillhandahålla flera definitioner om du vill använda samma kontroll för att visa olika grupper.</span><span class="sxs-lookup"><span data-stu-id="d51d7-125">However, it is possible to provide multiple definitions if you want to use the same control to display different groups.</span></span> <span data-ttu-id="d51d7-126">I dessa fall kan du definiera ett- `CustomEntry` element för en grupp.</span><span class="sxs-lookup"><span data-stu-id="d51d7-126">In those cases, you can define a `CustomEntry` element for a group.</span></span>

## <a name="see-also"></a><span data-ttu-id="d51d7-127">Se även</span><span class="sxs-lookup"><span data-stu-id="d51d7-127">See Also</span></span>

[<span data-ttu-id="d51d7-128">CustomEntry-element för CustomEntries för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="d51d7-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="d51d7-129">CustomControl-element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="d51d7-129">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="d51d7-130">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="d51d7-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
