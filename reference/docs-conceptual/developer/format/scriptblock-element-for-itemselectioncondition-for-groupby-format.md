---
ms.date: 09/13/2016
ms.topic: reference
title: ScriptBlock-element för ItemSelectionCondition för GroupBy (format)
description: ScriptBlock-element för ItemSelectionCondition för GroupBy (format)
ms.openlocfilehash: fe366fa31b93e8d69409cc49c3fe2c350d4d06d9
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665087"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-groupby-format"></a>ScriptBlock-element för ItemSelectionCondition för GroupBy (format)

Anger det skript som utlöser villkoret. När det här skriptet utvärderas `true` , uppfylls villkoret och kontrollen används. Det här elementet används när du definierar hur en ny grupp av objekt visas.

Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for GroupBy (format) CustomEntry-element för CustomControl för GroupBy (format) CustomItem-element för CustomEntry for GroupBy (format) ExpressionBinding-element för CustomItem for GroupBy (format) ItemSelectionCondition-element för ExpressionBinding för GroupBy (format) script block element for ItemSelectionCondition for groupby (format)

## <a name="syntax"></a>Syntax

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och `ScriptBlock` elementets överordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

Inga.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ItemSelectionCondition-element för ExpressionBinding för GroupBy (format)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas.|

## <a name="text-value"></a>Textvärde

Ange det skript som utvärderas.

## <a name="remarks"></a>Kommentarer

Om det här elementet används kan du inte ange elementet [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) när du definierar urvals villkoret.

## <a name="see-also"></a>Se även

[ItemSelectionCondition-element för ExpressionBinding för GroupBy (format)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[PropertyName-element för ItemSelectionCondition för GroupBy (format)](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
