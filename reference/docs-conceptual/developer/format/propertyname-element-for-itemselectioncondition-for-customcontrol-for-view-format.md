---
title: PropertyName-element för ItemSelectionCondition för CustomControl för vy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 0131fa86be4be4daec1d9d24b50397fb8529f050
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785582"
---
# <a name="propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a>PropertyName-element för ItemSelectionCondition för CustomControl för View (format)

Anger den .NET-egenskap som utlöser villkoret. När den här egenskapen finns eller när den utvärderas `true` , uppfylls villkoret och kontrollen används. Det här elementet används när du definierar en anpassad kontrol vy.

Konfigurations element (format) ViewDefinitions element (format) View element (format) CustomControl element (format) CustomEntries-element för CustomControl för View (format) CustomEntry-element för CustomEntries för View (format) CustomItem-element för CustomEntry för visnings-(format) ExpressionBinding-element för CustomItem för CustomControl för View (format) ItemSelectionCondition-element för uttrycks bindning för CustomControl för View (format) PropertyName-element för ItemSelectionCondition för View (format

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
|[ItemSelectionCondition-element för uttrycks bindning för CustomControl för vy (format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas.|

## <a name="text-value"></a>Textvärde

Ange namnet på den .NET-egenskap som utlöser villkoret.

## <a name="remarks"></a>Kommentarer

Om det här elementet används kan du inte ange [script block](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) -elementet när du definierar urvals villkoret.

## <a name="see-also"></a>Se även

[ScriptBlock-element för ItemSelectionCondition för CustomControl för View (format)](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[ItemSelectionCondition-element för uttrycks bindning för CustomControl för vy (format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
