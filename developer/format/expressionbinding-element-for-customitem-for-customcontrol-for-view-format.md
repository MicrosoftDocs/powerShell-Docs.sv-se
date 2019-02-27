---
title: ExpressionBinding Element för CustomItem för anpassad kontroll för vy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f5ebea5-ee9c-4b90-a116-12a1daa28fc7
caps.latest.revision: 7
ms.openlocfilehash: 226bbea1d7613ad3099e05e8caa9817ff16c1f42
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850094"
---
# <a name="expressionbinding-element-for-customitem-for-customcontrol-for-view-format"></a>ExpressionBinding-element för CustomItem för CustomControl för View (format)

Definierar de data som visas i kontrollen. Det här elementet används när du definierar en anpassad kontroll vy.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) anpassad kontroll konfigurationselement för Visa (Format) CustomEntries elementet för anpassad kontroll för Visa (Format) CustomEntry elementet för CustomEntries för anpassad kontroll för Visa ( Format) CustomItem Element för CustomEntry för anpassad kontroll för Visa (Format) ExpressionBinding elementet för CustomItem för anpassad kontroll för vy (Format)

## <a name="syntax"></a>Syntax

```xml
<ExpressionBinding>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameofCommonCustomControl</CustomControlName>
  <EnumerateCollection/>
  <ItemSelectionCondition>...</ItemSelectionCondition>
  <PropertyName>Nameof.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate></ScriptBlock>
</ExpressionBinding>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `ExpressionBinding` element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|`CustomControl Element`|Valfritt element.<br /><br /> Definierar en kontroll som används av den här kontrollen.|
|[CustomControlName Element för ExpressionBinding för anpassad kontroll för vy (Format)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Valfritt element.<br /><br /> Anger namnet på en gemensam kontroll eller en kontroll.|
|[EnumerateCollection Element för ExpressionBinding för anpassad kontroll för vy (Format)](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Valfritt element.<br /><br /> Ange att elementen i samlingar visas.|
|[ItemSelectionCondition Element för ExpressionBinding för anpassad kontroll för vy (Format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|Valfritt element.<br /><br /> Definierar de villkor som måste finnas för den här kontrollen som ska användas.|
|[PropertyName-Element för ExpressionBinding för anpassad kontroll för vy (Format)](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Valfritt element.<br /><br /> Anger egenskapen .NET vars värde visas i kontrollen.|
|[ScriptBlock Element för ExpressionBinding för CustomCustomControl för vy (Format)](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Valfritt element.<br /><br /> Anger skriptet vars värde visas i kontrollen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomItem Element för CustomEntry för anpassad kontroll för vy (Format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|Definierar vilka data som visas i vyn anpassad kontroll och hur de visas.|

## <a name="remarks"></a>Anmärkningar

## <a name="see-also"></a>Se även

[CustomControlName Element för ExpressionBinding för anpassad kontroll för vy (Format)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[EnumerateCollection Element för ExpressionBinding för anpassad kontroll för vy (Format)](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[ItemSelectionCondition Element för ExpressionBinding för anpassad kontroll för vy (Format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[PropertyName-Element för ExpressionBinding för anpassad kontroll för vy (Format)](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[ScriptBlock Element för ExpressionBinding för anpassad kontroll för vy (Format)](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[CustomItem Element för CustomEntry för anpassad kontroll för vy (Format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
