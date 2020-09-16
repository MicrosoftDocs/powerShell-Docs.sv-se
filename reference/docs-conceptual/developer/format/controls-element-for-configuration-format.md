---
title: Kontrollerar element för konfiguration (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 44b9db0d3523e5e9086da9911882b258a2a54ca6
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783797"
---
# <a name="controls-element-for-configuration-format"></a><span data-ttu-id="a1bb5-102">Controls-element för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="a1bb5-102">Controls Element for Configuration (Format)</span></span>

<span data-ttu-id="a1bb5-103">Definierar de gemensamma kontroller som kan användas av alla vyer i formaterings filen.</span><span class="sxs-lookup"><span data-stu-id="a1bb5-103">Defines the common controls that can be used by all views of the formatting file.</span></span>

<span data-ttu-id="a1bb5-104">Konfigurations element (format) styr elementet i konfigurationen (format)</span><span class="sxs-lookup"><span data-stu-id="a1bb5-104">Configuration Element (Format) Controls Element of Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a1bb5-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="a1bb5-105">Syntax</span></span>

```xml
<Controls>
  <Control>...</Control>
</Controls>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a1bb5-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="a1bb5-106">Attributes and Elements</span></span>

<span data-ttu-id="a1bb5-107">I följande avsnitt beskrivs attributen, underordnade element och `Controls` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="a1bb5-107">The following sections describe the attributes, child elements, and the parent element of the `Controls` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a1bb5-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="a1bb5-108">Attributes</span></span>

<span data-ttu-id="a1bb5-109">Inga.</span><span class="sxs-lookup"><span data-stu-id="a1bb5-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a1bb5-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="a1bb5-110">Child Elements</span></span>

|<span data-ttu-id="a1bb5-111">Element</span><span class="sxs-lookup"><span data-stu-id="a1bb5-111">Element</span></span>|<span data-ttu-id="a1bb5-112">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a1bb5-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a1bb5-113">Control-element för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="a1bb5-113">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)|<span data-ttu-id="a1bb5-114">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="a1bb5-114">Required element.</span></span><br /><br /> <span data-ttu-id="a1bb5-115">Definierar en gemensam kontroll som kan användas av alla vyer i formaterings filen.</span><span class="sxs-lookup"><span data-stu-id="a1bb5-115">Defines a common control that can be used by all views of the formatting file.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a1bb5-116">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="a1bb5-116">Parent Elements</span></span>

|<span data-ttu-id="a1bb5-117">Element</span><span class="sxs-lookup"><span data-stu-id="a1bb5-117">Element</span></span>|<span data-ttu-id="a1bb5-118">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a1bb5-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a1bb5-119">Configuration-element (format)</span><span class="sxs-lookup"><span data-stu-id="a1bb5-119">Configuration Element (Format)</span></span>](./configuration-element-format.md)|<span data-ttu-id="a1bb5-120">Representerar det översta elementet i en textfil.</span><span class="sxs-lookup"><span data-stu-id="a1bb5-120">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a1bb5-121">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="a1bb5-121">Remarks</span></span>

<span data-ttu-id="a1bb5-122">Du kan skapa valfritt antal vanliga kontroller.</span><span class="sxs-lookup"><span data-stu-id="a1bb5-122">You can create any number of common controls.</span></span> <span data-ttu-id="a1bb5-123">För varje kontroll måste du ange det namn som ska användas för att referera till kontrollen och kontrollens komponenter.</span><span class="sxs-lookup"><span data-stu-id="a1bb5-123">For each control, you must specify the name that is used to reference the control and the components of the control.</span></span>

## <a name="see-also"></a><span data-ttu-id="a1bb5-124">Se även</span><span class="sxs-lookup"><span data-stu-id="a1bb5-124">See Also</span></span>

[<span data-ttu-id="a1bb5-125">Configuration-element (format)</span><span class="sxs-lookup"><span data-stu-id="a1bb5-125">Configuration Element (Format)</span></span>](./configuration-element-format.md)

[<span data-ttu-id="a1bb5-126">Control-element för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="a1bb5-126">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)

[<span data-ttu-id="a1bb5-127">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="a1bb5-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
