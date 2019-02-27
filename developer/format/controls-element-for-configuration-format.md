---
title: Styr Element för konfiguration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d4ef63d-5866-4319-ba00-7ed96de26821
caps.latest.revision: 18
ms.openlocfilehash: ac9f7ff08f6e87ef83b5a2fe23fc58ee2651566d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850437"
---
# <a name="controls-element-for-configuration-format"></a>Controls-element för Configuration (format)

Definierar de vanliga kontroller som kan användas av alla vyer i filen formatering.

Konfigurationselementet Element (Format) kontroller av konfigurationen (Format)

## <a name="syntax"></a>Syntax

```xml
<Controls>
  <Control>...</Control>
</Controls>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `Controls` element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Control-Element för kontroller för Configuration (Format)](./control-element-for-controls-for-configuration-format.md)|Element som krävs.<br /><br /> Definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Konfigurationselementet (Format)](./configuration-element-format.md)|Representerar det översta elementet i en formatering fil.|

## <a name="remarks"></a>Anmärkningar

Du kan skapa hur många vanliga kontroller som helst. Du måste ange det namn som används för att referera till kontrollen och komponenterna i kontrollen för varje kontroll.

## <a name="see-also"></a>Se även

[Konfigurationselementet (Format)](./configuration-element-format.md)

[Control-Element för kontroller för Configuration (Format)](./control-element-for-controls-for-configuration-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
