---
title: Bredd element för TableColumnHeader för TableControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e9540d3d351041ad7cb98a21bb360ebea7eca117
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779921"
---
# <a name="width-element-for-tablecolumnheader-for-tablecontrol-format"></a>Width-element för TableColumnHeader för TableControl (format)

Definierar bredden (i tecken) för en kolumn.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) TableControl element (format) TableHeaders-element för TableControl (format) TableColumnHeader element TableHeaders för TableControl (format) width-element för TableColumnHeader (format)

## <a name="syntax"></a>Syntax

```xml
<Width>NumberOfCharacters</Width>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet för det `Width` element som används när kolumn rubriker definieras.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

Inga.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[TableColumnHeader-element för TableHeaders för TableControl (format)](./tablecolumnheader-element-format.md)|Definierar en etikett, bredd och justering för data i en kolumn i tabellen.|

## <a name="text-value"></a>Textvärde

När som helst kan du ange en bredd (i tecken) som är större än längden på de visade egenskapsvärdena.

## <a name="remarks"></a>Kommentarer

Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).

## <a name="example"></a>Exempel

I följande exempel visas ett `TableColumnHeader` element vars bredd är 16 tecken.

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a>Se även

[Skapa en tabellvy](./creating-a-table-view.md)

[TableColumnHeader-element för TableHeader för TableControl (format)](./tablecolumnheader-element-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
