---
title: Bredd-Element för TableColumnHeader för TableControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 94eb0535-8002-4f17-9a2b-4be75ec20e5c
caps.latest.revision: 18
ms.openlocfilehash: 4a25c9d81df670dc10955065bfb66766cdb1bd33
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083628"
---
# <a name="width-element-for-tablecolumnheader-for-tablecontrol-format"></a>Width-element för TableColumnHeader för TableControl (format)

Anger bredden (i antal tecken) för en kolumn.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) TableControl Element (Format) TableHeaders konfigurationselement för TableControl (Format) TableColumnHeader elementet TableHeaders för TableControl (Format) bredd-elementet för TableColumnHeader för TableControl (Format)

## <a name="syntax"></a>Syntax

```xml
<Width>NumberOfCharacters</Width>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs de attribut och underordnade element överordnade elementet i den `Width` element som används när du definierar kolumnrubriker.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[TableColumnHeader Element för TableHeaders för TableControl (Format)](./tablecolumnheader-element-format.md)|Definierar en etikett, bredd och justering av data för en kolumn i tabellen.|

## <a name="text-value"></a>Textvärde

Ange en bredd (i antal tecken) som är större än längden på de visade egenskapsvärdena när de är på alla möjliga.

## <a name="remarks"></a>Anmärkningar

Läs mer om komponenterna i en tabellvy, [skapar en tabellvy](./creating-a-table-view.md).

## <a name="example"></a>Exempel

I följande exempel visas en `TableColumnHeader` element vars bredd är 16 tecken.

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a>Se även

[Skapa en tabellvy](./creating-a-table-view.md)

[TableColumnHeader Element för TableHeader för TableControl (Format)](./tablecolumnheader-element-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
