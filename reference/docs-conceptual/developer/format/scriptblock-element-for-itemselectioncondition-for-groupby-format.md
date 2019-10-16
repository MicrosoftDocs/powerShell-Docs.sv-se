---
title: Script block-element för ItemSelectionCondition for GroupBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 58d25835-4636-4c58-9f6c-0332b9318051
caps.latest.revision: 6
ms.openlocfilehash: 4045196e306e766cd805b3e7ae31bfcb3de184ee
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355806"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-groupby-format"></a>ScriptBlock-element för ItemSelectionCondition för GroupBy (format)

Anger det skript som utlöser villkoret. När det här skriptet utvärderas till `true`, uppfylls villkoret och kontrollen används. Det här elementet används när du definierar hur en ny grupp av objekt visas.

Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for GroupBy (format) CustomEntry-element för CustomControl for GroupBy (format) CustomItem-element för CustomEntry för GroupBy (format) ExpressionBinding-element för CustomItem för GroupBy (format) ItemSelectionCondition-element för ExpressionBinding för GroupBy (format) script block-element för ItemSelectionCondition för GroupBy (format)

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
|[ItemSelectionCondition-element för ExpressionBinding för GroupBy (format)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas.|

## <a name="text-value"></a>Text värde

Ange det skript som utvärderas.

## <a name="remarks"></a>Anmärkningar

Om det här elementet används kan du inte ange elementet [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) när du definierar urvals villkoret.

## <a name="see-also"></a>Se även

[ItemSelectionCondition-element för ExpressionBinding för GroupBy (format)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[PropertyName-element för ItemSelectionCondition för GroupBy (format)](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
