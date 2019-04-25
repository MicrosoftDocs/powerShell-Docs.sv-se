---
title: PropertyName-Element för ItemSelectionCondition för anpassad kontroll för vy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b12006-8d52-486b-91a3-e6224ca80e56
caps.latest.revision: 6
ms.openlocfilehash: 52d0b0816eaef6752220e0c3b1249e5a0e44a3ee
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064874"
---
# <a name="propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a>PropertyName-element för ItemSelectionCondition för CustomControl för View (format)

Anger den .NET-egenskap som utlöser villkoret. När den här egenskapen finns eller att inventera till `true`villkoret uppfylls och kontrollen används. Det här elementet används när du definierar en anpassad kontroll vy.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) anpassad kontroll Element (Format) CustomEntries konfigurationselement för anpassad kontroll för Visa (Format) CustomEntry elementet för CustomEntries för vyn (Format) CustomItem elementet för CustomEntry för Visa (Format) ExpressionBinding elementet för CustomItem för anpassad kontroll för Visa (Format) ItemSelectionCondition elementet för uttrycket bindningen för anpassad kontroll för Visa (Format) PropertyName elementet för ItemSelectionCondition för Anpassad kontroll för vy (Format

## <a name="syntax"></a>Syntax

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `PropertyName` element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ItemSelectionCondition Element för uttrycket bindningen för anpassad kontroll för vy (Format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|Definierar de villkor som måste finnas för den här kontrollen som ska användas.|

## <a name="text-value"></a>Textvärde

Ange namnet på egenskapen .NET som utlöser villkoret.

## <a name="remarks"></a>Anmärkningar

Om det här elementet används som du kan inte ange den [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) element när du definierar urvalsvillkoret.

## <a name="see-also"></a>Se även

[ScriptBlock Element för ItemSelectionCondition för anpassad kontroll för vy (Format)](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[ItemSelectionCondition Element för uttrycket bindningen för anpassad kontroll för vy (Format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
