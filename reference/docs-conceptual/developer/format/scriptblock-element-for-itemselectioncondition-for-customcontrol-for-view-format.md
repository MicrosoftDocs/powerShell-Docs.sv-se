---
title: Script block-element för ItemSelectionCondition för CustomControl för View (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 946cd2b5-ac37-4a13-bb49-29fbc70ec8d7
caps.latest.revision: 6
ms.openlocfilehash: 0c07ab0e5d04c4056a7e7215bfa55773bfccb41d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353874"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a>ScriptBlock-element för ItemSelectionCondition för CustomControl för View (format)

Anger det skript som utlöser villkoret. När det här skriptet utvärderas till `true`, uppfylls villkoret och kontrollen används. Det här elementet används när du definierar en anpassad kontrol vy.

Konfigurations element (format) ViewDefinitions element (format) View element (format) CustomControl element (format) CustomEntries-element för CustomControl för View (format) CustomEntry-element för CustomEntries för View (format) CustomItem-element för CustomEntry för visnings-(format) ExpressionBinding-element för CustomItem för CustomControl för View (format) ItemSelectionCondition-element för uttrycks bindning för CustomControl för View (format) script block-element för ItemSelectionCondition för CustomControl för vy (format)

## <a name="syntax"></a>Syntax

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för elementet `ScriptBlock`.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ItemSelectionCondition-element för uttrycks bindning för CustomControl för vy (format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas.|

## <a name="text-value"></a>Text värde

Ange det skript som utvärderas.

## <a name="remarks"></a>Anmärkningar

Om det här elementet används kan du inte ange elementet [PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) när du definierar urvals villkoret.

## <a name="see-also"></a>Se även

[PropertyName-element för ItemSelectionCondition för CustomControl för vy (format)](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[ItemSelectionCondition-element för uttrycks bindning för CustomControl för vy (format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
