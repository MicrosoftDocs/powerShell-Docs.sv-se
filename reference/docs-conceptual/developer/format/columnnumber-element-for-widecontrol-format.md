---
title: ColumnNumber-element för WideControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 5f151bb0e629efcebe6295cdcae6cebcbbb1b39b
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783865"
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
