---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSetName-element för SelectionCondition för EntrySelectedBy för TableControl (format)
description: SelectionSetName-element för SelectionCondition för EntrySelectedBy för TableControl (format)
ms.openlocfilehash: 2fb09e27eef1ce5d6e864c72edb595817d91f729
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92655042"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a>SelectionSetName-element för SelectionCondition för EntrySelectedBy för TableControl (format)

Anger den uppsättning av .NET-typer som utlöser villkoret. När någon av typerna i den här uppsättningen finns, uppfylls villkoret och objektet visas med hjälp av den här definitionen av tabellvy.

Konfigurations element (format) ViewDefinitions element (format) Visa element (format) TableControl-element (format) TableRowEntries-element (format) TableRowEntry-element (format) EntrySelectedBy-element för TableRowEntry (format) SelectionCondition element for EntrySelectedBy for TableRowEntry (format) SelectionSetName-element för SelectionCondition för EntrySelectedBy (format)

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
|[SelectionCondition-element för EntrySelectedBy för TableRowEntry (format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|Definierar det villkor som måste finnas för att användas för den här definitionen av tabellvy.|

## <a name="text-value"></a>Textvärde

Ange namnet på urvals uppsättningen.

## <a name="remarks"></a>Kommentarer

Urvals villkoret kan ange en urvals uppsättning eller en .NET-typ, men det går inte att ange båda. Mer information om hur du använder urvals villkor finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).

Urvals uppsättningar är vanliga grupper av .NET-objekt som kan användas av alla vyer som format filen definierar. Mer information om hur du skapar och refererar till urvals uppsättningar finns i [definiera uppsättningar av objekt](./defining-selection-sets.md).

Mer information om andra komponenter i en bred vy finns i [skapa en tabellvy](./creating-a-table-view.md).

## <a name="see-also"></a>Se även

[Skapa en tabellvy](./creating-a-table-view.md)

[Definiera villkor för när data visas](./defining-conditions-for-displaying-data.md)

[Elementet TypeName för SelectionCondition för EntrySelectedBy för TableRowEntry (format)](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[SelectionCondition-element för EntrySelectedBy för TableRowEntry (format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
