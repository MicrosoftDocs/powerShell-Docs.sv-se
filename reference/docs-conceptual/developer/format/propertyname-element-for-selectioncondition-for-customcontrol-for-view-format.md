---
title: PropertyName-element för SelectionCondition för CustomControl för vy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fc48a417-2083-46d4-ac38-16c12e65b6b9
caps.latest.revision: 7
ms.openlocfilehash: e08037d5d051d3be51e90193c7e87cc2e738f78a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354070"
---
# <a name="propertyname-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="f5f3e-102">PropertyName-element för SelectionCondition för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="f5f3e-102">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="f5f3e-103">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="f5f3e-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="f5f3e-104">När den här egenskapen finns eller när den utvärderas till `true`, uppfylls villkoret och definitionen används.</span><span class="sxs-lookup"><span data-stu-id="f5f3e-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="f5f3e-105">Det här elementet används när du definierar en anpassad kontrol vy.</span><span class="sxs-lookup"><span data-stu-id="f5f3e-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="f5f3e-106">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) CustomControl-element för View (format) CustomEntries-element för CustomControl för View (format) CustomEntry-element för CustomEntries för View Format) CustomItem-element för CustomEntry för CustomControl för View (format) EntrySelectedBy-element för CustomEntry för CustomControl för View (format) SelectionCondition-element för EntrySelectedBy för View (format) PropertyName Element för SelectionCondition för CustomControl för vy (format)</span><span class="sxs-lookup"><span data-stu-id="f5f3e-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) EntrySelectedBy Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f5f3e-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="f5f3e-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f5f3e-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="f5f3e-108">Attributes and Elements</span></span>

<span data-ttu-id="f5f3e-109">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `PropertyName`-elementet.</span><span class="sxs-lookup"><span data-stu-id="f5f3e-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f5f3e-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="f5f3e-110">Attributes</span></span>

<span data-ttu-id="f5f3e-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="f5f3e-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f5f3e-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="f5f3e-112">Child Elements</span></span>

<span data-ttu-id="f5f3e-113">Ingen.</span><span class="sxs-lookup"><span data-stu-id="f5f3e-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f5f3e-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="f5f3e-114">Parent Elements</span></span>

|<span data-ttu-id="f5f3e-115">Element</span><span class="sxs-lookup"><span data-stu-id="f5f3e-115">Element</span></span>|<span data-ttu-id="f5f3e-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f5f3e-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f5f3e-117">SelectionCondition-element för EntrySelectedBy för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="f5f3e-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="f5f3e-118">Definierar ett villkor som måste finnas för att den kontroll definition som ska användas.</span><span class="sxs-lookup"><span data-stu-id="f5f3e-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f5f3e-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="f5f3e-119">Text Value</span></span>

<span data-ttu-id="f5f3e-120">Ange .NET-egenskaps namnet.</span><span class="sxs-lookup"><span data-stu-id="f5f3e-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="f5f3e-121">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="f5f3e-121">Remarks</span></span>

<span data-ttu-id="f5f3e-122">Urvals villkoret måste ange minst ett egenskaps namn eller ett skript, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="f5f3e-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="f5f3e-123">Mer information om hur urvals villkor kan användas finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="f5f3e-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f5f3e-124">Se även</span><span class="sxs-lookup"><span data-stu-id="f5f3e-124">See Also</span></span>

[<span data-ttu-id="f5f3e-125">SelectionCondition-element för EntrySelectedBy för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="f5f3e-125">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="f5f3e-126">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="f5f3e-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
