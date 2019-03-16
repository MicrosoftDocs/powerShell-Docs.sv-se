---
title: TableRowEntries Element för TableControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d10b68ca-256c-4c58-b503-73f7777b39ae
caps.latest.revision: 15
ms.openlocfilehash: 88de19be02de4933f892e02093403a82ccdd5788
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055741"
---
# <a name="tablerowentries-element-for-tablecontrol-format"></a>TableRowEntries-element för TableControl (format)

Definierar raderna i tabellen.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) TableControl Element (Format) TableRowEntries konfigurationselement för TableControl (Format)

## <a name="syntax"></a>Syntax

```xml
<TableRowEntries>
  <TableRowEntry>...</TableRowEntry>
</TableRowEntries>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs de attribut och underordnade element överordnade elementet i den `TableRowEntries` element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[TableRowEntry Element för TableRowEntries för TableControl (Format)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|Element som krävs.<br /><br /> Definierar de data som visas i en rad i tabellen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[TableControl Element (Format)](./tablecontrol-element-format.md)|Definierar ett tabellformat för en vy.|

## <a name="remarks"></a>Anmärkningar

Du måste ange en eller flera `TableRowEntry` -element för tabellvyn. Det finns ingen högsta gräns för hur många `TableRowEntry` element som du kan lägga till och kan inte heller deras inbördes ordning betydande.

Läs mer om komponenterna i en tabellvy, [skapar en tabellvy](./creating-a-table-view.md).

## <a name="example"></a>Exempel

I följande exempel visas en `TableRowEntries` element som definierar en rad som visar värdena för två egenskaper för den [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objekt.

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

[TableControl Element (Format)](./tablecontrol-element-format.md)

[TableRowEntry Element (Format)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
