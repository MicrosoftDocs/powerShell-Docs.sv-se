---
title: PropertyName-element för SelectionCondition för kontroller för vy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92c4237d-c2b2-4908-82ac-f36070f89d26
caps.latest.revision: 6
ms.openlocfilehash: 79859bed3d762948182e03babf71d4270278bae7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354077"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="b2c73-102">PropertyName-element för SelectionCondition för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="b2c73-102">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="b2c73-103">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="b2c73-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="b2c73-104">När den här egenskapen finns eller när den utvärderas till `true`, uppfylls villkoret och posten används.</span><span class="sxs-lookup"><span data-stu-id="b2c73-104">When this property is present or when it evaluates to `true`, the condition is met, and the entry is used.</span></span> <span data-ttu-id="b2c73-105">Det här elementet används när du definierar kontroller som kan användas av en vy.</span><span class="sxs-lookup"><span data-stu-id="b2c73-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="b2c73-106">Konfigurations element (format) ViewDefinitions element (format) View-element (format) styr element (format) styr element (format) styr element för Controls (format) CustomControl-element för kontroll för Control for View (format) CustomEntries-element för CustomControl for Controls for View (format) CustomEntry-elementet för CustomEntries for Controls for View (format) EntrySelectedBy-elementet for CustomEntry for Controls for View (format) SelectionCondition element for EntrySelectedBy for Controls for View ( Format) PropertyName-element för SelectionCondition för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="b2c73-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b2c73-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="b2c73-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b2c73-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="b2c73-108">Attributes and Elements</span></span>

<span data-ttu-id="b2c73-109">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `PropertyName`-elementet.</span><span class="sxs-lookup"><span data-stu-id="b2c73-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b2c73-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="b2c73-110">Attributes</span></span>

<span data-ttu-id="b2c73-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="b2c73-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b2c73-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="b2c73-112">Child Elements</span></span>

<span data-ttu-id="b2c73-113">Ingen.</span><span class="sxs-lookup"><span data-stu-id="b2c73-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b2c73-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="b2c73-114">Parent Elements</span></span>

|<span data-ttu-id="b2c73-115">Element</span><span class="sxs-lookup"><span data-stu-id="b2c73-115">Element</span></span>|<span data-ttu-id="b2c73-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b2c73-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b2c73-117">SelectionCondition-element för EntrySelectedBy för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="b2c73-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="b2c73-118">Definierar ett villkor som måste finnas för att den kontroll definition som ska användas.</span><span class="sxs-lookup"><span data-stu-id="b2c73-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b2c73-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="b2c73-119">Text Value</span></span>

<span data-ttu-id="b2c73-120">Ange .NET-egenskaps namnet.</span><span class="sxs-lookup"><span data-stu-id="b2c73-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="b2c73-121">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="b2c73-121">Remarks</span></span>

<span data-ttu-id="b2c73-122">Urvals villkoret måste ange minst ett egenskaps namn eller ett skript, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="b2c73-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="b2c73-123">Mer information om hur urvals villkor kan användas finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="b2c73-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b2c73-124">Se även</span><span class="sxs-lookup"><span data-stu-id="b2c73-124">See Also</span></span>

[<span data-ttu-id="b2c73-125">SelectionCondition-element för EntrySelectedBy för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="b2c73-125">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="b2c73-126">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="b2c73-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
