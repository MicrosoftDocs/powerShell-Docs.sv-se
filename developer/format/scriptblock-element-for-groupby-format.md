---
title: ScriptBlock Element för GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30183927-6f0e-4717-b6f5-f07a6e134cfb
caps.latest.revision: 6
ms.openlocfilehash: 37a297228eb33ff75daf94a12635d42b52c6cc9f
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229311"
---
# <a name="scriptblock-element-for-groupby-format"></a><span data-ttu-id="bab0b-102">ScriptBlock-element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="bab0b-102">ScriptBlock Element for GroupBy (Format)</span></span>

<span data-ttu-id="bab0b-103">Anger det skript som startar en ny grupp när dess värde ändras.</span><span class="sxs-lookup"><span data-stu-id="bab0b-103">Specifies the script that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="bab0b-104">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) GroupBy konfigurationselement för Visa (Format) ScriptBlock elementet för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="bab0b-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) ScriptBlock Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bab0b-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="bab0b-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bab0b-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="bab0b-106">Attributes and Elements</span></span>

<span data-ttu-id="bab0b-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `ScriptBlock` element.</span><span class="sxs-lookup"><span data-stu-id="bab0b-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="bab0b-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="bab0b-108">Attributes</span></span>

<span data-ttu-id="bab0b-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="bab0b-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bab0b-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="bab0b-110">Child Elements</span></span>

<span data-ttu-id="bab0b-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="bab0b-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="bab0b-112">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="bab0b-112">Parent Elements</span></span>

|<span data-ttu-id="bab0b-113">Element</span><span class="sxs-lookup"><span data-stu-id="bab0b-113">Element</span></span>|<span data-ttu-id="bab0b-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="bab0b-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bab0b-115">GroupBy-Element för Visa (Format)</span><span class="sxs-lookup"><span data-stu-id="bab0b-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="bab0b-116">Definierar hur en grupp med .NET-objekt visas.</span><span class="sxs-lookup"><span data-stu-id="bab0b-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="bab0b-117">Textvärde</span><span class="sxs-lookup"><span data-stu-id="bab0b-117">Text Value</span></span>

<span data-ttu-id="bab0b-118">Ange det skript som ska utvärderas.</span><span class="sxs-lookup"><span data-stu-id="bab0b-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="bab0b-119">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="bab0b-119">Remarks</span></span>

<span data-ttu-id="bab0b-120">PowerShell startar en ny grupp när det här skriptet ändras.</span><span class="sxs-lookup"><span data-stu-id="bab0b-120">PowerShell starts a new group whenever the value of this script changes.</span></span>

<span data-ttu-id="bab0b-121">När det här elementet har angetts ska du inte ange den [PropertyName](propertyname-element-for-groupby-format.md) element att starta en ny grupp.</span><span class="sxs-lookup"><span data-stu-id="bab0b-121">When this element is specified, you cannot specify the [PropertyName](propertyname-element-for-groupby-format.md) element to start a new group.</span></span>

## <a name="see-also"></a><span data-ttu-id="bab0b-122">Se även</span><span class="sxs-lookup"><span data-stu-id="bab0b-122">See Also</span></span>

[<span data-ttu-id="bab0b-123">PropertyName-Element för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="bab0b-123">PropertyName Element for GroupBy (Format)</span></span>](propertyname-element-for-groupby-format.md)

[<span data-ttu-id="bab0b-124">GroupBy-Element för Visa (Format)</span><span class="sxs-lookup"><span data-stu-id="bab0b-124">GroupBy Element for View (Format)</span></span>](groupby-element-for-view-format.md)

[<span data-ttu-id="bab0b-125">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="bab0b-125">Writing a PowerShell Formatting File</span></span>](writing-a-powershell-formatting-file.md)
