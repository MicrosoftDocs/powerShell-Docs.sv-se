---
title: PropertyName-Element för SelectionCondition för GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d1707317-6c26-4866-bcc1-8924103c9014
caps.latest.revision: 6
ms.openlocfilehash: 7241ea0ea364befa7ad4ab0af4c4209be72214a7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064823"
---
# <a name="propertyname-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="7e8f1-102">PropertyName-element för SelectionCondition för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="7e8f1-102">PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="7e8f1-103">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="7e8f1-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="7e8f1-104">När den här egenskapen finns eller att inventera till `true`villkoret uppfylls och definitionen används.</span><span class="sxs-lookup"><span data-stu-id="7e8f1-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="7e8f1-105">Det här elementet används när du definierar hur en ny grupp med objekt visas.</span><span class="sxs-lookup"><span data-stu-id="7e8f1-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="7e8f1-106">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) GroupBy konfigurationselement för Visa (Format) anpassad kontroll elementet för GroupBy (Format) CustomEntries Element för anpassad kontroll för GroupBy (Format) CustomEntry elementet för Anpassad kontroll för GroupBy (Format) EntrySelectedBy elementet för CustomEntry för GroupBy (Format) SelectionCondition elementet för EntrySelectedBy för GroupBy (Format) PropertyName elementet för SelectionCondition för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7e8f1-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7e8f1-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="7e8f1-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7e8f1-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="7e8f1-108">Attributes and Elements</span></span>

<span data-ttu-id="7e8f1-109">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `PropertyName` element.</span><span class="sxs-lookup"><span data-stu-id="7e8f1-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7e8f1-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="7e8f1-110">Attributes</span></span>

<span data-ttu-id="7e8f1-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="7e8f1-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7e8f1-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="7e8f1-112">Child Elements</span></span>

<span data-ttu-id="7e8f1-113">Ingen.</span><span class="sxs-lookup"><span data-stu-id="7e8f1-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7e8f1-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="7e8f1-114">Parent Elements</span></span>

|<span data-ttu-id="7e8f1-115">Element</span><span class="sxs-lookup"><span data-stu-id="7e8f1-115">Element</span></span>|<span data-ttu-id="7e8f1-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7e8f1-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7e8f1-117">SelectionCondition Element för EntrySelectedBy för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7e8f1-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="7e8f1-118">Definierar ett villkor som måste finnas för kontrolldefinition som ska användas.</span><span class="sxs-lookup"><span data-stu-id="7e8f1-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7e8f1-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="7e8f1-119">Text Value</span></span>

<span data-ttu-id="7e8f1-120">Ange namnet på .NET-egenskapen.</span><span class="sxs-lookup"><span data-stu-id="7e8f1-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="7e8f1-121">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="7e8f1-121">Remarks</span></span>

<span data-ttu-id="7e8f1-122">Urvalsvillkoret måste ange ett namn med minst en egenskap eller ett skript, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="7e8f1-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="7e8f1-123">Läs mer om hur du kan använda villkor för val av [definiera villkor för att visa Data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="7e8f1-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7e8f1-124">Se även</span><span class="sxs-lookup"><span data-stu-id="7e8f1-124">See Also</span></span>

[<span data-ttu-id="7e8f1-125">SelectionCondition Element för EntrySelectedBy för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7e8f1-125">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="7e8f1-126">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="7e8f1-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
