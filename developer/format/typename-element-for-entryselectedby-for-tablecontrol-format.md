---
title: TypeName-Element för EntrySelectedBy för TableControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd872ada-d476-4c4d-a788-ccac3f983070
caps.latest.revision: 10
ms.openlocfilehash: 7bbb47268a23fcb37a34e2287a6ce949313a13bb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083968"
---
# <a name="typename-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="9720c-102">TypeName-element för EntrySelectedBy för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="9720c-102">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="9720c-103">Anger ett .NET-typ som använder den här posten i tabellvyn.</span><span class="sxs-lookup"><span data-stu-id="9720c-103">Specifies a .NET type that uses this entry of the table view.</span></span> <span data-ttu-id="9720c-104">Det finns ingen gräns för hur många typer som kan anges för en post.</span><span class="sxs-lookup"><span data-stu-id="9720c-104">There is no limit to the number of types that can be specified for a table entry.</span></span>

<span data-ttu-id="9720c-105">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format) TypeName konfigurationselement för EntrySelectedBy för TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="9720c-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format) TypeName Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9720c-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="9720c-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9720c-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="9720c-107">Attributes and Elements</span></span>

<span data-ttu-id="9720c-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `TypeName` element.</span><span class="sxs-lookup"><span data-stu-id="9720c-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9720c-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="9720c-109">Attributes</span></span>

<span data-ttu-id="9720c-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="9720c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9720c-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="9720c-111">Child Elements</span></span>

<span data-ttu-id="9720c-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="9720c-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9720c-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="9720c-113">Parent Elements</span></span>

|<span data-ttu-id="9720c-114">Element</span><span class="sxs-lookup"><span data-stu-id="9720c-114">Element</span></span>|<span data-ttu-id="9720c-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="9720c-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9720c-116">EntrySelectedBy Element (Format)</span><span class="sxs-lookup"><span data-stu-id="9720c-116">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="9720c-117">Definierar vilka typer av .NET som använder den här posten eller villkor som måste finnas för den här posten som ska användas.</span><span class="sxs-lookup"><span data-stu-id="9720c-117">Defines the .NET types that use this entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9720c-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="9720c-118">Text Value</span></span>

<span data-ttu-id="9720c-119">Ange namnet på .NET-typen.</span><span class="sxs-lookup"><span data-stu-id="9720c-119">Specify the name of the .NET type.</span></span>

## <a name="remarks"></a><span data-ttu-id="9720c-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="9720c-120">Remarks</span></span>

<span data-ttu-id="9720c-121">Varje listpost måste ha minst ett namn, val av set eller Urvalsvillkoret som definierats.</span><span class="sxs-lookup"><span data-stu-id="9720c-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="9720c-122">Läs mer om komponenterna i en tabellvy, [skapar en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="9720c-122">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9720c-123">Se även</span><span class="sxs-lookup"><span data-stu-id="9720c-123">See Also</span></span>

[<span data-ttu-id="9720c-124">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="9720c-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="9720c-125">EntrySelectedBy Element (Format)</span><span class="sxs-lookup"><span data-stu-id="9720c-125">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="9720c-126">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="9720c-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
