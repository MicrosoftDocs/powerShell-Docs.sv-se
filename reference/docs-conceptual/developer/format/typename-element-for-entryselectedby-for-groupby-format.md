---
title: Elementet TypeName för EntrySelectedBy för GroupBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b8b6739b-770c-432a-95ab-551c7507c51f
caps.latest.revision: 6
ms.openlocfilehash: 3b5ce60d3a0d76988af48f49445a5478a415d498
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353594"
---
# <a name="typename-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="796cc-102">TypeName-element för EntrySelectedBy för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="796cc-102">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="796cc-103">Anger en .NET-typ som använder den här definitionen av den anpassade kontrollen.</span><span class="sxs-lookup"><span data-stu-id="796cc-103">Specifies a .NET type that uses this definition of the custom control.</span></span> <span data-ttu-id="796cc-104">Det här elementet används när du definierar hur en ny grupp av objekt visas.</span><span class="sxs-lookup"><span data-stu-id="796cc-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="796cc-105">Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for GroupBy (format) CustomEntry-element för CustomControl för GroupBy (format) EntrySelectedBy-element för CustomEntry för GroupBy-element (format) för EntrySelectedBy för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="796cc-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="796cc-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="796cc-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="796cc-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="796cc-107">Attributes and Elements</span></span>

<span data-ttu-id="796cc-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `TypeName`-elementet.</span><span class="sxs-lookup"><span data-stu-id="796cc-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="796cc-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="796cc-109">Attributes</span></span>

<span data-ttu-id="796cc-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="796cc-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="796cc-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="796cc-111">Child Elements</span></span>

<span data-ttu-id="796cc-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="796cc-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="796cc-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="796cc-113">Parent Elements</span></span>

|<span data-ttu-id="796cc-114">Element</span><span class="sxs-lookup"><span data-stu-id="796cc-114">Element</span></span>|<span data-ttu-id="796cc-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="796cc-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="796cc-116">EntrySelectedBy-element för CustomEntry för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="796cc-116">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="796cc-117">Definierar de .NET-typer som använder den här kontroll definitionen eller det villkor som måste finnas för att den här definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="796cc-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="796cc-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="796cc-118">Text Value</span></span>

<span data-ttu-id="796cc-119">Ange det fullständigt kvalificerade namnet för .NET-typen, t. ex. `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="796cc-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="796cc-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="796cc-120">Remarks</span></span>

<span data-ttu-id="796cc-121">Varje kontroll definition måste ha minst ett typ namn, en markerings uppsättning eller ett urvals villkor definierat.</span><span class="sxs-lookup"><span data-stu-id="796cc-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="796cc-122">Mer information om komponenterna i en anpassad kontroll vy finns i [skapa anpassade kontroller](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="796cc-122">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="796cc-123">Se även</span><span class="sxs-lookup"><span data-stu-id="796cc-123">See Also</span></span>

[<span data-ttu-id="796cc-124">Skapa anpassade kontroller</span><span class="sxs-lookup"><span data-stu-id="796cc-124">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="796cc-125">EntrySelectedBy-element för CustomEntry för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="796cc-125">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="796cc-126">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="796cc-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
