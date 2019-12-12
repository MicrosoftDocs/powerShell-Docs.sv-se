---
title: DisplayError-element (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45c45800-a87d-456e-b07c-12d4d8c27c67
caps.latest.revision: 8
ms.openlocfilehash: 2c6a3d678ca68dc0d189f6ab981fdea5fef894cb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355218"
---
# <a name="displayerror-element-format"></a><span data-ttu-id="c3556-102">DisplayError-element (format)</span><span class="sxs-lookup"><span data-stu-id="c3556-102">DisplayError Element (Format)</span></span>

<span data-ttu-id="c3556-103">Anger att strängen #ERR visas när det uppstår ett fel vid visning av en data del.</span><span class="sxs-lookup"><span data-stu-id="c3556-103">Specifies that the string #ERR is displayed when an error occurs displaying a piece of data.</span></span>

<span data-ttu-id="c3556-104">Konfigurations element (format) DefaultSettings-element (format) DisplayError-element (format)</span><span class="sxs-lookup"><span data-stu-id="c3556-104">Configuration Element (Format) DefaultSettings Element (Format) DisplayError Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c3556-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="c3556-105">Syntax</span></span>

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c3556-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="c3556-106">Attributes and Elements</span></span>

<span data-ttu-id="c3556-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `DisplayError`-elementet.</span><span class="sxs-lookup"><span data-stu-id="c3556-107">The following sections describe attributes, child elements, and the parent element of the `DisplayError` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c3556-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="c3556-108">Attributes</span></span>

<span data-ttu-id="c3556-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="c3556-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c3556-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="c3556-110">Child Elements</span></span>

<span data-ttu-id="c3556-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="c3556-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c3556-112">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="c3556-112">Parent Elements</span></span>

|<span data-ttu-id="c3556-113">Element</span><span class="sxs-lookup"><span data-stu-id="c3556-113">Element</span></span>|<span data-ttu-id="c3556-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c3556-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c3556-115">DefaultSettings-element (format)</span><span class="sxs-lookup"><span data-stu-id="c3556-115">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="c3556-116">Definierar vanliga inställningar som gäller för alla vyer i formaterings filen.</span><span class="sxs-lookup"><span data-stu-id="c3556-116">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c3556-117">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="c3556-117">Remarks</span></span>

<span data-ttu-id="c3556-118">När ett fel inträffar när ett fel inträffar när ett data försöker visas, lämnas som standard data platsen tom.</span><span class="sxs-lookup"><span data-stu-id="c3556-118">By default, when an error occurs while trying to display a piece of data, the location of the data is left blank.</span></span> <span data-ttu-id="c3556-119">När det här elementet är inställt på True visas #ERR strängen.</span><span class="sxs-lookup"><span data-stu-id="c3556-119">When this element is set to true, the #ERR string will be displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="c3556-120">Se även</span><span class="sxs-lookup"><span data-stu-id="c3556-120">See Also</span></span>

[<span data-ttu-id="c3556-121">DefaultSettings-element (format)</span><span class="sxs-lookup"><span data-stu-id="c3556-121">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="c3556-122">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="c3556-122">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
