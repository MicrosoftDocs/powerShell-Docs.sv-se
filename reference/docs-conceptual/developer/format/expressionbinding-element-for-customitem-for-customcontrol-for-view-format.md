---
title: ExpressionBinding-element för CustomItem för CustomControl för View (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f5ebea5-ee9c-4b90-a116-12a1daa28fc7
caps.latest.revision: 7
ms.openlocfilehash: 226bbea1d7613ad3099e05e8caa9817ff16c1f42
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354630"
---
# <a name="expressionbinding-element-for-customitem-for-customcontrol-for-view-format"></a>ExpressionBinding-element för CustomItem för CustomControl för View (format)

Definierar de data som visas av kontrollen. Det här elementet används när du definierar en anpassad kontrol vy.

Konfigurations element (format) ViewDefinitions element (format) Visa element (format) CustomControl-element för View (format) CustomEntries-element för CustomControl för View (format) CustomEntry-element för CustomEntries för View Format) CustomItem-element för CustomEntry för CustomControl för View (format) ExpressionBinding-elementet för CustomItem för View (format)

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

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `ExpressionBinding`-elementet.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|`CustomControl Element`|Valfritt element.<br /><br /> Definierar en kontroll som används av den här kontrollen.|
|[CustomControlName-element för ExpressionBinding för CustomControl för View (format)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Valfritt element.<br /><br /> Anger namnet på en gemensam kontroll eller en visnings kontroll.|
|[EnumerateCollection-element för ExpressionBinding för CustomControl för View (format)](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Valfritt element.<br /><br /> Anger att samlings elementen visas.|
|[ItemSelectionCondition-element för ExpressionBinding för CustomControl för View (format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|Valfritt element.<br /><br /> Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas.|
|[PropertyName-element för ExpressionBinding för CustomControl för vy (format)](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Valfritt element.<br /><br /> Anger den .NET-egenskap vars värde visas av kontrollen.|
|[Script block-element för ExpressionBinding för CustomCustomControl för View (format)](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Valfritt element.<br /><br /> Anger det skript vars värde visas i kontrollen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomItem-element för CustomEntry för CustomControl för View (format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|Definierar vilka data som visas i vyn anpassad kontroll och hur den visas.|

## <a name="remarks"></a>Anmärkningar

## <a name="see-also"></a>Se även

[CustomControlName-element för ExpressionBinding för CustomControl för View (format)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[EnumerateCollection-element för ExpressionBinding för CustomControl för View (format)](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[ItemSelectionCondition-element för ExpressionBinding för CustomControl för View (format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[PropertyName-element för ExpressionBinding för CustomControl för vy (format)](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[Script block-element för ExpressionBinding för CustomControl för View (format)](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[CustomItem-element för CustomEntry för CustomControl för View (format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
