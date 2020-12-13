---
ms.date: 09/13/2016
ms.topic: reference
title: ScriptBlock-element för GroupBy (format)
description: ScriptBlock-element för GroupBy (format)
ms.openlocfilehash: 117cbef93889046626741449886a1caaa39815cb
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665251"
---
# <a name="scriptblock-element-for-groupby-format"></a><span data-ttu-id="98705-103">ScriptBlock-element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="98705-103">ScriptBlock Element for GroupBy (Format)</span></span>

<span data-ttu-id="98705-104">Anger det skript som startar en ny grupp när dess värde ändras.</span><span class="sxs-lookup"><span data-stu-id="98705-104">Specifies the script that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="98705-105">Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) script block-element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="98705-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) ScriptBlock Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="98705-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="98705-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="98705-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="98705-107">Attributes and Elements</span></span>

<span data-ttu-id="98705-108">I följande avsnitt beskrivs attribut, underordnade element och `ScriptBlock` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="98705-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="98705-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="98705-109">Attributes</span></span>

<span data-ttu-id="98705-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="98705-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="98705-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="98705-111">Child Elements</span></span>

<span data-ttu-id="98705-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="98705-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="98705-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="98705-113">Parent Elements</span></span>

|<span data-ttu-id="98705-114">Element</span><span class="sxs-lookup"><span data-stu-id="98705-114">Element</span></span>|<span data-ttu-id="98705-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="98705-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="98705-116">GroupBy-element för View (format)</span><span class="sxs-lookup"><span data-stu-id="98705-116">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="98705-117">Definierar hur en grupp med .NET-objekt visas.</span><span class="sxs-lookup"><span data-stu-id="98705-117">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="98705-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="98705-118">Text Value</span></span>

<span data-ttu-id="98705-119">Ange det skript som utvärderas.</span><span class="sxs-lookup"><span data-stu-id="98705-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="98705-120">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="98705-120">Remarks</span></span>

<span data-ttu-id="98705-121">PowerShell startar en ny grupp när värdet för det här skriptet ändras.</span><span class="sxs-lookup"><span data-stu-id="98705-121">PowerShell starts a new group whenever the value of this script changes.</span></span>

<span data-ttu-id="98705-122">När det här elementet har angetts kan du inte ange elementet [PropertyName](propertyname-element-for-groupby-format.md) för att starta en ny grupp.</span><span class="sxs-lookup"><span data-stu-id="98705-122">When this element is specified, you cannot specify the [PropertyName](propertyname-element-for-groupby-format.md) element to start a new group.</span></span>

## <a name="see-also"></a><span data-ttu-id="98705-123">Se även</span><span class="sxs-lookup"><span data-stu-id="98705-123">See Also</span></span>

[<span data-ttu-id="98705-124">PropertyName-element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="98705-124">PropertyName Element for GroupBy (Format)</span></span>](propertyname-element-for-groupby-format.md)

[<span data-ttu-id="98705-125">GroupBy-element för View (format)</span><span class="sxs-lookup"><span data-stu-id="98705-125">GroupBy Element for View (Format)</span></span>](groupby-element-for-view-format.md)

[<span data-ttu-id="98705-126">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="98705-126">Writing a PowerShell Formatting File</span></span>](writing-a-powershell-formatting-file.md)
