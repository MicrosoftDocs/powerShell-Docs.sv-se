---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSetName-element för EntrySelectedBy för ListControl (format)
description: SelectionSetName-element för EntrySelectedBy för ListControl (format)
ms.openlocfilehash: 413a77f7ba06fe952e574061e58d0b5d80c5b3c4
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651838"
---
# <a name="selectionsetname-element-for-entryselectedby-for-listcontrol-format"></a>SelectionSetName-element för EntrySelectedBy för ListControl (format)

Anger en uppsättning .NET-objekt för List posten. Det finns ingen gräns för antalet markerings uppsättningar som kan anges för en post.

Konfigurations element (format) ViewDefinitions element (format) Visa element (format) ListControl-element (format) ListEntries-element (format) ListEntry element (format) EntrySelectedBy-element för ListEntry (format) SelectionSetName-element för EntrySelectedBy (format)

## <a name="syntax"></a>Syntax

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och `SelectionSetName` elementets överordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

Inga.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[EntrySelectedBy-element för ListEntry (format)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|Definierar de .NET-typer som använder den här List posten eller det villkor som måste finnas för att den här posten ska kunna användas.|

## <a name="text-value"></a>Textvärde

Ange namnet på urvals uppsättningen.

## <a name="remarks"></a>Kommentarer

Varje List post måste ha minst ett typ namn, en urvals uppsättning eller ett urvals villkor definierat.

Urvals uppsättningar används vanligt vis när du vill definiera en grupp objekt som används i flera vyer. Du kanske till exempel vill skapa en tabellvy och en listvy för samma uppsättning objekt. Mer information om hur du definierar urvals uppsättningar finns i [definiera uppsättningar av objekt för en vy](./defining-selection-sets.md).

Mer information om komponenterna i en listvy finns i [skapa en listvy](./creating-a-list-view.md).

## <a name="example"></a>Exempel

I följande exempel visas hur du anger en markerings uppsättning för en post i en listvy.

```xml
<ListEntry>
  <EntrySelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a>Se även

[Skapa en listvy](./creating-a-list-view.md)

[EntrySelectedBy-element för ListEntry (format)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
