---
title: PropertyName-element för SelectionCondition för CustomControl för vy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: aa3955b84b8de9901f394e8108f31440fcb6c942
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780805"
---
# <a name="propertyname-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="e40ef-102">PropertyName-element för SelectionCondition för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="e40ef-102">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="e40ef-103">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="e40ef-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="e40ef-104">När den här egenskapen finns eller när den utvärderas `true` , uppfylls villkoret och definitionen används.</span><span class="sxs-lookup"><span data-stu-id="e40ef-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="e40ef-105">Det här elementet används när du definierar en anpassad kontrol vy.</span><span class="sxs-lookup"><span data-stu-id="e40ef-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="e40ef-106">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) CustomControl-element för View (format) CustomEntries-element för CustomControl för View (format) CustomEntry-element för CustomEntries för CustomControl för View (format) CustomItem-element för CustomEntry för CustomControl för View (format) EntrySelectedBy-element för CustomEntry för CustomControl för View (format) SelectionCondition-element för EntrySelectedBy för CustomControl för View (format) PropertyName-element för SelectionCondition för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="e40ef-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) EntrySelectedBy Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e40ef-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="e40ef-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e40ef-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="e40ef-108">Attributes and Elements</span></span>

<span data-ttu-id="e40ef-109">I följande avsnitt beskrivs attribut, underordnade element och `PropertyName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="e40ef-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e40ef-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="e40ef-110">Attributes</span></span>

<span data-ttu-id="e40ef-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="e40ef-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e40ef-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="e40ef-112">Child Elements</span></span>

<span data-ttu-id="e40ef-113">Inga.</span><span class="sxs-lookup"><span data-stu-id="e40ef-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e40ef-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="e40ef-114">Parent Elements</span></span>

|<span data-ttu-id="e40ef-115">Element</span><span class="sxs-lookup"><span data-stu-id="e40ef-115">Element</span></span>|<span data-ttu-id="e40ef-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e40ef-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e40ef-117">SelectionCondition-element för EntrySelectedBy för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="e40ef-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="e40ef-118">Definierar ett villkor som måste finnas för att den kontroll definition som ska användas.</span><span class="sxs-lookup"><span data-stu-id="e40ef-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e40ef-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="e40ef-119">Text Value</span></span>

<span data-ttu-id="e40ef-120">Ange .NET-egenskaps namnet.</span><span class="sxs-lookup"><span data-stu-id="e40ef-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="e40ef-121">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="e40ef-121">Remarks</span></span>

<span data-ttu-id="e40ef-122">Urvals villkoret måste ange minst ett egenskaps namn eller ett skript, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="e40ef-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="e40ef-123">Mer information om hur urvals villkor kan användas finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="e40ef-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e40ef-124">Se även</span><span class="sxs-lookup"><span data-stu-id="e40ef-124">See Also</span></span>

[<span data-ttu-id="e40ef-125">SelectionCondition-element för EntrySelectedBy för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="e40ef-125">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="e40ef-126">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="e40ef-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
