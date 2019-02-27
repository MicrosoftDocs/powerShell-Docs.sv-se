---
title: CustomEntries Element för anpassad kontroll för kontroller för konfiguration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 80fc4de2-208f-4506-9a6a-c2675bb83be4
caps.latest.revision: 11
ms.openlocfilehash: abef6c91500f665c2366f221496d4cfd6444f5c9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847028"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-configuration-format"></a><span data-ttu-id="37e52-102">CustomEntries-element för CustomControl för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="37e52-102">CustomEntries Element for CustomControl for Controls for Configuration (Format)</span></span>

<span data-ttu-id="37e52-103">Innehåller definitioner av en gemensam kontroll.</span><span class="sxs-lookup"><span data-stu-id="37e52-103">Provides the definitions of a common control.</span></span> <span data-ttu-id="37e52-104">Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.</span><span class="sxs-lookup"><span data-stu-id="37e52-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="37e52-105">Konfigurationselementet Element (Format) kontroller av (Format) kontroll konfigurationselement för kontroller för (Format) anpassad kontroll konfigurationselement för kontroll för (Format) CustomEntries konfigurationselement för anpassad kontroll för konfiguration ( Format)</span><span class="sxs-lookup"><span data-stu-id="37e52-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="37e52-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="37e52-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="37e52-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="37e52-107">Attributes and Elements</span></span>

<span data-ttu-id="37e52-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `CustomEntries` element.</span><span class="sxs-lookup"><span data-stu-id="37e52-108">The following sections describe attributes, child elements, and the parent element of the `CustomEntries` element.</span></span> <span data-ttu-id="37e52-109">Du måste ange en eller flera underordnade element.</span><span class="sxs-lookup"><span data-stu-id="37e52-109">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="37e52-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="37e52-110">Attributes</span></span>

<span data-ttu-id="37e52-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="37e52-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="37e52-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="37e52-112">Child Elements</span></span>

|<span data-ttu-id="37e52-113">Element</span><span class="sxs-lookup"><span data-stu-id="37e52-113">Element</span></span>|<span data-ttu-id="37e52-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="37e52-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="37e52-115">CustomEntry Element för anpassad kontroll för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="37e52-115">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="37e52-116">Innehåller en definition av vanliga kontrollen.</span><span class="sxs-lookup"><span data-stu-id="37e52-116">Provides a definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="37e52-117">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="37e52-117">Parent Elements</span></span>

|<span data-ttu-id="37e52-118">Element</span><span class="sxs-lookup"><span data-stu-id="37e52-118">Element</span></span>|<span data-ttu-id="37e52-119">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="37e52-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="37e52-120">Anpassad kontroll Element för kontroll för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="37e52-120">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="37e52-121">Definierar en gemensam kontroll.</span><span class="sxs-lookup"><span data-stu-id="37e52-121">Defines a common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="37e52-122">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="37e52-122">Remarks</span></span>

<span data-ttu-id="37e52-123">I de flesta fall en kontroll har endast en definition som definieras i en enda `CustomEntry` element.</span><span class="sxs-lookup"><span data-stu-id="37e52-123">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="37e52-124">Det är dock möjligt att ha flera definitioner om du vill använda samma kontroll för att visa olika .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="37e52-124">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="37e52-125">I sådana fall kan du definiera en `CustomEntry` element för varje objekt eller en uppsättning objekt.</span><span class="sxs-lookup"><span data-stu-id="37e52-125">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="37e52-126">Se även</span><span class="sxs-lookup"><span data-stu-id="37e52-126">See Also</span></span>

[<span data-ttu-id="37e52-127">Anpassad kontroll Element för kontroll för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="37e52-127">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="37e52-128">CustomEntry Element för anpassad kontroll för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="37e52-128">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="37e52-129">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="37e52-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
