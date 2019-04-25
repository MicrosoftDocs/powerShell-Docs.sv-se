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
ms.openlocfilehash: f2f6b9af7740b1231881294c2f32bf97b5a1568b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064517"
---
# <a name="scriptblock-element-for-groupby-format"></a><span data-ttu-id="41d11-102">ScriptBlock-element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="41d11-102">ScriptBlock Element for GroupBy (Format)</span></span>

<span data-ttu-id="41d11-103">Anger det skript som startar en ny grupp när dess värde ändras.</span><span class="sxs-lookup"><span data-stu-id="41d11-103">Specifies the script that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="41d11-104">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) GroupBy konfigurationselement för Visa (Format) ScriptBlock elementet för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="41d11-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) ScriptBlock Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="41d11-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="41d11-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="41d11-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="41d11-106">Attributes and Elements</span></span>

<span data-ttu-id="41d11-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `ScriptBlock` element.</span><span class="sxs-lookup"><span data-stu-id="41d11-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="41d11-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="41d11-108">Attributes</span></span>

<span data-ttu-id="41d11-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="41d11-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="41d11-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="41d11-110">Child Elements</span></span>

<span data-ttu-id="41d11-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="41d11-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="41d11-112">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="41d11-112">Parent Elements</span></span>

|<span data-ttu-id="41d11-113">Element</span><span class="sxs-lookup"><span data-stu-id="41d11-113">Element</span></span>|<span data-ttu-id="41d11-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="41d11-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="41d11-115">GroupBy-Element för Visa (Format)</span><span class="sxs-lookup"><span data-stu-id="41d11-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="41d11-116">Definierar hur en grupp med .NET-objekt visas.</span><span class="sxs-lookup"><span data-stu-id="41d11-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="41d11-117">Textvärde</span><span class="sxs-lookup"><span data-stu-id="41d11-117">Text Value</span></span>

<span data-ttu-id="41d11-118">Ange det skript som ska utvärderas.</span><span class="sxs-lookup"><span data-stu-id="41d11-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="41d11-119">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="41d11-119">Remarks</span></span>

<span data-ttu-id="41d11-120">Windows PowerShell startar en ny grupp när det här skriptet ändras.</span><span class="sxs-lookup"><span data-stu-id="41d11-120">Windows PowerShell starts a new group whenever the value of this script changes.</span></span>

<span data-ttu-id="41d11-121">När det här elementet har angetts ska du inte ange den [PropertyName](http://msdn.microsoft.com/en-us/396dede0-039a-4a87-a5ef-3ecabb729676) element att starta en ny grupp.</span><span class="sxs-lookup"><span data-stu-id="41d11-121">When this element is specified, you cannot specify the [PropertyName](http://msdn.microsoft.com/en-us/396dede0-039a-4a87-a5ef-3ecabb729676) element to start a new group.</span></span>

## <a name="see-also"></a><span data-ttu-id="41d11-122">Se även</span><span class="sxs-lookup"><span data-stu-id="41d11-122">See Also</span></span>

[<span data-ttu-id="41d11-123">PropertyName-Element för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="41d11-123">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)

[<span data-ttu-id="41d11-124">GroupBy-Element för Visa (Format)</span><span class="sxs-lookup"><span data-stu-id="41d11-124">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="41d11-125">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="41d11-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
