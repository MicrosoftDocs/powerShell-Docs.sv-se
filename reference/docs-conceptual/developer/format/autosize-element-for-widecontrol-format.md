---
title: AutoSize-element för WideControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: def37479-7b6e-40cf-bc81-0f7cbc651b31
caps.latest.revision: 11
ms.openlocfilehash: 6dbaef5886a0600bd9fe96dbc8d21f00a674dfcf
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359102"
---
# <a name="autosize-element-for-widecontrol-format"></a>AutoSize-element för WideControl (format)

Anger om kolumn storleken och antalet kolumner justeras baserat på data storleken.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) WideControl-element (format) element för AutoSize för WideControl (format)

## <a name="syntax"></a>Syntax

```xml
<AutoSize/>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för elementet `AutoSize`.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Inga

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[WideControl-element (format)](./widecontrol-element-format.md)|Definierar ett brett List format (enskilt värde) för vyn.|

## <a name="remarks"></a>Anmärkningar

När du definierar en bred vy kan du lägga till `AutoSize`-elementet eller [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) -elementet, men du kan inte lägga till båda.

Mer information om komponenterna i en bred vy finns i [skapa en bred vy](./creating-a-wide-view.md).

Ett exempel på en bred vy finns i [wide View (grundläggande)](./wide-view-basic.md).

## <a name="see-also"></a>Se även

[ColumnNumber-element för WideControl (format)](./columnnumber-element-for-widecontrol-format.md)

[Skapa en bred vy](./creating-a-wide-view.md)

[WideControl-element (format)](./widecontrol-element-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
