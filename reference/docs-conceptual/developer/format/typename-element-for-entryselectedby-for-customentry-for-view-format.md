---
title: Elementet TypeName för EntrySelectedBy för CustomEntry för vyn (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76548af7-05bd-4d12-bf71-6fb69c434ef2
caps.latest.revision: 10
ms.openlocfilehash: c3dd761cd9b6c468d4833ea35b897ba5d425f598
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72358761"
---
# <a name="typename-element-for-entryselectedby-for-customentry-for-view-format"></a><span data-ttu-id="bfbdd-102">TypeName-element för EntrySelectedBy för CustomEntry för View (format)</span><span class="sxs-lookup"><span data-stu-id="bfbdd-102">TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

<span data-ttu-id="bfbdd-103">Anger en .NET-typ som använder den här definitionen för den anpassade kontrollen.</span><span class="sxs-lookup"><span data-stu-id="bfbdd-103">Specifies a .NET type that uses this definition of the custom control view.</span></span> <span data-ttu-id="bfbdd-104">Det finns ingen gräns för antalet typer som kan anges för en definition.</span><span class="sxs-lookup"><span data-stu-id="bfbdd-104">There is no limit to the number of types that can be specified for a definition.</span></span>

<span data-ttu-id="bfbdd-105">Konfigurations element (format) ViewDefinitions element (format) View element (format) CustomControl element (format) CustomEntries-element för CustomControl för View (format) CustomEntry-element för CustomEntries för View (format) EntrySelectedBy Element för CustomEntry för visnings-(format) elementet TypeName för EntrySelectedBy för CustomEntry för View (format)</span><span class="sxs-lookup"><span data-stu-id="bfbdd-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bfbdd-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="bfbdd-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bfbdd-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="bfbdd-107">Attributes and Elements</span></span>

<span data-ttu-id="bfbdd-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `TypeName`-elementet.</span><span class="sxs-lookup"><span data-stu-id="bfbdd-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="bfbdd-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="bfbdd-109">Attributes</span></span>

<span data-ttu-id="bfbdd-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="bfbdd-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bfbdd-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="bfbdd-111">Child Elements</span></span>

<span data-ttu-id="bfbdd-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="bfbdd-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="bfbdd-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="bfbdd-113">Parent Elements</span></span>

|<span data-ttu-id="bfbdd-114">Element</span><span class="sxs-lookup"><span data-stu-id="bfbdd-114">Element</span></span>|<span data-ttu-id="bfbdd-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="bfbdd-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bfbdd-116">EntrySelectedBy-element för CustomEntry för vy (format)</span><span class="sxs-lookup"><span data-stu-id="bfbdd-116">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="bfbdd-117">Definierar de .NET-typer som använder den här anpassade kontroll definitionen eller det villkor som måste finnas för att den här definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="bfbdd-117">Defines the .NET types that use this custom control view definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="bfbdd-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="bfbdd-118">Text Value</span></span>

<span data-ttu-id="bfbdd-119">Ange det fullständigt kvalificerade namnet för .NET-typen, t. ex. `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="bfbdd-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="bfbdd-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="bfbdd-120">Remarks</span></span>

<span data-ttu-id="bfbdd-121">Varje definition av anpassad kontroll måste ha minst ett typ namn, en urvals uppsättning eller ett urvals villkor definierat.</span><span class="sxs-lookup"><span data-stu-id="bfbdd-121">Each custom control view definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="bfbdd-122">Mer information om komponenterna i en anpassad kontroll vy finns i [skapa anpassade kontroller](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="bfbdd-122">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bfbdd-123">Se även</span><span class="sxs-lookup"><span data-stu-id="bfbdd-123">See Also</span></span>

[<span data-ttu-id="bfbdd-124">Skapa anpassade kontroller</span><span class="sxs-lookup"><span data-stu-id="bfbdd-124">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="bfbdd-125">EntrySelectedBy-element för CustomEntry för vy (format)</span><span class="sxs-lookup"><span data-stu-id="bfbdd-125">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="bfbdd-126">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="bfbdd-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
