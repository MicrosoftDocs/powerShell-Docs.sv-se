---
title: PropertyName-element för ItemSelectionCondition för GroupBy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: f6d671035bfd2ef6323b638fdd951bb020bd6548
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780890"
---
# <a name="propertyname-element-for-itemselectioncondition-for-groupby-format"></a>PropertyName-element för ItemSelectionCondition för GroupBy (format)

Anger den .NET-egenskap som utlöser villkoret. När den här egenskapen finns eller när den utvärderas `true` , uppfylls villkoret och kontrollen används. Det här elementet används när du definierar hur en ny grupp av objekt visas.

Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for GroupBy (format) CustomEntry-element för CustomControl för GroupBy (format) CustomItem-element för CustomEntry for GroupBy (format) ExpressionBinding-element för CustomItem for GroupBy (format) ItemSelectionCondition element for ExpressionBinding for GroupBy (format) elementet PropertyName för ItemSelectionCondition för GroupBy (format)

## <a name="syntax"></a>Syntax

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och `PropertyName` elementets överordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

Inga.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ItemSelectionCondition-element för ExpressionBinding för GroupBy (format)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas.|

## <a name="text-value"></a>Textvärde

Ange namnet på den .NET-egenskap som utlöser villkoret.

## <a name="remarks"></a>Kommentarer

Om det här elementet används kan du inte ange [script block](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) -elementet när du definierar urvals villkoret.

## <a name="see-also"></a>Se även

[ScriptBlock-element för ItemSelectionCondition för GroupBy (format)](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)

[ItemSelectionCondition-element för ExpressionBinding för GroupBy (format)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
