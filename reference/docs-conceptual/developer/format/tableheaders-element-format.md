---
title: TableHeaders-element (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9fa2b6f-b99a-42de-9779-44e9cb583f71
caps.latest.revision: 15
ms.openlocfilehash: bd44fcf4878c858afe81fb071ce72f627ac465dc
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353699"
---
# <a name="tableheaders-element-format"></a>TableHeaders-element (format)

Definierar rubrikerna för kolumnerna i en tabell.

ViewDefinitions-element (format) View-element (format) TableControl-element (format) TableHeaders-element för TableControl (format)

## <a name="syntax"></a>Syntax

```xml
<TableHeaders>
  <TableColumnHeader>...</TableColumnHeader>
</TableHeaders>

```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attributen, underordnade element och de överordnade elementen i `TableHeaders`-elementet. Det måste finnas ett underordnat element för varje egenskap i objektet som ska visas. Kolumn rubrik informationen visas i den ordning som de underordnade elementen har angetts.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[TableColumnHeader-element (format)](./tablecolumnheader-element-format.md)|Valfritt element.<br /><br /> Definierar etiketten, bredden och data justeringen för en kolumn i en tabellvy.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[TableControl-element (format)](./tablecontrol-element-format.md)|Definierar ett tabell format för en vy.|

## <a name="remarks"></a>Anmärkningar

Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).

## <a name="example"></a>Exempel

I det här exemplet visas ett `TableHeaders`-element som definierar två kolumn rubriker.

```xml
<TableHeaders>
  <TableColumnHeader>
    <Label>Column 1</Label)
    <Width>16</Width>
    <Alignment>Left</Alignment>
  </TableColumnHeader>
  <TableColumnHeader>
    <Label>Column 2</Label)
    <Width>10</Width>
    <Alignment>Centered</Alignment>
  </TableColumnHeader>
</TableHeaders>
```

## <a name="see-also"></a>Se även

[Skapa en tabellvy](./creating-a-table-view.md)

[TableColumnHeader-element (format)](./tablecolumnheader-element-format.md)

[TableControl-element (format)](./tablecontrol-element-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
