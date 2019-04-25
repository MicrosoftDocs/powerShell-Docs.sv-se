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
ms.openlocfilehash: 2c6a3d678ca68dc0d189f6ab981fdea5fef894cb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066268"
---
# <a name="displayerror-element-format"></a><span data-ttu-id="386d6-102">DisplayError-element (format)</span><span class="sxs-lookup"><span data-stu-id="386d6-102">DisplayError Element (Format)</span></span>

<span data-ttu-id="386d6-103">Anger att strängen #ERR visas när ett fel uppstår visar en typ av data.</span><span class="sxs-lookup"><span data-stu-id="386d6-103">Specifies that the string #ERR is displayed when an error occurs displaying a piece of data.</span></span>

<span data-ttu-id="386d6-104">Elementet (Format) DefaultSettings Element (Format) DisplayError konfigurationselement (Format)</span><span class="sxs-lookup"><span data-stu-id="386d6-104">Configuration Element (Format) DefaultSettings Element (Format) DisplayError Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="386d6-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="386d6-105">Syntax</span></span>

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="386d6-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="386d6-106">Attributes and Elements</span></span>

<span data-ttu-id="386d6-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `DisplayError` element.</span><span class="sxs-lookup"><span data-stu-id="386d6-107">The following sections describe attributes, child elements, and the parent element of the `DisplayError` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="386d6-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="386d6-108">Attributes</span></span>

<span data-ttu-id="386d6-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="386d6-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="386d6-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="386d6-110">Child Elements</span></span>

<span data-ttu-id="386d6-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="386d6-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="386d6-112">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="386d6-112">Parent Elements</span></span>

|<span data-ttu-id="386d6-113">Element</span><span class="sxs-lookup"><span data-stu-id="386d6-113">Element</span></span>|<span data-ttu-id="386d6-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="386d6-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="386d6-115">DefaultSettings Element (Format)</span><span class="sxs-lookup"><span data-stu-id="386d6-115">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="386d6-116">Definierar gemensamma inställningar som gäller för alla vyer i filen formatering.</span><span class="sxs-lookup"><span data-stu-id="386d6-116">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="386d6-117">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="386d6-117">Remarks</span></span>

<span data-ttu-id="386d6-118">Som standard när ett fel uppstår när du försöker visa en typ av data, är platsen för dina data tomt.</span><span class="sxs-lookup"><span data-stu-id="386d6-118">By default, when an error occurs while trying to display a piece of data, the location of the data is left blank.</span></span> <span data-ttu-id="386d6-119">När det här elementet har angetts till true, #ERR sträng visas.</span><span class="sxs-lookup"><span data-stu-id="386d6-119">When this element is set to true, the #ERR string will be displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="386d6-120">Se även</span><span class="sxs-lookup"><span data-stu-id="386d6-120">See Also</span></span>

[<span data-ttu-id="386d6-121">DefaultSettings Element (Format)</span><span class="sxs-lookup"><span data-stu-id="386d6-121">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="386d6-122">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="386d6-122">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
