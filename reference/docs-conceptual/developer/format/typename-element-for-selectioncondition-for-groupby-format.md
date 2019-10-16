---
title: Elementet TypeName för SelectionCondition för GroupBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 290d38e3-b9bd-4382-9671-2e28b32b7260
caps.latest.revision: 6
ms.openlocfilehash: a4036b1e9de85da7e0029e02cca9e0eaed462f70
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353461"
---
# <a name="typename-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="c4988-102">TypeName-element för SelectionCondition för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="c4988-102">TypeName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="c4988-103">Anger en .NET-typ som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="c4988-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="c4988-104">Det här elementet används när du definierar hur en ny grupp av objekt visas.</span><span class="sxs-lookup"><span data-stu-id="c4988-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="c4988-105">Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for GroupBy (format) CustomEntry-element för CustomControl for GroupBy (format) EntrySelectedBy-element för CustomEntry för GroupBy (format) SelectionCondition-element för EntrySelectedBy för GroupBy-element (format) för SelectionCondition för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="c4988-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c4988-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="c4988-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="c4988-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="c4988-107">Attributes and Elements</span></span>

<span data-ttu-id="c4988-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för elementet `TypeName`.</span><span class="sxs-lookup"><span data-stu-id="c4988-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c4988-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="c4988-109">Attributes</span></span>

<span data-ttu-id="c4988-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="c4988-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c4988-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="c4988-111">Child Elements</span></span>

<span data-ttu-id="c4988-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="c4988-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c4988-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="c4988-113">Parent Elements</span></span>

|<span data-ttu-id="c4988-114">Element</span><span class="sxs-lookup"><span data-stu-id="c4988-114">Element</span></span>|<span data-ttu-id="c4988-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c4988-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c4988-116">SelectionCondition-element för EntrySelectedBy för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="c4988-116">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="c4988-117">Definierar ett villkor som måste finnas för att den kontroll definition som ska användas.</span><span class="sxs-lookup"><span data-stu-id="c4988-117">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c4988-118">Text värde</span><span class="sxs-lookup"><span data-stu-id="c4988-118">Text Value</span></span>

<span data-ttu-id="c4988-119">Ange det fullständigt kvalificerade namnet för .NET-typen, t. ex. `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="c4988-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="c4988-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="c4988-120">Remarks</span></span>

<span data-ttu-id="c4988-121">När det här elementet har angetts kan du inte ange ett `SelectionSetName`-element.</span><span class="sxs-lookup"><span data-stu-id="c4988-121">When this element is specified, you cannot specify the `SelectionSetName` element.</span></span> <span data-ttu-id="c4988-122">Mer information om hur du definierar urvals villkor finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="c4988-122">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c4988-123">Se även</span><span class="sxs-lookup"><span data-stu-id="c4988-123">See Also</span></span>

[<span data-ttu-id="c4988-124">SelectionCondition-element för EntrySelectedBy för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="c4988-124">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="c4988-125">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="c4988-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
