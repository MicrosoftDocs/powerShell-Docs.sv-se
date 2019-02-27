---
title: TypeName-Element för EntrySelectedBy för GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b8b6739b-770c-432a-95ab-551c7507c51f
caps.latest.revision: 6
ms.openlocfilehash: 3b5ce60d3a0d76988af48f49445a5478a415d498
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850780"
---
# <a name="typename-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="d2acb-102">TypeName-element för EntrySelectedBy för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="d2acb-102">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="d2acb-103">Anger ett .NET-typ som använder den här definitionen av den anpassade kontrollen.</span><span class="sxs-lookup"><span data-stu-id="d2acb-103">Specifies a .NET type that uses this definition of the custom control.</span></span> <span data-ttu-id="d2acb-104">Det här elementet används när du definierar hur en ny grupp med objekt visas.</span><span class="sxs-lookup"><span data-stu-id="d2acb-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="d2acb-105">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) GroupBy konfigurationselement för Visa (Format) anpassad kontroll elementet för GroupBy (Format) CustomEntries Element för anpassad kontroll för GroupBy (Format) CustomEntry elementet för Anpassad kontroll för GroupBy (Format) EntrySelectedBy elementet för CustomEntry för GroupBy (Format) TypeName-elementet för EntrySelectedBy för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="d2acb-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d2acb-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="d2acb-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d2acb-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="d2acb-107">Attributes and Elements</span></span>

<span data-ttu-id="d2acb-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `TypeName` element.</span><span class="sxs-lookup"><span data-stu-id="d2acb-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d2acb-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="d2acb-109">Attributes</span></span>

<span data-ttu-id="d2acb-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="d2acb-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d2acb-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="d2acb-111">Child Elements</span></span>

<span data-ttu-id="d2acb-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="d2acb-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d2acb-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="d2acb-113">Parent Elements</span></span>

|<span data-ttu-id="d2acb-114">Element</span><span class="sxs-lookup"><span data-stu-id="d2acb-114">Element</span></span>|<span data-ttu-id="d2acb-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d2acb-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d2acb-116">EntrySelectedBy Element för CustomEntry för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="d2acb-116">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="d2acb-117">Definierar vilka typer av .NET som använder den här kontrollen definitionen eller villkor som måste finnas för den här definitionen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="d2acb-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d2acb-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="d2acb-118">Text Value</span></span>

<span data-ttu-id="d2acb-119">Ange det fullständigt kvalificerade namnet för .NET-typ, till exempel `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="d2acb-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="d2acb-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="d2acb-120">Remarks</span></span>

<span data-ttu-id="d2acb-121">Varje kontrolldefinition måste ha minst ett namn, val av set eller Urvalsvillkoret som definierats.</span><span class="sxs-lookup"><span data-stu-id="d2acb-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="d2acb-122">Mer information om komponenter för en anpassad kontroll vy finns i [skapar anpassade kontroller](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="d2acb-122">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d2acb-123">Se även</span><span class="sxs-lookup"><span data-stu-id="d2acb-123">See Also</span></span>

[<span data-ttu-id="d2acb-124">Skapa anpassade kontroller</span><span class="sxs-lookup"><span data-stu-id="d2acb-124">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="d2acb-125">EntrySelectedBy Element för CustomEntry för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="d2acb-125">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="d2acb-126">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="d2acb-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
