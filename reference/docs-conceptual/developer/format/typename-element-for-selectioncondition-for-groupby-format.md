---
title: Elementet TypeName för SelectionCondition för GroupBy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: ea1e0cb50c3a749f6c26d13fff4b001240ce6b95
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772560"
---
# <a name="typename-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="99921-102">TypeName-element för SelectionCondition för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="99921-102">TypeName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="99921-103">Anger en .NET-typ som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="99921-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="99921-104">Det här elementet används när du definierar hur en ny grupp av objekt visas.</span><span class="sxs-lookup"><span data-stu-id="99921-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="99921-105">Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for GroupBy (format) CustomEntry-element for CustomControl for groupby (format) EntrySelectedBy-element för CustomEntry-element (format)</span><span class="sxs-lookup"><span data-stu-id="99921-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="99921-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="99921-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="99921-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="99921-107">Attributes and Elements</span></span>

<span data-ttu-id="99921-108">I följande avsnitt beskrivs attribut, underordnade element och `TypeName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="99921-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="99921-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="99921-109">Attributes</span></span>

<span data-ttu-id="99921-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="99921-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="99921-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="99921-111">Child Elements</span></span>

<span data-ttu-id="99921-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="99921-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="99921-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="99921-113">Parent Elements</span></span>

|<span data-ttu-id="99921-114">Element</span><span class="sxs-lookup"><span data-stu-id="99921-114">Element</span></span>|<span data-ttu-id="99921-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="99921-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="99921-116">SelectionCondition-element för EntrySelectedBy för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="99921-116">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="99921-117">Definierar ett villkor som måste finnas för att den kontroll definition som ska användas.</span><span class="sxs-lookup"><span data-stu-id="99921-117">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="99921-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="99921-118">Text Value</span></span>

<span data-ttu-id="99921-119">Ange det fullständigt kvalificerade namnet för .NET-typen, t `System.IO.DirectoryInfo` . ex..</span><span class="sxs-lookup"><span data-stu-id="99921-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="99921-120">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="99921-120">Remarks</span></span>

<span data-ttu-id="99921-121">När det här elementet har angetts kan du inte ange `SelectionSetName` elementet.</span><span class="sxs-lookup"><span data-stu-id="99921-121">When this element is specified, you cannot specify the `SelectionSetName` element.</span></span> <span data-ttu-id="99921-122">Mer information om hur du definierar urvals villkor finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="99921-122">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="99921-123">Se även</span><span class="sxs-lookup"><span data-stu-id="99921-123">See Also</span></span>

[<span data-ttu-id="99921-124">SelectionCondition-element för EntrySelectedBy för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="99921-124">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="99921-125">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="99921-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
