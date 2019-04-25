---
title: TableRowEntry Element för TableRowEntries för TableControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 18d86af7-7ff9-4968-81be-2caa61937d49
caps.latest.revision: 10
ms.openlocfilehash: 946ffb3fe857503c02b9000238a86775969abbd6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075332"
---
# <a name="tablerowentry-element-for-tablerowentries-for-tablecontrol-format"></a>TableRowEntry-element för TableRowEntries för TableControl (format)

Definierar de data som visas i en rad i tabellen.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) TableControl Element (Format) TableRowEntries konfigurationselement för TableControl (Format) TableRowEntry elementet för TableRowEntries för TableControl (Format)

## <a name="syntax"></a>Syntax

```xml
<TableRowEntry>
  <Wrap/>
  <EntrySelectedBy>...</EntrySelectedBy>
  <TableColumnItems>...</TableColumnItems>
</TableRowEntry>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och överordnade elementet i den `TableRowEntry` element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[EntrySelectedBy Element för TableRowEntry för TableControl (Format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Element som krävs.<br /><br /> Definierar de objekt vars egenskapsvärden visas i raden.|
|[TableColumnItems Element för TableRowEntry för TableControl (Format)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|Element som krävs.<br /><br /> Definierar egenskaper eller skript som vars värden visas.|
|[Omsluta Element för TableRowEntry för TableControl (Format)](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)|Valfritt element.<br /><br /> Anger att text som överskrider kolumnbredden visas på nästa rad.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[TableRowEntries Element för TableControl (Format)](./tablerowentries-element-for-tablecontrol-format.md)|Definierar raderna i tabellen.|

## <a name="remarks"></a>Anmärkningar

En `TableColumnItems` element och en `EntrySelectedBy` element måste anges.

Läs mer om komponenterna i en tabellvy, [skapar en tabellvy](./creating-a-table-view.md).

## <a name="example"></a>Exempel

I följande exempel visas en `TableRowEntry` element som definierar en rad som visar värdena för två egenskaper för den [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objekt.

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

[EntrySelectedBy Element för TableRowEntry för TableControl (Format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[TableColumnItems Element för TableRowEntry för TableControl (Format)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[TableRowEntries Element för TableControl (Format)](./tablerowentries-element-for-tablecontrol-format.md)

[Omsluta Element för TableRowEntry för TableControl (Format)](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
