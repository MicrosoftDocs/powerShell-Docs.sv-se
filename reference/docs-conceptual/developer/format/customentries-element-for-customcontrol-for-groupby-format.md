---
title: CustomEntries-element för CustomControl for GroupBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af83c0f6-7fdd-4aa0-af12-efc62f632974
caps.latest.revision: 7
ms.openlocfilehash: f073142bf836ae892f161cf8c36ed16c35e311f5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355288"
---
# <a name="customentries-element-for-customcontrol-for-groupby-format"></a><span data-ttu-id="7d9ca-102">CustomEntries-element för CustomControl för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="7d9ca-102">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

<span data-ttu-id="7d9ca-103">Innehåller definitionerna för kontrollen.</span><span class="sxs-lookup"><span data-stu-id="7d9ca-103">Provides the definitions for the control.</span></span> <span data-ttu-id="7d9ca-104">Det här elementet används när du definierar hur en ny grupp av objekt visas.</span><span class="sxs-lookup"><span data-stu-id="7d9ca-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="7d9ca-105">Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="7d9ca-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7d9ca-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="7d9ca-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7d9ca-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="7d9ca-107">Attributes and Elements</span></span>

<span data-ttu-id="7d9ca-108">I följande avsnitt beskrivs attribut, underordnade element och överordnade element i `CustomEntries`-elementet.</span><span class="sxs-lookup"><span data-stu-id="7d9ca-108">The following sections describe attributes, child elements, and parent elements of the `CustomEntries` element.</span></span> <span data-ttu-id="7d9ca-109">Det finns ingen övre gräns för antalet underordnade element som kan anges.</span><span class="sxs-lookup"><span data-stu-id="7d9ca-109">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="7d9ca-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="7d9ca-110">Attributes</span></span>

<span data-ttu-id="7d9ca-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="7d9ca-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7d9ca-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="7d9ca-112">Child Elements</span></span>

|<span data-ttu-id="7d9ca-113">Element</span><span class="sxs-lookup"><span data-stu-id="7d9ca-113">Element</span></span>|<span data-ttu-id="7d9ca-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d9ca-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7d9ca-115">CustomEntry-element för CustomControl för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="7d9ca-115">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="7d9ca-116">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="7d9ca-116">Required element.</span></span><br /><br /> <span data-ttu-id="7d9ca-117">Ger en definition av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="7d9ca-117">Provides a definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7d9ca-118">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="7d9ca-118">Parent Elements</span></span>

|<span data-ttu-id="7d9ca-119">Element</span><span class="sxs-lookup"><span data-stu-id="7d9ca-119">Element</span></span>|<span data-ttu-id="7d9ca-120">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d9ca-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7d9ca-121">CustomControl-element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="7d9ca-121">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="7d9ca-122">Definierar den anpassade kontrollen som visar den nya gruppen.</span><span class="sxs-lookup"><span data-stu-id="7d9ca-122">Defines the custom control that displays the new group.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7d9ca-123">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="7d9ca-123">Remarks</span></span>

<span data-ttu-id="7d9ca-124">I de flesta fall har en kontroll bara en definition som anges i ett enda `CustomEntry`-element.</span><span class="sxs-lookup"><span data-stu-id="7d9ca-124">In most cases, a control has only one definition, which is specified in a single `CustomEntry` element.</span></span> <span data-ttu-id="7d9ca-125">Det är dock möjligt att tillhandahålla flera definitioner om du vill använda samma kontroll för att visa olika grupper.</span><span class="sxs-lookup"><span data-stu-id="7d9ca-125">However, it is possible to provide multiple definitions if you want to use the same control to display different groups.</span></span> <span data-ttu-id="7d9ca-126">I dessa fall kan du definiera ett `CustomEntry`-element för en grupp.</span><span class="sxs-lookup"><span data-stu-id="7d9ca-126">In those cases, you can define a `CustomEntry` element for a group.</span></span>

## <a name="see-also"></a><span data-ttu-id="7d9ca-127">Se även</span><span class="sxs-lookup"><span data-stu-id="7d9ca-127">See Also</span></span>

[<span data-ttu-id="7d9ca-128">CustomEntry-element för CustomEntries för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="7d9ca-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="7d9ca-129">CustomControl-element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="7d9ca-129">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="7d9ca-130">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="7d9ca-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
