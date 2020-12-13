---
ms.date: 09/13/2016
ms.topic: reference
title: TableControl-element (format)
description: TableControl-element (format)
ms.openlocfilehash: 93e05e22d61504d7781b6f3c07f9a3fd0b3c9e8a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651460"
---
# <a name="tablecontrol-element-format"></a>TableControl-element (format)

Definierar ett tabell format för en vy.

ViewDefinitions-element (format) Visa element (format) TableControl-element (format)

## <a name="syntax"></a>Syntax

```xml
<TableControl>
  <AutoSize/>
  <HideTableHeaders/>
  <TableHeaders>...</TableHeaders>
  <TableRowEntries>...</TableRowEntries>
</TableControl>

```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och `TableControl` elementets överordnade element. Du måste ange raderna i tabellen. Alla andra underordnade element är valfria.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[AutoSize-element för TableControl (format)](./autosize-element-for-tablecontrol-format.md)|Valfritt element.<br /><br /> Anger om kolumn storleken och antalet kolumner justeras baserat på data storleken.|
|[HideTableHeaders-element för TableControl (format)](./hidetableheaders-element-format.md)|Valfritt element.<br /><br /> Anger om tabellens rubrik inte visas.|
|[TableHeaders-element för TableControl (format)](./tableheaders-element-format.md)|Nödvändigt element.<br /><br /> Definierar etiketter, bredder och justering för data för kolumnerna i Tabellvy.|
|[TableRowEntries-element för TableControl (format)](./tablerowentries-element-for-tablecontrol-format.md)|Valfritt element.<br /><br /> Innehåller definitionerna för tabellvy.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[View-element (format)](./view-element-format.md)|Definierar en vy som används för att visa medlemmar i ett eller flera objekt.|

## <a name="remarks"></a>Kommentarer

Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).

## <a name="example"></a>Exempel

Det här exemplet visar ett- `TableControl` element som används för att visa egenskaperna för [system. serviceprocess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) -objektet.

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>
    <TableHeaders>...</TableHeaders>
    <TableRowEntries>...</TableRowEntries>
  </TableControl>
</View>

```

## <a name="see-also"></a>Se även

[Skapa en tabellvy](./creating-a-table-view.md)

[View-element (format)](./view-element-format.md)

[AutoSize-element för TableControl (format)](./autosize-element-for-tablecontrol-format.md)

[HideTableHeaders-element (format)](./hidetableheaders-element-format.md)

[TableHeaders-element (format)](./tableheaders-element-format.md)

[TableRowEntries-element (format)](./tablerowentries-element-for-tablecontrol-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
