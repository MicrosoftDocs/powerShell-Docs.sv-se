---
title: Styr Element för konfiguration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d4ef63d-5866-4319-ba00-7ed96de26821
caps.latest.revision: 18
ms.openlocfilehash: ac9f7ff08f6e87ef83b5a2fe23fc58ee2651566d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850437"
---
# <a name="controls-element-for-configuration-format"></a><span data-ttu-id="85b82-102">Controls-element för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="85b82-102">Controls Element for Configuration (Format)</span></span>

<span data-ttu-id="85b82-103">Definierar de vanliga kontroller som kan användas av alla vyer i filen formatering.</span><span class="sxs-lookup"><span data-stu-id="85b82-103">Defines the common controls that can be used by all views of the formatting file.</span></span>

<span data-ttu-id="85b82-104">Konfigurationselementet Element (Format) kontroller av konfigurationen (Format)</span><span class="sxs-lookup"><span data-stu-id="85b82-104">Configuration Element (Format) Controls Element of Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="85b82-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="85b82-105">Syntax</span></span>

```xml
<Controls>
  <Control>...</Control>
</Controls>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="85b82-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="85b82-106">Attributes and Elements</span></span>

<span data-ttu-id="85b82-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `Controls` element.</span><span class="sxs-lookup"><span data-stu-id="85b82-107">The following sections describe the attributes, child elements, and the parent element of the `Controls` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="85b82-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="85b82-108">Attributes</span></span>

<span data-ttu-id="85b82-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="85b82-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="85b82-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="85b82-110">Child Elements</span></span>

|<span data-ttu-id="85b82-111">Element</span><span class="sxs-lookup"><span data-stu-id="85b82-111">Element</span></span>|<span data-ttu-id="85b82-112">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="85b82-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="85b82-113">Control-Element för kontroller för Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="85b82-113">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)|<span data-ttu-id="85b82-114">Element som krävs.</span><span class="sxs-lookup"><span data-stu-id="85b82-114">Required element.</span></span><br /><br /> <span data-ttu-id="85b82-115">Definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.</span><span class="sxs-lookup"><span data-stu-id="85b82-115">Defines a common control that can be used by all views of the formatting file.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="85b82-116">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="85b82-116">Parent Elements</span></span>

|<span data-ttu-id="85b82-117">Element</span><span class="sxs-lookup"><span data-stu-id="85b82-117">Element</span></span>|<span data-ttu-id="85b82-118">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="85b82-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="85b82-119">Konfigurationselementet (Format)</span><span class="sxs-lookup"><span data-stu-id="85b82-119">Configuration Element (Format)</span></span>](./configuration-element-format.md)|<span data-ttu-id="85b82-120">Representerar det översta elementet i en formatering fil.</span><span class="sxs-lookup"><span data-stu-id="85b82-120">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="85b82-121">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="85b82-121">Remarks</span></span>

<span data-ttu-id="85b82-122">Du kan skapa hur många vanliga kontroller som helst.</span><span class="sxs-lookup"><span data-stu-id="85b82-122">You can create any number of common controls.</span></span> <span data-ttu-id="85b82-123">Du måste ange det namn som används för att referera till kontrollen och komponenterna i kontrollen för varje kontroll.</span><span class="sxs-lookup"><span data-stu-id="85b82-123">For each control, you must specify the name that is used to reference the control and the components of the control.</span></span>

## <a name="see-also"></a><span data-ttu-id="85b82-124">Se även</span><span class="sxs-lookup"><span data-stu-id="85b82-124">See Also</span></span>

[<span data-ttu-id="85b82-125">Konfigurationselementet (Format)</span><span class="sxs-lookup"><span data-stu-id="85b82-125">Configuration Element (Format)</span></span>](./configuration-element-format.md)

[<span data-ttu-id="85b82-126">Control-Element för kontroller för Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="85b82-126">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)

[<span data-ttu-id="85b82-127">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="85b82-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
