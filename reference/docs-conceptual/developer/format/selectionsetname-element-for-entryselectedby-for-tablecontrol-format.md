---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSetName-element för EntrySelectedBy för TableControl (format)
description: SelectionSetName-element för EntrySelectedBy för TableControl (format)
ms.openlocfilehash: a5a395f718d0e1a2d7f33d120ce4fd2ff787cc34
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92651778"
---
# <a name="selectionsetname-element-for-entryselectedby-for-tablecontrol-format"></a>SelectionSetName-element för EntrySelectedBy för TableControl (format)

Anger en uppsättning .NET-typer. Använd den här posten i vyn tabell. Det finns ingen gräns för antalet markerings uppsättningar som kan anges för en post.

Konfigurations element (format) ViewDefinitions element (format) Visa element (format) TableControl-element (format) TableRowEntries-element (format) TableRowEntry-element (format) EntrySelectedBy element (format) SelectionSetName-element för EntrySelectedBy (format)

## <a name="syntax"></a>Syntax

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och överordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

Inga.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[EntrySelectedBy-element (format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Definierar de .NET-typer som använder den här posten eller det villkor som måste finnas för att den här posten ska kunna användas.|

## <a name="text-value"></a>Textvärde

Ange namnet på urvals uppsättningen.

## <a name="remarks"></a>Kommentarer

Urvals uppsättningar används vanligt vis när du vill definiera en grupp objekt som används i flera vyer. Du kanske till exempel vill skapa en tabellvy och en listvy för samma uppsättning objekt. Mer information om hur du definierar urvals uppsättningar finns i [definiera uppsättningar av objekt för en vy](./defining-selection-sets.md).

Om du anger en markerings uppsättning för en post kan du inte ange ett typnamn. Mer information om hur du anger en .NET-typ finns i [elementet TypeName för EntrySelectedBy för TableRowEntry (format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md).

Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).

## <a name="see-also"></a>Se även

[EntrySelectedBy-element (format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[Definiera uppsättningar av objekt för en vy](./defining-selection-sets.md)

[Skapa en tabellvy](./creating-a-table-view.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
