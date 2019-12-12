---
title: PropertyName-element för SelectionCondition för kontroll av konfiguration (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec048408-e1c6-41ef-b39b-72f4c2dcf2ac
caps.latest.revision: 6
ms.openlocfilehash: b4b2440fdb7171d09fdc16ac7cc4f25ed1a4bb78
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354105"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="3ee04-102">PropertyName-element för SelectionCondition för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="3ee04-102">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="3ee04-103">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="3ee04-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="3ee04-104">När den här egenskapen finns eller när den utvärderas till `true`, uppfylls villkoret och posten används.</span><span class="sxs-lookup"><span data-stu-id="3ee04-104">When this property is present or when it evaluates to `true`, the condition is met, and the entry is used.</span></span> <span data-ttu-id="3ee04-105">Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.</span><span class="sxs-lookup"><span data-stu-id="3ee04-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="3ee04-106">Konfigurations element (format) styr element i konfigurations-(format) kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för konfiguration ( Format) CustomEntry-element för CustomControl for Controls for Configuration (format) EntrySelectedBy-element för CustomEntry for Controls for Configuration (format) SelectionCondition-element för EntrySelectedBy för CustomEntry för konfiguration ( Format) PropertyName-element för SelectionCondition för EntrySelectedBy för ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="3ee04-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3ee04-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="3ee04-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3ee04-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="3ee04-108">Attributes and Elements</span></span>

<span data-ttu-id="3ee04-109">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `PropertyName`-elementet.</span><span class="sxs-lookup"><span data-stu-id="3ee04-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3ee04-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="3ee04-110">Attributes</span></span>

<span data-ttu-id="3ee04-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="3ee04-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3ee04-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="3ee04-112">Child Elements</span></span>

<span data-ttu-id="3ee04-113">Ingen.</span><span class="sxs-lookup"><span data-stu-id="3ee04-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3ee04-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="3ee04-114">Parent Elements</span></span>

|<span data-ttu-id="3ee04-115">Element</span><span class="sxs-lookup"><span data-stu-id="3ee04-115">Element</span></span>|<span data-ttu-id="3ee04-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="3ee04-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3ee04-117">SelectionCondition-element för EntrySelectedBy för kontroller för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="3ee04-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="3ee04-118">Definierar ett villkor som måste finnas för att en gemensam kontroll definition ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="3ee04-118">Defines a condition that must exist for a common control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3ee04-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="3ee04-119">Text Value</span></span>

<span data-ttu-id="3ee04-120">Ange .NET-egenskaps namnet.</span><span class="sxs-lookup"><span data-stu-id="3ee04-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="3ee04-121">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="3ee04-121">Remarks</span></span>

<span data-ttu-id="3ee04-122">Urvals villkoret måste ange minst ett egenskaps namn eller ett skript, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="3ee04-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="3ee04-123">Mer information om hur urvals villkor kan användas finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="3ee04-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3ee04-124">Se även</span><span class="sxs-lookup"><span data-stu-id="3ee04-124">See Also</span></span>

[<span data-ttu-id="3ee04-125">SelectionCondition-element för EntrySelectedBy för kontroller för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="3ee04-125">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="3ee04-126">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="3ee04-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
