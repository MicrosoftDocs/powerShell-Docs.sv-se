---
ms.date: 09/13/2016
ms.topic: reference
title: Control-element för Controls för View  (format)
description: Control-element för Controls för View  (format)
ms.openlocfilehash: c48b8b7ecaebfde5e6ed2123b837d92561551766
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668090"
---
# <a name="control-element-for-controls-for-view--format"></a>Control-element för Controls för View  (format)

Definierar en kontroll som kan användas av vyn och det namn som används för att referera till kontrollen.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) styr element (format) styr element (format) kontroll element för vyer (format)

## <a name="syntax"></a>Syntax

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attributen, underordnade element och `Control` elementets överordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Namn element för kontroll för vy (format)](./name-element-for-control-for-controls-for-view-format.md)|Nödvändigt element.<br /><br /> Anger kontrollens namn.|
|[CustomControl-element för Control för Controls för View (format)](./customcontrol-element-for-control-for-controls-for-view-format.md)|Nödvändigt element.<br /><br /> Definierar den kontroll som används i den här vyn.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Kontrollerar element (format)](./controls-element-for-view-format.md)|Definierar de visnings kontroller som kan användas av en speciell vy.|

## <a name="remarks"></a>Kommentarer

Den här kontrollen kan anges med följande element:

- [CustomControlName-element för ExpressionBinding för Controls för View (format)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [CustomControlName-element för ExpressionBinding för CustomControl för View (format)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [CustomControlName-element för ExpressionBinding för GroupBy (format)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [CustomControlName-element för GroupBy (format)](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a>Se även

[CustomControl-element för Control för Controls för View (format)](./customcontrol-element-for-control-for-controls-for-view-format.md)

[CustomControlName-element för ExpressionBinding för Controls för View (format)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[CustomControlName-element för ExpressionBinding för CustomControl för View (format)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[CustomControlName-element för ExpressionBinding för GroupBy (format)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[CustomControlName-element för ExpressionBinding för GroupBy (format)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[Kontrollerar element (format)](./controls-element-for-view-format.md)

[Name-element för Control för Controls för View (format)](./name-element-for-control-for-controls-for-view-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
