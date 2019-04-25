---
title: ItemSelectionCondition Element för ExpressionBinding för kontroller för konfiguration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd3ddc33-b21c-4464-b3f2-a78dbe0062a8
caps.latest.revision: 8
ms.openlocfilehash: 4865d716ebe0460b662253a3019e93e82428b882
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065520"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format"></a>ItemSelectionCondition-element för ExpressionBinding för Controls för Configuration (format)

Definierar de villkor som måste finnas för den här kontrollen som ska användas. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.

Konfigurationselementet Element (Format) kontroller av (Format) kontroll konfigurationselement för kontroller för (Format) anpassad kontroll konfigurationselement för kontroll för (Format) CustomEntries konfigurationselement för anpassad kontroll för konfiguration ( Format) CustomEntry Element för anpassad kontroll för kontroller för (Format) CustomItem konfigurationselement för CustomEntry för kontroller för ExpressionBinding konfigurationselement för CustomItem för kontroller för konfiguration (Format) ItemSelectionCondition Element för ExpressionBinding för kontroller för konfiguration (Format)

## <a name="syntax"></a>Syntax

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `ItemSelectionCondition` element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[PropertyName-Element för ItemSelectionCondition för kontroller för konfiguration (Format)](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Anger den .NET-egenskap som utlöser villkoret.|
|[ScriptBlock Element för ItemSelectionCondition för kontroller för konfiguration (Format)](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Anger det skript som utlöser villkoret.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ExpressionBinding Element för CustomItem för kontroller för konfiguration (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|Definierar de data som visas i kontrollen.|

## <a name="remarks"></a>Anmärkningar

Du kan ange ett egenskapsnamn eller ett skript för det här villkoret men kan inte ange båda.

## <a name="see-also"></a>Se även

[PropertyName-Element för ItemSelectionCondition för kontroller för konfiguration (Format)](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[ScriptBlock Element för ItemSelectionCondition för kontroller för konfiguration (Format)](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[ExpressionBinding Element för CustomItem för kontroller för konfiguration (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
