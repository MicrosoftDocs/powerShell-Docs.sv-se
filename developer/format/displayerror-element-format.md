---
title: DisplayError Element (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45c45800-a87d-456e-b07c-12d4d8c27c67
caps.latest.revision: 8
ms.openlocfilehash: 431e5d8407b9f689a5224b329d8c7b52802e19e1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846055"
---
# <a name="displayerror-element-format"></a><span data-ttu-id="4ce6d-102">DisplayError-element (format)</span><span class="sxs-lookup"><span data-stu-id="4ce6d-102">DisplayError Element (Format)</span></span>

<span data-ttu-id="4ce6d-103">Anger att strängen #ERR visas när ett fel uppstår visar en typ av data.</span><span class="sxs-lookup"><span data-stu-id="4ce6d-103">Specifies that the string #ERR is displayed when an error occurs displaying a piece of data.</span></span>

<span data-ttu-id="4ce6d-104">Elementet (Format) DefaultSettings Element (Format) DisplayError konfigurationselement (Frmat)</span><span class="sxs-lookup"><span data-stu-id="4ce6d-104">Configuration Element (Format) DefaultSettings Element (Format) DisplayError Element (Frmat)</span></span>

## <a name="syntax"></a><span data-ttu-id="4ce6d-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="4ce6d-105">Syntax</span></span>

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4ce6d-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="4ce6d-106">Attributes and Elements</span></span>

<span data-ttu-id="4ce6d-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `DisplayError` element.</span><span class="sxs-lookup"><span data-stu-id="4ce6d-107">The following sections describe attributes, child elements, and the parent element of the `DisplayError` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4ce6d-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="4ce6d-108">Attributes</span></span>

<span data-ttu-id="4ce6d-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="4ce6d-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4ce6d-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="4ce6d-110">Child Elements</span></span>

<span data-ttu-id="4ce6d-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="4ce6d-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4ce6d-112">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="4ce6d-112">Parent Elements</span></span>

|<span data-ttu-id="4ce6d-113">Element</span><span class="sxs-lookup"><span data-stu-id="4ce6d-113">Element</span></span>|<span data-ttu-id="4ce6d-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="4ce6d-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4ce6d-115">DefaultSettings Element (Format)</span><span class="sxs-lookup"><span data-stu-id="4ce6d-115">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="4ce6d-116">Definierar gemensamma inställningar som gäller för alla vyer i filen formatering.</span><span class="sxs-lookup"><span data-stu-id="4ce6d-116">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4ce6d-117">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="4ce6d-117">Remarks</span></span>

<span data-ttu-id="4ce6d-118">Som standard när ett fel uppstår när du försöker visa en typ av data, är platsen för dina data tomt.</span><span class="sxs-lookup"><span data-stu-id="4ce6d-118">By default, when an error occurs while trying to display a piece of data, the location of the data is left blank.</span></span> <span data-ttu-id="4ce6d-119">När det här elementet har angetts till true, #ERR sträng visas.</span><span class="sxs-lookup"><span data-stu-id="4ce6d-119">When this element is set to true, the #ERR string will be displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="4ce6d-120">Se även</span><span class="sxs-lookup"><span data-stu-id="4ce6d-120">See Also</span></span>

[<span data-ttu-id="4ce6d-121">DefaultSettings Element (Format)</span><span class="sxs-lookup"><span data-stu-id="4ce6d-121">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="4ce6d-122">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="4ce6d-122">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
