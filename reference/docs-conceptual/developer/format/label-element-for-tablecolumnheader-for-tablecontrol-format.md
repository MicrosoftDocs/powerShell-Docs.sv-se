---
title: Etikett element för TableColumnHeader för TableControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: b7b1d6825d3bca0e36b230415d19c2ac48377a46
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785752"
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
