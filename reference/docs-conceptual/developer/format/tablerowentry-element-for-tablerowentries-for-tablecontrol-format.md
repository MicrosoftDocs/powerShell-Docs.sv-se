---
ms.date: 09/13/2016
ms.topic: reference
title: TableRowEntry-element för TableRowEntries för TableControl (format)
description: TableRowEntry-element för TableRowEntries för TableControl (format)
ms.openlocfilehash: 60d64b7c14b40e87825ada36e19f52a66fe8b6cb
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92659777"
---
# <a name="tablerowentry-element-for-tablerowentries-for-tablecontrol-format"></a>TableRowEntry-element för TableRowEntries för TableControl (format)

Definierar de data som visas i en rad i tabellen.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) TableControl element (format) TableRowEntries-element för TableControl (format) TableRowEntry-element för TableRowEntries (format)

## <a name="syntax"></a>Syntax

```xml
<TableRowEntry>
  <Wrap/>
  <EntrySelectedBy>...</EntrySelectedBy>
  <TableColumnItems>...</TableColumnItems>
</TableRowEntry>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och `TableRowEntry` elementets överordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[EntrySelectedBy-element för TableRowEntry för TableControl (format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Nödvändigt element.<br /><br /> Definierar de objekt vars egenskaps värden visas på raden.|
|[TableColumnItems-element för TableRowEntry för TableControl (format)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|Nödvändigt element.<br /><br /> Definierar de egenskaper eller skript vars värden visas.|
|[Figursatta element för TableRowEntry för TableControl (format)](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)|Valfritt element.<br /><br /> Anger att text som överskrider kolumn bredden visas på nästa rad.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[TableRowEntries-element för TableControl (format)](./tablerowentries-element-for-tablecontrol-format.md)|Definierar raderna i tabellen.|

## <a name="remarks"></a>Kommentarer

Ett `TableColumnItems` element och ett `EntrySelectedBy` element måste anges.

Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).

## <a name="example"></a>Exempel

I följande exempel visas ett- `TableRowEntry` element som definierar en rad som visar värdena för två egenskaper för objektet [system. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) .

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </EntrySelectedBy>
  <TableColumnItems>
    <TableColumnItem>
      <PropertyName> Property for first column</PropertyName>
    </TableColumnItem>
    <TableColumnItem>
      <PropertyName> Property for second column</PropertyName>
    </TableColumnItem>
  </TableColumnItems>
</TableRowEntry>
```

## <a name="see-also"></a>Se även

[Skapa en tabellvy](./creating-a-table-view.md)

[EntrySelectedBy-element för TableRowEntry för TableControl (format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[TableColumnItems-element för TableRowEntry för TableControl (format)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[TableRowEntries-element för TableControl (format)](./tablerowentries-element-for-tablecontrol-format.md)

[Figursatta element för TableRowEntry för TableControl (format)](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
