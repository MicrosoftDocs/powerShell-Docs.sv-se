---
ms.date: 09/13/2016
ms.topic: reference
title: TableRowEntries-element för TableControl (format)
description: TableRowEntries-element för TableControl (format)
ms.openlocfilehash: 1df63e645234da8276c7ccc5af34e81a56475e43
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651473"
---
# <a name="tablerowentries-element-for-tablecontrol-format"></a>TableRowEntries-element för TableControl (format)

Definierar raderna i tabellen.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) TableControl-element (format) element för TableControl (format)

## <a name="syntax"></a>Syntax

```xml
<TableRowEntries>
  <TableRowEntry>...</TableRowEntry>
</TableRowEntries>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attributen, underordnade element och `TableRowEntries` elementets överordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[TableRowEntry-element för TableRowEntries för TableControl (format)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|Nödvändigt element.<br /><br /> Definierar de data som visas i en rad i tabellen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[TableControl-element (format)](./tablecontrol-element-format.md)|Definierar ett tabell format för en vy.|

## <a name="remarks"></a>Kommentarer

Du måste ange ett eller flera `TableRowEntry` element i vyn tabellvy. Det finns ingen övre gräns för antalet `TableRowEntry` element som kan läggas till eller som är deras inbördes ordning.

Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).

## <a name="example"></a>Exempel

I följande exempel visas ett- `TableRowEntries` element som definierar en rad som visar värdena för två egenskaper för objektet [system. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) .

```xml
<TableRowEntries>
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
</TableRowEntries>

```

## <a name="see-also"></a>Se även

[Skapa en tabellvy](./creating-a-table-view.md)

[TableControl-element (format)](./tablecontrol-element-format.md)

[TableRowEntry-element (format)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
