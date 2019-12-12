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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359043"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-configuration-format"></a><span data-ttu-id="bbec4-102">CustomEntries-element för CustomControl för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="bbec4-102">CustomEntries Element for CustomControl for Controls for Configuration (Format)</span></span>

<span data-ttu-id="bbec4-103">Innehåller definitionerna för en gemensam kontroll.</span><span class="sxs-lookup"><span data-stu-id="bbec4-103">Provides the definitions of a common control.</span></span> <span data-ttu-id="bbec4-104">Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.</span><span class="sxs-lookup"><span data-stu-id="bbec4-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="bbec4-105">Konfigurations element (format) styr element i konfigurations-(format) kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för konfiguration ( Formatering</span><span class="sxs-lookup"><span data-stu-id="bbec4-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bbec4-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="bbec4-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="bbec4-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="bbec4-107">Attributes and Elements</span></span>

<span data-ttu-id="bbec4-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `CustomEntries`-elementet.</span><span class="sxs-lookup"><span data-stu-id="bbec4-108">The following sections describe attributes, child elements, and the parent element of the `CustomEntries` element.</span></span> <span data-ttu-id="bbec4-109">Du måste ange ett eller flera underordnade element.</span><span class="sxs-lookup"><span data-stu-id="bbec4-109">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="bbec4-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="bbec4-110">Attributes</span></span>

<span data-ttu-id="bbec4-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="bbec4-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bbec4-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="bbec4-112">Child Elements</span></span>

|<span data-ttu-id="bbec4-113">Element</span><span class="sxs-lookup"><span data-stu-id="bbec4-113">Element</span></span>|<span data-ttu-id="bbec4-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="bbec4-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bbec4-115">CustomEntry-element för CustomControl för kontroller för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="bbec4-115">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="bbec4-116">Ger en definition av den gemensamma kontrollen.</span><span class="sxs-lookup"><span data-stu-id="bbec4-116">Provides a definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="bbec4-117">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="bbec4-117">Parent Elements</span></span>

|<span data-ttu-id="bbec4-118">Element</span><span class="sxs-lookup"><span data-stu-id="bbec4-118">Element</span></span>|<span data-ttu-id="bbec4-119">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="bbec4-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bbec4-120">CustomControl-element för kontroll av konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="bbec4-120">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="bbec4-121">Definierar en gemensam kontroll.</span><span class="sxs-lookup"><span data-stu-id="bbec4-121">Defines a common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="bbec4-122">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="bbec4-122">Remarks</span></span>

<span data-ttu-id="bbec4-123">I de flesta fall har en kontroll bara en definition som definieras i ett enda `CustomEntry`-element.</span><span class="sxs-lookup"><span data-stu-id="bbec4-123">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="bbec4-124">Det är dock möjligt att ha flera definitioner om du vill använda samma kontroll för att visa olika .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="bbec4-124">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="bbec4-125">I dessa fall kan du definiera ett `CustomEntry`-element för varje objekt eller uppsättning objekt.</span><span class="sxs-lookup"><span data-stu-id="bbec4-125">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="bbec4-126">Se även</span><span class="sxs-lookup"><span data-stu-id="bbec4-126">See Also</span></span>

[<span data-ttu-id="bbec4-127">CustomControl-element för kontroll av konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="bbec4-127">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="bbec4-128">CustomEntry-element för CustomControl för kontroller för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="bbec4-128">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="bbec4-129">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="bbec4-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
