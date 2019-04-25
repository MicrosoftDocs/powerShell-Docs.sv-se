---
title: PropertyName-Element för GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ddcecc46-ac75-43fa-b03a-802a68524ec3
caps.latest.revision: 10
ms.openlocfilehash: da6ac5abe7acbbee8f57b3e81529664f81800b86
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075876"
---
# <a name="propertyname-element-for-groupby-format"></a><span data-ttu-id="4d17f-102">PropertyName-element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="4d17f-102">PropertyName Element for GroupBy (Format)</span></span>

<span data-ttu-id="4d17f-103">Anger den .NET-egenskap som startar en ny grupp när dess värde ändras.</span><span class="sxs-lookup"><span data-stu-id="4d17f-103">Specifies the .NET property that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="4d17f-104">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) GroupBy konfigurationselement för Visa (Format) PropertyName elementet för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="4d17f-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) PropertyName Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4d17f-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="4d17f-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4d17f-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="4d17f-106">Attributes and Elements</span></span>

<span data-ttu-id="4d17f-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `PropertyName` element.</span><span class="sxs-lookup"><span data-stu-id="4d17f-107">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4d17f-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="4d17f-108">Attributes</span></span>

<span data-ttu-id="4d17f-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="4d17f-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4d17f-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="4d17f-110">Child Elements</span></span>

<span data-ttu-id="4d17f-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="4d17f-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4d17f-112">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="4d17f-112">Parent Elements</span></span>

|<span data-ttu-id="4d17f-113">Element</span><span class="sxs-lookup"><span data-stu-id="4d17f-113">Element</span></span>|<span data-ttu-id="4d17f-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="4d17f-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4d17f-115">GroupBy-Element för Visa (Format)</span><span class="sxs-lookup"><span data-stu-id="4d17f-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="4d17f-116">Definierar hur en grupp med .NET-objekt visas.</span><span class="sxs-lookup"><span data-stu-id="4d17f-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4d17f-117">Textvärde</span><span class="sxs-lookup"><span data-stu-id="4d17f-117">Text Value</span></span>

<span data-ttu-id="4d17f-118">Ange namnet på .NET-egenskapen.</span><span class="sxs-lookup"><span data-stu-id="4d17f-118">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="4d17f-119">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="4d17f-119">Remarks</span></span>

<span data-ttu-id="4d17f-120">Windows PowerShell startar en ny grupp när den här egenskapen ändras.</span><span class="sxs-lookup"><span data-stu-id="4d17f-120">Windows PowerShell starts a new group whenever the value of this property changes.</span></span>

<span data-ttu-id="4d17f-121">När det här elementet har angetts ska du inte ange den [ScriptBlock](./scriptblock-element-for-groupby-format.md) element att starta en ny grupp.</span><span class="sxs-lookup"><span data-stu-id="4d17f-121">When this element is specified, you cannot specify the [ScriptBlock](./scriptblock-element-for-groupby-format.md) element to start a new group.</span></span>

## <a name="example"></a><span data-ttu-id="4d17f-122">Exempel</span><span class="sxs-lookup"><span data-stu-id="4d17f-122">Example</span></span>

<span data-ttu-id="4d17f-123">I följande exempel visas hur du startar en ny grupp när en egenskap ändras.</span><span class="sxs-lookup"><span data-stu-id="4d17f-123">The following example shows how to start a new group when the value of a property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="4d17f-124">Ett exempel på en fullständig formatering fil som innehåller det här elementet finns [bred vy (GroupBy)](./wide-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="4d17f-124">For an example of a complete formatting file that includes this element, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4d17f-125">Se även</span><span class="sxs-lookup"><span data-stu-id="4d17f-125">See Also</span></span>

[<span data-ttu-id="4d17f-126">GroupBy-Element för Visa (Format)</span><span class="sxs-lookup"><span data-stu-id="4d17f-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="4d17f-127">ScriptBlock Element för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="4d17f-127">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="4d17f-128">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="4d17f-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
