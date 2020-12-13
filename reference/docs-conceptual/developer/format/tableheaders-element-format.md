---
ms.date: 09/13/2016
ms.topic: reference
title: TableHeaders-element (format)
description: TableHeaders-element (format)
ms.openlocfilehash: 5ac4dccae746c167ebf95add9f3d18030a2b3a99
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659823"
---
# <a name="tableheaders-element-format"></a>TableHeaders-element (format)

Definierar rubrikerna för kolumnerna i en tabell.

ViewDefinitions-element (format) View-element (format) TableControl-element (format) TableHeaders-element för TableControl (format)

## <a name="syntax"></a>Syntax

```xml
<TableHeaders>
  <TableColumnHeader>...</TableColumnHeader>
</TableHeaders>

```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attributen, underordnade element och `TableHeaders` elementens överordnade element. Det måste finnas ett underordnat element för varje egenskap i objektet som ska visas. Kolumn rubrik informationen visas i den ordning som de underordnade elementen har angetts.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[TableColumnHeader-element (format)](./tablecolumnheader-element-format.md)|Valfritt element.<br /><br /> Definierar etiketten, bredden och data justeringen för en kolumn i en tabellvy.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[TableControl-element (format)](./tablecontrol-element-format.md)|Definierar ett tabell format för en vy.|

## <a name="remarks"></a>Kommentarer

Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).

## <a name="example"></a>Exempel

Det här exemplet visar ett `TableHeaders` element som definierar två kolumn rubriker.

```xml
<TableHeaders>
  <TableColumnHeader>
    <Label>Column 1</Label)
    <Width>16</Width>
    <Alignment>Left</Alignment>
  </TableColumnHeader>
  <TableColumnHeader>
    <Label>Column 2</Label)
    <Width>10</Width>
    <Alignment>Centered</Alignment>
  </TableColumnHeader>
</TableHeaders>
```

## <a name="see-also"></a>Se även

[Skapa en tabellvy](./creating-a-table-view.md)

[TableColumnHeader-element (format)](./tablecolumnheader-element-format.md)

[TableControl-element (format)](./tablecontrol-element-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
