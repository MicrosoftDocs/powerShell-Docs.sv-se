---
ms.date: 09/13/2016
ms.topic: reference
title: EntrySelectedBy-element för CustomEntry för GroupBy (format)
description: EntrySelectedBy-element för CustomEntry för GroupBy (format)
ms.openlocfilehash: 5af4abe081ca268699d281a1b586a584107b9a83
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652366"
---
# <a name="entryselectedby-element-for-customentry-for-groupby-format"></a>EntrySelectedBy-element för CustomEntry för GroupBy (format)

Definierar de .NET-typer som använder den här kontroll definitionen eller det villkor som måste finnas för att den här definitionen ska kunna användas. Det här elementet används när du definierar hur en ny grupp av objekt visas.

Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for GroupBy (format) CustomEntry element for CustomControl for GroupBy (format) EntrySelectedBy-element för CustomEntry (format)

## <a name="syntax"></a>Syntax

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och `EntrySelectedBy` elementets överordnade element. Du måste ange minst en typ, markerings uppsättning eller ett markerings villkor för en definition. Det finns ingen övre gräns för antalet underordnade element som du kan använda.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[SelectionCondition-element för EntrySelectedBy för GroupBy (format)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|Valfritt element.<br /><br /> Definierar det villkor som måste finnas för att den här definitionen ska kunna användas.|
|[SelectionSetName-element för EntrySelectedBy för GroupBy (format)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)|Valfritt element.<br /><br /> Anger en uppsättning av .NET-typer som använder den här definitionen av kontrollen.|
|[TypeName-element för EntrySelectedBy för GroupBy (format)](./typename-element-for-entryselectedby-for-groupby-format.md)|Valfritt element.<br /><br /> Anger en .NET-typ som använder den här definitionen av kontrollen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomEntry-element för CustomControl för GroupBy (format)](./customentry-element-for-customcontrol-for-groupby-format.md)|Ger en definition av kontrollen.|

## <a name="remarks"></a>Kommentarer

Urvals villkor används för att definiera ett villkor som måste finnas för att definitionen ska kunna användas, till exempel när ett objekt har en speciell egenskap eller när ett angivet egenskaps värde eller skript utvärderas till `true` . Mer information om urvals villkor finns i [definiera villkor för när en visnings post eller ett objekt används](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Se även

[SelectionCondition-element för EntrySelectedBy för GroupBy (format)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[SelectionSetName-element för EntrySelectedBy för GroupBy (format)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

[TypeName-element för EntrySelectedBy för GroupBy (format)](./typename-element-for-entryselectedby-for-groupby-format.md)

[CustomEntry-element för CustomEntries för Controls för View (format)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
