---
ms.date: 09/13/2016
ms.topic: reference
title: Label-element för TableColumnHeader för TableControl (format)
description: Label-element för TableColumnHeader för TableControl (format)
ms.openlocfilehash: fe4c209903c04e683b44e2bdcbf381adb6874ace
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667801"
---
# <a name="label-element-for-tablecolumnheader-for-tablecontrol-format"></a>Label-element för TableColumnHeader för TableControl (format)

Definierar etiketten som visas överst i en kolumn. Det här elementet används när du definierar en tabellvy.

Konfigurations element (format) ViewDefinitions element (format) Visa element (format) TableControl element (format) TableHeaders-element för TableControl (format) TableColumnHeader element för TableHeaders för TableControl (format) etikett element för TableColumnHeader (format)

## <a name="syntax"></a>Syntax

```xml
<Label>DisplayedLabel</Label>

```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attributen, underordnade element och `Label` elementets överordnade element. Endast en etikett tillåts för varje kolumn.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

Inga.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[TableColumnHeader-element för TableHeaders för TableControl (format)](./tablecolumnheader-element-format.md)|Definierar en etikett, bredd och justering för data i en kolumn i tabellen.|

## <a name="text-value"></a>Textvärde

Ange texten som visas överst i kolumnen i tabellen. Det finns inga begränsade tecken för kolumn etiketten.

## <a name="remarks"></a>Kommentarer

Om ingen etikett anges används namnet på den egenskap vars värde visas i raderna.

Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).

## <a name="example"></a>Exempel

Det här exemplet visar ett `TableColumnHeader` element vars etikett är "kolumn 1".

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
