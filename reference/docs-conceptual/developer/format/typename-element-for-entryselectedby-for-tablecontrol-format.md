---
title: Elementet TypeName för EntrySelectedBy för TableControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd872ada-d476-4c4d-a788-ccac3f983070
caps.latest.revision: 10
ms.openlocfilehash: 7bbb47268a23fcb37a34e2287a6ce949313a13bb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353566"
---
# <a name="typename-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="33c79-102">TypeName-element för EntrySelectedBy för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="33c79-102">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="33c79-103">Anger en .NET-typ som använder den här posten i vyn tabell.</span><span class="sxs-lookup"><span data-stu-id="33c79-103">Specifies a .NET type that uses this entry of the table view.</span></span> <span data-ttu-id="33c79-104">Det finns ingen gräns för antalet typer som kan anges för en tabell post.</span><span class="sxs-lookup"><span data-stu-id="33c79-104">There is no limit to the number of types that can be specified for a table entry.</span></span>

<span data-ttu-id="33c79-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) TableControl-element (format) element för TableRowEntries (format) TableRowEntry element (format) EntrySelectedBy element (format) element för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="33c79-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format) TypeName Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="33c79-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="33c79-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="33c79-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="33c79-107">Attributes and Elements</span></span>

<span data-ttu-id="33c79-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `TypeName`-elementet.</span><span class="sxs-lookup"><span data-stu-id="33c79-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="33c79-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="33c79-109">Attributes</span></span>

<span data-ttu-id="33c79-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="33c79-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="33c79-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="33c79-111">Child Elements</span></span>

<span data-ttu-id="33c79-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="33c79-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="33c79-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="33c79-113">Parent Elements</span></span>

|<span data-ttu-id="33c79-114">Element</span><span class="sxs-lookup"><span data-stu-id="33c79-114">Element</span></span>|<span data-ttu-id="33c79-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33c79-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="33c79-116">EntrySelectedBy-element (format)</span><span class="sxs-lookup"><span data-stu-id="33c79-116">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="33c79-117">Definierar de .NET-typer som använder den här posten eller det villkor som måste finnas för att den här posten ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="33c79-117">Defines the .NET types that use this entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="33c79-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="33c79-118">Text Value</span></span>

<span data-ttu-id="33c79-119">Ange namnet på .NET-typen.</span><span class="sxs-lookup"><span data-stu-id="33c79-119">Specify the name of the .NET type.</span></span>

## <a name="remarks"></a><span data-ttu-id="33c79-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="33c79-120">Remarks</span></span>

<span data-ttu-id="33c79-121">Varje List post måste ha minst ett typ namn, en urvals uppsättning eller ett urvals villkor definierat.</span><span class="sxs-lookup"><span data-stu-id="33c79-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="33c79-122">Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="33c79-122">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="33c79-123">Se även</span><span class="sxs-lookup"><span data-stu-id="33c79-123">See Also</span></span>

[<span data-ttu-id="33c79-124">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="33c79-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="33c79-125">EntrySelectedBy-element (format)</span><span class="sxs-lookup"><span data-stu-id="33c79-125">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="33c79-126">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="33c79-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
