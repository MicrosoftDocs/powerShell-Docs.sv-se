---
title: TableColumnItem-element för TableColumnItems för TableControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef8395aa-4b31-48c0-a0b8-b481fd0b3738
caps.latest.revision: 15
ms.openlocfilehash: 9e6cffc7476ef01124d95ecbf287d9788b0324c9
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/19/2019
ms.locfileid: "71143587"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a>TableColumnItem-element för TableColumnItems för TableControl (format)

Definierar egenskapen eller skriptet vars värde visas i kolumnen på raden.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) TableControl element (format) TableRowEntries-element för TableControl (format) TableRowEntry-element för TableRowEntries (format) TableColumnItems-element för TableControlEntry för TableControl (format) TableColumnItem-elementet för TableColumnItems för TableControl (format)

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

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Justerings element för TableColumnItem för TableControl (format)](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|Valfritt element.<br /><br /> Definierar hur data i en kolumn i raden visas.|
|[FormatString-element för TableColumnItem för TableControl (format)](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|Anger ett format mönster som används för att formatera data i kolumnen i raden.|
|[PropertyName-element för TableColumnItem för TableControl (format)](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|Valfritt element.<br /><br /> Anger namnet på den egenskap vars värde visas.|
|[Script block-element för TableColumnItem för TableControl (format)](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|Valfritt element.<br /><br /> Anger det skript vars värde visas i kolumnen i en rad.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[TableColumnItems-element för TableControlEntry för TableControl (format)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|Definierar de egenskaper eller skript vars värden visas på raden.|

## <a name="remarks"></a>Anmärkningar

Du kan ange en egenskap för ett objekt eller ett skript i varje kolumn i raden. Om inga underordnade element anges, är objektet en plats hållare och inga data visas.

Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).

## <a name="example"></a>Exempel

Det här exemplet visar `TableColumnItem` ett-element som visar värdet `Status` på egenskapen för [system. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) -objektet.

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a>Se även

[Skapa en tabellvy](./creating-a-table-view.md)

[Justerings element för TableColumnItem för TableControl (format)](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[TableColumnItems-element (format)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[FormatString-element för TableColumnItem för TableControl (format)](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[PropertyName-element för TableColumnItem för TableControl (format)](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[Script block-element för TableColumnItem för TableControl (format)](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
