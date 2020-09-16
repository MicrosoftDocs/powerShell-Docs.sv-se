---
title: Script block-element för GroupBy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e761e02a7910cd598449d564e827889162da9f25
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787690"
---
# <a name="scriptblock-element-for-groupby-format"></a><span data-ttu-id="53512-102">ScriptBlock-element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="53512-102">ScriptBlock Element for GroupBy (Format)</span></span>

<span data-ttu-id="53512-103">Anger det skript som startar en ny grupp när dess värde ändras.</span><span class="sxs-lookup"><span data-stu-id="53512-103">Specifies the script that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="53512-104">Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) script block-element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="53512-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) ScriptBlock Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="53512-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="53512-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="53512-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="53512-106">Attributes and Elements</span></span>

<span data-ttu-id="53512-107">I följande avsnitt beskrivs attribut, underordnade element och `ScriptBlock` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="53512-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="53512-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="53512-108">Attributes</span></span>

<span data-ttu-id="53512-109">Inga.</span><span class="sxs-lookup"><span data-stu-id="53512-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="53512-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="53512-110">Child Elements</span></span>

<span data-ttu-id="53512-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="53512-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="53512-112">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="53512-112">Parent Elements</span></span>

|<span data-ttu-id="53512-113">Element</span><span class="sxs-lookup"><span data-stu-id="53512-113">Element</span></span>|<span data-ttu-id="53512-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="53512-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="53512-115">GroupBy-element för View (format)</span><span class="sxs-lookup"><span data-stu-id="53512-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="53512-116">Definierar hur en grupp med .NET-objekt visas.</span><span class="sxs-lookup"><span data-stu-id="53512-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="53512-117">Textvärde</span><span class="sxs-lookup"><span data-stu-id="53512-117">Text Value</span></span>

<span data-ttu-id="53512-118">Ange det skript som utvärderas.</span><span class="sxs-lookup"><span data-stu-id="53512-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="53512-119">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="53512-119">Remarks</span></span>

<span data-ttu-id="53512-120">PowerShell startar en ny grupp när värdet för det här skriptet ändras.</span><span class="sxs-lookup"><span data-stu-id="53512-120">PowerShell starts a new group whenever the value of this script changes.</span></span>

<span data-ttu-id="53512-121">När det här elementet har angetts kan du inte ange elementet [PropertyName](propertyname-element-for-groupby-format.md) för att starta en ny grupp.</span><span class="sxs-lookup"><span data-stu-id="53512-121">When this element is specified, you cannot specify the [PropertyName](propertyname-element-for-groupby-format.md) element to start a new group.</span></span>

## <a name="see-also"></a><span data-ttu-id="53512-122">Se även</span><span class="sxs-lookup"><span data-stu-id="53512-122">See Also</span></span>

[<span data-ttu-id="53512-123">PropertyName-element för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="53512-123">PropertyName Element for GroupBy (Format)</span></span>](propertyname-element-for-groupby-format.md)

[<span data-ttu-id="53512-124">GroupBy-element för View (format)</span><span class="sxs-lookup"><span data-stu-id="53512-124">GroupBy Element for View (Format)</span></span>](groupby-element-for-view-format.md)

[<span data-ttu-id="53512-125">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="53512-125">Writing a PowerShell Formatting File</span></span>](writing-a-powershell-formatting-file.md)
