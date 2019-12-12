---
title: TableControl-element (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1550b068-dfbc-4ae0-9aa1-72c9a680ec59
caps.latest.revision: 15
ms.openlocfilehash: 3942c008e026b0b99db3c77af4a0152b50fffc4e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72358795"
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

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `TableControl`-elementet. Du måste ange raderna i tabellen. Alla andra underordnade element är valfria.

### <a name="attributes"></a>Attribut

Ingen.

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
|[Visa element (format)](./view-element-format.md)|Definierar en vy som används för att visa medlemmar i ett eller flera objekt.|

## <a name="remarks"></a>Anmärkningar

Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).

## <a name="example"></a>Exempel

I det här exemplet visas ett `TableControl`-element som används för att visa egenskaperna för objektet [system. serviceprocess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .

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

[Visa element (format)](./view-element-format.md)

[AutoSize-element för TableControl (format)](./autosize-element-for-tablecontrol-format.md)

[HideTableHeaders-element (format)](./hidetableheaders-element-format.md)

[TableHeaders-element (format)](./tableheaders-element-format.md)

[TableRowEntries-element (format)](./tablerowentries-element-for-tablecontrol-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
