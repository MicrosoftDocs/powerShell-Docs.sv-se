---
title: TypeName-Element för EntrySelectedBy för CustomEntry för vy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76548af7-05bd-4d12-bf71-6fb69c434ef2
caps.latest.revision: 10
ms.openlocfilehash: c3dd761cd9b6c468d4833ea35b897ba5d425f598
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083985"
---
# <a name="typename-element-for-entryselectedby-for-customentry-for-view-format"></a><span data-ttu-id="24d5c-102">TypeName-element för EntrySelectedBy för CustomEntry för View (format)</span><span class="sxs-lookup"><span data-stu-id="24d5c-102">TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

<span data-ttu-id="24d5c-103">Anger ett .NET-typ som använder den här definitionen av vyn anpassad kontroll.</span><span class="sxs-lookup"><span data-stu-id="24d5c-103">Specifies a .NET type that uses this definition of the custom control view.</span></span> <span data-ttu-id="24d5c-104">Det finns ingen gräns för hur många typer som kan anges för en Definitionsuppdatering.</span><span class="sxs-lookup"><span data-stu-id="24d5c-104">There is no limit to the number of types that can be specified for a definition.</span></span>

<span data-ttu-id="24d5c-105">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) anpassad kontroll Element (Format) CustomEntries konfigurationselement för anpassad kontroll för Visa (Format) CustomEntry elementet för CustomEntries för EntrySelectedBy vy (Format) Element för CustomEntry för vyn (Format) TypeName-elementet för EntrySelectedBy för CustomEntry för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="24d5c-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="24d5c-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="24d5c-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="24d5c-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="24d5c-107">Attributes and Elements</span></span>

<span data-ttu-id="24d5c-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `TypeName` element.</span><span class="sxs-lookup"><span data-stu-id="24d5c-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="24d5c-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="24d5c-109">Attributes</span></span>

<span data-ttu-id="24d5c-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="24d5c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="24d5c-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="24d5c-111">Child Elements</span></span>

<span data-ttu-id="24d5c-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="24d5c-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="24d5c-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="24d5c-113">Parent Elements</span></span>

|<span data-ttu-id="24d5c-114">Element</span><span class="sxs-lookup"><span data-stu-id="24d5c-114">Element</span></span>|<span data-ttu-id="24d5c-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="24d5c-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="24d5c-116">EntrySelectedBy Element för CustomEntry för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="24d5c-116">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="24d5c-117">Definierar vilka typer av .NET som använder den här anpassade kontrollen vydefinitionen eller villkor som måste finnas för den här definitionen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="24d5c-117">Defines the .NET types that use this custom control view definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="24d5c-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="24d5c-118">Text Value</span></span>

<span data-ttu-id="24d5c-119">Ange det fullständigt kvalificerade namnet för .NET-typ, till exempel `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="24d5c-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="24d5c-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="24d5c-120">Remarks</span></span>

<span data-ttu-id="24d5c-121">Varje anpassad kontroll vydefinitionen måste ha minst ett namn, val av set eller Urvalsvillkoret som definierats.</span><span class="sxs-lookup"><span data-stu-id="24d5c-121">Each custom control view definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="24d5c-122">Mer information om komponenter för en anpassad kontroll vy finns i [skapar anpassade kontroller](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="24d5c-122">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="24d5c-123">Se även</span><span class="sxs-lookup"><span data-stu-id="24d5c-123">See Also</span></span>

[<span data-ttu-id="24d5c-124">Skapa anpassade kontroller</span><span class="sxs-lookup"><span data-stu-id="24d5c-124">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="24d5c-125">EntrySelectedBy Element för CustomEntry för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="24d5c-125">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="24d5c-126">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="24d5c-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
