---
title: AutoSize-Element för WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: def37479-7b6e-40cf-bc81-0f7cbc651b31
caps.latest.revision: 11
ms.openlocfilehash: 6dbaef5886a0600bd9fe96dbc8d21f00a674dfcf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066931"
---
# <a name="autosize-element-for-widecontrol-format"></a>AutoSize-element för WideControl (format)

Anger om kolumnstorlek och antalet kolumner justeras beroende på storleken på data.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) WideControl Element (Format) Autosize konfigurationselement för WideControl (Format)

## <a name="syntax"></a>Syntax

```xml
<AutoSize/>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `AutoSize` element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Inga

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[WideControl Element (Format)](./widecontrol-element-format.md)|Definierar en bred (enstaka värde) listformat för vyn.|

## <a name="remarks"></a>Anmärkningar

När du definierar en bred vy, kan du lägga till den `AutoSize` element eller [antal_kolumner anger](./columnnumber-element-for-widecontrol-format.md) element, men du kan inte lägga till båda.

Mer information om komponenter för en bred vy finns i [skapar en bred vy](./creating-a-wide-view.md).

Ett exempel på en bred vy finns i [bred vy (grundläggande)](./wide-view-basic.md).

## <a name="see-also"></a>Se även

[Antal_kolumner anger Element för WideControl (Format)](./columnnumber-element-for-widecontrol-format.md)

[Skapa en bred vy](./creating-a-wide-view.md)

[WideControl Element (Format)](./widecontrol-element-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
