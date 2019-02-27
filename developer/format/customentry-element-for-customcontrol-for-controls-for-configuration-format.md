---
title: CustomEntry Element för anpassad kontroll för kontroller för konfiguration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9dfba86f-29b2-473c-9e98-9d679176acce
caps.latest.revision: 11
ms.openlocfilehash: 497485a388d1cdc834ecc1d1079b0714a7d7f9db
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849478"
---
# <a name="customentry-element-for-customcontrol-for-controls-for-configuration-format"></a><span data-ttu-id="9e004-102">CustomEntry-element för CustomControl för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="9e004-102">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>

<span data-ttu-id="9e004-103">Innehåller en definition av vanliga kontrollen.</span><span class="sxs-lookup"><span data-stu-id="9e004-103">Provides a definition of the common control.</span></span> <span data-ttu-id="9e004-104">Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.</span><span class="sxs-lookup"><span data-stu-id="9e004-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="9e004-105">Konfigurationselementet Element (Format) kontroller av (Format) kontroll konfigurationselement för kontroller för (Format) anpassad kontroll konfigurationselement för kontroll för (Format) CustomEntries konfigurationselement för anpassad kontroll för konfiguration ( Format) CustomEntry Element för anpassad kontroll för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="9e004-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9e004-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="9e004-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="9e004-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="9e004-107">Attributes and Elements</span></span>

<span data-ttu-id="9e004-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `CustomEntry` element.</span><span class="sxs-lookup"><span data-stu-id="9e004-108">The following sections describe attributes, child elements, and the parent element of the `CustomEntry` element.</span></span> <span data-ttu-id="9e004-109">Du måste ange objekt som visas av definitionen.</span><span class="sxs-lookup"><span data-stu-id="9e004-109">You must specify the items displayed by the definition.</span></span>

### <a name="attributes"></a><span data-ttu-id="9e004-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="9e004-110">Attributes</span></span>

<span data-ttu-id="9e004-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="9e004-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9e004-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="9e004-112">Child Elements</span></span>

|<span data-ttu-id="9e004-113">Element</span><span class="sxs-lookup"><span data-stu-id="9e004-113">Element</span></span>|<span data-ttu-id="9e004-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="9e004-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9e004-115">EntrySelectedBy Element för CustomEntry för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="9e004-115">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="9e004-116">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="9e004-116">Optional element.</span></span><br /><br /> <span data-ttu-id="9e004-117">Definierar vilka typer av .NET som använder definitionen av den vanliga kontrollen eller villkor som måste finnas för den här kontrollen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="9e004-117">Defines the .NET types that use the definition of the common control or the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="9e004-118">CustomItem Element för CustomEntry för kontroller för konfiguration</span><span class="sxs-lookup"><span data-stu-id="9e004-118">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="9e004-119">Element som krävs.</span><span class="sxs-lookup"><span data-stu-id="9e004-119">Required element.</span></span><br /><br /> <span data-ttu-id="9e004-120">Definierar vilka data som visas av kontrollen och hur de visas.</span><span class="sxs-lookup"><span data-stu-id="9e004-120">Defines what data is displayed by the control and how it is displayed.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9e004-121">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="9e004-121">Parent Elements</span></span>

|<span data-ttu-id="9e004-122">Element</span><span class="sxs-lookup"><span data-stu-id="9e004-122">Element</span></span>|<span data-ttu-id="9e004-123">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="9e004-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9e004-124">CustomEntries Element för anpassad kontroll för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="9e004-124">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="9e004-125">Innehåller definitionerna av vanliga kontrollen.</span><span class="sxs-lookup"><span data-stu-id="9e004-125">Provides the definitions of the common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9e004-126">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="9e004-126">Remarks</span></span>

<span data-ttu-id="9e004-127">Endast en definition som krävs för varje anpassad kontroll som är vanliga i de flesta fall, men det är möjligt att ha flera definitioner om du vill använda samma kontroll för att visa olika .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="9e004-127">In most cases, only one definition is required for each common custom control, but it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="9e004-128">I sådana fall kan ange du en definition av separat för varje objekt eller en uppsättning objekt.</span><span class="sxs-lookup"><span data-stu-id="9e004-128">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="9e004-129">Se även</span><span class="sxs-lookup"><span data-stu-id="9e004-129">See Also</span></span>

[<span data-ttu-id="9e004-130">CustomEntries Element för anpassad kontroll för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="9e004-130">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="9e004-131">CustomItem Element för CustomEntry för kontroller för konfiguration</span><span class="sxs-lookup"><span data-stu-id="9e004-131">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="9e004-132">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="9e004-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
