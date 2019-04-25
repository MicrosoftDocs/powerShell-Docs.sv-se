---
title: ScriptBlock Element för ItemSelectionCondition för kontroller för att visa (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4191157-bf01-4831-b221-6f8cc581cd53
caps.latest.revision: 6
ms.openlocfilehash: 0cbefbb48427b56d4ae2a5ae27c7726dcfad7b84
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064738"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-controls-for-view-format"></a>ScriptBlock-element för ItemSelectionCondition för Controls för View (format)

Anger det skript som utlöser villkoret. När det här skriptet ska utvärderas till `true`villkoret uppfylls och kontrollen används. Det här elementet används när du definierar kontroller som kan användas av en vy.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) kontroller Element (Format) kontroll konfigurationselement för kontroller för att visa (Format) anpassad kontroll Element för kontroll för kontroller för att visa (Format) CustomEntries Element för Anpassad kontroll för Visa (Format) CustomEntry elementet för CustomEntries för kontroller för att visa (Format) CustomItem Element för CustomEntry för kontroller för att visa (Format) ExpressionBinding Element för CustomItem för kontroller för att visa (Format) ItemSelectionCondition Element i ExpressionBinding för kontroller för att visa (Format) ScriptBlock Element för ItemSelectionCondition för kontroller för att visa (Format)

## <a name="syntax"></a>Syntax

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `ScriptBlock` element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ItemSelectionCondition Element i ExpressionBinding för kontroller för att visa (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|Definierar de villkor som måste finnas för den här kontrollen som ska användas.|

## <a name="text-value"></a>Textvärde

Ange det skript som ska utvärderas.

## <a name="remarks"></a>Anmärkningar

Om det här elementet används som du kan inte ange den [PropertyName](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) element när du definierar urvalsvillkoret.

## <a name="see-also"></a>Se även

[PropertyName-Element för ItemSelectionCondition för kontroller för att visa (Format)](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[ItemSelectionCondition Element i ExpressionBinding för kontroller för att visa (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
