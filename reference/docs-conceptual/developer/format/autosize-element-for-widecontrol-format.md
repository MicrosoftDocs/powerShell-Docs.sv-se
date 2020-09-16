---
title: AutoSize-element för WideControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 64e62142738916978b37eb1cd3a73536b0447099
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783882"
---
# <a name="autosize-element-for-widecontrol-format"></a>AutoSize-element för WideControl (format)

Anger om kolumn storleken och antalet kolumner justeras baserat på data storleken.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) WideControl-element (format) element för AutoSize för WideControl (format)

## <a name="syntax"></a>Syntax

```xml
<AutoSize/>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och `AutoSize` elementets överordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

Inget

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[WideControl-element (format)](./widecontrol-element-format.md)|Definierar ett brett List format (enskilt värde) för vyn.|

## <a name="remarks"></a>Kommentarer

När du definierar en bred vy kan du lägga till `AutoSize` elementet eller [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) -elementet, men du kan inte lägga till båda.

Mer information om komponenterna i en bred vy finns i [skapa en bred vy](./creating-a-wide-view.md).

Ett exempel på en bred vy finns i [wide View (grundläggande)](./wide-view-basic.md).

## <a name="see-also"></a>Se även

[ColumnNumber-element för WideControl (format)](./columnnumber-element-for-widecontrol-format.md)

[Skapa en bred vy](./creating-a-wide-view.md)

[WideControl-element (format)](./widecontrol-element-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
