---
title: ScriptBlock Element för ItemSelectionCondition för GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 58d25835-4636-4c58-9f6c-0332b9318051
caps.latest.revision: 6
ms.openlocfilehash: 4045196e306e766cd805b3e7ae31bfcb3de184ee
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064551"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-groupby-format"></a>ScriptBlock-element för ItemSelectionCondition för GroupBy (format)

Anger det skript som utlöser villkoret. När det här skriptet ska utvärderas till `true`villkoret uppfylls och kontrollen används. Det här elementet används när du definierar hur en ny grupp med objekt visas.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) GroupBy konfigurationselement för Visa (Format) anpassad kontroll elementet för GroupBy (Format) CustomEntries Element för anpassad kontroll för GroupBy (Format) CustomEntry elementet för Anpassad kontroll för GroupBy (Format) CustomItem elementet för CustomEntry för GroupBy (Format) ExpressionBinding elementet för CustomItem för GroupBy (Format) ItemSelectionCondition elementet för ExpressionBinding för GroupBy (Format) ScriptBlock elementet för ItemSelectionCondition för GroupBy (Format)

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
|[ItemSelectionCondition Element för ExpressionBinding för GroupBy (Format)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|Definierar de villkor som måste finnas för den här kontrollen som ska användas.|

## <a name="text-value"></a>Textvärde

Ange det skript som ska utvärderas.

## <a name="remarks"></a>Anmärkningar

Om det här elementet används som du kan inte ange den [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) element när du definierar urvalsvillkoret.

## <a name="see-also"></a>Se även

[ItemSelectionCondition Element för ExpressionBinding för GroupBy (Format)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[PropertyName-Element för ItemSelectionCondition för GroupBy (Format)](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
