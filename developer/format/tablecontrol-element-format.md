---
title: TableControl Element (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1550b068-dfbc-4ae0-9aa1-72c9a680ec59
caps.latest.revision: 15
ms.openlocfilehash: dd48e82452e83f93e2e005c9db53bbc51d8b2eb4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848855"
---
# <a name="tablecontrol-element-format"></a>TableControl-element (format)

Definierar ett tabellformat för en vy.

ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format)

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

I följande avsnitt beskrivs attribut, underordnade element och överordnade elementet i den `TableControl` element. Du måste ange raderna i tabellen. Alla andra underordnade element är valfria.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[AutoSize-Element för TableControl (Format)](./autosize-element-for-tablecontrol-format.md)|Valfritt element.<br /><br /> Anger om kolumnstorlek och antalet kolumner justeras beroende på storleken på data.|
|[HideTableHeaders Element för TableControl (Format)](./hidetableheaders-element-format.md)|Valfritt element.<br /><br /> Anger om rubriken för tabellen inte ska visas.|
|[TableHeaders Element för TableControl (Format)](./tableheaders-element-format.md)|Element som krävs.<br /><br /> Definierar etiketter, bredderna och justering av data för kolumner i tabellvyn.|
|[TableRowEntries Element för TableCotrol (Format)](./tablerowentries-element-for-tablecontrol-format.md)|Valfritt element.<br /><br /> Innehåller definitioner av tabellvyn.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Visa Element (Format)](./view-element-format.md)|Definierar en vy som används för att visa medlemmarna i ett eller flera objekt.|

## <a name="remarks"></a>Anmärkningar

Läs mer om komponenterna i en tabellvy, [skapar en tabellvy](./creating-a-table-view.md).

## <a name="example"></a>Exempel

Det här exemplet visar en `TableControl` element som används för att visa egenskaperna för den [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objekt.

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

[Visa Element (Format)](./view-element-format.md)

[AutoSize-Element för TableControl (Format)](./autosize-element-for-tablecontrol-format.md)

[HideTableHeaders Element (Format)](./hidetableheaders-element-format.md)

[TableHeaders Element (Format)](./tableheaders-element-format.md)

[TableRowEntries Element (Format)](./tablerowentries-element-for-tablecontrol-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
