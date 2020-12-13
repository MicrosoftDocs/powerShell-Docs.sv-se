---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSetName-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format)
description: SelectionSetName-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format)
ms.openlocfilehash: 0c9372113a79f75cfbda67acf869164fde894ee3
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651599"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a>SelectionSetName-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format)

Anger den uppsättning av .NET-typer som utlöser villkoret. När någon av typerna i den här uppsättningen är närvarande uppfylls villkoret.

DefaultSettings-element för konfigurations element (format) EnumerableExpansions-element (format) EnumerableExpansions-element (format) EntrySelectedBy-element för EnumerableExpansion (format) SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format) SelectionSetName-element för SelectionCondition för EntrySelectedBy (format)

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
|[SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|Definierar det villkor som måste finnas för att expandera samlings objekt i den här definitionen.|

## <a name="text-value"></a>Textvärde

Ange namnet på urvals uppsättningen.

## <a name="remarks"></a>Kommentarer

Urvals villkoret kan ange en urvals uppsättning eller en .NET-typ, men det går inte att ange båda. Mer information om hur du använder urvals villkor finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).

Urvals uppsättningar är vanliga grupper av .NET-objekt som kan användas av alla vyer som format filen definierar. Mer information om hur du skapar och refererar till urvals uppsättningar finns i [definiera urvals uppsättningar](./defining-selection-sets.md).

## <a name="see-also"></a>Se även

[Definiera valuppsättningar](./defining-selection-sets.md)

[SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
