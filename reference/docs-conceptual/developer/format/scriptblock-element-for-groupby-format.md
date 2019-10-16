---
title: Script block-element för GroupBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30183927-6f0e-4717-b6f5-f07a6e134cfb
caps.latest.revision: 6
ms.openlocfilehash: 37a297228eb33ff75daf94a12635d42b52c6cc9f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355876"
---
# <a name="scriptblock-element-for-groupby-format"></a><span data-ttu-id="61170-102">ScriptBlock-element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="61170-102">ScriptBlock Element for GroupBy (Format)</span></span>

<span data-ttu-id="61170-103">Anger det skript som startar en ny grupp när dess värde ändras.</span><span class="sxs-lookup"><span data-stu-id="61170-103">Specifies the script that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="61170-104">Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) script block-element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="61170-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) ScriptBlock Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="61170-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="61170-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="61170-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="61170-106">Attributes and Elements</span></span>

<span data-ttu-id="61170-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för elementet `ScriptBlock`.</span><span class="sxs-lookup"><span data-stu-id="61170-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="61170-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="61170-108">Attributes</span></span>

<span data-ttu-id="61170-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="61170-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="61170-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="61170-110">Child Elements</span></span>

<span data-ttu-id="61170-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="61170-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="61170-112">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="61170-112">Parent Elements</span></span>

|<span data-ttu-id="61170-113">Element</span><span class="sxs-lookup"><span data-stu-id="61170-113">Element</span></span>|<span data-ttu-id="61170-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="61170-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="61170-115">GroupBy-element för vy (format)</span><span class="sxs-lookup"><span data-stu-id="61170-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="61170-116">Definierar hur en grupp med .NET-objekt visas.</span><span class="sxs-lookup"><span data-stu-id="61170-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="61170-117">Text värde</span><span class="sxs-lookup"><span data-stu-id="61170-117">Text Value</span></span>

<span data-ttu-id="61170-118">Ange det skript som utvärderas.</span><span class="sxs-lookup"><span data-stu-id="61170-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="61170-119">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="61170-119">Remarks</span></span>

<span data-ttu-id="61170-120">PowerShell startar en ny grupp när värdet för det här skriptet ändras.</span><span class="sxs-lookup"><span data-stu-id="61170-120">PowerShell starts a new group whenever the value of this script changes.</span></span>

<span data-ttu-id="61170-121">När det här elementet har angetts kan du inte ange elementet [PropertyName](propertyname-element-for-groupby-format.md) för att starta en ny grupp.</span><span class="sxs-lookup"><span data-stu-id="61170-121">When this element is specified, you cannot specify the [PropertyName](propertyname-element-for-groupby-format.md) element to start a new group.</span></span>

## <a name="see-also"></a><span data-ttu-id="61170-122">Se även</span><span class="sxs-lookup"><span data-stu-id="61170-122">See Also</span></span>

[<span data-ttu-id="61170-123">PropertyName-element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="61170-123">PropertyName Element for GroupBy (Format)</span></span>](propertyname-element-for-groupby-format.md)

[<span data-ttu-id="61170-124">GroupBy-element för vy (format)</span><span class="sxs-lookup"><span data-stu-id="61170-124">GroupBy Element for View (Format)</span></span>](groupby-element-for-view-format.md)

[<span data-ttu-id="61170-125">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="61170-125">Writing a PowerShell Formatting File</span></span>](writing-a-powershell-formatting-file.md)
