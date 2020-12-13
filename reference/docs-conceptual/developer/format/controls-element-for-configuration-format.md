---
ms.date: 09/13/2016
ms.topic: reference
title: Controls-element för Configuration (format)
description: Controls-element för Configuration (format)
ms.openlocfilehash: 53f874ddccf3b4f1f0a23aad608e786524bde830
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668107"
---
# <a name="controls-element-for-configuration-format"></a><span data-ttu-id="b4817-103">Controls-element för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="b4817-103">Controls Element for Configuration (Format)</span></span>

<span data-ttu-id="b4817-104">Definierar de gemensamma kontroller som kan användas av alla vyer i formaterings filen.</span><span class="sxs-lookup"><span data-stu-id="b4817-104">Defines the common controls that can be used by all views of the formatting file.</span></span>

<span data-ttu-id="b4817-105">Konfigurations element (format) styr elementet i konfigurationen (format)</span><span class="sxs-lookup"><span data-stu-id="b4817-105">Configuration Element (Format) Controls Element of Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b4817-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="b4817-106">Syntax</span></span>

```xml
<Controls>
  <Control>...</Control>
</Controls>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b4817-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="b4817-107">Attributes and Elements</span></span>

<span data-ttu-id="b4817-108">I följande avsnitt beskrivs attributen, underordnade element och `Controls` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="b4817-108">The following sections describe the attributes, child elements, and the parent element of the `Controls` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b4817-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="b4817-109">Attributes</span></span>

<span data-ttu-id="b4817-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="b4817-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b4817-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="b4817-111">Child Elements</span></span>

|<span data-ttu-id="b4817-112">Element</span><span class="sxs-lookup"><span data-stu-id="b4817-112">Element</span></span>|<span data-ttu-id="b4817-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b4817-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b4817-114">Control-element för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="b4817-114">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)|<span data-ttu-id="b4817-115">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="b4817-115">Required element.</span></span><br /><br /> <span data-ttu-id="b4817-116">Definierar en gemensam kontroll som kan användas av alla vyer i formaterings filen.</span><span class="sxs-lookup"><span data-stu-id="b4817-116">Defines a common control that can be used by all views of the formatting file.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b4817-117">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="b4817-117">Parent Elements</span></span>

|<span data-ttu-id="b4817-118">Element</span><span class="sxs-lookup"><span data-stu-id="b4817-118">Element</span></span>|<span data-ttu-id="b4817-119">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b4817-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b4817-120">Configuration-element (format)</span><span class="sxs-lookup"><span data-stu-id="b4817-120">Configuration Element (Format)</span></span>](./configuration-element-format.md)|<span data-ttu-id="b4817-121">Representerar det översta elementet i en textfil.</span><span class="sxs-lookup"><span data-stu-id="b4817-121">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b4817-122">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="b4817-122">Remarks</span></span>

<span data-ttu-id="b4817-123">Du kan skapa valfritt antal vanliga kontroller.</span><span class="sxs-lookup"><span data-stu-id="b4817-123">You can create any number of common controls.</span></span> <span data-ttu-id="b4817-124">För varje kontroll måste du ange det namn som ska användas för att referera till kontrollen och kontrollens komponenter.</span><span class="sxs-lookup"><span data-stu-id="b4817-124">For each control, you must specify the name that is used to reference the control and the components of the control.</span></span>

## <a name="see-also"></a><span data-ttu-id="b4817-125">Se även</span><span class="sxs-lookup"><span data-stu-id="b4817-125">See Also</span></span>

[<span data-ttu-id="b4817-126">Configuration-element (format)</span><span class="sxs-lookup"><span data-stu-id="b4817-126">Configuration Element (Format)</span></span>](./configuration-element-format.md)

[<span data-ttu-id="b4817-127">Control-element för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="b4817-127">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)

[<span data-ttu-id="b4817-128">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="b4817-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
