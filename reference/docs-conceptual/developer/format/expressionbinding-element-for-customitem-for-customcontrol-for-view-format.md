---
ms.date: 09/13/2016
ms.topic: reference
title: ExpressionBinding-element för CustomItem för CustomControl för View (format)
description: ExpressionBinding-element för CustomItem för CustomControl för View (format)
ms.openlocfilehash: 8f4bfef4f6c65c6dabc7a776dda1083bac11fdf7
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92648199"
---
# <a name="expressionbinding-element-for-customitem-for-customcontrol-for-view-format"></a>ExpressionBinding-element för CustomItem för CustomControl för View (format)

Definierar de data som visas av kontrollen. Det här elementet används när du definierar en anpassad kontrol vy.

Konfigurations element (format) ViewDefinitions element (format) Visa element (format) CustomControl-element för View (format) CustomEntries-element för CustomControl för View (format) CustomEntry-element för CustomEntries för CustomControl för View (format) CustomItem-element för CustomEntry för CustomControl för View (format) ExpressionBinding-element för CustomItem för View (format)

## <a name="syntax"></a>Syntax

```xml
<ExpressionBinding>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameofCommonCustomControl</CustomControlName>
  <EnumerateCollection/>
  <ItemSelectionCondition>...</ItemSelectionCondition>
  <PropertyName>Nameof.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate></ScriptBlock>
</ExpressionBinding>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och `ExpressionBinding` elementets överordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|`CustomControl Element`|Valfritt element.<br /><br /> Definierar en kontroll som används av den här kontrollen.|
|[CustomControlName-element för ExpressionBinding för CustomControl för View (format)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Valfritt element.<br /><br /> Anger namnet på en gemensam kontroll eller en visnings kontroll.|
|[EnumerateCollection-element för ExpressionBinding för CustomControl för View (format)](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Valfritt element.<br /><br /> Anger att samlings elementen visas.|
|[ItemSelectionCondition-element för ExpressionBinding för CustomControl för View (format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|Valfritt element.<br /><br /> Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas.|
|[PropertyName-element för ExpressionBinding för CustomControl för View (format)](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Valfritt element.<br /><br /> Anger den .NET-egenskap vars värde visas av kontrollen.|
|[Script block-element för ExpressionBinding för CustomCustomControl för View (format)](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Valfritt element.<br /><br /> Anger det skript vars värde visas i kontrollen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomItem-element för CustomEntry för CustomControl för View (format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|Definierar vilka data som visas i vyn anpassad kontroll och hur den visas.|

## <a name="remarks"></a>Kommentarer

## <a name="see-also"></a>Se även

[CustomControlName-element för ExpressionBinding för CustomControl för View (format)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[EnumerateCollection-element för ExpressionBinding för CustomControl för View (format)](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[ItemSelectionCondition-element för ExpressionBinding för CustomControl för View (format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[PropertyName-element för ExpressionBinding för CustomControl för View (format)](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[ScriptBlock-element för ExpressionBinding för CustomControl för View (format)](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[CustomItem-element för CustomEntry för CustomControl för View (format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
