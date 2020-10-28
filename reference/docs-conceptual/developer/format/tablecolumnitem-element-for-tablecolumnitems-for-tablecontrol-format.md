---
ms.date: 09/13/2016
ms.topic: reference
title: TableColumnItem-element för TableColumnItems för TableControl (format)
description: TableColumnItem-element för TableColumnItems för TableControl (format)
ms.openlocfilehash: 8ef5158c9bb9f074d5c58190d4d3b20c10c83744
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92659849"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a>TableColumnItem-element för TableColumnItems för TableControl (format)

Definierar egenskapen eller skriptet vars värde visas i kolumnen på raden.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) TableControl-element (format) TableRowEntries-element för TableControl (format) TableRowEntry-element för TableRowEntries för TableControl (format) TableColumnItems-element för TableControlEntry (format) TableControl-element för TableColumnItem (format)

## <a name="syntax"></a>Syntax

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <FormatString>FormatPattern</FormatString>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attributen, underordnade element och `TableColumnItem` elementets överordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Alignment-element för TableColumnItem för TableControl (format)](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|Valfritt element.<br /><br /> Definierar hur data i en kolumn i raden visas.|
|[FormatString-element för TableColumnItem för TableControl (format)](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|Anger ett format mönster som används för att formatera data i kolumnen i raden.|
|[PropertyName-element för TableColumnItem för TableControl (format)](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|Valfritt element.<br /><br /> Anger namnet på den egenskap vars värde visas.|
|[ScriptBlock-element för TableColumnItem för TableControl (format)](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|Valfritt element.<br /><br /> Anger det skript vars värde visas i kolumnen i en rad.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[TableColumnItems-element för TableControlEntry för TableControl (format)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|Definierar de egenskaper eller skript vars värden visas på raden.|

## <a name="remarks"></a>Kommentarer

Du kan ange en egenskap för ett objekt eller ett skript i varje kolumn i raden. Om inga underordnade element anges, är objektet en plats hållare och inga data visas.

Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).

## <a name="example"></a>Exempel

Det här exemplet visar ett- `TableColumnItem` element som visar värdet på `Status` egenskapen för [system. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) -objektet.

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a>Se även

[Skapa en tabellvy](./creating-a-table-view.md)

[Alignment-element för TableColumnItem för TableControl (format)](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[TableColumnItems-element (format)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[FormatString-element för TableColumnItem för TableControl (format)](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[PropertyName-element för TableColumnItem för TableControl (format)](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[ScriptBlock-element för TableColumnItem för TableControl (format)](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
