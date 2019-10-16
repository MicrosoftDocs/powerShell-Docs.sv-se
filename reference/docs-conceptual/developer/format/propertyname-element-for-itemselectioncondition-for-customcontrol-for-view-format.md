---
title: PropertyName-element för ItemSelectionCondition för CustomControl för vy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b12006-8d52-486b-91a3-e6224ca80e56
caps.latest.revision: 6
ms.openlocfilehash: 52d0b0816eaef6752220e0c3b1249e5a0e44a3ee
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354133"
---
# <a name="propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a>PropertyName-element för ItemSelectionCondition för CustomControl för View (format)

Anger den .NET-egenskap som utlöser villkoret. När den här egenskapen finns eller när den utvärderas till `true`, uppfylls villkoret och kontrollen används. Det här elementet används när du definierar en anpassad kontrol vy.

Konfigurations element (format) ViewDefinitions element (format) View element (format) CustomControl element (format) CustomEntries-element för CustomControl för View (format) CustomEntry-element för CustomEntries för View (format) CustomItem-element för CustomEntry för visnings-(format) ExpressionBinding-element för CustomItem för CustomControl för View (format) ItemSelectionCondition-element för uttrycks bindning för CustomControl för View (format) PropertyName-element för ItemSelectionCondition för CustomControl för vy (format

## <a name="syntax"></a>Syntax

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för elementet `PropertyName`.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ItemSelectionCondition-element för uttrycks bindning för CustomControl för vy (format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas.|

## <a name="text-value"></a>Text värde

Ange namnet på den .NET-egenskap som utlöser villkoret.

## <a name="remarks"></a>Anmärkningar

Om det här elementet används kan du inte ange [script block](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) -elementet när du definierar urvals villkoret.

## <a name="see-also"></a>Se även

[Script block-element för ItemSelectionCondition för CustomControl för View (format)](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[ItemSelectionCondition-element för uttrycks bindning för CustomControl för vy (format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
