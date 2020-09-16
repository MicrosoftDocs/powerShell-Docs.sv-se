---
title: TableHeaders-element (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: b3176cbe1316d5b30cb61831d9915a80389709a5
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787435"
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
