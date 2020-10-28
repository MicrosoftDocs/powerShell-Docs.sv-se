---
ms.date: 09/13/2016
ms.topic: reference
title: ColumnNumber-element för WideControl (format)
description: ColumnNumber-element för WideControl (format)
ms.openlocfilehash: 1ddbbfbd5b53065afcc6c1326d6abf1fadedc67b
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92648391"
---
# <a name="columnnumber-element-for-widecontrol-format"></a>ColumnNumber-element för WideControl (format)

Anger antalet kolumner som visas i den bred vyn.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) WideControl-element (format) element för WideControl (format)

## <a name="syntax"></a>Syntax

```xml
<ColumnNumber>PositiveInteger</ColumnNumber>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och `ColumnNumber` elementets överordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

Inga.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[WideControl-element (format)](./widecontrol-element-format.md)|Definierar ett brett List format (enskilt värde) för vyn.|

## <a name="text-value"></a>Textvärde

Ange ett positivt heltals värde.

## <a name="remarks"></a>Kommentarer

När du definierar en bred vy kan du lägga till `AutoSize` elementet eller `ColumnNumber` elementet, men du kan inte lägga till båda.

Mer information om komponenterna i en bred vy finns i [skapa en bred vy](./creating-a-wide-view.md).

Ett exempel på en bred vy finns i [wide View (grundläggande)](./wide-view-basic.md).

## <a name="see-also"></a>Se även

[AutoSize-element för WideControl (format)](./autosize-element-for-widecontrol-format.md)

[Skapa en bred vy](./creating-a-wide-view.md)

[Bred vy (grundläggande)](./wide-view-basic.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
