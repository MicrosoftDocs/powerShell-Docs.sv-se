---
ms.date: 09/13/2016
ms.topic: reference
title: CustomControlName-element för ExpressionBinding för GroupBy (format)
description: CustomControlName-element för ExpressionBinding för GroupBy (format)
ms.openlocfilehash: bb7dbd449137628da1794628c5a7d7e10158dd46
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92655442"
---
# <a name="customcontrolname-element-for-expressionbinding-for-groupby-format"></a>CustomControlName-element för ExpressionBinding för GroupBy (format)

Anger namnet på en gemensam kontroll eller en visnings kontroll. Det här elementet används när du definierar hur en ny grupp av objekt visas.

Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for GroupBy (format) CustomEntry-element for CustomControl for groupby (format) CustomItem-element för CustomEntry (format) ExpressionBinding element for CustomItem för groupby (format) CustomControlName element for ExpressionBinding

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
|[ExpressionBinding-element för CustomItem för GroupBy (format)](./expressionbinding-element-for-customitem-for-groupby-format.md)|Definierar de data som visas av kontrollen.|

## <a name="text-value"></a>Textvärde

Ange namnet på kontrollen.

## <a name="remarks"></a>Kommentarer

Du kan skapa vanliga kontroller som kan användas av alla vyer i en fil format och du kan skapa visnings kontroller som kan användas av en speciell vy. Följande element anger namnen på dessa kontroller:

- [Name-element för Control för Controls för Configuration (format)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Name-element för Control för Controls för View (format)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Se även

[Name-element för Control för Controls för Configuration (format)](./name-element-for-control-for-controls-for-configuration-format.md)

[Name-element för Control för Controls för View (format)](./name-element-for-control-for-controls-for-view-format.md)

[ExpressionBinding-element för CustomItem för GroupBy (format)](./expressionbinding-element-for-customitem-for-groupby-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
