---
title: EntrySelectedBy-element för TableRowEntry för TableControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 047a10fb6b38dfa8f78a7741fd50b781d4a14b6d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787707"
---
# <a name="entryselectedby-element-for-tablerowentry--for-tablecontrol-format"></a>EntrySelectedBy-element för TableRowEntry  för TableControl (format)

Definierar de .NET-typer som använder den här definitionen av Tabellvy eller det villkor som måste finnas för att den här definitionen ska kunna användas.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) TableControl-element (format) TableRowEntries-element (format) TableRowEntry-element (format) EntrySelectedBy-element (format)

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
|[SelectionCondition-element för EntrySelectedBy för TableControl (format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|Valfritt element.<br /><br /> Definierar det villkor som måste finnas för att den här tabell visnings definitionen ska kunna användas.|
|[SelectionSetName-element för EntrySelectedBy för TableControl (format)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)|Valfritt element.<br /><br /> Anger en uppsättning av .NET-typer som använder den här Table View-definitionen.|
|[TypeName-element för EntrySelectedBy för TableControl (format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md)|Valfritt element.<br /><br /> Anger en .NET-typ som använder den här Table View-definitionen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[TableRowEntry-element för TableControl (format)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|Definierar de data som visas i en rad i tabellen.|

## <a name="remarks"></a>Kommentarer

Du måste ange minst en typ, markerings uppsättning eller ett markerings villkor för en tabell visnings definition. Det finns ingen övre gräns för antalet underordnade element som du kan använda.

Urvals villkor används för att definiera ett villkor som måste finnas för att definitionen ska kunna användas, till exempel när ett objekt har en speciell egenskap eller ett angivet egenskaps värde eller skript utvärderas till `true` . Mer information om urvals villkor finns i [definiera villkor för när en visnings post eller ett objekt används](./defining-conditions-for-displaying-data.md).

Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).

## <a name="example"></a>Exempel

I följande exempel visas ett- `TableRowEntry` element som används för att visa egenskaperna för [system. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) -objektet.

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </EntrySelectedBy>
  <TableColumnItems>
    <TableColumnItem>
      <PropertyName>PropertyForFirstColumn</PropertyName>
    </TableColumnItem>
    <TableColumnItem>
      <PropertyName>PropertyForSecondColumn</PropertyName>
    </TableColumnItem>
  </TableColumnItems>
</TableRowEntry>
```

## <a name="see-also"></a>Se även

[Skapa en tabellvy](./creating-a-table-view.md)

[SelectionCondition-element för EntrySelectedBy för TableControl (format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[SelectionSetName-element för EntrySelectedBy för TableControl (format)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

[TableRowEntry-element för TableControl (format)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[TypeName-element för EntrySelectedBy för TableControl (format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
