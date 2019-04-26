---
title: ItemSelectionCondition Element för ExpressionBinding för anpassad kontroll (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f4bea9d8-27ad-410e-ad48-287f807d3e4e
caps.latest.revision: 7
ms.openlocfilehash: 18b0113c9b7b0895a1093cb0b56cd2d02c74a6c1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065840"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-customcontrol-format"></a>ItemSelectionCondition-element för ExpressionBinding för CustomControl (format)

Definierar de villkor som måste finnas för den här kontrollen som ska användas. Det finns ingen gräns för hur många val av villkor som kan anges för ett kontrollobjekt. Det här elementet används när du definierar en anpassad kontroll vy.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) anpassad kontroll Element (Format) CustomEntries konfigurationselement för anpassad kontroll för Visa (Format) CustomEntry elementet för CustomEntries för vyn (Format) CustomItem elementet för CustomEntry för Visa (Format) ExpressionBinding elementet för CustomItem för anpassad kontroll för Visa (Format) ItemSelectionCondition elementet för uttrycket bindningen för anpassad kontroll för vy (Format)

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
|[PropertyName-Element för ItemSelectionCondition för anpassad kontroll för vy (Format](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|Valfritt element.<br /><br /> Anger den .NET-egenskap som utlöser villkoret.|
|[ScriptBlock Element för ItemSelectionCondition för anpassad kontroll för vy (Format)](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|Valfritt element.<br /><br /> Anger det skript som utlöser villkoret.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ExpressionBinding Element för CustomItem för anpassad kontroll för vy (Format)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|Definierar de data som visas i kontrollen.|

## <a name="remarks"></a>Anmärkningar

Du kan ange ett egenskapsnamn eller ett skript för det här villkoret men kan inte ange båda.

## <a name="see-also"></a>Se även

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)

[ExpressionBinding Element för CustomItem för anpassad kontroll för vy (Format)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)
