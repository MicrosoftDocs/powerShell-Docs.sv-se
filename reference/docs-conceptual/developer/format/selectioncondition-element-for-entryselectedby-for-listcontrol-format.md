---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionCondition-element för EntrySelectedBy för ListControl (format)
description: SelectionCondition-element för EntrySelectedBy för ListControl (format)
ms.openlocfilehash: e93499691dd0046265e43abd26497b2974546083
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92655100"
---
# <a name="selectioncondition-element-for-entryselectedby-for-listcontrol-format"></a>SelectionCondition-element för EntrySelectedBy för ListControl (format)

Definierar det villkor som måste finnas för att använda den här definitionen av listvyn. Det finns ingen gräns för antalet urvals villkor som kan anges för en List definition.

Konfigurations element (format) ViewDefinitions element (format) Visa element (format) ListControl-element (format) ListEntries-element (format) ListEntry element (format) EntrySelectedBy-element för ListEntry (format) SelectionCondition-element för EntrySelectedBy (format)

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

I följande avsnitt beskrivs attribut, underordnade element och `SelectionCondition` elementets överordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[PropertyName-element för SelectionCondition för EntrySelectedBy för ListEntry (format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|Valfritt element.<br /><br /> Anger den .NET-egenskap som utlöser villkoret.|
|[Script block-element för SelectionCondition för EntrySelectedBy för ListEntry (format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|Valfritt element.<br /><br /> Anger det skript som utlöser villkoret.|
|[SelectionSetName-element för SelectionCondition för EntrySelectedBy för ListEntry (format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)|Valfritt element.<br /><br /> Anger den uppsättning av .NET-typer som utlöser villkoret.|
|[Elementet TypeName för SelectionCondition för EntrySelectedBy för ListEntry (format)](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|Valfritt element.<br /><br /> Anger en .NET-typ som utlöser villkoret.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[EntrySelectedBy-element för TableRowEntry (format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Definierar de .NET-typer som använder den här tabell posten eller det villkor som måste finnas för att den här posten ska kunna användas.|

## <a name="remarks"></a>Kommentarer

lWhen du definierar ett urvals villkor gäller följande krav:

- Markerings villkoret måste ange minst ett egenskaps namn eller ett skript block, men kan inte ange båda.

- Urvals villkoret kan ange valfritt antal .NET-typer eller markerings uppsättningar, men kan inte ange båda.

Mer information om hur du använder urvals villkor finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).

Mer information om andra komponenter i en listvy finns i [skapa en listvy](./creating-a-list-view.md).

## <a name="see-also"></a>Se även

[Skapa en listvy](./creating-a-list-view.md)

[Definiera villkor för när data visas](./defining-conditions-for-displaying-data.md)

[ListEntry-element (format)](./listentry-element-for-listcontrol-format.md)

[SelectionSetName-element för EntrySelectedBy för ListEntry (format)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[Elementet TypeName för EntrySelectedBy för ListEntry (format)](/powershell/scripting/developer/format/typename-element-for-entryselectedby-for-listcontrol-format)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
