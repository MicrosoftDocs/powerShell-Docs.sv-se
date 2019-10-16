---
title: ItemSelectionCondition-element för ExpressionBinding för kontroll av konfiguration (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd3ddc33-b21c-4464-b3f2-a78dbe0062a8
caps.latest.revision: 8
ms.openlocfilehash: 4865d716ebe0460b662253a3019e93e82428b882
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354469"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format"></a>ItemSelectionCondition-element för ExpressionBinding för Controls för Configuration (format)

Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.

Konfigurations element (format) styr element i konfigurations-(format) kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för konfiguration ( Format) CustomEntry-element för CustomControl for Controls for Configuration (format) CustomItem element for CustomEntry for Controls for Configuration ExpressionBinding element for CustomItem for Controls for Configuration (format) ItemSelectionCondition-element för ExpressionBinding för kontroller för konfiguration (format)

## <a name="syntax"></a>Syntax

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för elementet `ItemSelectionCondition`.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[PropertyName-element för ItemSelectionCondition för kontroll av konfiguration (format)](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Anger den .NET-egenskap som utlöser villkoret.|
|[Script block-element för ItemSelectionCondition för kontroller för konfiguration (format)](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Anger det skript som utlöser villkoret.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ExpressionBinding-element för CustomItem för kontroller för konfiguration (format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|Definierar de data som visas av kontrollen.|

## <a name="remarks"></a>Anmärkningar

Du kan ange ett egenskaps namn eller ett skript för villkoret, men kan inte ange båda.

## <a name="see-also"></a>Se även

[PropertyName-element för ItemSelectionCondition för kontroll av konfiguration (format)](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[Script block-element för ItemSelectionCondition för kontroller för konfiguration (format)](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[ExpressionBinding-element för CustomItem för kontroller för konfiguration (format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
