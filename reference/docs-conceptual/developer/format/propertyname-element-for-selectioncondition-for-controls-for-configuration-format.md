---
title: PropertyName-element för SelectionCondition för kontroll av konfiguration (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 7730951a840fcfcd8bf819fff5182049bd6b6c23
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773138"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="880ed-102">PropertyName-element för SelectionCondition för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="880ed-102">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="880ed-103">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="880ed-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="880ed-104">När den här egenskapen finns eller när den utvärderas `true` , uppfylls villkoret och posten används.</span><span class="sxs-lookup"><span data-stu-id="880ed-104">When this property is present or when it evaluates to `true`, the condition is met, and the entry is used.</span></span> <span data-ttu-id="880ed-105">Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.</span><span class="sxs-lookup"><span data-stu-id="880ed-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="880ed-106">Konfigurations element (format) styr element i konfigurations-(format)-kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för Configuration (format) CustomEntry-elementet för CustomControl for Controls for Configuration (format) EntrySelectedBy-elementet för CustomEntry for Controls for Configuration (format) SelectionCondition element for EntrySelectedBy for CustomEntry for Configuration (format) PropertyName-element för SelectionCondition för EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="880ed-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="880ed-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="880ed-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="880ed-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="880ed-108">Attributes and Elements</span></span>

<span data-ttu-id="880ed-109">I följande avsnitt beskrivs attribut, underordnade element och `PropertyName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="880ed-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="880ed-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="880ed-110">Attributes</span></span>

<span data-ttu-id="880ed-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="880ed-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="880ed-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="880ed-112">Child Elements</span></span>

<span data-ttu-id="880ed-113">Inga.</span><span class="sxs-lookup"><span data-stu-id="880ed-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="880ed-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="880ed-114">Parent Elements</span></span>

|<span data-ttu-id="880ed-115">Element</span><span class="sxs-lookup"><span data-stu-id="880ed-115">Element</span></span>|<span data-ttu-id="880ed-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="880ed-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="880ed-117">SelectionCondition-element för EntrySelectedBy för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="880ed-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="880ed-118">Definierar ett villkor som måste finnas för att en gemensam kontroll definition ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="880ed-118">Defines a condition that must exist for a common control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="880ed-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="880ed-119">Text Value</span></span>

<span data-ttu-id="880ed-120">Ange .NET-egenskaps namnet.</span><span class="sxs-lookup"><span data-stu-id="880ed-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="880ed-121">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="880ed-121">Remarks</span></span>

<span data-ttu-id="880ed-122">Urvals villkoret måste ange minst ett egenskaps namn eller ett skript, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="880ed-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="880ed-123">Mer information om hur urvals villkor kan användas finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="880ed-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="880ed-124">Se även</span><span class="sxs-lookup"><span data-stu-id="880ed-124">See Also</span></span>

[<span data-ttu-id="880ed-125">SelectionCondition-element för EntrySelectedBy för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="880ed-125">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="880ed-126">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="880ed-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
