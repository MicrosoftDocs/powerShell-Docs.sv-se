---
title: PropertyName-Element för SelectionCondition för kontroller för konfiguration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec048408-e1c6-41ef-b39b-72f4c2dcf2ac
caps.latest.revision: 6
ms.openlocfilehash: b4b2440fdb7171d09fdc16ac7cc4f25ed1a4bb78
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064735"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="d3fc5-102">PropertyName-element för SelectionCondition för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="d3fc5-102">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="d3fc5-103">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="d3fc5-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="d3fc5-104">När den här egenskapen finns eller att inventera till `true`villkoret uppfylls och posten används.</span><span class="sxs-lookup"><span data-stu-id="d3fc5-104">When this property is present or when it evaluates to `true`, the condition is met, and the entry is used.</span></span> <span data-ttu-id="d3fc5-105">Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.</span><span class="sxs-lookup"><span data-stu-id="d3fc5-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="d3fc5-106">Konfigurationselementet Element (Format) kontroller av (Format) kontroll konfigurationselement för kontroller för (Format) anpassad kontroll konfigurationselement för kontroll för (Format) CustomEntries konfigurationselement för anpassad kontroll för konfiguration ( Format) CustomEntry Element för anpassad kontroll för kontroller för (Format) EntrySelectedBy konfigurationselement för CustomEntry för kontroller för (Format) SelectionCondition konfigurationselement för EntrySelectedBy för CustomEntry för konfiguration ( Format) PropertyName Element för SelectionCondition för EntrySelectedBy för ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="d3fc5-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d3fc5-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="d3fc5-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d3fc5-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="d3fc5-108">Attributes and Elements</span></span>

<span data-ttu-id="d3fc5-109">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `PropertyName` element.</span><span class="sxs-lookup"><span data-stu-id="d3fc5-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d3fc5-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="d3fc5-110">Attributes</span></span>

<span data-ttu-id="d3fc5-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="d3fc5-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d3fc5-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="d3fc5-112">Child Elements</span></span>

<span data-ttu-id="d3fc5-113">Ingen.</span><span class="sxs-lookup"><span data-stu-id="d3fc5-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d3fc5-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="d3fc5-114">Parent Elements</span></span>

|<span data-ttu-id="d3fc5-115">Element</span><span class="sxs-lookup"><span data-stu-id="d3fc5-115">Element</span></span>|<span data-ttu-id="d3fc5-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d3fc5-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d3fc5-117">SelectionCondition Element för EntrySelectedBy för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="d3fc5-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="d3fc5-118">Definierar ett villkor som måste finnas för en gemensam kontrolldefinition som ska användas.</span><span class="sxs-lookup"><span data-stu-id="d3fc5-118">Defines a condition that must exist for a common control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d3fc5-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="d3fc5-119">Text Value</span></span>

<span data-ttu-id="d3fc5-120">Ange namnet på .NET-egenskapen.</span><span class="sxs-lookup"><span data-stu-id="d3fc5-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="d3fc5-121">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="d3fc5-121">Remarks</span></span>

<span data-ttu-id="d3fc5-122">Urvalsvillkoret måste ange ett namn med minst en egenskap eller ett skript, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="d3fc5-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="d3fc5-123">Läs mer om hur du kan använda villkor för val av [definiera villkor för att visa Data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="d3fc5-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d3fc5-124">Se även</span><span class="sxs-lookup"><span data-stu-id="d3fc5-124">See Also</span></span>

[<span data-ttu-id="d3fc5-125">SelectionCondition Element för EntrySelectedBy för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="d3fc5-125">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="d3fc5-126">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="d3fc5-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
