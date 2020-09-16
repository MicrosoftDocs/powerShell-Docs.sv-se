---
title: Justerings element för TableColumnHeader för TableControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 1bf395b84af90d725c14b2f0ef569f72b5fcc613
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783933"
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
