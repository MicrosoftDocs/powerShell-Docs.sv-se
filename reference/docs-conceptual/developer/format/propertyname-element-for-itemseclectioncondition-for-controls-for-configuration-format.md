---
title: PropertyName-element för ItemSeclectionCondition för kontroll av konfiguration (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 0e304af1dbe816753d6dcd1dd8149f950f2a0941
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785599"
---
# <a name="propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a>PropertyName-element för ItemSeclectionCondition för Controls för Configuration (format)

Anger den .NET-egenskap som utlöser villkoret. När den här egenskapen finns eller när den utvärderas `true` , uppfylls villkoret och kontrollen används. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.

Konfigurations element (format) styr element i konfigurations-(format)-kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för Configuration (format) CustomEntry-element för CustomControl för kontroller för konfiguration (format) CustomItem-element för CustomEntry for Controls for Configuration ExpressionBinding-element för CustomItem for Controls for Configuration (format) ItemSelectionCondition-element för ExpressionBinding för Controls (format) PropertyName-element för ItemSeclectionCondition för kontroll av konfiguration (format)

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
|[ItemSelectionCondition-element för ExpressionBinding för Controls för Configuration (format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas.|

## <a name="text-value"></a>Textvärde

Ange namnet på den .NET-egenskap som utlöser villkoret.

## <a name="remarks"></a>Kommentarer

Om det här elementet används kan du inte ange [script block](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) -elementet när du definierar urvals villkoret.

## <a name="see-also"></a>Se även

[ScriptBlock-element för ItemSeclectionCondition för Controls för Configuration (format)](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[ItemSelectionCondition-element för ExpressionBinding för Controls för Configuration (format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
