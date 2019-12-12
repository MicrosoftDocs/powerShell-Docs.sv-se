---
title: TableRowEntries-element för TableControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d10b68ca-256c-4c58-b503-73f7777b39ae
caps.latest.revision: 15
ms.openlocfilehash: 88de19be02de4933f892e02093403a82ccdd5788
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72358786"
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

I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet i `TableRowEntries`-elementet.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[TableRowEntry-element för TableRowEntries för TableControl (format)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|Nödvändigt element.<br /><br /> Definierar de data som visas i en rad i tabellen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[TableControl-element (format)](./tablecontrol-element-format.md)|Definierar ett tabell format för en vy.|

## <a name="remarks"></a>Anmärkningar

Du måste ange ett eller flera `TableRowEntry` element för tabellvy. Det finns ingen övre gräns för antalet `TableRowEntry`-element som kan läggas till eller är deras inbördes ordning.

Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).

## <a name="example"></a>Exempel

I följande exempel visas ett `TableRowEntries`-element som definierar en rad som visar värdena för två egenskaper för objektet [system. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) .

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

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
