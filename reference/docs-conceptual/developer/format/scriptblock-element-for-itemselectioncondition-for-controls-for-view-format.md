---
ms.date: 09/13/2016
ms.topic: reference
title: ScriptBlock-element för ItemSelectionCondition för Controls för View (format)
description: ScriptBlock-element för ItemSelectionCondition för Controls för View (format)
ms.openlocfilehash: c005215f7b7984541806d2f5de47372d536787ff
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665192"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-controls-for-view-format"></a>ScriptBlock-element för ItemSelectionCondition för Controls för View (format)

Anger det skript som utlöser villkoret. När det här skriptet utvärderas `true` , uppfylls villkoret och kontrollen används. Det här elementet används när du definierar kontroller som kan användas av en vy.

Konfigurations element (format) ViewDefinitions element (format) Visa element (format) styr element (format) kontroll element (format) styr element (format) kontroll element för Controls for View (format) CustomControl-element för Control for View (format) CustomEntries-element för CustomControl för View (format) CustomEntry-element för för Controls for View (format) CustomItem-element för CustomEntry for Controls for View (format) ExpressionBinding-element för CustomItem för Controls for View (format) ItemSelectionCondition-elementet i ExpressionBinding for Controls for View (format) script block element for ItemSelectionCondition for Controls for View (format)

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
|[ItemSelectionCondition-element för ExpressionBinding för kontroller för vy (format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas.|

## <a name="text-value"></a>Textvärde

Ange det skript som utvärderas.

## <a name="remarks"></a>Kommentarer

Om det här elementet används kan du inte ange elementet [PropertyName](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) när du definierar urvals villkoret.

## <a name="see-also"></a>Se även

[PropertyName-element för ItemSelectionCondition för Controls för View (format)](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[ItemSelectionCondition-element för ExpressionBinding för kontroller för vy (format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
