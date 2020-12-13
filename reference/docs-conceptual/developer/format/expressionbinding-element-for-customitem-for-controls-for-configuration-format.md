---
ms.date: 09/13/2016
ms.topic: reference
title: ExpressionBinding-element för CustomItem för Controls för Configuration (format)
description: ExpressionBinding-element för CustomItem för Controls för Configuration (format)
ms.openlocfilehash: 1abcf2173e18d45839161b4c7e59f1ad238f81a1
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655333"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-configuration-format"></a>ExpressionBinding-element för CustomItem för Controls för Configuration (format)

Definierar de data som visas av kontrollen. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.

Konfigurations element (format) styr element i konfigurations-(format)-kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för Configuration (format) CustomEntry-element för CustomControl för Controls (format) CustomItem-element för CustomEntry för Controls för Configuration ExpressionBinding-element för CustomItem för Controls (format)

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

I följande avsnitt beskrivs attribut, underordnade element och `ExpressionBinding` elementets överordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|`CustomControl Element`|Valfritt element.<br /><br /> Definierar en kontroll som används av den här kontrollen.|
|[CustomControlName-element för ExpressionBinding för Controls för Configuration (format)](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Anger namnet på en gemensam kontroll eller en visnings kontroll.|
|[EnumerateCollection-element för ExpressionBinding för Controls för Configuration (format)](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Anger att elementen i samlingar visas av kontrollen.|
|[ItemSelectionCondition-element för ExpressionBinding för Controls för Configuration (format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Definierar det villkor som måste finnas för att den här gemensamma kontrollen ska kunna användas.|
|[PropertyName-element för ExpressionBinding för Controls för Configuration (format)](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Anger .NET-egenskapen vars värde visas av den gemensamma kontrollen.|
|[ScriptBlock-element för ExpressionBinding för Controls för Configuration (format)](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Anger det skript vars värde visas av den gemensamma kontrollen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomItem-element för CustomEntry för kontroller för konfiguration](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|Definierar vilka data som visas i vyn anpassad kontroll och hur den visas.|

## <a name="remarks"></a>Kommentarer

## <a name="see-also"></a>Se även

[CustomItem-element för CustomEntry för kontroller för konfiguration](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
