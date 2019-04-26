---
title: Justering Element för TableColumnHeader för TableControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff85e83a-c9c2-4c37-accc-e6a27c182f3c
caps.latest.revision: 19
ms.openlocfilehash: 16b41535109ca503e679a135f5ba30054e33de5b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067016"
---
# <a name="alignment-element-for-tablecolumnheader-for-tablecontrol-format"></a>Alignment-element för TableColumnHeader för TableControl (format)

Definierar hur data i en kolumnrubrik visas.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) TableControl Element (Format) TableHeaders Element (Format) TableColumnHeader Element (Format) justering konfigurationselement för TableColumnHeader (Format)

## <a name="syntax"></a>Syntax

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs de attribut och underordnade element överordnade elementet i den `Alignment` element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[TableColumnHeader Element (Format)](./tablecolumnheader-element-format.md)|Definierar en etikett, bredd och justering av data för en kolumn i tabellen.|

## <a name="text-value"></a>Textvärde

Ange ett av följande värden. Dessa värden är inte skiftlägeskänsliga.

Vänsterjusterar data som visas i kolumnen till vänster detta är standardvärdet om det här elementet inte har angetts.

Högerjusterar data visas i kolumnen till höger.

Center Datacenter data som visas i kolumnen.

## <a name="remarks"></a>Anmärkningar

Läs mer om komponenterna i en tabellvy, [skapar en tabellvy](./creating-a-table-view.md).

## <a name="example"></a>Exempel

Det här exemplet visar en `TableColumnHeader` element vars data justeras till vänster.

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a>Se även

[Skapa en tabellvy](./creating-a-table-view.md)

[TableColumnHeader Element (Format)](./tablecolumnheader-element-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
