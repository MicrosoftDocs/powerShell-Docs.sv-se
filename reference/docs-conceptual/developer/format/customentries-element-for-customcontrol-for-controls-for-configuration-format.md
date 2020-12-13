---
ms.date: 09/13/2016
ms.topic: reference
title: CustomEntries-element för CustomControl för Controls för Configuration (format)
description: CustomEntries-element för CustomControl för Controls för Configuration (format)
ms.openlocfilehash: 86c2b517d0d7075a355a3190a14e25d9dd4fe374
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655393"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-configuration-format"></a><span data-ttu-id="48879-103">CustomEntries-element för CustomControl för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="48879-103">CustomEntries Element for CustomControl for Controls for Configuration (Format)</span></span>

<span data-ttu-id="48879-104">Innehåller definitionerna för en gemensam kontroll.</span><span class="sxs-lookup"><span data-stu-id="48879-104">Provides the definitions of a common control.</span></span> <span data-ttu-id="48879-105">Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.</span><span class="sxs-lookup"><span data-stu-id="48879-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="48879-106">Konfigurations element (format) styr element i konfigurations-(format)-kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="48879-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="48879-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="48879-107">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="48879-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="48879-108">Attributes and Elements</span></span>

<span data-ttu-id="48879-109">I följande avsnitt beskrivs attribut, underordnade element och `CustomEntries` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="48879-109">The following sections describe attributes, child elements, and the parent element of the `CustomEntries` element.</span></span> <span data-ttu-id="48879-110">Du måste ange ett eller flera underordnade element.</span><span class="sxs-lookup"><span data-stu-id="48879-110">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="48879-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="48879-111">Attributes</span></span>

<span data-ttu-id="48879-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="48879-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="48879-113">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="48879-113">Child Elements</span></span>

|<span data-ttu-id="48879-114">Element</span><span class="sxs-lookup"><span data-stu-id="48879-114">Element</span></span>|<span data-ttu-id="48879-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="48879-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="48879-116">CustomEntry-element för CustomControl för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="48879-116">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="48879-117">Ger en definition av den gemensamma kontrollen.</span><span class="sxs-lookup"><span data-stu-id="48879-117">Provides a definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="48879-118">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="48879-118">Parent Elements</span></span>

|<span data-ttu-id="48879-119">Element</span><span class="sxs-lookup"><span data-stu-id="48879-119">Element</span></span>|<span data-ttu-id="48879-120">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="48879-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="48879-121">CustomControl-element för kontroll av konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="48879-121">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="48879-122">Definierar en gemensam kontroll.</span><span class="sxs-lookup"><span data-stu-id="48879-122">Defines a common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="48879-123">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="48879-123">Remarks</span></span>

<span data-ttu-id="48879-124">I de flesta fall har en kontroll bara en definition som definieras i ett enda `CustomEntry` element.</span><span class="sxs-lookup"><span data-stu-id="48879-124">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="48879-125">Det är dock möjligt att ha flera definitioner om du vill använda samma kontroll för att visa olika .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="48879-125">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="48879-126">I dessa fall kan du definiera ett- `CustomEntry` element för varje objekt eller uppsättning objekt.</span><span class="sxs-lookup"><span data-stu-id="48879-126">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="48879-127">Se även</span><span class="sxs-lookup"><span data-stu-id="48879-127">See Also</span></span>

[<span data-ttu-id="48879-128">CustomControl-element för kontroll av konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="48879-128">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="48879-129">CustomEntry-element för CustomControl för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="48879-129">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="48879-130">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="48879-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
