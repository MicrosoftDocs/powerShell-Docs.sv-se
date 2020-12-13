---
ms.date: 09/13/2016
ms.topic: reference
title: EntrySelectedBy-element för WideEntry (format)
description: EntrySelectedBy-element för WideEntry (format)
ms.openlocfilehash: 246a1967300ab0551f376c4799deac275068308c
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660244"
---
# <a name="entryselectedby-element-for-wideentry-format"></a>EntrySelectedBy-element för WideEntry (format)

Definierar de .NET-typer som använder den här definitionen för wide View eller det villkor som måste finnas för att den här definitionen ska kunna användas.

Konfigurations element (format) ViewDefinitions element (format) Visa element (format) WideControl-element (format) WideEntries-element (format) WideEntry element (format) EntrySelectedBy-element för WideEntry (format)

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
|[SelectionCondition-element för EntrySelectedBy för WideEntry (format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|Valfritt element.<br /><br /> Definierar det villkor som måste finnas för att denna wide View-definition ska användas.|
|[SelectionSetName-element för EntrySelectedBy för WideEntry (format)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)|Valfritt element.<br /><br /> Anger en uppsättning av .NET-typer som använder denna wide View-definition.|
|[TypeName-element för EntrySelectedBy för WideEntry (format)](./typename-element-for-entryselectedby-for-wideentry-format.md)|Valfritt element.<br /><br /> Anger en .NET-typ som använder denna wide View-definition.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[WideEntry-element (format)](./wideentry-element-for-widecontrol-format.md)|Ger en definition av den breda vyn.|

## <a name="remarks"></a>Kommentarer

Du måste ange minst en typ, markerings uppsättning eller ett markerings villkor för en wide View-definition. Det finns ingen övre gräns för antalet underordnade element som du kan använda.

Urvals villkor används för att definiera ett villkor som måste finnas för att definitionen ska kunna användas, till exempel när ett objekt har en speciell egenskap eller ett angivet egenskaps värde eller skript värde utvärderas till `true` . Mer information om urvals villkor finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).

Mer information om andra komponenter i en bred vy finns i [skapa en bred vy](./creating-a-wide-view.md).

## <a name="see-also"></a>Se även

[WideEntry-element (format)](./wideentry-element-for-widecontrol-format.md)

[SelectionCondition-element för EntrySelectedBy för WideEntry (format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[SelectionSetName-element för EntrySelectedBy för WideEntry (format)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[TypeName-element för EntrySelectedBy för WideEntry (format)](./typename-element-for-entryselectedby-for-wideentry-format.md)

[Skapa en bred vy](./creating-a-wide-view.md)

[Definiera villkor för datavisning](./defining-conditions-for-displaying-data.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
