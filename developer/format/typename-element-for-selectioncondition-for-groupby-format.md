---
title: TypeName-Element för SelectionCondition för GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 290d38e3-b9bd-4382-9671-2e28b32b7260
caps.latest.revision: 6
ms.openlocfilehash: a4036b1e9de85da7e0029e02cca9e0eaed462f70
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083781"
---
# <a name="typename-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="6bef4-102">TypeName-element för SelectionCondition för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="6bef4-102">TypeName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="6bef4-103">Anger ett .NET-typ som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="6bef4-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="6bef4-104">Det här elementet används när du definierar hur en ny grupp med objekt visas.</span><span class="sxs-lookup"><span data-stu-id="6bef4-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="6bef4-105">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) GroupBy konfigurationselement för Visa (Format) anpassad kontroll elementet för GroupBy (Format) CustomEntries Element för anpassad kontroll för GroupBy (Format) CustomEntry elementet för Anpassad kontroll för GroupBy (Format) EntrySelectedBy elementet för CustomEntry för GroupBy (Format) SelectionCondition elementet för EntrySelectedBy för GroupBy (Format) TypeName-elementet för SelectionCondition för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="6bef4-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6bef4-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="6bef4-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="6bef4-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="6bef4-107">Attributes and Elements</span></span>

<span data-ttu-id="6bef4-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `TypeName` Element.</span><span class="sxs-lookup"><span data-stu-id="6bef4-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6bef4-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="6bef4-109">Attributes</span></span>

<span data-ttu-id="6bef4-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="6bef4-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6bef4-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="6bef4-111">Child Elements</span></span>

<span data-ttu-id="6bef4-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="6bef4-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6bef4-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="6bef4-113">Parent Elements</span></span>

|<span data-ttu-id="6bef4-114">Element</span><span class="sxs-lookup"><span data-stu-id="6bef4-114">Element</span></span>|<span data-ttu-id="6bef4-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="6bef4-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6bef4-116">SelectionCondition Element för EntrySelectedBy för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="6bef4-116">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="6bef4-117">Definierar ett villkor som måste finnas för kontrolldefinition som ska användas.</span><span class="sxs-lookup"><span data-stu-id="6bef4-117">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="6bef4-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="6bef4-118">Text Value</span></span>

<span data-ttu-id="6bef4-119">Ange det fullständigt kvalificerade namnet för .NET-typ, till exempel `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="6bef4-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="6bef4-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="6bef4-120">Remarks</span></span>

<span data-ttu-id="6bef4-121">När det här elementet har angetts ska du inte ange den `SelectionSetName` element.</span><span class="sxs-lookup"><span data-stu-id="6bef4-121">When this element is specified, you cannot specify the `SelectionSetName` element.</span></span> <span data-ttu-id="6bef4-122">Läs mer om hur du definierar villkoren för val av [definiera villkor för att visa Data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="6bef4-122">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6bef4-123">Se även</span><span class="sxs-lookup"><span data-stu-id="6bef4-123">See Also</span></span>

[<span data-ttu-id="6bef4-124">SelectionCondition Element för EntrySelectedBy för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="6bef4-124">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="6bef4-125">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="6bef4-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
