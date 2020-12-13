---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSetName-element för SelectionCondition för EntrySelectedBy för WideEntry (format)
description: SelectionSetName-element för SelectionCondition för EntrySelectedBy för WideEntry (format)
ms.openlocfilehash: c6466e3ac6e1f194df9172468d26448f9630da6a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655003"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a>SelectionSetName-element för SelectionCondition för EntrySelectedBy för WideEntry (format)

Anger den uppsättning av .NET-typer som utlöser villkoret. När någon av typerna i den här uppsättningen finns, uppfylls villkoret och objektet visas genom att använda den här definitionen av wide View.

Konfigurations element (format) ViewDefinitions element (format) Visa element (format) WideControl-element (format) WideEntries-element (format) WideEntry-element (format) EntrySelectedBy-element för WideEntry (format) SelectionCondition element for EntrySelectedBy for WideEntry (format) SelectionSetName-element för SelectionCondition för EntrySelectedBy (format)

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
|[SelectionCondition-element för EntrySelectedBy för WideEntry (format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|Definierar det villkor som måste finnas för att den här definitionen ska kunna användas.|

## <a name="text-value"></a>Textvärde

Ange namnet på urvals uppsättningen.

## <a name="remarks"></a>Kommentarer

Urvals villkoret kan ange en urvals uppsättning eller en .NET-typ, men det går inte att ange båda. Mer information om hur du använder urvals villkor finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).

Urvals uppsättningar är vanliga grupper av .NET-objekt som kan användas av alla vyer som format filen definierar. Mer information om hur du skapar och refererar till urvals uppsättningar finns i [definiera uppsättningar av objekt](./defining-selection-sets.md).

Mer information om andra komponenter i en bred vy finns i [skapa en bred vy](./creating-a-wide-view.md).

## <a name="see-also"></a>Se även

[Skapa en bred vy](./creating-a-wide-view.md)

[Definiera villkor för när data visas](./defining-conditions-for-displaying-data.md)

[Definiera valuppsättningar](./defining-selection-sets.md)

[SelectionCondition-element för EntrySelectedBy för WideEntry (format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[Elementet TypeName för SelectionCondition för EntrySelectedBy för WideEntry (format)](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
