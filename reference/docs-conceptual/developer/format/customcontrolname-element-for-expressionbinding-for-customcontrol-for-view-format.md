---
ms.date: 09/13/2016
ms.topic: reference
title: CustomControlName-element för ExpressionBinding för CustomControl för View (format)
description: CustomControlName-element för ExpressionBinding för CustomControl för View (format)
ms.openlocfilehash: 24b27428c07d7178f0069f6d0e5b7ffc555efe34
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92666815"
---
# <a name="customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format"></a>CustomControlName-element för ExpressionBinding för CustomControl för View (format)

Anger namnet på en gemensam kontroll eller en visnings kontroll. Det här elementet används när du definierar en anpassad kontrol vy.

Konfigurations element (format) ViewDefinitions-element (format) Visa element (format) CustomControl-element för View (format) CustomEntries-element för CustomControl för View (format) CustomEntry-element för CustomEntries för View (format) CustomItem-element för CustomEntry för View (format) ExpressionBinding-element för CustomItem (format)

## <a name="syntax"></a>Syntax

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och `CustomControlName` elementets överordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

Inga.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ExpressionBinding-element för CustomItem (format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|Definierar de data som visas av kontrollen.|

## <a name="text-value"></a>Textvärde

Ange namnet på kontrollen.

## <a name="remarks"></a>Kommentarer

Du kan skapa vanliga kontroller som kan användas av alla vyer i en fil format och du kan skapa visnings kontroller som kan användas av en speciell vy. Namnen på dessa kontroller anges med följande element.

- [Name-element för Control för Controls för Configuration (format)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Name-element för Control för Controls för View (format)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Se även

[Name-element för Control för Controls för Configuration (format)](./name-element-for-control-for-controls-for-configuration-format.md)

[Name-element för Control för Controls för View (format)](./name-element-for-control-for-controls-for-view-format.md)

[ExpressionBinding-element för CustomItem (format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
