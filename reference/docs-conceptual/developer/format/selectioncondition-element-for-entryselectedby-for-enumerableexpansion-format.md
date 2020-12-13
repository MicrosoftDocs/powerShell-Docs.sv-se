---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format)
description: SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format)
ms.openlocfilehash: 3ecf7fde99b9ee66a153eea416792f351ff62af3
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92647917"
---
# <a name="selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format"></a>SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format)

Definierar det villkor som måste finnas för att expandera samlings objekt i den här definitionen.

Konfigurations element (format) DefaultSettings-element (format) EnumerableExpansions-element (format) EnumerableExpansion-element (format) EntrySelectedBy-element för EnumerableExpansion (format) SelectionCondition-element för EntrySelectedBy (format)

## <a name="syntax"></a>Syntax

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och `SelectionCondition` elementets överordnade element. Du måste ange ett enskilt `PropertyName` eller- `ScriptBlock` element. `SelectionSetName` `TypeName` Elementen och är valfria. Du kan ange ett av båda elementen.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[PropertyName-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|Valfritt element.<br /><br /> Anger den .NET-egenskap som utlöser villkoret.|
|[ScriptBlock-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|Valfritt element.<br /><br /> Anger det skript som utlöser villkoret.|
|[SelectionSetName-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|Valfritt element.<br /><br /> Anger den uppsättning av .NET-typer som utlöser villkoret.|
|[TypeName-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format)](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|Valfritt element.<br /><br /> Anger en .NET-typ som utlöser villkoret.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[EntrySelectedBy-element för EnumerableExpansion (format)](./entryselectedby-element-for-enumerableexpansion-format.md)|Definierar vilka .NET-samlings objekt som expanderas av den här definitionen.|

## <a name="remarks"></a>Kommentarer

Varje definition måste ha minst ett typ namn, en urvals uppsättning eller ett urvals villkor definierat.

När du definierar ett urvals villkor gäller följande krav:

- Markerings villkoret måste ange minst ett egenskaps namn eller ett skript block, men kan inte ange båda.

- Urvals villkoret kan ange valfritt antal .NET-typer eller markerings uppsättningar, men kan inte ange båda.

Mer information om hur du använder urvals villkor finns i [definiera villkor för Diplaying-data](./defining-conditions-for-displaying-data.md).

Mer information om andra komponenter i en bred vy finns i [wide View](./creating-a-wide-view.md).

## <a name="see-also"></a>Se även

[Definiera villkor för när data visas](./defining-conditions-for-displaying-data.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
