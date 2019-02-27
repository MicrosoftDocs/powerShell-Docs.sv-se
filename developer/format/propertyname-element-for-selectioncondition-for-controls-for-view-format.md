---
title: PropertyName-Element för SelectionCondition för kontroller för att visa (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92c4237d-c2b2-4908-82ac-f36070f89d26
caps.latest.revision: 6
ms.openlocfilehash: 79859bed3d762948182e03babf71d4270278bae7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845082"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="37892-102">PropertyName-element för SelectionCondition för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="37892-102">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="37892-103">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="37892-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="37892-104">När den här egenskapen finns eller att inventera till `true`villkoret uppfylls och posten används.</span><span class="sxs-lookup"><span data-stu-id="37892-104">When this property is present or when it evaluates to `true`, the condition is met, and the entry is used.</span></span> <span data-ttu-id="37892-105">Det här elementet används när du definierar kontroller som kan användas av en vy.</span><span class="sxs-lookup"><span data-stu-id="37892-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="37892-106">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) kontroller Element (Format) kontroll konfigurationselement för kontroller för att visa (Format) anpassad kontroll Element för kontroll för kontroller för att visa (Format) CustomEntries Element för Anpassad kontroll för kontroller för att visa (Format) CustomEntry Element för CustomEntries för kontroller för att visa (Format) EntrySelectedBy Element för CustomEntry för kontroller för att visa (Format) SelectionCondition Element för EntrySelectedBy för kontroller för att visa ( Format) PropertyName Element för SelectionCondition för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="37892-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="37892-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="37892-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="37892-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="37892-108">Attributes and Elements</span></span>

<span data-ttu-id="37892-109">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `PropertyName` element.</span><span class="sxs-lookup"><span data-stu-id="37892-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="37892-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="37892-110">Attributes</span></span>

<span data-ttu-id="37892-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="37892-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="37892-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="37892-112">Child Elements</span></span>

<span data-ttu-id="37892-113">Ingen.</span><span class="sxs-lookup"><span data-stu-id="37892-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="37892-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="37892-114">Parent Elements</span></span>

|<span data-ttu-id="37892-115">Element</span><span class="sxs-lookup"><span data-stu-id="37892-115">Element</span></span>|<span data-ttu-id="37892-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="37892-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="37892-117">SelectionCondition Element för EntrySelectedBy för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="37892-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="37892-118">Definierar ett villkor som måste finnas för kontrolldefinition som ska användas.</span><span class="sxs-lookup"><span data-stu-id="37892-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="37892-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="37892-119">Text Value</span></span>

<span data-ttu-id="37892-120">Ange namnet på .NET-egenskapen.</span><span class="sxs-lookup"><span data-stu-id="37892-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="37892-121">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="37892-121">Remarks</span></span>

<span data-ttu-id="37892-122">Urvalsvillkoret måste ange ett namn med minst en egenskap eller ett skript, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="37892-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="37892-123">Läs mer om hur du kan använda villkor för val av [definiera villkor för att visa Data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="37892-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="37892-124">Se även</span><span class="sxs-lookup"><span data-stu-id="37892-124">See Also</span></span>

[<span data-ttu-id="37892-125">SelectionCondition Element för EntrySelectedBy för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="37892-125">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="37892-126">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="37892-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
