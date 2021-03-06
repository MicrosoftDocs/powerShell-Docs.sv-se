---
ms.date: 09/13/2016
ms.topic: reference
title: Alignment-element för TableColumnHeader för TableControl (format)
description: Alignment-element för TableColumnHeader för TableControl (format)
ms.openlocfilehash: cf8b90c12c28951283b5870186e2c88d427318a5
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666832"
---
# <a name="alignment-element-for-tablecolumnheader-for-tablecontrol-format"></a>Alignment-element för TableColumnHeader för TableControl (format)

Definierar hur data i en kolumn rubrik visas.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) TableControl element (format) TableHeaders element (format) TableColumnHeader element (format) justerings element för TableColumnHeader (format)

## <a name="syntax"></a>Syntax

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attributen, underordnade element och `Alignment` elementets överordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

Inga.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[TableColumnHeader-element (format)](./tablecolumnheader-element-format.md)|Definierar en etikett, bredd och justering för data i en kolumn i tabellen.|

## <a name="text-value"></a>Textvärde

Ange ett av följande värden. De här värdena är inte skiftlägeskänsliga.

Vänster justerar data som visas i kolumnen till vänster detta är standardvärdet om det här elementet inte har angetts.

Högerjusterar de data som visas i kolumnen till höger.

Center centrerar de data som visas i kolumnen.

## <a name="remarks"></a>Kommentarer

Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).

## <a name="example"></a>Exempel

I det här exemplet visas ett `TableColumnHeader` element vars data justeras till vänster.

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a>Se även

[Skapa en tabellvy](./creating-a-table-view.md)

[TableColumnHeader-element (format)](./tablecolumnheader-element-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
