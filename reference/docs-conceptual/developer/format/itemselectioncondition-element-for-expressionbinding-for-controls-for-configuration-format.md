---
ms.date: 09/13/2016
ms.topic: reference
title: ItemSelectionCondition-element för ExpressionBinding för Controls för Configuration (format)
description: ItemSelectionCondition-element för ExpressionBinding för Controls för Configuration (format)
ms.openlocfilehash: 6bd3d386ba64b33a1744fcc9e602cf13404765a0
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648084"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format"></a>ItemSelectionCondition-element för ExpressionBinding för Controls för Configuration (format)

Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.

Konfigurations element (format) styr element i konfigurations-(format)-kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för konfiguration (format) CustomEntry-element för CustomControl for Controls for Configuration (format) CustomItem-elementet för CustomEntry för Controls för Configuration ExpressionBinding-element för CustomItem för Controls (format) ItemSelectionCondition-element för ExpressionBinding för kontroll av konfiguration (format)

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
|[PropertyName-element för ItemSelectionCondition för kontroll av konfiguration (format)](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Anger den .NET-egenskap som utlöser villkoret.|
|[Script block-element för ItemSelectionCondition för kontroller för konfiguration (format)](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Anger det skript som utlöser villkoret.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ExpressionBinding-element för CustomItem för Controls för Configuration (format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|Definierar de data som visas av kontrollen.|

## <a name="remarks"></a>Kommentarer

Du kan ange ett egenskaps namn eller ett skript för villkoret, men kan inte ange båda.

## <a name="see-also"></a>Se även

[PropertyName-element för ItemSelectionCondition för kontroll av konfiguration (format)](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[Script block-element för ItemSelectionCondition för kontroller för konfiguration (format)](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[ExpressionBinding-element för CustomItem för Controls för Configuration (format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
