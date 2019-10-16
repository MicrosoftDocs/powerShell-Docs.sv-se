---
title: CustomEntries-element för CustomControl för kontroll av konfiguration (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 80fc4de2-208f-4506-9a6a-c2675bb83be4
caps.latest.revision: 11
ms.openlocfilehash: abef6c91500f665c2366f221496d4cfd6444f5c9
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359043"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-configuration-format"></a><span data-ttu-id="94167-102">CustomEntries-element för CustomControl för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="94167-102">CustomEntries Element for CustomControl for Controls for Configuration (Format)</span></span>

<span data-ttu-id="94167-103">Innehåller definitionerna för en gemensam kontroll.</span><span class="sxs-lookup"><span data-stu-id="94167-103">Provides the definitions of a common control.</span></span> <span data-ttu-id="94167-104">Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.</span><span class="sxs-lookup"><span data-stu-id="94167-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="94167-105">Konfigurations element (format) styr element i konfigurations-(format) kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för konfiguration ( Formatering</span><span class="sxs-lookup"><span data-stu-id="94167-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="94167-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="94167-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="94167-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="94167-107">Attributes and Elements</span></span>

<span data-ttu-id="94167-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för elementet `CustomEntries`.</span><span class="sxs-lookup"><span data-stu-id="94167-108">The following sections describe attributes, child elements, and the parent element of the `CustomEntries` element.</span></span> <span data-ttu-id="94167-109">Du måste ange ett eller flera underordnade element.</span><span class="sxs-lookup"><span data-stu-id="94167-109">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="94167-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="94167-110">Attributes</span></span>

<span data-ttu-id="94167-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="94167-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="94167-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="94167-112">Child Elements</span></span>

|<span data-ttu-id="94167-113">Element</span><span class="sxs-lookup"><span data-stu-id="94167-113">Element</span></span>|<span data-ttu-id="94167-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="94167-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="94167-115">CustomEntry-element för CustomControl för kontroller för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="94167-115">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="94167-116">Ger en definition av den gemensamma kontrollen.</span><span class="sxs-lookup"><span data-stu-id="94167-116">Provides a definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="94167-117">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="94167-117">Parent Elements</span></span>

|<span data-ttu-id="94167-118">Element</span><span class="sxs-lookup"><span data-stu-id="94167-118">Element</span></span>|<span data-ttu-id="94167-119">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="94167-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="94167-120">CustomControl-element för kontroll av konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="94167-120">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="94167-121">Definierar en gemensam kontroll.</span><span class="sxs-lookup"><span data-stu-id="94167-121">Defines a common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="94167-122">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="94167-122">Remarks</span></span>

<span data-ttu-id="94167-123">I de flesta fall har en kontroll bara en definition som definieras i ett enda `CustomEntry`-element.</span><span class="sxs-lookup"><span data-stu-id="94167-123">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="94167-124">Det är dock möjligt att ha flera definitioner om du vill använda samma kontroll för att visa olika .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="94167-124">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="94167-125">I dessa fall kan du definiera ett `CustomEntry`-element för varje objekt eller uppsättning objekt.</span><span class="sxs-lookup"><span data-stu-id="94167-125">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="94167-126">Se även</span><span class="sxs-lookup"><span data-stu-id="94167-126">See Also</span></span>

[<span data-ttu-id="94167-127">CustomControl-element för kontroll av konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="94167-127">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="94167-128">CustomEntry-element för CustomControl för kontroller för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="94167-128">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="94167-129">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="94167-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
