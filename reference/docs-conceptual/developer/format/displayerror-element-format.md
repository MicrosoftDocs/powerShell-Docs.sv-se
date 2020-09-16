---
title: DisplayError-element (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 5d46c2fbd48f592db5ba1b33eb6cead8dc1c4698
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774294"
---
# <a name="displayerror-element-format"></a><span data-ttu-id="2a006-102">DisplayError-element (format)</span><span class="sxs-lookup"><span data-stu-id="2a006-102">DisplayError Element (Format)</span></span>

<span data-ttu-id="2a006-103">Anger att strängen #ERR visas när det uppstår ett fel vid visning av en data del.</span><span class="sxs-lookup"><span data-stu-id="2a006-103">Specifies that the string #ERR is displayed when an error occurs displaying a piece of data.</span></span>

<span data-ttu-id="2a006-104">Konfigurations element (format) DefaultSettings-element (format) DisplayError-element (format)</span><span class="sxs-lookup"><span data-stu-id="2a006-104">Configuration Element (Format) DefaultSettings Element (Format) DisplayError Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2a006-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="2a006-105">Syntax</span></span>

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2a006-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="2a006-106">Attributes and Elements</span></span>

<span data-ttu-id="2a006-107">I följande avsnitt beskrivs attribut, underordnade element och `DisplayError` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="2a006-107">The following sections describe attributes, child elements, and the parent element of the `DisplayError` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2a006-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="2a006-108">Attributes</span></span>

<span data-ttu-id="2a006-109">Inga.</span><span class="sxs-lookup"><span data-stu-id="2a006-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2a006-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="2a006-110">Child Elements</span></span>

<span data-ttu-id="2a006-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="2a006-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2a006-112">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="2a006-112">Parent Elements</span></span>

|<span data-ttu-id="2a006-113">Element</span><span class="sxs-lookup"><span data-stu-id="2a006-113">Element</span></span>|<span data-ttu-id="2a006-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="2a006-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2a006-115">DefaultSettings-element (format)</span><span class="sxs-lookup"><span data-stu-id="2a006-115">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="2a006-116">Definierar vanliga inställningar som gäller för alla vyer i formaterings filen.</span><span class="sxs-lookup"><span data-stu-id="2a006-116">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2a006-117">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="2a006-117">Remarks</span></span>

<span data-ttu-id="2a006-118">När ett fel inträffar när ett fel inträffar när ett data försöker visas, lämnas som standard data platsen tom.</span><span class="sxs-lookup"><span data-stu-id="2a006-118">By default, when an error occurs while trying to display a piece of data, the location of the data is left blank.</span></span> <span data-ttu-id="2a006-119">När det här elementet är inställt på True visas #ERR strängen.</span><span class="sxs-lookup"><span data-stu-id="2a006-119">When this element is set to true, the #ERR string will be displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="2a006-120">Se även</span><span class="sxs-lookup"><span data-stu-id="2a006-120">See Also</span></span>

[<span data-ttu-id="2a006-121">DefaultSettings-element (format)</span><span class="sxs-lookup"><span data-stu-id="2a006-121">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="2a006-122">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="2a006-122">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
