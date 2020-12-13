---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSetName-element för SelectionCondition för EntrySelectedBy för ListEntry (format)
description: SelectionSetName-element för SelectionCondition för EntrySelectedBy för ListEntry (format)
ms.openlocfilehash: f3193799e67706eb07f0fe1c2cd42cce83f7af57
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651535"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format"></a>SelectionSetName-element för SelectionCondition för EntrySelectedBy för ListEntry (format)

Anger den uppsättning av .NET-typer som utlöser villkoret. När någon av typerna i den här uppsättningen finns, uppfylls villkoret och objektet visas med hjälp av den här definitionen av listvyn.

Konfigurations element (format) ViewDefinitions element (format) Visa element (format) ListControl-element (format) ListEntries-element (format) ListEntry-element (format) EntrySelectedBy-element för ListEntry (format) SelectionCondition element for EntrySelectedBy for ListEntry (format) SelectionSetName-element för SelectionCondition för EntrySelectedBy (format)

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
|[SelectionCondition-element för EntrySelectedBy för ListEntry (format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|Definierar det villkor som måste finnas för att använda den här definitionen av listvyn.|

## <a name="text-value"></a>Textvärde

Ange namnet på urvals uppsättningen.

## <a name="remarks"></a>Kommentarer

Urvals villkoret kan ange en urvals uppsättning eller en .NET-typ, men det går inte att ange båda. Mer information om hur du använder urvals villkor finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).

Urvals uppsättningar är vanliga grupper av .NET-objekt som kan användas av alla vyer som format filen definierar. Mer information om hur du skapar och refererar till urvals uppsättningar finns i [definiera uppsättningar av objekt](./defining-selection-sets.md).

Mer information om andra komponenter i en listvy finns i [skapa en listvy](./creating-a-list-view.md).

## <a name="see-also"></a>Se även

[Skapa en listvy](./creating-a-list-view.md)

[Definiera villkor för när data visas](./defining-conditions-for-displaying-data.md)

[SelectionCondition-element för EntrySelectedBy för ListEntry (format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
