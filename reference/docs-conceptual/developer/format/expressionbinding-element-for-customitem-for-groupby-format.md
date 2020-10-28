---
ms.date: 09/13/2016
ms.topic: reference
title: ExpressionBinding-element för CustomItem för GroupBy (format)
description: ExpressionBinding-element för CustomItem för GroupBy (format)
ms.openlocfilehash: 742d9f081a674dc3ee4c84d600933aaf57b2aa6b
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92655301"
---
# <a name="expressionbinding-element-for-customitem-for-groupby-format"></a>ExpressionBinding-element för CustomItem för GroupBy (format)

Definierar de data som visas av kontrollen. Det här elementet används när du definierar hur en ny grupp av objekt visas.

Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for GroupBy (format) CustomEntry-element for CustomControl for groupby (format) CustomItem-element för CustomEntry (format)

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
|[CustomControlName-element för ExpressionBinding för GroupBy (format)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)|Valfritt element.<br /><br /> Anger namnet på en gemensam kontroll eller en visnings kontroll.|
|[EnumerateCollection-element för ExpressionBinding för groupby (format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md) EnumerateCollection-element för ExpressionBinding för GroupBy (format)|Valfritt element.<br /><br /> Anger att samlings elementen visas.|
|[ItemSelectionCondition-element för ExpressionBinding för GroupBy (format)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|Valfritt element.<br /><br /> Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas.|
|[PropertyName-element för ExpressionBinding för GroupBy (format)](./propertyname-element-for-expressionbinding-for-groupby-format.md)|Valfritt element.<br /><br /> Anger den .NET-egenskap vars värde visas av kontrollen.|
|[ScriptBlock-element för ExpressionBinding för GroupBy (format)](./scriptblock-element-for-expressionbinding-for-groupby-format.md)|Valfritt element.<br /><br /> Anger det skript vars värde visas i kontrollen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomItem-element för CustomEntry för GroupBy (format)](./customitem-element-for-customentry-for-groupby-format.md)|Definierar vilka data som visas i vyn anpassad kontroll och hur den visas.|

## <a name="see-also"></a>Se även

[CustomControlName-element för ExpressionBinding för GroupBy (format)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[EnumerateCollection-element för ExpressionBinding för GroupBy (format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)

[ItemSelectionCondition-element för ExpressionBinding för GroupBy (format)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[PropertyName-element för ExpressionBinding för GroupBy (format)](./propertyname-element-for-expressionbinding-for-groupby-format.md)

[ScriptBlock-element för ExpressionBinding för GroupBy (format)](./scriptblock-element-for-expressionbinding-for-groupby-format.md)

[CustomItem-element för CustomEntry för GroupBy (format)](./customitem-element-for-customentry-for-groupby-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
