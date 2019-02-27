---
title: EntrySelectedBy Element för TableRowEntry för TableControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49623fcf-1238-4d20-a7ce-238d47d9d565
caps.latest.revision: 15
ms.openlocfilehash: e18564c10898c73128e0a4bc7d077e7c7ffb1c22
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851242"
---
# <a name="entryselectedby-element-for-tablerowentry--for-tablecontrol-format"></a>EntrySelectedBy-element för TableRowEntry  för TableControl (format)

Definierar vilka typer av .NET som använder den här definitionen av tabellvyn eller villkor som måste finnas för den här definitionen som ska användas.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy konfigurationselement (Format)

## <a name="syntax"></a>Syntax

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `EntrySelectedBy` element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[SelectionCondition Element för EntrySelectedBy för TableControl (Format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|Valfritt element.<br /><br /> Definierar de villkor som måste finnas för den här tabellen vydefinitionen som ska användas.|
|[SelectionSetName Element för EntrySelectedBy för TableControl (Format)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)|Valfritt element.<br /><br /> Anger en uppsättning med .NET-typer som använder den här tabellen vydefinitionen.|
|[TypeName-Element för EntrySelectedBy för TableControl (Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md)|Valfritt element.<br /><br /> Anger ett .NET-typ som använder den här tabellen vydefinitionen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[TableRowEntry Element för TableControl (Format)](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)|Definierar de data som visas i en rad i tabellen.|

## <a name="remarks"></a>Anmärkningar

Du måste ange minst en typ, val av set eller urvalsvillkoret för en tabell vydefinitionen. Det finns ingen högsta gräns för antalet underordnade element som du kan använda.

Val av villkor används för att definiera ett villkor som måste finnas för definitionen som ska användas, till exempel när ett objekt har en specifik egenskap eller som en specifik egenskapsvärde eller ett skript som utvärderas till `true`. Mer information om val av villkor finns i [definiera villkor för när en post i vyn eller objektet används](./defining-conditions-for-displaying-data.md).

Läs mer om komponenterna i en tabellvy, [skapar en tabellvy](./creating-a-table-view.md).

## <a name="example"></a>Exempel

I följande exempel visas en `TableRowEntry` element som används för att visa egenskaperna för den [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objekt.

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

[SelectionCondition Element för EntrySelectedBy för TableControl (Format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[SelectionSetName Element för EntrySelectedBy för TableControl (Format)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

[TableRowEntry Element för TableControl (Format)](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)

[TypeName-Element för EntrySelectedBy för TableControl (Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
