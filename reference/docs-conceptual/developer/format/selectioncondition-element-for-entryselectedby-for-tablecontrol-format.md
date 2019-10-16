---
title: SelectionCondition-element för EntrySelectedBy för TableControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 912f3e63-e4d5-41ce-8710-6dfd8c885dc2
caps.latest.revision: 12
ms.openlocfilehash: 2faca6021dc26878869bdd2d35bc4ffc64d0fe7b
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72358878"
---
# <a name="selectioncondition-element-for-entryselectedby-for-tablecontrol-format"></a>SelectionCondition-element för EntrySelectedBy för TableControl (format)

Definierar det villkor som måste finnas för att användas för den här definitionen av tabellvy. Det finns ingen gräns för antalet urvals villkor som kan anges för en tabell definition.

Konfigurations element (format) ViewDefinitions element (format) Visa element (format) TableControl-element (format) TableRowEntries-element (format) TableRowEntry element (format) EntrySelectedBy-element för TableRowEntry (format) SelectionCondition-element för EntrySelectedBy för TableRowEntry (format)

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

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i SelectionCondition-elementet.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[PropertyName-element för SelectionCondition för EntrySelectedBy för TableRowEntry (format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)|Valfritt element.<br /><br /> Anger den .NET-egenskap som utlöser villkoret.|
|[Script block-element för SelectionCondition för EntrySelectedBy för TableRowEntry (format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|Valfritt element.<br /><br /> Anger det skript som utlöser villkoret.|
|[SelectionSetName-element för SelectionCondition för EntrySelectedBy för TableRowEntry (format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|Valfritt element.<br /><br /> Anger den uppsättning av .NET-typer som utlöser villkoret.|
|[Elementet TypeName för SelectionCondition för EntrySelectedBy för TableRowEntry (format)](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|Valfritt element.<br /><br /> Anger en .NET-typ som utlöser villkoret.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[EntrySelectedBy-element för TableRowEntry (format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Definierar de .NET-typer som använder den här tabell posten eller det villkor som måste finnas för att den här posten ska kunna användas.|

## <a name="remarks"></a>Anmärkningar

Varje List post måste ha minst ett typ namn, en urvals uppsättning eller ett urvals villkor definierat.

När du definierar ett urvals villkor gäller följande krav:

- Markerings villkoret måste ange minst ett egenskaps namn eller ett skript block, men kan inte ange båda.

- Urvals villkoret kan ange valfritt antal .NET-typer eller markerings uppsättningar, men kan inte ange båda.

Mer information om hur du använder urvals villkor finns i [definiera villkor för när en visnings post eller ett objekt används](./defining-conditions-for-displaying-data.md).

Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).

## <a name="see-also"></a>Se även

[Skapa en tabellvy](./creating-a-table-view.md)

[Definiera villkor för när data visas](./defining-conditions-for-displaying-data.md)

[EntrySelectedBy-element (format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[PropertyName-element för SelectionCondition för EntrySelectedBy för TableRowEntry (format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[Script block-element för SelectionCondition för EntrySelectedBy för TableRowEntry (format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[SelectionSetName-element för SelectionCondition för EntrySelectedBy för TableRowEntry (format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[Elementet TypeName för SelectionCondition för EntrySelectedBy för TableRowEntry (format)](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[Skriva en Windows PowerShell-formatering och en typ fil](./writing-a-powershell-formatting-file.md)
