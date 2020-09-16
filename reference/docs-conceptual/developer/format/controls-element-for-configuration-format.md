---
title: Kontrollerar element för konfiguration (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 44b9db0d3523e5e9086da9911882b258a2a54ca6
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783797"
---
# <a name="controls-element-for-configuration-format"></a>Controls-element för Configuration (format)

Definierar de gemensamma kontroller som kan användas av alla vyer i formaterings filen.

Konfigurations element (format) styr elementet i konfigurationen (format)

## <a name="syntax"></a>Syntax

```xml
<Controls>
  <Control>...</Control>
</Controls>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attributen, underordnade element och `Controls` elementets överordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Control-element för Controls för Configuration (format)](./control-element-for-controls-for-configuration-format.md)|Nödvändigt element.<br /><br /> Definierar en gemensam kontroll som kan användas av alla vyer i formaterings filen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Configuration-element (format)](./configuration-element-format.md)|Representerar det översta elementet i en textfil.|

## <a name="remarks"></a>Kommentarer

Du kan skapa valfritt antal vanliga kontroller. För varje kontroll måste du ange det namn som ska användas för att referera till kontrollen och kontrollens komponenter.

## <a name="see-also"></a>Se även

[Configuration-element (format)](./configuration-element-format.md)

[Control-element för Controls för Configuration (format)](./control-element-for-controls-for-configuration-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
