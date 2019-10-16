---
title: PropertyName-element för SelectionCondition för GroupBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d1707317-6c26-4866-bcc1-8924103c9014
caps.latest.revision: 6
ms.openlocfilehash: 7241ea0ea364befa7ad4ab0af4c4209be72214a7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355890"
---
# <a name="propertyname-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="b4c34-102">PropertyName-element för SelectionCondition för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="b4c34-102">PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="b4c34-103">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="b4c34-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="b4c34-104">När den här egenskapen finns eller när den utvärderas till `true`, uppfylls villkoret och definitionen används.</span><span class="sxs-lookup"><span data-stu-id="b4c34-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="b4c34-105">Det här elementet används när du definierar hur en ny grupp av objekt visas.</span><span class="sxs-lookup"><span data-stu-id="b4c34-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="b4c34-106">Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for GroupBy (format) CustomEntry-element för CustomControl for GroupBy (format) EntrySelectedBy-element för CustomEntry för GroupBy (format) SelectionCondition-element för EntrySelectedBy för GroupBy (format) PropertyName-element för SelectionCondition för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="b4c34-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b4c34-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="b4c34-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b4c34-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="b4c34-108">Attributes and Elements</span></span>

<span data-ttu-id="b4c34-109">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för elementet `PropertyName`.</span><span class="sxs-lookup"><span data-stu-id="b4c34-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b4c34-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="b4c34-110">Attributes</span></span>

<span data-ttu-id="b4c34-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="b4c34-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b4c34-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="b4c34-112">Child Elements</span></span>

<span data-ttu-id="b4c34-113">Ingen.</span><span class="sxs-lookup"><span data-stu-id="b4c34-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b4c34-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="b4c34-114">Parent Elements</span></span>

|<span data-ttu-id="b4c34-115">Element</span><span class="sxs-lookup"><span data-stu-id="b4c34-115">Element</span></span>|<span data-ttu-id="b4c34-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b4c34-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b4c34-117">SelectionCondition-element för EntrySelectedBy för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="b4c34-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="b4c34-118">Definierar ett villkor som måste finnas för att den kontroll definition som ska användas.</span><span class="sxs-lookup"><span data-stu-id="b4c34-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b4c34-119">Text värde</span><span class="sxs-lookup"><span data-stu-id="b4c34-119">Text Value</span></span>

<span data-ttu-id="b4c34-120">Ange .NET-egenskaps namnet.</span><span class="sxs-lookup"><span data-stu-id="b4c34-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="b4c34-121">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="b4c34-121">Remarks</span></span>

<span data-ttu-id="b4c34-122">Urvals villkoret måste ange minst ett egenskaps namn eller ett skript, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="b4c34-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="b4c34-123">Mer information om hur urvals villkor kan användas finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="b4c34-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b4c34-124">Se även</span><span class="sxs-lookup"><span data-stu-id="b4c34-124">See Also</span></span>

[<span data-ttu-id="b4c34-125">SelectionCondition-element för EntrySelectedBy för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="b4c34-125">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="b4c34-126">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="b4c34-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
