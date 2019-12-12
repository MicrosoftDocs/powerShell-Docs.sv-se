---
title: EntrySelectedBy-element för TableRowEntry för TableControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49623fcf-1238-4d20-a7ce-238d47d9d565
caps.latest.revision: 15
ms.openlocfilehash: 9302bfed0324773cb98d698acdcf608f34ee19c1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354763"
---
# <a name="entryselectedby-element-for-tablerowentry--for-tablecontrol-format"></a>EntrySelectedBy-element för TableRowEntry  för TableControl (format)

Definierar de .NET-typer som använder den här definitionen av Tabellvy eller det villkor som måste finnas för att den här definitionen ska kunna användas.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) TableControl-element (format) TableRowEntries-element (format) TableRowEntry-element (format) EntrySelectedBy-element (format)

## <a name="syntax"></a>Syntax

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `EntrySelectedBy`-elementet.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[SelectionCondition-element för EntrySelectedBy för TableControl (format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|Valfritt element.<br /><br /> Definierar det villkor som måste finnas för att den här tabell visnings definitionen ska kunna användas.|
|[SelectionSetName-element för EntrySelectedBy för TableControl (format)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)|Valfritt element.<br /><br /> Anger en uppsättning av .NET-typer som använder den här Table View-definitionen.|
|[Elementet TypeName för EntrySelectedBy för TableControl (format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md)|Valfritt element.<br /><br /> Anger en .NET-typ som använder den här Table View-definitionen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[TableRowEntry-element för TableControl (format)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|Definierar de data som visas i en rad i tabellen.|

## <a name="remarks"></a>Anmärkningar

Du måste ange minst en typ, markerings uppsättning eller ett markerings villkor för en tabell visnings definition. Det finns ingen övre gräns för antalet underordnade element som du kan använda.

Urvals villkor används för att definiera ett villkor som måste finnas för att definitionen ska kunna användas, till exempel när ett objekt har en speciell egenskap eller ett angivet egenskaps värde eller skript utvärderar till `true`. Mer information om urvals villkor finns i [definiera villkor för när en visnings post eller ett objekt används](./defining-conditions-for-displaying-data.md).

Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).

## <a name="example"></a>Exempel

I följande exempel visas ett `TableRowEntry`-element som används för att visa egenskaperna för [system. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) -objektet.

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </EntrySelectedBy>
  <TableColumnItems>
    <TableColumnItem>
      <PropertyName>PropertyForFirstColumn</PropertyName>
    </TableColumnItem>
    <TableColumnItem>
      <PropertyName>PropertyForSecondColumn</PropertyName>
    </TableColumnItem>
  </TableColumnItems>
</TableRowEntry>
```

## <a name="see-also"></a>Se även

[Skapa en tabellvy](./creating-a-table-view.md)

[SelectionCondition-element för EntrySelectedBy för TableControl (format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[SelectionSetName-element för EntrySelectedBy för TableControl (format)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

[TableRowEntry-element för TableControl (format)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[Elementet TypeName för EntrySelectedBy för TableControl (format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
