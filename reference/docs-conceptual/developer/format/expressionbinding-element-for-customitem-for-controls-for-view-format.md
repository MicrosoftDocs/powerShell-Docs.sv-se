---
ms.date: 09/13/2016
ms.topic: reference
title: ExpressionBinding-element för CustomItem för Controls för View (format)
description: ExpressionBinding-element för CustomItem för Controls för View (format)
ms.openlocfilehash: da87bb26d21dcb051871e67997cc3fba7ce73c74
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92649890"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-view-format"></a>ExpressionBinding-element för CustomItem för Controls för View (format)

Definierar de data som visas av kontrollen. Det här elementet används när du definierar kontroller som kan användas av en vy.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) styr element (format) kontroll element (format) styr element (format) för kontroll element för View (format) CustomControl-element för kontroll för Control for View (format) CustomEntries element för CustomControl for View (format) CustomEntry-elementet för CustomEntries for Controls for View (format) CustomItem-elementet for CustomEntry for Controls for View (format) ExpressionBinding element for CustomItem for Controls for View (format)

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
|[CustomControlName-element för ExpressionBinding för Controls för View (format)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)|Valfritt element.<br /><br /> Anger namnet på en gemensam kontroll eller en visnings kontroll.|
|[EnumerateCollection-element för ExpressionBinding för Controls för View (format)](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)|Valfritt element.<br /><br /> Anger att elementen i samlingar visas.|
|[ItemSelectionCondition-element för ExpressionBinding för kontroller för vy (format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|Valfritt element.<br /><br /> Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas.|
|[PropertyName-element för ExpressionBinding för Controls för View (format)](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)|Valfritt element.<br /><br /> Anger den .NET-egenskap vars värde visas av kontrollen.|
|[ScriptBlock-element för ExpressionBinding för Controls för View (format)](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)|Valfritt element.<br /><br /> Anger det skript vars värde visas i kontrollen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomItem-element för CustomEntry för Controls för View (format)](./customitem-element-for-customentry-for-controls-for-view-format.md)|Definierar vilka data som visas av kontrollen och hur de visas.|

## <a name="remarks"></a>Kommentarer

## <a name="see-also"></a>Se även

[CustomItem-element för CustomEntry för Controls för View (format)](./customitem-element-for-customentry-for-controls-for-view-format.md)

[CustomControlName-element för ExpressionBinding för Controls för View (format)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[EnumerateCollection-element för ExpressionBinding för Controls för View (format)](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)

[ItemSelectionCondition-element för ExpressionBinding för kontroller för vy (format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[PropertyName-element för ExpressionBinding för Controls för View (format)](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)

[ScriptBlock-element för ExpressionBinding för Controls för View (format)](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
