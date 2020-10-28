---
ms.date: 09/13/2016
ms.topic: reference
title: DisplayError-element (format)
description: DisplayError-element (format)
ms.openlocfilehash: fb54df86a3558263687a8c417870495b7066f563
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92649927"
---
# <a name="displayerror-element-format"></a><span data-ttu-id="508d1-103">DisplayError-element (format)</span><span class="sxs-lookup"><span data-stu-id="508d1-103">DisplayError Element (Format)</span></span>

<span data-ttu-id="508d1-104">Anger att strängen #ERR visas när det uppstår ett fel vid visning av en data del.</span><span class="sxs-lookup"><span data-stu-id="508d1-104">Specifies that the string #ERR is displayed when an error occurs displaying a piece of data.</span></span>

<span data-ttu-id="508d1-105">Konfigurations element (format) DefaultSettings-element (format) DisplayError-element (format)</span><span class="sxs-lookup"><span data-stu-id="508d1-105">Configuration Element (Format) DefaultSettings Element (Format) DisplayError Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="508d1-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="508d1-106">Syntax</span></span>

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="508d1-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="508d1-107">Attributes and Elements</span></span>

<span data-ttu-id="508d1-108">I följande avsnitt beskrivs attribut, underordnade element och `DisplayError` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="508d1-108">The following sections describe attributes, child elements, and the parent element of the `DisplayError` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="508d1-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="508d1-109">Attributes</span></span>

<span data-ttu-id="508d1-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="508d1-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="508d1-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="508d1-111">Child Elements</span></span>

<span data-ttu-id="508d1-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="508d1-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="508d1-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="508d1-113">Parent Elements</span></span>

|<span data-ttu-id="508d1-114">Element</span><span class="sxs-lookup"><span data-stu-id="508d1-114">Element</span></span>|<span data-ttu-id="508d1-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="508d1-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="508d1-116">DefaultSettings-element (format)</span><span class="sxs-lookup"><span data-stu-id="508d1-116">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="508d1-117">Definierar vanliga inställningar som gäller för alla vyer i formaterings filen.</span><span class="sxs-lookup"><span data-stu-id="508d1-117">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="508d1-118">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="508d1-118">Remarks</span></span>

<span data-ttu-id="508d1-119">När ett fel inträffar när ett fel inträffar när ett data försöker visas, lämnas som standard data platsen tom.</span><span class="sxs-lookup"><span data-stu-id="508d1-119">By default, when an error occurs while trying to display a piece of data, the location of the data is left blank.</span></span> <span data-ttu-id="508d1-120">När det här elementet är inställt på True visas #ERR strängen.</span><span class="sxs-lookup"><span data-stu-id="508d1-120">When this element is set to true, the #ERR string will be displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="508d1-121">Se även</span><span class="sxs-lookup"><span data-stu-id="508d1-121">See Also</span></span>

[<span data-ttu-id="508d1-122">DefaultSettings-element (format)</span><span class="sxs-lookup"><span data-stu-id="508d1-122">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="508d1-123">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="508d1-123">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
