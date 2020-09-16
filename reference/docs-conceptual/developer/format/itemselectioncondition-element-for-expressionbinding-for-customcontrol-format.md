---
title: ItemSelectionCondition-element för ExpressionBinding för CustomControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 6a5c66a63c02980b16c2d2d9dd689410c8aec51c
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781196"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-customcontrol-format"></a>ItemSelectionCondition-element för ExpressionBinding för CustomControl (format)

Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas. Det finns ingen gräns för antalet urvals villkor som kan anges för ett kontroll objekt. Det här elementet används när du definierar en anpassad kontrol vy.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) CustomControl-element (format) CustomEntries-element för CustomControl för View (format) CustomEntry-element för CustomEntries för View (format) CustomItem-element för CustomEntry för View (format) ExpressionBinding-element för CustomItem för View (format) CustomControl-element för ItemSelectionCondition för View (format) CustomControl-element för för View

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
|[PropertyName-element för ItemSelectionCondition för CustomControl för visning (format](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|Valfritt element.<br /><br /> Anger den .NET-egenskap som utlöser villkoret.|
|[ScriptBlock-element för ItemSelectionCondition för CustomControl för View (format)](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|Valfritt element.<br /><br /> Anger det skript som utlöser villkoret.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ExpressionBinding-element för CustomItem för CustomControl för View (format)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|Definierar de data som visas av kontrollen.|

## <a name="remarks"></a>Kommentarer

Du kan ange ett egenskaps namn eller ett skript för villkoret, men kan inte ange båda.

## <a name="see-also"></a>Se även

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)

[ExpressionBinding-element för CustomItem för CustomControl för View (format)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)
