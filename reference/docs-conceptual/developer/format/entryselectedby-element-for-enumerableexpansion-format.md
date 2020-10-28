---
ms.date: 09/13/2016
ms.topic: reference
title: EntrySelectedBy-element för EnumerableExpansion (format)
description: EntrySelectedBy-element för EnumerableExpansion (format)
ms.openlocfilehash: 8b2fff2d0b14d0622d0be2c5af3a95194c733a73
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92652331"
---
# <a name="entryselectedby-element-for-enumerableexpansion-format"></a>EntrySelectedBy-element för EnumerableExpansion (format)

Definierar de .NET-typer som använder den här definitionen eller det villkor som måste finnas för att den här definitionen ska kunna användas.

Konfigurations element (format) DefaultSettings-element (format) EnumerableExpansions-element (format) EnumerableExpansion-element (format) EntrySelectedBy-element för EnumerableExpansion (format)

## <a name="syntax"></a>Syntax

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och `EntrySelectedBy` elementets överordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|Valfritt element.<br /><br /> Definierar det villkor som måste finnas för att expandera samlings objekt i den här definitionen.|
|[SelectionSetName-element för EntrySelectedBy för EnumerableExpansion (format)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)|Valfritt element.<br /><br /> Anger en uppsättning .NET-typer som använder den här definitionen av hur samlings objekt expanderas.|
|[TypeName-element för EntrySelectedBy för EnumerableExpansion (format)](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)|Valfritt element.<br /><br /> Anger en .NET-typ som använder den här definitionen av hur samlings objekt expanderas.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[EnumerableExpansion-element (format)](./enumerableexpansion-element-format.md)|Definierar hur vissa .NET Collection-objekt expanderas när de visas i en vy.|

## <a name="remarks"></a>Kommentarer

Du måste ange minst en typ, markerings uppsättning eller ett markerings villkor för en definitions post. Det finns ingen övre gräns för antalet underordnade element som du kan använda.

Urvals villkor används för att definiera ett villkor som måste finnas för att definitionen ska kunna användas, till exempel när ett objekt har en speciell egenskap eller ett angivet egenskaps värde eller skript utvärderas till `true` . Mer information om urvals villkor finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Se även

[Definiera villkor för datavisning](./defining-conditions-for-displaying-data.md)

[EnumerableExpansion-element (format)](./enumerableexpansion-element-format.md)

[SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[SelectionSetName-element för EntrySelectedBy för EnumerableExpansion (format)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

[TypeName-element för EntrySelectedBy för EnumerableExpansion (format)](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
