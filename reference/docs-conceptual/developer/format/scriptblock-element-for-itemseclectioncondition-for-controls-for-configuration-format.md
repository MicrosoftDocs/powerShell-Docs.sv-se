---
title: Script block-element för ItemSeclectionCondition för kontroll av konfiguration (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 51f7aec9-7b01-4370-84f4-1e58508a851f
caps.latest.revision: 6
ms.openlocfilehash: e92b2dfff07358132c480c47c34279e5365fe400
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353909"
---
# <a name="scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a>ScriptBlock-element för ItemSeclectionCondition för Controls för Configuration (format)

Anger det skript som utlöser villkoret. När det här skriptet utvärderas till `true`, uppfylls villkoret och kontrollen används. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.

Konfigurations element (format) styr element i konfigurations-(format) kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för konfiguration ( Format) CustomEntry-element för CustomControl for Controls for Configuration (format) CustomItem element for CustomEntry for Controls for Configuration ExpressionBinding element for CustomItem for Controls for Configuration (format) ItemSelectionCondition-element för ExpressionBinding för kontroller för Configuration (format) script block-element för ItemSelectionCondition för kontroller för konfiguration (format)

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
|[ItemSelectionCondition-element för ExpressionBinding för kontroller för konfiguration (format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas.|

## <a name="text-value"></a>Text värde

Ange det skript som utvärderas.

## <a name="remarks"></a>Anmärkningar

Om det här elementet används kan du inte ange elementet [PropertyName](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) när du definierar urvals villkoret.

## <a name="see-also"></a>Se även

[PropertyName-element för ItemSeclectionCondition för kontroll av konfiguration (format)](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[ItemSelectionCondition-element för ExpressionBinding för kontroller för konfiguration (format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
