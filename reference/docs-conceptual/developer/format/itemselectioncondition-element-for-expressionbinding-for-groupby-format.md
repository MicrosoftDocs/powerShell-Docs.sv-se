---
ms.date: 09/13/2016
ms.topic: reference
title: ItemSelectionCondition-element för ExpressionBinding för GroupBy (format)
description: ItemSelectionCondition-element för ExpressionBinding för GroupBy (format)
ms.openlocfilehash: 92120ace5ed316fbfbf1d51422071c27d5a604cf
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92651979"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-groupby-format"></a>ItemSelectionCondition-element för ExpressionBinding för GroupBy (format)

Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas. Det finns ingen gräns för antalet urvals villkor som kan anges för ett kontroll objekt. Det här elementet används när du definierar hur en ny grupp av objekt visas.

Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for GroupBy (format) CustomEntry-element for CustomControl for groupby (format) CustomItem-element för CustomEntry (format) ExpressionBinding element for CustomItem för groupby (format) ItemSelectionCondition element for ExpressionBinding

## <a name="syntax"></a>Syntax

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och `ItemSelectionCondition` elementets överordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[PropertyName-element för ItemSelectionCondition för GroupBy (format)](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)|Valfritt element.<br /><br /> Anger den .NET-egenskap som utlöser villkoret.|
|[ScriptBlock-element för ItemSelectionCondition för GroupBy (format)](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)|Valfritt element.<br /><br /> Anger det skript som utlöser villkoret.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ExpressionBinding-element för CustomItem för GroupBy (format)](./expressionbinding-element-for-customitem-for-groupby-format.md)|Definierar de data som visas av kontrollen.|

## <a name="remarks"></a>Kommentarer

Du kan ange ett egenskaps namn eller ett skript för villkoret, men kan inte ange båda.

## <a name="see-also"></a>Se även

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)

[ExpressionBinding-element för CustomItem för GroupBy (format)](./expressionbinding-element-for-customitem-for-groupby-format.md)
