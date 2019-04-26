---
title: PropertyName-Element för ItemSeclectionCondition för kontroller för konfiguration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ad8ab181-c559-492e-a0cf-299e381fdcc3
caps.latest.revision: 6
ms.openlocfilehash: ce25789bdfc2679372ca9e42f99dcc6a30ae2def
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064915"
---
# <a name="propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a>PropertyName-element för ItemSeclectionCondition för Controls för Configuration (format)

Anger den .NET-egenskap som utlöser villkoret. När den här egenskapen finns eller att inventera till `true`villkoret uppfylls och kontrollen används. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.

Konfigurationselementet Element (Format) kontroller av (Format) kontroll konfigurationselement för kontroller för (Format) anpassad kontroll konfigurationselement för kontroll för (Format) CustomEntries konfigurationselement för anpassad kontroll för konfiguration ( Format) CustomEntry Element för anpassad kontroll för kontroller för (Format) CustomItem konfigurationselement för CustomEntry för kontroller för ExpressionBinding konfigurationselement för CustomItem för kontroller för konfiguration (Format) ItemSelectionCondition Element för ExpressionBinding för kontroller för (Format) PropertyName konfigurationselement för ItemSeclectionCondition för kontroller för konfiguration (Format)

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
|[ItemSelectionCondition Element för ExpressionBinding för kontroller för konfiguration (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|Definierar de villkor som måste finnas för den här kontrollen som ska användas.|

## <a name="text-value"></a>Textvärde

Ange namnet på egenskapen .NET som utlöser villkoret.

## <a name="remarks"></a>Anmärkningar

Om det här elementet används som du kan inte ange den [ScriptBlock](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) element när du definierar urvalsvillkoret.

## <a name="see-also"></a>Se även

[ScriptBlock Element för ItemSeclectionCondition för kontroller för konfiguration (Format)](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[ItemSelectionCondition Element för ExpressionBinding för kontroller för konfiguration (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
