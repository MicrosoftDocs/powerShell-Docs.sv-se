---
title: ItemSelectionCondition-element för ExpressionBinding för kontroller för vy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e8e3ea64fd947fbb2b98c410ac08533f386c9505
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781213"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format"></a>ItemSelectionCondition-element för ExpressionBinding för Controls för View (format)

Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas. Det här elementet används när du definierar kontroller som kan användas av en vy.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) styr element (format) styr element (format) styr element för Controls (format) CustomControl-element för Control for View (format) CustomEntries-element för CustomControl för visning (format) CustomEntry-element för CustomEntries for Controls for View (format) CustomItem element for CustomEntry for Controls for View (format) ExpressionBinding element for CustomItem for Controls for View (format) ItemSelectionCondition element of ExpressionBinding for Controls for View (format)

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
|[PropertyName-element för ItemSelectionCondition för Controls för View (format)](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)|Valfritt element.<br /><br /> Anger den .NET-egenskap som utlöser villkoret.|
|[ScriptBlock-element för ItemSelectionCondition för Controls för View (format)](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)|Valfritt element.<br /><br /> Anger det skript som utlöser villkoret.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ExpressionBinding-element för CustomItem för Controls för View (format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|Definierar de data som visas av kontrollen.|

## <a name="remarks"></a>Kommentarer

Du kan ange ett egenskaps namn eller ett skript för villkoret, men kan inte ange båda.

## <a name="see-also"></a>Se även

[PropertyName-element för ItemSelectionCondition för Controls för View (format)](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[ScriptBlock-element för ItemSelectionCondition för Controls för View (format)](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[ExpressionBinding-element för CustomItem för Controls för View (format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
