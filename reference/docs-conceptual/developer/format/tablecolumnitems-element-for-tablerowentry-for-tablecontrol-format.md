---
title: TableColumnItems-element för TableRowEntry för TableControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 661b938e8db0e68e10dc05f552e4f3a14608bc55
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785157"
---
# <a name="tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format"></a>TableColumnItems-element för TableRowEntry för TableControl (format)

Definierar de egenskaper eller skript vars värden visas i en rad.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) TableControl element (format) TableRowEntries-element för TableControl (format) TableRowEntry-element för TableRowEntries för TableControl (format) TableColumnItems-element för TableControlEntry (format)

## <a name="syntax"></a>Syntax

```xml
TableColumnItems>
  <TableColumnItem>...</TableColumnItem>
</TableColumnItems>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attributen, underordnade element och `TableColumnItems` elementets överordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[TableColumnItem-element för TableColumnItems för TableControl (format)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|Nödvändigt element.<br /><br /> Definierar egenskapen eller skriptet vars värde visas i en kolumn i raden.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[TableRowEntry-element för TableRowEntries för TableControl (format)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|Definierar de data som visas i en rad i tabellen.|

## <a name="remarks"></a>Kommentarer

Ett `TableColumnItem` element krävs för varje kolumn i raden. Den första posten visas i första kolumnen, den andra posten i den andra kolumnen och så vidare.

Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).

## <a name="example"></a>Exempel

I följande exempel visas ett- `TableColumnItems` element som definierar tre egenskaper för objektet [system. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) .

```xml
<TableColumnItems>
  <TableColumnItem>
    <PropertyName>Status</PropertyName>
  </TableColumnItem>
  <TableColumnItem>
    <PropertyName>Name</PropertyName>
  </TableColumnItem>
  <TableColumnItem>
    <PropertyName>DisplayName</PropertyName>
  </TableColumnItem>
</TableColumnItems>

```

## <a name="see-also"></a>Se även

[Skapa en tabellvy](./creating-a-table-view.md)

[TableColumnItem-element (format)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[TableRowEntry-element (format)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
